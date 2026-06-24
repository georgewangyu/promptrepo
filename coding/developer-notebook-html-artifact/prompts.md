# Developer Notebook HTML Artifact Prompts

## General Artifact Prompt

```text
Create a polished static HTML artifact for [technical subject].

Use this design language:
- warm off-white or paper-like background
- warm grays for secondary text
- one confident accent color, not a purple/blue AI gradient
- distinctive display typography for headings
- readable sans-serif body typography
- dark IDE-style code panels with exact code snippets
- generous whitespace and clear scroll rhythm
- visual explanations before long paragraphs

Use this content structure:
1. Start with the concrete user/workflow outcome.
2. Name the main actors: modules, files, services, agents, or systems.
3. Trace the important flow from trigger to result.
4. Show exact source snippets beside plain-English interpretation.
5. Identify risk areas and failure modes.
6. End with practical next actions.

Rules:
- Do not modify quoted code snippets. Use exact source text.
- Avoid walls of text. If a section has 3+ items, turn it into cards, steps, or a diagram.
- Keep each screen/section focused on one idea.
- Add glossary/tooltips for technical terms when the audience may not know them.
- Use quizzes or scenario checks only when they test practical application, not memorization.
- Make the output feel like a durable product artifact, not a chat transcript.

Input:
[paste source notes, repo facts, code snippets, or analysis here]
```

## Repo Visualization Prompt

```text
Turn [repo name/path] into a repo visualization HTML artifact.

Audience:
- a coding agent that needs to work safely in this repo
- a technical human who wants the agent's map and guardrails

Output sections:
1. What this repo does in plain English
2. Architecture map: folders, modules, entry points, and data/control flow
3. Agent reading order: the first files to inspect and why
4. Workflow commands: run, test, build, lint, deploy if applicable
5. Risk areas: auth, secrets, deploy, migrations, schemas, automation, public APIs
6. Exact code snippets with plain-English explanation
7. Safe first tasks: docs, tests, small isolated changes, verification commands
8. Stop conditions: when the agent should ask for human review

Design constraints:
- Warm developer-notebook visual style.
- Exact code snippets on the left; plain English on the right.
- Use cards, timelines, flow diagrams, or step panels instead of dense prose.
- No generic AI styling.

Source material:
[paste repo scan, README, scripts, tree, and key snippets here]
```
