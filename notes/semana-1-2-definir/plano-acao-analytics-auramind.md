# Reestruturação do Analytics Auramind — Plano de Definição

> **Owner:** Matheus · **Fase:** Define (Semana 1–2) · **Data:** 2026-07-13
> Documento de definição de produto baseado nas Aulas 1–2 (MasterClass Product Engineer), na quantificação da dor e nas conclusões da office hour com o professor.

---

## Contexto

O Analytics da plataforma B2B **Auramind** já existe e entrega valor (clientes geram relatórios com ele), mas está sendo reestruturado porque os dados não estão bem organizados — o que o torna pouco confiável e difícil de defender para a diretoria dos clientes. O caso concreto que motiva a reestruturação: um gestor precisou regerar várias vezes um relatório mensal porque o analytics **assumiu premissas que ele não pediu e não conseguia justificar para a diretoria** (falha de confiança = quebra de um "must-be").

**Problema:** refatorar o analytics para que ele prove o valor de uso da Auramind para a diretoria do cliente.
**Impacto de negócio:** evitar churn, ampliar assinaturas dentro dos clientes e gerar novos clientes por indicação de gestores/diretores.
**Métrica do que importa:** não é volume de output (telas/relatórios entregues), e sim renovação/expansão do contrato e adoção recuperada antes de virar churn.

---

## Decisões de julgamento

### 1. Formulário de pressuposições — fazer (prioridade alta)

É o conserto direto do must-be quebrado (o gestor não conseguia defender premissas que não pediu). Regra de design: **toda premissa que entra no relatório precisa ser (a) visível, (b) editável pelo gestor e (c) ter um default razoável.** Isso transforma "premissas que eu não pedi" em "premissas que eu controlo" — que é o que o gestor leva para a diretoria. É a intervenção mais barata com o maior ganho de confiança.

### 2. Sistema de pontuação de uso (1/2/3 pts) — bom instinto, com ressalvas

Acertos: "tokens" é jargão (falar "profundidade de uso" com o gestor) e volume bruto engana (quem usa mais é quem gasta mais tokens). Ressalvas antes de construir:

- **É hipótese.** Validar no formulário/entrevistas se o gestor liga para profundidade de uso ou só para "quem usa / não usa".
- **Quem define que uma pergunta é "difícil" é você** — ou seja, é exatamente o tipo de premissa opaca que quebrou a confiança. Se implementar, os pesos precisam ser transparentes/configuráveis (mesma lógica do formulário de premissas).
- **É camada de performance, não must-be.** O must-be é o binário "quem não está usando", que não precisa de pontuação nenhuma. Fazer o simples primeiro.

---

## Plano de ação

O **scope 0 (ETL + refatoração de tabelas) é o "mastro do circo"**: enquanto o dado não bate, tudo acima dele mente. Nenhuma feature nova antes disso passar. Mas o discovery é paralelizável — começa agora, sem esperar o ETL terminar.

### Agora — 2 trilhas em paralelo

- **Trilha A — Mastro (bloqueia o resto):** terminar os testes do ETL e a refatoração das tabelas. **Critério de saída objetivo:** as queries que não batiam agora reconciliam com a fonte dentro de um % de tolerância definido. Só isso destrava as fases seguintes.
- **Trilha B — Discovery (não espera a Trilha A):** disparar o formulário para os 10 clientes **e** agendar 5–7 conversas de 20 min. O formulário dá largura; a conversa dá profundidade (o "me conta a última vez que deu errado" não cabe num formulário). Levantar os clientes-chave com o PO.

### Fase 1 — Definir o must-be com dado real

Consolidar formulário + entrevistas, ranquear as visualizações e separar **must-be / performance / delighter** (Modelo de Kano). Confirmar ou derrubar a hipótese de que "quem não usa" é a visualização nº 1. Escrever o **email de anúncio (PRFAQ)** mesmo antes de construir: se não é possível escrever, a ideia ainda não fechou. Esse texto força explicitar o retorno para a empresa (anti-churn), lacuna comum do "working backwards".

### Fase 2 — Formulário de pressuposições

Campo de configuração de premissas junto dos filtros (custo-hora, janela de tempo, o que conta como "uso ativo", etc.). Must-be de confiança e decisão de **mão dupla** (reversível) → executar logo após o mastro. **Critério:** o gestor consegue justificar cada número ("saiu daqui, eu mesmo setei").

### Fase 3 — Alerta automático de uso (must-be)

Alerta de "quem não está usando", empurrado para o gestor **onde ele já está** (email), sem exigir login no analytics (insight de "achar o usuário no fluxo dele" / servidor MCP). Antes do backend pesado: mockar o alerta + 1 relatório real de 1 cliente e mostrar para um gestor — **validar o output primeiro** (evitar a armadilha de reconstruir arquitetura antes de validar demanda).

### Fase 4 — Relatório que defende o uso (performance)

Relatório mensal para a diretoria, com o uso "traduzido" (não em tokens) e, se a discovery confirmar, o sistema de pontuação com pesos transparentes.

### Fase 5 — Delighter (depois)

Correlação entre uso e resultado de negócio (ex.: vendedores que mais usam × crescimento de vendas). Alto valor percebido, porém caro e dependente de dados do cliente. Não construir antes de must-be + performance sólidos — senão vira o "super dashboard que ninguém vê".

> **Loop de feedback:** validar com um gestor ao fim de cada fase (human on the loop).

---

## Formulário de discovery — enviar aos 10 clientes

### Princípios de design

- Pedir para **dar nota / ranquear**, não só marcar — separa must-be de nice-to-have (Kano).
- Perguntar **comportamento** (o que faz hoje), não só preferência (o que quer) — técnica do *The Mom Test*.
- **Um campo aberto por seção** para capturar o que não foi previsto ("dogs not barking").
- **A última pergunta recruta para a entrevista** (o formulário dá largura; a entrevista dá profundidade).
- Curto (~5 min, 6 seções): retornos decrescentes — 5–7 respostas já rendem a maior parte do aprendizado.
- Abrir com uma linha de "por que estou perguntando isso" para aumentar a taxa de resposta.

### Seção 0 — Contexto

- Nome, empresa, cargo/função.
- Quantas pessoas do seu time usam a Auramind?
- Você é quem reporta o uso da plataforma para a diretoria? (Sim / Não / Às vezes)

### Seção 1 — Processo atual (comportamento)

- Com que frequência você precisa reportar o uso da Auramind para cima? (Semanal / Mensal / Trimestral / Nunca)
- Descreva, passo a passo, como você faz isso **hoje**. *(aberta)*
- Quanto tempo por mês você gasta nisso? (faixas: <1h / 1–3h / 4–8h / >8h)
- Qual foi a **última vez** que isso te deu trabalho ou deu errado? O que aconteceu? *(aberta — Mom Test)*
- O que você faz na segunda de manhã em relação ao uso da plataforma? *(aberta — testa a hipótese do produto)*

### Seção 2 — Decisões (o "job" real)

- Que decisões você toma a partir dos dados de uso? *(múltipla: cobrar quem não usa / justificar renovação / expandir licenças / treinar times / outro)*
- Qual pergunta sobre o uso você gostaria de responder e hoje não consegue? *(aberta)*

### Seção 3 — Visualizações desejadas (o "top 10", com priorização)

Peça uma **nota de importância de 1 a 5** para cada item:

| Visualização | Importância (1–5) |
|---|---|
| Usuários inativos (quem **não** está usando) | |
| Ranking de usuários por volume de uso | |
| Ranking por profundidade / complexidade de uso | |
| Temas e assuntos mais perguntados | |
| Problemas / dores mais recorrentes nas conversas | |
| Evolução (tendência) do uso ao longo do tempo | |
| Comparativo entre times / departamentos | |
| Sentimento das conversas | |
| Correlação uso × resultado de negócio (ex.: vendas) | |
| Relatório pronto para a diretoria (export/PDF) | |

- Marque as **3** que, se faltassem, tornariam o analytics **inútil** para você. *(isola o must-be)*
- Que visualização faltou nessa lista? *(aberta)*

### Seção 4 — Premissas e confiança (o problema-chave)

- Você confia nos números a ponto de levá-los para a diretoria? *(escala 0–10)*
- Quais premissas você precisa poder ajustar sozinho? *(múltipla: custo-hora / período / o que conta como "uso ativo" / metas / quais usuários entram / outro)*
- Já teve algum número que você **não conseguiu defender / justificar**? Qual? *(aberta)*

### Seção 5 — Formato de entrega

- Como você prefere receber isso? *(dashboard / relatório PDF mensal / alerta automático por email / dentro de uma ferramenta que já uso / outro)*
- Se recebesse um alerta automático de quem não está usando, com que frequência? *(Semanal / Quinzenal / Mensal)*

### Seção 6 — Fechamento

- De 0 a 10, quão importante é melhorar isso para você? *(prioriza)*
- Topa uma conversa de 20 min para eu te mostrar um protótipo? *(Sim / Não — converte o formulário nas 5–7 entrevistas)*

---

## Próximo passo imediato

Escrever o **email de anúncio (PRFAQ)** do novo analytics — o exercício que mais destrava o resto e pode ser rascunhado enquanto o ETL roda. Ele deve conquistar o leitor nos dois primeiros parágrafos e deixar explícito o retorno para a empresa (anti-churn), não só o benefício para o cliente.
