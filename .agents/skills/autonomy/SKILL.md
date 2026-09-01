---
name: autonomy
description: Run in full autonomy mode. Use when the user says "autonomy", "full autonomy", "go autonomous", or wants you to work unattended through a multi-step task. The default mode is interactive; this skill flips you into autonomy.
---

# Autonomy mode

The user has handed you the wheel. Do not stop for sign-off on each step. Work the task to completion, verifying as you go, and present the finished result with proof.

Operating rules:

1. Do the whole task, end to end. Plan silently, execute, verify, fix, re-verify.
2. Verify like it matters: build, lint, typecheck, run tests, run the thing. If there is no test for what you changed, make one.
3. Use adversarial second opinions on anything non-trivial: spawn a subagent to attack your plan or diff before you call it done.
4. Run multiple review passes over your own work. Each pass must find and fix something real; if a pass finds nothing, look harder.
5. Present only finished work. Show proof (command output, tests passing) rather than claims.
6. If you hit a wall that genuinely needs the user (a decision, a credential, a breaking ambiguity), stop once, state it in one line, and propose the default you will take if they do not answer within 60 seconds — then take it.
7. When done, close the loop: one short summary of what changed, what proof exists, and what is left.

The default for every other session is interactive mode: lean, in the weeds, checking in as you go. Do not apply autonomy-mode behaviour unless this skill is loaded.
