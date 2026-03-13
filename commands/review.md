---
description: Expert code review of git changes or a PR
allowed-tools: Read, Glob, Grep, Bash(git:*), Bash(gh:*), Bash(rg:*), Skill
argument-hint: [PR-number or PR-URL]
---

Use the `code-review-expert` skill to perform a structured code review.

**Target**:
- If the user provides `$1` (a PR number or URL), first run `gh pr diff $1` to get the diff, then review it.
- Otherwise, review the current unstaged + staged git changes.
