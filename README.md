# DSmailes' Skills Marketplace

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

## Installation

### Codex

If you use a Codex plugin marketplace installer, install the plugin directly from this repository:

```bash
npx codex-marketplace add dsmailes/dsmailes-skills-marketplace/plugins/tech-test-coach --plugin
```

Or install the skill manually:

```bash
git clone https://github.com/dsmailes/dsmailes-skills-marketplace.git
mkdir -p ~/.codex/skills
cp -R dsmailes-skills-marketplace/plugins/tech-test-coach/skills/tech-test-coach ~/.codex/skills/
```

Restart Codex, then invoke:

```text
Use $tech-test-coach.
```

### Claude Code

Claude Code supports personal skills in `~/.claude/skills`. Install this skill with:

```bash
git clone https://github.com/dsmailes/dsmailes-skills-marketplace.git
mkdir -p ~/.claude/skills
cp -R dsmailes-skills-marketplace/plugins/tech-test-coach/skills/tech-test-coach ~/.claude/skills/
```

Start Claude Code in a coding challenge repository and invoke:

```text
/tech-test-coach
```

You can also ask naturally for coaching on a coding challenge; Claude Code may load the skill automatically when the request matches the description.

### Claude.ai

Claude.ai custom skills are uploaded as ZIP files. Build a ZIP that contains the skill folder:

```bash
git clone https://github.com/dsmailes/dsmailes-skills-marketplace.git
cd dsmailes-skills-marketplace/plugins/tech-test-coach/skills
zip -r tech-test-coach.zip tech-test-coach
```

In Claude.ai, enable Skills and code execution/file creation, then upload `tech-test-coach.zip` from **Customize > Skills**.

### Cursor, Windsurf, Gemini CLI, and Other Agents

If your agent supports the open `SKILL.md` folder convention, copy this folder into that agent's configured skills directory:

```text
plugins/tech-test-coach/skills/tech-test-coach/
```

If your agent does not support skills yet, use the skill as a prompt pack: attach or paste `SKILL.md` and the relevant files from `references/` into the conversation, then ask the agent to follow those instructions while working in your challenge repo.

## Usage After Installation

Invoke the skill with:

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
