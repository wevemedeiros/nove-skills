---
name: nove-api
description: Use when a developer wants to integrate the Nove API (nove.care) into code, an agent or a terminal, through the REST API, the nove-care JavaScript/TypeScript SDK, the nove CLI or the Nove MCP server. Covers auth (optional OAuth 2.0 client credentials), rate limits, errors, pagination, async jobs and the sandbox. Use quando alguém quiser integrar a Nove API, o SDK, a CLI ou o MCP da Nove.
---

# Nove API: integrar a Nove em código e agentes

Documentação: https://nove.care/developers · OpenAPI: https://nove.care/openapi.json · llms.txt: https://nove.care/llms.txt

## Escolha o caminho

| Precisa de | Use |
| --- | --- |
| Chamar de JavaScript ou TypeScript | SDK `npm install nove-care` (https://nove.care/developers/sdk) |
| Terminal ou script shell | CLI `npx nove-care semana 20` ou `brew install wevemedeiros/nove/nove` (https://nove.care/developers/cli) |
| Assistente de IA (Claude, ChatGPT, Cursor) | MCP remoto `https://nove.care/mcp` ou `npx -y nove-mcp` (https://nove.care/developers/mcp) |
| Qualquer linguagem | REST em `https://nove.care/api/v1` |
| Testar sem efeitos | Sandbox `https://sandbox.nove.care/v1` (mesmos endpoints) |

## Endpoints (base `https://nove.care/api/v1`)

- `GET /semanas/{4-40}`: bebê, corpo, dicas, perguntas e exames da semana.
- `GET /semanas?limit=&cursor=`: lista paginada por cursor (`next_cursor`).
- `GET /dpp?dum=AAAA-MM-DD` (ou `us_data`, `us_semanas`, `us_dias`, ou `dpp`): data provável do parto e idade gestacional.
- `GET /buscar?q=`: busca no conteúdo do nove.care.
- `GET /precos`, `GET /recursos`: planos e recursos do app.
- `POST /enxoval` (escopo `enxoval:write`): job assíncrono, responde 202 com `Location: /jobs/{id}`; faça polling em `GET /jobs/{id}` até `status` ser `succeeded` ou `failed`. Envie `Idempotency-Key` para repetir com segurança.

## Autenticação e limites

- Sem token: 60 pedidos por minuto por IP.
- Com token: 600 por minuto. Registre um cliente em `POST /oauth/register` (RFC 7591, corpo pode ser vazio) e troque por token em `POST /oauth/token` com `grant_type=client_credentials`. Metadados: `/.well-known/oauth-authorization-server`.
- Cabeçalhos `RateLimit` e `RateLimit-Policy`; em 429, respeite `Retry-After`.
- Erros em `application/problem+json` (RFC 9457) com `code` estável, por exemplo `invalid_week`, `missing_date`, `rate_limited`.

## Exemplo (SDK)

```js
import { Nove } from 'nove-care';
const nove = new Nove();
const semana = await nove.semana(20);
const lista = await nove.enxoval({ due_date: '2027-03-10', mode: 'minimalista', city: 'Curitiba' });
```

## Limites de conteúdo

Informação geral, não diagnóstico. Não use a API para sugerir remédio ou dose. Em sinal de alerta, oriente procurar a maternidade.
