---
name: project_regulamento_exl
description: Regulamento completo EXL Trade para clientes — planos, regras, saques, ativos, custos, consistência, conta remunerada (lido do código-fonte em 10/04/2026)
type: project
---
# Regulamento EXL Trade — Referência Oficial para Clientes

> Fonte: `SITE-DASHBOARD-TRADER/app/regulamento/page.tsx`
> Lido em: 10/04/2026
> Atualizar quando o arquivo fonte for alterado.

---

## 1. Membro EXL

Todo plano contratado inclui automaticamente o status **Membro EXL** com acesso a:

- Comunidade seleta de traders profissionais
- Conteúdo educacional atualizado constantemente
- Mentorias exclusivas com traders experientes
- Psicólogo de Performance
- EXL Trading Hub (app exclusivo)
- Sala ao vivo com operações em tempo real
- Saque diário disponível na Conta Real Definitiva
- Tecnologia e plataformas profissionais

---

## 2. Conta Exame (Avaliação)

- Mínimo **3 dias** operados
- Atingir a **meta de lucro** do plano contratado
- **Sem limite de tempo** para completar a avaliação
- Resets ilimitados nos primeiros **30 dias** da contratação
- Não há pagamento de lucros durante a fase de avaliação

---

## 3. Planos e Regras de Risco

| Plano | Margem | Contratos | Meta Lucro | Stop Diário | Perda Máxima |
|---|---|---|---|---|---|
| Elite | R$7.500 | 70 | R$6.000 | R$3.000 | R$7.500 |
| Pro | R$14.000 | 130 | R$11.000 | R$5.000 | R$14.000 |
| Hedge | R$20.000 | 190 | R$15.000 | R$8.000 | R$20.000 |
| Master | R$30.000 | 290 | R$21.000 | R$12.000 | R$30.000 |

### Stop Diário
- **NÃO elimina** o trader
- Pausa as operações apenas no dia atingido
- Reinicia automaticamente no dia seguinte (valor fixo do plano)
- Lucro do mesmo dia se soma ao stop como colchão adicional
- Exemplo Elite: Se lucrou R$500 no dia → stop do dia = R$3.500

### Perda Máxima (Margem)
- **ELIMINA** o trader se atingida
- Equivale à margem do plano contratado
- Lucros acumulados expandem o limite de forma crescente
- **Fórmula:** `Limite Atual = Perda Máxima + Lucro Acumulado`
- Exemplo Elite: Lucro acumulado R$2.500 → pode perder até R$10.000 antes de ser eliminado

### Comparativo Stop Diário vs Perda Máxima

| Característica | Stop Diário | Perda Máxima |
|---|---|---|
| Elimina o trader? | Não | Sim |
| Reinicia? | Todo dia | Nunca |
| Acumula com lucro? | Só no mesmo dia | Sempre (permanente) |
| Consequência | Pausa até amanhã | Desqualificação da conta |

---

## 4. Regra de Consistência (35%)

O maior dia de lucro não pode ultrapassar **35% do lucro total acumulado**.

- **No Exame:** descumprir = **eliminação da conta**
- **Na Conta Remunerada:** descumprir = deve adequar operação (não elimina)

**Exemplo:**
- Lucro total acumulado: R$10.000
- Melhor dia máximo permitido: R$3.500 (35%)
- Se melhor dia foi R$4.000 → regra violada
- Se melhor dia foi R$3.000 → regra cumprida

---

## 5. Conta Remunerada (Simulador Remunerado)

Ambiente após aprovação na Conta Exame onde o trader opera com **capital real da EXL Trade**.

### Como funciona
- Sem meta de lucro
- **80% dos lucros** para o trader
- Regra de consistência (35%) continua valendo
- Mínimo **7 dias operados** para solicitar saque

### Diferença Conta Exame vs Conta Remunerada

| Característica | Conta Exame | Conta Remunerada |
|---|---|---|
| Objetivo | Avaliação | Operação Real |
| Lucros | Não pagos | 80% para o trader |
| Dias mínimos | 3 dias | 7 dias (para saque) |
| Meta de lucro | Obrigatória | Não há |
| Saques | Não permitido | A cada 14 dias |

### Progressão na Conta Remunerada

**Fase 1 — SR (Simulação Remunerada):**
- Teto de saque = margem do plano contratado
- Exemplo Elite: máximo R$7.500 por saque, mesmo lucrando mais

**Fase 2 — Conta Real Definitiva:**
- Ativada após **2 saques concluídos** na fase SR
- Sem teto para saques
- Saques diários disponíveis

---

## 6. Saques e Pagamentos

### Periodicidade
- Solicitação a cada **14 dias de operação** (Nacionais e FX)
- Processamento: até **48h** após aprovação
- Pagamento: dias **5 e 20** de cada mês

### Onde solicitar
Dashboard do Trader: `exltrade.com.br/dashboard` → seção **Pagamentos**

### Valores Mínimos de Saque

| Plano | Margem | Mínimo de Saque |
|---|---|---|
| Elite | R$7.500 | R$1.500 |
| Pro | R$14.000 | R$2.800 |
| Hedge | R$20.000 | R$4.000 |
| Master | R$30.000 | R$6.000 |

### Política de Pagamentos
- Trader Padrão: **80%** dos lucros
- Membro EXL: **80%** dos lucros

---

## 7. Ativos Disponíveis

### Planos Nacionais (B3)
- **Mini Índice (WIN):** Futuro do Ibovespa
  - Variação: 5 em 5 pontos
  - Valor: R$0,20 por ponto por contrato
  - Horário: 09h00 às 17h55 (pré-abertura 08h45)

- **Mini Dólar (WDO):** Futuro USD/BRL
  - Tick mínimo: R$5,00 por contrato
  - Variação: 0,5 em 0,5 ponto
  - Horário: 09h00 às 17h55 (pré-abertura 08h45)

### Planos FX (Forex)
**Pares principais:** EUR/USD, GBP/USD, USD/JPY, AUD/USD, USD/CAD

**Pares exóticos:** USD/BRL, EUR/GBP, EUR/JPY, GBP/JPY e outros

**Horário:** 24h — abre domingo 17h, fecha sexta 17h (horário de Brasília)

---

## 8. Custos Operacionais

| Ativo | Custo |
|---|---|
| Mini Dólar (WDO) | R$1,75 por contrato |
| Mini Índice (WIN) | R$0,50 por contrato |
| FX (Forex) | U$2,50 por lote |

- Cobrado por operação completa (entrada + saída)
- Descontado automaticamente do resultado

---

## 9. Plataformas de Negociação

| Plataforma | Preço | Período Grátis |
|---|---|---|
| Black Arrow ONE / ProfitChart | R$99,90/mês | 30 dias grátis |
| Black Arrow PRO | R$210,00/mês | Sem período grátis |

- Cobrada mensalmente na data de contratação
- Responsabilidade do trader manter assinaturas ativas
- EXL Trade não se responsabiliza por interrupções por falta de pagamento

---

## 10. Plano de Escala

Permite aumentar margem e contratos após atingir consistência.

| Nível | Margem | Contratos |
|---|---|---|
| 25% | +25% | +25% |
| 50% | +50% | +50% |
| 75% | +75% | +100% |

**Exemplo Elite com escala 75%:**
- Margem: R$7.500 × 1,75 = R$13.125
- Contratos: 70 × 2 = 140

---

## 11. Reset de Contas

- Recomeça a avaliação por **fração do valor** de uma nova conta
- Disponível durante os **primeiros 30 dias** da contratação
- Valores disponíveis via Loja no dashboard
- Sem limite de resets no período dos 30 dias

---

## 12. Sistema de Pontos EXL Coin

*(Seção presente no regulamento — detalhes operacionais via dashboard)*

---

## 13. Compromisso Institucional EXL Trade

- Regras claras e sem ambiguidades
- Comunicação proativa sobre mudanças
- Relatórios completos de performance
- Auditoria independente regular
- Suporte especializado disponível
- Educação contínua atualizada
- Comunidade ativa e colaborativa
- Tecnologia e ferramentas profissionais

---

## Resumo das Regras Críticas

| Regra | Fase Exame | Fase Remunerada |
|---|---|---|
| Stop Diário atingido | Pausa o dia (não elimina) | Pausa o dia (não elimina) |
| Perda Máxima atingida | Elimina a conta | Elimina a conta |
| Consistência 35% violada | Elimina a conta | Deve adequar (não elimina) |
| Sem dias mínimos | Não pode solicitar aprovação | Não pode solicitar saque |

**Why:** Documento de referência para evitar inconsistências entre o que o sistema valida e o que o regulamento diz. Qualquer feature que toque em regras de negócio (reset, saque, consistência, eliminação) deve ser verificada contra este documento.

**How to apply:** Antes de implementar lógica de reset, saque, avaliação ou eliminação — checar este documento. Quando Paulo perguntar sobre regras, usar este como fonte primária.
