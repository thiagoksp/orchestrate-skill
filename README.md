# Orchestrate

**English** | [Português (Brasil)](README.pt-BR.md)

A personal adaptation of Rafael Quintanilha's Orchestrate skill for coordinating
specialized Codex sub-agents while keeping scope,
authorization, integration, and the final answer under the root agent's control.

This public repository, `thiagoksp/orchestrate-skill`, is the canonical source for
Thiago's version of the skill.

## Original work and credits

The original **Orchestrate** skill was created by
[Rafael Quintanilha](https://github.com/rafaelquintanilha) and published in
[rafaelquintanilha/skills](https://github.com/rafaelquintanilha/skills).

- [Original skill](https://github.com/rafaelquintanilha/skills/tree/master/skills/orchestrate)
- [Original SKILL.md at revision `8c4991b`](https://github.com/rafaelquintanilha/skills/blob/8c4991b3852de693b2af529723b960bf76700f5a/skills/orchestrate/SKILL.md)

The initial `SKILL.md` imported here matches the upstream Git blob
`ef41630867715f8e24890e0e5ed9a7b86ce65004`. This repository maintains a separate,
modified copy; it does not claim authorship of the original skill or endorsement by
its author. The adaptations are described below; credit for the original remains with
Rafael Quintanilha.

## When to use it

Use Orchestrate when a task has genuinely independent workstreams, a long-running
operation that should not block the conversation, a bounded parallel investigation, or
an independent review that materially reduces risk. Small or tightly sequential tasks
stay with the root agent.

The default routing uses:

- Luna for bounded execution agents, evidence gathering, and established workflows. In
  the skill, **leaf agent** means an agent that owns a bounded assignment and does not
  delegate further; it does not mean a literal sheet or page;
- Terra for a collaborative implementation or coordination workstream;
- Sol for independent senior judgment on ambiguous or high-impact decisions.

See [SKILL.md](SKILL.md) for the complete routing, disclosure, assignment, committee,
authority, and synthesis rules.

## What this version adds

- structured specialist handoffs using `Verdict`, `Findings`, `Risks`,
  `Recommendation`, and `Evidence`;
- safe fallback when a model, tool, slot, or usage quota is unavailable;
- respect for a persistent Coder or another explicitly assigned implementation owner;
- repository committees converted into bounded decision questions;
- no repeated spawning without a concrete change in availability.

The skill can be selected automatically by global or repository instructions, or invoked
explicitly as `$orchestrate`.

## Install

Prerequisites: Git, Codex, and a model/runtime that provides Codex collaboration tools.

```powershell
$orchestrateCodexRoot = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $env:USERPROFILE ".codex" }
$orchestrateSkillsRoot = Join-Path $orchestrateCodexRoot "skills"
New-Item -ItemType Directory -Force -Path $orchestrateSkillsRoot | Out-Null
git clone https://github.com/thiagoksp/orchestrate-skill.git (Join-Path $orchestrateSkillsRoot "orchestrate")
```

To update an existing installation:

```powershell
$orchestrateCodexRoot = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $env:USERPROFILE ".codex" }
$orchestrateSkillPath = Join-Path $orchestrateCodexRoot "skills\orchestrate"
git -C $orchestrateSkillPath pull --ff-only
```

Start a new Codex task after installing or updating so the skill and global rules are
reloaded.

## Governance

This repository is Thiago's canonical adaptation. Proposed changes are reviewed before
they are merged. Preserve upstream attribution in subsequent copies and adaptations.

No explicit license was found in the upstream repository when checked on 2026-09-02.
This attribution does not add a license or grant rights to the original work.
