---
name: karpathy-guidelines
description: Behavioral guidelines to reduce common LLM coding mistakes. Use when writing, reviewing, or refactoring code to avoid overcomplication, make surgical changes, surface assumptions, and define verifiable success criteria.
license: MIT
memory_tags:
  - domain:coding
  - framework:agent-behavior
  - source:andrej-karpathy
  - source_repo:forrestchang-andrej-karpathy-skills
  - use_case:coding-agents
  - style:simplicity-first
  - style:surgical-changes
  - style:goal-driven-execution
  - risk:medium
---

# Karpathy Guidelines

Behavioral guidelines to reduce common LLM coding mistakes, derived from [Andrej Karpathy's observations](https://x.com/karpathy/status/2015883857489522876) on LLM coding pitfalls.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## Trigger

Use when:
- writing, refactoring, or reviewing code
- the task benefits from tighter scoping and explicit verification
- the risk of LLM overbuilding or guessing is non-trivial

Do not use when:
- the task is purely brainstorming with no implementation pressure
- the user explicitly wants rapid ideation over disciplined execution

## Inputs

- Required: task request, codebase context, and success criteria if known
- Optional: constraints, existing tests, and acceptable tradeoffs

## Workflow

1. State assumptions and ambiguities before implementing.
2. Pick the smallest coherent change that satisfies the request.
3. Keep edits surgical and aligned with the existing codebase style.
4. Define how success will be verified before claiming completion.
5. Report what changed, what was verified, and what remains uncertain.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

## Output Contract

Good output should include:
- explicit assumptions or ambiguities
- a scoped implementation plan when the task is multi-step
- the smallest coherent code change
- real verification or a clear statement that verification was not run

## Guardrails

- Do not add speculative abstractions that were not requested.
- Do not silently refactor unrelated areas.
- Do not claim tests or checks you did not actually run.
