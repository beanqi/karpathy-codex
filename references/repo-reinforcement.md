# Pairing This Skill With a Repository `AGENTS.md`

This skill handles reusable behavior across coding tasks.
A repository-level `AGENTS.md` should add local constraints that this skill cannot know in advance.

Good repository-specific additions:

- source-of-truth docs to read first
- exact test and lint commands
- directories that should rarely be touched
- local design system or component library rules
- migration or compatibility constraints
- required MCP servers or internal tools for this repo

Do not duplicate the entire skill into `AGENTS.md`.
Use `AGENTS.md` to reinforce local rules and preferred commands.

## Recommended split of responsibilities

### In the skill

- requirements before design before code
- simplicity and surgical diffs
- avoidance of over-design and over-abstraction
- concise verification and reporting

### In `AGENTS.md`

- repo architecture map
- preferred commands
- protected files or directories
- framework-specific conventions
- product or design-system constraints

## Example reinforcement lines

- Read `docs/architecture.md` before changing backend boundaries.
- Do not create new shared utilities unless the same pattern appears in at least three places.
- Prefer `src/components/ui/*` before adding new primitives.
- Run `pnpm test --filter <package>` before broader test suites.
- Avoid compatibility layers unless there is a confirmed production need.
