# Workflow Patterns

Use these patterns when the task benefits from a short structured flow before coding.

## Pattern 1: Requirements Summary

Use for medium or large tasks.

- Goal: what outcome is actually needed
- Constraints: what must stay unchanged
- Unknowns: what is still unclear
- Assumptions: what will be assumed if proceeding now
- Success criteria: what would count as done

Example:

- Goal: add bulk archive to the notifications page
- Constraints: keep current API contract and table layout
- Unknowns: whether archived items should disappear immediately
- Assumptions: optimistic UI removal is acceptable unless told otherwise
- Success criteria: multi-select archive works, existing single-item archive still works, tests cover reducer changes

## Pattern 2: Smallest Viable Design

Keep design discussion short.

- Change surface: which files or layers likely change
- Chosen approach: the narrowest implementation that solves the task
- Why this is enough now: why broader alternatives are unnecessary
- Risk check: likely regression area or edge case

Example:

- Change surface: notifications toolbar, reducer, archive action, one integration test
- Chosen approach: reuse existing single-item archive action in a batched loop on selected ids
- Why this is enough now: avoids inventing a new bulk API until current limits are proven
- Risk check: selection state and optimistic update ordering

## Pattern 3: Minimal Implementation Plan

A plan should be executable, not performative.

1. inspect existing archive flow and selection state
2. add bulk action wiring in toolbar and reducer
3. reuse current archive request path for selected ids
4. add or update the narrowest tests
5. verify UI flow and summarize residual risks

## Pattern 4: Compression For Tiny Tasks

For a very small task, compress the flow into three lines:

- Requirement: what exact thing must change
- Design: smallest place to change it
- Verify: smallest check to confirm it worked

Example:

- Requirement: button label should read “Save draft” on mobile
- Design: change the label in the shared button prop without touching behavior
- Verify: inspect mobile render snapshot or relevant component test
