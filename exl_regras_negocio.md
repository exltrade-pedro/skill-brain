---
name: exl_regras_negocio
description: Regras completas de negócio da EXL Trade — produtos, preços, planos, avaliação, funded, licenças, resets, saques, estados e fluxos operacionais. Consultar e atualizar a cada sessão.
type: reference
---

# EXL Trade — Regras de Negócio Completas

Fonte de verdade para produtos, regras, fluxos e operação da EXL Trade Mesa Proprietária.
Atualizado: abr/2026. Etapas diagnóstico 1–6 concluídas.

---

## PRODUTOS E PREÇOS

### Planos de Avaliação (vendidos)
| Plano   | Preço Avaliação | Preço Reset |
|---------|----------------|-------------|
| Elite   | R$ 1.578       | R$ 589      |
| Pro     | R$ 2.578       | R$ 959      |
| Hedge   | R$ 3.978       | R$ 1.789    |
| Master  | R$ 5.978       | R$ 2.259    |

- Resets: ilimitados dentro de 30 dias da compra, por conta
- Planos funded: NÃO são vendidos — concedidos após aprovação, sem preço

### Classificação Financeira
| Item | Classificação |
|------|--------------|
| Venda de plano de avaliação | RECEITA EXL |
| Venda de reset | RECEITA EXL |
| Profit split (20% EXL / 80% trader) | RECEITA EXL |
| Profitchart ONE — primeiros 30 dias | CUSTO EXL (não repassa ao trader) |
| Profitchart ONE — após 30 dias | PASS-THROUGH (trader paga EXL → EXL repassa Nelogica) |
| Profitchart PRO — todos os dias | PASS-THROUGH (trader paga EXL → EXL repassa Nelogica) |

---

## MODELO DE CONTAS (CRÍTICO)

- Um trader (CPF) pode ter **MÚLTIPLAS contas simultâneas**
- Limite: uma conta por CPF por **conta master cadastrada**
- Cada conta é **COMPLETAMENTE INDEPENDENTE**:
  - Avaliação, licença, estado, reset, janela de 30 dias — tudo por conta
  - Uma conta resetada não afeta outra conta do mesmo CPF
  - Uma conta aprovada não aprova as demais
- **O estado é da CONTA, não do trader/CPF**
- Profit split: 20% EXL / 80% trader — todos os planos

---

## REGRAS DA AVALIAÇÃO (por conta)

- Meta de lucro: varia por plano
- Dias mínimos operados: mesmo número para todos os planos
- Limite de perda diária: bloqueia operações no dia, libera no dia seguinte — **NÃO elimina**
- Limite de perda total: **elimina a conta imediatamente**
- Regra de consistência: maior dia de lucro ≤ 35% da meta
- Violação de consistência: **elimina a conta**
- **Sem prazo de avaliação** — trader tenta até eliminar ou aprovar
- Reset: zera risco e parâmetros na mesma conta/licença, disponível por 30 dias da compra

---

## REGRAS DO FUNDED (por conta)

- Entra no simulador remunerado primeiro (não em conta real)
- Dias mínimos operados: número diferente da avaliação, igual para todos os planos aprovados
- Sem meta de lucro — acumula livremente
- Lucro mínimo para saque: varia por plano
- Regra de consistência: maior dia ≤ 35% do total acumulado na conta
- Limite de saque simulador: igual à margem do plano contratado
- Limite de saque conta real: sem limite
- **REGRA CONFIRMADA 07/04/2026:** 2 saques aprovados (status="approved" em withdrawals) = migração para conta real (funded). Regra formal, não mais subjetiva.
- **RESOLVIDO 07/04/2026:** regra formal, 2 saques aprovados = conta real. Não mais subjetivo.
- Trader continua pagando licença no funded (pass-through)

---

## REGRAS DE LICENÇA (por conta)

- Uma licença por conta — se trader tem 2 contas, paga 2 licenças
- Licença vencida sem renovação = **cancelamento imediato da licença E da conta**
- Sistema envia e-mail automático: 7 dias antes, 3 dias antes, no dia do vencimento
- Paulo envia WhatsApp manual de cobrança
- Renovação: trader paga via PIX pelo link (e-mail ou WhatsApp)
- Se dentro de 30 dias sem renovar: Paulo oferece reset
- Se fora de 30 dias sem renovar: Paulo cancela e informa sobre nova avaliação

---

## ESTADOS POR CONTA (máquina de estados)

```
COMPRA CONFIRMADA
        ↓
  EM ATIVAÇÃO (aguardando corretora — até 72h)
        ↓
  EM AVALIAÇÃO ←─────────────────────────────┐
   ↙          ↘                              │
perda total  meta + dias                  reset
consistência + consistência             executado
violada      + Paulo aprova                  │
   ↓               ↓                        │
REPROVADA     FUNDED SIMULADOR               │
COM RESET ────────────────────────────────── ┘
   ↓ 30 dias passaram
REPROVADA
SEM RESET
   ↓
CANCELADA ←── licença vence sem renovar (qualquer estado)
   ↓
Nova compra = nova conta do zero (independente)
```

- Conta reprovada: trader mantém acesso ao dashboard, histórico visível no admin e painel
- "Reprovada com reset" = reprovada + dentro de 30 dias da compra
- Nova avaliação após cancelamento: nova conta completamente independente
- Sem estado de suspensão

---

## FLUXO 1 — Nova Avaliação (por conta)

1. Paulo vê venda no Guru Manager
2. Paulo envia WhatsApp de boas-vindas (manual)
3. Paulo cria licença no admin EXL — status: aguardando liberação
4. Sistema envia licenças à corretora por e-mail em lote às 17h (criadas após 17h → lote do dia seguinte)
5. Corretora libera e confirma por e-mail (até 72h)
6. Paulo clica "liberação confirmada" no admin
7. Paulo acessa Profitchart → conta aparece sem perfil de risco
8. Paulo aloca perfil de risco correspondente ao plano
9. Conta ativa — trader pode operar

**Gargalo:** corretora (até 72h) + lote das 17h. Futuro: EXL criará licença por conta própria.
**Profitchart é sistema separado — sem integração — etapas 7-8 sempre manuais.**

---

## FLUXO 2 — Reset (por conta)

1. Trader solicita reset (WhatsApp / botão em construção)
2. Sistema valida: dentro de 30 dias da compra? conta não eliminada por perda total?
3a. SE elegível: Paulo vai ao Profitchart → "zerar margem total" → confirma ao trader
3b. SE não elegível: sistema informa motivo sem precisar de Paulo

---

## FLUXO 3 — Aprovação (por conta)

1. Trader solicita análise (WhatsApp / botão em construção)
2. Paulo analisa no Profitchart: meta, dias, consistência
3. Paulo aprova ou rejeita no admin com motivo estruturado
4a. SE rejeitado: trader informado com motivo — continua em avaliação
4b. SE aprovado: Paulo informa trader → admin gera certificado → Paulo vai ao Profitchart → zera margem → altera perfil para "plano + aprovado" → trader reinicia no simulador remunerado

**Motivos de rejeição (lista fechada):**
- Atingiu limite de perda total
- Está fora da regra de consistência
- Não renovou a licença

---

## FLUXO 4 — Saque (por conta)

1. Trader acessa painel → preenche solicitação de saque (KYC incompleto bloqueia upstream, antes de chegar ao admin)
2. Admin EXL mostra checklist pré-calculado dos critérios
3. Paulo analisa e aprova ou rejeita com motivo estruturado
4a. SE rejeitado: e-mail automático com motivo + trader reabre nova solicitação
4b. SE aprovado: **Paulo executa PIX ou TED pelo banco da EXL** (sempre humano)

**Motivos de rejeição (lista fechada):**
- Dias mínimos não cumpridos
- Lucro mínimo do plano não atingido
- Regra de consistência violada (maior dia > 35% do total acumulado)

**Aprovação e pagamento de saque: SEMPRE supervisão humana (Paulo)**

---

## FLUXO 5 — Renovação/Cancelamento de Licença (por conta)

1. Sistema envia e-mail automático (7d, 3d, no dia do vencimento)
2. Paulo envia WhatsApp com link de renovação
3a. SE renova: trader paga via PIX → EXL repassa → licença renovada
3b. SE não renova: dentro de 30 dias → Paulo oferece reset; fora dos 30 dias → Paulo cancela + informa nova avaliação

---

## PESSOAS E SISTEMAS

| Pessoa/Sistema | Função |
|---|---|
| Paulo | Toda a operação: ativação, reset, aprovação, saque, licença, Profitchart, PIX |
| Roger | Somente comercial — nenhuma operação |
| Guru Manager | Gateway de pagamento e vendas — fonte de verdade de vendas |
| Admin EXL | Licenças, aprovações, saques, resets, estados |
| Profitchart (subcontas) | Criação, perfil de risco, zeragem, monitoramento — MANUAL, sem integração |
| Corretora CM Capital | Libera licença — gargalo externo (será eliminado em breve) |
| WhatsApp | Comunicação com trader — manual, não rastreado (intencional) |
| E-mail | Notificações automáticas do sistema |

---

## GAPS CRÍTICOS

1. Toda operação depende de Paulo — inoperante sem ele
2. Eliminação de conta não gera alerta — Paulo só sabe olhando Profitchart
3. Aprovação depende do trader perceber e avisar — EXL não identifica proativamente
4. Corretora é gargalo de 72h sem SLA rastreado (temporário — será eliminado)
5. Certificado de aprovação gerado fora do sistema — sem padrão, sem registro
6. Distinção avaliação vs funded = apenas nome de perfil no Profitchart — frágil
7. Sem visão consolidada de contas por estado
8. Reclamações de traders vão apenas para WhatsApp
9. Regulamento diz "2 saques = conta real" — prática é subjetiva (risco jurídico)
10. Validação de elegibilidade de reset é manual na cabeça de Paulo
11. Monitoramento diário = Paulo olhando Profitchart — sem cobertura fora do horário

---

## SUPERVISÃO HUMANA OBRIGATÓRIA

- Aprovação final de saque + pagamento PIX/TED → Paulo sempre
- Migração simulador → conta real → Paulo sempre (decisão subjetiva)
- Sistema pode pré-validar critérios — Paulo confirma a decisão final

---

## PLANO DE AÇÃO

### FASE 1 — Quick Wins (2–3 semanas)
1. Dashboard de operação: contas por estado, licenças a vencer, saques pendentes
2. Checklist de ativação por conta no admin (etapas sequenciais com status)
3. Campo de estado da conta visível e atualizável no admin
4. Tela de análise de saque com checklist automático dos 3 critérios
5. Campo de prazo de ativação (data_compra + 72h) com alerta visual
6. Geração automática de certificado ao aprovar conta

### FASE 2 — Estrutura Operacional (1–2 meses)
7. Botão de reset na área do trader com validação automática de elegibilidade
8. Botão de solicitação de aprovação na área do trader
9. Tela de análise de aprovação no admin com dados lado a lado
10. Motivos estruturados de rejeição como seleção (não texto livre)
11. Registro de cada reset como evento (data, número, conta)
12. Fila de renovações de licença no admin

### FASE 3 — Banco de Dados (paralelo à Fase 2)
Ver project_diagnostico_db.md para plano completo de migrations.

### FASE 4 — Automação (somente após Fases 1, 2 e 3 validadas)
Nenhum item de automação antes da operação manual estar estruturada.

---

## CHECKLIST DE PRONTIDÃO PARA AUTOMAÇÃO

- [ ] Paulo vê estado de todas as contas em uma tela
- [ ] Nenhuma ativação fica em limbo sem sinalização
- [ ] Todo reset registrado como evento com data e número
- [ ] Toda aprovação registrada com parâmetros no momento da decisão
- [ ] Todo saque com motivo estruturado de aprovação/rejeição
- [ ] Certificado gerado pelo sistema ao aprovar
- [ ] Estado da conta consistente entre admin e banco
- [ ] Critérios de migração simulador → conta real documentados no sistema
- [ ] Elegibilidade de reset validada pelo sistema
