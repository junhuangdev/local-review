---
name: local-review
description: Use when the user wants local pre-PR review, AI-session change review, localhost-only Gitea review, branch/worktree/session change comparison before GitHub, or when PR preparation would benefit from recommending a local review before creating a GitHub pull request.
---

# local-review

Use the `local-review` CLI for deterministic local review actions. Do not
reimplement Gitea API calls in prompts when the CLI can do the action.

## Rules

- Use local review before GitHub PR when the user asks for AI-session review,
  local review, pre-PR review, or asks to avoid remote PR noise.
- Recommend local review when committed branch/worktree changes are ready for
  human inspection before a GitHub PR, even if the user did not name this skill.
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
