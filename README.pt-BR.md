# Orchestrate

[English](README.md) | **Português (Brasil)**

Skill pessoal do Codex para coordenar subagentes especializados sem transferir do agente
principal a responsabilidade por escopo, autorizações, integração e resposta final.

Este repositório público, `thiagoksp/orchestrate-skill`, é a fonte canônica da versão do
Thiago.

## Quando usar

Use Orchestrate quando houver frentes realmente independentes, uma operação demorada que
não deve bloquear a conversa, uma investigação paralela delimitada ou uma revisão
independente que reduza materialmente o risco. Tarefas pequenas ou estritamente
sequenciais permanecem com o agente principal.

O roteamento padrão usa:

- Luna para subagentes executores delimitados, coleta de evidências e workflows já
  definidos. Na skill, **leaf agent** significa um agente que recebe uma tarefa limitada
  e não delega novamente; é um termo técnico, não uma tradução literal;
- Terra para uma frente colaborativa de implementação ou coordenação;
- Sol para julgamento sênior independente em decisões ambíguas ou de alto impacto.

Consulte [SKILL.md](SKILL.md) para as regras completas de roteamento, divulgação,
atribuição, comitês, limites de autoridade e síntese.

## O que esta versão acrescenta

- retornos estruturados com `Verdict`, `Findings`, `Risks`, `Recommendation` e
  `Evidence`;
- fallback seguro quando modelo, ferramenta, vaga ou cota de uso estiver indisponível;
- respeito ao Coder persistente ou a outro responsável de implementação explicitamente
  definido;
- transformação de comitês obrigatórios em perguntas decisórias delimitadas;
- nenhuma repetição de subagentes sem mudança concreta de disponibilidade.

A skill pode ser selecionada automaticamente pelas regras globais ou do repositório e
também pode ser invocada explicitamente como `$orchestrate`.

## Instalação

Pré-requisitos: Git, Codex e um modelo/runtime com ferramentas de colaboração do Codex.

```powershell
$orchestrateCodexRoot = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $env:USERPROFILE ".codex" }
$orchestrateSkillsRoot = Join-Path $orchestrateCodexRoot "skills"
New-Item -ItemType Directory -Force -Path $orchestrateSkillsRoot | Out-Null
git clone https://github.com/thiagoksp/orchestrate-skill.git (Join-Path $orchestrateSkillsRoot "orchestrate")
```

Para atualizar uma instalação existente:

```powershell
$orchestrateCodexRoot = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $env:USERPROFILE ".codex" }
$orchestrateSkillPath = Join-Path $orchestrateCodexRoot "skills\orchestrate"
git -C $orchestrateSkillPath pull --ff-only
```

Abra uma nova tarefa do Codex depois de instalar ou atualizar para recarregar a skill e
as regras globais.

## Governança

Este repositório é a versão canônica do Thiago. Mudanças propostas são revisadas antes do
merge. Outros usuários podem criar um fork do repositório público e adaptar sua própria
cópia.
