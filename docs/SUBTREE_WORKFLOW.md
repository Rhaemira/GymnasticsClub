# Synchronizing component repositories

The standalone repositories are the upstreams:

- iOS: `https://github.com/Rhaemira/GymnasticsClubApp`
- Backend: `https://github.com/Rhaemira/GymnasticsClubBackend`

This repository stores them under `ios/` and `backend/` using Git subtree history. Do not copy folders manually or force-push rewritten subtree histories.

## Configure remotes

Run once in a local clone of this monorepo:

```bash
git remote add ios-upstream https://github.com/Rhaemira/GymnasticsClubApp.git
git remote add backend-upstream https://github.com/Rhaemira/GymnasticsClubBackend.git
git fetch ios-upstream
git fetch backend-upstream
```

## Pull reviewed component changes

After the corresponding standalone PR has been reviewed and its intended branch is ready to synchronize:

```bash
git subtree pull --prefix=ios ios-upstream engineering/secure-integrated-overhaul
git subtree pull --prefix=backend backend-upstream engineering/secure-integrated-overhaul
```

Run only the subtree pull for the component that changed. Resolve conflicts deliberately; do not use `--squash` if preserving the existing subtree history is required.

## Validate the synchronized tree

```bash
git diff --check
git status --short
```

Then run the relevant iOS and backend validation described in the root README. Confirm the root `docs/API_CONTRACT.md` agrees with both component implementations.

## Important

The component branches may contain changes not yet merged into their standalone `main` branches. Synchronize the reviewed feature branch explicitly, and do not merge either component PR merely to make the monorepo update possible. The monorepo should retain a clear audit trail of each subtree pull.
