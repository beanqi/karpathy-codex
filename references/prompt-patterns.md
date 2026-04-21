# Prompt Patterns for Karpathy Codex

Use these examples as trigger patterns and usage references.

## Good prompts for requirement-first coding work

- Before coding, help me clarify the requirements, propose the smallest design, then implement it.
- Do not jump into code yet. First restate the requirements and identify the key design choice.
- I want the minimal safe fix. Align on the requirement, then plan, then patch.
- Help me scope this feature conservatively before we touch the code.

## Good prompts for coding work

- Find the root cause of this bug and fix it with the smallest safe diff.
- Review this PR diff and call out only the highest-signal issues.
- Refactor this file carefully without changing behavior.
- Add tests only for the code paths changed in this patch.
- Explain this module and suggest the simplest improvement path.

## Good prompts for UI and design implementation

- Compare this screenshot to the current implementation and make the smallest change that fixes the mismatch.
- Implement this modal using the existing design system and keep the diff minimal.
- Clean up this component layout without changing unrelated styles.
- Bring this screen closer to the spec using existing tokens and components.
- First align on the intended UX, then propose the smallest UI change, then implement it.

## Good follow-up prompts

- Keep the current architecture. Avoid introducing new abstractions.
- Rework this using patterns already present in the repo.
- Before editing, summarize the requirements, likely root cause, and smallest fix.
- Keep the patch easy to review.
- Do not over-design, over-abstract, or add speculative fallback logic.

## Prompts to avoid

These are likely to push the model away from the intended style:

- Rewrite this whole subsystem in a cleaner way.
- Modernize everything in this folder.
- Make this more scalable, elegant, and reusable.
- Improve the styling across the app for consistency.
- Design the ideal architecture for this area before coding.

If the user gives a broad prompt like these, narrow the work to the smallest viable outcome first.
