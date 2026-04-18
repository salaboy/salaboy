# Post Lengths Style Guide

## Short Posts (300–600 words)

**Best for:** Announcements, quick conference recaps, book launches, job changes, short event reports.

**Typical types:** Type E (Announcement), small Type C (Conference Recap), brief Type B (Conference Preview)

### Structure Rules
- **No internal headers** — prose flows without section dividers
- **2–4 sentence paragraphs throughout** — scannable, each paragraph makes one point
- Personal narrative arc: "I was here → I did this → here's what I thought"
- Gratitude-heavy — name organizers, collaborators, audience
- Closing is a simple community invitation

### Opening
Lead immediately with the most interesting thing. No warm-up paragraphs. The first sentence should contain the most important information.

### Middle
Tell the story chronologically or thematically, but keep each thread short. If you name three things, describe each in 1–2 sentences. Avoid tangents — save them for a longer post.

### Closing
A single forward-facing sentence or a brief community CTA. No summary paragraph. The reader doesn't need you to recap what they just read.

### Formatting
- No H2 headers
- Bold text only for names or event titles if needed
- Bullet lists acceptable for quick-fire lists (e.g., "I presented at: X, Y, Z") but keep short
- 1–2 links maximum (slides or event page)
- Flag emoji in title acceptable for event location identification (🇧🇷🇩🇪🇯🇵)

### Word Count Target
300–600 words. If you're going over 600, either cut content or promote to a medium post.

### Example Rhythm
```
[Exciting opening sentence with the core fact.]

[2–3 sentence paragraph expanding on context.]

[2–3 sentence paragraph on what happened / what you did.]

[1–2 sentence paragraph with a key observation or highlight.]

[Named people and their contributions — 1–3 lines.]

[1–2 sentence forward-looking close with CTA.]
```

---

## Medium Posts (600–1,800 words)

**Best for:** Conference recaps of major events (KubeCon, regional conferences), technical observations, community trends, book announcements with context.

**Typical types:** Type C (Conference Recap — major event), Type A (Thought Leadership — focused topic), Type B (Conference Preview — multi-day event)

### Structure Rules
- **2–4 H2 section headers** — divide the post into named thematic areas
- Mix of narrative and structured content
- Named individuals appear with affiliations throughout
- Technical observations stay at the level of "I noticed X" and "this signals Y" — no deep dive
- May include links to session slides or GitHub repos

### Opening
One punchy sentence capturing the overall impression, then immediately into the first section or thematic observation. No throat-clearing paragraphs.

### Sections
Each H2 section should cover one theme, event day, or topic cluster. Name sections descriptively, not generically:
- Good: "KubeCon Announcements," "Platform Engineering Conversations," "Rejekts and Co-located Events"
- Avoid: "Day 1," "Overview," "Details"

Each section: 2–4 paragraphs. Open with the broad observation, close with a specific example or named person/project.

### Middle
Alternate between narrative paragraphs (what happened) and observation paragraphs (what it means). Don't let either mode dominate for more than two consecutive paragraphs.

### Closing
Forward-looking reference to next event, or a brief synthesis statement followed by community CTA. No "In conclusion..." framing.

### Formatting
- H2 headers for sections
- Bold text for names and project names
- Bullet lists for enumerating talks, resources, or highlights within a section
- Code blocks only if referencing a specific command or config
- Flag emojis in section headers acceptable for international events

### Word Count Target
600–1,800 words. If you're under 600, it's a short post. If you're going past 1,800, you need either a "Sum up" section and tighter editing, or you're writing a long post.

### Paragraph Length Guidance
- Narrative paragraphs: 3–5 sentences
- Observation/opinion paragraphs: 2–4 sentences
- Emphasis/pivot paragraphs: 1–2 sentences (after a long argument, land the point)

---

## Long Posts (1,800–4,500+ words)

**Best for:** Industry analysis, state-of-the-ecosystem reports, deep technical comparisons, year-in-review, book-length topic introductions.

**Typical types:** Type A (Thought Leadership — major), Type F (Year-in-Review)

### Structure Rules
- **4–7 H2 headers** with occasional H3 subheaders for nested concepts
- A TLDR/summary statement at the top (used in the most recent posts — one sentence, optional)
- Multiple concrete examples per section, including code blocks or ASCII diagrams
- Questions posed rhetorically to the reader, then answered within the same section
- Explicitly acknowledges competing perspectives before stating your own
- "Sum up" section at the end (recap key points, not a generic conclusion)
- Final paragraph: community-facing CTA

### Opening
A personal observation or confession about why you're writing this now. This can be 2–3 sentences. Don't rush to the thesis — the opening establishes that you've been wrestling with this topic.

Then optionally: one-sentence TLDR for readers who want the bottom line first.

### Sections — Logical Arc
Long posts must build an argument. Each section should advance the narrative:
1. **Problem/observation** — what you've been seeing
2. **Context/history** — why this is happening now
3. **Deep dive 1** — first major dimension of the problem
4. **Deep dive 2** — second major dimension
5. **Synthesis** — how these connect
6. **Recommendations** — what to do about it
7. **Sum up** — key takeaways
8. **What's next / CTA** — forward look + community invitation

This is a template, not a formula. Sections can be merged, split, or reordered based on the argument.

### Paragraph Length Guidance
Long posts deliberately vary paragraph length for rhythm:
- **Long argument paragraph** (5–8 sentences): develop a complex point fully
- **Short emphasis paragraph** (1–2 sentences): immediately after a long one, land the key claim
- Never stack more than two long paragraphs consecutively without a short one to breathe

### Bullet Lists in Long Posts
Use bullet lists when you have 3+ parallel items that would create run-on prose. Each bullet should be:
- 1–2 sentences maximum
- Self-contained (the reader can scan the list independently)
- Content-dense — no filler bullets

Acceptable list subjects: tool lists, enumerated challenges, recommended strategies, open questions, project/community names.

Never use a bullet list as the entire post or an entire section. Lists live inside narrative paragraphs.

### Code and Diagrams in Long Posts
For technical long posts:
- Embed minimal illustrative code snippets inline (5–20 lines)
- Use ASCII workflow diagrams for process flows: `code → build → test → debug → repeat`
- Link to complete GitHub implementation — never try to make the post self-contained for code
- One diagram or code block per major concept — don't illustrate every point

### "Sum up" Section
Required for long posts. Contains:
- 3–5 bullet points recapping the main arguments
- One synthesizing sentence
- NOT a repetition of the opening — advance from observation to implication

### Closing Pattern
The final paragraph after "Sum up" should:
1. Acknowledge what comes next (next conference, next post, next project milestone)
2. Issue a community invitation
3. Include the standard CTA: *"As always if you have any questions or you want to reach out drop me a message on my social networks @Salaboy."*

### Commercial/Employer Balance in Long Posts
Mauricio frequently writes about tools related to his employers (Dapr, Diagrid, Dash0, OpenTelemetry). Rules for maintaining credibility:
- Criticize your own employer's tools when they don't solve the problem
- Name competitor tools and evaluate them fairly
- Attribute ideas and credit to collaborators, not just your employer
- Book/project promotion is contextual and brief — one reference per relevant section maximum

### Word Count Target
1,800–4,500+ words. There is no upper limit if the argument requires it, but every sentence should earn its place. If a section doesn't advance the argument, cut it.
