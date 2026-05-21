---
name: local-review
description: Use when the user wants local pre-PR review, AI-session change review, localhost-only Gitea review, or to publish branch/worktree changes for local review without creating a GitHub pull request.
---

# local-review

Use the `local-review` CLI for deterministic local review actions. Do not
reimplement Gitea API calls in prompts when the CLI can do the action.

## Rules

- Use local review before GitHub PR when the user asks for AI-session review,
  local review, pre-PR review, or asks to avoid remote PR noise.
- Never create a GitHub PR from this skill.
- Never push to `origin` from this skill.
- Use `local-review publish` to push only to the `local-review` remote.
- Read the project's `.local-review.json` or local review docs for repo names
  and base branches.

## Commands

```bash
local-review up
local-review status
local-review publish --project /path/to/project --repo <repo-name>
local-review list --project /path/to/project
local-review open
```

## Delivery

Report:

- local PR URL
- repo, base branch, and head branch
- changed-file count when available
- whether GitHub was untouched
- rollback command

## References

- `references/workflow.md` for the full workflow.
- `references/safety.md` for hard boundaries.
