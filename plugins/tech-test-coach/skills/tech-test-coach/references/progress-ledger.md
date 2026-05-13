# Progress Ledger

Use this reference when the user wants close progress tracking through a coding challenge.

## Ledger Principles

- Keep status evidence-based.
- Separate "attempted" from "verified".
- Keep "done" meaningful: visible tests pass, manual repro is fixed, or the user accepts the remaining risk.
- Track hidden-evaluator risk separately from visible-test status.
- Preserve the user's agency: show progress and the next move, not a giant solution plan.

## Status Definitions

- `not started`: Read enough to identify the task, but no investigation yet.
- `investigating`: Gathering symptoms, code paths, tests, or reproduction steps.
- `hypothesis`: A plausible cause has been named, but no patch or decisive experiment yet.
- `attempted`: The user made a change, but verification is incomplete or failing.
- `blocked`: Progress needs missing context, a failing environment, or a user decision.
- `verified`: The targeted check passes, but broader challenge criteria may remain.
- `done`: The task's success criteria are satisfied with acceptable residual risk.

## Compact Format

```text
Progress
- <task>: <status> | Evidence: <short fact> | Next: <one action>
- <task>: <status> | Evidence: <short fact> | Risk: <short risk>
```

## Detailed Format

Use this only when the user asks for a fuller checkpoint:

```text
Task: <name>
Status: <status>
Contract: <what success requires>
Evidence: <test, output, repro, or diff>
Hypothesis: <current explanation>
Next move: <one action>
Risk: <hidden-test/protected-file/regression risk>
```

## Update Triggers

Update the ledger:

- after reading challenge instructions
- after identifying a failing test or bug
- after the user states a hypothesis
- after reviewing a diff
- after a test, build, or manual verification
- before switching to another task
- at the end of a session

## End-Of-Session Summary

End a coaching session with:

- completed tasks
- current active task and hypothesis
- exact next command or observation
- known risks
- files touched by the user, if relevant
