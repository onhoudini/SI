# Lean Canvas — Avaliação de Segurança de Modelos de Linguagem Locais

| Público-alvo | Elaborado por | Data | Versão |
|---|---|---|---|
| Pesquisadores que avaliam modelos de linguagem locais (SLMs e LLMs) | Gabriel Rodrigues da Rocha | 27/10/2026 | 3.0 |

| **Problema** | **Solução** | **Proposta de Valor Única** | **Vantagem Injusta** | **Segmentos de Usuários** |
|---|---|---|---|---|
| - Modelos de linguagem podem violar regras de segurança ou revelar informações protegidas.<br>- Pesquisadores precisam de métodos sistemáticos para avaliar a segurança desses modelos.<br>- A realização de avaliações exige organização, rastreabilidade e reprodutibilidade dos experimentos, mantendo os dados em ambiente local. | - Plataforma configurável para avaliação de modelos de linguagem locais.<br>- Utilização de ataques predefinidos ou personalizados, de turno único ou multi-turno.<br>- Execução de avaliações com diferentes modelos, *system prompts* e configurações.<br>- Verificação das respostas, registro das evidências e geração de relatórios. | Permitir que pesquisadores avaliem, comparem e investiguem sistematicamente a segurança de modelos de linguagem locais, utilizando seus próprios ataques e configurações, sem expor modelos e dados a serviços externos. | Interface intuitiva, simples de instalar, configurar e executar. | Pesquisadores que desenvolvem estudos sobre segurança, vulnerabilidades e comportamento de modelos de linguagem (SLMs e LLMs), especialmente aqueles que trabalham com modelos executados localmente. |

| **Alternativas Existentes** | **Métricas-Chave** | **Canais** | **Usuários Iniciais** |
|---|---|---|---|
| - PyRIT (Microsoft)<br>- Promptfoo<br>- Garak | - Quantidade de avaliações executadas.<br>- Quantidade de tentativas realizadas.<br>- Taxa de violações identificadas.<br>- Quantidade de ataques bem-sucedidos e malsucedidos.<br>- Violações identificadas por modelo e tipo de ataque. | - Publicação e disponibilização do código-fonte e da ferramenta em repositório público.<br>- Divulgação em eventos e publicações acadêmicas.<br>- Compartilhamento com grupos e comunidades de pesquisa em inteligência artificial e segurança. | Pesquisadores que já trabalham com modelos de linguagem locais e precisam avaliar seu comportamento diante de ataques, comparar modelos ou investigar vulnerabilidades de segurança. |