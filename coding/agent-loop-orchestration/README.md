# Agent Loop Orchestration

Prompt layers for turning coding agents from one-off responders into bounded
loops with goals, verification, context isolation, and explicit stop
conditions.

## Source

This entry synthesizes public X posts and replies from:

- [Peter Steinberger](https://x.com/steipete/status/2063697162748260627) on designing loops that prompt coding agents, plus follow-up examples around `/goal`, live testing, autoreview, and waking Codex to maintain repos.
- [Peter Steinberger](https://x.com/steipete/status/2066246419694948365)
  amplifying the pattern of asking Codex to write its own `/goal` prompt, and
  separate goal prompts for each spawned agent, instead of hand-authoring every
  agent objective up front.
- [Boris Cherny](https://x.com/bcherny/status/2063792263067754658) on long-running Claude Code work, dynamic workflows, nested subagents, and self-verification loops.
- [Mitchell Hashimoto](https://x.com/mitchellh/status/2064773611647574429) on the practical caveat: loop-based workloads can be real and useful, but expensive and easy to overhype without tooling, limits, and clear definitions.

This is not a transcript or quote archive. It turns the useful public ideas
into reusable prompting patterns.

## Core Idea

The next useful step beyond "prompt the coding agent" is to design a bounded
operating loop:

```text
goal -> plan -> act -> verify -> review -> decide: stop, retry, or delegate
```

The loop is only valuable when the goal, verifier, limits, and approval gates
are explicit. Otherwise it is just an expensive way to keep a model busy.

## Why It Works

### 1. Goals create continuity

A good `/goal` prompt gives the agent a durable objective, not just the next
instruction. That helps with refactors, maintenance, and multi-step fixes.

### 1a. The agent can draft the goal

For complex work, the user does not always need to hand-write the final
`/goal`. A better first move is often to ask the agent to inspect the repo,
constraints, and desired outcome, then draft the goal it would want to execute
against. The human reviews and tightens that goal before launching the loop.

This is especially useful when spawning subagents: the parent agent can draft
role-specific goals and output contracts for each worker instead of making the
human decompose the whole system manually.

### 2. Verification stops drift

Long-running agents need regular checks against reality: tests, builds,
browser flows, computer/app views, logs, and autoreview.

### 3. Context isolation keeps work reviewable

Subagents, threads, or worktrees are useful when they isolate context and make
outputs easier to review. They are not useful when they multiply unmanaged
state.

### 4. Limits make autonomy safe

Loops need runtime, cost, scope, and permission limits. A loop without a stop
condition eventually becomes a debugging problem.

## When To Use It

- Architecture refactors with fuzzy-but-real quality targets
- Repo maintenance across issues, PRs, failing checks, or review comments
- Long-running coding tasks where an agent can verify progress itself
- Parallel work where separate threads reduce context collisions
- Agent experiments where cost and stopping rules are part of the task

## Caveats

- Do not use loop language to hide a vague goal.
- Do not let the agent be both unchecked maker and final judge.
- Do not spawn subagents unless their outputs are separately reviewable.
- Do not run persistent loops without cost, runtime, and external-action gates.
- For small edits, a normal prompt plus a test is better than a loop.

## Included Prompt Layers

See [prompts.md](prompts.md) for:

- a bounded agent-loop design prompt
- an agent-written goal bootstrap prompt
- a Peter-style refactor goal prompt
- a live-verification add-on
- a Boris-style self-verification/subagent prompt
- a Mitchell-style loop reality check

See [SKILL.md](SKILL.md) for the tagged agent-layer version.
