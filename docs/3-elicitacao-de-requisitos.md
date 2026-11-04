# Elicitação de Requisitos

## 1. Requisitos Funcionais

### 1.1. Configuração da Avaliação

**RF01.** O sistema deve permitir selecionar os modelos de linguagem locais (SLMs ou LLMs) que serão avaliados, sem exigir adaptações nos modelos.

**RF02.** O sistema deve permitir definir um ou mais *system prompts* para a avaliação, incluindo a possibilidade de executar testes sem *system prompt*.

**RF03.** O sistema deve permitir configurar os parâmetros de execução dos modelos. As configurações selecionadas serão compartilhadas e aplicadas igualmente a todos os modelos da avaliação.

**RF04.** O sistema deve disponibilizar uma coleção predefinida de ataques de *prompt injection*, organizada por tipos de estratégias, permitindo sua ampliação.

**RF05.** O sistema deve permitir adicionar ataques personalizados, definidos pelo pesquisador em um formato estruturado, como JSON, e armazená-los para reutilização em avaliações futuras.

**RF06.** O sistema deve permitir utilizar ataques de turno único ou multi-turno. Para ataques multi-turno, deve ser possível fornecer uma sequência de mensagens, preservando o contexto da conversa durante sua execução.

**RF07.** O sistema deve permitir configurar o número de repetições de cada ataque.

**RF08.** Todos os modelos selecionados devem ser avaliados utilizando o mesmo conjunto de *system prompts*, configurações e ataques, permitindo comparações equivalentes.

### 1.2. Execução da Avaliação

**RF09.** O sistema deve calcular a quantidade total de chamadas necessárias para a avaliação com base nos parâmetros configurados:

$$
N = M \times S \times C \times A \times R
$$

Onde:

- \(N\): quantidade total de chamadas;
- \(M\): quantidade de modelos;
- \(S\): quantidade de condições de *system prompt* avaliadas;
- \(C\): quantidade de configurações;
- \(A\): quantidade de ataques;
- \(R\): quantidade de repetições por ataque.

A quantidade de condições de *system prompt* considera também a condição sem *system prompt*, quando selecionada.

**RF10.** O sistema deve executar os ataques configurados contra os modelos selecionados, respeitando as combinações e quantidades definidas na avaliação.

**RF11.** O sistema deve executar uma avaliação por vez, sem permitir avaliações simultâneas.

**RF12.** A execução deve ser encerrada somente após a conclusão da quantidade de chamadas planejada, sem interrupção antecipada em função da identificação de uma violação.

**RF13.** O sistema deve registrar, para cada chamada, o ataque utilizado, a entrada enviada e a resposta recebida do modelo.

### 1.3. Avaliação dos Resultados

**RF14.** O sistema deve utilizar pelo menos dois métodos de verificação para avaliar se houve violação.

**RF15.** O sistema deve utilizar um método de verificação principal, considerado o mais confiável, e um método complementar para auxiliar na avaliação dos resultados.

**RF16.** O sistema deve apresentar o veredito de cada tentativa (execução completa de um ataque) e as evidências correspondentes, incluindo a entrada enviada e a resposta recebida.

**RF17.** O sistema deve permitir que o pesquisador revise manualmente qualquer tentativa, utilizando o histórico e as evidências registradas.

**RF18.** A avaliação humana deve poder considerar os resultados dos métodos de verificação, especialmente nos casos em que não houver conclusões suficientemente claras.

### 1.4. Relatórios e Histórico

**RF19.** O sistema deve manter um histórico das chamadas realizadas, incluindo suas respectivas configurações, entradas, respostas e resultados das verificações.

**RF20.** O sistema deve disponibilizar o histórico das tentativas em formato CSV, permitindo sua análise e revisão manual.

**RF21.** O sistema deve gerar relatórios contendo o histórico das tentativas e um resumo dos resultados obtidos.

**RF22.** O sistema deve apresentar quais ataques foram bem-sucedidos e malsucedidos, permitindo analisar os resultados por modelo, *system prompt* e tipo de ataque.

---

## 2. Requisitos Não Funcionais

### 2.1. Operacional

**RNF01.** O sistema deve funcionar integralmente em ambiente local, sem depender de chamadas a serviços externos.

### 2.2. Desempenho

**RNF02.** O sistema deve considerar as limitações de processamento do ambiente local, uma vez que a execução de modelos de linguagem pode exigir recursos computacionais significativos e apresentar tempos elevados.

### 2.3. Segurança

**RNF03.** Nenhum dado relacionado à avaliação, incluindo modelos, *system prompts*, ataques, respostas, relatórios e resultados, pode ser enviado para fora do ambiente local.


### 2.4. Confiabilidade

**RNF04.** Os resultados e as configurações de cada avaliação devem ser registrados e preservados, permitindo rastrear as condições em que os experimentos foram realizados.

**RNF05.** O sistema deve preservar as evidências necessárias para a revisão dos resultados, considerando que os métodos automáticos de verificação podem apresentar divergências ou conclusões inconclusivas.

### 2.5. Usabilidade

**RNF06.** A interface deve ser intuitiva e facilitar a instalação, configuração e execução das avaliações.

**RNF07.** A definição de ataques personalizados deve utilizar um formato estruturado e de fácil edição, como JSON, facilitando sua criação, organização, armazenamento e reutilização.

### 2.6. Manutenibilidade e Extensibilidade

**RNF08.** A coleção de ataques disponibilizada pelo sistema deve permitir ampliação e manutenção, possibilitando a inclusão de novas estratégias de *prompt injection*.

---

## 3. Restrições de Uso

**RE01.** A ferramenta possui natureza ofensiva e deve ser utilizada exclusivamente em avaliações autorizadas.