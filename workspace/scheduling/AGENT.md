# Agent Execution Protocol

## Fluxo de Processamento de Agendamento

### Passo 1: Análise de Dados e Limitação de Fronteira (Memory & Soul)
1. Carregar as variáveis de estado do paciente via `memory/MEMORY.md`.
2. Validar a janela biológica (`prazo_biologico_minimo_dias`). Calcular: $DataMinima = DataAtual + PrazoBiologico$.

### Passo 2: Casamento de Agendas (Matchmaking)
1. Consultar a API de calendário do **BasiClinic** para buscar a disponibilidade do `dentista_id` e do `paciente_id` a partir da $DataMinima$.
2. Filtrar e descartar finais de semana, feriados nacionais/locais e horários fora da jornada comercial da clínica.

### Passo 3: Filtro de Equilíbrio Financeiro
1. Aplicar a regra dos 5% descrita no `SOUL.md`:
   $$\left| \frac{TotalServicos - TotalPago}{TotalServicos} \right| \le 0.05$$
2. Se o desvio for maior que 5% negativo (inadimplência parcial além da margem), o agente deve emitir um alerta interno no payload e priorizar horários que coincidam com dias de plantão financeiro ou gerar um aviso discreto de "Necessário alinhamento na recepção".

### Passo 4: Geração de Output
1. Consolidar as 3 opções ordenadas.
2. Formatar a saída estritamente conforme o padrão visual limpo definido no `USER.md`.
