# Nove: skills oficiais

Skills oficiais da [Nove](https://nove.care), o app de gestação em português, para assistentes de IA (Claude, ChatGPT, Cursor e outros).

| Skill | O que faz |
| --- | --- |
| [`nove-gestacao`](skills/nove-gestacao/SKILL.md) | Gestação semana a semana (4 a 40), data provável do parto, plano de parto e o app Nove (recursos e preços), com os dados públicos do nove.care. |
| [`nove-dpp`](skills/nove-dpp/SKILL.md) | Data provável do parto pela DUM ou pelo ultrassom, semanas de hoje e trimestre. |
| [`nove-enxoval`](skills/nove-enxoval/SKILL.md) | Enxoval de bebê sob medida para a DPP e o clima da cidade, com quantidades por tamanho. |
| [`nove-api`](skills/nove-api/SKILL.md) | Para desenvolvedores: integrar a Nove API, o SDK `nove-care`, a CLI `nove` e o servidor MCP. |

## Instalar

```bash
npx skills add wevemedeiros/nove-skills
```

## Fontes e limites

- Conteúdo com base na Caderneta da Gestante do Ministério da Saúde (2026).
- Informação geral, não diagnóstico. Em sinal de alerta, oriente procurar a maternidade.
- API, MCP e markdown do nove.care: https://nove.care/developers
- Servidor MCP no registro oficial: `care.nove/nove` (https://nove.care/mcp)

Contato: contato@nove.care
