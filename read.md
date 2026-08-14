<!--
 * @Author: lzxgf 1690185297@qq.com
 * @Date: 2026-08-14 18:20:03
 * @LastEditors: lzxgf 1690185297@qq.com
 * @LastEditTime: 2026-08-14 18:38:02
 * @FilePath: \AAA\read.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
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
