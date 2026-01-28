# Skill Permission Examples

## Global: Allow Most, Deny Internals

```json
{
  "$schema": "https://opencode.ai/config.json",
  "permission": {
    "skill": {
      "*": "allow",
      "internal-*": "deny"
    }
  }
}
```

## Global: Ask For Experimental

```json
{
  "$schema": "https://opencode.ai/config.json",
  "permission": {
    "skill": {
      "*": "allow",
      "experimental-*": "ask"
    }
  }
}
```

## Per-Agent: Maintain a Tight Allowlist

```json
{
  "$schema": "https://opencode.ai/config.json",
  "agent": {
    "maintainer": {
      "description": "Maintainer workflows with controlled skills",
      "mode": "subagent",
      "permission": {
        "skill": {
          "*": "deny",
          "git-release": "allow",
          "pr-review": "allow"
        }
      }
    }
  }
}
```
