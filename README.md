# Skill Repository

This repository stores reusable Codex/agent skills and the shared conventions for maintaining them.

## Repository Layout

```text
.
├── README.md
├── docs/
│   └── SKILL_STANDARD.md
└── skills/
    └── <skill-name>/
        ├── SKILL.md
        ├── scripts/
        ├── assets/
        └── references/
```

## Conventions

- Put each skill in `skills/<skill-name>/`.
- Keep the skill entrypoint in `SKILL.md`.
- Keep executable helpers in `scripts/`, reusable static files in `assets/`, and longer background material in `references/`.
- Prefer short, task-oriented instructions over broad background notes.
- Do not commit secrets, local credentials, generated caches, virtual environments, or IDE workspace state.

See [docs/SKILL_STANDARD.md](docs/SKILL_STANDARD.md) for the full authoring and review checklist.
