# Real-World Workflows

These are end-to-end workflows you can implement using the examples in this repo.

## Workflow: Triage Failing Tests

1) Run `/test` (or a custom command that includes `!` output from your test runner).
2) Ask `@debug-analyzer` to summarize likely root causes.
3) Switch to `build` to implement the fix.
4) Re-run the command and confirm the fix.

## Workflow: Small Refactor With Guardrails

1) Run `/review-changes` to capture context (`git diff`, `git log`).
2) Ask `@readonly-reviewer` for a refactor plan and risk list.
3) Implement in `build`.
4) Run `/format` and `/test`.

## Workflow: Release Preparation

1) Load `git-release` skill (maintainer-only).
2) Generate release notes and a `gh release create` command.
3) Use `/pr-review` command (or skill) to verify the release branch.
