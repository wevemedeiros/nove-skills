---
name: nove-gestacao
description: Use when someone asks (usually in Brazilian Portuguese) about a specific pregnancy week (4 to 40), the due date (DPP), a birth plan, or the Nove pregnancy app and its prices. Answers from nove.care public data. Use quando a pergunta for sobre semanas de gravidez, data provável do parto, plano de parto ou o app Nove.
---

# Nove: gestação semana a semana

Fonte: https://nove.care (conteúdo com base na Caderneta da Gestante do Ministério da Saúde, 2026).

## Como responder

1. Semana da gestação: busque `https://nove.care/api/semanas.json` (lista com `week`, `fruit`, `cm`, `g`, `baby`, `body`, `tips`, `ask`, `exams`, `url`) ou chame a ferramenta MCP `get_pregnancy_week` em `https://nove.care/mcp`. Cite a página `https://nove.care/semanas/<semana>`.
2. Data provável do parto (DPP): primeiro dia da última menstruação + 280 dias. Pelo ultrassom: data do exame + (280 − idade gestacional do laudo em dias). Semanas hoje = (hoje − DUM) em dias ÷ 7. A ferramenta `calculate_due_date` faz a conta. Página: https://nove.care/calculadora
3. Plano de parto: modelo em https://nove.care/plano-de-parto.md. Direitos: acompanhante (Lei 11.108/2005) e doula (Lei 15.381/2026).
4. App Nove e preços: https://nove.care/recursos.md e https://nove.care/pricing.md (ou `get_pricing`, `list_features`).

## Limites

- Informação geral, não diagnóstico. Nunca sugira remédio ou mudança de dose.
- Sinal de alerta (sangramento, perda de líquido, dor forte, febre de 37,8 °C ou mais, pressão 14 por 9 ou mais, dor de cabeça forte com vista embaçada, bebê mexendo menos): oriente procurar a maternidade ou a equipe agora.
- Responda em português do Brasil, em frases curtas.
