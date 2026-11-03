# home-search-ai

Natural-language search assistant over fictional real estate listings.
Ask *"bright 3-room flat near the metro, under €600k"* and get matching listings, each answer citing the listings it comes from.

> Work in progress. The demo link and results will be added as the project moves forward.

## What it demonstrates
- **Tool use** with the Claude API: the question becomes structured search calls.
- **Hybrid retrieval**: SQL filters for hard constraints (price, rooms) plus vector similarity (pgvector) for fuzzy ones ("bright", "quiet").
- **Structured output** validated with Zod, **streaming** answers, **guardrails** against made-up facts.
- **Evals** run in CI, with cost and latency tracked per request.

## Stack
Next.js (TypeScript) on Vercel · Anthropic SDK · Voyage AI embeddings · PostgreSQL + pgvector on Neon · Prisma · Zod · Vitest

## Project layout
- `src/core/`: framework-agnostic AI core (pure, tested functions)
- `src/app/`: Next.js UI and route handlers
- `docs/decisions/`: why each technical choice was made

## Getting started
Requires Node.js 24.

```bash
npm install
npm run dev
```

Checks: `npm run lint`, `npm run typecheck`, `npm test`, `npm run build`.

## License
MIT. All listings are fictional.
