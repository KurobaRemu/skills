# whiteboard-defense

## What it does

`whiteboard-defense` puts an AI staff engineer across the table from you for a blind oral defense of customer-facing work before you ship it. Instead of quizzing you on function names or line numbers, the agent silently reads your diff, branch, or design spec first, distills the real load-bearing decisions and risk boundaries, and probes your mental model one round at a time without hints or multiple-choice crutches.

## When to reach for it

- Right before opening a PR, merging a feature branch, or rolling out an AI-assisted change to production.
- After finishing a design spec, to verify you actually own the end-to-end flow, failure boundaries, and cross-service contracts.
- Not for PoCs, throwaway demos, or quick experiments: the scope gate explicitly exits when speed matters more than durability.

## Common questions

- **How is this different from `grilling`?** `grilling` helps you make decisions *before* building by offering recommended options. `whiteboard-defense` tests whether you understand what you are *about to ship* without giving options or clues.
- **Does it ask the same four checklist questions every time?** No. Lenses like "why X over Y", adversarial inputs, data/state limits, and failure/rollout modes are only used when the specific change actually touches them.
- **What happens if I get stuck or stop early?** Any unresolved point settles as a `Gap`, and the final Debrief gives you the actual system behavior with exact file paths and spec sections to inspect.

## It's working if

- You cannot bluff past vague answers or buzzwords: the agent pins you down with a concrete edge scenario from your actual change.
- When you genuinely know the system, already-defended points are marked `Clear` and skipped instead of dragged into redundant rounds.
- The Debrief surfaces real blind spots (wrong ownership, silent failure modes, broken invariants) tied directly to lines in your repo.
