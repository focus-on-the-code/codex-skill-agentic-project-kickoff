# Agentic Project Kickoff

A Codex skill for turning a software, application, automation, AI workflow, or agentic coding idea into a structured, reviewable project workspace.

`SKILL.md` is authoritative for agent behavior. This README is the human-facing overview.

## When to use it

Use the skill when you want the complete project-kickoff workflow: adaptive discovery, strategy, decisions, task tracking, workspace structure, readiness review, and reusable planning templates.

It can be invoked explicitly:

```text
$agentic-project-kickoff
```

It can also be requested naturally:

```text
Use my project kickoff workflow for this idea.
```

The skill is not intended for a narrow coding question, a small isolated task, or casual brainstorming that does not need a complete kickoff.

## Staged workflow

The default workflow is deliberately staged:

1. Codex accepts the project idea, summarizes what is clear, and asks one important adaptive question at a time.
2. Codex creates the initial four planning documents.
3. Codex stops for human review and reports assumptions, unresolved decisions, recommendations, and the next step.
4. After approval, Codex expands the project workspace.

Approval to expand authorizes the workspace expansion; it does not automatically approve proposed project decisions. Proposed decisions remain proposed until the user explicitly approves them or clearly includes them in an approval.

The user may explicitly request the complete kickoff package in one pass.

## Template library

Templates are starting structures, not rigid forms. Codex adapts them to the project, removes irrelevant placeholders, and preserves uncertainty as assumptions, risks, open questions, decisions needed, or human-review items.

### Initial project documents

- `Context/IDEA_INTAKE.md`
- `ProjectPlans/STRATEGY.md`
- `ProjectPlans/DECISIONS.md`
- `ProjectPlans/TASKS.md`

Codex creates only these four documents initially, then stops for review.

### Expanded project documents

- `AGENTS.md`
- `ProjectPlans/ROADMAP.md`
- `Context/Decision_Notes.md`
- `Context/3-Hop-Method.md`
- `docs/phase0/PHASE0_CHECKLIST.md`
- `docs/phase0/READINESS_ASSESSMENT.md`

The expanded workspace also includes `z-archive/`, reusable phase templates, and a conservative `.gitignore` when appropriate.

A project `README.md` is not created by default. It may be added when requested, when the repository will be shared immediately, or when external-facing documentation is needed.

### Reusable phase templates copied into projects

- `docs/templates/PHASE_PLAN.template.md`
- `docs/templates/PHASE_CHECKLIST.template.md`
- `docs/templates/REVIEW_SUMMARY.template.md`
- `docs/templates/PHASE_RETROSPECTIVE.template.md`
- `docs/templates/PROJECT_RETROSPECTIVE.template.md`

These remain reusable blank structures until a project phase or review needs them.

### Skill-only master file

- `references/BUILDER_PLAYBOOK.md`

This is the single authoritative Builder Playbook. The skill reads and applies its approved cross-project practices when relevant, but does not copy it into projects by default. A project-local snapshot is created only when explicitly requested or needed for portability.

## Retrospectives and learning

A Phase Retrospective can serve as a running learning log during a phase. Its phase-end review is conditional: use it when meaningful learning, rework, bugs, design changes, tooling issues, collaboration friction, major decisions, or reusable patterns occurred; skip or compress it for straightforward low-risk work without meaningful lessons.

A Project Retrospective gathers candidate lessons from phase retrospectives and other project evidence. It consolidates duplicates, identifies conflicts, separates project-specific observations from transferable improvements, and compares proposed promotions with the master Builder Playbook.

All normal promotion recommendations are presented together for human approval. Approved changes may update the master playbook, `SKILL.md`, relevant templates, this README, or invocation metadata. The skill package is not updated lesson-by-lesson during normal project work.

## Prototype and sample code

Kickoff favors discovery, planning, and validation before implementation, but it does not impose a rigid no-code rule. Codex may create a small prototype, sample script, proof of concept, pseudocode, mock data, or runnable example when it materially improves a decision.

Exploratory work should be labeled clearly and explain how to run it, what it demonstrates, and what it does not prove. Production implementation or irreversible commitments require explicit approval.

## Installation

Copy or symlink the complete `agentic-project-kickoff` folder into:

`~/.agents/skills/agentic-project-kickoff`

Keep the complete folder together so `SKILL.md`, `agents/openai.yaml`, the master reference, and output templates remain available.

## Basic validation and testing

Before installation:

- confirm the expected files and folders exist
- confirm `SKILL.md` frontmatter and `agents/openai.yaml` parse correctly
- search for stale or missing file references
- confirm ordinary files are not executable or world-writable
- test the initial four-document stop and the post-approval expansion in a disposable project

An independent fresh-context test provides stronger behavioral evidence than a same-agent static simulation.
