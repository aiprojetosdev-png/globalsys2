# Pulso — protótipo para o Hackathon Business Tech 2026 (case Globalsys)

Este arquivo é o contexto completo do projeto. Leia inteiro antes de responder ou mexer no código.
As fontes originais estão em `contexto/` (fora do Git, por sigilo). Consulte-as quando precisar de detalhe.

---

## 1. Como trabalhar comigo (o usuário)

- **Explique antes de implementar.** Quando eu pedir uma mudança ou ideia nova, primeiro diga em poucas linhas o que entendeu e espere eu confirmar. Só implemente direto quando eu disser "implemente", "pode fazer" ou equivalente.
- **Uma coisa por vez.** Trabalho página por página. Não mexa em páginas que eu não pedi.
- **Respostas curtas, simples e diretas.** Sem elogio vazio, sem enrolação.
- **Seja advogado do diabo.** Aponte falhas, riscos e inconsistências com exemplos concretos. Se minha ideia for fraca, diga e explique por quê. Reconheça quando ela for boa.
- **Não adicione coisas que eu não pedi.** Quando eu pedi "o que falta", e você acrescentou vários itens na ficha do cliente, eu não gostei. Proponha; não empilhe.
- **Não troque o que eu decidi sem perguntar.** Exemplo real: trocar o indicador "Custo de atender" por "Excedente não faturado" sem perguntar foi um erro.
- **Antes de afirmar fato que pode estar desatualizado, pesquise.** Se não tiver certeza, diga.
- Escreva sempre em português do Brasil.

---

## 2. O hackathon

- **Evento:** Hackathon Business Tech 2026, FUCAPE. Desafio proposto pela Globalsys.
- **Apresentação:** 15/10/2026, das 8h às 12h. Pitch de **10 minutos** + até **7 minutos** de perguntas da banca. Estourar o tempo tira pontos.
- **Primeiro slide precisa ter o nome da equipe.** Todos os integrantes precisam estar presentes e se apresentar.
- **Sigilo:** proibido citar nomes de pessoas ligadas à Globalsys. Clientes reais também ficam de fora. Os valores do caso foram alterados de propósito (mantendo ordem de grandeza): **use sempre os números do caso**.

**Ficha de avaliação (100 pontos):**

| Critério | Pontos | O que avalia |
|---|---|---|
| Aplicabilidade real da solução | 45 | Solução estruturada, criativa, aplicável e exequível na empresa |
| Domínio do conteúdo e postura | 20 | Clareza, organização, segurança |
| Qualidade visual da apresentação | 20 | **Organização dos slides**, clareza visual |
| Argumentação e defesa | 10 | Sustentar decisões com lógica e fundamentação |
| Gestão do tempo | 5 | Cumprir os 10 minutos |

Fontes: `contexto/caso/desafio-globalsys.pdf`, `contexto/fotos/ficha-de-avaliacao.jpeg`.

---

## 3. O caso Globalsys

Empresa B2B de serviços de tecnologia (sustentação, serviços gerenciados, automação, projetos). Contratos recorrentes: o cliente paga valor mensal fixo e a empresa entrega horas. **Mais horas por cliente = menor margem. O resultado depende da produtividade.**

**Números do caso (os únicos que usamos):**

| Dado | Valor |
|---|---|
| Clientes ativos | 30 |
| Equipe | 10 pessoas |
| Custo anual da área | R$ 1 milhão (≈ R$ 83,4 mil/mês) |
| Horas demandadas | ≈ 1.400 h/mês |
| Custo por hora entregue | ≈ R$ 59,50 (R$ 1 mi ÷ 16.800 h) |
| Horas por cliente | ≈ 47 h/mês |
| Carga por pessoa | 140 h/mês |

**Como funciona hoje:** demandas chegam por vários canais; quem recebe prioriza; urgências interrompem o planejado; alertas técnicos não viram indicador; relatórios ao cliente são manuais, cada analista no seu formato, focados em atividades e não em resultado; o valor percebido depende de quem conduz a reunião.

**Lacunas listadas no caso:** satisfação dos clientes, custo por cliente, rentabilidade por contrato, distribuição real do tempo, histórico comparável. Também: indicadores formalizados, baseline de produtividade, critério documentado de distribuição, rito com cliente e diretoria, métricas de qualidade acordadas.

**Pergunta central:** como estruturar um modelo de gestão, processos, governança e indicadores que dê visibilidade e controle e permita ampliar a capacidade **sem aumento proporcional da equipe e dos custos**?

**Teste da banca:** o que medir? Como governar? Quanto custa e quanto retorna?

---

## 4. O que a liderança da Globalsys disse (entrevista)

Fonte: `contexto/conversas/entrevista-lideranca-globalsys.md` (transcrição automática, com erros). **Nunca cite nomes no pitch.** Chame de "a liderança".

- **Dor número 1:** não sabe se cada cliente vale a pena. Exemplo dado: contrato novo em Oracle APEX que paga ~R$ 1.000 enquanto o especialista custa ~R$ 2.000. Pergunta se faz sentido trocar um cliente grande por vários pequenos.
- Propôs a **matriz colaborador × cliente × stack**.
- Hoje a única métrica é o **SLA**. Hora é apontada à mão no chamado do GLPI; o analista não abre chamado (só a gestão).
- **GLPI** é a fonte de chamados e horas (open source, modificado, com MCP). Chamados também são replicados para o **Azure DevOps**, onde um agente de IA gera a especificação técnica. Usam um gateway de LLM com modelos baratos.
- Contratos: pool de horas mensal, excedente cobrado à parte, horas não acumulam. **O preço de venda da hora fica com o comercial; a liderança não sabe.** O "R$ 160/h" que aparece na transcrição foi erro: ~R$ 60/h é **custo**.
- Sprints **semanais**; urgência estoura a sprint.
- "**Não temos braço para customizar o GLPI.**" A solução precisa ser configuração e leitura de dados.
- **Contra bonificação por volume.** Defende carga equivalente e bom ambiente. Métrica não pode soar como cobrança.
- Aceita contratar (tech lead, QA) **se houver justificativa de ganho**.
- Conhecimento preso nas pessoas: certos analistas ficam presos a certos clientes por domínio de negócio.
- Ele **já tem uma solução própria** (cadastro de colaborador, stack, salário, encargos). Pediu para **não citarmos isso**. Replicar ideias parecidas é aceitável (o caso não fala da solução dele), mas o diferencial do pitch deve ser o que ele disse que **não** tem: gestão de desempenho, processo, alocação e rentabilidade.

A reunião interna da equipe está em `contexto/conversas/reuniao-interna-equipe.md`. As fotos do quadro (`contexto/fotos/`) mostram o mapeamento de processos e os critérios de distribuição (afinidade de stack, horas disponíveis, relação com o projeto).

---

## 5. Diagnóstico e tese

- **Causa raiz:** a hora é registrada **sem qualificação** (tipo, stack, causa) e **sem preço ao lado** (custo e contrato). Por isso nada vira indicador.
- O GLPI **já liga** chamado → cliente → horas → analista. O que falta é: (1) **horas fora de chamado** (estudo, reunião, documentação, pedidos por WhatsApp) e (2) **em quê** a hora foi gasta.
- **Tese do pitch:** "A operação funciona, mas ninguém consegue provar quanto, nem dizer quanto mais ela aguenta."
- **Frase de defesa:** "O GLPI continua sendo onde o dado entra. O painel é onde a decisão acontece."

---

## 6. Formato da apresentação (decidido)

- **O protótipo é a apresentação.** A demo mostra na prática processo, governança e viabilidade.
- **Slides só como complemento** (mínimo 3): capa com nome da equipe, projeção financeira com premissas escritas, e visão de futuro.
- **Visão de futuro:** "se a Globalsys aprovar, o próximo passo é levar esse painel para dentro do GLPI" (open source, aceita plugin de painel). Não vamos implementar no GLPI agora. Falar como **plano**, não como "talvez um dia".
- A demo deve ser contada como **história com decisões**, não como tour de telas.
- Riscos: legibilidade no projetor (testar zoom 125–150%), falha ao vivo (gravar vídeo de backup), tempo (ensaiar cronometrado).

---

## 7. Decisões do modelo

| Tema | Decisão |
|---|---|
| Natureza | Modelo de gestão; o painel é a prova |
| Fonte de dados | GLPI como fonte única de entrada; ninguém digita em dois lugares |
| Arquitetura real (futuro) | GLPI + camada de leitura/análise, painel embutido no GLPI; ações aprovadas por pessoa e gravadas no GLPI |
| Custo de pessoas | Custo-hora **por nível** (júnior, pleno, sênior), nunca salário individual; só exibir grupos com 3+ pessoas (LGPD) |
| Horas disponíveis | Ponto do RH (o GLPI não tem ponto) |
| Trabalho fora de chamado | Chamados internos recorrentes + chamado "Atendimentos avulsos" por cliente; campo "cliente relacionado" |
| Metas | Só de equipe e de cliente. Nada de ranking ou meta individual |
| IA | Pré-preenche, resume, compara e sinaliza. **Sempre com aprovação humana.** Cálculo simples sem IA |
| Visões | Gestor (completa) e Diretoria (enxuta) |
| Histórico | Filtro de mês em todas as telas, não página separada |

**Descartado:** sistema novo de chamados; guardar salário; ponto dentro do GLPI; cronômetro por tarefa; monitorar tela/teclado; ranking individual; relatório semanal para todos os clientes; índice composto de "saúde da conta" (difícil de defender).

**Ideia adiada, não descartada:** subníveis de senioridade (Sênior I/II/III etc.) com custos diferentes no cálculo, exibidos agrupados por nível; e simular a margem de um cliente se outra pessoa assumir o atendimento.

---

## 8. O protótipo (`index.html`)

### 8.1 Técnico

- **Um único arquivo HTML**, sem build, sem framework. CSS + JavaScript puro. Fontes Inter, Space Grotesk e JetBrains Mono (Google Fonts). Login de demonstração com globo de pontos em canvas (qualquer e-mail válido e senha entram; sessão no navegador). Gráficos em SVG desenhados à mão.
- Visual inspirado no admin template do shadcn: barra lateral, cards, tabelas com selos, tema claro/escuro (tokens CSS em `:root`, com blocos para `prefers-color-scheme` e `[data-theme]`).
- **Dados fictícios**, coerentes com o caso. Nomes de pessoas e clientes inventados (conferir que nenhum coincide com cliente real).
- Também publicado como artifact no claude.ai ("Pulso da Operação"). Para republicar, alguém precisa colar o arquivo lá; o Claude Code não publica artifact.

### 8.2 Estrutura do código (seções em ordem)

| Seção (comentário `/* ---------- X ---------- */`) | O que contém |
|---|---|
| Ícones | `IC` (paths SVG estilo lucide), `ic(nome)` |
| Formatação | `brl`, `brlk`, `pct`, `pct1`, `hh`, `esc` |
| Dados fictícios | `MONTHS`, `MF` (volume mensal), `OP_COST=83400`, `BASE_H=170`, `LEVEL_COST`, `STACKS`, `SLA`, `SAT`, `CONF`, `TYPES`, `PEOPLE`, `RAW` → `CLIENTS` |
| Estado | objeto `S` (página, mês, visão, preço, filtros, `kstage` do Kanban, `monthly`, `reports`, `tasks`, `log`, camadas abertas), `URGENT`, `URG_HIST`, `BUF`, `SPRINT_CAP`, `SPRINT_PLAN` |
| Cálculos | `directedH`, `monthCalc(m)` (núcleo: receita, custo, margem por cliente), `avgCost`, `focal`, `quadOf`, `QUAD`, `negStreak`, `coverage`, `alerts` |
| Gráficos | `chartHours`, `chartQuadrant` (mapa da carteira com zoom), `quadList`, `sparkMargin`, `chartUrg` |
| Componentes | `kpi`, `delta`, `qBadge`, `marginBadge`, `useBar` |
| Clientes | `PROJ` (segmento, projeto, ano de início por cliente), `cliInfo`, `satM`, `rwM`, `rowOf`, `cSeries`, `CTABS` + `pgClients` (sub-abas), `tabRent`, `clientTable` (ordenável, `S.csort`), `pgClient` (página completa, `S.client`, abas `S.cpt`) + `cResumo`, `cSignals`, `cTimeline`, `cFin` (+ `chartFin`, `simCalc`/`simOut`), `cCham` (+ `chartTickets`), `cSpr`, `cPess`. `monthCalc` tem memória por mês e preço (`MCC`). Dica flutuante `#tip` via `data-tip` |
| Páginas | `PAGES` + `pgOverview`, Kanban (`KST`, `kanbanItems`, `kanbanHTML`), `score`, `pgSprint`, `pgTeam` + `teamTable`, `teamMatrix`, `teamRisks`, `teamOff` |
| Pessoas: ficha individual | `TL` (tech lead), `DEVX` (RH e 1:1), `LVP` (referência por nível), `STORY` (situações plantadas), `devMonth(p,m)`, `hoursByClient`, `reallocEvents`, `ownDelta` (compara com a média dos 3 meses anteriores da pessoa), `pgPerson`, `pgTechLead`, `modalPauta` |
| Camadas | `reportDraft` (relatório mensal), `sheetClient` (ficha do cliente) |
| Relatórios | `AI` (textos simulados), `makeReport`, `checks` (cada item com chave `k`), `monthTasks(c,m)` (relatórios de task fictícios que compõem o mensal; id `v:cid:m:k`), `getR`, `taskTable`/`tabTask`, `tabMonthly`, `tabQuality`, `pipeline`, `pgReports`, `isGeneric`, `aiMerge`, `modalReport` (aceita id numérico ou virtual), `modalAdd`, `sheetMonthly`, `cliSla`, `cliRework` |
| Render | `render()` redesenha a página; `renderLayer()` só as camadas (ficha, modal); `toast()` usa `#toastbox` separado (não apaga o que está digitado) |
| Eventos | **delegação**: todo clique tem `data-act` e cai num único `addEventListener('click')`. Também `input`, `change`, `mouseover` (destaque ligado lista↔gráfico via `data-hl`), drag & drop do Kanban, `Escape` fecha camadas |

**Cuidados ao editar:**
- Ações novas: adicione `data-act="nome"` no HTML e um `if(a==='nome')` no handler de clique.
- Se a ação mexe numa camada aberta, use `renderLayer()`; se muda a página, `render()`.
- Antes de re-renderizar um modal com campos, salve os valores no estado (`readFields`), senão o texto digitado se perde.
- Mantenha cores só via tokens CSS (funciona nos dois temas).

### 8.3 Dados fictícios e situações plantadas

- **Pessoas (10):** 3 sêniores (Ana, Bruno, Diego), 4 plenos (Carla, Elisa, Fábio, Íris), 3 júniores (Gabriela, Heitor, João). Custo mensal com encargos e ferramentas: Sênior R$ 11.900, Pleno R$ 7.950, Júnior R$ 5.300 → soma R$ 83,4 mil. Cada pessoa tem stacks com nível 1–4, horas de ponto, horas em clientes e internas.
- **Clientes (30):** stack, pool, horas por mês (abril a setembro), criticidade, fator de preço, se o excedente é faturado, quem atende (% das horas), satisfação. **Setembro soma exatamente 1.400 h.**
- **Vale Verde Agro:** contrato de R$ 1.000 em Oracle APEX (ativo desde julho), ninguém tem nível 3+ em APEX. As horas de estudo de APEX da Carla vão para ele como custo → margem ≈ −129%. É o exemplo da liderança.
- **Ferro & Aço Industrial:** cliente grande (190 h de 160 h), atendido por sênior, margem ~11% → Reprecificar.
- **Go:** stack que ninguém domina (Logística Porto Seco).
- **Clínica Viver:** atendida 70% por sênior num contrato barato → Revisar escopo.
- **Ana:** acima de 90% de ocupação.
- **Excedente não faturado** em 3 clientes (vazamento de receita).

### 8.4 Fórmulas

- **Custo-hora do nível** = custo mensal do nível ÷ 170 h.
- **Custo direto do cliente** = Σ (horas no cliente × custo-hora do nível de quem atendeu) + tempo interno dedicado a ele (campo "cliente relacionado").
- **Rateio** = (custo total da área − tempo dedicado) ÷ soma dos custos diretos de horas → fator (~1,17). Custo total do cliente = custo direto de horas × fator + tempo dedicado. **A soma de todos os clientes fecha em R$ 83,4 mil.**
- **Receita** = contrato (pool × preço da hora × fator do cliente) + excedente × preço × 1,3 (se faturado). **Preço da hora é premissa ajustável** (padrão R$ 85/h), porque o preço real fica com o comercial.
- **Margem** = (receita − custo) ÷ receita.
- **Quadrante:** consumo do pool > 100% = esforço alto; margem ≥ 15% = margem boa. Proteger (boa, ≤100%), Otimizar (boa, >100%), Reprecificar (baixa, >100%), Revisar escopo (baixa, ≤100%).
- **Regra de pauta:** margem negativa 2 meses seguidos → pauta de reprecificação.
- **Ocupação** = horas em clientes ÷ horas de ponto (≈ 83%). Atenção: depende da jornada; dizer na banca que vem do ponto do RH.
- **Buffer de urgência** = média das horas urgentes das últimas 8 sprints + 1 desvio-padrão (≈ 35 h).
- **Score de alocação** = stack (nível/4 × 50) + folga na sprint (até 30) + já atende o cliente (até 20).
- **Retorno (conservador):** relatório 1,5 h/cliente × 30 × 70% + triagem 5% × 50% + retrabalho 3% × 50% ≈ 88 h/mês liberadas; implantação 170 h; manutenção 20 h/mês + R$ 60 de gateway; payback ≈ 2,6 meses após 3 meses de implantação.

### 8.5 Páginas atuais (estado em 14/10, 22h)

**Visão geral** — 6 indicadores do mês (ocupação, consumo do pool, margem, SLA, satisfação, confiabilidade do dado), horas × pool em 6 meses, alertas do mês, para onde foi o tempo, pauta da revisão mensal. *Ainda não revisada com o usuário.*

**Clientes** — reformulada em 15/10 a pedido do usuário:
- 4 indicadores: Receita do mês, **Custo de atender**, Margem média, Satisfação média. Seletor de preço da hora (premissa).
- **Sub-abas:** Mapa da carteira · Rentabilidade · Ações em andamento · Todos os clientes.
- **Mapa da carteira**: **escala fixa 50–150% de pool e −20% a 80% de margem** (era 0–200% / −60–75%; mudada para tirar o aperto), tamanho = margem em R$, tracejado = margem negativa, quem passa do limite fica preso na borda com o valor escrito (Vale Verde). Linhas de referência rotuladas, contagem por quadrante, dica flutuante ao passar o mouse. **Clicar numa área dá zoom** no mesmo card, com só uma seta de voltar. Lista à direita com resumo dos quadrantes ou os clientes do quadrante em ordem.
- **Rentabilidade**: barras de margem em R$ por cliente (direita = resultado, esquerda = prejuízo), acumulado da margem positiva, ordenar por R$ ou %.
- **Ações em andamento**: Kanban (Em alerta → Na pauta da revisão → Em negociação → Resolvido; arrastável; entram sozinhos os clientes com margem < 15%).
- **Todos os clientes**: busca (nome, stack, segmento), filtro por stack e quadrante, colunas ordenáveis, tendência da margem (sparkline), SLA, satisfação.
- **Dentro de Clientes, clicar num cliente abre a página completa** (`pgClient`): cabeçalho (segmento, projeto, stack, criticidade, desde, pool, ponto focal) e abas Resumo (6 indicadores com sparkline, sobre o projeto, sinais do mês sem nota composta, linha do tempo), Financeiro (receita × custo, de onde vem a margem linha a linha, preço × custo por hora, contrato mínimo para 15%, **simulador de renegociação**), Chamados (volume por tipo, lista que abre o relatório da task), Sprints e entregas (itens da Sprint 42, planejado × realizado, previsão), Pessoas e conhecimento (quem atende, cobertura da stack).
- **Ficha lateral do cliente** (enxuta) continua igual quando aberta da Visão geral ou da Equipe, com botão "Ver tudo sobre o cliente". Na ficha enxuta, **não** colocar custo direto/total, valor mínimo ou ponto focal (isso fica só na página completa).
- Segmento, descrição do projeto, ano de início, tempo de resolução e histórico por sprint são **fictícios**: conferir que nada lembra cliente real.

**Sprint e alocação** — capacidade (350 h), planejado (300 h), buffer, alocado; urgência com 3 sugestões de pessoa (score aberto); quando o buffer acaba, sugere adiar item de baixa prioridade; tabela de itens com botão **"Encerrar task"** (gera o relatório da task).

**Relatórios** — fluxo: task encerrada → IA gera relatório → **analista confere e aprova** → IA junta no relatório mensal → **ponto focal aprova e envia**. Abas "Por task" e "Mensal por cliente". Botão "Adicionar relatório" (escolhe a task; chamado, cliente e projeto vêm junto).
- **Relatório da task abre como documento pronto.** Embaixo, campo **"Faltou algo?"**. Botões: **Aprovar depois**, **Corrigir com IA**, **Aprovar relatório**. Link "Editar manualmente". "Corrigir com IA" compara o texto digitado com o relatório: se já estava, avisa e não muda; se é novo, incorpora e destaca. Único aviso automático mantido: horas apontadas maiores que o tempo do chamado aberto (dado do GLPI).
- **Reformulada em 15/10:** 17 relatórios na Sprint 42 (= 17 tasks / 118 h concluídas), com `done`/`apr` (dia de outubro) e `fix` (sem alteração / corrigido com IA / editado à mão). Funil clicável no topo (6 etapas: task → mensal). Abas: **Por task** (filtros de status, analista, busca), **Mensal por cliente** (filtro de status, progresso de envio, horas/pool, SLA, satisfação), **Qualidade do processo** (indicadores da equipe, histórico por sprint fictício 48% → 67%, pontos da conferência, por tipo). Modal da task com dados do GLPI, conferência, linha do tempo e links. Relatório mensal com etapas, prévia do documento, indicadores acordados e a lista de tasks que o compõem (abre a task por cima; fechar volta ao mensal via `closeTop`).

**Equipe** — reformulada em 15/10 e aprovada pelo usuário. 4 indicadores (Ocupação média, Acima de 90%, Stacks em risco, Clientes com uma pessoa só); tabela única "Pessoas e carga do mês" (tech lead no topo, fora da capacidade; colunas Domina nível 3+, Clientes, Ponto, Em clientes, Sem registro, Ocupação; sem coluna "Interno"); matriz de competências agrupada por nível, com stacks em risco destacadas no cabeçalho; "Riscos de cobertura" (stacks com < 2 pessoas nível 3+ e clientes atendidos por uma pessoa só, que abrem a ficha do cliente); "Tempo fora de chamado de cliente" (barra por tipo + sem registro). **Custo por nível foi removido da tela** (continua no cálculo). Clicar numa pessoa abre a **ficha individual** (`S.person`):
- Dev: ocupação, entregas (por complexidade), tempo médio de entrega, precisão de estimativa, retrabalho (reaberto em 30 dias), aprovação de PR de primeira; qualidade de código (Azure DevOps: ciclos de revisão, comentários por PR, tempo até merge, bugs após entrega), SLA, satisfação dos clientes; horas por projeto (planejado × realizado); horas realocadas (inclui urgências atribuídas na Sprint); competências; clientes; plano de desenvolvimento e notas de 1:1; botão **Pauta do 1:1** (rascunho da IA, tech lead revisa).
- Tech lead (Rafael Monteiro, sênior, pessoa nova): PRs revisados, tempo até a 1ª revisão, aprovação de primeira e retrabalho do time, mentoria, incidentes; time sob liderança; tempo por atividade; ADRs; riscos técnicos. **Fica fora da capacidade e do custo** (o caso é 10 pessoas e R$ 1 mi/ano).
- Regras: cada número comparado só com o histórico da própria pessoa; sem ranking, nota ou custo individual; tabelas em ordem alfabética.
- Situações plantadas: Ana (>90% e retrabalho subindo), Carla (retrabalho dobrou desde julho com APEX no Vale Verde), Heitor (retrabalho caiu pela metade com mentoria desde junho), Diego (única pessoa em Go, estimativas estourando).

**Governança** e **Capacidade e retorno** — **removidas do protótipo em 15/10** a pedido do usuário (código apagado; recuperável no histórico do Git, commit `fa53628`). Governança e retorno precisam aparecer em outro lugar (slides ou fala), porque a banca pergunta "como governar" e "quanto retorna".

---

## 9. Pendências (próximos passos combinados)

**Equipe:** página feita em 15/10. Ainda não entraram na ficha individual: lista de tasks do mês e relatórios aprovados/pendentes.

**Sprint** (aguardando confirmação do usuário):
- Urgência **sem tempo estimado** visível (a IA estima por trás; o buffer se ajusta pelas horas reais apontadas).
- Níveis: só **Crítica** entra na sprint atual; **Alta, Média e Baixa** vão para o topo da próxima sprint, nessa ordem.
- "Escolher mais de um": confirmar se é atribuir a urgência a várias pessoas ou selecionar várias urgências.
- **Previsão da próxima sprint** pela automação: saldo de horas dos contratos + urgências pendentes + média das sprints anteriores → "Sprint 43 prevista: X h de 350 h", com o detalhe.
- Explicado ao usuário: as horas dos itens são inventadas no protótipo; na realidade, a estimativa vem da especificação do agente de IA no Azure DevOps ou da média histórica (tipo × stack), e o real vem das horas apontadas no GLPI.

**Outros:**
- Revisar a Visão geral com o usuário (adiada).
- Slides (capa, financeiro, futuro), roteiro falado da demo, vídeo de backup, ensaio cronometrado.
- Conferir que nenhum nome fictício coincide com cliente real.

---

## 10. Como testar

- Abrir `index.html` no navegador (não precisa de servidor).
- Checagem rápida de sintaxe do script:
  ```bash
  node -e "const s=require('fs').readFileSync('index.html','utf8');new Function(s.slice(s.indexOf('<script>')+8,s.lastIndexOf('</script>')));console.log('ok')"
  ```
- Para testar fluxos, usei Playwright (Chromium headless): navegar pelas páginas, clicar em quadrantes, arrastar card do Kanban, encerrar task, corrigir relatório com IA, e verificar que não há erros no console.
- Ao mudar dados ou fórmulas, confira: setembro soma 1.400 h e a soma do custo dos clientes fecha em R$ 83,4 mil.

---

## 11. Arquivos de contexto (`contexto/`, fora do Git)

| Arquivo | Conteúdo |
|---|---|
| `caso/desafio-globalsys.pdf` | Texto oficial do desafio, dados, critérios, regras |
| `caso/slides-apresentacao-do-caso.pdf` | Slides com que a Globalsys apresentou o caso |
| `conversas/entrevista-lideranca-globalsys.md` | Resumo + transcrição da conversa com a liderança (fonte mais importante) |
| `conversas/reuniao-interna-equipe.md` | Resumo + transcrição da reunião interna da equipe |
| `fotos/quadro-mapeamento-de-processos.jpeg` | Fluxo: entrada → criação/categorização → distribuição → sprint → urgência → execução → apontamento; critérios de distribuição |
| `fotos/quadro-glpi-e-distribuicao.jpeg` | GLPI, distribuição sem critério, dados financeiros (garantia, compras, contrato) |
| `fotos/quadro-problemas-e-fluxo-1.jpeg` e `-2.jpeg` | Lista de problemas e fluxo chamado → priorização → trabalho → CS |
| `fotos/ficha-de-avaliacao.jpeg` | Critérios e pontos da banca |

As transcrições são automáticas e têm muitos erros de palavras. Use o resumo no topo de cada uma como referência principal.
