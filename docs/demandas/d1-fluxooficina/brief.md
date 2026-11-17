# Brief — FluxoOficina

## Fontes de contexto

| Tag | Fonte | Observação |
|---|---|---|
| `E1` | Oficina A — dono/gerente (conversa exploratória informal) | Vem da síntese do Entregável Parcial 01. Não é fala literal: a transcrição original não foi fornecida. |
| `E2` | Oficina B — mecânico (questionário de validação, preenchido) | Resposta literal. As seções "dono/gerente" e "cliente final" do questionário estão em branco. A pergunta coringa 1 também está em branco. |
| `E3` | Cliente final nº 1 (questionário de cliente final, respondido em 30/10/2026) | Resposta literal. Um cliente só. Serviço que ficou pronto no mesmo dia. O serviço e a oficina não foram informados. |
| `NOTA` | Entregável Parcial 01 — contexto, hipóteses, desk research e síntese do grupo | Texto do próprio grupo. O desk research (ERPs, Pitz) entra como nota, não como dado de pesquisa. |

| `NOTA-R` | Respostas do Roberto às pendências do brief (30/10/2026) | Observações dele nas visitas. Quando ele marca "acredito" ou "me parece", o texto abaixo diz que é impressão. |

O Entregável Parcial 02 (FIAP) é o guia da disciplina. Não é fonte sobre a demanda e não é citado.

Não havia a base de conhecimento do XPrints nesta sessão. As marcas `🔍` abaixo não passaram por essa consulta.

---

## 🔹 1: Informações Gerais da Demanda

### 1.1 Qual o nome que podemos dar para a demanda?

**Citações**
- `NOTA`: "FluxoOficina — Sistema multiagente para oficinas mecânicas gerais de porte médio no Brasil"

Síntese: A demanda se chama FluxoOficina.

### 1.2 Qual o problema que queremos resolver?

**Citações**
- `NOTA`: as oficinas operam de forma fragmentada. Atendimento, orçamento, compra de peças, execução e pós-venda dependem de processo manual e de comunicação dispersa entre WhatsApp, ligações e papel.
- `NOTA`: o cliente final fica sem visibilidade do andamento e cobra status com frequência.
- `E1`: a demora na cotação e no pedido junto a fornecedores é o principal gargalo operacional.
- `E2` (coringa 3): "Demora para dar um retorno pro cliente, o serviço fica parado por causa da pesquisa de preços de auto peças."

Síntese: A dor validada é a demora e a falta de visibilidade na cotação e compra de peças, que para o serviço e gera cobrança do cliente.

### 1.3 Qual o escopo da demanda?

**Citações**
- `NOTA`: recorte validado — "demora e falta de visibilidade na etapa de cotação e aquisição de peças", em oficinas mecânicas gerais de porte médio no Brasil.
- `NOTA`: público prioritário é o dono/gerente e o mecânico. A interface do mecânico deve ser por voz/áudio.
- `NOTA`: achado novo — um agente de triagem/intake mais estruturado no primeiro contato com o cliente.

Síntese: O escopo é a etapa de peças, com apoio de voz ao mecânico e uma triagem inicial do cliente.

- Funcionalidades incluídas e excluídas da primeira versão: Informação não mencionada nas fontes.

### 1.4 Quem participa do processo hoje?

**Citações**
- `NOTA`: quatro perfis — dono/gerente, mecânico, atendente/recepção e cliente final.
- `E1`: vendedores de fornecedores participam da cotação e têm baixo conhecimento técnico das peças.
- `E2` (coringa 4): "essa parte fica mais no departamento gerencial" (a pesquisa de preço de peças).
- `E1`: falta mão de obra de escritório especializada para a comunicação e a gestão administrativa.

Síntese: Participam o dono/gerente, o mecânico, a recepção, o cliente final e os vendedores de fornecedores.

### 1.5 Quem é o ponto focal e quem mais deveria ser ouvido?

**Citações**
- `NOTA`: o dono/gerente é o "decisor da compra e da relação com fornecedores".
- `NOTA`: atendente/recepção e cliente final foram mapeados como perfis, mas não foram ouvidos nas duas entrevistas. No questionário (`E2`), as seções do dono/gerente e do cliente final estão em branco.

- `NOTA-R`: o ponto focal que valida escopo e prioridades é o grupo da FIAP.
- `NOTA-R`: a recepção não será entrevistada nesta etapa, porque o prazo não permite. Um cliente final foi ouvido em 30/10/2026 (`E3`).
- `NOTA-R`: o dono/gerente da Oficina B respondeu o bloco de dono/gerente. As respostas estão só num bloco de notas dele e não foram enviadas.

Síntese: O ponto focal é o grupo da FIAP. O dono/gerente decide a compra de peças. A recepção fica sem ouvir. Do cliente final, só um cliente foi ouvido.

- Decisor técnico (stack, plataforma, integrações): Informação não mencionada nas fontes.
- Conteúdo das respostas do dono/gerente da Oficina B: Informação não mencionada nas fontes.

### 1.6 Outras features do produto ou do ecossistema interno que tocam o domínio?

Informação não mencionada nas fontes.

### 1.7 Constraints de plataforma e idioma

**Citações**
- `E2` (mecânico 5): o que faria não usar uma ferramenta digital é "Não ser prática e exigir muito detalhe. Se for algo por áudio, economizaria muito mais tempo."
- `NOTA`: ferramentas baseadas em digitação tendem a ser rejeitadas no chão de oficina.
- `E1`: o agendamento é feito hoje por WhatsApp.

Síntese: A interface do mecânico precisa ser por áudio. O WhatsApp já é canal de uso.

- `NOTA-R`: a ferramenta será usada no celular e no computador.
- `E3` (cliente 4): o cliente já usa WhatsApp para acompanhar o serviço e diz que atende bem.

- Uso offline: Informação não mencionada nas fontes.
- Idioma: Informação não mencionada nas fontes.

---

## 🔹 2: Perfis, Personas e Permissões

### 2.1 Perfis e personas do sistema futuro

**Citações**
- `NOTA`: dono/gerente (visão macro, custos, fornecedores), mecânico (diagnóstico e serviço), atendente/recepção (comunicação com o cliente) e cliente final (acompanha o status).
- `NOTA`: prioritários na próxima etapa — dono/gerente e mecânico.
- `E2`: confiaria numa ferramenta que sugerisse causas, "pois cada modelo carro tem suas peculiaridades".
- `E1`: uma ferramenta de apoio ao diagnóstico ajudaria, principalmente a mão de obra nova e menos experiente.

Síntese: Os usuários são os quatro perfis. Dono/gerente e mecânico vêm primeiro.

### 2.2 O processo é único ou varia? Por qual dimensão?

**Citações**
- `E2` (mecânico 1): "No começo, quando haviam mais mecânicos, havia um checklist mas hoje em dia, por ter uma equipe enxuta e mais experiente, não tem mais checklist e é executado um test drive."

Síntese: O diagnóstico mudou com o tamanho e a experiência da equipe. As fontes não comparam as duas oficinas por outra dimensão.

- Variação por região, unidade ou porte: Informação não mencionada nas fontes.

### 2.3 Restrições linguísticas, legais ou regulatórias por perfil

Informação não mencionada nas fontes.

### 2.4 Ações que cada perfil pode e não pode executar

**Citações**
- `E2` (coringa 4): a pesquisa de preço de peças "fica mais no departamento gerencial".
- `NOTA`: a decisão da pesquisa de preço fica com o gerencial, "fora do controle do mecânico".

- `NOTA-R`: quem decide fornecedor e preço é o dono. Impressão dele: os donos conhecem fornecedores de outros serviços e fazem parcerias.
- `NOTA-R`: na Oficina B, o gerente pesquisa o preço e o dono decide.

Síntese: O mecânico não decide a pesquisa de preço de peças. Isso é do gerencial, e o dono decide o fornecedor.

- Ações permitidas e restritas por perfil (criar, aprovar, enviar, ver relatório): Informação não mencionada nas fontes.
- Controle de acesso: Informação não mencionada nas fontes.

---

## 🔹 3: Características do Processo

### 3.1 Processo atual em etapas

**Citações**
- `E2` (mecânico 1 e 2): o carro chega, o mecânico faz um test drive para achar o problema, e o diagnóstico leva "de 1-2 horas" quando há vaga.
- `E2` (coringa 3): o serviço fica parado enquanto se pesquisa o preço das peças. Isso atrasa o retorno ao cliente.
- `E2` (coringa 2): "Relata dor na execução do trabalho pós diagnóstico."
- `E1`: o agendamento é feito por WhatsApp. O cliente cobra o status do serviço.
- `NOTA`: atendimento, orçamento, compra de peças, execução e pós-venda dependem de WhatsApp, ligações e papel.

Síntese: As etapas citadas são agendamento, chegada do carro, diagnóstico por test drive, pesquisa de preço de peças, retorno ao cliente e execução. A ordem é inferida das fontes.

- Ator e gatilho de cada etapa: Informação não mencionada nas fontes. A pergunta coringa 1 ("como funciona o processo, do início ao fim") está em branco.

### 3.2 Problemas do processo atual

**Citações**
- `E1`: demora na cotação e no pedido com fornecedores. Falta atualização de preços e do catálogo de peças. A integração oficina–fornecedor é falha e manual.
- `E1`: falta mão de obra de escritório especializada. O cliente cobra follow-up constante.
- `E2` (mecânico 3): "50% dos casos são impactados por erros na informação inical do problema." Exemplo dado: o cliente aponta o defeito num lado, mas ele está em outro.
- `E2` (coringa 3): o serviço fica parado por causa da pesquisa de preço de peças.
- `E2` (coringa 2): dor na execução do trabalho depois do diagnóstico.
- `NOTA`: a comunicação fragmentada gera retrabalho e perda de tempo de mão de obra qualificada.
- `E3` (cliente 1 e 2): o mecânico avisou o cliente por WhatsApp que o carro estava pronto. O cliente não ligou nem foi à oficina, porque sabia que o serviço ficaria pronto no mesmo dia.
- `E3` (cliente 5): o que mais frustra o cliente é ter de acompanhar por conta própria os itens de revisão e pedir ao mecânico que os verifique quando leva o carro.

⚠ divergência a resolver: `E1` diz que o cliente cobra o status o tempo todo. `E3` não cobrou nenhuma vez. As duas fontes podem estar certas, porque `E3` falou de um serviço de um dia, sem espera por peça. Não escolhi um lado.
- `NOTA-R`: impressão dele, não medida — a espera pelas peças pesa mais do que a dor na execução do serviço.

Síntese: O problema mais citado é a espera por cotação e preço de peças. A informação inicial ruim do cliente piora o diagnóstico.

🔍 Precisa de descoberta: tempo parado por etapa (diagnóstico, peça, aprovação do cliente) numa amostra de ordens de serviço, e quantas tiveram informação inicial errada. Quem pode trazer: dono/gerente da Oficina A ou da Oficina B. Quem pode responder: pedir o dado ao cliente; sem o dado, teste barato (`cheap-test-from-hypothesis`).

### 3.3 Indicadores e critérios de sucesso

**Citações**
- `E2` (mecânico 2): tempo até o diagnóstico de "1-2 horas", quando há vaga.
- `E2` (mecânico 3): 50% dos casos com erro na informação inicial.
- `E2` (coringa 5): nota 8 (0 a 10) para o processo atual.
- `E1`: cobrança constante de follow-up do cliente `(inferido: volume de cobranças de status)`.
- `NOTA`: atrasos na entrega por diagnóstico, peças e aprovação do cliente `(inferido: tempo de entrega)`.

Síntese: Há três números (tempo até o diagnóstico, taxa de erro na informação inicial e a nota 8). O tempo de entrega e o tempo de cotação são indicadores inferidos, sem linha de base.

- Meta de cada indicador: Informação não mencionada nas fontes.
- Como é medido e quem mede: Informação não mencionada nas fontes. A pergunta do dono/gerente sobre como mede o tempo de entrega está em branco, e novas perguntas ao dono/gerente não cabem no prazo.

🔍 Precisa de descoberta: série histórica do tempo médio de entrega e do tempo de cotação de peças, com quem mede. Quem pode trazer: dono/gerente da Oficina A ou da Oficina B. Quem pode responder: pedir o dado ao cliente.

### 3.4 Ferramentas, sistemas e canais usados hoje

**Citações**
- `E1`: o agendamento é feito por WhatsApp. A integração entre oficina e fornecedor é majoritariamente manual.
- `NOTA`: WhatsApp, ligações e papel.
- `NOTA`: mercado de ERPs para oficinas fragmentado, com mais de 15 players e sem líder. APIs públicas são raras, e as integrações provavelmente exigirão abordagem customizada ou scraping.

- `NOTA-R`: impressão dele — a Oficina A não parece usar sistema. A Oficina B tem um sistema, que ele acredita ser bem arcaico.
- `NOTA-R`: o sistema da Oficina B é um CRUD, sem acesso à internet.

Síntese: O processo roda em WhatsApp, ligação e papel. Os ERPs existem, mas quase não oferecem API. A Oficina B tem um CRUD sem internet, e a Oficina A parece não ter sistema.

- Nome do sistema da Oficina B: Informação não mencionada nas fontes.
- Atributos técnicos de integração (protocolo, autenticação, endpoints, SLA): Informação não mencionada nas fontes.

### 3.5 Momentos e gatilhos do processo

**Citações**
- `E2` (mecânico 1): o gatilho do diagnóstico é a chegada do carro.
- `E1`: o cliente cobra status de forma recorrente durante o serviço.

Síntese: O processo começa quando o carro chega. As cobranças de status acontecem ao longo do serviço.

- Recorrência, datas-chave e sazonalidade: Informação não mencionada nas fontes.

### 3.6 Regras de negócio conhecidas

**Citações**
- `E2` (coringa 4): a pesquisa de preço de peças é do departamento gerencial.
- `NOTA`: o cliente aprova o serviço, e a aprovação é um dos elos que atrasam a entrega.

- `NOTA-R`: o dono decide o fornecedor (ver 2.4).

Síntese: Aparecem três regras, todas ainda a confirmar: quem pesquisa preço de peças, quem decide o fornecedor e que o cliente aprova o serviço.

- Regras de orçamento, aprovação, prazo e garantia: Informação não mencionada nas fontes.

### 3.7 Hipóteses de melhoria

**Citações**
- `NOTA` (H2): uma ferramenta que sugira causas prováveis a partir dos sintomas. Parcialmente validada.
- `E2` (mecânico 4): "Confiaria na ferramenta pois cada modelo carro tem suas peculiaridades."
- `E1`: uma ferramenta de apoio ao diagnóstico ajudaria a mão de obra nova.
- `NOTA`: um agente de triagem/intake mais estruturado no primeiro contato com o cliente.
- `NOTA` (H3): integração com os ERPs de fornecedores. Ainda não validada tecnicamente.
- `E2` (mecânico 5): interface por áudio.
- `E3` (cliente 3): o cliente ficaria mais tranquilo com um registro detalhado do que foi feito, de preferência com fotos, inclusive dos itens que foram verificados e estavam bons. Também quer lembretes do que não foi feito desta vez mas importa para a próxima.
- `E3` (cliente 3 e 5): o cliente não pediu etapa nem estimativa de data como forma de acompanhar o serviço.

Síntese: As melhorias levantadas são apoio ao diagnóstico, triagem inicial, integração com fornecedores e voz para o mecânico.

🔍 Precisa de descoberta: reclamações de clientes sobre status e prazo, e um teste de compreensão da triagem inicial. Quem pode trazer: atendente/recepção das oficinas. Quem pode responder: pedir o dado ao cliente ou teste barato (`cheap-test-from-hypothesis`).

### 3.8 Processo ou ferramenta legada e acervo a replicar

**Citações**
- `E2` (mecânico 1): "No começo [...] havia um checklist." Hoje não existe mais.
- `NOTA`: o processo atual usa WhatsApp, ligações e papel.

- `NOTA-R`: nas oficinas que ele visitou, não há formulário, planilha ou mensagem padrão para cotação e orçamento.

Síntese: Existiu um checklist de diagnóstico no passado, mas ele não foi fornecido. Não há acervo de cotação ou orçamento a replicar.

- Manual, FAQ, telas ou templates de outras áreas: Informação não mencionada nas fontes.
- O que replicar do processo atual e o que é decisão nova: Informação não mencionada nas fontes.

### 3.9 Entidades-chave e campos

Informação não mencionada nas fontes.

### 3.10 Requisitos não-funcionais

**Citações**
- `E2` (mecânico 5): a ferramenta não pode exigir muito detalhe nem ser pouco prática. Por áudio, "economizaria muito mais tempo".

Síntese: O único requisito citado é praticidade, com entrada por voz.

- Performance: Informação não mencionada nas fontes.
- Disponibilidade (SLA): Informação não mencionada nas fontes.
- Capacidade e volume: Informação não mencionada nas fontes.
- Acessibilidade: Informação não mencionada nas fontes.
- Auditoria: Informação não mencionada nas fontes.
- Retenção de dados: Informação não mencionada nas fontes.
- Segurança e criptografia: Informação não mencionada nas fontes.
- Fuso horário: Informação não mencionada nas fontes.

---

## Pendências e dúvidas

1. Dos clientes que passam pela oficina, quantos cobram o status do serviço? (nenhum, poucos, a maioria) (3.2)

As outras lacunas não podem ser fechadas antes do prazo e seguem para a EF Macro como hipóteses a testar.

Respondidas por você em 30/10/2026: transcrição da Oficina A (não existe), respostas do dono/gerente da Oficina B (só em bloco de notas, não enviadas), ponto focal (o grupo da FIAP), plataforma (celular e computador), peso da espera por peças (impressão), quem decide o fornecedor (o dono; na Oficina B o gerente pesquisa e o dono decide), formulários de cotação (não há), sistema usado (A sem sistema, B com CRUD sem internet), tempo gasto com cobranças de clientes (não será perguntado) e entrevistas da recepção e do cliente final (não cabem no prazo).

### Descobertas em aberto

- 3.2: tempo parado por etapa (diagnóstico, peça, aprovação) e taxa de erro na informação inicial. Quem pode trazer: dono/gerente da Oficina A ou da Oficina B. Quem pode responder: pedir o dado ao cliente; sem o dado, teste barato (`cheap-test-from-hypothesis`).
- 3.3: série histórica do tempo médio de entrega e do tempo de cotação de peças, com quem mede. Quem pode trazer: dono/gerente da Oficina A ou da Oficina B. Quem pode responder: pedir o dado ao cliente.
- 3.7: reclamações de clientes sobre status e prazo, e teste de compreensão da triagem inicial. Quem pode trazer: atendente/recepção das oficinas. Quem pode responder: pedir o dado ao cliente ou teste barato (`cheap-test-from-hypothesis`).
