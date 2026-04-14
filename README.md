# PromptRepo

A curated collection of reusable prompt layers: classic thinking frameworks, decision lenses, and agent-behavior overlays turned into actionable AI instructions.

## The Idea

Some prompt layers are about **how to think**.
Examples: Ray Dalio on radical transparency, second-order consequences, and principled decision-making.

Some prompt layers are about **how an AI system should behave while doing work**.
Examples: coding-agent guidelines that force the model to think before coding, stay simple, and verify against explicit success criteria.

PromptRepo exists to collect both.

The point is not just "good prompts." The point is portable operating layers you can drop into ChatGPT, Claude, Codex, or another agent workflow when you want a specific style of reasoning or execution.

## Structure

```
promptrepo/
├── AGENTS.md              # Bootstrap for AI assistants
├── SOUL.md                # Identity and style guide
├── README.md              # This file
├── coding/                # Coding-agent behavior layers and implementation philosophy
├── decision-making/       # Prompts for better decisions
├── problem-solving/       # Mental models and analysis frameworks
├── creativity/            # Lateral thinking and ideation
├── communication/         # Feedback, negotiation, clarity
└── planning/              # Goal setting and strategic thinking
```

Within each category:

```
[category]/
├── README.md              # Category overview
└── [framework-or-layer]/
    ├── README.md          # What it is, why it works, when to use it
    ├── SKILL.md           # Tagged agent-skill version for structured reuse
    └── prompts.md         # Copy-paste-ready prompt layer(s)
```

## Format Strategy

PromptRepo entries should support two formats at the same time:

- `prompts.md` for small, copy-paste-ready prompts that someone can drop into ChatGPT, Claude, or another tool immediately
- `SKILL.md` for the same idea in a more structured, tagged format that works better as a reusable agent layer

Why keep both:
- prompts are faster for ad hoc usage
- skill files are better for indexing, tagging, discoverability, and future orchestration

The long-term shape should be: every serious PromptRepo entry has both.

## Two Kinds of Entries

### 1. Thinker Frameworks

These capture a person's mental model and turn it into prompts you can apply on demand.

Examples:
- Ray Dalio for principled decision-making
- Charlie Munger for mental-model-based reasoning
- Other strategic, creative, or communication frameworks

### 2. Agent Skill Layers

These are not really "thinker quotes." They are behavioral overlays for AI systems.

Examples:
- Coding-agent rules
- Research-agent rules
- Writing-agent rules
- Feedback or critique modes

These belong in PromptRepo because they are still reusable prompt layers, just aimed at agent behavior rather than human reflection.

## Quick Start

1. Browse by use case.
2. Pick a framework or behavior layer.
3. Open `README.md` to understand when to use it.
4. Copy from `prompts.md` into your tool and customize the placeholders.

## Starting Points

- [`decision-making/ray-dalio-principles/`](decision-making/ray-dalio-principles/) for principled decision-making
- [`coding/andrej-karpathy-coding-guidelines/`](coding/andrej-karpathy-coding-guidelines/) for coding-agent behavior

## Contributing

Entries should be:
- Actionable: prompts you can use immediately
- Sourced: attribute the original thinker, post, repo, or framework
- Explained: include why it works and when to use it
- Portable: readable as a prompt layer, not only as an essay

## License

MIT for original repository content. Third-party frameworks and prompt layers should keep clear attribution to their source.
