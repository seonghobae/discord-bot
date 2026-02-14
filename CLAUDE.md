# CLAUDE

Claude-specific working notes for this repository.

Common repository policies live in `AGENTS.md`.
This file only captures Claude-specific operating notes.

## Mission

Implement safe, minimal, testable changes while preserving repository
boundaries and security posture.

## Repository Boundaries

- `src/`: runtime behavior
- `__tests__/`: tests
- `prisma/`: schema/migrations
- `scripts/`: automation

## Required Local Verification

Run from repository root:

```bash
pnpm install
pnpm exec tsc --noEmit
pnpm test
pnpm build
```

## Guardrails

- Keep changes small and reversible.
- Avoid renaming or refactoring unless required for correctness.
- Never commit secrets or credentials.
- Avoid destructive git operations unless explicitly requested.
- If checks cannot run, report blockers and remaining risk clearly.

## Security

- Follow `SECURITY.md` for vulnerability handling.
- Do not disclose exploit details publicly before maintainer triage.
