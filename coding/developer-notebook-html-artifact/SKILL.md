---
name: developer-notebook-html-artifact
description: "Create polished static HTML technical artifacts with a warm developer-notebook design language, exact code snippets, plain-English explanations, visual structure, and practical next actions. Use for repo visualization, architecture walkthroughs, agent eval reports, implementation retrospectives, and codebase walkthrough outputs."
memory_tags:
  - domain:documentation
  - workflow:html-artifact
  - skill_role:generator
  - repo_boundary:tools
  - inputs:technical-context
  - outputs:html-artifact
  - risk:low
---

# Developer Notebook HTML Artifact

Use this skill when the user wants a technical explanation, repo visualization,
repo walkthrough, eval report, or implementation retrospective to become a
polished static HTML artifact.

## Design Language

- Warm paper-like background and warm gray secondary text.
- One bold accent color. Avoid generic purple/blue AI gradients.
- Distinctive display typography for headings.
- Readable body typography and monospaced code typography.
- Dark IDE-style code panels paired with warm plain-English explanation panels.
- Generous whitespace, scroll rhythm, and strong hierarchy.
- Cards, step panels, diagrams, timelines, or flow visuals before long prose.

## Content Rules

1. Start from the practical outcome or user action.
2. Name the main actors: files, modules, services, agents, or systems.
3. Trace the core flow from trigger to result.
4. Use exact source snippets. Do not simplify quoted code.
5. Put plain-English interpretation beside the code.
6. Identify risk areas and failure modes.
7. End with actionable next steps and stop conditions.

## Guardrails

- Treat this as a house design layer, not a one-off decorative pass.
- Do not copy another project's files, brand, or exact visual identity unless
  the user explicitly asks to use licensed source material.
- Do not hide uncertainty. If repo understanding is heuristic, label it that
  way.
- If the artifact may guide code changes, include verification commands and
  human-review boundaries.
