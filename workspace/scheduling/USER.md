# User Interaction Contract

## Contexto de Entrada do Usuário
O agente será acionado em dois cenários principais:
1. **Fim de Consulta:** O dentista finaliza o atendimento atual e solicita que o agente gere propostas de retorno para o paciente.
2. **Interação Direta do Paciente:** O paciente interage via PWA ou Totem para selecionar uma das 3 opções calculadas.

## Estrutura de Payload Esperada (JSON do Sistema)
```json
{
  "paciente_id": 1,
  "staff_id": 2,
  "clinic_id": 1,
  "procedimento_atual": "Restauração em Resina",
  "prazo_biologico_minimo_dias": 14,
  "historico_financeiro": {
    "executed_value": 150000,
    "paid_amount": 145000
  }
}
```

### Tipos de dados
| Campo | Tipo | Exemplo |
|-------|------|---------|
| `paciente_id` | uint | 1 |
| `staff_id` | uint | 2 |
| `clinic_id` | uint | 1 |
| `executed_value` | int64 (centavos) | 150000 (= R$1.500,00) |
| `paid_amount` | int64 (centavos) | 145000 (= R$1.450,00) |
