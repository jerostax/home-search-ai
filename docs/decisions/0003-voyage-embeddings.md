# 0003 — Voyage AI `voyage-3.5-lite` for embeddings

Date: 2026-11-03 · Status: accepted

## Context
Semantic search needs an embedding model. Anthropic does not offer one, so a second provider is required.

## Decision
Voyage AI, model `voyage-3.5-lite`, with `input_type` set to `document` when indexing listings and `query` when embedding a user question.

## Options considered
- **`voyage-3.5`**: better quality, higher cost and latency. Reconsidered only if evals show retrieval misses relevant listings.
- **OpenAI `text-embedding-3-small`**: widely used and cheap, but no advantage here and one more paid account.
- **Local model (transformers.js)**: free and keyless, but loading a model of about 100 MB in a serverless function means slow cold starts, and quality is lower.

## Consequences
- Indexing about 300 listings uses roughly 60,000 tokens, well inside Voyage's free allowance.
- Vectors from different models are not comparable: changing model means re-indexing every listing, and the `vector(N)` column must match the model's output dimension.
