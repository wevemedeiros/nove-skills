---
name: nove-enxoval
description: Use when someone asks (usually in Brazilian Portuguese) what to buy for a baby's layette (enxoval), how many pieces of each size, or how to adapt the list to the city's climate in the baby's first months. Builds the list from the Nove API (nove.care). Use quando a pergunta for sobre enxoval de bebê, lista de enxoval, quantidade de roupas por tamanho ou enxoval para frio ou calor.
---

# Nove: enxoval de bebê sob medida

Fonte: https://nove.care/enxoval e a Nove API (https://nove.care/developers).

## Como montar a lista

1. Pergunte a data provável do parto (DPP) e a cidade. Se ela não souber a DPP, calcule pela skill `nove-dpp`.
2. Peça a lista à API:
   - `POST https://nove.care/api/v1/enxoval` com JSON `{"due_date":"AAAA-MM-DD","mode":"completo"|"minimalista","city":"Cidade"}` (ou `"region":"quente"|"ameno"|"frio"` sem cidade).
   - A resposta é 202 com `Location: /api/v1/jobs/{id}`. Consulte `GET https://nove.care/api/v1/jobs/{id}` a cada 1 a 2 segundos até `status` ser `succeeded`.
   - Ou chame `npx nove-care enxoval --dpp AAAA-MM-DD --cidade "Cidade"`.
3. O resultado traz `windows` (tamanho RN, P, M e G, com os meses e o clima médio de cada fase), `categories` com itens, quantidades e tamanhos, e `warnings`.
4. Apresente por categoria, com as quantidades, e explique por que o clima mudou a lista (por exemplo, mais macacão de malha grossa se o tamanho P cair no inverno).

## Regras

- Modo minimalista: só o essencial, para quem quer gastar pouco ou ganhar no chá de bebê.
- Não recomende fórmula infantil, mamadeira, bico ou chupeta (Lei 11.265/2006). Se perguntarem, diga que é decisão para conversar com a pediatra.
- Lista do chá de bebê compartilhável: app Nove (https://nove.care/recursos).
- Responda em português do Brasil, em frases curtas.
