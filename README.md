# SchemaPulse

A Vite + React + TypeScript database schema and SQL migration studio, deployed as one Vercel project.

## Features
- Editable relational tables, columns, primary keys, nullability and uniqueness
- Seed schema for users, projects, deployments and API keys
- PostgreSQL, SQLite and MySQL DDL generation with optional down scripts
- Foreign-key index advisor and migration lint warnings
- Copy/download SQL and responsive dark developer UI
- Vercel Functions at /api/schemas and /api/migrate; local frontend fallback when functions are not running

## Development
```bash
npm install
npm run dev
```
For API routes locally, use `npx vercel dev`. The plain Vite server falls back to bundled demo data and a local SQL compiler.

## Deployment
Import this repository into Vercel. Framework preset: Vite. Build command: `npm run build`. Output directory: `dist`.

## Important persistence note
The schemas endpoint stores edits in process memory to satisfy the starter in-memory workflow. Vercel Functions are ephemeral and may cold-start or scale independently, so this is not durable shared storage. Connect Postgres/Neon/Supabase or another persistent database before relying on saved schema changes in production. Review generated migrations before executing them against a live database.
