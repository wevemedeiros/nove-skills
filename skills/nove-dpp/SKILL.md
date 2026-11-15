---
name: nove-dpp
description: Use when someone asks (usually in Brazilian Portuguese) to calculate the due date (data provável do parto, DPP), how many weeks pregnant they are today, the trimester, or to convert between the last menstrual period (DUM) and an ultrasound dating. Use quando pedirem para calcular a DPP, quantas semanas de gestação, o trimestre ou a data do parto pela DUM ou pelo ultrassom.
---

# Nove: data provável do parto e idade gestacional

Calculadora: https://nove.care/calculadora · API: `GET https://nove.care/api/v1/dpp`

## Contas

- Pela DUM (primeiro dia da última menstruação): DPP = DUM + 280 dias. Idade gestacional hoje = (hoje − DUM) em dias; semanas = dias ÷ 7 (parte inteira) e o resto são os dias.
- Pelo ultrassom: DPP = data do exame + (280 − idade gestacional do laudo em dias). Se o ultrassom do primeiro trimestre diferir da DUM em mais de 7 dias, a equipe costuma usar o ultrassom; quem decide é ela.
- Trimestres: 1º até 13 semanas e 6 dias, 2º de 14 a 27 semanas e 6 dias, 3º a partir de 28.
- A termo: de 37 semanas a 41 semanas e 6 dias.

## Pela API

- `GET https://nove.care/api/v1/dpp?dum=2026-06-01` → `due_date`, `weeks`, `days`, `trimester`.
- `GET https://nove.care/api/v1/dpp?us_data=2026-08-10&us_semanas=9&us_dias=3`.
- MCP: ferramenta `calculate_due_date` em `https://nove.care/mcp`.
- Terminal: `npx nove-care dpp --dum 2026-06-01`.

Depois da conta, ofereça a página da semana atual: `https://nove.care/semanas/<semana>`.

## Limites

Estimativa, não diagnóstico. Só 4% a 5% dos bebês nascem na DPP exata. Datas e condutas são decididas com a equipe do pré-natal.
