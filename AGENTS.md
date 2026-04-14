# PromptRepo Session Bootstrap

Use pointer-style startup context to keep guidance centralized and concise.

## Required Startup Context

At the start of every new session in this repository, read in order:

1. `README.md` — Repository overview and conventions
2. `SOUL.md` — Assistant identity and style
3. The relevant use-case `README.md` (e.g., `decision-making/README.md`)

## Directory Structure

```
promptrepo/
├── [use-case]/                   # decision-making/, coding/, problem-solving/, etc.
│   ├── README.md                 # Overview of frameworks in this category
│   └── [framework-or-layer]/     # Individual framework folders
│       ├── README.md             # Explanation, source, and usage
│       ├── SKILL.md              # Tagged structured version
│       └── prompts.md            # Copy-paste ready prompts
```

## Priority

If instructions conflict:

1. User instructions override file instructions
2. More specific directory-level docs override broad/root docs
3. Framework-specific docs override use-case category docs

## Behavior

- Keep edits scoped to the target framework unless explicitly asked to span categories
- When cross-category changes are needed, state the categories being changed before editing
- Prompts should be copy-paste ready with clear placeholder indicators like `[situation]`
- Preserve attribution when adapting third-party prompt layers or agent guidelines
- Prefer dual-format entries: lightweight `prompts.md` plus tagged `SKILL.md`
