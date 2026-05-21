# local-review

`local-review` is a localhost-only review workflow for AI-assisted development.

It gives agents and humans a stable CLI for creating local, PR-like review
requests without creating a GitHub pull request. The default backend is a
Dockerized Gitea instance running on `127.0.0.1`.

## What It Owns

- Start and stop a local Gitea review backend.
- Keep Gitea runtime data in a user-level state directory.
- Add a local-only Git remote named `local-review`.
- Push selected base/head branches to the local backend.
- Create or update local pull requests through the Gitea API.
- Open and list local review requests.

## What It Does Not Own

- It does not push to `origin`.
- It does not create GitHub pull requests.
- It does not modify project source files during publish.
- It does not run project tests.
- It does not replace a project's release or task workflow.

## Requirements

- Bash
- Git
- Docker with Docker Compose v2
- `curl`
- `jq`
- `openssl`

## Quick Start

```bash
./bin/local-review up
./bin/local-review status
./bin/local-review publish --project /path/to/project --repo my-repo
./bin/local-review list --project /path/to/project
./bin/local-review open
```

Project-specific facts live in `.local-review.json` at the project root.
See [`examples/brandklout.local-review.json`](examples/brandklout.local-review.json).

## Install

```bash
mkdir -p ~/.agents/tools ~/.local/bin
cp -R /path/to/local-review ~/.agents/tools/local-review
ln -sf ~/.agents/tools/local-review/bin/local-review ~/.local/bin/local-review
```

## Runtime Layout

By default, runtime state lives under:

```text
~/.local/share/local-review/
```

This directory contains Gitea data, generated Compose files, credentials, and
logs. It is intentionally outside every project repository.

## Gitea Dependency

Gitea is an external runtime dependency. It is not vendored into this project.
The default pinned image is:

```text
gitea/gitea:1.26.1
```

See [`docs/gitea-boundary.md`](docs/gitea-boundary.md).
