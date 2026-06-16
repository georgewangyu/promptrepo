---
name: agent-loop-orchestration
description: Design bounded coding-agent loops with explicit goals, verification gates, context isolation, cost/runtime limits, and human approval. Use for long-running coding work, `/goal` prompts, subagent orchestration, repo maintenance loops, and loop reality checks.
license: MIT
memory_tags:
  - domain:coding
  - framework:agent-behavior
  - source:peter-steinberger
  - source:boris-cherny
  - source:mitchell-hashimoto
  - use_case:coding-agents
  - use_case:agent-loops
  - style:goal-driven-execution
  - style:self-verification
  - risk:high
---

# Agent Loop Orchestration

Design bounded coding-agent loops that can make progress without losing
verification, scope control, or human approval gates.

## Trigger

Use when:

- a coding task may run for many steps
- the user mentions loops, `/goal`, autonomous agents, subagents, worktrees, or
  long-running coding work
- the task needs explicit live verification
- the agent might otherwise keep working without a clear stop condition

Do not use when:

- the task is a trivial one-shot edit
- no verifier exists
- the user wants brainstorming only
- the loop would require irreversible actions without approval

## Inputs

- Required: task goal, target repo/module, available verification path
- Optional: issue/PR list, runtime/cost limits, subagent roles, approval rules

## Workflow

1. Define the durable goal in one sentence.
2. Define the stop condition before starting.
3. Identify the strongest available verification gates.
4. Decide whether subagents/threads/worktrees actually isolate useful context.
5. Set runtime, cost, scope, and external-action limits.
6. Run the loop as plan -> act -> verify -> review -> decide.
7. Stop with changed files, verification, unresolved risks, and next action.

## Design Rules

### Goals Before Motion

The goal should be concrete enough that progress can be judged. If the goal is
vague, rewrite it before delegating work.

### Let The Agent Draft The Goal

When the user has a desired outcome but not a crisp execution contract, first
ask the agent to write the `/goal` prompt it would want to run. The human
should review the proposed goal, stop condition, verification gates, and
approval gates before the loop starts.

For multi-agent work, the parent agent should draft role-specific goals and
output contracts for spawned agents. Do not make the human manually decompose
every worker prompt when the agent has enough context to propose them.

### Verification Before Trust

After meaningful changes, verify against reality: tests, builds, browser
flows, computer/app views, logs, or CLI smoke tests. If none are possible,
report the gap.

### Context Isolation With Purpose

Use subagents, threads, or worktrees only when each one has a clear role and
reviewable output. More workers are not automatically better.

### Maker And Checker Split

For risky work, separate implementation from review. Do not let the unchecked
maker be the final judge.

### Limits And Approval Gates

Set limits before autonomy:

- max runtime or cadence
- max scope or file area
- cost/token sensitivity when relevant
- actions requiring human approval

Commits, merges, pushes, publishing, deletion, emails, account actions, and
other external-state changes require explicit approval unless the user has
already authorized them.

## Output Contract

Return:

- goal
- stop condition
- loop cycle
- verification gates
- delegation plan, if any
- limits and approval gates
- final status with evidence

## Guardrails

- Do not call vague persistence "a loop."
- Do not run indefinitely.
- Do not spawn subagents without output contracts.
- Do not claim live verification you did not perform.
- Do not hide cost, runtime, or context-growth concerns.
