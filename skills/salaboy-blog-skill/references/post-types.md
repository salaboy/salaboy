# Post Types Style Guide

## Type A: Thought Leadership

**Examples from corpus:** "DevEx in the Age of AI," "Platform Engineering on Kubernetes in 2025," "Learning in the Open," "The Evolution of Platforms (GenAI Edition)"

**When to use:** Industry observations, trend analysis, predictions, contrarian takes, reflections on the state of an ecosystem.

### Opening Pattern
Start with a personal confession about why you're writing this *now*:
- *"I've been trying to write about this topic for a while, but the feeling that we already have too much content... has been slowing me down lately."*
- *"I am writing this blog post because many things have happened since the book was published."*
- *"Wow! What a year it has been!"*

Never open with the conclusion. Open with the moment of friction or realization that prompted the post.

### Structure
1. Personal/contextual opening — what prompted this post
2. Optional TLDR (one-sentence summary only — used sparingly in recent posts)
3. Named H2 sections (3–7) forming a logical arc
4. Each section: broad claim → narrow to specifics → concrete example
5. Bullet lists for tool lists, challenges, or enumerated recommendations
6. "Sum up" or "So what's next" section to close
7. Final paragraph: community invitation or personal forward-look

### Section Naming
Noun phrases or short questions, not generic labels:
- Good: "Coding, before agents," "Who owns the experience?," "From a one developer mindset to enterprises"
- Avoid: "Introduction," "Background," "Conclusion"

### Argument Pattern
> "Here is what I've observed → here is why it matters → here is what I think will happen → here is what you can do"

### Key Techniques
- Historical precedent as predictor (e.g., Java ecosystem tool proliferation → cloud-native consolidation)
- Direct mapping between known patterns and emerging ones (e.g., platform engineering lessons → coding agents)
- Concrete scenario walkthroughs: name the tool, run the command, describe what happens
- Name real tools in comparisons — never hypothetical "Tool A vs. Tool B"
- The recurring Pizza Store demo application as pedagogical anchor

### Closing Pattern
Look ahead or invite community:
- *"I look forward to crossing paths with all of you this year."*
- *"Ok, now time to go to KubeCon EU in Amsterdam. I hope to see you all there!"*
- *"As always if you have any questions or you want to reach out drop me a message on my social networks @Salaboy."*

---

## Type B: Conference Preview (Pre-Event)

**Examples from corpus:** "KubeCon EU 2025, Rejekts, Maintainers Summit," "Next week: KubeCon NA 2024," "Have you ever been to KubeCon?"

**When to use:** Announcing upcoming conference appearances, talks, and co-located events.

### Opening Pattern
Direct, energetic announcement:
- *"I am preparing myself for a crazy week at KubeCon EU next week."*
- *"I am extremely eager to meet all the amazing folks attending KubeCon NA 2024 in Salt Lake City USA."*
- *"I am heading to KubeCon NA Chicago, USA for a full 7 days of Cloud Native, Kubernetes, Platform Engineering, and Open Source"*

### Structure
1. Opening excitement + event location/date
2. Brief personal context (your role, why this event matters)
3. Day-by-day or event-by-event breakdown using H2 or bold text
4. Named people with affiliations for each session/activity
5. Closing: social invitation to connect

### Schedule Format
Use bold text or H2 headers for each day/sub-event. For each session include:
- Talk title (linked if schedule is published)
- Co-presenters named with affiliation
- Room/time if known
- What the session is about in one sentence

### Closing Pattern
Always a standing social invitation:
- *"Say hello! Don't be shy! If you see me running around the conference, please stop me to say hi! Let's talk tech!"*
- *"See you all at the conference!"*

---

## Type C: Conference Recap (Post-Event)

**Examples from corpus:** "KubeCon NA 2024 recap," "KubeCon EU 2024," "Learnings from Cloud Native Denmark and Devoxx Belgium 2025," "Cloud-Native & OSS is thriving in Brazil"

**When to use:** Post-event reflections, highlights, and community shoutouts.

### Opening Pattern
One punchy sentence summarizing the overall feeling, then pivot to specifics:
- *"After thousands of exciting conversations, I survived KubeCon NA 2024."*
- *"KubeCon gets better and better, and this post can quickly become a thank you post for everyone I met last week."*
- *"Last Saturday and Monday, I presented at two Brazilian events."*
- *"Last week, I enjoyed attending, presenting, and sharing extraordinary times with the Spring community at Spring I/O Barcelona."*

### Structure
1. Brief emotional/energetic opening (1–2 sentences)
2. 2–5 thematic sections or event-section breakdowns
3. Named individuals with company/role throughout (generous attribution)
4. Key announcements, milestones, or project news called out
5. Technical observations embedded naturally in narrative
6. Links to slides, recordings, or GitHub repos
7. Forward-looking close ("See you in London," "Looking forward to KubeCon NA")

### Attribution Culture
- Name every person you spoke with, presented with, or learned from
- Always include their affiliation/company/role
- Link their Twitter/X handle when mentioning them
- Shoutouts are not optional — they are part of the post's purpose

### Closing Pattern
Forward reference to next event, or gratitude:
- *"See you all in London! 🇬🇧🫖"*
- *"If you have any questions or comments or want to start contributing to Open Source projects, drop me a comment here or on Twitter."*

---

## Type D: Technical Tutorial

**Examples from corpus:** "Back to basics: APIs to rule them all #1 and #2"

**When to use:** Step-by-step guide to implementing something specific, with working code.

### Opening Pattern
Start with the problem space, not the solution:
- *"Applications require persistent storage to maintain data across restarts. Various database types—relational, key-value, document, and graph—serve different needs. However, developers face challenges..."*

State the problem clearly before introducing any tooling.

### Structure
1. Problem context (what pain this solves, who it's for)
2. Prerequisites list (explicit, numbered)
3. Step-by-step setup with numbered or bulleted instructions
4. Code snippets embedded directly in post (kept short — full impl in GitHub)
5. Shell commands in code blocks
6. Testing/verification section (how to confirm it works)
7. Key takeaway statement
8. GitHub link for complete source code

### Code Block Rules
- Actual working code, not pseudocode
- Shell commands shown exactly as typed
- Dependency coordinates (Maven, npm, etc.) shown in full
- Keep snippets illustrative — link to GitHub for complete implementation
- Always include the import or dependency that makes the snippet work

### Closing Pattern
Summary of what was demonstrated + mandatory GitHub link:
- *"The article demonstrates creating a Spring Boot application using Dapr APIs without introducing unfamiliar tools or complexity. The source code is available at: https://github.com/salaboy/..."*

---

## Type E: Short Announcement / Personal Update

**Examples from corpus:** "New Beginnings, same principles, still pushing for Open Source and Open Standards," "Developer Experience on Kubernetes," "KCD Brazil and SouJava Rio"

**When to use:** Job changes, book launches, project milestones, short event recaps.

### Opening Pattern
The headline is the opening statement. First paragraph amplifies it immediately:
- *"I am hyped to be joining Dash0 as an Ecosystem Engineer because OpenTelemetry is the foundation for understanding agentic systems."*

The hook and the rationale arrive together. Don't build to the announcement.

### Structure
1. One-sentence hook (often echoes the title)
2. Brief personal context (what you were doing before, what changed)
3. Core announcement or observation
4. Belief or reasoning statement (the "why")
5. Forward-looking final sentence

### Closing Pattern
Hopeful, community-facing forward look:
- *"As always, you will see me out in the open, collaborating with and learning from the industry's smartest people."*

---

## Type F: Year-in-Review

**Examples from corpus:** "2023/2024 (Year-in-review)"

**When to use:** Annual retrospective, typically published in late December or early January.

### Opening Pattern
High energy, celebratory:
- *"Wow! What a year it has been!"*

### Structure
1. Enthusiastic opening (one sentence, no hedging)
2. Acknowledgment of scale (talks given, countries visited, books published, etc.)
3. Thematic sections for each major area (talks, book, projects, community)
4. Named individuals and collaborations throughout
5. Honest reflection on what was hard or didn't go as planned
6. Forward-looking close for the new year

### Tone Notes
Year-in-review posts are the most personal. More emotional range is expected and appropriate. Gratitude is explicit and specific, not generic.
