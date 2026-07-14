# 2026-07-13 — Masterclass (Semana 2)

Convidado: Matheus Montenegro, apresentando o relatório "Guia de Campo AIE 2026" (Analog). Boa parte das anotações abaixo são prints do material apresentado; os comentários da "Visão do Matt" são falas/opiniões próprias do apresentador dentro do material.

## Tópicos
- Custo de IA e precificação de SaaS
- Fluxo de trabalho com agentes de código
- Disciplina de engenharia (harness, evals, segurança)
- Impacto no mercado de trabalho
- Conclusões e direções práticas

## Anotações

### Custo de IA pessoal vs. enterprise
Matheus Montenegro relatou gastar cerca de US$2.500/mês de uso pessoal de IA — traduzido para o contexto enterprise, esse número sobe para aproximadamente US$12.500.

### Harness importa mais que o modelo (custo na prática)
Rodar o GPT 5.6 Sol no Claude Code está sendo mais barato do que no Cursor — só por conta do harness (mesmo modelo, harness diferente, custo diferente). Reforça a tese já discutida na Aula 1: harness > modelo.

## CAP 02 · Os Modelos

### Duas pistas: volume commodity, dólares premium
- **Pista commodity** — o modelo capaz mais barato leva o trabalho em massa (classificação, extração, backends de chat, retrieval: trabalhos medidos em bilhões de tokens/mês). Os modelos open-weight estão disparando nessa pista. ~46% do volume de tokens, puxado por labs abertos chineses.
- **Pista premium** — o melhor raciocínio mantém poder de preço (raciocínio difícil, código agêntico, garantias enterprise). A Anthropic sangra volume e ainda assim leva os dólares: código é onde Claude tem a maior fatia do gasto. ~11% dos tokens, mas ~42% da receita.
- Visão do Matt: "Escolha pistas, não lados. O mercado é um mosaico de modelos combinados por tarefa, não um vencedor único." (Retratos OpenRouter, meados de 2026)

### A inversão de custo: retenção ≠ lucro
Gráfico "custo de servir por cliente" × "intensidade de uso/carga": o custo de servir em SaaS tradicional é praticamente plano; em IA, cresce de forma exponencial conforme a carga de uso aumenta — os clientes mais fiéis, talvez os mais caros de servir.

Citação: "Os clientes mais fiéis podem ser exatamente os mais caros de servir." (Rodrigo Fernandes, Digital Metrics Community)

Nota complementar: os clientes mais fiéis são exatamente os que gastam mais tokens.

### A conta está chegando (Ramp AI Index)
Gasto mensal de IA por funcionário (jan'24 → jan'26): top 1% em US$7.449, top 10% em US$611, mediana em apenas US$11. O gasto do top 1% cresceu mais de 10x em dois anos — a distância para a mediana é de três ordens de grandeza.

Até os gigantes sentem: a Meta estaria limitando o uso de tokens por funcionário, com custos internos de IA subindo às dezenas de bilhões (jun/2026). Eficiência de token deixou de ser otimização e virou linha de orçamento — por isso a pista open source segue ganhando volume.

### Pricing: entre seats, tokens e outcomes
- **Seats** — fácil de comprar e faturar, mas cego ao valor que a IA entrega, e trava a receita onde o uso a faria crescer. Status: erodindo.
- **Tokens** — tecnicamente preciso, acompanha a nova física de custos, mas difícil de entender, prever e justificar internamente. Status: fica para APIs & infra.
- **Outcomes** — se a ferramenta entrega valor concreto, a monetização acompanha esse valor, não tokens consumidos nem usuários cadastrados. Status: em alta.

Visão do Matt: "A conta de cobrar por entrega e/ou consumo não para de pé para enterprise. As assinaturas existem justamente para entregar o software na escala necessária. Engenharia de pricing é muito mais complexa do que andam dizendo por aí." (@eusouomatt, 10 jul)

Nota do Matheus: cobre pelo valor entregado, não por token ou por usuário.

### Roteie por complexidade, contabilize por outcome ("teste na segunda")
1. **Roteie por complexidade** — modelos abertos na triagem; fronteira só quando a tarefa merece. O Notion roda agnóstico de modelo exatamente por essa alavancagem.
2. **Cacheie o que repete** — prompt caching reescreveu o playbook: descontos de ~50x no cache, histórico completo venceu sumarização em recall, custo e velocidade. (Está resolvendo bugs ou desenvolvendo? Cacheie o que se repete.)
3. **Benchmark nas suas tarefas** — rode uma semana de carga real em dois modelos abertos + um de fronteira. Benchmark público não conta; seus traces contam.
4. **Contabilize por coorte** — acompanhe o custo de servir ao lado da receita, por coorte. Cliente que renova não é automaticamente lucrativo.

### Precificação tridimensional de SaaS (discussão em sala)
A maneira correta de fazer cobrança em SaaS é tridimensional: por usuário, por feature e por uso — todas essas dimensões devem estar interligadas. Todo SaaS precisa ter uma cobrança mínima, para não dar prejuízo. Vale pesquisar "multi access price", um modelo padrão de precificação.

## CAP 03 · O Fluxo

### A interface de dev converge para sessões de trabalho com agentes
- **Modelo antigo**: um dev escrevendo código, com autocomplete.
- **Modelo novo**: sessões de trabalho com agentes — workspaces persistentes, tarefas paralelas, delegação real.
- Todos na mesma direção: Cursor, Warp, Conductor, Superconductor, Zed, Claude Code, Codex, Kiro.
- Estão indo além da engenharia: preview no browser, interação com interface e colaboração visual aparecem tanto no Cursor quanto no Conductor. IDE, browser, ferramenta de design e ambiente de colaboração estão virando uma superfície só — tudo está ficando em uma única IDE.

Recomendação em sala (comentário de Fernando Sérgio): pesquisar "Stripe Projects" para subir stack de projeto — "tá insano!".

Dica do Matheus: usar Wispr Flow ou OpenWisper para falar os prompts em vez de digitar.

### Como um CTO entrega com agentes de IA (Hursh Agrawal, The Browser Company — Arc, Dia)
- **18:00 — Instrua os agentes**: instruções escritas no fim do dia (tarefa, contexto, restrições).
- **Madrugada — Agentes trabalham**: cada agente com uma tarefa específica, rodando enquanto ele dorme.
- **09:00 — Revise os resultados**: a manhã é triagem — aceitar, redirecionar ou descartar o que saiu da madrugada.
- **Resto do dia — Decisões & alavancagem**: pessoas, interações e as decisões que só um humano toma.

Síntese: menos mágica, mais método — contexto organizado, instruções claras, revisão constante, agentes em tarefas específicas ("Prototyping as Leadership", Dia 2). Complementa o experimento já relatado na Aula 1 (o líder da Browser Company rodando agentes à noite).

Comentário: hoje o normal é um dev com 6 sessões simultâneas rodando.

### Skills como artefatos: aprender sem retreinar
1. **Destile** — um workflow que se provou confiável vira um `SKILL.md` versionado, guardado com embeddings.
2. **Recupere** — um manifesto enxuto a cada turno; o corpo completo só carrega quando invocado.
3. **Promova & descontinue** — toda skill passa por eval; descontinue quando o modelo passar sem ela.

Já mensurável: ~15% de ganho medido pelo SkillsBench em 50.000+ skills indexadas do GitHub; ~90% de melhora num eval de skills do Gemini com 117 casos.

Fontes citadas: "How to Eval Skills" (Google DeepMind), "Total Recall" (Oracle), Simon Willison — skills podem ser maiores que o MCP.

## CAP 04 · A Disciplina

### agente = modelo + harness
- **O modelo — alugado**: pesos congelados, saída não determinística, trocado embaixo de você a cada poucos meses. Você não controla.
- **O harness — seu**: memória, ferramentas, skills, hooks, orçamento de contexto, verificação. A parte que você engenheira. É de onde a confiabilidade vem.

Citação: "Um agente é um modelo mais um harness." (Ignacio Martinez, Oracle) — o runtime em volta do modelo virou o jogo inteiro.

Analogia do Matheus: modelo é imóvel alugado, harness é imóvel próprio. Se preocupe em melhorar o seu harness — ele está acessível para o seu time de desenvolvimento? Traz bem o contexto? Tem processo bem definido?

### Evals viraram infraestrutura, não hype
- Traces são os logs da IA. Evals são os testes da IA — o modelo mental que substitui "roda três consultas, acena, deploya".
- Medição vem antes de otimização — os workshops partiam disso como premissa, não proposta.
- Tracing virou requisito de primeiro dia — gates de entrega no CI, não um time de dashboards depois.
- Nada de frameworks elaborados: assertions nas saídas, juízes automáticos no pipeline, ciclos de feedback que tornam o comportamento observável.

Citação: "Talvez seja uma das lacunas mais acessíveis de fechar, justamente porque depende mais de disciplina de engenharia do que de novas tecnologias." (César Morais, Engenheiro de Software, Hotmart — nota convidada)

### A trifecta letal (Simon Willison)
Três círculos que, juntos, geram exfiltração: **dados privados** + **conteúdo não confiável** + **canal de saída**. Fechar a trifecta é tratar a saída com o mesmo rigor da entrada.

Caso real citado: 9 segundos para apagar o banco inteiro de uma empresa, via um agente convencido por instruções escondidas num input de aparência comum — "a história mais repetida do evento".

### Instrumente, leia, julgue, gate ("teste na segunda")
1. **Instrumente** — duas linhas de OpenTelemetry no seu agente principal. Não dá para avaliar o que não se observa.
2. **Leia 12 traces** — categorize as falhas na mão antes de escrever qualquer eval. Quinze minutos de saídas reais valem mais que uma hora montando testes.
3. **Um juiz por dimensão** — rótulos binários, fidelidade acima de correção; um modelo julgando diferente do que gera. Realimente o prompt com as explicações do juiz.
4. **Gate no CI & auditoria da trifecta** — promova falhas a um conjunto de regressão que serve de gate para deploys. Depois mapeie dados privados, entradas não confiáveis e canais de saída de um agente, e filtre a saída.

### De pilotos a frotas: a governança virou um agente
Dados da RunLayer: 482 agentes em produção, 40 humanos no time que os opera, US$65k economizados por ano por um meta-agente que audita a frota toda semana, ajustando modelos e podando ferramentas sem uso. ("Agent Optimizer", Dia 3 — a conversa enterprise saiu de pilotos para frotas.)

## CAP 06 · As Pessoas

### O lado barulhento: demissões com o nome da IA
Cortes por motivo declarado (2026 YTD): IA 22% (era ~5% em 2025 — um ano depois, lidera a tabela), mercado & economia 18%, fechamentos 17%, reestruturação 13%, perda de contrato 9%, corte de custos 8%.

~150k vagas de tech cortadas no 1º semestre de 2026 (maio foi o pior mês em anos, com IA como motivo mais citado). ~US$700B de capex de IA em 2026 na Alphabet, Microsoft, Meta & Amazon — corta gente, sobe o orçamento das máquinas. (Fontes: Layoffs.fyi, Challenger Gray & Christmas.)

### O que as manchetes pulam: criação
Contraponto ao slide anterior: vagas no Indeed para engenheiros de software caíram até meados de 2025, depois subiram forte, acima das vagas gerais (Citadel Securities/Indeed).

- +15% de projeção do BLS para devs 2024–34, com IA citada como motor de demanda.
- ~43% de prêmio salarial para quem domina múltiplas habilidades de IA.
- 3x na contratação júnior da IBM nos EUA para funções de IA, mesmo cortando em outras áreas.
- Quando a API do agente custa mais que o salário: "Bem-vindo de volta, Leo."

Citação: "So far at least, I'm pretty sure AI has been net job-creating. This was not what I expected. It is possible this direction keeps going!" (Sam Altman, @sama, 11 jul 2026, 2,4M views) — cargos de engenharia na tecnologia estão aumentando.

### Times pequenos, alta capacidade de execução
2-3 pessoas prototipando, testando e entregando features; ciclos de 4-7 dias que antes levavam semanas ou meses. Mesmo dentro de empresas grandes, a adoção mais forte veio de grupos pequenos com gente forte, autonomia clara e problemas bem definidos.

Visão do Matt: "O tamanho da empresa importou menos que a qualidade do time, a clareza do problema e a liberdade para executar."

Ressalva honesta: entregar mais não é o mesmo que criar mais valor — mas o salto de capacidade é real.

### Forward Deployed Engineer: a contratação do ano
- **O que é**: engenheiros na linha de frente, com clientes todo dia, entregando a solução de maior impacto dentro do ambiente do cliente.
- **Origem**: título criado na Palantir. Agora OpenAI, Anthropic e Google montam times de FDE no mesmo estilo.
- **No palco**: um dia inteiro de talks — Cursor, Sierra, Ramp, Decagon, Kepler, cada uma dissecando como opera.
- Checklist "você precisa de um? Os quatro, ou pule": produto técnico, cliente técnico, time técnico, resultado esperado técnico. (Felipe Barreiros, AWS)
- Prova de que funciona — caso Decagon × Chime: 70% de resolução em chat e voz, 60% menos custo de suporte, 2x satisfação.

### FDE ∩ product engineer: o mesmo instinto
- **FDE**: embarcado no problema de um cliente exigente, entregando no ambiente dele, responsável pelo resultado dele.
- **Product Engineer**: dono do arco da ideia ao impacto dentro da organização de produto — define, constrói, entrega e observa o que os usuários fazem.
- **Núcleo comum**: ficar perto de quem usa a coisa; entender o problema antes da solução; fechar o loop até o impacto.

Citação: "A IA barateou o construir. O que segue raro é saber o que construir, e por quê: o gargalo migrou da execução para o julgamento." (Felipe Barreiros, AWS)

### Acabou o time de 2 pizzas. Agora, 2 pizzas é demais.
Visão do Matt: antes, unidade de construção = squads; agora, unidade de construção = squares (3-4 pessoas, agentes por baixo, julgamento por cima):

1. **Owner** — responsável pela definição do produto. A cadeira do julgamento.
2. **Builder + Lever** — um builder principal mais um de apoio. Os agentes multiplicam a dupla.
3. **Tinker** — define políticas das disciplinas e faz os checks finais das entregas. Harness, evals e gates de gosto vivem aqui.

"O futuro é squares, não squads."

## A Conclusão

### A engenharia de IA entrou na fase madura
Visão do Matt:
- Agentes de código são uma nova camada de trabalho; IDEs viraram ambientes agênticos.
- A batalha foi para a infraestrutura onde vivem código, agentes e colaboração.
- Harnesses, evals, contexto e observabilidade são a superfície de engenharia.
- Retenção sozinha não prova defensabilidade quando o custo de servir entra na conta.
- Escala de time importa menos que perfil de time: FDEs, product engineers, julgamento — a escala do time não interessa mais, o importante é o equilíbrio do time.

Quem combina times fortes, processos sólidos, boa infraestrutura e cultura real de experimentação leva uma vantagem desproporcional.

### Recapitulando — Seis direções para levar para casa
Visão do Matt:

1. **O harness é o produto** — você aluga o modelo; a memória, as ferramentas, os hooks e o contexto são seus. É aí que mora a sua engenharia agora.
2. **Roteie por tarefa, contabilize por outcome** — modelos abertos para volume, fronteira para julgamento. Cliente que renova não é automaticamente lucrativo.
3. **O workflow vai para a nuvem** — sessões sobrevivem a laptops. Quem hospeda o ambiente (código, contexto, agentes) hospeda o workflow. Feche o MacBook.
4. **Meça antes de otimizar** — traces e evals são o salto de maturidade mais barato que existe: disciplina, não tecnologia nova. Use-os como gate de entrega.
5. **Gosto é versionável. Codifique** — com código commodity, estilo é o produto. Um padrão de design que seus agentes leem, ou slop por padrão.
6. **O gargalo é o julgamento** — construir ficou barato; saber o que construir, não. Fique perto do cliente e feche o loop. FDE e product engineer são o mesmo instinto.

---

Fonte principal desta aula: "Guia de Campo AIE 2026" (Analog), apresentado por Matheus Montenegro (palestrante convidado).
