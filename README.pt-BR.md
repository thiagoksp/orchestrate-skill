# Orchestrate

[English](README.md) | **Português (Brasil)**

Adaptação pessoal da skill Orchestrate, de Rafael Quintanilha, para coordenar subagentes
especializados do Codex sem transferir do agente
principal a responsabilidade por escopo, autorizações, integração e resposta final.

Este repositório público, `thiagoksp/orchestrate-skill`, é a fonte canônica da versão do
Thiago.

## Trabalho original e créditos

A skill **Orchestrate** original foi criada por
[Rafael Quintanilha](https://github.com/rafaelquintanilha) e publicada em
[rafaelquintanilha/skills](https://github.com/rafaelquintanilha/skills).

- [Skill original](https://github.com/rafaelquintanilha/skills/tree/master/skills/orchestrate)
- [SKILL.md original na revisão `8c4991b`](https://github.com/rafaelquintanilha/skills/blob/8c4991b3852de693b2af529723b960bf76700f5a/skills/orchestrate/SKILL.md)

O `SKILL.md` inicialmente importado aqui corresponde ao blob Git original
`ef41630867715f8e24890e0e5ed9a7b86ce65004`. Este repositório mantém uma cópia separada
e modificada; não reivindica a autoria da skill original nem o endosso de seu autor.
As adaptações estão descritas abaixo; o crédito pelo trabalho original permanece com
Rafael Quintanilha.

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

Este repositório é a adaptação canônica do Thiago. Mudanças propostas são revisadas antes
do merge. Preserve a atribuição à origem em cópias e adaptações posteriores.

Não foi encontrada uma licença explícita no repositório original na verificação de
2026-09-02. Esta atribuição não adiciona uma licença nem concede direitos sobre o
trabalho original.
