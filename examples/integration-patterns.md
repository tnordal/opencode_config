# Integration Patterns

This doc shows common ways to combine agents, commands, and skills.

## Pattern: Read-only Review Loop

- Subagent `@readonly-reviewer` has `write/edit` disabled.
- Command `/review-changes` injects `!` shell output (e.g. `git diff`, `git log`).
- Reviewer produces a checklist + suggested diffs; you apply changes with `build`.

Why it works:

- Keeps review separate from implementation.
- Lowers risk of unintended edits.

## Pattern: Safe Git Helper

- Subagent `@git-helper` has granular bash permissions:
  - allow `git status`, `git diff`, `git log`
  - ask for `git push`, `git reset`, `git clean`

Add a command like `/prepare-commit` that asks for:

- `!` output: `git status`, `git diff`, `git log -5`
- A draft commit message and staging plan

## Pattern: Skill-Gated Maintainer Workflow

- Skills like `git-release` and `pr-review` live under `.opencode/skills/`.
- A maintainer agent enables only those skills:

```json
{
  "permission": {
    "skill": {
      "*": "deny",
      "git-release": "allow",
      "pr-review": "allow"
    }
  }
}
```

Why it works:

- Prevents agents from loading broad, unrelated skills.
- Keeps on-demand instructions crisp.

## Pattern: Orchestrator With Task Allowlist

- Primary agent `orchestrator` can only call certain subagents via Task.
- Keep internal helpers `hidden: true` so they do not clutter `@` autocomplete.

Use when:

- You want deterministic delegation.
- You want to prevent the model from calling arbitrary subagents.
