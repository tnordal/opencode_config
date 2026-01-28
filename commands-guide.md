# Commands Guide

Custom commands are prompt templates you can trigger in the TUI via `/command-name`.

This repo keeps examples under `commands/` for learning. In a real project, copy command markdown files into `.opencode/commands/` (project-local).

## Where Commands Are Defined

Two supported ways:

1) JSON config (`opencode.json`)
2) Markdown command files

Project-local location for markdown commands:

- `.opencode/commands/<name>.md`

The filename becomes the command name.

## Command Configuration Formats

### JSON (in `opencode.json`)

```json
{
  "$schema": "https://opencode.ai/config.json",
  "command": {
    "test": {
      "template": "Run the full test suite and summarize failures. Suggest fixes.",
      "description": "Run tests",
      "agent": "build",
      "model": "anthropic/claude-3-5-sonnet-20241022"
    }
  }
}
```

### Markdown (in `.opencode/commands/`)

```md
---
description: Run tests and summarize failures
agent: build
model: anthropic/claude-3-5-sonnet-20241022
---
Run the full test suite and summarize failures.
If there are failures, propose a minimal fix.
```

The frontmatter defines properties; the body is the command template.

## Prompt Template Features

### Arguments

Use `$ARGUMENTS` to inject all arguments.

```md
---
description: Create a component
---
Create a React component named $ARGUMENTS.
```

Run:

`/component Button`

Use positional args (`$1`, `$2`, ...):

```md
---
description: Create a file
---
Create file $1 inside $2 with contents: $3
```

Run:

`/create-file config.json src "{ \"key\": \"value\" }"`

### Shell output injection

Use `!` backticks to inject bash output into the prompt:

```md
---
description: Review recent commits
---
Recent commits:
!`git log --oneline -10`

Summarize what changed and flag risks.
```

### File references

Use `@path/to/file` to include file contents:

```md
---
description: Review a component
---
Review @src/components/Button.tsx for performance and correctness.
```

## Options Reference

- `template` (required, JSON only): prompt text.
- Body content (required, Markdown only): prompt text.
- `description` (optional but strongly recommended): shown in command palette.
- `agent` (optional): which agent runs the command.
- `model` (optional): override model for this command.
- `subtask` (optional, boolean): force execution as a subtask session (useful to avoid polluting primary context).

## Built-in Command Overrides

Custom commands can override built-in names (e.g. defining `/help` would replace the built-in one). Prefer unique names unless you intentionally want to replace behavior.
