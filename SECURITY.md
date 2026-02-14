# Security Policy

## Supported Scope

This policy covers the whole repository, including:

- `src/`
- `__tests__/`
- `prisma/`
- `scripts/`

## Reporting a Vulnerability

Please do not disclose vulnerabilities in public issues or PR threads
before maintainers triage.

Preferred path:

1. Open a private GitHub Security Advisory via the Security tab
   (`Report a vulnerability`).
2. Include reproduction steps, impact, and affected file paths.

If private advisory is unavailable, contact maintainers privately and include:

- title prefix: `[SECURITY]`
- affected branch/commit
- proof of concept or minimal reproduction
- suggested mitigation (if known)

## Triage Targets

- Initial acknowledgment: within 3 business days
- Triage/update: within 7 business days

## Contributor Security Requirements

- Never commit secrets (`.env`, keys, tokens, credentials).
- Treat external input (Discord/API payloads) as untrusted.
- Validate auth/permission paths for admin endpoints.
- Keep dependencies and GitHub Actions updated.

## Security Verification Baseline

```bash
pnpm install
pnpm exec tsc --noEmit
pnpm test
pnpm build
```
