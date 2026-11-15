# Platform release checklist

## Source and compatibility

- [ ] Confirm the exact reviewed iOS, backend and monorepo commit SHAs.
- [ ] Confirm the standalone repositories and monorepo subtrees are synchronized.
- [ ] Confirm `docs/API_CONTRACT.md` matches the client and server DTOs.
- [ ] Review migrations for data preservation and upgrade behavior.

## iOS

- [ ] Debug and Release Simulator builds pass.
- [ ] Xcode static analysis and XCTest pass.
- [ ] Physical-device sign-in, restore, offline and sign-out flows pass.
- [ ] All tabs, forms, native swipe actions and Undo behavior pass.
- [ ] VoiceOver, Dynamic Type, Reduce Motion, appearance and iPad layouts are checked.
- [ ] Release API URL is HTTPS.

## Backend

- [ ] Linux/PostgreSQL integration tests pass.
- [ ] Native macOS migration/startup smoke test passes.
- [ ] Docker deployment smoke test passes.
- [ ] Auth, authorization, capacity concurrency and attendance uniqueness are verified.
- [ ] Backup archive and isolated restore drill are verified.
- [ ] Production secrets, database TLS, proxy trust and shared edge rate limiting are configured.

## Approval

Record app version/build, backend release, device/OS versions, CI links and reviewer sign-off. Document known limitations; do not waive failing checks silently.
