# 0001 — TypeScript end to end

Date: 2026-11-02 · Status: accepted

## Context
Most generative AI examples are written in Python. This project targets full-stack JavaScript roles that ship AI features inside web products.

## Decision
TypeScript everywhere: Next.js, the Anthropic TypeScript SDK, Zod for validation, Prisma for the database.

## Options considered
- **Python (FastAPI, LangChain/LlamaIndex)**: richer AI ecosystem, but a second language and a second deployment for a web product, and not the stack of the roles targeted.

## Consequences
- One language and one type system from the database to the UI; Zod schemas validate both user input and model output.
- Fewer ready-made RAG libraries: retrieval and the tool-use loop are written by hand, which keeps them small and explainable.
