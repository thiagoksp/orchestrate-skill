# Orchestrate

Skill pessoal do Codex para coordenar subagentes especializados sem transferir do agente
principal a responsabilidade por escopo, autorizações, integração e resposta final.

O repositório privado `thiagoksp/orchestrate-skill` é a fonte canônica desta cópia.

## Quando usar

A skill é indicada quando há frentes realmente independentes, uma operação demorada que
não deve bloquear a conversa, uma investigação paralela ou uma revisão independente que
reduza risco. Tarefas pequenas ou estritamente sequenciais permanecem com o agente
principal.

O roteamento padrão usa:

- Luna para folhas delimitadas, coleta de evidência e execução de workflows definidos;
- Terra para uma frente colaborativa de implementação ou coordenação mais complexa;
- Sol para julgamento sênior independente em decisões ambíguas ou de alto impacto.

Consulte [SKILL.md](SKILL.md) para as regras completas de seleção, divulgação,
delegação, comitês, limites de autoridade e síntese.

## Uso

A skill pode ser descoberta automaticamente quando as regras globais ou do repositório
mandarem avaliar `orchestrate`. Também pode ser invocada explicitamente como
`$orchestrate`.

Ela respeita o Coder persistente definido pelo projeto, padroniza o retorno dos
especialistas, trata indisponibilidade de modelos sem tentativas repetitivas e transforma
comitês obrigatórios em perguntas delimitadas.

## Instalação privada

Pré-requisitos: Git, GitHub CLI (`gh`) e uma conta com acesso ao repositório privado.
Autentique a conta, resolva o diretório global do Codex e clone a skill:

```powershell
gh auth login
$orchestrateCodexRoot = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $env:USERPROFILE ".codex" }
$orchestrateSkillsRoot = Join-Path $orchestrateCodexRoot "skills"
New-Item -ItemType Directory -Force -Path $orchestrateSkillsRoot | Out-Null
gh repo clone thiagoksp/orchestrate-skill (Join-Path $orchestrateSkillsRoot "orchestrate")
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

Alterações no conteúdo da skill exigem autorização explícita de Thiago. Propostas de
melhoria devem ser apresentadas para revisão antes da edição. Projetos podem complementar
o comportamento em seus próprios `AGENTS.md`, sem duplicar as regras globais.
