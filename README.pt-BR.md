# Orchestrate

[English](README.md) | **Português (Brasil)**

Adaptação pessoal da skill Orchestrate, de Rafael Quintanilha, para coordenar subagentes
especializados do Codex mantendo no agente principal a responsabilidade por escopo,
autorizações, integração e resposta final.

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

Use Orchestrate quando frentes independentes puderem avançar em paralelo, uma operação
demorada precisar de acompanhamento ou uma revisão independente melhorar o resultado.
O agente principal adapta a equipe conforme a tarefa evolui e resolve diretamente o
trabalho simples e sequencial.

O roteamento padrão usa:

- **Luna Max** para execução delimitada, programação, evidências e revisão focada.
  Um **leaf agent** recebe uma tarefa delimitada e não delega novamente;
- **Sol High** para revisão sênior independente e diagnóstico delimitado;
- **Astra Medium** para novas atribuições de coordenação e trabalho entre componentes;
- **Astra High** para ambiguidades difíceis, arquitetura e decisões de maior consequência;
- **Astra XHigh/Max** quando a dificuldade ainda não resolvida ou uma escolha explícita
  justificar o esforço.

Escolhas explícitas do usuário e capacidades disponíveis de modelo/esforço prevalecem.
A skill não altera o modelo principal nem as configurações do aplicativo. Consulte
[SKILL.md](SKILL.md) para roteamento e supervisão, e a [referência de modelos](references/model-evidence.md)
para os dados datados do DeepSWE e a documentação oficial do GPT-6 usados na política.

## O que esta versão acrescenta

- Distribuição dinâmica: sem trio fixo nem teto total de tarefas; a capacidade real limita
  quantas unidades independentes executam ao mesmo tempo. As demais ficam na fila.
- Supervisão: diferenciar espera legítima de repetição sem evidência nova, intervir,
  preservar contexto e manter a contagem de tentativas ao trocar o responsável.
- Reuso de evidências: um responsável pelos testes caros compartilhados; verificações
  adicionais precisam de uma mudança ou dúvida ainda não resolvida.
- Coder persistente e coordenação direta pelo Senior, sem repasse manual de mensagens.
- Continuidade após novas orientações, com notas ou histórico pesquisável quando disponíveis.
- Retornos compactos: `Verdict`, `Findings`, `Risks`, `Recommendation` e `Evidence`.

Os cenários são exemplos adaptáveis, não equipes obrigatórias. O agente principal pode
atribuir coordenação a Astra ou Sol dentro do escopo autorizado. A skill não aumenta a
capacidade do ambiente nem ativa recursos experimentais; isso exige uma decisão separada
sobre configuração.

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
