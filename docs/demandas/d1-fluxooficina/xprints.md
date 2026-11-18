# XPRINTS: FluxoOficina

| | |
|---|---|
| **Demanda** | `d1-fluxooficina` |
| **Tipo de entrega** | planejamento em código |
| **Caminho da estimativa** | prévia |
| **Autoridade visual** | DS próprio, `fluxo-oficina-ds` (https://github.com/guantunes17/fluxo-oficina-ds), feito do zero sobre o shadcn/ui, com Inter e tokens petróleo, âmbar e neutro frio. Pacotes web e native (Expo). Não usa o DS XPRINTS (decisão da pessoa em 2026-11-17) |
| **Superfícies** | App mobile em Expo (React Native) para o mecânico, sempre com internet. Painel web desktop para dono, gerente e recepção. Cliente final por WhatsApp. Três repositórios de código (mobile, painel, agentes) e este repositório como hub de especificação (decisão da pessoa em 2026-11-17) |
| **Fase atual** | 2 · Diagnóstico e validação |
| **Passo atual** | 2.61E · `exploratory-prototype-from-ef-macro`, comparação revisada em 2026-11-17 |
| **Próximo passo** | 2.62 · `activity-diagrams-from-ef-macro`, depois da aprovação da arquitetura alvo pela Liderança |
| **Ciclo** | 1 |
| **Atualizado em** | 2026-11-17|

## Entrada direta pela Validação

| | |
|---|---|
| **Motivo da entrada** | O discovery foi feito fora da pipeline (resposta da pessoa em 2026-11-17: "Discovery já foi feito"). A demanda entra pelo brief e vai até o protótipo. |
| **Passos pulados** | Fase 1 inteira e diagnóstico (2.01 a 2.54), com o motivo "entrada direta pela Validação" |
| **Escopo vendido** | Não se aplica: projeto interno, sem venda. Escopo: sistema multiagentes para auxiliar uma oficina mecânica (P-01, resolvida em 2026-11-17) |
| **Gates que não se aplicam** | 1, 2, 3a, 3b, 4 e 5 |

| Fonte usada na 2.60 no lugar do discovery | Caminho | Trazida por | Data |
|---|---|---|---|
| Proposta de valor e business model | `docs/demandas/d1-fluxooficina/context-sources/fluxo-oficina-proposta-de-valor-e-business-model.md` | a pessoa | 2026-11-17 |
| Fontes E1, E2, E3, NOTA e NOTA-R | `docs/demandas/d1-fluxooficina/brief.md`, seção "Fontes de contexto" | a pessoa | 2026-11-17 |

## Passos

| Passo | Etapa | Atividade | Skill | Status | Artefato | Data | Motivo ou nota |
|---|---|---|---|---|---|---|---|
| 1.01 | 01 | B-01 Coleta do briefing | `compilar-transcricao` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.01D | 01 | D-01 Setup do workspace de IA do projeto | `/playbooks/pre-venda/como-funciona/d-01` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.02 | 01 | B-02 Análise do briefing e lacunas | `briefing-from-meeting` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.02C | 01 | Sem atividade no catálogo | `setup-navigable-catalog` | pulado | | 2026-11-17 | sem repositório do produto |
| 1.03 | 01 | B-02 | `debriefing-from-client-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.04 | 01 | B-02 | `compilar-transcricao` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.05 | 01 | B-02 | `debriefing-from-client-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.06 | 01 | B-03 Montagem da estimativa | `preliminary-estimate-from-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.07 | 01 | B-03 | `estimate` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.08 | 01 | B-03 | `preliminary-estimate-from-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.09 | 01 | B-04 Montagem do cronograma e da proposta | `proposal-from-preliminary-estimate` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.10 | 02 | D-76 Importação da estimativa no XPrints | `preliminary-estimate-from-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.12 | 02 | D-02 Premissas de dados, privacidade e uso de IA | `/playbooks/setup-inicial-de-projeto/como-funciona/d-02` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.13 | 02 | D-03 Curadoria contínua de outputs de IA | `/playbooks/setup-inicial-de-projeto/como-funciona/d-03` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.14 | 02 | D-04 Condução de rituais, status semanal e gestão da estimativa | `weekly-status-from-xprints` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 1.15 | 02 | D-76, D-04 e A-01, o reporte contínuo | `xprints-apontar-atividades` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.01 | 03 | D-05 Kick-off e reunião de alinhamento inicial | `kickoff-deck-from-proposal` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.02 | 03 | D-05 | `compilar-transcricao` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.03 | 03 | D-06 Imersão no produto atual com navegação guiada | `/playbooks/diagnostico/como-funciona/d-06` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.04 | 03 | D-07 Digestão das bases existentes e curadoria dos achados | `/playbooks/diagnostico/como-funciona/d-07` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.10 | 03 | D-77 Desk research e benchmark de referências | `desk-research-from-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.11 | 03 | D-08 Conversas de imersão com o time interno e síntese | `research-guide-from-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.12 | 03 | D-08 | `compilar-transcricao` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.13 | 03 | D-09 Desk research e benchmarking de concorrentes (diretos, indiretos e análogos) | `desk-research-from-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.14 | 03 | D-12 Roteiro da conversa exploratória, critérios de amostra e modelo de convite | `research-guide-from-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.15 | 03 | D-13 Validação Cliente (roteiro e recrutamento) | `research-guide-from-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.16 | 03 | D-14 Conversas exploratórias com usuários | `compilar-transcricao` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.17 | 03 | D-15 Análise do qualitativo (codificação, temas, evidências) e triangulação | `/playbooks/diagnostico/como-funciona/d-15` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.18 | 03 | D-16 Roteiro quantitativo, lógica de ramificação e cadastro na ferramenta | `survey-from-qualitative-findings` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.19 | 03 | D-17 Validação Cliente (questionário) | `survey-from-qualitative-findings` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.20 | 03 | D-18 Testes, disparo e janela de campo do questionário | `/playbooks/diagnostico/como-funciona/d-18` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.21 | 03 | D-19 Análise do quantitativo e cruzamento com o qualitativo | `/playbooks/diagnostico/como-funciona/d-19` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.22 | 03 | D-21 Dores, gargalos e capacidades atuais | `problems-from-research` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.23 | 03 | D-10 Mapa de Experiência As Is e D-20 Refinamento e consolidação (digital e operação) | `experience-map-from-problems` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.24 | 03 | D-21 | `problems-from-research` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.25 | 03 | D-22 Mapeamento de oportunidades de IA na jornada e D-23 Visão To Be macro | `to-be-map-from-problems` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.26 | 03 | D-23 | `/playbooks/diagnostico/como-funciona/d-23` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.40 | 03 | D-39 Preparação do terreno: autorização de acessos, repositório e documentos-base | `technical-assessment-from-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.41 | 03 | D-26 Perímetro de sistemas, D-28 Leitura das camadas técnicas e D-45 Ondas de entrevistas | `technical-assessment-from-briefing` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.42 | 03 | D-45 | `compilar-transcricao` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.43 | 03 | D-49, D-50, D-51, D-53, D-54, D-55, D-56 e D-57, o As Is técnico | `legacy-discovery-from-assessment` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.44 | 05 | D-67 Desenho da arquitetura alvo | `target-architecture-from-assessment` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.45 | 05 | D-69 Validação da arquitetura e do stack com o cliente | `target-architecture-from-assessment` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.50 | 03 | D-11 e D-25 Apresentação ao cliente | `diagnosis-deck-from-discovery` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.51 | 03 | D-11 | `compilar-transcricao` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.52 | 03 | D-11 | `diagnosis-deck-from-discovery` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.53 | 03 | D-11 | `AJ-NN` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.54 | 03 | D-11 e D-25 | `diagnosis-deck-from-discovery` | pulado | | 2026-11-17 | entrada direta pela Validação: discovery feito fora da pipeline |
| 2.60 | 06 | D-62 Protótipo navegável do conceito macro | `brief-from-context-sources` | concluído | `docs/demandas/d1-fluxooficina/brief.md` | 2026-11-17 | estado reconstruído a partir do artefato |
| 2.60O | 06 | D-62 | `opportunity-tree-from-brief` | concluído | `docs/demandas/d1-fluxooficina/descoberta/arvore.md` | 2026-11-17 | estado reconstruído a partir do artefato |
| 2.61 | 06 | D-62 | `ef-macro-from-brief` | em andamento | `docs/demandas/d1-fluxooficina/ef-macro.md` | 2026-11-17 | EF Macro v0.7 em Rascunho, com os achados da rodada 2 aplicados |

## Gates

| # | Gate | Quem decide | Material apresentado | Decisão | Data | Quem respondeu |
|---|---|---|---|---|---|---|
| 1 | O cliente confirma o briefing consolidado (B-02, passo 17) | Cliente | `briefing.md` consolidado | não se aplica | 2026-11-17 | entrada direta pela Validação |
| 2 | Proposta aprovada? | Cliente | o deck da proposta | não se aplica | 2026-11-17 | entrada direta pela Validação |
| 3a | Roteiro e recrutamento validados pelo cliente (D-13) | Cliente | `pesquisa/roteiro-exploratoria.md` | não se aplica | 2026-11-17 | entrada direta pela Validação |
| 3b | Questionário validado pelo cliente (D-17) | Cliente | `pesquisa/questionario.md` | não se aplica | 2026-11-17 | entrada direta pela Validação |
| 4 | Arquitetura validada com o cliente no discovery (D-69, na 2.45) | Contato do cliente que decide a stack | `tecnico/arquitetura-alvo/` | não se aplica | 2026-11-17 | entrada direta pela Validação |
| 5 | Diagnóstico validado com os stakeholders | Stakeholders do cliente | o deck do diagnóstico | não se aplica | 2026-11-17 | entrada direta pela Validação |
| 2.61E | Confirmação: comparação do protótipo exploratório revisada | A pessoa que conduz a validação | `prototipo-exploratorio/comparacao.md`, com toda conversa resolvida e todo achado com veredito | revisada | 2026-11-17 | Gustavo Antunes |

## Confirmações

| Confirmação | Passo | Quem confirma | Resposta | Data |
|---|---|---|---|---|
| Publicação privada no claude.ai autorizada: protótipo exploratório da demanda no Claude Design, com dados fictícios | 2.61E | a pessoa que conduz a demanda | Aprovou o roteiro de 10 telas com o destino Claude Design | 2026-11-17 |

## Publicações

| Deck ou protótipo | Roteiro ou fonte | URL | Versão (rótulo) | Quem publicou | Data |
|---|---|---|---|---|---|
| protótipo exploratório | `prototipo-exploratorio/` | https://claude.ai/artifact/E9LmMjG7nRcsMWTzEn7P7j | protótipo 2026-11-17 | Gustavo Antunes | 2026-11-17 |
| protótipo exploratório | `prototipo-exploratorio/Main.dc.html` | https://claude.ai/artifact/E9LmMjG7nRcsMWTzEn7P7j | protótipo 2026-11-17, rodada 1 com as decisões da pessoa | Gustavo Antunes | 2026-11-17 |
| protótipo exploratório | `prototipo-exploratorio/` | https://claude.ai/artifact/E9LmMjG7nRcsMWTzEn7P7j | protótipo 2026-11-17, visão de quadros estilo Figma | Gustavo Antunes | 2026-11-17 |
| protótipo exploratório | `prototipo-exploratorio/` | https://claude.ai/artifact/E9LmMjG7nRcsMWTzEn7P7j | protótipo 2026-11-17, rodada 2: app mobile e painel desktop | Gustavo Antunes | 2026-11-17 |
| protótipo exploratório | `prototipo-exploratorio/` | https://claude.ai/artifact/E9LmMjG7nRcsMWTzEn7P7j | protótipo 2026-11-17, rodada 2 com push e ordem atribuída | Gustavo Antunes | 2026-11-17 |
| protótipo exploratório | `prototipo-exploratorio/` | https://claude.ai/artifact/E9LmMjG7nRcsMWTzEn7P7j | protótipo 2026-11-18, rodada 3 com os tokens do DS próprio | Gustavo Antunes | 2026-11-18 |

## Pendências que travam

| ID | Origem | Pendência | Passo travado | Dono | Aberta em | Status |
|---|---|---|---|---|---|---|
| P-01 | `xprints.md` | Sem estimativa prévia: escopo vendido indefinido. Resposta: projeto interno, sem escopo vendido. O escopo é um sistema multiagentes para auxiliar uma oficina mecânica | importação no XPrints e estimativa da execução | TD Produto | 2026-11-17 | Resolvida em 2026-11-17 |
| P-02 | `xprints.md` | Autoridade visual (design system) não definida. Respostas: shadcn/ui, depois DS XPRINTS, e por fim DS próprio do zero (2026-11-17) | 2.66 e 2.67 | a pessoa | 2026-11-17 | Resolvida em 2026-11-17: DS próprio `fluxo-oficina-ds` |
| P-03 | `xprints.md` | O DS nativo para o app Expo precisava ser criado (tokens e componentes) | 2.66 e Passo 7 do app mobile | TD Produto | 2026-11-17 | Resolvida em 2026-11-17: pacote `@fluxo-oficina/native` com 20 componentes, testado em bundle e em react-native-web (não em aparelho) |
| P-04 | `xprints.md` | Como o mecânico entra no app (login) e como o app é distribuído (loja ou distribuição interna) | 2.66 e 4.01 | TD Produto | 2026-11-17 | Aberta |
| P-05 | `xprints.md` | O mecânico recebe notificação push no celular? Sim ou não | 2.61 (§9) | a pessoa | 2026-11-17 | Resolvida em 2026-11-17: sim (RF-07) |
| P-06 | `ef-macro.md` | Quem atribui a ordem a um mecânico, e em que momento (P-29 da EF Macro) | 2.66 | a pessoa | 2026-11-17 | Aberta |
| P-07 | `ef-macro.md` | Outros eventos que geram notificação push ao mecânico (P-30 da EF Macro) | 2.66 | a pessoa | 2026-11-17 | Aberta |

## Registro das transições

| Data | De | Para | Motivo |
|---|---|---|---|
| 2026-11-17 | Início | Fase 2, passo 2.61 | Entrada direta pela Validação: discovery feito fora da pipeline; estado reconstruído dos artefatos existentes |
| 2026-11-17 | Fase 2, passo 2.61 | Fase 2, passo 2.61 | Pendências P-01 (projeto interno, sem escopo vendido) e P-02 (shadcn/ui como autoridade visual) resolvidas pela pessoa; sem mudança de passo |
| 2026-11-17 | Fase 2, passo 2.61 | Fase 2, passo 2.61 | Autoridade visual trocada para o DS XPRINTS; linha 2.61 corrigida para em andamento: a EF Macro segue em Rascunho |
| 2026-11-17 | Fase 2, passo 2.61E | Fase 2, passo 2.61 | Passo atrás por decisão de plataforma: mecânico em app Expo, painel desktop e três repositórios. Loop esperado, sem novo ciclo. 2.61 e 2.61E voltam a em andamento |
| 2026-11-17 | Fase 2, passo 2.61 | Fase 2, passo 2.61E | Rodada 2 do protótipo exploratório concluída e comparação revisada. EF Macro v0.7, arquitetura alvo (3 contêineres) e lente r1-mvp gravadas |
| 2026-11-18 | Fase 2, passo 2.61E | Fase 2, passo 2.61E | Autoridade visual passa a ser o DS próprio `fluxo-oficina-ds`. Fecham as pendências P-02 e P-03. O fonte do XPRINTS foi removido deste repositório |
