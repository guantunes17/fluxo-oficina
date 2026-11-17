# Árvore de descoberta — FluxoOficina

Gerada pela exploração enxuta do passo 2 (`ef-macro-from-brief`). Os arquivos de referência da skill não estavam instalados. O formato e os critérios abaixo são os do `SKILL.md`, completados com premissas do analista.

**Critério de confiança usado (premissa):**
- **Alta:** pelo menos duas fontes convergem e há dado por trás (pesquisa, analytics ou amostra real).
- **Média:** duas fontes ou mais convergem, mas sem dado por trás.
- **Baixa:** uma fonte só, ou ideia sem fonte.

Nenhuma hipótese chegou a alta, porque as três linhas `🔍` do brief (3.2, 3.3 e 3.7) seguem sem dado.

**Roteamento usado (premissa):**
- Média entra em must-have só se o ponto focal (o grupo da FIAP) pediu. O recorte validado em 1.3 do brief pede cotação de peças, visibilidade e voz.
- Média fora desse recorte vai para should-have.
- Baixa vai para teste barato ou fica fora.

## Resultado desejado (Sugestão)

Reduzir o tempo em que o serviço fica parado esperando preço e compra de peças, e reduzir as cobranças de status do cliente. A meta numérica segue em aberto.

## OPP-01 — Espera pelo preço das peças para o serviço

Fontes: `E1`, `E2` (coringa 3), `NOTA`. Dado: nenhum (🔍 3.2).

| ID | Solução | Versão mínima testável | Confiança | Destino |
|---|---|---|---|---|
| HIP-01 | Agente de cotação: o dono ou o gerente manda a lista de peças, o agente pede preço aos fornecedores e mostra um comparativo. É a solução pedida pelo grupo. | O gerente manda uma mensagem padrão a 3 fornecedores e anota as respostas numa planilha de comparação. | Média | Must-have |
| HIP-02 | Integração direta com os sistemas (ERPs) e catálogos dos fornecedores, por API ou raspagem de dados. | Listar os fornecedores de uma oficina e checar se algum expõe API. | Baixa | Fora do escopo |
| HIP-03 | Catálogo de preços mantido pelo dono, atualizado por rotina. | Planilha de preços das 20 peças mais pedidas, atualizada toda semana. | Baixa | Fora do escopo (teste barato) |

Confiança: HIP-01 é média porque `E1` e `E2` apontam as peças como gargalo, mas nenhum dado mede o tempo parado. HIP-02 é baixa porque `NOTA` diz que APIs de ERP são raras e `NOTA-R` diz que o sistema da Oficina B não tem internet. HIP-03 é baixa porque só `E1` cita a falta de atualização de preço.

## OPP-02 — Cliente sem visibilidade do andamento

Fontes: `E1` (follow-up constante), `NOTA`. Contra-evidência parcial: `E3` (um cliente, serviço de um dia) não cobrou status, porque o mecânico avisou por WhatsApp. Dado: nenhum (🔍 3.3).

| ID | Solução | Versão mínima testável | Confiança | Destino |
|---|---|---|---|---|
| HIP-04 | Status por etapa do serviço, com aviso ao cliente por mensagem quando a etapa muda. | A recepção manda uma mensagem manual a cada mudança de etapa em 5 serviços. | Média | Must-have |
| HIP-05 | Só uma estimativa de data de entrega, sem etapas. | A recepção informa uma data ao cliente na entrada do carro. | Baixa | Fora do escopo |
| HIP-06 | Agente que responde a cobrança do cliente ("ficou pronto?") por mensagem. | Um modelo de resposta pronto com a etapa atual, enviado pela recepção. | Baixa | Fora do escopo |

Confiança: HIP-04 segue média, com ressalva. `E1` e `NOTA` convergem, e o recorte do grupo inclui visibilidade. O único cliente ouvido (`E3`) não cobrou status, mas falou de um serviço de um dia, sem espera por peça. Se mais clientes de serviço longo confirmarem, a confiança sobe. Se não cobrarem, cai para baixa (P-24). HIP-05 e HIP-06 são baixas porque nenhuma fonte as pede.

## OPP-03 — Informação inicial do cliente errada compromete o diagnóstico

Fontes: `E2` (mecânico 3), `NOTA`. Dado: nenhum, só uma entrevista (🔍 3.2 e 3.7).

| ID | Solução | Versão mínima testável | Confiança | Destino |
|---|---|---|---|---|
| HIP-07 | Triagem estruturada com perguntas padrão ao cliente no primeiro contato, feita por um agente. | A recepção usa 5 perguntas fixas em 10 entradas de carro e compara com o diagnóstico final. | Baixa | Should-have (com teste barato) |
| HIP-08 | Checklist de perguntas feito pela recepção, sem agente. | Uma folha de 5 perguntas na recepção. | Baixa | Fora do escopo |
| HIP-09 | Sugestão de causas prováveis a partir dos sintomas, para o mecânico. É a hipótese H2 do Parcial 01. | O mecânico lê uma lista de causas por modelo para 5 sintomas comuns. | Média | Should-have |
| HIP-10 | Checklist de diagnóstico por modelo de carro. | Um checklist de 10 itens para um modelo comum. | Baixa | Fora do escopo |

Confiança: HIP-07 e HIP-08 são baixas porque a taxa de 50% vem de uma entrevista só. HIP-09 é média porque `E1` e `E2` convergem. O valor maior aparece para mão de obra nova (`E1`, `NOTA`), e fica fora do recorte do grupo.

## OPP-04 — Mecânico não pode digitar no chão da oficina

Fontes: `E2` (mecânico 5), `NOTA` (H4 refutada). Dado: nenhum.

| ID | Solução | Versão mínima testável | Confiança | Destino |
|---|---|---|---|---|
| HIP-11 | Entrada por voz: o mecânico grava um áudio, e o sistema transcreve e estrutura. | O mecânico manda um áudio de WhatsApp e alguém transcreve a lista de peças. | Média | Must-have |
| HIP-12 | Botões de toque com opções prontas, sem digitar. | Um cartão de papel com as opções mais comuns. | Baixa | Fora do escopo |
| HIP-13 | Texto livre no WhatsApp. | Mecânico manda texto. | Baixa | Fora do escopo |

Confiança: HIP-11 é média porque `E2` condiciona o uso a áudio e `NOTA` registra a preferência. É uma entrevista de mecânico só. HIP-13 é baixa porque `E2` rejeita digitação.

## OPP-05 — Cliente não tem registro do que foi feito nem lembrete de revisão

Fontes: `E3` (cliente 3 e 5). Dado: nenhum, um cliente só.

| ID | Solução | Versão mínima testável | Confiança | Destino |
|---|---|---|---|---|
| HIP-14 | Registro do serviço com fotos, enviado ao cliente por WhatsApp no fim do serviço, inclusive dos itens verificados e bons. | O mecânico manda 3 fotos e uma lista curta por WhatsApp ao entregar o carro, em 5 serviços. | Baixa | Should-have (com teste barato) |
| HIP-15 | Lembretes ao cliente dos itens de revisão que ficaram pendentes. | A recepção anota os itens pendentes e manda uma mensagem manual na data combinada. | Baixa | Fora do escopo |
| HIP-16 | Resumo em texto do serviço, sem fotos. | Uma mensagem curta com a lista do que foi feito. | Baixa | Fora do escopo |

Confiança: as três são baixas porque vêm de um cliente só. O registro com fotos não depende de peça e pode ser testado sem construir nada. A Pitz já sugere manutenção futura por quilometragem (Expansión), então lembretes não diferenciam.

## Resumo

- Total: 16 soluções em 5 oportunidades.
- Por destino: must-have 3 (HIP-01, HIP-04, HIP-11), should-have 3 (HIP-07, HIP-09, HIP-14), fora do escopo 10.
- Por confiança: alta 0, média 4 (HIP-01, HIP-04, HIP-09, HIP-11), baixa 12.
