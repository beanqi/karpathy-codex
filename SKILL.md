---
name: karpathy-codex
description: "karpathy-style coding and implementation guardrails for codex. use when chatgpt or codex is asked to write, edit, refactor, review, debug, test, or explain code, or to implement ui from specs, screenshots, or design notes. apply this skill to keep work thoughtful, simple, and review-friendly: align on requirements before coding, discuss the smallest viable design before implementation, turn approved direction into a minimal plan, then code with small surgical diffs. strongly prefer existing repository patterns and explicitly avoid over-design, over-abstraction, and over-defensive fallback logic. especially useful for bug fixes, feature work, refactors, code review, ui polish, and design-to-code tasks where minimal, high-signal changes matter."
---

# Karpathy Codex

## Overview

Use this skill as a coding stance and execution discipline, not as a framework-specific rulebook.
Apply it alongside more specific repo instructions, framework guidance, tool-specific skills, and installed skills. Keep those more specific instructions when they conflict with this skill.

This skill combines two ideas into one reusable flow:

1. Do not jump straight into code. Align on the task first, then confirm the design, then implement.
2. Once implementation starts, keep the solution simple, local, and easy to review.

Use the full workflow for non-trivial work. For obvious, low-risk, narrowly-scoped tasks, compress the workflow into a short requirements summary, a one-paragraph design choice, and then implementation.

## Priority Order

Follow instructions in this order:

1. System, developer, and user instructions
2. More specific installed skills for the current toolchain or task
3. This skill's workflow and simplicity rules

Do not let this skill override direct user requests or repository constraints.

## Core Principles

### 1. Requirements before design before code

When the task is not completely obvious, do not start coding immediately.
First clarify what outcome is actually wanted.
Then choose the smallest design that satisfies it.
Only then implement.

### 2. Think before coding

Read the relevant files before proposing changes.
Identify the likely root cause, local constraints, and the smallest reasonable place to intervene.
For non-trivial tasks, state a short plan before editing.

### 3. Prefer simplicity first

Choose the simplest approach that fully solves the current request.
Prefer existing patterns, components, helpers, and conventions over new abstractions.
Introduce a new abstraction only when repetition or complexity clearly justifies it now.

### 4. Make surgical changes

Keep the diff as small as possible while still solving the task correctly.
Avoid unrelated cleanup, broad renames, formatting churn, and speculative rewrites.
Preserve working architecture unless the user explicitly asks for redesign.

### 5. Stay goal-driven

Tie every code change to the user's requested outcome.
Do not drift into “while I am here” improvements unless they are required for correctness.
When tradeoffs exist, pick the option that is easiest to review, verify, and maintain.

### 6. Add Chinese comments on key code elements

When writing or modifying code, add concise Chinese comments above key functions, structs, and important fields.
This is a default documentation requirement for this skill, unless the user or repository explicitly requests another language.

Comment scope:

- key functions: explain purpose, core behavior, and important side effects
- key structs/types: explain responsibility and major usage context
- important fields: explain meaning, unit/range, or lifecycle constraints when not obvious

Comment placement and style:

- place comments directly above the target function, struct/type, or field
- use concise Chinese; avoid repeating what the name already says
- prefer intent and constraints over line-by-line narration
- keep comments updated when behavior changes
- for trivial local variables or obvious one-liners, comments are optional

## Default Workflow

### Phase 1: Align on requirements

Before designing or coding, establish what success means.

For non-trivial tasks:

- restate the task in concrete terms
- identify missing constraints, assumptions, or acceptance criteria
- ask focused clarifying questions when the uncertainty is blocking
- if asking would create too much friction, state the assumptions explicitly and proceed conservatively

Good requirement outputs are short and testable.
Avoid vague restatements like “improve architecture” or “make it cleaner.”
Translate them into specific outcomes.

### Phase 2: Discuss the smallest viable design

After requirements are clear enough, describe the implementation approach before changing code.

For non-trivial tasks, include:

- the likely root cause or implementation approach
- the files or layers likely to change
- the smallest design that solves the problem
- why broader alternatives are unnecessary right now

Present the design in chunks small enough to review quickly.
Do not dump a giant spec unless the user explicitly wants one.

### Phase 3: Turn the design into a minimal implementation plan

Once the approach is acceptable, turn it into a compact execution plan.

A good plan:

- breaks the work into a few concrete steps
- names the likely files or modules when known
- includes validation or test steps
- is detailed enough to execute, but not bloated into project-management theater

Prefer small, reviewable steps over long speculative roadmaps.

### Phase 4: Implement carefully

Edit only the files needed for the task.
Reuse existing helpers before creating new ones.
Keep function signatures and public interfaces stable unless the request requires otherwise.
Preserve comments and docs when still accurate; update them when behavior changes.
For newly added or modified key functions, structs/types, and important fields, add concise Chinese comments above them.

### Phase 5: Verify and report

Run or describe the smallest meaningful validation available.
At the end, summarize:

- what changed
- why it changed
- how it was verified
- remaining risks, assumptions, or follow-up work

## Compression Rule

Do not force a long requirements-design-plan ceremony for a tiny task.
If the request is already specific, low-risk, and local, compress the workflow into:

1. a brief task framing
2. a brief design choice
3. implementation and verification

The goal is deliberate execution, not bureaucracy.

## Anti-Patterns to Avoid

### Do not over-design

Do not introduce a new architecture, plugin system, service layer, or generalized framework unless the present task clearly needs it.
Do not optimize for hypothetical future features.
Do not create extension points “just in case.”

### Do not over-abstract

Do not extract helpers, base classes, hooks, utilities, or shared layers only to make code look cleaner.
Abstract only when duplicated logic or current complexity makes the local code meaningfully worse.
Prefer a little duplication over premature indirection.

### Do not over-defend or over-pad

Do not add fallback branches, configuration knobs, guards, retries, feature flags, or ultra-defensive handling unless:

- the current requirements call for them
- the repository already expects them in this area
- there is concrete evidence of the failure mode being handled

Avoid code that exists mainly to soothe anxiety rather than solve the task.

### Do not turn planning into theater

Do not produce huge specs, exhaustive option matrices, or long implementation plans when a short one would do.
Do not invent extra phases, subprojects, or follow-up tickets without a real need.

## Task-Specific Guidance

### Bug fixes

Reconstruct the failure mode before patching.
Trace the bug to the narrowest likely cause.
Avoid shotgun fixes across multiple layers unless evidence supports it.
If the exact reproduction is unavailable, say what assumption the fix is based on.

### Feature work

Fit the feature into the existing architecture before inventing a new one.
Favor incremental extension of current modules, routes, components, and state flows.
Add only the minimal API surface needed for the feature.

### Refactors

Refactor only when it directly supports the requested outcome or meaningfully reduces risk.
Prefer extraction, renaming, and simplification over structural rewrites.
Keep behavior unchanged unless the user asked for behavior changes.

### Code review

Prioritize correctness, security, reliability, and maintainability.
Call out the highest-signal issues first.
Prefer concrete, minimal suggestions over broad stylistic opinions.
When a diff is acceptable, say so clearly.

### Test work

Add the narrowest tests that prove the changed behavior.
Reuse existing test style, fixtures, and helpers.
Do not add a large new testing harness unless the repository already uses it or the user explicitly asks.

### UI and design implementation

Treat design work as implementation constrained by the existing product.
Match nearby patterns before inventing new layout or interaction rules.
Prefer existing design tokens, spacing scales, typography, and shared components.
When given screenshots, specs, or design notes:

- identify the minimum visible difference that matters
- map it to the current component structure
- implement the smallest change that closes that gap

Do not invent a new design system.
Do not restyle unrelated screens for visual consistency.
If important design context is missing, proceed conservatively and state the assumptions.

## Output Style

For non-trivial tasks, usually present work in this order:

1. requirements summary or assumptions
2. smallest viable design
3. minimal implementation plan
4. implementation and verification result

Keep each section compact.
Prefer plain language over jargon.

## Do Not

Do not start coding before reading the relevant files.
Do not skip requirements and design discussion on non-trivial work.
Do not introduce new abstractions by default.
Do not mix unrelated cleanup into the same diff.
Do not claim certainty when the evidence is partial.
Do not hide risk, assumptions, or skipped verification.

## Resources

Use these bundled references when needed:

- `references/prompt-patterns.md` for example prompts that trigger this skill well
- `references/repo-reinforcement.md` for guidance on pairing this skill with a repository-level `AGENTS.md`
- `references/workflow-patterns.md` for sample requirement, design, and plan formats
- `assets/AGENTS.md.example` as a copyable repo-local companion file
