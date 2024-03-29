# Fud Names API



This repo is the codebase for the Fudders Names API

## Local Development

Install dependencies:

```bash
pnpm install
```

Create a `.env` file with `DATABASE_URL` pointing to a Postgres database URL. You'll need to have Postgres installed and running on your machine.

```dotenv
DATABASE_URL="postgresql://localhost:5432/fud-api-dev"
```

Setup the DB migrations with:

```bash
pnpm prisma migrate dev
```

Finally, run the server with:

```bash
pnpm dev
```

## Hosting the API

Running a hosted version of the API requires a Postgres instance available at the `DATABASE_URL` environment variable.

A `Dockerfile` is provided, which can be used to easily deploy the project.

## Project architecture

A few notes about the tech stack of the FUD names Names API:

- All code is in TypeScript
- Fastify as the server framework
- Prisma as the database ORM

Included in the codebase is a small "worker" architecture, which is used to constantly stay in sync with the Ordinals network. When running the server, a scheduled job is configured to sync with any newly minted Ordinals.

To run the server without running the worker, set the environment variable `RUN_SYNC` to `"false"`. This allows for running a typical worker/server setup.
