# EF Macro — FluxoOficina

| Campo | Valor |
|---|---|
| Demanda | d1-fluxooficina |
| Versão | 0.4 (inclui análise da Pitz, respostas do Roberto e o cliente final nº 1, de 30/10/2026) |
| Status | Rascunho |
| Data | 30/10/2026 |
| Autor | `<a preencher>` |
| Produto / Revisor | Grupo da FIAP (ponto focal) |
| Origem | `brief.md` desta pasta e `descoberta/arvore.md` |

**Legenda dos rótulos.** `📌 Nota crítica` é lacuna que precisa de resposta antes do Passo 3. `Premissa` é algo assumido sem validação. `Risco` é o que pode dar errado. `Sugestão` é proposta do analista, que não veio das fontes. `[A DEFINIR]` é valor ainda não decidido, e cada um tem linha na §13.

**Nota de método.** O template `ef-macro-template.md` e os arquivos de referência da skill não estavam instalados. Esta EF Macro segue as 13 seções descritas no `SKILL.md`. Os nomes exatos das seções podem diferir do template oficial. Os scripts de conferência (`demand-index.mjs`) e a consulta à base do XPrints também não rodaram.

---

## Sumário

- [1. Contexto, Problema e Critérios de Sucesso](#1-contexto-problema-e-critérios-de-sucesso)
- [2. Escopo](#2-escopo)
- [3. Atores e Permissões](#3-atores-e-permissões)
- [4. Modelo de Dados](#4-modelo-de-dados)
- [5. Requisitos Funcionais](#5-requisitos-funcionais): [RF-01](#rf-01), [RF-02](#rf-02), [RF-03](#rf-03), [RF-04](#rf-04), [RF-05](#rf-05)
- [6. Regras de Negócio](#6-regras-de-negócio)
- [7. Fluxos](#7-fluxos)
- [8. Premissas e Constraints](#8-premissas-e-constraints)
- [9. Integrações e Restrições Conhecidas](#9-integrações-e-restrições-conhecidas)
- [10. Requisitos Não-Funcionais](#10-requisitos-não-funcionais)
- [11. Riscos](#11-riscos)
- [12. Glossário](#12-glossário)
- [13. Pendências](#13-pendências)

---

## 1. Contexto, Problema e Critérios de Sucesso

### Contexto

Oficinas mecânicas gerais de porte médio no Brasil trabalham de forma fragmentada. Atendimento, orçamento, compra de peças, execução e pós-venda usam processo manual e mensagens dispersas entre WhatsApp, ligações e papel (brief 1.2, 3.4).

### Problema

A espera pelo preço e pela compra das peças para o serviço. Isso aparece nas duas oficinas ouvidas: o dono/gerente da Oficina A aponta a demora na cotação com fornecedores como o principal gargalo, e o mecânico da Oficina B diz que o serviço fica parado por causa da pesquisa de preço (brief 1.2, 3.2). O cliente final cobra o status com frequência, e a equipe perde tempo respondendo.

Dois problemas menores reforçam o quadro. A informação inicial errada do cliente afeta cerca de metade dos diagnósticos, segundo uma entrevista (brief 3.2). Os fornecedores não atualizam preço e catálogo, e a integração entre oficina e fornecedor é manual (brief 3.2).

📌 Nota crítica: nenhum dado mede o tempo parado por etapa. A afirmação de que as peças são o maior gargalo vem de duas entrevistas. (P-01)

⚠ divergência a resolver: o dono da Oficina A diz que o cliente cobra o status o tempo todo. O cliente final ouvido (`E3`) não cobrou, porque o serviço ficou pronto no mesmo dia e o mecânico avisou por WhatsApp. A dor do cliente nesse caso foi outra: acompanhar sozinho os itens de revisão e pedir ao mecânico que os verifique. As duas fontes podem estar certas. A cobrança de status pode existir só em serviços longos, com espera por peça. (P-24)

### Critérios de Sucesso

Nenhuma meta numérica veio das fontes. O Resultado Desejado abaixo é uma Sugestão: reduzir o tempo em que o serviço fica parado esperando peças e reduzir as cobranças de status.

| Indicador | Linha de base | Meta | Como é medido | Responsável |
|---|---|---|---|---|
| Tempo parado esperando preço e compra de peças, por serviço | [A DEFINIR] (P-01) | Reduzir (Sugestão). Número [A DEFINIR] (P-18) | [A DEFINIR] (P-02) | [A DEFINIR] (P-02) |
| Cobranças de status do cliente, por serviço (inferido) | [A DEFINIR] (P-02) | Reduzir (Sugestão). Número [A DEFINIR] (P-18) | [A DEFINIR] (P-02) | [A DEFINIR] (P-02) |
| Tempo total de entrega do carro (inferido) | [A DEFINIR] (P-02) | [A DEFINIR] (P-18) | [A DEFINIR] (P-02) | [A DEFINIR] (P-02) |
| Parcela dos diagnósticos afetados por informação inicial errada | 50% (uma entrevista, Oficina B) | [A DEFINIR] (P-18) | [A DEFINIR] (P-02) | [A DEFINIR] (P-02) |

Outros números das fontes, sem função de meta: tempo até o diagnóstico de 1 a 2 horas quando há vaga, e nota 8 (de 0 a 10) para o processo atual, ambos da Oficina B.

---

## 2. Escopo

### Must-have

Todas as capacidades abaixo têm confiança média. Elas entram porque o recorte validado pelo grupo da FIAP, o ponto focal, é a dor de cotação e compra de peças, com visibilidade e voz para o mecânico (brief 1.3). Isso leva `Premissa` em §8 e `Risco` em §11.

- Entrada por voz do mecânico (RF-01). Hipótese HIP-11.
- Cotação de peças com fornecedores (RF-02). Hipótese HIP-01.
- Status do serviço por etapa (RF-03). Hipótese HIP-04.
- Aviso de status ao cliente final (RF-04). Hipótese HIP-04.
- Cadastro de fornecedores (RF-05). Apoia HIP-01.

### Should-have

- Sugestão de causas prováveis a partir dos sintomas, para o mecânico. HIP-09, confiança média. Fica fora do recorte do grupo. O valor maior aparece para mão de obra nova.
- Triagem estruturada do cliente no primeiro contato. HIP-07, confiança baixa. Precisa de teste barato antes (P-03).
- Registro do serviço com fotos, enviado ao cliente por WhatsApp. HIP-14, confiança baixa, vem de um cliente só (`E3`). Precisa de teste barato antes (P-24).

### NÃO faremos (Sugestão)

1. Integração direta com os sistemas dos fornecedores por API ou raspagem. Nenhuma API pública foi achada, e a confiança é baixa (HIP-02).
2. Compra automática de peças e pagamento ao fornecedor. O agente cota, e o dono decide (RN-02).
3. Agendamento de serviços. Hoje usa WhatsApp (`E1`), e fica fora do recorte.
4. Substituição ou integração com o sistema da Oficina B, que é um CRUD sem internet.
5. Aplicativo próprio para o cliente final. O aviso usa mensagem (RF-04).
6. Emissão de nota fiscal, controle financeiro e pós-venda.
7. Catálogo de preços mantido pelo sistema (HIP-03, confiança baixa).

📌 Nota crítica: o grupo ainda não confirmou essa lista de exclusões. (P-16)

### Diferencial frente à concorrência (Sugestão)

Fonte: pesquisa na web de 30/10/2026, fora do brief. Parte do que a Pitz diz de si mesma é alegação da empresa. Nada abaixo foi validado com oficinas.

A Pitz já oferece assistente de voz, diagnóstico por IA, orçamento por WhatsApp e marketplace de peças. Por isso, voz e diagnóstico não são diferencial. Hipóteses de diferencial, em ordem de força:

1. **Cotação neutra nos fornecedores do dono.** O marketplace da Pitz cobra comissão por venda. O agente da FluxoOficina cota nos fornecedores que o dono já usa e compara, sem vender peça. Encaixa em RN-02.
2. **Camada por cima do que a oficina já tem.** Entra por mensagem e áudio, sem trocar o sistema da oficina.
3. **Assinatura fixa, sem comissão.** O Roberto indica que o dono prefere assinatura fixa (`NOTA-R`, sem número de donos ouvidos). Valor [A DEFINIR] (P-23).
4. **Oficina média, com dono e gerente.** A Pitz mira oficinas independentes e familiares.

Os fornecedores já respondem por WhatsApp (`NOTA-R`), o que sustenta o item 1. O item 4 é uma aposta de segmento. Os donos que o Roberto consultou nunca ouviram falar da Pitz, então o mercado ainda não a conhece. Isso não prova que ela não vá crescer. (P-20)

### Features adjacentes

📌 Nota crítica: as fontes não dizem se a demanda é greenfield nem se existem outras features do produto que toquem o domínio (brief 1.6). (P-16)

### Arquitetura alvo

Não gerada nesta rodada. A skill `target-architecture-from-assessment` não estava disponível. (P-19)

---

## 3. Atores e Permissões

### Atores

| Ator | Tipo | Papel |
|---|---|---|
| Dono | Humano | Decide o fornecedor e decide a compra. Conhece fornecedores de outros serviços (impressão do Roberto). |
| Gerente | Humano | Pesquisa o preço das peças. Na Oficina B, quem pesquisa o preço é o gerente. |
| Mecânico | Humano | Faz o diagnóstico e o serviço. Não decide a pesquisa de preço. Prefere interface por áudio. |
| Atendente/recepção | Humano | Fala com o cliente. Não foi ouvido nas entrevistas. |
| Cliente final | Humano | Deixa o carro e, segundo o dono da Oficina A, cobra o status. Um cliente foi ouvido (`E3`) e não cobrou. Quer registro do serviço e lembretes de revisão. |
| Fornecedor | Humano (externo) | Recebe o pedido de cotação e informa preço e prazo. |
| Agente de voz | Sistema | Transcreve e estrutura o áudio do mecânico. |
| Agente de cotação | Sistema | Envia pedidos de cotação e consolida as respostas. |
| Agente de aviso | Sistema | Avisa o cliente quando a etapa muda. |

### Matriz de Permissões (Sugestão)

A fonte confirma só duas linhas: o mecânico não pesquisa preço, e o dono decide o fornecedor. O restante é proposta. Controle de acesso não foi pensado nas fontes. (P-10)

| Ação | Dono | Gerente | Mecânico | Recepção | Cliente final |
|---|---|---|---|---|---|
| Gravar áudio de diagnóstico e peças | — | — | Pode | — | — |
| Cadastrar fornecedor | Pode | Pode | — | — | — |
| Pedir cotação | Pode | Pode | — | — | — |
| Ver comparativo de cotações | Pode | Pode | — | — | — |
| Escolher o fornecedor | Pode | Não pode | Não pode | Não pode | — |
| Mudar a etapa do serviço | Pode | Pode | Pode | Pode | Não pode |
| Ver o painel de status | Pode | Pode | Pode | Pode | Não pode |
| Receber aviso de status | — | — | — | — | Pode |

---

## 4. Modelo de Dados

📌 Nota crítica: as fontes não trazem entidades nem campos (brief 3.9). Tudo abaixo é Sugestão, montado a partir dos campos que os RFs precisam. Tipos, obrigatoriedade e validações são [A DEFINIR]. (P-11)

### 4.1 Relações

| Relação | Descrição |
|---|---|
| Cliente — Veículo | Um cliente tem um ou mais veículos. |
| Veículo — Ordem de Serviço | Um veículo tem várias ordens de serviço ao longo do tempo. |
| Ordem de Serviço — Item de peça | Uma ordem de serviço tem zero ou mais itens de peça. |
| Item de peça — Cotação | Um item de peça tem uma ou mais cotações. |
| Fornecedor — Cotação | Um fornecedor responde várias cotações. |
| Ordem de Serviço — Evento de etapa | Uma ordem de serviço tem vários eventos de etapa. |

### 4.2 Entidades e campos

| Entidade | Campos |
|---|---|
| Cliente | nome do cliente; telefone do cliente |
| Veículo | placa; modelo |
| Ordem de Serviço | número da OS; sintoma relatado; áudio do mecânico; transcrição; diagnóstico; etapa atual; data de entrada |
| Item de peça | descrição da peça; quantidade |
| Fornecedor | nome do fornecedor; contato do fornecedor; categoria de peças |
| Cotação | preço informado; prazo de entrega da peça; data da resposta; fornecedor escolhido |
| Evento de etapa | etapa; data e hora da etapa; autor da etapa |
| Aviso | mensagem de aviso; data e hora do aviso |

Tipo, obrigatoriedade e validação de cada campo: [A DEFINIR] (P-11).

---

## 5. Requisitos Funcionais

### RF-01

**Entrada por voz do mecânico**

**Descrição.** O mecânico grava um áudio com o sintoma confirmado, o diagnóstico e as peças necessárias. O agente de voz transcreve o áudio e monta a lista de peças. O mecânico confere a lista com poucos toques e envia ao gerente.

**Hipótese:** HIP-11 (Confiança: média)

**Telas.** Tela de gravação com um botão grande. Tela de conferência da lista de peças.

**Campos.** placa; modelo; sintoma relatado; áudio do mecânico; transcrição; diagnóstico; descrição da peça; quantidade; data de entrada.

**Regras.** RN-04 (a ferramenta não pode exigir digitação nem muito detalhe).

**Critérios de aceite.** [A DEFINIR] (P-12). Direção: o mecânico monta a lista de peças sem digitar texto longo.

📌 Nota crítica: a taxa de acerto da transcrição para termos de peças ainda não foi testada. (P-08)

### RF-02

**Cotação de peças com fornecedores**

**Descrição.** Com a lista de peças pronta, o gerente ou o dono pede a cotação. O agente de cotação envia o pedido aos fornecedores cadastrados, recebe preço e prazo, e mostra um comparativo ao dono. O dono escolhe o fornecedor. O sistema não compra a peça.

**Hipótese:** HIP-01 (Confiança: média)

**Telas.** Tela de pedido de cotação. Tela de comparativo de respostas, com preço e prazo.

**Campos.** descrição da peça; quantidade; nome do fornecedor; preço informado; prazo de entrega da peça; data da resposta; fornecedor escolhido.

**Regras.** RN-01, RN-02, RN-05.

**Critérios de aceite.** [A DEFINIR] (P-12).

Canal (`NOTA-R`): os fornecedores respondem hoje por WhatsApp. Quando demoram, o pessoal da oficina liga. O agente usa WhatsApp. A ligação de cobrança fica fora desta fase (Sugestão).

📌 Nota crítica: o prazo de espera antes de cobrar o fornecedor segue em aberto. (P-12)

### RF-03

**Status do serviço por etapa**

**Descrição.** Cada ordem de serviço tem uma etapa atual. O mecânico, o gerente, o dono ou a recepção mudam a etapa. Todos os perfis internos veem o painel. As etapas propostas são diagnóstico, aguardando peça, aprovação do cliente, execução e pronto (Sugestão, a partir dos elos listados em `NOTA`).

**Hipótese:** HIP-04 (Confiança: média)

**Telas.** Painel com os carros por etapa. Tela de mudança de etapa.

**Campos.** número da OS; placa; etapa atual; etapa; data e hora da etapa; autor da etapa.

**Regras.** RN-03, RN-06.

**Critérios de aceite.** [A DEFINIR] (P-12).

### RF-04

**Aviso de status ao cliente final**

**Descrição.** Quando a etapa de uma ordem de serviço muda, o agente de aviso manda uma mensagem curta ao cliente com a etapa atual. O objetivo é reduzir as cobranças de status.

**Hipótese:** HIP-04 (Confiança: média)

**Telas.** Sem tela para o cliente nesta fase. A mensagem sai por WhatsApp (Premissa). O dono e a recepção veem o histórico de avisos no painel.

**Campos.** nome do cliente; telefone do cliente; etapa atual; mensagem de aviso; data e hora do aviso.

**Regras.** RN-06.

**Critérios de aceite.** [A DEFINIR] (P-12).

Um cliente final (`E3`) usa WhatsApp e já recebe o aviso de "pronto" do mecânico por lá. Ele não pediu aviso por etapa.

📌 Nota crítica: não sabemos se o cliente de um serviço longo, com espera por peça, quer aviso por etapa. Só um cliente foi ouvido, e o serviço dele durou um dia. (P-07, P-24)

### RF-05

**Cadastro de fornecedores**

**Descrição.** O dono e o gerente cadastram os fornecedores que recebem pedidos de cotação, com o contato e as categorias de peças que cada um atende.

**Hipótese:** HIP-01 (Confiança: média)

**Telas.** Lista de fornecedores. Formulário de cadastro.

**Campos.** nome do fornecedor; contato do fornecedor; categoria de peças.

**Regras.** RN-02.

**Critérios de aceite.** [A DEFINIR] (P-12).

---

## 6. Regras de Negócio

| ID | Regra | Status |
|---|---|---|
| RN-01 | O mecânico não decide a pesquisa de preço de peças. Ela fica com o gerencial. | Confirmado |
| RN-02 | O dono decide qual fornecedor usar. Na Oficina B, o gerente pesquisa o preço e o dono decide. | Confirmado (com ressalva: confirmado só na Oficina B). Ver P-10. |
| RN-03 | O cliente aprova o serviço antes da execução. | Pendente (P-06) |
| RN-04 | A ferramenta do mecânico não pode exigir digitação nem muito detalhe. Entrada por áudio é condição de uso. | Confirmado (com ressalva: vem de uma entrevista, com mecânico da Oficina B) |
| RN-05 | O sistema não compra peça sem a decisão do dono (Sugestão). | Pendente (P-05) |
| RN-06 | O aviso ao cliente sai quando a etapa muda, e só então (Sugestão). | Pendente (P-07) |

📌 Nota crítica: regras de orçamento, aprovação, prazo e garantia não foram mencionadas nas fontes. (P-06)

---

## 7. Fluxos

### 7.1 Fluxo principal

Etapas inferidas das fontes (Sugestão). A pergunta de ator e gatilho de cada etapa ficou em branco no brief. (P-17) As fontes só dizem que o diagnóstico mudou com o tamanho da equipe, e não comparam oficinas de outro porte. (P-13)

1. O cliente deixa o carro. A recepção abre a ordem de serviço. (P-17)
2. O mecânico faz o test drive e define o diagnóstico. Leva de 1 a 2 horas quando há vaga.
3. O mecânico grava o áudio com o diagnóstico e as peças (RF-01).
4. O gerente ou o dono pede a cotação (RF-02). O serviço passa para "aguardando peça" (RF-03).
5. O agente de cotação recebe as respostas. O dono escolhe o fornecedor.
6. O cliente aprova o serviço (RN-03, P-06).
7. A peça chega. O mecânico executa o serviço. A etapa passa para "execução" e depois para "pronto".
8. A cada mudança de etapa, o cliente recebe um aviso (RF-04).

### 7.2 Fluxos alternativos

Categorias assumidas: dado inválido ou incompleto, falha de sistema ou serviço externo, desistência ou cancelamento, e exceção de regra ou permissão.

| Categoria | Fluxo | Tratamento proposto |
|---|---|---|
| Dado inválido ou incompleto | O áudio fica ininteligível ou a transcrição erra a peça. | O mecânico corrige a lista na tela de conferência antes de enviar. |
| Falha de serviço externo | O fornecedor demora a responder à cotação. | Hoje a oficina liga (`NOTA-R`). O agente avisa o gerente, e o pedido pode ir a outro fornecedor. Prazo de espera [A DEFINIR] (P-12). |
| Desistência ou cancelamento | O cliente não aprova o serviço ou retira o carro. | O serviço sai do painel como cancelado. Regra de cobrança [A DEFINIR] (P-06). |
| Exceção de regra ou permissão | O gerente tenta escolher o fornecedor. | O sistema bloqueia e pede a decisão do dono (RN-02). |

---

## 8. Premissas e Constraints

### Premissas

- Premissa: o mecânico tem um celular com internet e microfone na oficina. A Oficina B tem um sistema sem internet, então a conexão pode faltar. (P-08)
- Os fornecedores respondem pedidos de preço por WhatsApp hoje (`NOTA-R`). Deixou de ser premissa.
- Premissa: o cliente aceita receber aviso de status por WhatsApp. Um cliente confirmou que usa WhatsApp e que atende bem (`E3`). (P-07)
- Premissa: as hipóteses de confiança média (HIP-01, HIP-04 e HIP-11) estão certas o bastante para entrar no must-have. Elas vêm de duas entrevistas, sem dado.
- Premissa: o idioma é português do Brasil. As fontes não dizem. (P-14)

### 8.1 Constraints de plataforma e idioma

- Plataforma: celular e computador (informação do Roberto).
- Interface do mecânico: por voz, sem digitação longa (`E2`, `NOTA`).
- Uso sem internet: [A DEFINIR] (P-14).
- Idioma: [A DEFINIR] (P-14).

---

## 9. Integrações e Restrições Conhecidas

| Sistema | Finalidade | Situação |
|---|---|---|
| WhatsApp | Canal de mensagem com fornecedores e clientes | Fornecedores respondem por WhatsApp (`NOTA-R`). Já é usado no agendamento (`E1`). Atributos técnicos [A DEFINIR] (P-09). |
| Sistemas (ERPs) dos fornecedores | Preço e catálogo de peças | Não faremos nesta fase. O mercado tem mais de 15 players, sem líder, e APIs públicas são raras (`NOTA`). |
| Sistema da Oficina B | Gestão interna da oficina | Não integra. É um CRUD sem internet. Nome [A DEFINIR] (P-15). |
| Serviço de transcrição de voz | Transforma áudio em texto (RF-01) | Sugestão. Escolha técnica [A DEFINIR] (P-09). |

📌 Nota crítica: o decisor técnico (stack, plataforma, integrações) não foi identificado. (P-09)

Restrição conhecida: a concorrente Pitz tem tese de "sistema operacional para oficinas" e entra no mercado brasileiro com capital internacional (`NOTA`). A Pitz nasceu no México (confirmado pelo Roberto em 30/10/2026). O Parcial 01 diz "colombiana", e essa informação deve ser corrigida. Segundo a imprensa, a Pitz opera na Grande São Paulo desde outubro de 2025 e tem assistente de voz, orçamento por WhatsApp e marketplace de peças com comissão. Essas funções são alegações da empresa.

---

## 10. Requisitos Não-Funcionais

| Requisito | Valor | Origem |
|---|---|---|
| Praticidade de uso | Entrada por áudio, sem digitação longa | `E2`, `NOTA` |
| Performance | [A DEFINIR] | P-12 |
| Disponibilidade (SLA) | [A DEFINIR] | P-12 |
| Capacidade e volume | [A DEFINIR] | P-12 |
| Acessibilidade | [A DEFINIR] | P-12 |
| Auditoria | [A DEFINIR] | P-12 |
| Retenção de dados | [A DEFINIR] | P-11 |
| Segurança e criptografia | [A DEFINIR] | P-11 |
| Fuso horário | [A DEFINIR] | P-12 |

---

## 11. Riscos

| Risco | Mitigação |
|---|---|
| Hipóteses de confiança média vêm de duas entrevistas e nenhum dado. O gargalo de peças pode não ser o maior. | Medir o tempo parado por etapa em uma amostra de serviços antes de investir (P-01). |
| Fornecedores não respondem por mensagem ou respondem devagar, e o agente de cotação não ajuda. | Testar a cotação por mensagem com 3 fornecedores antes de construir (HIP-01, versão mínima). |
| Mecânicos não aceitam a ferramenta, ou o áudio no barulho da oficina não funciona. | Testar a transcrição com áudio real da oficina (P-08). |
| Oficinas sem internet estável. A Oficina B tem sistema sem internet. | Confirmar a conexão em cada oficina (P-08). |
| Risco regulatório (Sugestão): o sistema guarda telefone, placa e áudio de clientes. A lei de proteção de dados (LGPD) pode exigir consentimento e prazo de retenção. | Definir retenção e consentimento antes da primeira versão (P-11). |
| Concorrente Pitz com capital internacional já cobre voz, diagnóstico, orçamento por WhatsApp e marketplace de peças em São Paulo. As funções do must-have se sobrepõem. | Apostar no diferencial de cotação neutra e de camada sobre o sistema atual (§2). Testar com donos se isso pesa na decisão (P-20, P-21). |
| O diferencial de neutralidade falha se os fornecedores demoram a responder por mensagem. Hoje, quando demoram, a oficina liga. | Medir o tempo de resposta dos fornecedores em 3 cotações reais antes de construir (P-12). |
| A preferência por assinatura fixa vem de poucas conversas, sem número definido, e o valor que o dono aceita pagar é desconhecido. | Testar um valor com 2 ou 3 donos (P-23). |
| O aviso por etapa (RF-04) pode não ser a dor do cliente. O único cliente ouvido não cobrou status e pediu registro do serviço com fotos e lembretes de revisão. | Perguntar a clientes de serviços longos o que querem saber durante a espera (P-24). Considerar subir HIP-14 se mais clientes pedirem. |
| O cliente final não aceita aviso por mensagem. | Um cliente já usa WhatsApp. Confirmar com mais clientes (P-07). |

---

## 12. Glossário

| Termo | O que é |
|---|---|
| Cotação | Pedido de preço e prazo de uma peça a um fornecedor. |
| Oficina geral de porte médio | Oficina que atende vários tipos de serviço, com equipe enxuta. O limite de tamanho não foi definido nas fontes. |
| Test drive | Teste de rodagem que o mecânico faz para achar o problema. |
| Ordem de serviço (OS) | Registro de um serviço feito num carro. Termo do analista, não das fontes. |
| Agente | Parte do sistema que faz uma tarefa sozinha, como cotar ou avisar. |
| ERP | Sistema de gestão usado por oficinas ou fornecedores. |
| Triagem (intake) | Conversa inicial com o cliente para coletar o sintoma do carro. |

### 12.1 Glossário por regime ou contexto

Não aplicável — domínio opera em contexto único.

---

## 13. Pendências

| ID | Pergunta | Referência | Status |
|---|---|---|---|
| P-01 | Você consegue medir, em 10 serviços recentes, quantas horas o serviço ficou parado esperando preço de peças? (sim/não) | §1, §11, HIP-01 | Aberta |
| P-02 | A oficina registra a data de entrada e de entrega dos carros e quem mede esses números? (sim/não) | §1 | Aberta |
| P-03 | A recepção pode testar 5 perguntas fixas ao cliente na entrada do carro, em 10 serviços? (sim/não) | §2, HIP-07 | Aberta |
| P-04 | Os fornecedores respondem pedido de preço por WhatsApp, por ligação ou por e-mail? (WhatsApp, ligação, e-mail) | §9, RF-02, §8 | Fechada: WhatsApp, e a oficina liga quando demoram. |
| P-05 | O agente deve pedir preço a todos os fornecedores cadastrados, ou só aos da categoria da peça? (todos, só da categoria) | RF-02, RN-05 | Aberta |
| P-06 | O cliente aprova o orçamento antes de a peça ser comprada? (sim/não) | RN-03, §7, §6 | Aberta |
| P-07 | O cliente final aceita receber aviso de etapa por WhatsApp? (sim/não) | RF-04, RN-06, §8 | Aberta (parcial: um cliente usa WhatsApp e diz que atende bem) |
| P-08 | O mecânico tem celular com internet e microfone na oficina, e o áudio funciona com o barulho do serviço? (sim/não) | RF-01, §8, §11 | Aberta |
| P-09 | Quem define a tecnologia do sistema: o grupo da FIAP ou outra pessoa? (grupo da FIAP, outra pessoa) | §9 | Aberta |
| P-10 | O gerente e o dono devem ter telas separadas, com o dono sozinho decidindo o fornecedor? (sim/não) | §3, RN-02 | Aberta |
| P-11 | O grupo guarda áudios e telefones de clientes por tempo definido, com consentimento do cliente? (sim/não) | §4, §10, §11 | Aberta |
| P-12 | O grupo define metas de tempo de resposta, disponibilidade e volume, e o critério de aceite de cada função? (sim/não) | §5, §7.2, §10 | Aberta |
| P-13 | O processo muda entre oficinas de porte diferente, como as de equipe maior? (sim/não) | §7 | Aberta |
| P-14 | A primeira versão precisa funcionar sem internet, e só em português do Brasil? (sim/não) | §8.1 | Aberta |
| P-15 | O nome e o fornecedor do sistema da Oficina B são conhecidos? (sim/não) | §9 | Aberta |
| P-16 | O grupo confirma a lista de itens fora do escopo e que não há outras funções do produto que toquem esse domínio? (sim/não) | §2 | Aberta |
| P-17 | A recepção abre a ordem de serviço quando o carro chega? (sim/não) | §7.1 | Aberta |
| P-18 | O grupo define a meta de redução do tempo parado esperando peças e das cobranças de status? (sim/não) | §1 | Aberta |
| P-20 | Os donos consultados nunca ouviram falar da Pitz. Quantos donos foram ouvidos? | §2, §9, §11 | Aberta (parcial: ninguém conhecia a Pitz, e o país de origem é o México) |
| P-21 | Os fornecedores atuais de uma oficina responderiam um pedido de preço por mensagem? | §2, §11, HIP-01 | Fechada: respondem por WhatsApp, e a oficina liga quando demoram. |
| P-22 | O dono prefere pagar assinatura fixa ou pagar por venda de peça? | §2, §11 | Fechada: assinatura fixa (impressão, número de donos não informado). |
| P-23 | O grupo testa um valor mensal de assinatura com 2 ou 3 donos? (sim/não) | §2, §11 | Aberta |
| P-24 | Mais de um cliente final pede registro do serviço com fotos e lembretes de revisão, e clientes de serviço longo cobram o status? (sim/não) | §1, §2, RF-04, §11, HIP-14 | Aberta |
| P-19 | A arquitetura alvo e a lente da primeira release serão geradas depois, com a skill e o template disponíveis? (sim/não) | §2 | Aberta |

Descobertas ainda sem resposta (🔍 do brief): tempo parado por etapa e taxa de informação inicial errada (P-01, P-02); série histórica de tempo de entrega e de cotação (P-02); reclamações de clientes e teste da triagem (P-03).
