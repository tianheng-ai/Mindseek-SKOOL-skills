# Domain Docs

How agents should consume this repo's domain documentation when exploring the codebase.

## Before exploring, read these

- **`CONTEXT.md`** at the repo root — the project's glossary: what each domain term means here.
- **`docs/adr/`** — architecture decision records. Read the ones that touch the area you're about to work in.

If these don't exist, **proceed silently**. Don't flag their absence and don't create them upfront; add them when a term or decision actually gets settled.

## Use the glossary's vocabulary

When your output names a domain concept (an issue title, a refactor proposal, a test name), use the term as defined in `CONTEXT.md`. Don't drift to synonyms the glossary explicitly avoids.

## Flag ADR conflicts

If your output contradicts an existing ADR, say so explicitly rather than silently overriding:

> _Contradicts ADR-0007 (event-sourced orders) — but worth reopening because…_
