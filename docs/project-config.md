# Project Configuration

Projects opt in by adding `.local-review.json` at the project root.

```json
{
  "project": "example",
  "repos": [
    {
      "name": "api",
      "path": "api",
      "base": "main"
    }
  ],
  "ignoreWorktrees": ["scenario-*", "runtime-smoke"],
  "githubPrGate": "Only create a GitHub PR after the user explicitly asks for it."
}
```

## Fields

| Field | Purpose |
| --- | --- |
| `project` | Human-readable project id |
| `repos[].name` | Local Gitea repository name |
| `repos[].path` | Path from project root to the Git checkout |
| `repos[].base` | Default review base branch |
| `ignoreWorktrees` | Human/agent guidance for local scans |
| `githubPrGate` | Project-specific external-publish wording |

The config is declarative. It cannot run shell commands.
