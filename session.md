# Session Handoff

This file is a drop-in handoff note for a new OpenCode session.

## Project

- Workspace: `C:\Users\tnord\sandbox\opencode_config`
- Purpose: learning repo for OpenCode configuration focused on project-local setup of:
  - custom agents
  - custom commands
  - agent skills

This repo intentionally stores examples under `agents/`, `commands/`, and `skills/` for learning, not under `.opencode/`.

## What Exists Now

Core guides (read these first):

- `README.md`
- `agents-guide.md`
- `commands-guide.md`
- `skills-guide.md`

Examples by difficulty:

- Agents:
  - `agents/beginner/`
  - `agents/intermediate/`
  - `agents/advanced/`
- Commands:
  - `commands/beginner/`
  - `commands/intermediate/`
  - `commands/advanced/`
- Skills:
  - `skills/beginner/` (has `README.md` + skill folders)
  - `skills/intermediate/` (has `README.md` + skill folders)
  - `skills/advanced/` (has `README.md` + skill folders)

Integration / patterns:

- `examples/integration-patterns.md`
- `examples/real-world-workflows.md`
- `examples/skill-permission-examples.md`

## Design Constraints Used

- Keep everything project-local (no `~/.config/opencode` guidance required for this repo).
- Do not include `.claude` compatibility examples.
- Skills obey naming + frontmatter rules:
  - `SKILL.md` filename is all-caps
  - `name` matches directory name
  - name regex: `^[a-z0-9]+(-[a-z0-9]+)*$`
  - `description` 1-1024 chars
  - only recognized frontmatter keys: `name`, `description`, `license`, `compatibility`, `metadata`

## Recommended Next Work (Pick One)

1) Make this repo runnable as-is by adding a `.opencode/` mirror
   - Create `.opencode/agents/`, `.opencode/commands/`, `.opencode/skills/`
   - Copy a curated subset of examples into those directories
   - Optionally add a small `opencode.json` to demonstrate:
     - default model
     - a few agents
     - command definitions
     - permissions (`permission.bash` patterns and `permission.skill`)

2) Add a curated “starter pack”
   - A minimal set of:
     - 1 primary orchestrator agent
     - 2-3 subagents (reviewer, git-helper, debug-analyzer)
     - 3-5 commands (`/test`, `/review-changes`, `/pr`)
     - 2 skills (`pr-review`, `git-release`)
   - Provide copy paths into `.opencode/`.

3) Add validation scripts/docs
   - A short checklist (or script) that verifies skill naming and required frontmatter.

## Quick Verification Commands

From `C:\Users\tnord\sandbox\opencode_config`:

```bash
ls -R
```

## Notes

- No git repo is initialized here (as observed earlier). If needed, initialize separately.
- A previous tooling issue (“Tool execution aborted”) happened when writing larger files; using `apply_patch` worked reliably.
