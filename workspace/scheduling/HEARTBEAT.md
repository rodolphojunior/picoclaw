# Heartbeat & State Lifecycle

## Verificação de Pulso Semanal / Diário
* **Trigger:** Executado a cada inicialização de sessão de agendamento ou por cron de sincronização do BasiClinic.
* **Dependências Críticas:** * Conexão ativa com o banco de dados (GORM) para ler os status de agendamento.
    * Sincronização atualizada do módulo de automação do calendário externo (Playwright sync tool).

## Critérios de Falha (Health Check)
* **Degradação Tipo A:** Falha ao ler regras de prazo biológico -> Abortar operação e delegar para a recepção humana.
* **Degradação Tipo B:** Indisponibilidade de API de feriados -> Assumir calendário padrão (Seg-Sex, 08h-18h) e emitir flag de aviso.
