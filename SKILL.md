---
name: orchestrate
description: Coordinate agents for independent work, substantial investigations, or reviews that benefit from separate perspectives.
---

# Orchestrate

The root owns the outcome, user communication, scope, and final integration. Delegate
when independent work saves time or improves the result; handle simple sequential work
directly. Preserve the user's explicit model choices, current authorization, and any
designated persistent Coder.

## Route by difficulty

Consider ambiguity, component coupling, testability, duration, and consequence of error,
not patch length or a fixed percentage of work assigned to each model.

| Model | Effort | Preferred assignment |
|---|---|---|
| `gpt-5.6-luna` | `max` always | Bounded execution, coding, evidence gathering, and focused review; leaf, no delegation. |
| `gpt-5.6-sol` | `high` | Independent senior review and bounded diagnosis. |
| `gpt-6-astra` | `medium` | New coordination assignments and implementation across components. |
| `gpt-6-astra` | `high` | Difficult ambiguity, architecture, or consequential decisions. |
| `gpt-6-astra` | `xhigh` or `max` | Exceptional unresolved difficulty or explicit user selection. |

Use only model/effort combinations available through the selected tool. Preserve the
configured parent; do not silently downgrade Luna, replace a persistent Coder, or change
app settings. Disclose a supported fallback when necessary. Do not create unrelated
tasks or repeat unavailable spawns to bypass capacity limits.

## Load the relevant guidance

- **Dispatching or supervising agents:** read [execution guidance](references/execution.md)
  for ownership, dynamic scheduling, progress, recovery, and verification.
- **Reconsidering model choice or effort:** consult [model evidence](references/model-evidence.md)
  when dated benchmarks or capability notes help the decision. Do not load it for routine
  dispatch or treat benchmark scores as task-success probabilities.
- **Role and authority questions:** consult the project's delivery workflow or the shared
  Senior/Coder workflow when applicable. Reuse an already-current packet and instructions.

## Completion contract

Name the outcome and acceptance evidence before delegating. Concurrency limits how many
units run at once, not the total useful work: maintain a queue and reassess it as results
arrive. There is no mandatory trio or headcount target. The root may authorize Astra/Sol
coordination within the existing scope; Luna remains a leaf.

Prompt-based scope plus Senior review is the default unless an explicit applicable rule
requires more. Read-only work must not write files or external state, but a custom sandbox
or cryptographic contract is not a general prerequisite. Do not claim prompts enforce
technical isolation or weaken actual tool permissions.

Follow through on implementation, verification, and corrections already authorized.
Reuse fresh evidence and distinguish a legitimate pending operation from repetition.
Preserve the objective and completed work when the user steers the task. Finish at the
verified outcome, a real decision, an authority gate, or an unresolved blocker; a worker
still running or returning a first draft is not a reason to stop.
