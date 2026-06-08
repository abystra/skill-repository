# Skill Authoring Standard

This document defines the baseline rules for skills in this repository.

## Skill Structure

Each skill should live in `skills/<skill-name>/` and include:

- `SKILL.md`: required entrypoint with purpose, trigger conditions, workflow, and constraints.
- `scripts/`: optional executable helpers used by the skill.
- `assets/`: optional static templates, examples, images, or fixtures.
- `references/`: optional longer documentation that should only be loaded when needed.

Use lowercase kebab-case names for skill directories. Keep names specific enough to describe the task domain.

## SKILL.md Requirements

`SKILL.md` should include:

- A concise description of what the skill does.
- Clear trigger conditions for when the skill should be used.
- A step-by-step workflow that avoids unnecessary context loading.
- Required environment variables or external dependencies, without real values.
- Safety constraints, especially for network access, credentials, file writes, and publishing actions.
- Verification steps that prove the skill worked.

Keep examples minimal and reusable. Avoid copying large reference material into `SKILL.md`; link to files under `references/` instead.

## Security Rules

Never commit:

- API keys, tokens, passwords, private certificates, cookies, or session dumps.
- `.env` files containing real values.
- Local IDE state, machine-specific paths, caches, virtual environments, or dependency folders.
- Production data, customer data, private documents, or raw exports.
- Generated artifacts that can reveal credentials through logs or metadata.

Use placeholder names such as `OPENAI_API_KEY`, `GITHUB_TOKEN`, or `EXAMPLE_ENDPOINT` when documenting configuration.

Before committing, run a secret scan or targeted search for common credential patterns.

## Script Rules

Scripts should be deterministic, scoped, and easy to inspect.

- Prefer standard library dependencies unless the task clearly needs a package.
- Print actionable errors and exit with a non-zero status on failure.
- Do not read credentials from hardcoded paths.
- Do not write outside the repository unless explicitly documented.
- Keep generated output paths predictable and ignored when appropriate.

## Review Checklist

Before a skill is merged:

- The directory name and `SKILL.md` match the skill purpose.
- The workflow can be followed without hidden local state.
- Required dependencies and environment variables are documented.
- Sensitive values are absent from tracked files.
- Generated files and local tooling state are ignored.
- Verification steps were run or the reason they were skipped is documented.
