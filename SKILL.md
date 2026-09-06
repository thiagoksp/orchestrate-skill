---
name: orchestrate
description: Coordinate independent work and substantial reviews through Codex agents. Route by difficulty, schedule within available capacity, monitor progress, and integrate evidence while respecting the existing implementation owner and user authorizations.
---

# Orchestrate

The root owns decomposition, user communication, decisions, and integration. Follow the
user's intent and applicable AGENTS.md; this skill does not grant new scope or authority.
Where a workflow requires a verified execution contract or enforced read-only access,
validate those prerequisites before dispatch and follow-up. A read-only prompt is not
proof of isolation. If the executor cannot demonstrate the required boundary, keep that
dispatch pending and continue only independent work permitted to the root.

## Select by difficulty

Delegate when parallel work saves time or independent judgment improves the result.
Assess ambiguity, component coupling, testability, task duration, and consequences of
error. A short patch can require senior judgment; a large, well-specified edit can be
bounded execution. Handle simple sequential work directly without manufacturing subtasks.

| Model | Effort | Preferred assignment |
|---|---|---|
| `gpt-5.6-luna` | `max` always | Bounded execution, substantial but well-specified coding, evidence gathering, focused review, or established workflows. Leaf: does not delegate. |
| `gpt-5.6-sol` | `high` | Independent senior review, bounded diagnosis, or a second opinion on a difficult decision. |
| `gpt-6-astra` | `medium` | Default choice for new coordination assignments and implementation connecting multiple components. |
| `gpt-6-astra` | `high` | Ambiguous requirements, difficult architecture, consequential decisions, or diagnosis needing deeper investigation. |
| `gpt-6-astra` | `xhigh` or `max` | Exceptional work justified by unresolved difficulty or explicit user selection; not automatic escalation. |

Preserve explicit user model choices and the configured parent; routing is not permission
to change app settings or silently replace a persistent Coder. Luna is never silently
downgraded from max. Other model routes require an explicit user choice.

Check the available tool's model, effort, permission, and capacity metadata before
dispatch. Reuse that information until it changes; do not probe unavailable models with
repeated spawns. A model available in the app is not necessarily available through every
delegation tool. When a preferred route is unavailable, disclose it and use a supported
route from this table when appropriate; otherwise retain the work at the root within its
role or report the specific blocker. Do not create unrelated tasks to bypass limits.

Use observed outcomes, cost, latency, and rework to refine routing. There is no fixed
percentage of work assigned to each model. For a model-selection decision, consult
[model evidence](references/model-evidence.md) only when useful. Its dated DeepSWE
results are supporting evidence, not success probabilities for the user's task.

## Divide and schedule dynamically

Before implementation, check for a designated persistent Coder in the same project.
Verify its destination and send the authorized packet there rather than create a
competing implementer. Independent reviewers may work alongside it. If delivery fails,
retain the packet using the project's local handoff convention, inspect the failure,
and pursue available in-scope recovery; never make the user relay technical messages.

Each work unit needs an outcome, acceptance evidence, relevant sources/revision,
dependencies, owner and writable surfaces, current authority, requested model/effort,
and a useful next checkpoint. Assign one owner to each mutable surface. Prefer
`fork_turns: "none"` and a bounded packet; inherit history only when it materially helps.

Maintain a compact queue of ready, running, waiting, and completed units. Concurrency is
not a total task limit: no fixed trio, headcount target, or total-agent ceiling is imposed
by this skill. Respect actual runtime limits and their counting convention. Dispatch
ready independent units as capacity permits, reusing agents for dependent follow-ups.
After each result or material discovery, reassess the queue and launch the next useful
units. If nothing is ready but necessary work is still running, wait and supervise.
Do not end the task merely because the first group finished.

An Astra or Sol workstream owner may coordinate children when the root explicitly assigns
that responsibility. The root may revise that assignment as the task develops; this is
an internal scheduling choice within existing authority, not another user approval gate.
Nested delegation shares the same scope, ownership rules, and runtime limits. Keep Luna
as a leaf. Reuse or close completed agents when supported; preserve persistent Coders.

Before a spawn, briefly disclose task name, exact requested model and effort, and
leaf/coordinator role. Group simultaneous disclosures. Report runtime substitutions when
observable; a requested configuration is not proof of actual runtime identity.

### Adapt these scenarios

These are starting points, not fixed teams or mandatory stages:

- **Small correction:** existing Coder or one bounded executor, with focused verification.
- **PR or release:** distribute independent risk questions; assign one owner to shared
  test/CI evidence and keep integration with the root.
- **Cross-component change:** use an Astra coordinator with independent implementation
  owners or reviewers wherever ownership and dependencies permit.
- **Investigation:** divide by competing hypotheses, evidence sources, or components;
  expand or combine units as evidence changes.
- **Long-running operation:** retain its operation handle, continue useful independent
  work, and wait when a dependency requires the result. Do not launch duplicate jobs.

When a repository requires a committee, cover each required specialty with a bounded
question. Parallelize independent questions and sequence dependent ones. Report any
missing required review; neither a template nor available slots determine committee size.

## Supervise execution

Keep a compact progress record per unit: last concrete evidence, pending operation
handle, blocker/question, next checkpoint, and attempts already made. Use task-wait tools
with cursors or agent waits; inspect details at milestones or when progress is uncertain.
Keep individual waits bounded so user updates remain timely. Do useful independent root
work when available, without editing worker-owned files or inventing filler work.

Distinguish legitimate waiting from repetition. An active test, transfer, or service
wait may take time without new output. Elapsed time or an unchanged status alone is not
a loop. Investigate when an expected checkpoint is missed or when the agent repeats the
same plan, reads, command, or error without a new hypothesis or useful evidence.

Intervene with a focused question or correction. If an agent returns preparation instead
of the requested result, check its active task, mode, packet, and scope first. On a mismatch,
suspend dispatch, confirm the worker stopped, and preserve/compare the checkpoint before
recovery. An empty response or a sent stop message is not proof of containment. When the
contract matches but the result is incomplete, identify the unmet outcome and redirect it.
If repetition persists, interrupt the affected unit, retain evidence, and narrow or
reassign the work within existing authority. Do not spawn replicas of the same stalled work.
Observe the applicable retry limit; by default, at most three attempts of the same
failing action/cause across all agents. Each retry needs a changed hypothesis, input,
or environment. Reassignment does not reset the count. Stop that action at the limit
and route the evidence to the root; bring genuine user decisions or unresolved authority
needs to the user.

Workers send unresolved questions, failures, scope conflicts, and approval needs to the
root with evidence, prior attempts, and a recommended next step. They may continue
independent authorized work while the affected action waits. The root resolves technical
choices in scope and continues review/correction directly with the worker.

Treat new user messages as steering by default: answer side questions and preserve the
original objective, completed work, and constraints. Replace the objective only when
the user cancels it or requests incompatible work. For missing optional preferences,
use an asynchronous question when available and continue independent work; elapsed time
does not supply required approval.

When notes or searchable prior context are available, recover earlier decisions, failed
attempts, and evidence before redoing work. Otherwise retain a compact handoff at context
boundaries. This skill does not enable experimental context features, async APIs, or
dynamic effort changes that the current tool does not support.

## Verify and integrate

Assign one owner to expensive shared checks. Record command, revision/inputs, result,
and relevant environment so reviewers can reuse fresh evidence. Repeat or broaden checks
only after relevant changes, a failure, or a named unresolved concern. Independent review
should challenge the result, not automatically rerun the whole suite. Do not add tests
that merely mirror wording or reversible low-impact edits.

Require compact `Verdict`, `Findings`, `Risks`, `Recommendation`, and `Evidence` returns.
Check the actual artifact and acceptance criteria; a worker's completion message is not
acceptance. Resolve disagreements against primary evidence, send bounded authorized
corrections, and re-review affected work. Recheck live external state before claiming
publication, merge, deployment, or another externally completed action.

Finish when the authorized outcome and required verification are complete, or at a real
user decision, authority gate, or unresolved blocker. Do not end solely because an agent
is still working or a follow-up is needed. Return one integrated result with material
limitations; do not dump worker transcripts or repeat unchanged status messages.
