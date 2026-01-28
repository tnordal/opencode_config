# Agents Guide

Agents are specialized assistants with their own system prompt, tool access, permissions, and (optionally) model settings.

This repo keeps examples under `agents/` for learning. In a real project, copy agent markdown files into `.opencode/agents/` (project-local).

## Concepts

- Primary agents: the main assistants you switch between (e.g. built-in `build`, `plan`).
- Subagents: specialized helpers invoked via `@name` (and/or by other agents via Task).

Built-in agents (per OpenCode docs):

- `build` (primary): full tool access by default.
- `plan` (primary): restricted by default (commonly `edit` + `bash` set to `ask`).
- `general` (subagent): general purpose, can do multi-step work.
- `explore` (subagent): read-only exploration.

## How To Use Agents

- Switch primary agents in the TUI with Tab (or your configured keybind).
- Invoke subagents by mentioning them: `@reviewer ...`.
- Subagents may create child sessions; use your session navigation keybinds to cycle parent/child sessions.

## Where Agents Are Defined

Two supported ways:

1) JSON config (`opencode.json`)
2) Markdown agent files (recommended for portability)

Project-local location for markdown agents:

- `.opencode/agents/<name>.md`

The filename (without `.md`) becomes the agent name.

## Agent Configuration Formats

### JSON (in `opencode.json`)

```json
{
  "$schema": "https://opencode.ai/config.json",
  "agent": {
    "code-reviewer": {
      "description": "Reviews code for bugs, security, and maintainability",
      "mode": "subagent",
      "model": "anthropic/claude-sonnet-4-20250514",
      "temperature": 0.1,
      "prompt": "You are a code reviewer. Do not make edits; propose improvements.",
      "tools": {
        "write": false,
        "edit": false,
        "bash": false
      }
    }
  }
}
```

### Markdown (in `.opencode/agents/`)

```md
---
description: Reviews code without making changes
mode: subagent
model: anthropic/claude-sonnet-4-20250514
temperature: 0.1
tools:
  write: false
  edit: false
  bash: false
---
You are in code review mode.
Focus on correctness, security, and maintainability.
Provide actionable suggestions and small diffs, but do not edit files.
```

## Options Reference

Key options from the OpenCode docs:

- `description` (required): short purpose statement.
- `mode`: `primary`, `subagent`, or `all` (default: `all`).
- `prompt`: inline string or `{file:./path}` in JSON.
- `model`: `provider/model-id` (e.g. `openai/gpt-5`, `anthropic/...`).
- `temperature`: response randomness (commonly 0.0-0.2 for analysis, higher for brainstorming).
- `maxSteps`: cap agentic iterations (cost control).
- `disable`: disable an agent.
- `hidden`: hide subagent from `@` autocomplete (still invokable programmatically).
- `tools`: enable/disable specific tools (`write`, `edit`, `bash`, `webfetch`, `skill`, and MCP tools like `myserver_*`).
- `permission`: allow/ask/deny for tools that support permissions (notably `edit`, `bash`, `webfetch`, plus `skill` permissions for skills).
- `permission.task`: control which subagents an agent can invoke via Task (glob patterns; last match wins).
- Additional provider options: unknown keys are passed to the provider (e.g. `reasoningEffort`).

## Permissions Deep Dive

### Basic tool permissions

In `opencode.json`, you can set default permissions:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "permission": {
    "edit": "ask",
    "bash": "ask"
  }
}
```

And override per agent:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "agent": {
    "build": {
      "permission": {
        "edit": "allow",
        "bash": "ask"
      }
    }
  }
}
```

### Per-command bash permissions (glob patterns)

You can allow/ask/deny specific bash commands. Put `"*"` first and specific rules after; last match wins.

```json
{
  "$schema": "https://opencode.ai/config.json",
  "agent": {
    "git-helper": {
      "description": "Helps with git operations safely",
      "mode": "subagent",
      "permission": {
        "bash": {
          "*": "ask",
          "git status*": "allow",
          "git diff*": "allow",
          "git log*": "allow",
          "git push*": "ask"
        }
      }
    }
  }
}
```

### Task permissions (which subagents can be invoked)

```json
{
  "$schema": "https://opencode.ai/config.json",
  "agent": {
    "orchestrator": {
      "description": "Delegates work to specialized subagents",
      "mode": "primary",
      "permission": {
        "task": {
          "*": "deny",
          "explore": "allow",
          "code-reviewer": "ask"
        }
      }
    }
  }
}
```

Notes:

- `permission.task` affects Task tool availability for the agent, not whether a user can manually `@mention` a subagent.
- When a rule is `deny`, that subagent is omitted from the Task tool description.

## Model Selection Behavior

- If you do not set `model` for an agent:
  - Primary agents use the globally configured `model`.
  - Subagents default to the model of the primary agent that invoked them.

## Recommended Patterns

- Create at least one read-only reviewer subagent (no `write`/`edit`) for fast safety checks.
- Use `permission.bash` command patterns to make `git push`, `rm`, deploy scripts, etc. require approval.
- Put project-wide permanent rules in instruction files (e.g. `AGENTS.md` / configured `instructions`) and keep skills for on-demand workflows.
