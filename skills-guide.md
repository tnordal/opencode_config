# Skills Guide

Skills are reusable instructions discovered by OpenCode and loaded on-demand via the `skill` tool.

This repo keeps skill examples under `skills/` for learning. In a real project, copy skills into `.opencode/skills/<skill-name>/SKILL.md` (project-local).

## Skill File Layout

One folder per skill, containing `SKILL.md`:

`<config-root>/skills/<name>/SKILL.md`

Project-local for OpenCode:

- `.opencode/skills/<name>/SKILL.md`

## Discovery Behavior (Project-Local)

OpenCode walks up from your current working directory until it reaches the git worktree. Along the way, it loads matching `.opencode/skills/*/SKILL.md`.

## Frontmatter Requirements

`SKILL.md` must start with YAML frontmatter. Only these fields are recognized:

- `name` (required)
- `description` (required)
- `license` (optional)
- `compatibility` (optional)
- `metadata` (optional map of string->string)

Unknown fields are ignored.

## Skill Name Rules

`name` must:

- be 1-64 characters
- be lowercase alphanumeric with single hyphen separators
- not start/end with `-`
- not contain `--`
- match the directory name that contains `SKILL.md`

Regex equivalent:

```
^[a-z0-9]+(-[a-z0-9]+)*$
```

`description` must be 1-1024 characters.

## Example Skill

```md
---
name: git-release
description: Create consistent releases and changelogs
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: github
---

## What I do
- Draft release notes from merged PRs
- Propose a version bump
- Provide a copy-pasteable `gh release create` command

## When to use me
Use this when preparing a tagged release.
Ask clarifying questions if the versioning scheme is unclear.
```

## How Agents See Skills

OpenCode lists available skills in the `skill` tool description (name + description). Agents can load one skill at a time by calling:

```js
skill({ name: "git-release" })
```

## Permissions

### Global skill permissions (in `opencode.json`)

```json
{
  "$schema": "https://opencode.ai/config.json",
  "permission": {
    "skill": {
      "*": "allow",
      "internal-*": "deny",
      "experimental-*": "ask"
    }
  }
}
```

### Per-agent override

For custom agents (markdown frontmatter):

```md
---
description: Maintainer helper with safe skills
mode: subagent
permission:
  skill:
    "*": deny
    "git-release": allow
---
```

For built-in agents (in `opencode.json`):

```json
{
  "$schema": "https://opencode.ai/config.json",
  "agent": {
    "plan": {
      "permission": {
        "skill": {
          "internal-*": "allow"
        }
      }
    }
  }
}
```

### Disable the skill tool

Disable skill usage entirely:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "agent": {
    "plan": {
      "tools": {
        "skill": false
      }
    }
  }
}
```

## Troubleshooting

- Ensure the filename is exactly `SKILL.md` (all caps).
- Ensure frontmatter includes `name` and `description`.
- Ensure the directory name matches `name`.
- Check `permission.skill`: skills set to `deny` are hidden from the agent.
