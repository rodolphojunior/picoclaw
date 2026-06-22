# Agent Skills & Tools Mapping

## Descrição
Este arquivo mapeia as ferramentas técnicas (APIs REST do BasiClinic) que o agente está autorizado a invocar para executar o fluxo descrito no `AGENT.md`.

---

## 1. Ferramentas de Calendário e Agenda

### `fetch_doctor_availability`
* **Descrição:** Busca as janelas de horários livres de um staff (dentista) a partir de uma data.
* **Endpoint:** `GET /api/v1/staff/appointments/availability?staff_id={id}&date_from={data}&clinic_id={id}`
* **Parâmetros:**
  * `staff_id` (uint)
  * `data_inicio` (string, formato YYYY-MM-DD)
  * `clinic_id` (uint)
* **Retorno:** Array de objetos com `date`, `start_time`, `end_time`.
* **Status:** ⚠️ Precisa ser criado no backend do BasiClinic.

---

## 2. Ferramentas Clínicas e Prontuário

### `get_patient_clinical_constraints`
* **Descrição:** Recupera o histórico do último procedimento e calcula a janela biológica de retorno.
* **Endpoint:** `GET /api/v1/staff/patients/{id}/clinical-constraints?clinic_id={id}`
* **Parâmetros:**
  * `paciente_id` (uint)
  * `clinic_id` (uint)
* **Retorno:** `prazo_biologico_minimo_dias` (int), `restricoes_regiao_bucal` (string).
* **Status:** ⚠️ Precisa ser criado no backend do BasiClinic.

---

## 3. Ferramentas Financeiras

### `get_financial_balance`
* **Descrição:** Consulta o módulo financeiro para extrair o balanço de serviços prestados versus pagamentos do paciente.
* **Endpoint:** `GET /api/v1/staff/patients/{id}/financial-balance?clinic_id={id}`
* **Parâmetros:**
  * `paciente_id` (uint)
  * `clinic_id` (uint)
* **Retorno:**
  ```json
  {
    "executed_value": 150000,
    "paid_amount": 145000
  }
  ```
* **Status:** ⚠️ Precisa ser criado no backend do BasiClinic.
