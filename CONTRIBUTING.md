# Contributing

Thanks for contributing to `discord-bot`.

## 1) Prerequisites

- Node.js (LTS recommended)
- `pnpm`

## 2) Local Setup

```bash
pnpm install
```

## 3) Required Verification Before PR

```bash
pnpm exec tsc --noEmit
pnpm test
pnpm build
```

If any command fails, fix the issue before requesting review.

## 4) Repository Conventions

- Keep changes minimal and scoped.
- Preserve existing directory boundaries:
  - `src/` runtime
  - `__tests__/` tests
  - `prisma/` schema and migrations
  - `scripts/` tooling/automation
- Add or update tests for behavior changes.
- Do not commit secrets (`.env`, tokens, keys, credentials).

## 5) Branch and Commit Guidelines

- Branch prefixes: `feature/`, `fix/`, `chore/`, `docs/`
- Use imperative commit messages (example: `add dependency review workflow`).
- Keep unrelated changes out of the same commit.

## 6) Pull Request Checklist

- [ ] Scope is clear and limited.
- [ ] Typecheck/test/build pass locally.
- [ ] Tests updated for behavior changes.
- [ ] Docs updated if policy/architecture changed.
- [ ] No secrets or sensitive data included.

## 7) Security Issues

For vulnerabilities, do not open a public issue first.
Follow `SECURITY.md` for private disclosure.
