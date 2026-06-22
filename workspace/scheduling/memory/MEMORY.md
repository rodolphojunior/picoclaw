# Agent Contextual Memory

## Contexto de Sessão Ativa (Exemplo de Estado Volátil)
* **Último Paciente Consultado:** `Nenhum` (Aguardando chamada do pipeline)
* **Última Regra Biológica Aplicada:** `Nenhuma`
* **Estado da Última Proposta:** `Aguardando_Input`

## Logs de Cache e Decisões Recentes
* *Aqui o agente guardará de forma efêmera o array das 3 últimas datas geradas para o paciente atual, evitando re-processamento caro caso o paciente atualize a página do PWA antes de tomar a decisão final.*
