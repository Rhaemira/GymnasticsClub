# Contributing

Thank you for helping improve Gymnastics Club.

## Repository layout

- `ios/` contains the SwiftUI iPhone/iPad client.
- `backend/` contains the Swift/Vapor API, PostgreSQL migrations, scripts and deployment files.
- `docs/API_CONTRACT.md` is the shared client/server contract.

The standalone repositories are the reviewable upstreams for each component. Make component changes in the corresponding standalone repository first, then synchronize that upstream into this monorepo using the documented Git subtree workflow. Avoid hand-editing a subtree copy: it creates drift and makes future synchronization harder.

## Development standards

- Keep API changes coordinated between the client, backend and shared contract.
- Preserve existing data. Never run destructive migrations or reset a database containing user data.
- Keep credentials, tokens, signing files, local `.env` files and personal Xcode state out of commits.
- Prefer native SwiftUI behavior and small reusable components.
- Keep server authorization and business invariants enforced by the backend/database.
- Add deterministic regression tests for behavior and API contract changes.
- Keep documentation, examples and workflow commands aligned with the actual scripts.

## Validation

For iOS changes, build Debug and Release for the Simulator, run Xcode static analysis, and execute the XCTest suite.

For backend changes, run `swift build` and `swift test` against a disposable PostgreSQL database. Exercise migrations and startup scripts where affected.

For cross-component changes, verify the shared API contract and run both CI workflows.

Do not describe queued or skipped checks as passing. In pull requests, record the exact commands and CI runs that were completed.

## Pull requests

- Use a focused branch and descriptive commit messages.
- Explain user-visible behavior, security impact and data migration implications.
- Link the corresponding standalone-repository PRs when changing a subtree.
- Include screenshots only when captured from the current build and scrubbed of personal data.
- Do not merge until required checks pass and review conversations are resolved.
