# CLAUDE.md

🌐 **Português** | [English](CLAUDE.en.md)

Orientações para o Claude Code ao trabalhar neste repositório.

## Visão geral

**Open Agent Skills** é uma coleção open-source, acadêmica e colaborativa de **Skills para Agentes de IA** (Claude, Claude Code, ChatGPT, Google Antigravity e outros). O repositório é **só documentação/conteúdo**: não há código de aplicação, build, dependências nem suíte de testes. O "produto" são arquivos `SKILL.md` em Markdown.

- Repositório: `hanspeterdietiker/Open-Agents-Skills` (GitHub), branch principal `main`.
- Licença: MIT (`LICENSE`).
- Público: comunidade brasileira e internacional — conteúdo em **português** e **inglês**.

## Estrutura

```text
Open-Agents-Skills/
├── assets/                  # Imagens (ex.: assets/logo.png)
├── skills/                  # Todas as Skills da comunidade
│   └── <nome-da-skill>/
│       ├── SKILL.md         # Ponto de entrada (obrigatório)
│       ├── references/      # Documentos de apoio (opcional)
│       ├── scripts/         # Scripts auxiliares (opcional)
│       └── examples/        # Exemplos de uso (opcional)
├── README.md                # Versão em português (principal)
├── README.en.md             # Versão em inglês
├── CLAUDE.md                # Orientações para o Claude Code (português)
├── CLAUDE.en.md             # Orientações para o Claude Code (inglês)
└── LICENSE
```

A pasta `skills/` ainda pode não existir — crie-a ao adicionar a primeira Skill.

## Convenções de Skills

Toda Skill fica em `skills/<nome-da-skill>/SKILL.md`, com frontmatter YAML + corpo em Markdown:

```markdown
---
name: nome-da-skill
description: Use when ... / Use quando ... (diga QUANDO a Skill deve ser acionada)
---

# Nome da Skill

## Quando usar
## Passo a passo
## Exemplos
```

Regras:

- Nome da pasta em `kebab-case` (ex.: `code-review`, `gerador-de-relatorios`).
- O `name` do frontmatter deve ser **idêntico** ao nome da pasta.
- `name` e `description` são obrigatórios. A `description` é o gatilho: descreva *quando* usar, não *o que* a Skill faz em detalhe.
- Sempre que possível, inclua termos em **português e inglês** na `description` para melhorar o acionamento.
- Uma boa Skill é **focada** (um tipo de problema), **acionável** (diz exatamente o que fazer) e **verificável** (tem critérios de sucesso).
- Material longo vai em `references/`; o `SKILL.md` deve permanecer enxuto.
- **Autoria e créditos:** todo `SKILL.md` declara `license` e `metadata` (`author`, `source`/`based-on`) no frontmatter e termina com uma seção `## Créditos / Credits`. Skills copiadas de terceiros mantêm o `LICENSE` original na pasta e registram o que foi alterado. Sub-skills referenciadas são listadas com autor e onde obtê-las. Adicione a Skill ao glossário "Skills disponíveis" nos dois READMEs, em ordem alfabética (descrição curta + linha `<sub>` com autor e base).
- **Nada de regra de negócio:** antes de adicionar uma Skill vinda de um projeto, remova nomes de clientes/empresas, chaves de issue reais, URLs internas, caminhos locais, e-mails e regras específicas do domínio — use placeholders neutros (ex.: `PROJ-41`).

### Como testar uma Skill

Não há testes automatizados. Para validar, copie a Skill para o diretório de Skills do Claude Code e acione-a numa tarefa real:

```bash
cp -r skills/<nome-da-skill> ~/.claude/skills/      # pessoal
cp -r skills/<nome-da-skill> .claude/skills/        # do projeto
```

Confirme que ela dispara pela `description` e também via `/<nome-da-skill>`.

## Documentação bilíngue

- `README.md` (PT) ↔ `README.en.md` (EN) e `CLAUDE.md` (PT) ↔ `CLAUDE.en.md` (EN) devem ficar **sincronizados**: qualquer alteração em um deve ser espelhada no outro na mesma mudança.
- As âncoras dos links internos diferem entre os idiomas (ex.: `#-o-que-é-uma-skill` vs `#-what-is-a-skill`) — ajuste ao traduzir.
- Badges, logo (`assets/logo.png`, `width="420"`) e layout centralizado devem permanecer iguais nas duas versões do README.

## Fluxo Git: tipos, commits, branches e PRs

Commits, branches e Pull Requests seguem **o mesmo padrão**, baseado em [Conventional Commits](https://www.conventionalcommits.org/). Tudo é escrito **em inglês**, mesmo quando a conversa estiver em português.

### Tipos (verbos) permitidos

| Tipo | Quando usar |
| --- | --- |
| `feat` | Nova Skill ou nova capacidade em uma Skill existente |
| `fix` | Correção de erro (instrução errada, frontmatter inválido, link quebrado, gatilho que não dispara) |
| `docs` | Documentação: READMEs, `CLAUDE.md`, `LICENSE`, guias |
| `refactor` | Reorganização de uma Skill sem mudar o comportamento (dividir em `references/`, renomear seções) |
| `style` | Apenas formatação (espaços, tabelas, quebras de linha) |
| `chore` | Manutenção: assets, configs, arquivos auxiliares |
| `ci` | Workflows do GitHub Actions e automações |

Escopos comuns: `skills`, `readme`, `assets`, ou o nome da Skill (ex.: `code-review`).

### Commits

```
<tipo>(<escopo opcional>): <descrição curta>
```

- Descrição em minúsculas, no imperativo (`add`, `fix`, `update`, `remove`), sem ponto final, ≤ 72 caracteres.
- Um commit = uma mudança lógica. Se precisar de mais contexto, use o corpo do commit (linha em branco após o título).

```
feat(skills): add code-review skill
fix(conventional-commits): clarify scope rules in description
docs(readme): sync english readme with portuguese version
refactor(code-review): move checklist to references folder
chore(assets): compress project logo
```

Não faça commit nem push sem que o usuário peça.

### Branches

```
<tipo>/<descricao-em-kebab-case>
```

- Mesmos tipos da tabela acima; descrição curta, em inglês, em `kebab-case`.
- Sempre criada a partir da `main` atualizada. Nunca trabalhe direto na `main`.
- Se houver issue, o número pode ir no final: `feat/code-review-skill-12`.

```
feat/code-review-skill
fix/commit-skill-frontmatter
docs/sync-readme-translations
refactor/code-review-references
chore/compress-logo
```

### Pull Requests

**Título** — mesmo formato do commit:

```
<tipo>(<escopo opcional>): <descrição curta>
```

Ex.: `feat(skills): add code-review skill`

**Passos:**

1. `git push -u origin <branch>`
2. `gh pr create --base main --title "<título>" --body-file <arquivo>`
3. Pergunte ao usuário quem deve revisar e use `--reviewer <usuario>` ou mencione no corpo — **nunca invente um `@usuario`**.

**Corpo** — use sempre este template (em inglês):

```markdown
## Summary

<1–3 sentences: what this PR does and why.>

## Type of change

- [ ] feat — new skill or capability
- [ ] fix — bug fix
- [ ] docs — documentation
- [ ] refactor — restructure without behavior change
- [ ] style / chore / ci

## Changes

- <bullet list of the main changes, citing files/skills>

## How it was tested

- Agent: <Claude Code / Claude / ChatGPT / Antigravity / ...>
- Scenario: <prompt or task used to trigger the skill and the observed result>

## Related issue

Closes #<number>

## Checklist

- [ ] Skill lives at `skills/<skill-name>/SKILL.md`
- [ ] Frontmatter has `name` (matching the folder) and `description`
- [ ] Instructions are clear, actionable and include examples
- [ ] Tested with at least one agent
- [ ] PT/EN READMEs are in sync (if changed)
- [ ] Commits and branch follow Conventional Commits

## Reviewer

@<collaborator-username>
```

Remova as seções que não se aplicam (ex.: "Related issue" quando não há issue; itens específicos de Skill num PR só de `docs`).

## Ambiente

O mantenedor usa Windows (PowerShell / Git Bash). Prefira caminhos com `/` e comandos portáveis nos exemplos da documentação.
