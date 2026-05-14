# DSmailes' Skills Marketplace

A shareable Codex marketplace containing the `codebase-quiz` and `tech-test-coach` plugins and skills.

`codebase-quiz` quizzes developers on a repository with three adaptive questions, scores their answers, and gives feedback to build codebase awareness without letting the agent do all the learning work.

`tech-test-coach` coaches developers through coding challenges, take-home tech tests, interview debugging tasks, mobile app assessments, and failing-test repositories without immediately giving away the solution.

## What It Does

- `codebase-quiz`
  - Starts an interactive 3-question quiz when invoked with `Use $codebase-quiz.`
  - Reads repository docs, manifests, tests, entry points, and core modules.
  - Asks questions one at a time about structure, flow, and risk.
  - Scores each answer and gives focused feedback plus study targets.
  - Avoids editing files or dumping answers before the user attempts the question.

- `tech-test-coach`
  - Starts in Hint mode when invoked with `Use $tech-test-coach.`
  - Reads challenge instructions, tests, protected-file warnings, and project files.
  - Detects common mobile stacks: Swift/iOS, Kotlin/Android, Flutter, and React Native.
  - Tracks progress with a compact challenge ledger.
  - Reviews user diffs and gives feedback without jumping straight to full solutions.
  - Supports Exam, Hint, Pairing, and Solution modes.

## Layout

```text
.agents/plugins/marketplace.json
plugins/codebase-quiz/.codex-plugin/plugin.json
plugins/codebase-quiz/skills/codebase-quiz/SKILL.md
plugins/tech-test-coach/.codex-plugin/plugin.json
plugins/tech-test-coach/skills/tech-test-coach/SKILL.md
plugins/tech-test-coach/skills/tech-test-coach/references/
```

## Installation

### Codex

If you use a Codex plugin marketplace installer, install the plugin directly from this repository:

```bash
npx codex-marketplace add dsmailes/dsmailes-skills-marketplace/plugins/codebase-quiz --plugin
npx codex-marketplace add dsmailes/dsmailes-skills-marketplace/plugins/tech-test-coach --plugin
```

Or install the skill manually:

```bash
git clone https://github.com/dsmailes/dsmailes-skills-marketplace.git
mkdir -p ~/.codex/skills
cp -R dsmailes-skills-marketplace/plugins/codebase-quiz/skills/codebase-quiz ~/.codex/skills/
cp -R dsmailes-skills-marketplace/plugins/tech-test-coach/skills/tech-test-coach ~/.codex/skills/
```

Restart Codex, then invoke:

```text
Use $codebase-quiz.
Use $tech-test-coach.
```

### Claude Code

Claude Code supports personal skills in `~/.claude/skills`. Install this skill with:

```bash
git clone https://github.com/dsmailes/dsmailes-skills-marketplace.git
mkdir -p ~/.claude/skills
cp -R dsmailes-skills-marketplace/plugins/codebase-quiz/skills/codebase-quiz ~/.claude/skills/
cp -R dsmailes-skills-marketplace/plugins/tech-test-coach/skills/tech-test-coach ~/.claude/skills/
```

Start Claude Code in a repository and invoke:

```text
/codebase-quiz
/tech-test-coach
```

You can also ask naturally for a codebase quiz or coding challenge coaching; Claude Code may load the matching skill automatically when the request matches the description.

### Claude.ai

Claude.ai custom skills are uploaded as ZIP files. Build ZIPs that contain the skill folders:

```bash
git clone https://github.com/dsmailes/dsmailes-skills-marketplace.git
cd dsmailes-skills-marketplace
cd plugins/codebase-quiz/skills
zip -r codebase-quiz.zip codebase-quiz
cd ../../tech-test-coach/skills
zip -r tech-test-coach.zip tech-test-coach
```

In Claude.ai, enable Skills and code execution/file creation, then upload the generated skill ZIP from **Customize > Skills**.

### Cursor, Windsurf, Gemini CLI, and Other Agents

If your agent supports the open `SKILL.md` folder convention, copy this folder into that agent's configured skills directory:

```text
plugins/codebase-quiz/skills/codebase-quiz/
plugins/tech-test-coach/skills/tech-test-coach/
```

If your agent does not support skills yet, use the skill as a prompt pack: attach or paste `SKILL.md` and the relevant files from `references/` into the conversation, then ask the agent to follow those instructions while working in your challenge repo.

## Usage After Installation

Invoke the skill with:

```text
Use $codebase-quiz.
Use $tech-test-coach.
```

The default `codebase-quiz` invocation inspects the repository, asks three questions one at a time, scores each answer, and ends with study targets.

The default `tech-test-coach` invocation starts coaching immediately, initializes a progress ledger, and asks one focused first question.

## Development

The skill sources live at:

```text
plugins/codebase-quiz/skills/codebase-quiz/
plugins/tech-test-coach/skills/tech-test-coach/
```

The marketplace entry lives at:

```text
.agents/plugins/marketplace.json
```
