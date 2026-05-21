# Gitea Boundary

Gitea is an external runtime dependency used as a local review backend.

`local-review` does not vendor or fork Gitea. It starts a pinned Docker image
and talks to Gitea through Git and the Gitea HTTP API.

## Default Runtime

| Item | Value |
| --- | --- |
| Image | `gitea/gitea:1.26.1` |
| Web bind | `127.0.0.1:3300` |
| SSH bind | `127.0.0.1:3222` |
| Data | `~/.local/share/local-review/gitea` |
| Database | SQLite |
| Actions | disabled |
| Registration | disabled |

## Safety Boundary

- Gitea is localhost-only.
- Runtime data is outside project repositories.
- The CLI adds or updates only a `local-review` Git remote.
- The CLI never pushes to `origin`.
- The CLI has no GitHub PR creation command.
