# Atelier Store

Next.js (App Router) + TypeScript + Tailwind CSS, with Better Auth, Drizzle ORM and Postgres on Neon.

## Getting started

```bash
npm install
cp .env.example .env   # fill in DATABASE_URL and BETTER_AUTH_SECRET
npm run dev
```

## Project structure

```
src/
  app/
    api/auth/[...all]/route.ts   # Better Auth route handler
  db/
    index.ts                     # Drizzle client (Neon HTTP driver)
    schema/index.ts              # Drizzle schema barrel (empty for now)
  lib/
    auth.ts                      # Better Auth server instance
    auth-client.ts               # Better Auth React client
drizzle.config.ts                # drizzle-kit config
```

## Scripts

| Script                  | Purpose                                                      |
| ----------------------- | ------------------------------------------------------------ |
| `npm run dev`           | Start the dev server                                         |
| `npm run build`         | Production build                                             |
| `npm run lint`          | ESLint                                                       |
| `npm run typecheck`     | TypeScript check                                             |
| `npm run auth:generate` | Generate Better Auth tables into `src/db/schema/auth.ts`     |
| `npm run db:generate`   | Generate SQL migrations from the schema                      |
| `npm run db:migrate`    | Apply migrations                                             |
| `npm run db:push`       | Push schema directly (prototyping)                           |
| `npm run db:studio`     | Open Drizzle Studio                                          |

## Setting up the database

1. Create a Neon project and copy its pooled connection string into `DATABASE_URL`.
2. `npm run auth:generate`, then add `export * from "./auth";` to `src/db/schema/index.ts`.
3. `npm run db:generate && npm run db:migrate`.
