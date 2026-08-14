# Yuntian Automatic Delivery

Yuntian Automatic Delivery is a unified advertising management and delivery platform. It consolidates shared admin capabilities and media delivery workflows into a Vue 3, TypeScript, Pinia, Element Plus, and Vite application.

## Project Focus

- Unified entry for advertising management, delivery, reports, materials, assets, tasks, tools, and system management.
- Business modules are organized by product domain, not by legacy project source.
- New business code should follow the refactor rules in `AGENTS.md` and `docs/refactor/`.

## Tech Stack

- Vue 3 + TypeScript + Vite
- Vue Router + Pinia
- Element Plus
- SCSS, Less, UnoCSS, PostCSS
- pnpm

## Development

Use pnpm only. Node.js must be `>=18`.

```bash
pnpm install
pnpm dev
pnpm ts:check
pnpm lint:eslint
pnpm lint:style
pnpm build:dev
pnpm build:test
pnpm build:pro
```

On Windows, use `pnpm.cmd` if PowerShell blocks `pnpm`.

## Environment Files

The project uses Vite environment files:

- `.env.example`: committed example values.
- `.env.base`, `.env.dev`, `.env.test`, `.env.pro`: local environment files and ignored by Git.

New environment variables must use the `VITE_` prefix. Do not commit secrets, private tokens, or temporary debug addresses.

Production releases are built once and promoted unchanged from test to production. See [the release guide](docs/deployment/release.md) for the environment contract, artifact verification, and shared gateway template.

## Directory Rules

Main source directories:

```text
src/
  layout/
  router/
  axios/
  api/
  store/
  views/
  components/
  hooks/
  utils/
  styles/
```

Primary business domains:

```text
src/views/
  home/
  promotion/
  report/
  material/
  asset/
  task/
  tool/
  manage/
```

Route modules live in `src/router/modules/`. APIs follow business domains under `src/api/`. Cross-page state belongs in Pinia modules; page-local state should stay in the page or its composables.

## Commit Checks

Before committing code changes:

- Run `pnpm ts:check`.
- Run `pnpm lint:eslint` when changing TS, Vue, router, store, API, or shared components.
- Run `pnpm lint:style` when changing styles.
- For layout, menu, style, or interaction changes, run `pnpm dev` and verify the UI in a browser.
