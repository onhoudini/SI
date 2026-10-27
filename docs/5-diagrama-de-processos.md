# Diagrama de Processos

## Objetivo

Este diagrama representa o processo de avaliação local de segurança de um modelo de linguagem (SLM ou LLM), desde a configuração pelo pesquisador até a revisão do relatório.

## Diagrama de atividades

O diagrama é uma representação em fluxograma de um diagrama de atividades. Cada atividade indica o responsável: **Pesquisador**, **Sistema** ou **Modelo alvo**. Os ataques podem ser de turno único ou multi-turno, e a execução termina quando um critério de parada configurado é atingido.

```mermaid
flowchart TD
    INICIO([Início]) --> CONFIG["Pesquisador: informar modelos, system prompt, ataques e repetições"]
    CONFIG --> PARADA["Pesquisador: configurar critérios de parada e limites"]
    PARADA --> VALIDAR["Sistema: validar configuração"]
    VALIDAR --> VALIDA{"Configuração válida?"}
    VALIDA -->|Não| CORRIGIR["Pesquisador: corrigir dados obrigatórios"]
    CORRIGIR --> VALIDAR
    VALIDA -->|Sim| INICIAR["Pesquisador: iniciar avaliação"]
    INICIAR --> HISTORICO["Sistema: inicializar execução e histórico"]
    HISTORICO --> ENVIAR["Sistema: enviar ataque ao modelo alvo"]
    ENVIAR --> RESPOSTA["Modelo alvo: gerar resposta"]
    RESPOSTA --> TURNOS{"Ataque multi-turno com mensagens restantes?"}
    TURNOS -->|Sim| PROXIMA["Sistema: enviar próxima mensagem da sequência"]
    PROXIMA --> RESPOSTA
    TURNOS -->|Não| AVALIAR["Sistema: avaliar resposta e validar veredito com verificação redundante"]
    AVALIAR --> REGISTRAR["Sistema: registrar ataque, resposta, veredito e evidência"]
    REGISTRAR --> CRITERIO{"Algum critério de parada foi atingido?"}
    CRITERIO -->|Não| ENVIAR
    CRITERIO -->|Sim| FINALIZAR["Sistema: registrar estado final da execução"]
    FINALIZAR --> RELATORIO["Sistema: gerar resumo e relatório do histórico"]
    RELATORIO --> REVISAR["Pesquisador: consultar evidências e revisar vereditos por amostragem"]
    REVISAR --> FIM([Fim])

    classDef pesquisador fill:#dbeafe,stroke:#1d4ed8,color:#0f172a
    classDef sistema fill:#dcfce7,stroke:#15803d,color:#0f172a
    classDef modelo fill:#fef3c7,stroke:#b45309,color:#0f172a
    class CONFIG,PARADA,CORRIGIR,INICIAR,REVISAR pesquisador
    class VALIDAR,HISTORICO,ENVIAR,PROXIMA,AVALIAR,REGISTRAR,FINALIZAR,RELATORIO sistema
    class RESPOSTA modelo
```

**Legenda:** azul = atividades do Pesquisador; verde = atividades do Sistema; amarelo = atividade do Modelo alvo.

## Relação com os casos de uso

| Etapa do processo | Caso de uso relacionado |
|---|---|
| Configuração de modelos, *system prompt*, ataques, repetições e critérios de parada | UC-01 — Configurar avaliação |
| Envio dos ataques, avaliação e registro das tentativas | UC-02 — Executar avaliação |
| Consulta do relatório e revisão dos vereditos | UC-03 — Revisar resultado |