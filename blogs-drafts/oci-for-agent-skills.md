# [TITLE TBD]

I've seen this movie before. A new ecosystem explodes, adoption moves faster than anyone expected, and then everyone hits the same wall: how do we actually share this stuff in a reliable, secure, versioned way? In 2014 it was Docker images distributed as tarballs. In 2016 it was Helm charts floating around as zip files on Slack. Today, in 2026, it's Agent Skills — and the distribution story is, once again, "clone a repo and hope for the best."

I'm not saying this to be critical of the [Agent Skills specification](https://agentskills.io/specification). The spec, which Anthropic published in December 2025 and is now stewarded at [agentskills/agentskills](https://github.com/agentskills/agentskills), does something important: it defines a shared format for knowledge assets that coding agents — Claude Code, Cursor, GitHub Copilot, Codex, and others — can discover and use to do their work more accurately. That's genuinely useful. But the spec stops there. It says nothing about how to distribute skills, how to version them, how to verify their integrity, or how to consume them from inside a corporate firewall. And in my opinion, that gap needs to close before this ecosystem can grow up.

## We've Been Here Before

The cloud-native ecosystem spent years learning hard lessons about artifact distribution. Helm charts were shared as files attached to GitHub releases. WebAssembly modules were uploaded to ad-hoc buckets. Configuration bundles were copied between teams via Slack DMs. Each of these approaches had the same failure modes: no canonical discovery mechanism, no integrity guarantees, no reproducibility, and no supply chain security story.

The solution the community eventually converged on wasn't a new protocol or a new registry format. It was [OCI](https://opencontainers.org/) — the Open Container Initiative standards that most people associate with container images, but which are actually a general-purpose artifact store. Today, Helm charts live in OCI registries. WebAssembly components are distributed via OCI. [FluxCD](https://fluxcd.io/) manifests, SBOM files, Sigstore attestations — all OCI. The lesson the cloud-native world learned is that you don't need to invent new infrastructure when battle-tested infrastructure already exists and is running at every major cloud provider, every enterprise, and even on your laptop via Docker Desktop.

I strongly believe the same lesson applies directly to Agent Skills.

## The Problem With Git-Only Distribution

Right now, if you want to use a skill someone published, you navigate to their GitHub repository, browse around to find the skill directory, and copy the files into your project. GitHub's own [gh skill install](https://github.blog/changelog/2026-04-16-manage-agent-skills-with-github-cli/) command, released just this week in CLI v2.90.0, is a nice step forward — but it's still Git-URL-based under the hood, and GitHub itself warns users: "Skills are not verified by GitHub and may contain prompt injections, hidden instructions, or malicious scripts."

That warning isn't a minor footnote. It's the entire problem. [Thomas Vitale](https://www.thomasvitale.com/agent-skills-as-oci-artifacts/) put it well: "What if a vulnerability is found in one of its scripts? Can I even prove the integrity of the files I copied?" In the active [agentskills/agentskills Discussion #210](https://github.com/agentskills/agentskills/discussions/210), multiple independent implementors — [@erdemtuna](https://github.com/erdemtuna)'s `craft`, [@AlissonSteffens](https://github.com/AlissonSteffens)'s `sklz`, and others — converged on the same pain points: no discovery standard, no lockfile story, no integrity digests, and no enterprise-grade provenance. Everyone is solving it differently and nothing is interoperable.

The git-only model also creates a harder problem for companies running internal infrastructure. If your organisation uses [Forgejo](https://forgejo.org/) or an internal GitLab, you're on your own: either mirror public GitHub repositories manually or build custom tooling. That's not a distribution model — that's a liability.

## Skills as OCI Artifacts — The Right Abstraction

Thomas Vitale published [a detailed proposal](https://www.thomasvitale.com/agent-skills-as-oci-artifacts/) for packaging Agent Skills as OCI artifacts, and I think he's right. The core idea is elegant: a Skill artifact is an OCI Image Manifest with a custom `artifactType` (`application/vnd.agent-skills.skill.v1`), and its contents — the `SKILL.md`, scripts, and resources already defined by the spec — are packaged as the artifact's layers. Collections of skills are OCI Image Indexes, similar to multi-platform image manifests, referencing individual skill artifacts by digest.

On the consumer side, a `skills.json` declares which skills a project depends on by OCI reference, and a `skills.lock.json` pins the exact digest of each skill at install time. This is the same model Go modules, npm, and Cargo use — and it works. You get reproducible installs across your whole team, clear upgrade paths, and a paper trail.

Because these are standard OCI artifacts, any compliant registry works. Docker Hub, [GitHub Container Registry](https://ghcr.io), [Harbor](https://goharbor.io/), [Zot](https://zotregistry.dev/), your company's internal registry — it doesn't matter. No new infrastructure to run, no new accounts to create, no vendor lock-in on the registry side.

## Hands-On: Packaging and Sharing a Skill with `skills-oci`

I've been building [`skills-oci`](https://github.com/salaboy/skills-oci), a CLI built on the [ORAS Go client](https://github.com/oras-project/oras) that implements this approach. Here's the core workflow — four commands to go from a local skill to a shared, versioned artifact on Docker Hub:

**Package and push your skill:**
```bash
skills-oci push ./my-skill docker.io/salaboy/my-skill:v1.0.0
```

**Add it as a dependency to your project:**
```bash
skills-oci add docker.io/salaboy/my-skill:v1.0.0
```

**Install all declared skills (resolves and locks digests):**
```bash
skills-oci install
```

**Verify the integrity of an installed skill:**
```bash
skills-oci verify docker.io/salaboy/my-skill:v1.0.0
```

That last command is not just cosmetic. Because the artifact is content-addressed by digest and can be signed with [Cosign](https://github.com/sigstore/cosign), verification is a real guarantee — not a checkbox. The full source and examples are at [github.com/salaboy/skills-oci](https://github.com/salaboy/skills-oci).

## Free Supply Chain Security — No Extra Work

This is the part that genuinely excites me, and I think it's undersold in most conversations about OCI for non-container artifacts. Because a skill packaged as an OCI artifact is just an artifact like any other, the entire cloud-native supply chain security toolchain applies immediately — with zero additional format work.

You can sign a skill with [Cosign](https://docs.sigstore.dev/) and attach a [SLSA provenance](https://slsa.dev/) attestation so consumers can cryptographically verify who built it and from which source commit. You can generate an SBOM with [Syft](https://github.com/anchore/syft) and attach it as a referrer via the [OCI Referrers API](https://github.com/opencontainers/distribution-spec/blob/main/spec.md#listing-referrers). You can run a vulnerability scan with [Grype](https://github.com/anchore/grype) and attach the results so downstream teams can make informed decisions about which skills to adopt. None of this requires any new tooling — it all already works against any OCI-compliant registry.

For enterprises, this is the difference between "we allow skills" and "we have a governed, auditable skills programme." That distinction matters as agent-assisted development moves from hobby projects into regulated industries.

## What Still Needs to Happen

I want to be honest: this isn't done. The OCI artifact proposal, which Thomas and I are both pushing for as a formal addition to the core Agent Skills specification at [agentskills/agentskills](https://github.com/agentskills/agentskills), still needs broader community alignment. There are parallel implementations heading in the same direction — [Arconia CLI](https://github.com/ThomasVitale/arconia) by Thomas Vitale, [craft](https://github.com/erdemtuna/craft) by [@erdemtuna](https://github.com/erdemtuna), [ToolHive](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates) by [Stacklok](https://stacklok.com/) — and the fact that independent teams are converging on the same answers gives me confidence the direction is right. But convergence still needs to become interoperability, and that requires the community to commit to a shared spec.

The active discussions are public and open. [Discussion #210](https://github.com/agentskills/agentskills/discussions/210) on the agentskills repo is where the manifest format debate is live. [MCP Registry Discussion #895](https://github.com/modelcontextprotocol/registry/discussions/895) is exploring how discovery fits into the broader registry picture. These are the conversations worth joining if you care about where this lands.

I feel quite optimistic about where this is heading — but optimism doesn't write specs. If you're building in this space, come help shape it. Try `skills-oci`, open issues, push back on the proposal if you think something's wrong. The cloud-native ecosystem got here by arguing in the open, and I expect the agent skills ecosystem will need to do the same.

Drop me a message on [Bluesky](https://bsky.app/profile/salaboy.bsky.social) or open an issue at [github.com/salaboy/skills-oci](https://github.com/salaboy/skills-oci) — I look forward to seeing where this goes together.
