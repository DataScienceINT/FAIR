# Domain Docs

This repository uses a single domain documentation context.

## Before exploring, read these

- `GLOSSARY.md` at the repository root, if present.
- Relevant ADRs under `docs/adr/`, if present.

If these files do not exist, proceed silently. Do not suggest creating them upfront.
Domain modeling creates them lazily when terms or decisions actually get resolved.

## Use the glossary's vocabulary

Use the glossary's canonical terms when naming domain concepts. Avoid synonyms that the
glossary explicitly rejects. If a concept is missing, reconsider invented language or
note the gap for a future domain-modeling session.

## Flag ADR conflicts

Explicitly surface a conflict with an existing ADR rather than silently overriding it.

This documentation layout is a workflow configuration, not an adopted F-AI-R architecture.
