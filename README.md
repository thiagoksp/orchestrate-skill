# Orchestrate

**English** | [Português (Brasil)](README.pt-BR.md)

A personal adaptation of Rafael Quintanilha's Orchestrate skill for coordinating
specialized Codex sub-agents while keeping scope, authorization, integration, and the
final answer under the root agent's control.

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

Use Orchestrate when independent work can run in parallel, a long-running operation
needs supervision, or independent review improves the result. The root adapts the team
as the task develops and handles simple sequential work directly.

The default routing uses:

- **Luna Max** for bounded execution, coding, evidence, and focused review. A leaf agent
  owns an assignment and does not delegate further;
- **Sol High** for independent senior review and bounded diagnosis;
- **Astra Medium** for new coordination assignments and work across components;
- **Astra High** for difficult ambiguity, architecture, and consequential decisions;
- **Astra XHigh/Max** only when unresolved difficulty or explicit selection warrants it.

Explicit user choices and available model/effort capabilities take precedence. The skill
does not change the parent model or app settings. See [SKILL.md](SKILL.md) for routing and
supervision, and [model evidence](references/model-evidence.md) for the dated DeepSWE and
official GPT-6 references used to inform the policy.

## What this version adds

- Dynamic scheduling: no fixed trio or total task ceiling; actual concurrent capacity
  controls how many independent units can run at once. Remaining work stays queued.
- Progress supervision: distinguish a legitimate wait from repeated work without new
  evidence; intervene, retain context, and carry retry counts across reassignment.
- Evidence reuse: one owner for expensive shared checks, with additional verification
  justified by changes or unresolved concerns.
- Persistent Coder ownership and direct Senior coordination, without manual message relay.
- Steering and context continuity, using notes or searchable history when available.
- Compact specialist returns: `Verdict`, `Findings`, `Risks`, `Recommendation`, `Evidence`.

Scenarios are adaptable examples, not mandatory teams. The root can assign Astra or Sol
coordination within the authorized scope. A skill cannot increase runtime capacity or
enable experimental features; those are separate configuration decisions.

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
