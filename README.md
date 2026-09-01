# project-template

Clone this when a new project starts, especially when the hackathon whistle
blows. It is a standalone factory: grilling, taste, lessons, escape hatches,
HTML reports, the debrief, the inquiry log, the verification bar, all
self-contained.

## Why this exists

Every new project started with an agent that knew none of the rules. I
re-explained how I work from scratch each time, and each retelling lost bits.
This repo fixes that: the rules live in one file, get symlinked into every
harness, and get cloned into every new project.

Two calls I made early and won't undo.

No templates. Blank forms made the agent lazy. Every page came out looking
like every other page, because it was asked to. Now the rules say how to
write; the page gets designed fresh each time, or it doesn't get made.

Proof over "it works". I stopped accepting that phrase. Every implementation
lands with a report you can run yourself, and a debrief in plain language
that ends with a blank for what I learned. The agent never writes that part.

## What's inside

- AGENTS.md: how work flows in a freshly cloned project (grilling first,
  taste, lessons, escape hatches, HTML reports, verification bar)
- TASTE.md: how I write code, sectioned by stack. General rules apply
  everywhere, stack sections only in that stack
- LEARNINGS.md: lessons store with scope tags, so a React lesson never leaks
  into a Go project
- .agents/skills/: the skills (unslop, frontend-design, grilling, and the
  rest), mirrored so they survive any machine
- .github/: work-slot and bug issue templates, PR checklist
- plans/, reports/, debriefs/, inquiries/, proofs/, learnings/: the artefact
  folders

## Start

Clone, rename, commit the template state so the real history starts clean,
then open the first issue.