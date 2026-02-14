# AGENTS

Operational guardrails for AI coding agents in this repository.

## Scope and Boundaries

- `src/`: production runtime code
- `__tests__/`: tests only
- `prisma/`: schema and migrations
- `scripts/`: tooling/automation

Do not move logic across boundaries without explicit reason.

## Required Verification

Run from repository root before claiming completion:

```bash
pnpm install
pnpm exec tsc --noEmit
pnpm test
pnpm build
```

If something cannot run, report the exact blocker and what remains unverified.

## Safety Rules

1. Make minimal, scoped edits.
2. Preserve naming and structure unless a fix requires change.
3. Never commit secrets, tokens, private keys, or credentials.
4. Avoid destructive git operations unless explicitly requested.
5. Do not revert unrelated user changes.

## Quality Rules

- Add/adjust tests for behavior changes in `src/`.
- Keep Prisma changes synchronized with runtime usage.
- Keep scripts deterministic and non-destructive by default.

## Security Handling

If you find a potential vulnerability, follow `SECURITY.md`.
Do not publish exploit details in public discussion before triage.
