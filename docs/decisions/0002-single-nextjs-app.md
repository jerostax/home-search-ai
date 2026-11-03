# 0002 — Single Next.js app, framework-agnostic AI core

Date: 2026-11-03 · Status: accepted

## Context
The interesting part of the project is the AI core (hybrid retrieval, tool use, guardrails, evals), not the HTTP layer.

## Decision
One Next.js app deployed on Vercel. The AI core lives in `src/core/` as pure TypeScript functions with explicit dependencies (model client, embedding client, database) passed as parameters, so tests can swap them for fakes. Route handlers, the eval runner and an optional MCP server import the core directly.

## Options considered
- **Separate NestJS API + Next.js front**: clearer backend boundary and built-in dependency injection, but a second deployment, CORS, and streaming across two services, for no gain at this size.

## Consequences
- One deployment, one repository, end-to-end types.
- The core has no `next` import, so it could be wrapped in another server (NestJS, Express) later without rewriting it.
