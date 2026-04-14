# Andrej Karpathy Coding Guidelines

An agent-behavior layer for coding work: think before coding, prefer simple solutions, make surgical changes, and work against explicit success criteria.

## Source

This entry is adapted from:
- Andrej Karpathy's observations on common LLM coding failures
- [`forrestchang/andrej-karpathy-skills`](https://github.com/forrestchang/andrej-karpathy-skills), which packages those observations into a `CLAUDE.md` guideline set

The upstream repository is MIT-licensed, so PromptRepo can preserve the guideline body directly while reorganizing it into PromptRepo's `README.md` / `SKILL.md` / `prompts.md` structure.

This folder keeps the core ideas in PromptRepo's framework format rather than vendoring the upstream repo wholesale.

## Core Idea

Most coding-agent failures are not about raw capability. They are behavioral:
- the model assumes too much
- hides confusion
- overcomplicates the implementation
- touches unrelated code
- stops at "implemented" instead of "verified"

This layer tries to force the opposite behavior.

## Why It Works

### 1. It makes ambiguity visible

Instead of letting the model silently guess, it pushes assumptions and tradeoffs into the open.

### 2. It penalizes overengineering

Many coding agents default to extra abstractions, speculative flexibility, and unnecessary cleanup. This layer explicitly blocks that tendency.

### 3. It narrows the edit surface

By forcing surgical changes, it reduces collateral damage and makes diffs easier to review.

### 4. It defines success as verification

The strongest part of the framework is converting vague tasks into testable goals. That makes autonomous looping more reliable.

## When To Use It

- Repository-level coding instructions
- Pair programming with Claude, Codex, or ChatGPT
- PR review passes
- Bug fixing
- Small-to-medium implementation tasks where overengineering is the usual failure mode

## Caveats

- It biases toward caution over speed.
- For trivial edits, this can be heavier than necessary.
- It is most useful when the task is real enough to benefit from explicit verification.

## Included Prompt Layers

See [prompts.md](prompts.md) for:
- a full coding-agent layer
- a compact version for quick use
- a review lens for judging whether agent output followed the framework

See [SKILL.md](SKILL.md) for the tagged agent-layer version and [examples.md](examples.md) for concrete failure-mode examples adapted from the upstream repo.
