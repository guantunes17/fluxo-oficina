# Lente da release r1-mvp — FluxoOficina

- **EF Macro:** `docs/demandas/d1-fluxooficina/ef-macro.md`, versão 0.8
- **Brief da release:** sem brief da release
- **Data:** 2026-11-17
- **Recorte:** aberto: acompanha o must-have da §2

## Entra nesta release

| Item | IDs na EF Macro |
|---|---|
| Entrada por voz do mecânico, no app mobile | RF-01, RN-04, §7.1 passo 3, §7.2 fluxo 1 |
| Cotação de peças com fornecedores, no painel web | RF-02, RN-01, RN-02, RN-05, §7.1 passos 4 e 5, §7.2 fluxos 2 e 4 |
| Status do serviço por etapa, no painel web e no app | RF-03, RN-03, RN-07, §7.1 passos 6 e 7, §7.2 fluxo 3 |
| Aviso de status ao cliente final por WhatsApp | RF-04, RN-06, §7.1 passo 8 |
| Cadastro de fornecedores, no painel web | RF-05 |
| Abertura da ordem de serviço pela recepção, no painel web | RF-06, §7.1 passo 1 |
| Notificação push ao mecânico, no app | RF-07, §7.1 passos 1 e 5 |

## Fica fora desta release

| Item | IDs na EF Macro | Destino |
|---|---|---|
| Sugestão de causas prováveis a partir dos sintomas | §2 should-have | sem release definida |
| Triagem estruturada do cliente no primeiro contato | §2 should-have | sem release definida |
| Registro do serviço com fotos, enviado ao cliente por WhatsApp | §2 should-have | sem release definida |

## Personas

- Mecânico, no app mobile, com notificação push
- Dono, no painel web
- Gerente, no painel web
- Atendente/recepção, no painel web
- Cliente final, só por WhatsApp

## Pendências herdadas da EF Macro

| ID | Pendência | Trava |
|---|---|---|
| P-06 | O cliente aprova o orçamento antes de a peça ser comprada? | RN-03, RF-03 |
| P-07 | O cliente final aceita receber aviso de etapa por WhatsApp? | RF-04, RN-06 |
| P-08 | O áudio funciona com o barulho do serviço, no celular do mecânico? | RF-01 |
| P-12 | Metas de tempo e critério de aceite de cada função | RF-01, RF-02, RF-03, RF-04, RF-05, RF-06, RF-07 |
| P-29 | Quem atribui a ordem a um mecânico | RF-03 |
| P-30 | Outros eventos que geram notificação ao mecânico | RF-07 |
| P-26 | Tamanho máximo e tempo de envio do áudio | RF-01 |
| P-28 | Login do mecânico e distribuição do app | RF-01, RF-03 |
