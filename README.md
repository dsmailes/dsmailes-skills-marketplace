# Dsmailes' LLM Agent Skills Marketplace

A shareable Codex marketplace containing the `tech-test-coach` plugin and skill.

`tech-test-coach` coaches developers through coding challenges, take-home tech tests, interview debugging tasks, mobile app assessments, and failing-test repositories without immediately giving away the solution.

## What It Does

- Starts in Hint mode when invoked with `Use $tech-test-coach.`
- Reads challenge instructions, tests, protected-file warnings, and project files.
- Detects common mobile stacks: Swift/iOS, Kotlin/Android, Flutter, and React Native.
- Tracks progress with a compact challenge ledger.
- Reviews user diffs and gives feedback without jumping straight to full solutions.
- Supports Exam, Hint, Pairing, and Solution modes.

## Layout

```text
.agents/plugins/marketplace.json
plugins/tech-test-coach/.codex-plugin/plugin.json
plugins/tech-test-coach/skills/tech-test-coach/SKILL.md
plugins/tech-test-coach/skills/tech-test-coach/references/
```

## Usage

After installing or making this marketplace available to Codex, invoke the skill with:

```text
Use $tech-test-coach.
```

The default invocation starts coaching immediately, initializes a progress ledger, and asks one focused first question.

## Development

The skill source lives at:

```text
plugins/tech-test-coach/skills/tech-test-coach/
```

The marketplace entry lives at:

```text
.agents/plugins/marketplace.json
```
