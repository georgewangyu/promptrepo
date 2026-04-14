# Coding Frameworks

Prompt layers for coding agents, code review behavior, implementation discipline, and engineering execution style.

## Frameworks

| Framework | Source | Best For |
|-----------|--------|----------|
| [Andrej Karpathy Coding Guidelines](andrej-karpathy-coding-guidelines/) | Andrej Karpathy observations, adapted via `forrestchang/andrej-karpathy-skills` | Coding-agent behavior, reducing overengineering, cleaner diffs, goal-driven implementation |

## Core Concepts

### Think Before Coding
Surface assumptions, confusion, and tradeoffs before implementation.

### Simplicity First
Prefer the minimum code that solves the problem over speculative flexibility.

### Surgical Changes
Touch only what the task requires. Avoid adjacent cleanup unless your change caused it.

### Goal-Driven Execution
Turn vague implementation requests into explicit success criteria with verification.

## When to Use These

- Pairing with coding agents
- Reviewing agent-generated code
- Setting repo-level coding behavior
- Keeping diffs narrow and deliberate
- Reducing overengineering and speculative abstractions

## Quick Prompt

**For coding work:**

```text
Use this coding mode:
1. State assumptions before implementing.
2. If ambiguity exists, present interpretations instead of silently choosing one.
3. Prefer the simplest solution that satisfies the request.
4. Touch only lines directly required by the task.
5. Define success criteria and verify them before calling the task done.
```
