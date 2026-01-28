---
name: commit-format
description: Write concise commit messages focused on the why
license: MIT
compatibility: opencode
metadata:
  audience: developers
  scope: git
---

## What I do
- Suggest a 1-line subject and a short body (when needed)
- Emphasize intent (why) over implementation detail (what)

## Guidelines
- Use imperative mood: "add", "fix", "refactor"
- Keep subject under ~72 chars when possible
- Mention user impact or bug context in the body

## When to ask questions
- If the change spans multiple concerns, ask how to split commits
