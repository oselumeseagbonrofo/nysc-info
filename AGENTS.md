# Working here

This repo is the rulebook for a project. Clone it when a project starts,
including when the hackathon whistle blows. It carries the factory workflow:
grilling, taste, lessons, escape hatches, HTML reports, the verification bar,
the debrief, the inquiry log. Everything an agent or a contributor needs is
inside this repo, so it works on any machine with nothing else installed. A
machine-level control plane may also apply on top wherever one exists; this
file wins on conflict.

## Structure

```
project-template/
├── AGENTS.md         # this file: how work flows in this repo
├── TASTE.md          # taste rules, sectioned by stack
├── LEARNINGS.md      # approved lessons, scope-tagged
├── .agents/skills/   # skill store
├── plans/            # pre-implementation plans (HTML)
├── reports/          # post-implementation reports (HTML)
├── debriefs/         # required-reading pages (HTML)
├── inquiries/        # dated working history: changes, questions, answers
├── proofs/           # verifiable artefacts
├── learnings/        # project-specific lessons
└── .github/          # issue templates, PR checklist
```

## Grilling first

On the user's first prompt of what they want, run the **grilling** skill.

- Non-autonomous: drill the user round by round. Ask the whole frontier, give
  your recommended answer for each, wait for answers. Do not act until the
  frontier is empty.
- Autonomous: run grilling anyway. Pick the agreed answers and your
  recommendations as defaults, same diligence, no rushing.

## Taste

Read `TASTE.md` at the start of every session, the one in this repo first,
then the global copy if it exists. On conflict, the project-specific version
wins; the user's explicit instruction wins over both. Rules are sectioned:
General applies in every repo, a stack section applies only when the project
uses that stack. They are checkable yes/no items on a diff. A violation fails
review. New rules land there only with the user's approval.

## Lessons

Read `LEARNINGS.md` at the start of every session, the one in this repo first,
then the global copy if it exists. On conflict, the project-specific version
wins. Format, one lesson: what failed, why it failed, the correct thing to do,
scope (`general` | `stack:<name>` | `project:<name>`). Read lessons whose
scope matches the current work; skip the rest. Captured on the incident, never
on a schedule, no journal. The agent may draft a lesson; the user approves or
kills it. Project-specific lessons stay in `learnings/`, and human
contributors' accounts of what they learned can land there too. Lessons
surface in PRs: title the PR so the learning is visible, touch the diff with
it.

## Escape hatches

These rules are the default, not a cage. The user can opt out per request,
and it must work cleanly: no re-questioning, no added ceremony, no guilt.

- "Just implement this directly, no planning" or similar: skip grilling and
  planning, go build.
- "No html plan for this one": skip the plan artefact, keep the rest of the
  flow.
- "No report for this one" or "skip the report": skip the report and debrief,
  keep the verification.
- "Don't follow the rigorous workflow" or "skip the verification steps":
  relax or skip the named step.
- Any rule in this file or the global control plane is overridable by the
  user's explicit instruction. The user's word beats the rules.

## Talking to the user

Optimise for the human reading the end of your message. No one reads the
chit-chat mid-task. Every status line, decision, finding, and proof lands at
the end, in order of importance. Important things never sit in the middle
where they get lost.

The user's own words are the strongest signal, and they are only worth as much
as you can still see them. Inspect the conversation history when intent is
unclear, after compaction, or when a user message read like it mattered and
the current context thinned it. The value is mostly in the user messages. To
do this, always spin up a subagent that figures out how sessions are stored,
how the provider separates user messages from model messages, pulls whatever
is needed, and reports it back. Provider and harness specifics live in that
subagent prompt, never in this file.

## Working in parallel

Prefer background subagents so the main thread keeps moving while reviews,
research, and design ideas run alongside. When a subagent does not block the
next step, run it in the background and work on something else. When several
independent subagents are needed, launch them together.

## Verification

The bar is high and it is about verification, not tests. Tests are welcome
where a project has a test setup; not every project has one, and writing tests
is never a checkbox. What is always required: prove the thing works before you
present it. Be sure.

Before presenting anything:

1. Self-review the diff against the task. Fix what does not satisfy the request.
2. Run the checks that exist (lint, typecheck, tests) and run the thing.
3. Show proof: real command output, a running app, a screenshot. Not claims.
4. If something cannot be proved yet, say so plainly. Never leave it silent.
5. A change with a test setup but no coverage on the new path gets coverage.
   Follow the existing test pattern.

Quality bar, in order: correct, verified, then clean. No-slop means no
presenting work you have not run.

## Adversarial judgment

Subagents are the review force. Use them on judgment-worthy work. Never
self-review alone at the end: your own review finds your own blind spots.

- Code review after implementation: 2 adversarial review subagents. Give each
  the diff and the task. Aggregate their findings, fix, re-run until clean.
  One of the two must read as though it distrusts the writer.
- Plans: 2 adversarial reviewers review the plan before you present it as
  HTML. Same deal: findings in, fix, then present.
- For greenfield code, a reviewer applies `codebase-design` to the shape.
- Your writer's model never reviews alone. A different model always sees the
  work.

Reviewers are not infallible. Treat every finding as a claim, not a verdict:
verify it against the current code before fixing, and fix only what is
actually broken. If a review contradicts what you can see in the file, the
file wins. And reviewers drift: a suggestion can lead outside the user's
request. That is scope creep regardless of who proposed it. The main agent
owns the scope; if a finding does not serve the brief, note it and move on.

## Design

Every design task, without exception, loads the **frontend-design** skill. No
design ships without it.

- Get design ideas from 2 subagents minimum. Aggregate their ideas, pick the
  deliberate combination, do not average them into blandness.
- After you build the design, 2 subagents critique it against the brief.
  Address the findings. Not all critiques are right, but each gets answered.
- The brief's own words win. Where the brief leaves an axis free, spend it on
  a choice specific to the subject, not a default look.
- Verify the design renders: screenshots or DOM checks with `agent-browser`,
  not vibes.

## After implementation

Every implementation ends with two HTML pages:

**The report** (technical, complete, under `reports/`). Covers:

1. What changed and why.
2. What the user should test manually: the exact user flows, paths, screens,
   commands. Cover both what changed directly and anything that could have
   changed behaviour as a side effect, even with a 0.1% chance. State the
   expected behaviour for each.
3. Proof as a section in the report, clearly written: what ran, what passed,
   what was verified, with real command output pasted in. Proof is a section,
   never a separate `.md` file. If a thing cannot be proved yet, say so.

**The debrief** (required reading, under `debriefs/`). Plain-language, written
with unslop, what happened and why it matters. The "what" is for everyone,
including non-devs. The "why" is for the devs and the ones studying to be.
A human who was not in the session reads the debrief and understands the
project one level deeper. The human fills their own account of what they
learned; the agent leaves the space for it, it does not write that part.

Every implementation includes one of each, including the final wrap-up. The
chat gets a short summary, never the two pages as plain text. Give the user
one copy-paste line: "Paste this into your browser to read the report:
`file:///...`". A claim without a test path is not done.

## The inquiry log

`inquiries/` holds the working history: what changed in the session, the
user's questions and their answers, follow-ups, dead ends worth remembering.
Every file carries timestamps (date and time) in its name and in its body, so
agents can grep and filter out what is outdated. Never append to a stale file;
start a new dated one.

## Plans

- Plans (pre-implementation) are HTML under `plans/`.
- A plan is done when it has a build order and a break-it test.
- 2 adversarial reviewers pass over the plan before it becomes HTML.
- Write the plan from the brief: what we are building, constraints, why this
  path, build order, what to test, break-it test, open questions. No template
  file. The structure comes from the brief, not from a form.

## Artefacts

- Plans, reports, debriefs, and proofs are opened with `file://` URLs in the
  browser, never `xdg-open`.
- Proofs must be replayable: a command the user can paste, a file:// URL they
  can open, or a deterministic program. A video beats a screenshot beats a
  claim.
- Every report links back to its plan and its debrief; every debrief names its
  report; every plan says how it will be proved.
- When an artefact is ready, tell the user in one short line they can copy and
  paste: "Paste this into your browser to read the plan:
  `file:///abs/path/plan.html`". Give the exact path; no prose that hides it.

## Writing

Do not write like a model. Load the **unslop** skill and apply it to every
piece of writing that reaches a human or another agent: chat replies, plans,
reports, debriefs, proofs, docs, commit messages, subagent prompts. Cut filler
words, hedging, and enthusiasm. State the thing once. No em dashes, no curly
quotes, no emojis unless asked. If a sentence could sit unchanged in any other
project's docs, rewrite it or cut it. Self-audit before presenting.

## How work flows

1. Grill. Settle the design tree (see above) before any build.
2. Plan. Write the plan as designed HTML, have it adversarially reviewed, save
   to `plans/`. A plan is done when it has a build order and a break-it test.
3. Spec the slot. Each unit of work is a written issue: what it should do, how
   to know it works, what file it touches, with a test in place or clearly
   described. Write issues in plain language so a non-dev can own the "what"
   while agents write the "how".
4. Implement. For critical work, the failing test exists before the code and
   the implementer cannot touch it. Small, reviewable changes: under ~400
   changed lines unless the user says otherwise.
5. Verify. Run the thing. Be sure it works. For UI, use `agent-browser` live
   and capture proof into `proofs/`.
6. Report. Write the report and the debrief as designed HTML, save to
   `reports/` and `debriefs/`. Proof lives as a section in the report. Log
   the session in `inquiries/` with timestamps.
7. Review. Two adversarial review subagents pass over the work; a different
   model from the writer's must see it. Aggregate findings, fix, re-run until
   clean. Learnings show in the PR title and the diff.
8. Learn. Draft the lesson with a scope, get approval or a kill.

## The verification bar

The user runs at a high bar on his own repos. It carries here:

- Approval before work: acceptance criteria approved before code exists.
- Size: no change that can't be reviewed in one sitting (~400 lines, 60-90
  min).
- Two-model review: separate model reviews before merge.
- The user reads every diff that touches architecture or data. Make it
  possible for them to do that in the time they have: proof over claims,
  replayable artefacts.

## Editing this template

The template is a starting point, not a straitjacket. Change anything that
breaks on first use, and commit the fix so the next clone is better.