**What changed and why**

- CHANGE: WHY IT WAS MADE

**What may break or change behaviour**

Anything that could change behaviour as a side effect, even with a 0.1% chance. For each: the risk, the expected behaviour, and the user flow that exercises it.

- RISK: EXPECTED BEHAVIOUR. Test: SCREEN/PATH/COMMAND.

**What you learned (human fills this, not the agent)**

Explain what happened here in your own words, and what you learned from it. If you built a login flow, say what a session is. If you fixed a bug, say what the bug was and why it happened. The person who shipped this PR should be able to explain it without reading the code. One line is not enough if the work deserves more.

**Questions I asked the agent**

List the questions you asked about this work before filing the PR. If you asked none, that is a problem: go ask.

**Size**

- [ ] Under ~400 changed lines
- [ ] One thing, atomic
- [ ] The PR title names the lesson, not just the feature

**Verification**

- [ ] I ran the thing and saw it work
- [ ] A different model or human reviewed the diff (2 adversarial subagents)
- [ ] Every architecture/data change the owner read

**Lesson**

- The lesson for `learnings/`: what failed, why, what to do instead (or "nothing worth filing")