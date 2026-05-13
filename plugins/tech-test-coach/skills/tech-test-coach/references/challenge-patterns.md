# Challenge Patterns

Use this reference to classify the challenge and choose coaching prompts.

## Repository Recon

Start with:

- README or task instructions
- tests and fixtures
- comments containing "DO NOT MODIFY", "protected", "task", "TODO", "FIXME", "bug", "crash", or "challenge"
- package, project, or workspace files that reveal the test runner
- recent failing output from the user

Ask the user to predict where the failure lives before showing exact code.

## Common Challenge Types

### Failing Tests

Coach toward reading the assertion as a contract:

- What behavior does the test name promise?
- What are the expected values and timing constraints?
- Which production method is under test?
- Is the test checking shape, ordering, uniqueness, timing, errors, or side effects?

Hint progression: test name -> assertion -> fixture -> production path -> patch shape.

### Debugging Or Bug Hunt

Coach toward reproduction and isolation:

- What is the smallest way to trigger the bug?
- What changed in state immediately before the symptom?
- Which object owns that state?
- Is this a lifecycle, identity, threading, caching, parsing, or boundary problem?

Hint progression: reproduce -> suspect area -> ownership/data flow -> exact faulty assumption.

### UI Challenge

Coach toward observable behavior:

- Is the bug layout, navigation, state, identity, async loading, accessibility, or lifecycle?
- Does the issue appear on first load, after mutation, after navigation, or after refresh?
- Is the view creating model objects repeatedly?
- Is the UI using stable identity for repeated rows?

Favor screenshots, previews, simulator steps, and narrow state probes.

### Concurrency Challenge

Coach toward contracts:

- Must work happen in parallel or sequence?
- Which primitive is required: callbacks, promises/publishers, async/await, locks, actors, tasks?
- How are errors, cancellation, ordering, and completion handled?
- How does the test prove parallelism: timeout, timestamps, expected order, or call counting?

Push the user to explain completion semantics before editing.

### Performance Or Memory

Coach toward measurement:

- Can the user reproduce growth, slowness, repeated work, or retained objects?
- Which closure, subscription, timer, task, cache, or observer might retain something?
- Does the fix remove work, move work, debounce work, or break a retain cycle?

Avoid speculative rewrites until there is an observation.

### Architecture Or Refactor

Coach toward preserving behavior:

- What public contract must not change?
- What is the smallest refactor that exposes a seam for tests?
- Are hidden tests likely to rely on names, APIs, or file boundaries?

Prefer incremental refactors with tests after each step.

## Feedback Templates

Use these short prompts:

- "What is the contract this test is enforcing?"
- "What would you expect to happen if this work were sequential?"
- "Which line creates ownership, and which line releases it?"
- "Can you name the one assumption this function makes?"
- "What would be the smallest experiment to disprove that?"
- "Good. Now check the hidden-test angle: did the public API change?"

## Solution Mode Checklist

Before implementing directly:

- Confirm the user requested solution mode.
- Record protected files and sections.
- Keep changes localized.
- Run the narrowest verification first.
- Then run broader tests when available.
- Explain the fix as a debugging lesson, not just a diff.
