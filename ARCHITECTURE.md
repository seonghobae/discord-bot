# Architecture

Last updated: 2026-02-14

## 1) System Overview

This repository contains a TypeScript Discord bot service that runs:

- a Discord gateway client (`src/bot/`)
- an Express HTTP API (`src/api/`)
- Prisma-backed persistence (`src/infrastructure/persistence/`, `prisma/`)

The app starts from `src/index.ts`, initializes configuration from
`src/config.ts`, boots the bot, and serves API routes under
`/api/discord`.

## 2) Runtime Entry Points

- `src/index.ts`: process entrypoint; starts bot and Express server.
- `src/bot/index.ts`: initializes Discord client, event handlers, and DB connection.
- `src/api/routes/migrationRoutes.ts`: migration/status/channel/health routes.

## 3) Source Layout

- `src/domain/`: entities and repository/service interfaces.
- `src/application/`: use-cases and orchestration logic.
- `src/infrastructure/`: adapters for Discord and Prisma.
- `src/services/`: legacy service layer (still present).
- `src/utils/`: utility modules (including Prisma connection helpers).
- `__tests__/`: unit/integration tests for application, bot, API, and services.
- `prisma/schema.prisma`: DB schema.
- `prisma/migrations/`: migration history.
- `scripts/`: maintenance/dev scripts.

## 4) Dependency Boundaries

- Domain should remain free of framework-specific dependencies.
- Application can depend on domain contracts.
- Infrastructure adapts external systems and implements
  domain/application interfaces.
- Tests in `__tests__/` can depend on runtime code, but runtime code must
  not import test helpers.

## 5) External Integrations

- Discord API via `discord.js`
- PostgreSQL via Prisma (`@prisma/client`, `prisma`)
- HTTP API via Express

Configuration is sourced from environment variables in `src/config.ts`
(for example `DISCORD_TOKEN`, `DATABASE_URL`, `API_SECRET_KEY`).

## 6) Verification Baseline

Run from repository root:

```bash
pnpm install
pnpm exec tsc --noEmit
pnpm test
pnpm build
```

## 7) Change Management Expectations

- If you change module boundaries or entrypoint flow, update this file.
- If you change API behavior, update tests under `__tests__/api/`.
- If you change data models, update `prisma/` and relevant tests together.
