### **Requisitos Funcionais**

**1\. Entrada do Teste**

* 1.1 O sistema permitirá informar os modelos de linguagem locais (SLMs ou LLMs) a serem testados, sem exigir adaptações no material avaliado.
* 1.2 O sistema permitirá informar o *system prompt* definido para o teste.
* 1.3 O sistema permitirá que o pesquisador informe os ataques (prompts) a serem executados, de turno único ou multi-turno.
* 1.4 No caso de ataques multi-turno, o sistema permitirá que o pesquisador informe a sequência de mensagens.
* 1.5 O sistema permitirá informar o número de repetições.
* 1.6 O sistema permitirá que o pesquisador configure os critérios de parada (por exemplo, número fixo de tentativas ou parada na primeira violação) e os limites de execução, de forma totalmente configurável.

**2\. Execução do Teste**

* 2.1 O sistema executará os ataques informados contra o modelo testado e receberá suas respostas.
* 2.2 O sistema encerrará o teste quando um critério de parada configurado for atingido.
* 2.3 O sistema registrará, para cada tentativa, o ataque utilizado e a resposta do modelo.

**3\. Avaliação do Resultado**

* 3.1 O sistema indicará, para cada tentativa, se houve violação.
* 3.2 O sistema utilizará um sistema redundante de verificação para validar o veredito.
* 3.3 O sistema mostrará a evidência da violação (entrada enviada e resposta recebida).
* 3.4 O sistema permitirá revisão humana dos vereditos.

**4\. Relatórios e Histórico**

* 4.1 O sistema gerará um relatório do histórico de tentativas e seus vereditos.
* 4.2 O sistema gerará um resumo do resultado do teste.
* 4.3 O sistema registrará quais ataques funcionaram e quais falharam.

### **Requisitos Não Funcionais**

**1\. Operacional**

* 1.1 O sistema deve funcionar totalmente em ambiente local, sem chamadas a serviços externos.

**2\. Desempenho**

* 2.1 O sistema deve permitir configurar limites de execução, pois o tempo de execução pode ser alto.
* 2.2 O ambiente local deve ter capacidade de processamento suficiente para executar os modelos testados.

**3\. Segurança**

* 3.1 Nenhum dado (modelo, *system prompt*, ataques, respostas, relatórios ou resultados) pode ser enviado para fora do ambiente de teste.
* 3.2 O acesso ao sistema e aos relatórios deve ser restrito a usuários autorizados, pois o *system prompt* pode conter informação confidencial.

**4\. Confiabilidade**

* 4.1 Os resultados de cada execução devem ser registrados e preservados, pois os resultados podem variar entre execuções e os testes precisam ser repetidos.
* 4.2 Os vereditos devem passar por revisão humana por amostragem, pois julgar uma violação pode ser subjetivo.

**5\. Usabilidade**

* 5.1 A interface deve ser intuitiva e fácil de usar, de modo que iniciantes possam realizar testes de segurança de modelos locais.

**6\. Configurabilidade**

* 6.1 A configuração da avaliação deve ser adaptável às necessidades do pesquisador.

**7\. Cultural e Político**

* 7.1 O sistema tem natureza ofensiva e deve ser usado apenas com autorização.