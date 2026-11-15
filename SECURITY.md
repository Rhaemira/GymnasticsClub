# Security policy

## Reporting

Do not publish credentials, exploit details, personal data or production logs in public issues. Use GitHub's private vulnerability reporting feature where enabled. Otherwise contact the maintainer privately through GitHub.

Include the affected commit, impact, reproduction steps and a safe proof of concept. Never include live passwords, bearer tokens, database dumps or signing credentials.

## Security expectations

- Production API traffic must use HTTPS.
- Passwords are hashed by the backend; bearer tokens are stored in the iOS Keychain and only token digests are persisted by the backend.
- Authorization and business invariants are enforced server-side.
- Keep database credentials and deployment secrets outside source control.
- Treat client input and API responses as untrusted.
- Use a dedicated least-privilege database role and tested backups.
- Do not trust forwarding headers unless they are supplied by an explicitly trusted immediate proxy.
