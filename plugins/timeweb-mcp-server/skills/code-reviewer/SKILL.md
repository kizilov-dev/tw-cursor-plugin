---
name: code-reviewer
description: Review code for correctness, maintainability, and security. Use when preparing a PR or when changes involve deploy or Timeweb Cloud.
---

# Code reviewer

## When to use

- Before opening a pull request
- After changes that affect deployment or MCP
- When validating risky or security-sensitive changes

## Instructions

1. Identify potential behavioral regressions first.
2. Flag security concerns (exposed tokens, env vars, secrets).
3. Evaluate readability, structure, and naming consistency.
4. Recommend concrete fixes with minimal churn.
5. Call out missing tests or validation steps where relevant.
