---
name: git-release
description: Draft release notes, propose a version bump, and outline a release command
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: github
---

## What I do
- Collect notable changes since the last tag
- Propose semantic version bump (patch/minor/major) with rationale
- Draft release notes grouped by user impact

## Inputs I need
- The last released tag (or confirmation to infer it)
- Whether you use SemVer and any special rules

## Output
- Proposed version
- Release notes (copy/paste)
- Suggested commands (dry-run safe first)
