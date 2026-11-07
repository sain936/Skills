---
name: skill-creator
description: >
  Create, improve, review, and test agent skills for VS Code GitHub Copilot.
  Use when designing a new skill, revising SKILL.md instructions or metadata,
  improving skill discovery and trigger descriptions, adding bundled
  references or scripts, or validating a skill before publishing it.
---

# VS Code Skill Creator

Help create focused, discoverable, and verifiable skills for this repository's
agent environment. Use the existing repository's patterns and the VS Code
Agent Skills format. Do not assume Claude-specific commands or evaluation
infrastructure is available.

## 1. Understand the skill

Identify:

- The user task the skill should improve.
- When it should activate and example trigger phrases.
- The expected behavior and output.
- Required tools, scripts, references, and platform constraints.
- How a user can tell that the skill worked.

Use the current conversation and repository context first. Ask a focused
question only if an unresolved detail materially changes the skill. Otherwise
state a reasonable assumption and proceed.

## 2. Choose scope and location

Prefer one skill for one coherent, repeatable workflow. Put workspace skills
under `.github/skills/<skill-name>/`. A skill folder must contain `SKILL.md`;
add `references/`, `scripts/`, or `assets/` only when they materially help the
workflow.

Before creating or editing files:

1. Inspect relevant existing skills and repository instructions.
2. Check whether the target folder already exists.
3. Preserve unrelated work and integrate with existing content.
4. Avoid duplicating an existing skill; extend or clarify it when appropriate.

## 3. Write discoverable metadata

Use valid YAML frontmatter. `name` must be lowercase kebab-case and match the
folder name. Give `description` concrete task and trigger terms because it is
the primary discovery surface. Explain what the skill does and when to use it;
avoid vague descriptions and keyword stuffing.

Example:

```yaml
---
name: example-skill
description: >
  Explain what this skill does and use it when the user asks for the specific
  workflow, artifact, or task it supports.
argument-hint: "Describe the task"
---
```

Keep the main instructions concise and procedural. Put detailed material in
one-level-deep references and link it with relative paths. Avoid loading
unrelated instructions for every request.

## 4. Design the workflow

Write clear steps that tell the agent how to:

1. Recognize the task and collect necessary inputs.
2. Inspect applicable files, existing conventions, and available tools.
3. Perform the workflow with explicit constraints and decision points.
4. Handle ambiguity, errors, unavailable dependencies, and unsafe actions.
5. Verify the result and report outputs and limitations honestly.

Use examples, templates, and checklists when they improve repeatability.
Prefer the smallest complete procedure. Do not include generic advice that
does not change the agent's behavior.

## 5. Add resources responsibly

Add scripts only for deterministic, repeatable operations that cannot be
handled more simply by the agent. Document how to run them, prerequisites,
inputs, outputs, and failure behavior. Do not assume dependencies are installed;
check first and report missing requirements rather than silently installing
them.

Keep references targeted. Use relative links from `SKILL.md`, and ensure every
linked resource exists. Protect secrets and user data. Never make external
requests or perform destructive actions unless the task and permissions allow
them.

## 6. Test and refine

For objectively verifiable skills, define a few representative test requests
covering a normal case, an edge case, and an ambiguous or out-of-scope case.
Run them only with an evaluation harness that is actually available and
authorized. Some upstream evaluation scripts bundled with this skill require
Claude-specific tools; do not invoke those from Copilot unless that runtime is
explicitly available and requested.

Otherwise perform a static review:

- Frontmatter parses and contains a meaningful `name` and `description`.
- The name matches the directory.
- The workflow is clear, bounded, and consistent with available tools.
- References and scripts exist and are described accurately.
- Platform-specific commands and paths fit the target environment.
- Safety, privacy, error handling, and validation are addressed where relevant.
- The skill does not claim unverified behavior.

Improve the skill based on concrete test results or user feedback. Optimize
trigger phrases without making the description so broad that unrelated tasks
activate it.

## 7. Report the result

Summarize the skill's purpose, location, supporting resources, validation
performed, and anything that could not be tested. Do not claim a skill was
runtime-tested if only static checks were performed.
