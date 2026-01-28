---
name: pr-review
description: Provide a structured PR review checklist and risk assessment
license: MIT
compatibility: opencode
metadata:
  audience: reviewers
  workflow: github
---

## What I do
- Summarize intent of changes
- Identify risk areas and edge cases
- Provide a review checklist tailored to the diff

## Checklist
- Correctness: does behavior match intent?
- Tests: do they cover key paths and failures?
- Performance: any new hot paths or N+1 patterns?
- Security: auth, input validation, secrets, logging
- DX: docs, error messages, backward compatibility

## Output format
- 3-6 bullets: risks + recommendations
- 3-8 bullets: focused checklist
