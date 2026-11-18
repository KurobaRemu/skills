---
name: whiteboard-defense
description: Oral whiteboard defense checking the user's high-level grasp of customer-facing work. Use when preparing to ship or open a PR on production work, or when asked to test understanding of a system or change.
---

Run an **oral whiteboard defense** as a skeptical staff engineer. Verify that the user understands the system they are about to ship at an architectural level and can defend its **load-bearing** decisions.

## 1. Scope gate

Confirm in one sentence whether this work is **customer-facing** or a **PoC / demo / experiment** (skip asking if already stated).

- **PoC / demo / experiment**: Stop immediately: speed wins here.
- **Customer-facing**: Proceed to **Recon**.

## 2. Silent recon

Read the target diff, branch changes, design spec, or named modules yourself; dispatch a read-only subagent with a fresh context window if the surface is wide. Gather every fact directly from the workspace before asking anything.

Distill two things privately (withhold them until **Debrief**):

1. **Mental model**: End-to-end flow, component boundaries, and state ownership.
2. **Load-bearing points**: 3-6 concrete choices, implicit assumptions, or shifted failure/security/scale boundaries found in this specific change.

Every question must anchor to a real choice or boundary in this work. Use these lenses only when the change actually touches them:
- *Why X over Y?* (chosen design vs rejected alternative)
- *Adversarial / unexpected actor* (abuse, untrusted input, replay, race)
- *Data & state* (storage/structure choice, ordering, scale cliff)
- *Failure & rollout* (first failure mode, blast radius, rollback/migration)

Frame every question around system behavior, boundaries, and constraints; save file paths and symbol names for **Debrief**.

## 3. Defense rounds

Run an interactive **blind** defense in rounds (1-2 questions per round; one question, one target), pausing for the user's answer each time:

- **Open**: Ask the user to explain **how the change works end to end** on a whiteboard.
- **Probe**: Work through unresolved **load-bearing points** dynamically, following threads exposed by the user's answer rather than a fixed checklist; mark points already defended cleanly as `Clear` and skip them.
- **Ask cold**: Pose open-ended questions and wait for the user's unassisted answer before introducing options, hints, or code facts.
- **Challenge vagueness**: When an answer leans on buzzwords, hand-waving, or "the AI handled it," press once with a concrete edge scenario from the actual design.
- **Track silently**: Grade each point internally as `Clear` (sound reasoning), `Shaky` (needs one follow-up), or `Gap` (blind spot, wrong mental model, or user concedes).

## 4. Debrief

End only when every **load-bearing point** is resolved to `Clear` or `Gap` (zero `Shaky` points remaining), or the user stops the session (if stopped early, settle any remaining `Shaky` points as `Gap`).

Deliver a concise **Whiteboard Verdict**:
- **Verdict**: `Ready to ship` or `Close gaps first`.
- **Defended cleanly**: Points graded `Clear`.
- **Gaps exposed**: For each `Gap`, explain the real behavior or risk observed, now citing exact file paths, symbols, or spec sections so the user can inspect or fix them.
