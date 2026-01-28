---
name: security-audit
description: Threat-driven security review focusing on trust boundaries and exploitability
license: MIT
compatibility: opencode
metadata:
  audience: security
  scope: code
---

## What I do
- Identify trust boundaries (user input, network, filesystem, secrets)
- Look for injection, authz gaps, and sensitive data exposure
- Recommend fixes prioritized by exploitability and blast radius

## What I need
- Entry points (HTTP handlers, CLI args, jobs)
- Data stores and credential paths
- Deployment context (single-tenant vs multi-tenant)

## Output
- Findings with severity and suggested remediation
- Concrete examples of exploitation paths when applicable
