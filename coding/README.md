# Coding Frameworks

Prompt layers for coding agents, code review behavior, implementation discipline, and engineering execution style.

## Frameworks

| Framework | Source | Best For |
|-----------|--------|----------|
| [Andrej Karpathy Coding Guidelines](andrej-karpathy-coding-guidelines/) | Andrej Karpathy observations, adapted via `forrestchang/andrej-karpathy-skills` | Coding-agent behavior, reducing overengineering, cleaner diffs, goal-driven implementation |
| [Agent Loop Orchestration](agent-loop-orchestration/) | Peter Steinberger, Boris Cherny, Mitchell Hashimoto X posts and replies | Long-running coding-agent loops, `/goal` prompts, verification gates, subagent orchestration, cost-aware autonomy |

## Core Concepts

### Think Before Coding
Surface assumptions, confusion, and tradeoffs before implementation.

### Simplicity First
Prefer the minimum code that solves the problem over speculative flexibility.

### Surgical Changes
Touch only what the task requires. Avoid adjacent cleanup unless your change caused it.

### Goal-Driven Execution
Turn vague implementation requests into explicit success criteria with verification.

### Loop-Oriented Autonomy
For longer tasks, design the loop around goals, verification gates, context
isolation, cost limits, and human approval instead of repeatedly prompting the
agent by hand.

## When to Use These

- Pairing with coding agents
- Reviewing agent-generated code
- Setting repo-level coding behavior
- Keeping diffs narrow and deliberate
- Reducing overengineering and speculative abstractions
- Designing long-running coding-agent work without losing verification or
  control

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

**For agent-loop work:**

```text
Design this as a bounded agent loop:
1. State the goal and stop condition.
2. Break work into reviewable threads or subagents only where context isolation helps.
3. After each significant step, run real verification, including browser/computer/app views when relevant.
4. Keep cost, runtime, and scope limits explicit.
5. Do not commit, merge, publish, delete, or take external actions without approval.
```
