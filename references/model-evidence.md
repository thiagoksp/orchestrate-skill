# Model-routing evidence

Consult this reference for model/effort selection or a routing review, not for every
dispatch. The routes in SKILL.md are Thiago's approved operating preferences. Benchmark
results inform those preferences; they do not override explicit choices or runtime limits.

## DeepSWE snapshot — 2026-09-06

Source: [Datacurve DeepSWE](https://deepswe.datacurve.ai/), v1.1, leaderboard updated
2026-09-03. The per-effort rows were read from the public page's embedded leaderboard
data. Select **All effort levels** to inspect the configurations. The
[data view](https://deepswe.datacurve.ai/data/v1.1) provides individual rollout outcomes.

| Model | Effort | Reported pass rate | Mean output tokens | Attempted rollouts |
|---|---|---|---|---|
| GPT-5.6 Luna | xhigh | 56.9% | 44,678 | 452 |
| GPT-5.6 Luna | max | 67.2% | 73,400 | 448 |
| GPT-5.6 Sol | high | 69.4% | 28,450 | 451 |
| GPT-6 Astra | medium | 72.8% | 20,362 | 452 |
| GPT-6 Astra | high | 73.2% | 26,506 | 452 |
| GPT-6 Astra | xhigh | 74.1% | 29,557 | 452 |
| GPT-6 Astra | max | 73.2% | 61,149 | 452 |

The benchmark uses mini-swe-agent and 113 tasks with repeated runs. Attempt coverage
differs. Reported confidence intervals overlap between the Astra configurations; small
score differences do not establish a reliable ordering. Output tokens are not equivalent
to cost across models. The Astra cost metadata uses expected launch pricing, so do not
treat its dollar values as current Codex credit charges. Keep this v1.1 snapshot separate
from the **Extended DeepSWE** evaluation listed in the Astra launch article.

Operating interpretation: Luna max supports bounded execution at a low price tier;
Astra medium is a useful starting point, while high or exceptional xhigh/max should be
justified by task difficulty. These are routing hypotheses, not guarantees of success.
Do not infer a fixed percentage of agents or work for each model from benchmark scores.

## GPT-6 guidance relevant to orchestration

The [official Astra guide](https://developers.openai.com/api/docs/guides/latest-model?model=gpt-6-astra)
recommends explicit delegation guidance, follow-through on authorized work, auditing
ambiguous skill instructions, and verification proportional to the change. It also
describes steering during work and asynchronous tool execution. Use the facilities exposed
by the current environment rather than assuming every API feature exists in Codex tools.

[Changing reasoning effort](https://developers.openai.com/api/docs/guides/reasoning#change-reasoning-mid-conversation)
with configuration_update is documented for Astra in standard, single-agent mode.
[Async tool calling](https://developers.openai.com/api/docs/guides/async-tool-calling)
requires application support and has compatibility limits. Neither feature is enabled by
editing a skill.

The [Codex configuration reference](https://learn.chatgpt.com/docs/config-file/config-reference)
documents agents.max_concurrent_threads_per_session as a limit on open spawned threads,
excluding the primary; agents.max_threads is a legacy alias. Other environments may count
capacity differently. Use live runtime semantics, and do not hard-code a session's number
into this skill.

That reference also describes features.context_management.experimental_mode, using notes
and searchable history. It is experimental and account-dependent. Recover context through
available tools, but obtain the user's authorization before changing their configuration.

## Maintenance

Refresh evidence when a routing decision actually depends on new results, prices, or
capabilities. Record source, date, benchmark version, model, effort, harness, and missing
coverage. Compare representative project outcomes, elapsed time, rework, and total cost;
do not reload benchmarks for routine work or require new benchmark runs for a small task.
