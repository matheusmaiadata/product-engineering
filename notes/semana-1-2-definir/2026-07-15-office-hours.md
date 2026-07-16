# 2026-07-15 — Office Hours (Semana 2) — Aula 4

Convidado: Matheus Montenegro. Aula prática (hands-on) — ele demonstra ao vivo como usa o Conductor no dia a dia, aprimorando o site [product.engineer](https://product.engineer) como caso real.

## TL;DR da aula

- **Ferramentas do fluxo**: **Wispr Flow** (fala → prompt, camada de entrada) + **Conductor** (rodar N agentes de código em paralelo, cada um em um git worktree isolado). Complementares — dois pedaços do mesmo harness.
- **Fluxo de trabalho do Matt**: Domínios → **Spec** (nela: Pricing → Monetização/margem → Arquitetura) → Skill. Negócio antes de arquitetura.
- **`/drill-me`** na etapa de spec: skill que entrevista e fura buracos no plano *antes* de codar.
- **Briefing estruturado** ao agente: alvo + referências de tom + stack travada + referências visuais.
- **Analog Design Standards** ([repo](https://github.com/eusouomatt/analog-design-standards)): design system em 3 camadas (Foundation → AURORA/FROST) que os agentes leem — "gosto é versionável, codifique".
- **Esqueleto de prompt**: **Goal · Do's · Don'ts · Out of scope · Evals** — intenção vira instrução verificável, evals viram gate a cada deploy.

## Panorama: Wispr Flow × Conductor

Os dois já haviam aparecido na Aula 3 (07/13) dentro do mesmo tema — a interface de dev convergindo para sessões de trabalho com agentes. São ferramentas complementares, não concorrentes: **Wispr Flow** resolve a *entrada* (fala → texto/prompt), **Conductor** resolve a *orquestração* (rodar vários agentes de código em paralelo, isolados). Ambas são "harness" ao redor do modelo, no sentido discutido no CAP 04 da Aula 3 ("agente = modelo + harness").

### Wispr Flow — funcionalidades

**Ditado**
- Funciona em qualquer app com campo de texto (Notion, Gmail, Docs, WhatsApp, Cursor, VS Code, Windsurf) — dito como 4x mais rápido que digitar
- 100+ idiomas suportados
- Modo sussurro (funciona em ambientes silenciosos/compartilhados, sem precisar falar alto)
- Reconhecimento de nomes incomuns por contexto

**Edição por IA**
- Remove vícios de fala ("um", "uh", "tipo") automaticamente
- Corrige backtracking (correções feitas no meio da frase são absorvidas)
- Pontuação inteligente por pausas e entonação
- Converte números falados em listas formatadas
- **Command Mode** (só Pro, Mac/Windows): edita texto selecionado por voz — "deixa isso mais conciso", "traduz para polonês", "transforma esse outline em parágrafo"

**Personalização**
- Dicionário pessoal (aprende grafias e correções ao longo do tempo)
- Snippets de voz (atalhos para frases/templates recorrentes)
- Estilo de tom por app (casual → formal), 2026: configurável por categoria de app — só inglês/desktop

**Times**
- Dicionários e snippets compartilhados (padroniza jargão da empresa)
- Dashboards de uso/adoção

**Foco em dev**
- Preserva sintaxe de código, camelCase, comandos de CLI
- Auto-reconhece nomes de arquivo no Cursor/Windsurf (file tagging)
- Integrações nativas: Cursor, Windsurf, VS Code

**Privacidade**
- SOC 2 Type II, ISO 27001
- Modo privacidade (grátis em todos os planos): zero áudio/transcrição armazenados, dados não usados para treino
- HIPAA BAA disponível no app

**Plataformas / preço**
- Mac, Windows, iPhone, Android
- Trial grátis de 14 dias, sem cartão; tier pago "Flow Pro"

### Conductor — funcionalidades

**Workspaces isolados**
- Cada tarefa ganha seu próprio git worktree + branch: arquivos, terminal, diff e caminho de revisão isolados
- Resolve o problema de rodar duas sessões de Claude Code na mesma pasta (que colidiriam e corromperiam a branch)

**Agentes em paralelo**
- Roda múltiplos agentes de código simultaneamente: Claude Code, Codex, Cursor, OpenCode
- Ex. citado: 5 worktrees, 5 instâncias de Claude Code, sem interferência entre elas

**Interface**
- Chat igual ao do Claude Code, com @file tagging e slash commands
- Painel lateral: diff de git ao vivo + terminal integrado

**Revisão & entrega**
- Ajuda a revisar o diff, abrir PR, mergear e arquivar o workspace
- Integração com GitHub (agente abre PR, lê diffs, comenta, responde a review comments) e Linear

**Plataforma / preço**
- App nativo de Mac
- Grátis — mas depende de uma assinatura ativa de Claude Code (ou do agente usado) para o compute

### Paralelo direto

| Dimensão | Wispr Flow | Conductor |
|---|---|---|
| O que resolve | Entrada: falar em vez de digitar prompts/texto | Orquestração: rodar N agentes de código em paralelo sem colisão |
| Onde entra no fluxo | Antes/durante — como você conversa com o agente | Durante/depois — como o trabalho de vários agentes é isolado e revisado |
| Unidade de trabalho | Frase/comando falado | Workspace = git worktree + branch + agente |
| Integrações-chave | Cursor, Windsurf, VS Code | GitHub, Linear; suporta Claude Code, Codex, Cursor, OpenCode |
| Plataforma | Mac, Windows, iPhone, Android | Só Mac |
| Modelo de preço | Freemium (trial 14 dias + Flow Pro) | App grátis, compute cobrado pela assinatura do agente |

**Síntese**: na lógica do "squares" da Aula 3 (Owner / Builder+Lever / Tinker), Wispr Flow acelera o *Owner/Builder* ditando intenção sem fricção de teclado, e o Conductor dá ao *Builder+Lever* um jeito de escalar — várias tarefas de agente rodando ao mesmo tempo, cada uma isolada, com revisão centralizada antes do merge. Dois pedaços do mesmo harness: um cuida da entrada, o outro da execução paralela.

---

## Demonstração: fluxo de trabalho do Matheus Montenegro com Conductor

Fluxo geral que ele segue para aprimorar o site [product.engineer](https://product.engineer):

1. **Domínios** — mapeia as áreas/domínios do problema antes de qualquer coisa.
2. **Spec** — escreve a especificação de cada mudança antes de codar. Dentro dessa etapa ele detalhou a ordem que segue:
   - **Pricing** — quanto vou cobrar do cliente.
   - **Monetização** — quanto eu vou ganhar; precisa ter uma margem acima de X (definir o piso de margem antes de seguir). Conecta com a discussão de precificação da Aula 3: cobrar por outcome/valor e garantir uma cobrança mínima para não dar prejuízo.
   - **Arquitetura** — só depois de pricing/monetização fechados, define a arquitetura técnica.
3. **Skill** — só depois aciona o agente para executar via skill.

Para a etapa de spec, ele geralmente puxa o `/drill-me` — uma skill pública de Claude Code que age como "entrevistador técnico": faz perguntas uma de cada vez sobre o plano/spec, força decisões que ainda não foram tomadas, expõe premissas escondidas e trade-offs evitados, sempre sugerindo uma resposta recomendada para não travar o fluxo. O objetivo é furar buracos na spec *antes* de escrever código, não depois.

### O briefing que ele passou ao agente

Ele estruturou o prompt inicial como um **briefing** com seções claras — bom exemplo de como "trazer o contexto" para o harness:

- **Site a ser roasted/re-imaginado**: https://www.product.engineer/ (o alvo do trabalho)
- **Web References**: https://www.piratewires.com/ (referência de tom/editorial)
- **Stack** (bibliotecas que o agente deve usar):
  - [shadcn/ui](https://ui.shadcn.com/) — componentes base
  - [Base UI](https://base-ui.com/) — componentes base (complementar)
  - [TanStack](https://tanstack.com/) — tabelas etc., caso shadcn ou Base UI não tenham
  - Charts: [dither-kit (Tripwire)](https://www.tripwire.sh/dither-kit)
  - Motion: Framer Motion Lib
  - Toasts: [Sonner](https://sonner.emilkowal.ski/)
- **Visual references**: ~10 imagens (image.png) anexadas como referência visual do design pretendido

Padrão do briefing: define **o alvo**, **referências de tom**, **stack técnica travada** e **referências visuais** — tudo antes de o agente começar. (Nota: no print aparece "INTERRUPTED BY USER" ao fim — ele interrompeu para ajustar antes de deixar rodar.)

### Analog Design Standards (repo do Matt)

Repositório: [github.com/eusouomatt/analog-design-standards](https://github.com/eusouomatt/analog-design-standards) — design system portátil criado pela **Analog HQ** ([analoghq.ai](https://analoghq.ai)), licença Apache 2.0. É a materialização da tese "**gosto é versionável, codifique**" (direção 5 da Aula 3): um padrão de design que os agentes leem para produzir UI polida em vez de "slop por padrão".

**Arquitetura em 3 camadas:**
- **Analog Foundation** — base compartilhada: tokens semânticos, tipografia, ícones, radius, densidade, motion, cobertura de estados, acessibilidade e quality gates. Stack de referência: Tailwind + shadcn/Radix.
- **AURORA** — superfícies operacionais (CRM, dashboards, pipelines, tabelas, settings, billing, admin). Densa, precisa, "calma".
- **FROST** — superfícies conversacionais (Home, AI chat, comandos, artifacts, streaming). Imersiva, focada, orientada à ação.
- AURORA e FROST são *irmãs* da mesma foundation, não design systems separados.

**Estrutura do repo (o que vale olhar):**
- `docs/` — fonte de verdade. Destaques:
  - `principles.md` — "**Design the actual product surface first**" (produto antes de brochura); regras de coerência, densidade, e uma lista forte de anti-patterns.
  - `foundation.md` — token model, tipografia, ícones, radius/densidade, surfaces/elevation, motion.
  - `aurora.md` / `frost.md` — padrões por tipo de superfície.
  - `review-checklists.md` — **gates pass/fail** antes de dar merge (Product Fit, Visual System, State Coverage, Accessibility, Responsiveness, AI UX, Motion). Ótimo como checklist de revisão.
  - `ui-patterns.md`, `ai-app-patterns.md`, `accessibility.md`, `motion-and-feedback.md`, `examples.md`, `implementation-recipes.md`, `analog-case-study.md`.
- `skills/analog-design-standards/` — a **skill** de agente (`SKILL.md` + `references/` condensados). Carrega só o reference necessário por tarefa (foundation sempre; aurora/frost conforme a superfície).
- `adapters/` — plug-and-play por ferramenta: `claude-code.md`, `codex.md`, `cursor-rules.md`, `lovable-*`, `bolt-*`, `universal-prompt.md`, `agents.md`.
- `prompts/` — templates por tarefa: `design-a-screen.md`, `improve-existing-ui.md`, `audit-ui.md`, `build-aurora-dashboard.md`, `build-frost-chat.md`.

**Como instalar no Claude Code** (do README):
```bash
mkdir -p .claude/skills
cp -R analog-design-standards/skills/analog-design-standards .claude/skills/
```
Depois: `/analog-design-standards Refactor this Home screen using FROST.`

**Ideias-chave para levar:**
- *Product before chrome*: a primeira tela mostra o workflow real, não um hero de marketing.
- *State is part of design*: um componente está incompleto até cobrir loading/empty/error/success/disabled/permission/optimistic/long-text/mobile/reduced-motion — estados faltando = defeito funcional.
- *Coherence rules*: defina cedo tipografia, ícones, cor semântica, densidade, shape e motion — não deixe cada componente re-decidir.
- *Adaptation guide*: mantém as regras de interação/acessibilidade/gates; troca só paleta, tipografia e ícones para outra marca. "A estética muda; a barra de qualidade não."

### Estrutura de prompt do Matt (garantir aderência)

Ele mostrou um exemplo "exdrúxulo" (propositalmente exagerado) de como estrutura os prompts para o agente seguir **exatamente** o que foi pedido. O esqueleto:

- **Goal** — o objetivo em uma frase + o objetivo principal por trás.
  - Ex.: *"High conversion landing page (VSL style)"* / *"My main goal is to present all features, services from my company."*
- **Do's** — o que fazer (lista `++`).
- **Don'ts** — o que nunca fazer.
  - Ex.: nunca citar concorrente, nunca falar mal de terceiros, etc.
- **Evals** — checagens obrigatórias em cada deploy (a disciplina de evals da Aula 3 aplicada no nível do prompt):
  - checar o mobile em todo deploy e garantir que está como desenhado;
  - conferir o breakdown do Hero (se não está com scroll travado no meio);
  - garantir que forms e a rota do checkout não estão quebrando.
  - *"Everytime you find a regression, let me know or create a log."* (fecha o loop de observabilidade — regressão vira aviso ou log).
- **Out of scope** — *(faltou nesse exemplo)*. Bloco que delimita explicitamente o que **não** faz parte da tarefa, evitando que o agente expanda escopo. Vale sempre incluir.

Padrão a reter: **Goal · Do's · Don'ts · Out of scope · Evals** — transforma intenção em instruções verificáveis, com as evals servindo de gate a cada deploy.

---

## Fecho — o método por trás da demo

A aula amarrou, na prática, várias teses da Aula 3:

- **O harness é o produto**: Wispr Flow (entrada), Conductor (execução paralela isolada), skills e design standards versionados são todos harness — a parte que o Matt engenheira ao redor do modelo alugado.
- **Negócio antes de código**: o fluxo dele coloca pricing e margem *dentro* da spec, antes da arquitetura. Definir quanto cobrar e qual o piso de margem molda as decisões técnicas.
- **Trazer contexto de forma estruturada**: o briefing (alvo + tom + stack + visual) e o esqueleto de prompt (Goal/Do's/Don'ts/Out of scope/Evals) reduzem ambiguidade e mantêm o agente no trilho.
- **Gosto é versionável**: o Analog Design Standards dá aos agentes um padrão legível para produzir UI polida em vez de slop — com review-checklists como gate de qualidade.
- **Meça antes de otimizar**: as evals no prompt e o "regressão vira aviso ou log" fecham o loop de observabilidade no nível da tarefa.

Síntese: menos mágica, mais método — contexto organizado, instruções verificáveis, agentes em tarefas específicas e isoladas, revisão antes do merge.

Fontes consultadas: [Wispr Flow — Features](https://wisprflow.ai/features), [Wispr Flow](https://wisprflow.ai/), [Conductor Docs](https://www.conductor.build/docs/), [Conductor](https://www.conductor.build/), [Run multiple Claude Code sessions in parallel — Conductor Docs](https://www.conductor.build/docs/guides/parallel-agents/run-multiple-claude-code-sessions), [drill-me — Claude Code Skill for Plan Stress-Testing](https://mcpmarket.com/zh/tools/skills/drill-me)
