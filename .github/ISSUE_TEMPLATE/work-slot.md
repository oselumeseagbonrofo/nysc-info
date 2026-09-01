---
name: Work slot
about: A unit of work a human or agent can pick up and finish
title: ''
labels: 'help wanted'
assignees: ''

---

**The what, exactly**

One plain-language sentence: what the finished thing must do, from the user's side. Name the behaviour, not the mechanism. If you cannot write it in one sentence, the slot is two slots.

Example: "Signing in with a GitHub account creates a user and lands on the dashboard."

**How to know it works**

The acceptance check: a command to run and what it must print, or a behaviour to observe and what it must look like.

**The boundary**

What this slot does NOT do. One line each. Anything outside the boundary is a different slot.

**What file it touches**

The narrowest path(s). If it is more than a couple of files, the slot is too big. Mark "unknown" and let the implementer find it.

**Test**

The test that exists or must exist before the code. Failing first, unchangeable by the implementer.