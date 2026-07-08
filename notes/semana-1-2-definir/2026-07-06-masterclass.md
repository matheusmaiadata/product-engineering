# 2026-07-06 — Masterclass (Semana 1, DEFINE)

## Tópicos
-

## Anotações

### Vocabulário: Harness — tudo que existe em volta do modelo
O agente que você usa não é o LLM. É o LLM **dentro de um sistema**. Esse sistema tem nome (harness) e tem anatomia:

1. **LLM** — o motor. Recebe tokens, devolve tokens. Só isso.
2. **Tooling** — as mãos: bash, editor de arquivos, browser, MCP. O que o agente consegue fazer no mundo.
3. **Prompt orchestration** — system prompt, exemplos, contexto: o que entra na janela e em que ordem.
4. **Control flow** — o loop: quando pensa, quando age, quando para, quando pede ajuda.
5. **Parsing & validation** — gates: a saída compila? Testes passam? Formato válido? Retry se não.
6. **Memory & state** — o que sobrevive entre sessões: arquivos de contexto, aprendizados, estado da tarefa.

Claude Code, Codex e Kiro usam **modelos parecidos**. A diferença que você sente é o harness.

## Prints / referências
<!-- salve as imagens em ./assets/ e linke aqui, ex: ![nome](assets/2026-07-06-slide1.png) -->

### Stripe Economics — "The age of the solopreneur" (jun/2026)
Fonte: [stripeeconomics.com/p/the-age-of-the-solopreneur](https://www.stripeeconomics.com/p/the-age-of-the-solopreneur)

**Tese central:** o mundo está sendo reconstruído em torno de quem entrega sozinho, ponta a ponta — há uma aceleração estrutural na formação de negócios solo (não-empregadores), turbinada por IA, e não é ruído estatístico nem fraude.

**Principais números:**
- Solopreneurs faturando mais de US$1M mais que dobraram entre 2023 e 2025; os que passaram de US$5–10M quase triplicaram.
- ~4 milhões de americanos têm como renda principal um negócio solo com faturamento acima de US$100K/ano — quase o dobro do início dos anos 2010.
- Coorte 2025 de novos usuários Stripe atinge US$1M de receita acumulada ~30% mais rápido que a coorte 2023, e 3x mais rápido que a coorte 2019.
- Jornadas de usuário influenciadas por IA já representam quase 4x a fatia de sign-ups na Stripe vs. janeiro do ano anterior.
- Tendência global: registros de novas empresas subiram ~40% na Austrália, ~70% na Finlândia, ~80% na França desde 2017.

**Por que não é fraude (segundo o estudo):** sem subsídio federal incentivando registros falsos (diferente do PPP); coortes mais novas transacionam mais rápido, não mais devagar; aceleração acontece em vários países com regimes regulatórios diferentes; crescimento concentrado em jurisdições associadas a intenção real de negócio (ex: incorporações em Delaware, registros em Wyoming).

**Papel da IA:** preenche gaps de capacidade que antes exigiam contratar gente — ajuda em pesquisa de mercado, produto, precificação, marketing e fechamento de vendas. Há correlação positiva entre adoção de IA por setor e crescimento de negócios não-empregadores.

**Conclusão do estudo:** "podemos estar nos primeiros estágios de uma aceleração fundamental na formação de negócios", liderada por solopreneurs que usam IA e plataformas melhores pra operar sozinhos em escala relevante.

**Por que isso importa pro curso:** é evidência direta de que o perfil "Product Engineer" (uma pessoa cobrindo produto + engenharia + go-to-market) é exatamente o que o mercado está recompensando agora — conecta com a tese do PDE de operar como TPM + engenheiro + GTM no mesmo ciclo.

### Monaco — "the first revenue engine for startups"
Fontes: [monaco.com](https://www.monaco.com/) · [monaco.com/product](https://www.monaco.com/product) · [anúncio Series B (GlobeNewswire)](https://www.globenewswire.com/news-release/2026/05/12/3293132/0/en/monaco-secures-50-million-in-series-b-funding-to-grow-ai-powered-sales-platform-amid-strong-customer-demand.html) · [review crítico (Salesforge)](https://www.salesforge.ai/blog/monaco-sales-platform-review)

**O que é:** plataforma de vendas/GTM AI-native que substitui CRM + ferramentas fragmentadas por um único "sistema de registro" de receita. Fluxo do produto (visto no print): Build TAM → Overlay signals → Execute sequences → Capture Activity → Track Pipeline → Ask Monaco.

**Pra quem:** founders/startups em estágio inicial (seed/Series A), principalmente sem background em vendas, que precisam montar operação de GTM rápido — "valor em dias, não meses".

**Time fundador:** Sam Blond (CEO, ex-CRO Brex e Zenefits), Malay Desai (ex-CTO Clari), Shek Viswanathan (ex-CPO Apollo/Qualtrics) — pedigree forte em vendas/RevOps.

**Funding:** Series B de US$50M liderada pela Benchmark (Jack Altman), com Founders Fund, Human Capital, Alt Cap, Mantis, Saga VC e anjos (Garry Tan, Neil Mehta, John e Patrick Collison). Total captado > US$85M. Saiu do stealth em fev/2026, hoje em beta público com centenas de clientes.

**Diferencial citado:** IA com "humano no loop" — um executivo de vendas supervisiona os agentes de IA, evitando e-mails alucinados e dano ao domínio de envio.

**Pontos fracos apontados por review externo (Salesforge, concorrente):**
- Pricing não é público; CEO não divulgou números pra imprensa
- Só automação por e-mail — sem LinkedIn, dialer, SMS ou sequências multicanal
- Nenhuma info pública sobre infra de deliverability (domínios aquecidos, IP dedicado, DMARC)
- Zero validação independente ainda (sem G2/Capterra, todos os depoimentos são do próprio site)
- Não é indicado pra empresas Series B+ ou times enterprise que precisam de alto volume

**Por que isso importa pro curso:** é um case direto de "Product Engineer" em ação — um time pequeno e técnico atacando GTM com produto + IA, GTM Engineer sendo literalmente a proposta de valor da empresa. Bom benchmark de posicionamento e de como comunicar um produto AI-native (linguagem simples, foco no resultado do cliente, pipeline visual como hero da landing page).

## Ferramentas de agentes de IA — pesquisa comparativa
Pesquisa focada em desenvolvimento de produto e automação de trabalho com agentes. Avaliação independente (docs oficiais + reviews de terceiros + comunidade), não só marketing das próprias empresas.

### Hermes Agent (Nous Research)
Fontes: [hermes-agent.nousresearch.com](https://hermes-agent.nousresearch.com/) · [GitHub](https://github.com/NousResearch/hermes-agent) · [HN: lançamento](https://news.ycombinator.com/item?id=47264225) · [HN: controvérsia](https://news.ycombinator.com/item?id=48187581)

- **O que é:** agente open source (MIT) da Nous Research — "um agente, uma memória, várias superfícies" (Telegram, Discord, Slack, WhatsApp, Signal, e-mail, CLI). Agnóstico de modelo (Nous Portal, OpenRouter, OpenAI, endpoint próprio). Tool-calling programático, subagentes isolados, memória persistente com busca entre sessões, e um "loop de aprendizado fechado" que gera skills reutilizáveis a cada ~15 chamadas de ferramenta.
- **Utilidades:** automação de tarefas recorrentes por linguagem natural (relatórios, digests, backups), delegar subtarefas de código a subagentes em sandbox, acionar o agente via Slack/Telegram pra operações de servidor, construir runbooks incrementais.
- **Pontos fortes:** tração real (~210k+ stars, atividade diária no GitHub), MIT/self-hosted, sem lock-in de modelo, presença em 14+ canais, backends serverless que hibernam ocioso (custo baixo).
- **Pontos fracos:** não é especializado em codificação (mais fraco que Claude Code/Cursor em arquitetura de repo e refactor profundo); controvérsia no HN sobre possível derivação não creditada do projeto "Evolver" e edição de issues no GitHub em vez de resposta pública; maioria dos "reviews" achados é conteúdo de SEO gerado por IA, sem benchmark real; ~26 mil issues abertas.
- **Usabilidade:** instalação via curl ou apps desktop; setup é mais "administração de sistema" (modelo, backend, integrações) que plug-and-play.
- **Preço:** agente é gratuito/self-hosted (BYO chave de API). Nous Portal: Free ($0 + créditos), Plus ($20/mês), Super ($100/mês), Ultra ($200/mês).

### OpenClaw (openclaw.ai)
Fontes: [openclaw.ai](https://openclaw.ai/) · [docs.openclaw.ai](https://docs.openclaw.ai/) · [The Hacker News — falhas de segurança](https://thehackernews.com/2026/03/openclaw-ai-agent-flaws-could-enable.html) · [Microsoft Security Blog](https://www.microsoft.com/en-us/security/blog/2026/02/19/running-openclaw-safely-identity-isolation-runtime-risk/)

- **O que é:** assistente pessoal de IA open-source e self-hosted, criado por Peter Steinberger (ex-"Clawdbot"), rebatizado OpenClaw em jan/2026. É um **gateway** rodado localmente/servidor próprio que conecta ~30 apps de mensagem (WhatsApp, Telegram, Slack, Discord, iMessage etc.) a LLMs (Claude, GPT, local via Ollama), com acesso a filesystem, shell e browser.
- **Utilidades:** automação administrativa via chat (e-mail, agenda), orquestração multi-agente entre máquinas, ponte entre canais de time e IA, sandboxing empresarial via Microsoft Execution Containers.
- **Pontos fortes:** crescimento viral real (milhares de stars nas primeiras 24h), multimodelo, 100% self-hosted/privado, patrocínio citado de nomes grandes (OpenAI, GitHub, NVIDIA, Vercel).
- **Pontos fracos:** **segurança é o problema central** — múltiplas fontes independentes (Hacker News, Microsoft, Giskard, CNCERT chinês) documentam vulnerabilidades reais de prompt injection que vazam dados locais; não é uma ferramenta de coding (sem consciência de repo/git); permissões amplas por padrão e chaves em texto plano; curva de aprendizado "brutal" com falhas silenciosas difíceis de debugar; múltiplos rebrands sinalizam instabilidade do projeto.
- **Usabilidade:** instalação em um comando, mas operação segura exige configuração cuidadosa — não é plug-and-play.
- **Preço:** gratuito/open source; custo real é o consumo de API do LLM conectado por trás.

### Conductor (conductor.build)
Fontes: [conductor.build](https://www.conductor.build/) · [docs](https://www.conductor.build/docs) · [Show HN](https://news.ycombinator.com/item?id=44594584)

- **O que é:** app nativo de Mac (Apple Silicon) da Melty Labs (time YC S24) que orquestra **múltiplos agentes de código em paralelo** — Claude Code, Codex, Cursor — cada um em um git worktree isolado (branch, arquivos, terminal e diff próprios), com dashboard visual, "checks" e integração GitHub/Linear pra abrir PRs.
- **Utilidades:** rodar 3–5 tarefas de código simultâneas sem gerenciar worktrees na mão; "multi-model mode" pra comparar como Claude Code/Codex/Cursor resolvem o mesmo problema; review centralizado de diffs de vários agentes.
- **Pontos fortes:** resolve de fato a dor operacional de worktrees manuais; gratuito (só paga API/assinatura por trás); criadores responsivos a críticas de segurança.
- **Pontos fracos:** pedia originalmente OAuth de leitura/escrita total no GitHub (corrigido depois — sinal de imaturidade); cada worktree novo não herda `node_modules`/`.env`, exigindo reconfiguração; custo de API multiplicado por agente rodando em paralelo; sem memória entre sessões ("context amnesia"); mais código gerado em paralelo = mais revisão humana necessária; alternativas open-source (Crystal, Claude Squad) citadas como mais simples/transparentes.
- **Usabilidade:** curva moderada — bootstrap inicial (tokens, dependências, `.env`) gera confusão até "clicar"; **exclusivo macOS com Apple Silicon**, sem Windows/Linux/Intel Mac.
- **Preço:** gratuito para baixar; paga-se só a API/assinatura dos agentes subjacentes. Não é open source.

### Warp (warp.dev)
Fontes: [warp.dev](https://www.warp.dev/) · [pricing](https://www.warp.dev/pricing) · [Warp AI/Agent Mode](https://www.warp.dev/ai)

- **O que é:** terminal reescrito do zero em Rust com renderização por GPU, que trata saída como **blocos** editáveis (não fluxo de texto contínuo) e se reposiciona como "Agentic Development Environment". Tem Agent Mode nativo, orquestração multi-agente (Claude Code, Codex, Gemini CLI, OpenCode lado a lado) e "Oz" pra agentes rodando na nuvem reagindo a webhooks/CI/Slack.
- **Utilidades:** gerar comando por linguagem natural, Agent Mode decompõe tarefas e propõe/executa comandos com aprovação, rodar múltiplos agentes em abas paralelas, Warp Drive pra compartilhar workflows em equipe, MCP nativo.
- **Pontos fortes:** combinação coerente (blocos + busca + IA + agentes); multiplataforma real (Mac/Linux/Windows, diferente do iTerm2 que é só Mac); tração comercial forte (>500 mil engenheiros, US$73M captados, ARR crescendo rápido); open source desde abril/2026.
- **Pontos fracos:** histórico de telemetria controversa — no tier grátis, desativar "App Analytics" **quebra o Agent**; créditos de IA podem ficar caros em uso intenso; menos customização fina que iTerm2/tmux; capacidades agênticas avançadas dependem da nuvem da Warp, não são puramente locais.
- **Usabilidade:** curva de aprendizado baixa vs iTerm2/tmux; multiplataforma; maduro (lançado 2022, evolução contínua).
- **Preço:** Free (BYO IA); Build $20/mês (1.500 créditos); Max $200/mês (18.000 créditos); Business $50/usuário/mês; Enterprise sob consulta.

### Zed (zed.dev)
Fontes: [zed.dev](https://zed.dev/) · [pricing](https://zed.dev/pricing) · [zed.dev/agentic](https://zed.dev/agentic) · [zed.dev/compare/cursor](https://zed.dev/compare/cursor)

- **O que é:** editor de código nativo em Rust, focado em performance máxima (multi-core + GPU) e edição colaborativa em tempo real, feito do zero pelos criadores do Atom e Tree-sitter (não é fork do VS Code, diferente do Cursor). Tem Agent Panel nativo, não IA como plugin.
- **Utilidades:** Agent Panel delega tarefas com descoberta de contexto e edição multi-arquivo; "Parallel Agents" (abr/2026) roda múltiplos agentes ao mesmo tempo em partes diferentes do código; Agent Client Protocol integra Claude Code, Codex, Gemini CLI nativamente; multi-model (Opus/Sonnet, GPT-5.x, Gemini, local via Ollama) + MCP; Edit Predictions (Zeta2, open-weight).
- **Pontos fortes:** performance mensurável (~0,4s startup, ~2ms latência de input); 100% open source (GPL-3.0); comunidade grande (~85k stars); controle granular de permissões por ferramenta com revisão diff-first; colaboração multiplayer nativa "sem igual".
- **Pontos fracos:** ecossistema de extensões muito menor (~800 vs ~50.000 do VS Code); edit predictions "sólidas mas não no nível do Tab" do Cursor; indexação de codebase inteira mais fraca que Cursor; não herda extensões do VS Code (fricção de migração); suporte Windows é recente (out/2025), menos testado em produção.
- **Usabilidade:** curva baixa pra quem já usa editores modernos; setup simples (binário nativo); documentação boa e crescente; v1.0 em abr/2026 com releases semanais.
- **Preço:** Personal grátis (núcleo + até 2.000 edit predictions com BYOK); Pro $10/mês (predictions ilimitadas + $5 em tokens/mês); Business $30/assento/mês. Suporta BYOK mesmo no plano grátis.

### Síntese: como usar as 5 ferramentas juntas (complementares, não concorrentes)
- **Zed** — editor primário, dia a dia, foco solo. Claude Code plugado no Agent Panel via ACP.
- **Conductor** — orquestrador de escala: várias instâncias do Claude Code em paralelo (um worktree por tarefa), pra quando já tem 3-5 specs prontas pra rodar de uma vez.
- **Warp** — terminal de base pra tudo que não é escrever código (git, deploy, scripts, debug); também dá pra abrir o Claude Code numa aba se não quiser sair do terminal.
- **Hermes Agent** — automação fora do editor na fase LANÇAR: monitoramento/alertas recorrentes acionáveis via Slack/Telegram, sem precisar estar no teclado.
- **OpenClaw** — automação pessoal via apps de mensagem; fora do escopo de engenharia do curso, e com histórico de segurança problemático (prompt injection) — não recomendado pra esse fluxo.

Cadeia de uso: escrever/revisar no Zed → escalar tarefas paralelas no Conductor → tudo mais (deploy, git) no Warp → pós-lançamento, Hermes Agent cuida do monitoramento.

### Billing: usar só a assinatura do Claude Code (sem pagar API/modelo à parte)
**Usam a assinatura Claude Code de verdade:**
- **Conductor** — orquestra a CLI do Claude Code diretamente em cada worktree; é o caso de uso principal da ferramenta, não gambiarra.
- **Zed** — via ACP, pluga o Claude Code como agente no Agent Panel usando a sessão/login do Claude Code. Ressalva: isso é diferente de usar os modelos nativos do plano Zed Pro (esses cobram tokens com markup de +10%) — precisa configurar explicitamente pra usar o Claude Code externo.
- **Warp** — abrir uma aba e rodar `claude` normalmente = 100% assinatura Claude Code, sem custo extra. Cuidado: o "Warp Agent"/"Agent Mode" nativo é produto separado com créditos pagos à parte (Build $20/mês = 1.500 créditos) — não confundir os dois.

**Não foram pensadas pra isso (cobram API por token ou usam modelo próprio):**
- **Hermes Agent** — agnóstico de modelo, mas via chave de API (Nous Portal/OpenRouter/OpenAI); sem integração com login/assinatura do Claude Code.
- **OpenClaw** — conecta via chave de API do Claude/GPT ou modelo local; mesma limitação.

## Dúvidas / pontos pra Office Hours de quarta
-

## Ações
-
