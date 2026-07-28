---
name: agentic-project-kickoff
description: Use when the user explicitly asks to start, structure, or convert a software, app, automation, AI workflow, or agentic coding project using the project kickoff workflow. Guides adaptive discovery, creates project-specific planning/workspace docs from templates, preserves decisions and open questions, and supports compound learning without rushing into implementation.
---

# Agentic Project Kickoff Skill

## Purpose

Use this skill to turn a project idea into a structured agentic coding workspace.

The goal is not to rush into coding. The goal is to create enough shared understanding, structure, decisions, guardrails, and review points that later implementation can move faster and more safely.

## Activation Rule

Use this skill only when the user explicitly invokes it or clearly asks for this workflow.

Examples:

- `$agentic-project-kickoff`
- "Use my project kickoff kit."
- "Start this with the project kickoff workflow."
- "Turn this into a full agentic build project."
- "Set up the agentic project starter package for this idea."

Do not auto-apply this skill to every casual project idea, small question, lightweight script, or brainstorming conversation.

## Core Source/Destination Rule

This skill package is the reusable source.

The current project workspace is the destination.

Never overwrite source templates while generating a project workspace. Copy, adapt, or render templates into the project workspace.

If a destination file already exists, inspect it first. Preserve useful project-specific content. Do not overwrite existing files silently.

Human-approved retrospective promotion is the deliberate exception that permits updates to this skill package.

## Default Kickoff Flow

### 1. Ask for the current idea

When the skill starts, ask the user to describe the project idea in whatever form they currently have.

Do not begin by asking many questions.

Use:

> Tell me the project idea as you currently understand it. Rough notes are fine.

### 2. Assess what is known

After the user provides the idea, summarize:

- what the project appears to be
- who it is for
- the practical outcome it should create
- what is already clear
- the biggest gaps or uncertainties
- any likely risks, constraints, or assumptions

### 3. Ask adaptive one-question-at-a-time discovery questions

Ask only the single most important next question when the answer materially affects direction.

Do not run a long questionnaire unless the user asks for one.

Good discovery topics include:

- user / audience
- real-world workflow
- desired V1 outcome
- data inputs and outputs
- privacy and safety constraints
- likely tools/platforms
- success criteria
- what should be avoided
- review/approval needs

Stop interviewing when there is enough to draft useful first documents. Preserve remaining uncertainty instead of blocking progress.

### 4. Use web/current documentation when needed

Use web or current documentation when technical choices depend on facts that may change, such as:

- API availability
- pricing
- OAuth or app verification rules
- platform limits
- deployment rules
- package/library versions
- security requirements
- legal or compliance requirements
- official setup instructions

Prefer official documentation and primary sources.

Do not use web research for ordinary ideation unless the user asks or current facts materially affect the project direction.

### 5. Create the first small document set

After enough discovery, create only this first set by default:

- `Context/IDEA_INTAKE.md`
- `ProjectPlans/STRATEGY.md`
- `ProjectPlans/DECISIONS.md`
- `ProjectPlans/TASKS.md`

Then stop for human review.

Do not create the full workspace in the first pass unless the user explicitly asks for a one-pass full setup.

### 6. First review stop

After creating the first document set, summarize:

- files created or changed
- current recommended direction
- important assumptions
- unresolved questions
- decisions still needed
- recommendations
- what the human should review or correct
- the recommended next step

Do not proceed to full workspace expansion until the user approves.

Approval to expand authorizes creation or updating of the expanded workspace. It does not automatically approve proposed project decisions. Keep a decision `Proposed` unless the user's message explicitly approves it or clearly includes that decision in the approval.

### 7. Expand the full workspace after approval

After approval, create or update:

- `AGENTS.md`
- `ProjectPlans/ROADMAP.md`
- `Context/Decision_Notes.md`
- `Context/3-Hop-Method.md`
- `docs/phase0/01_PHASE0_READINESS_ASSESSMENT.md`
- `docs/phase0/02_PHASE0_CHECKLIST.md`
- `docs/templates/PHASE_PLAN.template.md`
- `docs/templates/PHASE_CHECKLIST.template.md`
- `docs/templates/REVIEW_SUMMARY.template.md`
- `docs/templates/PHASE_RETROSPECTIVE.template.md`
- `docs/templates/PROJECT_RETROSPECTIVE.template.md`
- `z-archive/`

Copy the reusable phase templates into `docs/templates/` as blank structures. They are not active project documents requiring immediate review.

Create a conservative `.gitignore` when appropriate for the project or when the user intends to use Git or GitHub.

Do not create a project `README.md` by default during kickoff. Use `ProjectPlans/STRATEGY.md` as the early project explanation. Create `README.md` only if the user asks, the repository will be shared immediately, or external-facing documentation is needed.

Do not create a project-local `BUILDER_PLAYBOOK.md` by default. Create one only when the user explicitly requests it or a portable snapshot is needed.

## Phase Review Ordering Rule

Name every active, phase-specific review artifact using this pattern:

`NN_PHASE<phase-number>_<DESCRIPTIVE_NAME>.md`

`NN` is a two-digit, zero-padded human review priority within that phase, starting at `01`. It is not the phase number or the order in which the file happened to be created.

Assign the prefix according to the order a human should review the artifacts. Use consecutive priorities for the active artifacts in a phase. For example:

```text
docs/phase1/
  01_PHASE1_PLAN.md
  02_PHASE1_DECISIONS.md
  03_PHASE1_CHECKLIST.md
  04_PHASE1_REVIEW_SUMMARY.md
  05_PHASE1_RETROSPECTIVE.md
```

Adapt the order to the work: a decision, research finding, or risk assessment may rank before the plan when it must be understood first. Keep each prefix stable after creation; if the recommended reading order materially changes, rename the affected phase artifacts together and report the rename in the next human-review summary.

Apply this rule only to active phase artifacts. Keep the reusable blank files in `docs/templates/` unnumbered. Do not silently rename existing project files; propose a migration and wait for approval.

## Template Use Rules

The long project files live in `assets/templates/`.

Use these templates as starting points, not rigid forms. Adapt headings and content to the specific project.

Remove placeholder text that no longer applies.

Preserve useful uncertainty by recording it as:

- assumptions
- open questions
- risks
- unresolved decisions
- human-review items

Do not pretend unknown facts are known.

## Open Questions and TASKS Rule

`ProjectPlans/TASKS.md` must include an `Open Questions / Decisions Needed` section.

Use it to collect unresolved items in one place.

For each item, include:

- the question or decision
- its source
- why it matters
- when it should be resolved
- whether it blocks the current phase
- where the answer should be documented

Not every open question blocks the current phase. Future-phase questions should remain visible without stopping current progress.

## Kickoff Code Rule

Do not rush into implementation during kickoff.

However, the agent may create small code files, runnable examples, prototypes, sample scripts, proofs of concept, pseudocode, or mock data when they materially help the human understand feasibility, compare options, test an assumption, explain architecture, demonstrate a workflow, or make a better project decision.

Kickoff code should be clearly labeled as exploratory, sample, prototype, or proof-of-concept unless the human explicitly approves it as implementation work.

When creating kickoff code, explain:

- why the code is useful now
- how to run it
- what it proves
- what it does not prove
- whether it should be deleted, archived, or converted before implementation

Avoid large implementation work, production integrations, deployment workflows, or irreversible architecture commitments during kickoff unless the human explicitly approves moving beyond kickoff.

## Branch / Recovery Rule

During kickoff and documentation-only setup, do not require a branch or recovery point by default.

When work moves into implementation, material changes to working code, production-like code, deployment configuration, database/schema changes, destructive edits, or changes that could break a working project, use an appropriate safety step first, such as:

- Git branch
- checkpoint commit
- backup
- explicit human approval

If the repo already contains working code, inspect the current state before changing it and avoid destructive edits without approval.

## `.gitignore` Rule

Create a conservative `.gitignore` during full workspace creation when appropriate for the project or when the user intends to use Git or GitHub.

The `.gitignore` should block common secrets, environment files, dependency folders, build outputs, OS/editor noise, logs, and private data folders.

If `.gitignore` already exists, do not overwrite it. Inspect it and propose safe additions.

## Builder Playbook Rule

The authoritative skill-level playbook is `references/BUILDER_PLAYBOOK.md`.

Read it when approved cross-project practices materially affect a kickoff and when comparing promotion candidates during a Project Retrospective.

Do not copy it into a project by default.

Do not edit it continuously during normal project work.

Do not promote one-off lessons into permanent global behavior automatically.

## Compound Learning Rule

Project learning should compound deliberately.

During normal work:

- capture meaningful lessons in Phase Retrospective files
- preserve potentially transferable lessons for the Project Retrospective
- update `ProjectPlans/TASKS.md` when lessons require action
- refine project-local docs when useful

At phase end:

- decide whether a phase retrospective is useful
- run it only when the phase produced meaningful learning, rework, bugs, design changes, tool/environment issues, collaboration friction, major decisions, or reusable patterns
- skip or compress it when the phase was small, straightforward, and produced no meaningful lessons beyond the review summary

When the project reaches a Project Retrospective trigger, or whenever the user asks:

- recommend a Project Retrospective
- gather candidates from Phase Retrospectives, review summaries, human feedback, recurring bugs, rework, important decisions, failures, and successful patterns
- consolidate similar lessons and remove one-off observations that should not transfer
- compare proposals with `references/BUILDER_PLAYBOOK.md`
- identify duplicates, conflicts, and destination files
- present all promotion recommendations together for human approval

After human approval, update:

- `references/BUILDER_PLAYBOOK.md`
- relevant skill templates
- `SKILL.md`, when the process changed
- `README.md`, when human-facing guidance changed
- `agents/openai.yaml`, when invocation metadata changed

Before editing the global skill package, state exactly which files will change and why. After changing them, summarize what future projects will now inherit.

If the human explicitly requests immediate promotion of one lesson, show the exact proposed files and changes, identify duplicate or conflict risks, and obtain approval before applying it.

## Phase Retrospective Rule

A Phase Retrospective serves as a running learning log and a conditional phase-end review. Create its file at the beginning of a phase or when the first meaningful lesson appears.

Complete a substantive review when the phase involved meaningful learning, rework, bugs, design changes, tooling or environment issues, human-agent collaboration friction, major decisions, or reusable patterns.

Skip or compress it when the phase was small, straightforward, low-risk, and free of meaningful reusable lessons or process issues.

When skipped, say:

> No substantive phase retrospective was needed because no major reusable lessons or process issues were identified.

## Project Retrospective Rule

A Project Retrospective is the consolidated promotion gate.

Recommend it when a project appears complete, meaningfully wrapped, paused for an extended period, abandoned, or ready for a major restart or transition. Run it whenever the user requests it.

Present all promotion recommendations together and wait for human approval before updating the skill package.

## Review / Readiness Rule

Before moving from planning into implementation, produce a readiness assessment covering:

- project goal clarity
- V1 scope clarity
- architecture confidence
- unresolved decisions
- privacy/security risks
- validation plan
- first implementation slice
- human review needs

Be honest about what is ready and what is not ready.

## Explanation Style

The user is learning software engineering and agentic coding.

Explain important concepts clearly and simply.

When the user says they do not understand something, asks for a deeper explanation, or asks to slow down, first explain simply, then ask whether they want a deeper explanation using the 3-Hop Method.

The 3-Hop Method:

1. Start with something familiar.
2. Build the bridge from that familiar thing to the new concept.
3. Explain the real concept in plain language before technical terminology.
4. End with a brief recap.

Use a fourth hop only when needed.

The full explanation pattern is stored in `assets/templates/Context/3-Hop-Method.md` and should be copied into each full project workspace.

## Final Response Rule

At each stopping point, report:

- files created or changed, listed in recommended review order when phase artifacts are involved
- decisions recorded
- assumptions preserved
- open questions / decisions needed
- checks performed or skipped
- recommended next action

Keep the final response concise and review-oriented.
