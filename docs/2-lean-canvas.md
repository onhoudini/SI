# Lean Canvas — Avaliação de Segurança de Modelos de Linguagem Locais

| Público-alvo | Elaborado por | Data | Versão |
|---|---|---|---|
| Pesquisadores que avaliam modelos de linguagem locais (SLMs e LLMs) | Gabriel Rodrigues da Rocha | 20/10/2026 | 2.0 |

| **Problema** | **Solução** | **Proposta de Valor Única** | **Vantagem Injusta** | **Segmentos de Usuários** |
|---|---|---|---|---|
| - Modelos de linguagem podem violar regras de segurança ou revelar conteúdo protegido.<br>- Pesquisadores precisam de um método para avaliar modelos locais mantendo os dados no ambiente local. | - Avaliar modelos locais e os *system prompts* definidos para o teste.<br>- Simular tentativas de violar regras ou revelar conteúdo protegido.<br>- Permitir que o pesquisador defina regras, conteúdos protegidos e critérios de parada.<br>- Adaptar tentativas conforme os resultados e gerar registros e relatórios das avaliações. | Método adaptável para pesquisadores avaliarem se modelos de linguagem locais (SLMs ou LLMs) se comportam de forma segura ou insegura nas condições testadas, mantendo modelos e dados localmente. | Interface altamente intuitiva e fácil de usar, pensada para que iniciantes possam realizar testes de segurança de modelos locais. | Pesquisadores que avaliam a segurança de modelos de linguagem locais (SLMs e LLMs). |

| **Alternativas Existentes** | **Métricas-Chave** | **Canais** | **Usuários Iniciais** |
|---|---|---|---|
| - PyRIT (Microsoft)<br>- Promptfoo<br>- Garak | - Violações identificadas por regra de segurança avaliada.<br>- Tentativas até a primeira violação, quando houver.<br>- Estratégias de teste registradas. | Publicação e disponibilização da ferramenta para uso por outros pesquisadores, que poderão utilizá-la e publicar trabalhos com base nela. | Pesquisadores que precisam avaliar a segurança de SLMs ou LLMs executados localmente. |
