# Agent execution guidance

Use this reference when dispatching or supervising work. It supplies operational detail
for SKILL.md; the project and user retain control of scope and authorization.

## Assign and schedule

Identify the outcome, relevant sources/revision, dependencies, owner, permitted writable
surfaces, prohibited actions, current mode, and acceptance evidence. Include a useful
checkpoint for longer work and allow necessary generated test/build outputs explicitly.
Prefer a bounded packet over full conversation history; reuse context already available.

When a persistent Coder owns implementation in this project, verify its destination and
dispatch directly there. Reviewers can work independently. If delivery fails, preserve
the packet in the project's handoff location and pursue in-scope recovery; the user should
not relay technical messages. Never give two workers overlapping writable ownership.

Keep ready, running, waiting, and completed units in a compact queue. Use actual runtime
capacity and its counting convention. When capacity becomes available, reuse a suitable
worker or dispatch the next ready unit. Close completed agents only when the tool supports
it; preserve persistent Coders. If dependencies are still running, supervise and wait.
Reassess after results or discoveries rather than ending after the first group.

Astra Low/Medium may coordinate children when the root assigns that responsibility; the root can
revise the assignment as the task develops. This internal scheduling decision needs no
new user approval when scope and authority stay unchanged. Nested work shares the same
ownership and capacity limits. Luna does not delegate.

Before spawning, briefly disclose the requested model/effort, task name, and role.
Group simultaneous disclosures. Do not present requested settings as verified runtime
identity. Supply both model and effort to avoid accidental parent/default inheritance.
Prefer `fork_turns: "none"` for temporary specialists unless inherited history materially
helps. Keep existing Senior/Coder chats and their history, context windows and compaction
settings intact; do not recreate or compact them to meet a helper's cost target.

Scenarios are examples, not fixed teams:

- Small correction: use the existing Coder and focused acceptance.
- Review: divide independent risk questions; one owner gathers shared test/CI evidence.
- Cross-component work: separate writable ownership and put dependencies in the queue.
- Investigation: divide by hypothesis, source, or component, then adjust with evidence.
- Long-running operation: retain its handle and avoid launching duplicate jobs.

Cover repository-required review specialties with bounded questions. Parallelize only
independent work; report a required review that could not be completed.

## Monitor and recover

Track the last concrete evidence, pending operation handle, blocker, next checkpoint,
and attempts per unit. Use compact task-waits with cursors or agent waits. Inspect details
at milestones or when evidence is missing. While workers run, do useful independent work
without editing their files, repeating checks, or inventing filler tasks.

Time without output is not itself a loop. Check the active operation when a checkpoint
is missed. Repeating a plan, read, command, or error without a new hypothesis or useful
evidence warrants focused intervention.

First confirm the current task, mode, root, and packet. On an actual mismatch, pause,
confirm worker status, and inspect differences before recovery. A sent stop message,
silence, or green tests do not prove containment or unchanged files. For incomplete work
within the correct scope, identify the unmet result and redirect the worker.

Carry retry counts with the failing action/cause across agents. Respect the applicable
limit, normally three attempts, and require a changed hypothesis, input, or condition for
each retry. Do not reset the count by reassigning work. If repetition persists, interrupt,
preserve evidence, narrow the problem, and bring unresolved decisions to the root.

Workers route uncertainty and scope/permission needs to the root with evidence, attempts,
and a recommended next step. Continue independent authorized work while an affected
action waits. Do not demand custom isolation, permission probes, or disabled connectors
as a default; actual permissions and task-specific external authorizations still apply.

## Verify and finish

Assign one owner to expensive shared checks. Record their command, revision/inputs,
environment, and result so reviewers can reuse fresh evidence. Broaden or repeat checks
for relevant changes, failures, explicit requests, or a named concern, not as a ritual.
Independent review challenges the result without automatically rerunning the whole suite.

Require compact Verdict, Findings, Risks, Recommendation, and Evidence. Inspect scope
and actual artifacts before accepting a worker's report. Resolve conflicting findings
against primary evidence, send authorized corrections, and re-review the affected work.
Recheck external state before claiming publication, merge, deployment, or another live
outcome. These actions keep their distinct authorization gates.

New user messages normally steer the active task: answer questions while retaining the
objective, constraints, and completed work. Use available notes or searchable prior
context to recover decisions and failed attempts before repeating work. If those features
are unavailable, keep a compact handoff; do not enable experimental app settings just
because this reference mentions them.

Continue until the authorized result is complete or a real decision/gate/blocker remains.
Give the user a concise integrated result rather than worker transcripts.
