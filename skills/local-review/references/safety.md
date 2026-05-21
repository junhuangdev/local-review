# Safety

The CLI is the safety boundary:

- It creates local Gitea repos through the localhost API.
- It adds or updates a `local-review` remote only.
- It injects local credentials into a single Git command using `http.extraHeader`.
- It does not store credentials in project Git config.
- It does not expose commands for GitHub PR creation.
- It stores runtime state under `~/.local/share/local-review` by default.
