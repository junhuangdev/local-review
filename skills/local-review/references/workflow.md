# Workflow

1. Confirm the project root.
2. Confirm the target repo from `.local-review.json`.
3. Run `local-review up` if the backend is not ready.
4. Run `local-review publish --project <root> --repo <repo>`.
5. Give the user the local PR URL.
6. Wait for review feedback.
7. Update the branch and run publish again.
8. Create a GitHub PR only when the user explicitly asks through the normal
   GitHub workflow.
