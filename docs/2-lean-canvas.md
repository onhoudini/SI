# Lean Canvas — Avaliação de Segurança de Modelos de Linguagem Locais

| Público-alvo | Elaborado por | Data | Versão |
|---|---|---|---|
| Pesquisadores que avaliam modelos de linguagem locais (SLMs e LLMs) | Gabriel Rodrigues da Rocha | 27/10/2026 | 3.0 |

| **Problema** | **Solução** | **Proposta de Valor Única** | **Vantagem Injusta** | **Segmentos de Usuários** |
|---|---|---|---|---|
| - Modelos de linguagem podem violar regras de segurança ou revelar conteúdo protegido.<br>- Pesquisadores precisam de um método para avaliar modelos locais mantendo os dados no ambiente local. | - Avaliar modelos locais e os *system prompts* definidos para o teste.<br>- Permitir que o pesquisador informe os modelos, o *system prompt*, os ataques (de turno único ou multi-turno) e as repetições.<br>- Executar os ataques contra o modelo e avaliar as respostas, com veredito validado por verificação redundante.<br>- Permitir que o pesquisador configure os critérios de parada e os limites de execução.<br>- Gerar registros e relatórios das avaliações. | Pipeline configurável para pesquisadores executarem seus próprios ataques contra modelos de linguagem locais (SLMs ou LLMs) e avaliarem se eles se comportam de forma segura ou insegura nas condições testadas, mantendo modelos e dados localmente. | Interface altamente intuitiva e fácil de usar, pensada para que iniciantes possam realizar testes de segurança de modelos locais. | Pesquisadores que avaliam a segurança de modelos de linguagem locais (SLMs e LLMs). |

| **Alternativas Existentes** | **Métricas-Chave** | **Canais** | **Usuários Iniciais** |
|---|---|---|---|
| - PyRIT (Microsoft)<br>- Promptfoo<br>- Garak | - Violações identificadas nas tentativas executadas.<br>- Tentativas até a primeira violação, quando houver.<br>- Ataques que funcionaram e que falharam, registrados. | Publicação e disponibilização da ferramenta para uso por outros pesquisadores, que poderão utilizá-la e publicar trabalhos com base nela. | Pesquisadores que precisam avaliar a segurança de SLMs ou LLMs executados localmente. |