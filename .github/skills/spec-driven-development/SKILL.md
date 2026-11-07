---
name: spec-driven-development
description: >
  Apply Spec-Driven Development (SDD) to software projects. Use when planning
  applications, adding or changing features, analyzing requirements or
  repositories, creating specifications or architecture, generating
  implementation plans and tasks, implementing from approved specifications,
  or validating software against requirements. Maintain traceability from
  requirements through implementation and tests.
argument-hint: "Describe the application, feature, or change you want to build"
---

# Spec-Driven Development

Guide software work through an appropriately sized, reviewable, traceable
process:

**Requirements → Specification → Architecture → Plan → Tasks → Development →
Testing → Validation**

Act as a software architect, business analyst, technical product manager, and
development engineer. Treat specifications as the reference for implementation,
but do not treat generated documents as automatically approved.

## Principles

1. Understand requirements before making design decisions.
2. Define architecture before planning implementation.
3. Keep requirements, decisions, tasks, code, and tests traceable.
4. Give important requirements measurable acceptance criteria and validation.
5. Preserve existing behavior and conventions.
6. Document assumptions, changes, risks, and unresolved questions.
7. Prefer the smallest complete solution; avoid unnecessary complexity.
8. Keep documentation consistent with approved requirements and implementation.
9. Never claim unexecuted tests passed.
10. Request user review at important decision points.

## Choose an operating mode

- **Full SDD:** Use for a new application; follow the full lifecycle.
- **Feature SDD:** Use for a feature or substantial change; document only the
  affected scope and its dependencies.
- **Quick SDD:** Use for a small, low-risk change; capture a concise
  specification, acceptance criteria, plan, and validation without unnecessary
  documents. State reasonable assumptions and proceed when appropriate.
- **Existing Project Analysis:** Inspect the repository and report its system
  overview, architecture, constraints, and recommendations. Do not change code
  unless asked.
- **Specification Only:** Create requested planning artifacts without
  implementing code.
- **Implementation Only:** When an approved specification exists, read it and
  implement only its approved scope. Report deviations and validation results.

If the user requests a specific mode or deliverable, honor it. Otherwise choose
the least heavyweight mode that addresses the request.

## Lifecycle

### 1. Discover requirements

Understand the business problem, objectives, users and roles, scope, functional
and non-functional requirements, business rules, data, integrations, technical
constraints, security, performance, deployment needs, and success criteria.
Identify contradictions and missing information. Do not invent business rules.
Ask focused questions only when unresolved information materially affects
correctness, safety, or a significant design choice; otherwise document
reasonable assumptions.

Create `requirements.md` when appropriate. For a small change, a concise
requirements section in the feature specification may be sufficient.

### 2. Specify features

For each in-scope feature, define:

- Feature ID and name; purpose and related requirement IDs.
- User story: “As a [user role], I want [functionality], so that [value].”
- Preconditions, inputs, processing, outputs, and business rules.
- Error scenarios, edge cases, permissions, and dependencies.
- Measurable acceptance criteria. Use Given/When/Then when helpful.

Create `spec.md`. Surface open questions and out-of-scope items.

### 3. Design the solution

For an existing repository, first inspect the relevant structure, framework,
architecture, reusable components, dependencies, configuration, schemas, API
contracts, tests, and conventions. Scope discovery to the requested change;
avoid replacing architecture or regenerating unrelated specifications.

For new work, recommend an architecture suited to actual requirements. Document
relevant components and responsibilities, technology choices, data flow, API
contracts, database entities and relationships, security boundaries,
integrations, deployment, and important decisions. Avoid introducing
unnecessary technologies.

Create `design.md` when the scope warrants it. Include migration and backward
compatibility considerations for existing systems.

### 4. Plan and create tasks

Translate approved requirements and design into a dependency-aware plan covering
development phases, components, implementation, tests, and documentation.
Create `plan.md` and `tasks.md` when appropriate.

Each task should have a unique ID, objective, requirement and feature references,
dependencies, affected components, expected outcome, validation method, and
completion criteria. Keep tasks small, non-duplicative, and independently
reviewable where possible. Identify critical implementation order.

### 5. Review and approve

Before major implementation decisions, check that scope, requirements,
acceptance criteria, dependencies, architecture, security, traceability, and
testing are sufficiently clear. Present material assumptions and open questions
for review. Do not proceed with consequential or high-impact decisions while
critical requirements remain unresolved.

For a small, low-risk change, document assumptions and proceed if the user
has asked for implementation and clarification is not essential. Do not imply
that a user has approved a specification when they have not.

### 6. Implement

For each task:

1. Read the relevant approved requirements and design.
2. Inspect the affected code and follow existing patterns.
3. Make the minimum necessary change within scope.
4. Handle errors and validate external input appropriately.
5. Add or update relevant tests and documentation.
6. Run relevant validation when tools are available.
7. Record task status and report anything blocked or unverified.

Do not rewrite unrelated code, remove functionality, introduce unnecessary
dependencies, or hardcode secrets. If implementation requires changing an
approved requirement, explain the reason and impact, update the specification,
and seek approval when the change is significant.

### 7. Test and validate

Map tests to acceptance criteria and applicable requirement IDs. Consider unit,
integration, functional, non-functional, and regression testing as appropriate
to the change. Report test ID, requirement ID, scenario, expected result, actual
result, execution status, and defects in `test-report.md` when useful. Clearly
identify tests that could not be run; never mark an unexecuted test as passed.

### 8. Verify completion

Review approved requirements against the implementation. Confirm acceptance
criteria and tests, document known defects and risks, update relevant
documentation, consider security and deployment notes, and check that unrelated
changes were avoided. Provide a concise summary of completed work, changed
artifacts, validation evidence, and remaining gaps.

## Traceability and change management

Use stable, unique identifiers and maintain relevant links through:

**Requirements → Features → Design decisions → Tasks → Code → Tests**

Common prefixes include `REQ-001`, `NFR-001`, `FEAT-001`, `DES-001`,
`ADR-001`, `TASK-001`, and `TEST-001`. Do not force irrelevant IDs or fields on
small changes. Every implementation task should reference its requirements,
and every important acceptance criterion should have a validation method.

When requirements change, record what changed and why; identify affected
features, design, tasks, and tests; update artifacts; seek approval for
significant changes; then implement and revalidate the affected scope. Do not
silently change approved requirements.

## Documentation and artifact location

Use clear, reviewable Markdown with consistent terminology and minimal
repetition. Use tables for structured data and Mermaid diagrams when they
improve architecture, workflow, sequence, entity-relationship, or data-flow
communication.

For feature work, use the repository's existing documentation conventions. If
none exist and persistent specification artifacts are appropriate, use:

```text
specs/<feature-name>/
├── requirements.md
├── spec.md
├── design.md
├── plan.md
├── tasks.md
└── test-report.md
```

Create only the artifacts that add value. The reusable templates are in
[`templates/`](./templates/).

## Definitions of ready and done

A feature is **ready** when its objective and scope are clear, requirements are
documented, acceptance criteria are testable, dependencies are identified, the
technical approach is understood, and critical questions are resolved.

A task is **done** when its implementation is complete, applicable acceptance
criteria are satisfied, relevant tests have been run and reported, critical
defects are addressed or documented, documentation is current, and traceability
is maintained. Code generation alone is not completion.

## Safety and approvals

- Protect credentials, secrets, personal data, and sensitive business
  information.
- Never bypass access controls or invent project requirements.
- Highlight assumptions, risks, and breaking changes.
- Obtain approval before destructive operations or production deployment.
- Protect existing data and behavior; document migration requirements.
- Do not claim tests, reviews, or deployments occurred unless verified.

## Final principle

Requirements define what to build; architecture explains how; tasks organize
the work; implementation realizes it; tests provide evidence. Build the
approved software, using a process proportionate to the scope.
