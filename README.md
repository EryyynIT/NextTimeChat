# Realtalk

A simple multi-room web chat built with Next.js 14 (App Router) and PostgreSQL.

## What it does

- Home page lists existing chat rooms (derived from messages already in the database).
- Users pick a nickname, join a room from the list, or create a new room at `/create`.
- Room pages (`/room/[id]`) show the message history and poll the server every 400 ms for new messages (no websockets).
- Messages are stored in a single `messages` table (`id`, `room`, `name`, `message`).
- UI text is in Russian.

## Stack

- Next.js 14 (App Router, server actions), React 18, TypeScript
- Tailwind CSS
- PostgreSQL via the `pg` driver

## Running locally

1. Install dependencies (pnpm is used by the lockfile):

   ```bash
   pnpm install
   ```

2. Provide a PostgreSQL connection. The app creates a `pg` `Client` with no explicit config, so it reads the standard `PGHOST` / `PGPORT` / `PGUSER` / `PGPASSWORD` / `PGDATABASE` environment variables (e.g. put them in `.env.local`).

3. Create the table by hitting the seed route once after the dev server is up:

   ```bash
   curl http://localhost:3000/seed
   ```

4. Start the dev server:

   ```bash
   pnpm dev
   ```

   Open http://localhost:3000.
