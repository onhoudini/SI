# Elicitação de Requisitos

## Contexto da elicitação

| Item | Descrição |
|---|---|
| Fontes | Solicitação de Sistema (documento 1) e Lean Canvas (documento 2), elaborados por Gabriel Rodrigues da Rocha. |
| Técnica | Análise documental das fontes, com validação das decisões de escopo junto ao patrocinador do projeto. |
| Interessados | Pesquisadores que avaliam a segurança de modelos de linguagem locais (SLMs e LLMs); patrocinador do projeto. |
| Escopo | Plataforma local, aberta e configurável, para avaliar se modelos de linguagem locais (SLMs ou LLMs) violam regras de segurança ou revelam conteúdo protegido nas condições testadas. |

*Nota: neste documento, "tentativa" é uma sequência de uma ou mais mensagens enviadas ao modelo testado, conforme o modo de ataque escolhido pelo pesquisador (turno único ou multi-turno).*

---

## Requisitos Funcionais

### 1. Configuração do Teste

* 1.1 O sistema permitirá informar o modelo de linguagem local (SLM ou LLM) a ser testado, sem exigir adaptações no modelo ou no material avaliado.
* 1.2 O sistema permitirá informar o *system prompt* definido para o teste.
* 1.3 O sistema permitirá que o pesquisador defina as regras de segurança a verificar.
* 1.4 O sistema analisará o *system prompt* e sugerirá regras de segurança adicionais, que só serão verificadas após confirmação do pesquisador.
* 1.5 O sistema permitirá que o pesquisador informe os conteúdos protegidos a verificar.
* 1.6 O sistema permitirá que o pesquisador configure, antes do início do teste, os critérios de parada e os limites de execução, de forma totalmente configurável. Entre os critérios disponíveis:
  * número fixo de tentativas;
  * parar na primeira violação (opção que o pesquisador pode ativar ou desativar);
  * parar após um número definido de violações;
  * tempo máximo de execução.
* 1.7 O sistema permitirá que o pesquisador escolha o modo de ataque (turno único ou multi-turno) e, no modo multi-turno, o número máximo de turnos por tentativa.

### 2. Execução do Teste

* 2.1 O sistema gerará tentativas de ataque contra o modelo testado, em turno único ou multi-turno, conforme o modo escolhido.
* 2.2 O sistema adaptará as tentativas seguintes com base nos resultados anteriores, respeitando os limites configurados.
* 2.3 O sistema encerrará o teste quando qualquer critério de parada configurado for atingido ou quando o pesquisador interromper a execução.
* 2.4 O sistema exibirá o progresso e o tempo estimado do teste.
* 2.5 O sistema registrará, para cada tentativa, as mensagens enviadas (a conversa completa, no modo multi-turno), as respostas do modelo e a estratégia utilizada.
* 2.6 O sistema permitirá repetir uma execução com a mesma configuração, para observar a variabilidade dos resultados.

### 3. Avaliação do Resultado

* 3.1 O sistema considerará que houve violação quando a resposta do modelo descumprir uma das regras de segurança definidas e confirmadas para o teste.
* 3.2 O sistema considerará que houve violação quando a resposta do modelo revelar conteúdo protegido informado pelo pesquisador.
* 3.3 O sistema indicará, para cada tentativa, se houve violação, sem violação ou resultado inconclusivo.
* 3.4 O sistema utilizará um sistema redundante de verificação (ex.: LLM-as-Judge, TF-IDF) para validar o veredito. Quando o avaliador principal e o verificador redundante discordarem, a tentativa será marcada como inconclusiva.
* 3.5 O sistema mostrará, para cada violação, a evidência (entrada enviada e resposta recebida), a regra violada ou o conteúdo protegido revelado e o motivo do veredito.
* 3.6 O sistema permitirá revisão humana dos vereditos, incluindo a seleção de uma amostra de vereditos para revisão.
* 3.7 O sistema registrará, com justificativa e autoria, toda alteração manual de veredito, inclusive a classificação de vereditos inconclusivos.

### 4. Relatórios e Histórico

* 4.1 O sistema gerará um relatório completo, com o histórico de todas as tentativas e seus vereditos.
* 4.2 O sistema gerará um resumo do resultado do teste.
* 4.3 O sistema registrará quais estratégias de ataque tiveram sucesso e quais falharam.
* 4.4 O sistema apresentará as métricas da avaliação: violações identificadas por regra de segurança avaliada, tentativas até a primeira violação (quando houver) e estratégias de teste registradas.
* 4.5 O sistema guardará a configuração completa de cada execução e permitirá exportar o relatório, para apoiar a reprodução e a publicação dos resultados.
* 4.6 O sistema permitirá comparar os resultados de duas ou mais execuções registradas.

---

## Requisitos Não Funcionais

### 1. Operacional

* 1.1 O sistema deve funcionar totalmente em ambiente local, sem chamadas a serviços externos.

### 2. Desempenho

* 2.1 O sistema deve informar o tempo estimado de execução e permitir limitá-lo por meio dos critérios de parada configurados.
* 2.2 O sistema deve operar com a capacidade de processamento disponível no ambiente local, ciente de que o tempo de execução pode ser alto.

### 3. Segurança

* 3.1 Nenhum dado (modelo, *system prompt*, regras, conteúdos protegidos, respostas, relatórios ou resultados) pode ser enviado para fora do ambiente de teste.
* 3.2 O acesso ao sistema e aos relatórios deve ser restrito a usuários autorizados, pois o *system prompt* pode conter informação confidencial.

### 4. Confiabilidade

* 4.1 Os resultados de cada execução devem ser registrados e preservados para permitir reavaliação e comparação entre execuções.
* 4.2 Os vereditos devem passar por revisão humana por amostragem, pois julgar uma violação pode ser subjetivo.

### 5. Usabilidade

* 5.1 A interface deve ser intuitiva e fácil de usar, de modo que pesquisadores iniciantes consigam realizar testes de segurança de modelos locais.
* 5.2 O sistema deve oferecer configuração guiada e valores padrão para os critérios de parada e o modo de ataque.

### 6. Configurabilidade e Extensibilidade

* 6.1 A configuração da avaliação deve ser adaptável às necessidades do pesquisador (regras, conteúdos protegidos, modo de ataque, critérios de parada e limites).
* 6.2 O sistema deve ser aberto à inclusão de novas estratégias de ataque e de novos métodos de verificação.

### 7. Reprodutibilidade e Documentação

* 7.1 O sistema deve manter registros suficientes (configuração, tentativas, vereditos e revisões) para que outros pesquisadores possam reproduzir e publicar avaliações com base na ferramenta.
* 7.2 O sistema deve ser acompanhado de documentação de uso para pesquisadores que o adotarem.

### 8. Cultural e Político

* 8.1 O sistema tem natureza ofensiva e deve ser usado apenas no contexto de segurança solicitado, com autorização do responsável pelo modelo e pelo *system prompt* avaliados.