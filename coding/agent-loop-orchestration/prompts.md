# Prompts

## Bounded Agent Loop Designer

```text
Design this coding task as a bounded agent loop.

Task:
[task]

Context:
[repo/project/context]

Return:
1. Goal: one sentence describing the durable objective.
2. Stop condition: what proves the loop should stop.
3. Inputs: files, issues, docs, tests, app flows, or logs the agent should inspect.
4. Loop cycle: the repeated plan -> act -> verify -> review steps.
5. Verification gates: tests, builds, browser/computer/app views, logs, or manual checks required after significant changes.
6. Delegation: whether subagents/threads/worktrees help, and what each one owns.
7. Limits: max runtime, max cost/tokens if known, max files/modules, and when to ask for help.
8. Approval gates: actions the agent must not take without explicit approval.

Bias toward the smallest loop that can produce reviewable progress. If this task is too small for a loop, say so and give the simpler prompt instead.
```

## Agent-Written Goal Bootstrap

```text
Before starting the work, write the `/goal` prompt you would want to execute.

Desired outcome:
[desired outcome]

Context:
[repo/project/context]

Constraints:
[constraints, approvals, timeline, risk tolerance]

Return:
1. The proposed `/goal` prompt in copy-paste-ready form.
2. The stop condition that proves the goal is complete.
3. The verification gates the agent should use while working.
4. The context files or docs that should be loaded before execution.
5. The approval gates for commits, pushes, publishing, deletion, external messages, or other irreversible actions.
6. If subagents would help, write one goal prompt for each subagent with its owner role, input context, output contract, and what it must not change.
7. The main risks or ambiguities a human should correct before launching the goal.

Do not start executing yet. First make the goal good enough that a separate agent could run it without needing constant steering.
```

## Peter-Style Refactor Goal

```text
/goal refactor [project-or-module] until the architecture is coherent and I would be happy maintaining it.

Constraints:
- Preserve existing behavior unless I explicitly ask for behavior changes.
- Keep a running progress note at [progress-note-path].
- After each significant step, run live verification that exercises the real workflow.
- Use computer/browser/app views when needed to verify actual user-facing behavior.
- Run an autoreview before considering the work done.
- Do not commit, merge, publish, delete, or move anything without explicit approval.

Stop when:
- the architecture is simpler or more coherent than the starting point,
- the relevant live workflow has been verified,
- remaining risks are listed clearly, and
- the diff is small enough to review.
```

## Live Verification Add-On

```text
Add this verification rule to the task:

Do not rely only on static inspection if the change affects behavior. After each significant change, run the strongest available live check:
- tests or build checks for code-level correctness,
- browser/app/computer-use verification for user-facing flows,
- logs or CLI smoke tests for background workflows,
- autoreview for scope creep, regressions, and hidden assumptions.

If live verification cannot be run, stop and report exactly what is unverified.
```

## Boris-Style Self-Verification And Subagents

```text
Run this task with self-verification and context isolation.

Goal:
[goal]

Use subagents/threads only when they isolate a real concern, such as:
- implementation,
- adversarial review,
- test generation,
- documentation or migration notes,
- investigation of an uncertain subsystem.

For each subagent/thread, define:
- owner role,
- exact input context,
- output contract,
- verification responsibility,
- what it must not change.

Main loop:
1. Plan the next step.
2. Delegate only if isolation helps.
3. Integrate outputs into one coherent diff or recommendation.
4. Verify with tests/live checks.
5. Run a maker/checker review split before stopping.

Do not let the same unchecked worker be the final judge of its own work.
```

## Mitchell-Style Loop Reality Check

```text
Before running this as a loop, critique whether it is worth it.

Task:
[task]

Answer:
1. Is a loop actually useful here, or is a single prompt/test cycle enough?
2. What is the concrete definition of "loop" in this case?
3. What cost, runtime, or context growth could make this worse than manual steering?
4. What is the smallest viable loop that would prove value?
5. What stop condition prevents this from becoming open-ended agent busywork?
6. What human approval gate is needed before any irreversible action?

If the loop is not justified, rewrite the task as a simpler one-shot prompt with verification.
```
