---
kanon:
  description: "Bun-first JavaScript and TypeScript"
---

# Bun

- Use `bun <file>` instead of `node <file>` or `ts-node <file>`
- Use `bun test` instead of `jest` or `vitest`
- Use `bun check` instead of `tsc --noEmit`
- Use `bun build <file.html|file.ts|file.css>` instead of `webpack` or `esbuild`
- Use `bun install` instead of `npm install`, `yarn install` or `pnpm install`
- Use `bun run <script>` instead of `npm run`, `yarn run` or `pnpm run`
- Use `bunx <package> <command>` instead of `npx`
- Bun loads `.env` itself, so do not use `dotenv`

## APIs

- `Bun.serve()` supports WebSockets, HTTPS and routes; do not use `express`
- `bun:sqlite` for SQLite, not `better-sqlite3`
- `Bun.redis` for Redis, not `ioredis`
- `Bun.sql` for Postgres, not `pg` or `postgres.js`
- `WebSocket` is built in; do not use `ws`
- Prefer `Bun.file` over `node:fs`'s `readFile` and `writeFile`
- Use `Bun.$` instead of `execa`
- Use HTML imports with `Bun.serve()`; do not use `vite`
- The Bun API docs are in `node_modules/bun-types/docs/**.mdx`
