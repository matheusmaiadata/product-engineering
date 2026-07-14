# Product Engineer

Documento com todos os conceitos, frameworks e exemplos abordados nas duas aulas da pasta "MasterClass Product Engineer" no Granola. Perguntas de alunos foram omitidas; as respostas com conteúdo relevante foram mantidas e integradas ao conteúdo abaixo.

- **Aula 1** — "\[Semana 1\] MasterClass Product Engineer | Fase Define" (6 jul 2026\)  
- **Aula 2** — "Working Session e Office Hour \- Product Engineer" (8 jul 2026\)

---

# PARTE 1 — Aula 1: \[Semana 1\] Fase Define

## 1\. A tese central da masterclass: de "construir" para "julgar"

Frase-guia repetida como fio condutor de toda a formação:

"Quando construir se torna abundante, julgar se torna cada vez mais escasso e cada vez mais específico."

Com IA generativa e agentes de código, a capacidade de *produzir* código, features e até produtos inteiros deixou de ser o gargalo. O gargalo passou a ser o **julgamento**: saber o que construir, para quem, por quê, e avaliar se o que foi construído gera o impacto certo.

A promessa do curso não é ensinar "a melhor decisão possível em abstrato", e sim:

"Te posicionar num nível onde você toma a melhor decisão possível a partir da informação que você tem em mãos." Não necessariamente a decisão ótima que só se enxerga depois de dez anos, mas a melhor decisão possível dado o contexto presente — o curso entrega ferramentas e mecanismos para isso.

A proposta pedagógica é deliberadamente **não nivelar pela média**: "se vocês não saírem incomodados depois das seis semanas, está errado." Como referência de padrão de exigência, foi citada uma palestra de **Christopher Manning** (autoridade em IA, Stanford/Vale do Silício) em que o próprio instrutor sentiu o nível de dificuldade subir a ponto de se perguntar "pra onde você está me levando".

### A trifecta do curso

As seis semanas são estruturadas em torno de três pilares:

- **Definir** — prioridade, visão de produto, métricas a observar.  
- **Construir** — com inteligência artificial: arquitetura, práticas seguras de construção.  
- **Lançar** — go-to-market científico, análise de comportamento do usuário, fechamento do ciclo de feedback (incluindo mecanismos de auto-cura e auto-deploy — "self healing, self deployment").

### Definição de Product Engineer

"A minha definição de engenharia de produto é: profissional sênior que é responsável da ideia ao impacto."

Isso contrasta com a lógica tradicional de squads em que um papel só "tem a ideia", outro "constrói" e outro mede o impacto. A proposta é que o profissional assuma o ciclo inteiro — do "porquê" construir até avaliar se aquilo gerou diferença real. Segundo o instrutor, nenhum líder ou CEO reclama de colaboradores que agem assim; o pedido recorrente de líderes é "queria que meu time trabalhasse como dono do começo ao fim", sem precisar do título formal de "dono".

### Exemplo: o "baseball card" da AWS

Na Amazon/AWS existe um documento de autoavaliação semestral apelidado internamente de "baseball card". Ao preenchê-lo, o instrutor tinha um dado do tipo "coloquei X commits/atualizações em produção neste semestre" e decidiu relegar esse número a uma nota de rodapé, porque colocar código em produção e atingir 50 mil, 100 mil ou 3 milhões de usuários não diz nada sobre qual experiência foi mudada ou qual foi o impacto real. Publicar muitas atualizações pode até passar ao cliente uma falsa sensação de "produto sempre novo" sem gerar valor de fato.

### Alerta sobre profissionais "de uma função só"

Previsão do instrutor: a IA vai substituir os "engenheiros que só fazem uma função" — pessoas hiperespecializadas em uma única tarefa/etapa. Relatou o caso de um engenheiro em Austin que, em novembro do ano anterior, disse estar preocupado por ter focado demais em habilidades que "não vão ser mais utilizadas" à medida que a IA evolui.

## 2\. O estado do mundo: panorama de adoção de IA em produto e engenharia

Conteúdo baseado em um evento em San Francisco (300+ palestrantes, 600+ sessões, 40+ atividades paralelas, 4 dias) do qual os instrutores trouxeram dados e visitas a escritórios (Cursor, Conductor).

### O mito da defasagem Brasil–EUA

A ideia clássica de que "uma tecnologia lançada nos EUA demora de 5 a 10 anos para chegar ao Brasil" morreu. Ao se conectar diretamente às fontes e adotar rápido, a distância entre "como as coisas são feitas aqui" e "como são feitas na ponta" está cada vez menor.

### Paralelo histórico: capa do New York Times de 1954

Como contraponto ao pânico de substituição de empregos por IA, foi citada uma capa do New York Times de 1954 anunciando que "o computador vai substituir os tradutores humanos" e que ninguém mais teria emprego — medo que não se concretizou. Posição do instrutor: os empregos vão se multiplicar e mudar drasticamente, e hoje há mais trabalho disponível do que em 1954; o mesmo padrão provavelmente se repetirá com a IA.

### Relatório "Stripe Economics"

Referência citada mostrando como o crescimento de empresas cada vez mais é feito por empreendedores individuais/times minúsculos:

- Maior número histórico de novas aplicações de negócio criadas nos EUA, com forte propensão a serem feitas por uma pessoa só.  
- É 3x mais rápido hoje chegar a uma receita de US$ 1 milhão do que era em 2019\.  
- O teto de crescimento está reduzindo (mais fácil de escalar, dada a vastidão de ferramentas disponíveis).  
- A quantidade de cadastros na Stripe feitos por agentes de IA é 4x maior em 15 meses.

### "A pessoa mais perigosa numa sala"

"Não existe alguém mais perigoso dentro de uma sala do que alguém que tem a ideia, coloca ela em prática, e avalia e analisa o impacto."

Citado como característica de todo empreendedor, inclusive reforçado pela fundadora do Nubank, que diria o mesmo — é raro encontrar alguém que "vai lá e resolve". Conclusão prática: mesmo dentro de uma grande empresa, é possível (e preferível) aplicar essa mentalidade "de dono" internamente, aproveitando marca e recursos da companhia.

### Caso Monaco.com — CRM agentic

CRM que substitui de 20 a 30 ferramentas dentro de um único fluxo. A partir do ICP (perfil de cliente ideal) do usuário, o sistema:

1. Identifica quais das \~245 milhões de empresas cadastradas na base fazem sentido abordar;  
2. Usa sinais da internet para priorizar quais empresas contatar primeiro;  
3. Identifica os executivos certos a contatar (ex.: para ferramenta de RH, não necessariamente o CEO; para ferramenta de tecnologia, não necessariamente o sócio);  
4. Constrói a lista de contatos (TAM) e a sequência de disparo de mensagens;  
5. Agenda a reunião automaticamente;  
6. Grava a reunião de vendas com um agente que avalia se o vendedor segue o processo certo e se o próprio ICP está mudando, retroalimentando o funil.

Ilustra o conceito de **produto fechando o próprio ciclo de feedback**, tema também tocado numa conversa com a PostHog, em que sinais de uso da plataforma já são usados para gerar sugestões de produto que o usuário só precisa aceitar.

### Caso Cursor

Empresa fundada há apenas 3 anos, citada em contexto de valorização de US$ 60 bilhões, com mais de 1.000 funcionários (contra estimativas públicas de \~300). Da visita ao escritório e conversa com o VP de vendas, veio o gráfico sobre **inversão da curva de esforço em engenharia de software**: antes, o tempo era gasto desproporcionalmente em planejamento e design, pouco tempo escrevendo/revisando código e menos ainda testando; hoje essa curva se inverteu — cada vez menos tempo é gasto "resolvendo" o código em si.

### SWE-bench

Benchmark que mede o quanto um agente de IA consegue resolver tarefas de engenharia de software como um engenheiro humano faria. Os melhores agentes já atingem a casa de **76%** — reforçando que "resolver o código" deixou de ser o problema principal (por isso o curso dedica duas a três das seis semanas ao bloco de planejamento/design).

### O gargalo virou revisão de código

Segundo conversas com líderes de desenvolvimento no Vale do Silício, o gargalo recorrente hoje não é mais gerar código, mas **revisar** o código gerado por agentes. Exemplo: um engenheiro da PostHog relatou que chegam apenas "sete" sugestões de código novas por dia no repositório — número baixo, mas que ainda assim vira gargalo, pois o papel do sênior passa a ser garantir que o código gerado siga as regras/convenções da equipe.

Caso pessoal do instrutor (\~1,5 ano atrás): um engenheiro recém-contratado não sabia todas as regras de nomenclatura de funções da equipe, recebendo feedback constante de revisão. A preocupação com código limpo sempre existiu, mas agora o central é **entender se o que foi construído por um agente está de fato certo** — a governança de padrões vira ainda mais crítica.

### Sobre saídas ("exits") de startups no Brasil

Em resposta a uma pergunta sobre por que há tantas startups avaliadas em milhões apesar de IPOs mais raros pós-2020:

- No Brasil, saídas via aquisição costumam ficar na faixa de R$ 100 a 200 milhões, e há poucos compradores nesse porte (diferente dos EUA, onde captar via Nasdaq em dólar é mais simples).  
- Exemplo: a **Alumni** (junção entre FIAP, Alura, Star.se e PM3), grupo formado por consolidação no setor de educação, citado como possível caso de saída via fusão. A **Ânima** foi citada como outro grupo que faz esse tipo de aquisição, embora também busque outros tipos de investimento.  
- Conclusão prática: no Brasil, a estratégia mais viável tende a ser construir para uma saída menor (ex.: R$ 30–50 milhões), evitando diluição excessiva do fundador (referência de \~30% de diluição numa saída de R$ 100 milhões).

## 3\. A evolução das ferramentas de desenvolvimento assistido por IA

Evolução em "gerações" de como se trabalha com IA no desenvolvimento:

1. **Copiar e colar**: conversa isolada com ChatGPT/Claude.ai em uma aba, copiando pergunta e resposta manualmente entre o chat e o código-fonte local — sem integração entre chat e IDE.  
2. **Autocomplete dentro da IDE**: ferramentas como GitHub Copilot e as primeiras versões do Cursor, com sugestão de código dentro do próprio editor.  
3. **Terminal agindo na máquina**: ferramentas de terminal em que uma instrução leva o agente a executar operações diretamente na máquina (alterar arquivos, pastas etc.), ainda sem múltiplos workspaces paralelos.  
4. **Múltiplos workspaces paralelos (estado da arte hoje)**: ferramentas que permitem abrir múltiplas sessões/tarefas isoladas em paralelo, cada uma numa pasta própria com cópia limpa do Git, sem que uma sobrescreva a outra, com o chat já vivendo dentro da própria IDE.

### Demonstração ao vivo: Conductor

Ferramenta (empresa de \~6 pessoas, US$ 20 milhões captados) descrita como origem desse modelo de múltiplos workspaces. Fluxo demonstrado: cria uma nova área de trabalho a partir de um pedido (ex.: "mude a home do product engineer para \[tema\], só a tela inicial, e deixe amarelo"), escolhe o modelo de IA, e a ferramenta cria uma pasta nova, puxa os dados do Git para gerar uma versão limpa/isolada, pesquisa o projeto, faz as alterações e permite rodar essa versão isolada em paralelo a outras alterações feitas simultaneamente em outras pastas/portas, sem risco de sobrescrita. Ao final, basta pedir "faça review" para o agente revisar as próprias mudanças antes de ir para produção.

### Outras ferramentas citadas (mesmo padrão)

- **Codex** — mesmo modelo de projetos isolados; integra com **Linear**, permitindo que o agente puxe itens do backlog, execute a tarefa e devolva para revisão (aprovar/comentar e reenviar).  
- **Zed** e **Windsurf** — alternativas ao Cursor, recomendadas gratuitamente para quem não usa Mac (ferramentas de IA para desenvolvimento costumam nascer primeiro para Mac, por causa da cultura do Vale do Silício, e só depois são portadas).  
- **Claude Code (CLI)** — debate em chat: mais liberdade no terminal, porém mais dificuldade de criar rotinas ("hooks") comparado ao Conductor.  
- **Antigravity** (Google) — mencionada, sem experiência pessoal relatada pelo instrutor.

## 4\. Harness vs. LLM: a nova camada de decisão

**Harness**: todo o sistema em torno do modelo de linguagem usado (ferramentas, orquestração, ambiente de execução). A tese: hoje existe mais peso no harness do que no LLM em si.

- **GLM** (possivelmente Zhipu AI): custo de uso muito baixo; modelo citado como "5.2" que não roda localmente, mas tem custo baixo por token e performance parecida com os modelos Opus (Anthropic).  
- **Minimax**: constrói modelos de vídeo, áudio e texto, entre os top 5 em cada categoria segundo o instrutor.

Tese prática: "se você troca o modelo e mantém o harness certo, você consegue uma performance tão boa quanto." A escolha crítica não é apenas qual LLM usar, mas:

- Qual é o motor (LLM);  
- Quais são as ferramentas e arquivos certos disponibilizados ao agente;  
- Como se dá a orquestração em cada etapa (entrada, design, escrita, teste, validação);  
- Como funciona o loop de execução;  
- Critérios de saída: o código compila? Existe teste (unitário, de mutação)? Como se mantém a qualidade ao longo do processo?

## 5\. Ferramenta de indexação/visualização de código

Ferramenta voltada a indexar e visualizar a estrutura de um código-fonte antes de alterá-lo (nome da empresa não identificado com clareza na transcrição):

- Fundada por dois ex-engenheiros do Google, um deles com 12 anos de experiência no índice de busca do Google.  
- Segundo a fundadora, reduz em até 70% o tempo gasto antes de começar a escrever código (tempo de exploração/entendimento do código-base).  
- Funcionamento: pega os dados do repositório e gera diferentes formas de visualização — grafos, hierarquias, símbolos, vetores — ajudando o desenvolvedor (ou o agente de IA) a encontrar rapidamente o componente/arquivo certo a modificar.  
- Motivação: resolver a dor de IDEs tentando "na mão" e de forma bruta identificar quais arquivos precisavam ser alterados.  
- Faz mais sentido para bases de código grandes/complexas, não necessariamente para projetos pequenos e individuais.

## 6\. Autonomia de agentes: até onde ela chega hoje

- Ao trocar de modelo (LLM) mantendo o harness, a taxa de sucesso em determinadas tarefas variou entre **62% e 80%**.  
- Ao pedir para os melhores agentes do mundo criarem um produto do zero, sozinhos, sem intervenção humana, a taxa de sucesso citada foi de **0%**.  
- Frase da equipe da Anthropic: **"Construir agora está mais fácil. Mas gerar valor ainda é difícil."**

### O caso "Open Claw" (grafia aproximada)

Peter, fundador de um projeto citado como "Open Claw", conhecido por uma foto viral trabalhando simultaneamente em 17 janelas/abas de código abertas. Frase dele: **"A habilidade mais importante hoje é decidir."** O projeto teria recebido a maior quantidade de estrelas no GitHub da história, crescendo mais rápido que Linux e que React (Facebook), com 0% do código escrito manualmente por humanos.

Debate gerado entre os instrutores:

- Um pondera que o exemplo "mata a discussão" de que desenvolvedores precisam continuar fazendo exatamente o que fazem hoje, mas reconhece riscos de segurança em deixar agentes soltos sem supervisão.  
- A outra questiona se, para produtos novos do zero, faz sentido buscar alta taxa de sucesso sem supervisão humana — mas, para produtos já em produção (onde o agente aprende como o produto é usado), faz mais sentido usar IA com maior autonomia para criar funcionalidades ou resolver bugs, mantendo "human on the loop" como revisão pontual antes de ir para produção.

### Experimento de rodar agentes durante a noite

Um líder de desenvolvimento de uma empresa citada como "the browser company" relatou o mecanismo: como nos EUA o time geralmente "solta o lápis" às 17h, ele gastava de 10 a 15 minutos construindo um prompt longo, disparado às 17h para rodar a noite toda, verificado só às 8h da manhã seguinte — orientando o agente a não pedir aprovações intermediárias.

O instrutor replicou o experimento: processo levou 2h38 e seguiu o fluxo:

1. Fazer pesquisa (distribuída em múltiplos agentes, se faltar informação);  
2. Analisar o código existente;  
3. Construir um plano de ação;  
4. Criar um agente adversário para avaliar se o plano é "alucinado" ou consistente;  
5. Executar em múltiplos agentes/execuções paralelas;  
6. Avaliar o código gerado;  
7. Fazer testes;  
8. Gerar um relatório final.

Resultado: pediu 26 ferramentas para o agente construir sozinho; ao final, apenas cerca de 5 realmente valiam a pena. Conclusão: bom modelo mental para deixar agentes rodando enquanto se está ausente, mas o output bruto ainda precisa de curadoria/julgamento humano.

## 7\. Human-in-the-loop vs. Human-on-the-loop

"Eu não acho que o seu trabalho deveria ser o seu trabalho. Eu acho que o seu trabalho deveria ser construir as ferramentas e os mecanismos para automatizar o seu próprio trabalho ao máximo possível."

Limites reconhecidos: coisas que um agente não substitui, como "ler a energia da sala", perceber que alguém está com sono, chamar atenção de alguém individualmente, ou liderança situacional ao vivo.

Definições:

- **Human in the loop**: o humano está *dentro* do processo, participando de cada etapa/execução.  
- **Human on the loop**: o humano está *por cima*, orquestrando e gerenciando o processo, intervindo principalmente na revisão/decisão final (ex.: decidir se algo vai para produção).

A tese defendida é tirar ao máximo o "human in the loop" e mover o humano para "on the loop" — aproveitando a competência de gerenciar pessoas, agora aplicada a gerenciar agentes, o que aumenta a capacidade de lidar com ambiguidade, complexidade, escopo e impacto.

## 8\. Uso pessoal/operacional de agentes — case do instrutor

- Mantém três agentes pessoais, apelidados **Tupã, Maia e Caio**:  
  - **Tupã**: agente "geral", com acesso a reuniões, fluxos de aquisição e gravações (exceto conteúdo restrito). Boa parte do conteúdo da própria aula foi baseada em informações puxadas pelo Tupã.  
  - **Maia**: focada em melhorias/otimização de um processo específico.  
  - **Caio**: focado em ajudar a equipe em um processo específico.  
- Roda os agentes no **Telegram** em vez de WhatsApp: não exige número dedicado/verificação da Meta para uso comercial, e fica isolado do ruído social (família, figurinhas, grupos). Para contornar as regras da Meta no WhatsApp, usa um segundo número pessoal (app "WhatsApp" \+ "WhatsApp Business" no mesmo aparelho) para o Tupã responder a "43 melhores amigos" (a turma).  
- Conteúdo sensível é gravado deliberadamente fora do alcance dos agentes: usa o **Granola** para mentorias privadas que os agentes não acessam, reservando o acesso amplo de contexto apenas a conteúdos "abertos".  
- Ferramenta de orquestração citada: **Hermes**, criada pela "No Research" — o diferencial é o gerenciamento de memória, que outras ferramentas exigiam fazer manualmente.  
- Racional para múltiplos agentes: o limitador é humano/mental — "gostamos de chamar coisas de coisas e colocá-las em lugares específicos" (analogia a um quadro na parede, que se sabe onde está mesmo de olhos fechados). O agente em si não "liga" para ter nome; a segmentação existe para facilitar a organização humana. Recomendação: só criar múltiplos agentes se houver valor real, senão é apenas mais trabalho de manutenção.

### Protocolo de comunicação entre pessoas e agentes (insight da AWS)

Um time de alta performance dentro da AWS relatou que o que precisa ser acordado entre as pessoas não é qual ferramenta usar (cada um pode escolher a que preferir), mas sim **o protocolo de como a informação flui de um para o outro** ("como eu pego a informação do meu mundo e entrego pro seu mundo"). A padronização deve estar no protocolo de comunicação/troca de contexto, não na ferramenta escolhida por cada pessoa.

## 9\. Roadmap anunciado para as próximas semanas

- **Semana 2**: forma de construção — como mudar radicalmente a maneira de construir e aproveitar a estrutura/marca de empresas grandes/médias para agir "como dono" internamente.  
- **Semanas 3 e 4**: foco técnico pesado em construção (com Leo Pales e Nate Barlow).  
- **Semana 5**: go-to-market científico, com Giovanni Salvador.  
- **Semana 6**: como fechar o ciclo de feedback em produto, incluindo "self healing" e "self deployment".

Tópicos prometidos e cobertos na Aula 2: framework das cinco perguntas de priorização/escopo, caso Palantir e de uma transportadora, processo de entrevista com clientes, Jobs to be Done, e tipos de pedidos de clientes.

## 10\. Síntese das ideias-chave da Aula 1

- Julgamento é o novo gargalo: construir ficou abundante; decidir o que e por que construir é o que se torna escasso e valioso.  
- Product Engineer \= dono da ideia ao impacto, não apenas de uma etapa da esteira.  
- Métrica de valor mudou: de volume de output (commits, deploys) para diferença/impacto real gerado.  
- Harness \> modelo: a orquestração, ferramentas e ambiente ao redor do LLM pesam tanto ou mais do que o LLM específico usado.  
- Ferramentas de desenvolvimento evoluíram: copy-paste em chat → autocomplete na IDE → terminal agindo na máquina → múltiplos workspaces paralelos isolados.  
- Autonomia total de agentes ainda não funciona de ponta a ponta (0% de sucesso para criação de produto do zero sem supervisão).  
- Human on the loop, não human in the loop: o valor humano desloca-se de executar para orquestrar/gerenciar agentes e revisar decisões críticas.  
- Revisão de código virou o novo gargalo de líderes técnicos, mesmo com baixo volume de sugestões de IA.  
- Protocolo de comunicação \> ferramenta específica escolhida por cada pessoa.

---

# PARTE 2 — Aula 2: Working Session e Office Hour

## 1\. O documento PRFAQ

O **PRFAQ** (Press Release \+ FAQ) é a ferramenta central apresentada para "definição de produto" — documento usado dentro da Amazon/AWS para lançar produtos internamente.

Características:

- Construído como um press release real, no estilo de um anúncio publicado em veículos como o New York Times — conta a "história" por trás do produto, como foi construído, e traz aspas de clientes e de pessoas internas.  
- É majoritariamente texto corrido: até chegar às perguntas frequentes (e aos apêndices), não há imagens, tabelas ou gráficos.  
- Lógica por trás: **"se você não conseguir, em texto, me falar qual que é a sua ideia e conduzir uma narrativa, quer dizer que essa ideia não está fechada o suficiente."** Com IA gerando texto facilmente, é ainda mais importante dominar profundamente o que está escrito.  
- Tem dois grupos de FAQ: (1) perguntas que o cliente faria (por que isso importa para ele) e (2) perguntas internas (por que a empresa está fazendo isso, qual a visão, como isso alavanca o produto como um todo).  
- Deve ser escrito para alguém que não entenda nada do negócio — qualquer pessoa precisa conseguir ler e consumir o conteúdo.  
- Formato de leitura tradicional na Amazon: os participantes leem o documento impresso, em silêncio, dentro da sala, apenas com caneta na mão, sem apresentação de slides. O instrutor relatou ter aplicado o mesmo exercício no SXSW com 120 executivos, com 20 minutos de silêncio absoluto de leitura numa sessão de 1h30–2h.

## 2\. Case analisado: produto fictício de revenda por crédito na Amazon

Produto fictício que permite a um cliente revender itens comprados na Amazon em troca de crédito para novas compras, aproveitando o histórico e a descrição de produto que a Amazon já possui como ativo de "reganho". Pontos levantados pelos alunos, todos tratados como conteúdo válido de análise crítica de um PRFAQ:

- O documento mostra bem o fluxo completo do produto/negócio e traz dados que sustentam o motivo do produto ("visão muito estratégica"), mas mesmo um produto fictício precisa seguir um modelo documental real, legível por qualquer pessoa.  
- Fragilidades identificadas: garantia de comprador/vendedor não estipulada; processo de validação de procedência do item ausente (pode ser caro/difícil de validar via parceiros); problemas de logística (tempo de despacho, previsão de entrega, viabilidade de vender itens muito baratos dado o custo de deslocamento/embalagem); a Amazon reinveste o crédito internamente sem permitir saque (deveria haver rendimento sobre o crédito?); falta de definição sobre validade/expiração do crédito.  
- Questão de "compra verificada"/"selo de confiança": como garantir que o mesmo produto físico está sendo revendido (ex.: um caderno trocado por outro) — possível para produtos com número serial, mas em aberto para outros itens.  
- A estratégia de transformar um ativo que a Amazon já possui (histórico e descrição perfeita do produto) em "reganho" via revenda é uma vantagem competitiva que nenhum concorrente consegue replicar.  
- Crítica de prolixidade: um leitor já havia entendido e "comprado" a ideia nos dois primeiros parágrafos, tendo que consumir mais 9 minutos repetindo o que já sabia. Lição: **é preciso conquistar o leitor logo no primeiro e segundo parágrafo**, senão a pessoa desiste (ex.: vai checar o Slack).  
- O foco claro no benefício ao cliente resolve facilmente a dificuldade que o vendedor teria de criar descrições de produto, já que a Amazon já tem todos os dados à mão.  
- Crítica ao formato do PRFAQ em si: quem escreve é o próprio autor da ideia, que naturalmente a defenderá e usará métricas favoráveis ("é o papo do vendedor que quer ver o filho nascer"), tornando o documento estruturalmente enviesado. Por isso a cultura da Amazon envolve destruir o documento em reunião — pessoas questionam a origem de cada dado ("de onde você tirou essa informação? Hoje a gente tem mais de 180 mil pontos") até o documento amadurecer. A AWS levou cerca de 8 meses de iteração de documento até nascer como empresa.  
- Conceito de **"dogs not barking"** ("os cachorros que não estão latindo"): atenção a perguntas sobre o que *não* foi levantado ou o que parece "silencioso demais" para ser verdade — sinal de que algo pode estar errado.  
- O PRFAQ é um **documento vivo**, que nasce "de baixo para cima": começa como ideia levada aos pares e ao chefe; se aprovado, faz-se um teste rápido e barato para coletar dados; conforme o teste cresce, mais gente fica sabendo ("a bolha vai subindo"), até chegar em fases como convites para um beta público. Exemplo: o teste do Amazon Alexa nasceu como um documento desse tipo.  
- Falta de métricas sobre o retorno **para a Amazon** no case analisado (o documento falava bastante do resultado para o cliente, pouco do retorno de negócio) — o "working backwards" (trabalhar de trás para frente a partir da necessidade do cliente) tende a deixar implícito o ganho da empresa, o que é uma lacuna a se atentar. Dados presentes no documento: 15% de taxa de administração e 86,3% de compras feitas diretamente na própria Amazon.

## 3\. As cinco perguntas de definição de produto

Framework central da fase "Definir":

1. **O problema existe de fato?**  
2. **Jobs to be Done** — qual é o "progresso" que a pessoa precisa fazer?  
3. **Que tipo de valor isso cria?**  
4. **Vale a pena construir?**  
5. **O que pode dar errado?**

## 4\. "O problema existe?" — Case Palantir e Forward Deployed Engineer (FDE)

A Palantir atende clientes (geralmente agências de governo, com contratos muito grandes) que têm, por exemplo, "123 mil bancos de dados" sem definição comum de terminologia, ontologia, hierarquia de dados ou capacidade de cruzar essas informações — problema que a empresa resolve.

- **Forward Deployed Engineer (FDE)**: engenheiro que, em vez de ficar "atrás" (como em consultoria tradicional), vai à frente e resolve o problema tecnicamente junto ao cliente, entregando software customizado (não um PPT, não um "novo processo").  
- O ACV (valor médio de contrato) da Palantir, impulsionado pelo modelo FDE, é de aproximadamente US$ 4 milhões — o maior da indústria, comparado a empresas como a Workday.  
- **Case da transportadora**: o cliente pediu um sistema, escreveu 47 páginas de requisitos, com escopo de 4 meses de construção e 3 meses de estimativa. Em vez de aceitar o pedido literal, o FDE perguntou: **"O que você faz primeiro, segunda-feira de manhã?"** Resposta: "Eu vejo se tem caminhão atrasado, ligo pro estoque." Em vez de construir o sistema completo, o FDE construiu apenas um **alerta no Slack** conectado ao sinal exato que a pessoa precisava.  
- Lição central: **"o que a pessoa precisa, que o cliente vai te dizer, não é necessariamente o que ele precisa."** Clientes descrevem soluções, não problemas — cabe ao time fazer as perguntas certas para identificar o problema real.

### FDE vs. consultoria tradicional — espectro de três modelos

- **Consultoria tradicional**: entrega uma "solução mágica" e depois vende um projeto de anos de implementação (ex.: implementação de um Windows Server — não altera o código do produto, só implementa a ferramenta).  
- **Alocação/terceirização de engenheiro**: faz o que o cliente mandar.  
- **Forward Deployed Engineer**: tem ownership total para mudar como o produto funciona/se comporta enquanto está no cliente — descrito por um aluno como "o sonho": "o cara entra, resolve e sai", entende onde dói, resolve com foco a laser, e sai.

## 5\. Técnicas de descoberta de problemas (Customer Discovery)

- **"The Mom Test"** (Rob Fitzpatrick): sua mãe nunca vai falar que sua ideia é ruim. Em vez de perguntar "você usaria isso?", a técnica correta é perguntar **"me conta a última vez que aconteceu esse problema"**, deixando a pessoa narrar o processo, o que fez e o que não fez.  
- **"Abre a tela"**: pedir para o usuário compartilhar a tela e mostrar como faz determinada tarefa no cotidiano (observação contextual).  
- Citação de um ex-líder de vendas do Google Enterprise LATAM: **"quanto mais você sobe no cargo e mais estratégico você se torna, mais importante é fazer perguntas de melhor qualidade — e não ter as respostas certas."**  
- **Case DocuSign**: negociação com um banco grande com contrato limitado a assinatura de documentos financeiros. Ao perguntar quanto custava o processo de gestão de papelada, o banco estimou "meio milhão de reais por mês, mais ou menos". O vendedor calculou uma estimativa própria de US$ 17 milhões; o cliente refez as contas e, quatro semanas depois, admitiu gastar na verdade US$ 40 milhões por ano. Lição: quantificar a dor real do cliente (que ele muitas vezes não sabe medir) é central tanto em vendas quanto em definição de funcionalidades — "muitas vezes, uma funcionalidade tão besta" resolve a dor que faz as pessoas voltarem.  
- **Exemplo interno da Amazon**: um produto interno de atalhos/links para acesso rápido a diferentes plataformas virou, por acidente, uma plataforma extremamente útil, com muitas funcionalidades construídas por causa dessa limitação inicial.  
- Anedota (aplicação bem-humorada da mesma técnica): perguntar "há quanto tempo você está com essa dor? Quanto isso está te custando? Quanto mais você produziria se estivesse melhor?" para quantificar e priorizar a dor antes de "vender" a solução que a resolve.

## 6\. Jobs to be Done (JTBD)

Referência ao livro **"Competing Against Luck"** (Clayton Christensen): em vez de ouvir o que a pessoa *quer que você faça*, o objetivo é entender o que ela *faz todos os dias*.

Estrutura de frase para escrever um JTBD:

"Quando \[situação/gatilho\], me ajude a \[job/progresso desejado\], para que eu \[resultado\], sem \[obstáculo\]."

Exemplos usados na aula:

- "Quando eu chego atrasado no workshop, me ajude a entrar rápido, para que eu não perca os primeiros vinte minutos, sem ficar preso na fila."  
- "Quando eu chego atrasado numa aula, me ajude a pegar o contexto que já foi falado, para que eu não precise pedir para ninguém, sem ficar perdido dentro do processo."  
- "Quando começa segunda-feira de manhã, me ajuda a saber se tem caminhão atrasado, para que eu reponha o estoque a tempo, sem varrer relatório." (conectado ao case Palantir/transportadora, que resultou na automação via Slack).

Depois de mapear o JTBD, a validação com o cliente deve ser direta: "eu tenho uma sugestão, o que você acha? Se eu fizesse isso aqui, quanto resolveria seu problema?" — lembrando sempre que todo código colocado em produção precisa de manutenção futura.

## 7\. Modelo de Kano (1984) — tipos de valor entregue

Metodologia de 1984, ainda muito relevante para decidir "o que construir". Existem três curvas de satisfação:

1. **Necessidades básicas ("must-be")**: ninguém elogia quando presentes, mas a ausência gera forte insatisfação. Exemplo: notificação de confirmação de pedido no iFood. Exemplo pessoal: ao usar o Zelle (equivalente ao Pix nos EUA), não recebeu confirmação de uma transferência e ficou sem saber se havia duplicado a transação.  
2. **Necessidades de performance** (crescimento linear): quanto melhor entregue, mais satisfação, em linha reta. Exemplo: precisão no prazo de entrega — na Amazon existe um "time de promessas" responsável por definir o prazo de chegada de um produto (exemplo pessoal: atraso na entrega de um Kindle recém-lançado). Quanto mais "certeira" a promessa, mais satisfeito o cliente, independentemente de ser mais rápido ou não.  
3. **Necessidades encantadoras/"delighters"** (crescimento exponencial de satisfação): ninguém espera, mas quando entregues geram altíssimo valor percebido.

Ponto de atenção: a barra de necessidades básicas sobe continuamente com o tempo/mercado. Quando o iFood foi lançado, a barra de expectativa era baixa; quando surgiu um concorrente (citado no chat como "Kitu"/"Kita"), a barra já estava muito mais alta (variedade de produtos, velocidade de entrega, notificações etc.), exigindo muito mais investimento inicial só para atingir o nível "básico" esperado.

## 8\. Case de erro de go-to-market — imobiliária australiana

Empresa de tecnologia imobiliária na Austrália, preparando-se para servir o país inteiro, se perguntou "e se todo australiano logar ao mesmo tempo?" O time passou um ano construindo microserviços de altíssima escala, com cache distribuído etc., gastando US$ 1,2 milhão em infraestrutura. No lançamento, tiveram zero usuários reais — a solução técnica estava pronta, mas a estratégia de ir a mercado foi fraca.

Lição aplicada ao contexto atual de IA: hoje é fácil gastar muito dinheiro se preparando com arquitetura/infraestrutura e construir funcionalidades que o cliente não quer. Recomendação: ter uma versão mínima e testar diretamente com o usuário pedindo que complete uma ação específica (ex.: "tenta finalizar uma corrida", "tenta imprimir o relatório X") para descobrir onde ele trava, em vez de assumir escala antes de validar demanda.

Referência complementar: um profissional da PostHog, cujo trabalho é ajudar usuários a descobrirem funcionalidades dentro da plataforma — reforçando que "crescimento é produto" e que observar onde as pessoas clicam/procuram já é suficiente para gerar aprendizado.

## 9\. Case de lançamento mal dimensionado tecnicamente — AOL/discador

Serviço de mensageria com discador (era do dial-up, campanha de CDs promocionais, mascote de cachorro famoso) lançou uma campanha de marketing tão bem-sucedida que a demanda explodiu, mas a infraestrutura de conexão não aguentou o volume, gerando milhares de usuários frustrados. O produto virou "sinônimo de produto ruim" por causa do lançamento malfeito, apesar do sucesso de marketing. Um investidor famoso da época comentou ter sido um dos piores investimentos que já fez, citando esse fracasso de execução técnica no lançamento.

## 10\. Retornos decrescentes em entrevistas de usuário

Gráfico apresentado sobre "diminishing returns" de entrevistas para aprendizado de produto:

- 5 usuários entrevistados → \~50% do feedback relevante coletado.  
- 10 usuários entrevistados → \~95% das melhorias identificadas.  
- 15 usuários entrevistados → \~98% das funcionalidades/problemas mapeados.

Conclusão: falar com poucas pessoas (5 a 7\) já rende uma quantidade "espetacular" de aprendizado. Recomendação atual: capturar todos esses sinais de conversas e usar ferramentas de IA para acelerar a próxima iteração do produto.

## 11\. Leituras recomendadas

- **"The Mom Test"** — Rob Fitzpatrick (técnicas de entrevista de descoberta de problema).  
- **"Competing Against Luck"** — Clayton Christensen (Jobs to be Done).  
- **"Working Backwards"**, publicado em português como "Obsessão pelo Cliente" — processo interno da Amazon de trabalhar de trás para frente a partir da necessidade do cliente, incluindo PRFAQ, FAQs e leitura silenciosa em reunião.  
- **"The Design of Everyday Things"** — citado pela capa icônica de uma chaleira com o bico próximo à alça, ilustrando como design mal pensado gera fricção; usado como analogia para o erro comum de desenvolvedores criarem soluções "tecnicamente corretas" mas mal desenhadas para o uso real.

## 12\. Decisões "One-Way Door" vs. "Two-Way Door"

Uma vez que construir é barato e fácil, o verdadeiro valor está no julgamento sobre o tipo de decisão que se está tomando.

- **One-way door (porta de mão única)**: decisão sem volta fácil, ou com custo de reversão altíssimo. Requer mais tempo, alinhamento e cautela.  
- **Two-way door (porta de mão dupla)**: decisão reversível rapidamente, sem grande custo de erro — a maioria das decisões do dia a dia se encaixa aqui e não deveria ser burocratizada.

Exemplos:

- Caso público dentro da Amazon: decisão de remover uma funcionalidade de reviews aplicada a todos os produtos da empresa. Foi amplamente documentada e aprovada em múltiplas instâncias, mas acabou sendo a decisão errada — e como o custo de reverter era enorme (aplicada em escala global), configurou-se como porta de mão única mesmo sem ter sido pensada assim inicialmente.  
- **Nike/CBF — camisa "Vou de Bandeira" x pedido popular "Vai Brasil"**: apesar da reação ruim do público, a Nike não conseguia reverter a decisão porque a distribuição de milhões de camisetas já estava em curso; só conseguiram ajustar algo pequeno (a cor da meia), não a camiseta em si.  
- Analogia com a decisão de uma emissora de transmitir a Copa do Mundo: a pergunta central levantada foi **"quanto custa ficar de fora?"** — o custo moral/competitivo de não participar de um evento massivo, mesmo caríssimo, quando toda a concorrência está competindo pela audiência.

## 13\. Priorização: a metáfora do mastro do circo

O primeiro mastro do circo demora, dá trabalho e trava diversas outras atividades, mas todo o time precisa erguê-lo primeiro — sem ele não há pipoca, refrigerante, picadeiro, nada funciona. Da mesma forma, em produto/software é preciso identificar quais soluções não são paralelizáveis — o "mastro" que trava a capacidade de operar de tudo o mais — mesmo que não seja a tarefa "sexy" ou a que entrega valor mais rápido, e priorizá-la antes de partir para funcionalidades mais atrativas.

## 14\. Julgamento como método, não dom

"Julgamento não é dom, é método."

O processo de julgamento se resume a percorrer, para qualquer problema/projeto/produto, as perguntas trabalhadas na sessão: qual é o problema? Qual é o Job to be Done? Que valor ele entrega? Vale a pena fazer agora? O que pode dar errado? É uma decisão de porta de mão única ou de mão dupla?

Frase final de impacto: **"A pessoa mais perigosa numa sala é alguém que consegue definir, que consegue construir, que consegue entregar — com velocidade e intensidade alta."**

Foi mencionada uma ferramenta futura (a ser publicada na comunidade) para ajudar a priorizar entre um grande número de funcionalidades — o instrutor citou seu próprio caso de ter tido 400 funcionalidades para decidir entre elas no fim do ano anterior, considerando impacto, necessidade do cliente e confiabilidade.

## 15\. Rigidez de definição vs. flexibilidade no Discovery

Como equilibrar a necessidade de ter uma definição de problema relativamente rígida com a flexibilidade de mudar de direção durante o Discovery:

- O Discovery é o processo de conversar com o cliente, entender os problemas, descobrir o que ele faz e como faz, e fazer as perguntas de alta qualidade já discutidas. **A forma como você constrói a solução precisa ser flexível** — o problema/necessidade é o que deve permanecer fixo, não a solução.  
- Sugestão prática: ao construir uma nova ferramenta/tela, construa primeiro o resultado/output (a tela final que o usuário vê) antes de construir toda a lógica de backend — porque é o backend que dá mais trabalho, e se tudo for construído antes de validar com o usuário, o risco de errar no que for mostrado é maior.  
- **Case pessoal**: responsável por uma plataforma com \~100 usuários que, por sua vez, impactam centenas de milhares de usuários finais. Passou dois meses construindo uma plataforma "super bonita" para acesso a informações, mas o retorno de uso (retenção/frequência) era muito baixo, apesar de feedback qualitativo positivo. Durante uma imersão/hackathon no Colorado, surgiu a ideia: em vez de exigir login na plataforma, encontrar a pessoa onde ela já está — como os usuários recebiam um e-mail automático de atribuição de tarefa, a solução foi criar um endereço de e-mail especial para o qual encaminhavam esse e-mail original; um sistema analisava o conteúdo, processava a ação necessária e devolvia a resposta por e-mail (com link opcional para a plataforma completa). Resultado: altíssima satisfação, pois os usuários não precisavam mais entrar na plataforma nem buscar dados manualmente.  
- Reflexão de fechamento: a equipe percebeu que a plataforma inteira provavelmente deveria virar um **servidor MCP (Model Context Protocol)** — a lógica de negócio e a orquestração determinística/não determinística via LLM continuam sendo responsabilidade do time, mas a interface de entrega passa a ser oferecida via MCP para rodar dentro do LLM/ferramenta que o próprio usuário já utiliza.  
- Frase-síntese: **"Seja apaixonado por resolver o problema, mas seja flexível em como você vai resolver o problema. Seja obcecado em resolver o problema, mas tome muito cuidado para não ficar apaixonado sobre como você está resolvendo ele."**  
- A forma de construir produto está mudando drasticamente por conta da IA, exigindo cada vez mais flexibilidade dos times de produto.

## 16\. Referências e ferramentas adicionais citadas

- **Conductor** — publicada como ferramenta de codificação com IA baseada em múltiplos workspaces (disponível para Mac).  
- **Zed** — citada como empresa seguindo o mesmo movimento de desenvolvimento orientado a IA.  
- **Cursor** — referenciada novamente como exemplo de "correr atrás do sinal certo": empresa construída em 3 anos, avaliada em US$ 60 bilhões.  
- Anúncio de um convidado da semana seguinte para falar sobre um case de transformação de cultura de construção de produto com impacto financeiro relevante, descrito como "uma das formas mais modernas de operar".

---

# Síntese geral (as duas aulas)

- **Julgamento, não construção, é o gargalo real**: com IA, produzir código e produtos ficou abundante; a habilidade escassa é decidir o que vale a pena construir e por quê.  
- **Product Engineer é dono do ciclo completo**, da ideia ao impacto — e não apenas de uma etapa isolada de descoberta, construção ou lançamento.  
- **O PRFAQ e as cinco perguntas de definição** (o problema existe? Qual o Job to be Done? Que valor cria? Vale a pena construir? O que pode dar errado?) formam o método central da fase "Definir".  
- **Clientes descrevem soluções, não problemas** — cabe ao time (via técnicas como "The Mom Test", observação contextual e perguntas de alta qualidade) identificar o problema real por trás do pedido.  
- **Nem toda funcionalidade cria valor da mesma forma** (Modelo de Kano): básicas, de performance e "delighters" — e a barra do que é "básico" sobe com o tempo e a concorrência.  
- **Toda decisão deve ser classificada como porta de mão única ou de mão dupla** antes de se investir tempo excessivo em alinhamento — a maioria das decisões do dia a dia é reversível e não deveria ser burocratizada.  
- **Human on the loop, não human in the loop**: o papel humano se desloca de executar para orquestrar agentes e revisar decisões críticas, especialmente o que vai para produção.  
- **Harness (orquestração, ferramentas, ambiente) pesa tanto quanto o modelo de IA escolhido.**  
- **Seja obcecado pelo problema, flexível na solução** — construa o resultado/output antes da lógica pesada de backend para validar rápido com o usuário.

