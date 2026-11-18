# Comparação EF Macro × protótipo exploratório — FluxoOficina

- **EF Macro:** `docs/demandas/d1-fluxooficina/ef-macro.md`, versão 0.8 (Rascunho). Os achados da rodada 1 entraram na versão 0.5, a decisão de plataforma (app mobile e painel desktop) na 0.6, os achados da rodada 2 na 0.7 e o design system próprio na 0.8, entre 17 e 18/11/2026
- **Recorte:** primeira release r1-mvp: RF-01 a RF-07 (Must-have da §2, [lente](../releases/r1-mvp/ef-macro-r1-mvp.md)) · RFs fora do recorte: 0. Fora também: 3 itens do Should-have, que não têm RF numerado
- **Protótipo:** `docs/demandas/d1-fluxooficina/prototipo-exploratorio/` (fonte local `Main.dc.html`, a mesma que está publicada no canvas) · canvas: https://claude.ai/artifact/E9LmMjG7nRcsMWTzEn7P7j
- **Lista fechada de componentes, painel web:** DS próprio FluxoOficina (`@fluxo-oficina/web`, https://github.com/guantunes17/fluxo-oficina-ds), 34 componentes baseados no shadcn/ui
- **Lista fechada de componentes, app do mecânico:** DS próprio FluxoOficina (`@fluxo-oficina/native`), 31 componentes (Tooltip, HoverCard e Kbd só no web), com alvo de toque de pelo menos 44 pontos
- **Revisão de UI/UX (rodada 6):** `Main.dc.html` ganhou foco visível, modal de cancelamento com `role=dialog` e Esc, `role=status`/`alert` nas mensagens, grupo de opções com `radiogroup`, saída em todo fim de fluxo (telas 2 e 5) e botão Voltar nas telas 3 a 5, estados vazios, estado "Transcrevendo", erro por campo com máscara de telefone e placa, desfazer ao remover peça, escolha de outro fornecedor na tela 4 e "Cancelar serviço" como ação destrutiva separada. As notas de pesquisa viraram "Nota do protótipo" recolhida. **Perguntas para a EF:** (a) prazo de espera antes de cobrar o fornecedor (já P aberta); (b) o desfazer da peça removida vale também no app real? (c) a recepção usa o painel em tablet? A EF não define o requisito (RNFs `[A DEFINIR]`)
- **Tokens e componentes novos no protótipo (rodada 5):** `estilo.css` e `Main.dc.html` ganharam os tokens `-soft`, `-surface` e `-solid-foreground` das famílias, `chart-*`, `sidebar-*`, `font-mono` e os 13 papéis de tipografia (títulos, rótulo, corpo compacto, selo e placa). Os componentes novos do DS entraram onde a EF já pede o dado: barra de progresso da etapa (`Etapa N de 5`) nas telas M3, M4 e 07, avatar do mecânico responsável no painel (tela 06) e ponto de situação com texto na resposta do fornecedor (tela 04). **Prioridade da ordem e chave de aviso (Switch) não entraram:** a EF Macro não pede nenhum dos dois, e o protótipo só mostra o que ela pede
- **Tokens semânticos no protótipo (rodada 4):** o canvas passou a usar também `surface`, `surface-raised`, `surface-sunken`, `overlay`, `foreground-subtle`, `primary-hover`, `primary-active`, `neutral` e `highlight`. O selo da superfície (App mobile, Painel web) usa `highlight`, e o selo "Protótipo exploratório" usa `neutral`.
- **Aplicação do DS no protótipo (rodada 3):** o canvas usa os tokens do `fluxo-oficina-ds` (azul-petróleo, âmbar, neutro frio, estados, Inter) em `estilo.css` e `Main.dc.html`. Os elementos (botão, cartão, tabela, campo, alerta, selo) seguem o desenho dos componentes do DS em HTML estilizado, e não são os componentes React. O Claude Design monta o canvas em HTML, sem importar pacotes npm
- **Retorno:** 0 conversas resolvidas de 0 (nenhum comentário no canvas até esta rodada)
- **Rodada:** 2, em 2026-11-17, depois da decisão de plataforma. Na rodada 1 o protótipo era uma tela web única; agora o mecânico tem o frame de celular (390 × 844) e os outros quatro perfis têm o frame de computador (1280 × 800). A rodada 1 seguiu até a versão 4 do canvas (versão 3 com as respostas da pessoa, versão 4 com os quadros). A versão 6 traz as duas superfícies. Protótipo regerado no mesmo dia com as respostas da pessoa às pendências (versão 3 do canvas). Versão 4 acrescentou a visão de quadros: um quadro por tela, lado a lado, como no Figma
- **Revisada pela pessoa:** rodada 1, Gustavo Antunes em 2026-11-17 (8 linhas). rodada 2, Gustavo Antunes em 2026-11-17 (linhas 1.5 e 2.5, com o veredito que ele escolheu)

## Sentido dos vereditos

Cada veredito tem um sentido só, do ponto de vista da EF Macro, nas duas tabelas. É o mesmo sentido do modo achados da `ef-macro-from-brief`.

| Veredito | O que acontece | Tabela onde aparece |
|---|---|---|
| manter | A EF fica como está. O protótipo muda na próxima rodada: ganha a tela que falta ou perde o que a EF não pede | As duas |
| incluir | Entra na EF como RF, RN, permissão ou fluxo | No protótipo e ausente na EF |
| remover | Sai da EF e vai para §2 "NÃO faremos" | Na EF e ausente no protótipo |
| adiar | Fica na EF e sai do recorte da release: a lente o leva para "Fica fora desta release" | Na EF e ausente no protótipo |
| pendência | Pergunta ao cliente; vira `P-NN` na §13 | As duas |

## 1. Na EF e ausente no protótipo

| # | Seção da EF | O que a EF pede | O que o protótipo mostra | Veredito | Nota |
|---|---|---|---|---|---|
| 1 | §5 RF-01, campo "data de entrada" | A tela de conferência traz a data de entrada da ordem de serviço | A tela 2 mostra placa, modelo e sintoma, sem data de entrada | manter | Aplicado na versão 3 do protótipo: a tela 2 mostra a data de entrada |
| 2 | §5 RF-01 e §6 RN-04 | O mecânico confere a lista "com poucos toques", sem digitação nem muito detalhe | A tela 2 corrige a peça em campo de texto e a quantidade em campo numérico | manter | Aplicado na versão 3: quantidade por botões de mais e menos, e peça regravada ou adicionada por voz |
| 3 | §7.1 passo 1 | A recepção abre a ordem de serviço quando o cliente deixa o carro | Nenhuma tela abre a OS. A OS 1042 já existe | incluir | Resposta da pessoa em 2026-11-17: a recepção abre a OS e isso entra na v1. O protótipo ganhou a tela 11 "Abrir ordem de serviço" |
| 4 | §6 RN-03 e §7.1 passo 6 | O cliente aprova o serviço antes da execução | "Aprovação do cliente" é só uma etapa do painel. Nada registra a aprovação | incluir | Resposta da pessoa em 2026-11-17: o atendente muda a etapa depois que o cliente confirma. Entra na EF como regra do RN-03. P-06 segue aberta para a regra de orçamento |
| 5 | §9 "Notificação push no celular" | O app pode avisar o mecânico, por exemplo, de cotação respondida (Sugestão, não decidido) | O app não mostrava nenhuma notificação | incluir | Resposta da pessoa em 2026-11-17: o push entra na primeira release. Entrou na EF como RF-07 (versão 0.7). Aplicado no protótipo: a lista de ordens do app mostra a notificação |

## 2. No protótipo e ausente na EF

| # | Tela do protótipo | O que o protótipo mostra | Seção da EF que deveria tratar | Veredito | Nota |
|---|---|---|---|---|---|
| 1 | 8. Histórico de avisos | Tela própria com a lista de avisos enviados, para o dono e a recepção | §3, Matriz de Permissões | incluir | Resposta da pessoa em 2026-11-17: dono, gerente e recepção veem o histórico. O RF-04 já cita o histórico, mas a matriz não. Aplicado na versão 3: o gerente ganhou a tela 8 |
| 2 | 7. Mudar etapa da OS | Botão "Cancelar serviço" com confirmação, disponível aos quatro perfis internos | §3 e §7.2 "Desistência ou cancelamento" | incluir | Resposta da pessoa em 2026-11-17: só dono e gerente cancelam. Entra na matriz da §3. Aplicado na versão 3 |
| 3 | 5. Escolher fornecedor | Depois da escolha, a tela manda a oficina fechar o pedido por fora | §5 RF-02 e §7.1 passo 5 | incluir | Resposta da pessoa em 2026-11-17: o agente avisa o fornecedor escolhido por WhatsApp, sem compra nem pagamento. Entra no RF-02 e no fluxo 7.1 passo 5. Aplicado na versão 3 |
| 4 | 3. Pedir cotação | O gerente marca a quais fornecedores o pedido vai | §5 RF-02 | incluir | Resposta da pessoa em 2026-11-17: o agente filtra pela categoria da peça e o gerente ou o dono ajusta. Entra no RF-02, usando a categoria do RF-05. Aplicado na versão 3 |
| 5 | M3. Minhas ordens de serviço | O app lista as ordens em aberto do mecânico, sem dizer de qual mecânico | §4.2 (Ordem de Serviço) e §5 RF-03 | incluir | Resposta da pessoa em 2026-11-17: o mecânico vê só as ordens atribuídas a ele. A ordem passa a ter mecânico responsável (RF-03 e §4.2, versão 0.7). Quem atribui ficou como pendência na EF. Aplicado no protótipo: o app lista só as ordens dele, e a abertura da ordem no painel tem o campo Mecânico responsável |

## Contagem

- Tabela 1: 5 linhas (manter 2, incluir 3).
- Tabela 2: 5 linhas (incluir 5).
- Total: 10 linhas (manter 2, incluir 8, pendência 0). As 8 primeiras entraram na EF Macro nas versões 0.5 e 0.6, e as linhas 1.5 e 2.5 na versão 0.7. Todas têm o aval da pessoa.

## Achados para revisar na EF Macro

Os achados das rodadas 1 e 2 já foram aplicados na EF Macro (versões 0.5, 0.6 e 0.7). Sobra só o que a pessoa deixou como pendência, já registrado na §13:

- §13 — quem atribui a ordem a um mecânico e em que momento (P-29, comparação 2.5).
- §13 — que outros eventos geram notificação ao mecânico, além da ordem atribuída e da cotação respondida (P-30, comparação 1.5).
