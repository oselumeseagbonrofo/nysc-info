# Taste

The taste rules for this project. Read them at session start. If a copy of
taste rules lives at machine level, read that too; on conflict, this
project-specific file wins, and the user's explicit instruction wins over
both. These rules ship with the template because the owner's taste is a
quality bar, not a secret.

Rules are sectioned so a React rule never becomes noise in a Go project. Every
repo applies the General rules. A stack section applies only when the project
uses that stack. When in doubt about the stack, ask.

Rules are checkable yes/no items on a diff. A rule is added only with the
user's approval. Violating a rule fails review.

## General, every repo

1. No bare type casting. Data entering the app goes through a schema
   (ArkType/zod), never `as`. Runtime data is validated or it does not exist.
2. Failure cases first. The error path and the edge cases exist before the
   happy path. Code that only handles success is unfinished.
3. Deep modules. A module has a tiny interface and deep implementation. No
   modules without a clear boundary. Framework projects get their own
   judgment, added to the right section when ratified.

## React / TypeScript, only in React/TS projects

4. Small components that make sense. A React component does not live past the
   size where it is hard to read. Split into parts that carry meaning.
5. No effect spam. State is typed first, `useEffect` is the last resort, not
   the first instinct. Write code by thinking about the process that produces
   the output, not by rushing to completion.

## How rules get written

When the user calls out a pattern they hate in agent output, that is a draft
rule. Draft it as: name, which section it belongs in (general or a stack), why
it is wrong, the checkable yes/no. Present it for approval. Approved rules
land here verbatim in the right section.