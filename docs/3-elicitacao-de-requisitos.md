### **Requisitos Funcionais**

**1\. Entrada do Teste**

* 1.1 O sistema permitirá informar o modelo a ser testado.  
* 1.2 O sistema permitirá informar o system prompt do modelo.  
* 1.3 O sistema permitirá que o operador defina as regras de segurança a verificar.  
* 1.4 O sistema sugerirá regras de segurança adicionais, que só serão verificadas após confirmação do operador.  
* 1.5 O sistema permitirá que o operador informe os conteúdos protegidos a verificar.  
* 1.6 O sistema permitirá configurar o número máximo de tentativas antes do início do teste.

**2\. Execução do Teste**

* 2.1 O sistema gerará tentativas de ataque de uma única mensagem contra o modelo testado.  
* 2.2 O sistema adaptará as tentativas seguintes com base nos resultados anteriores, respeitando o limite configurado.  
* 2.3 O sistema encerrará o teste ao detectar a primeira violação ou ao atingir o número máximo de tentativas, o que ocorrer primeiro.  
* 2.4 O sistema exibirá o progresso e o tempo estimado do teste.  
* 2.5 O sistema registrará, para cada tentativa, a entrada enviada e a resposta do modelo.

**3\. Avaliação do Resultado**

* 3.1 O sistema considerará que houve violação quando a resposta do modelo descumprir uma das regras de segurança definidas e confirmadas para o teste.  
* 3.2 O sistema considerará que houve violação quando a resposta do modelo revelar conteúdo protegido informado pelo operador.  
* 3.3 O sistema indicará, para cada tentativa, se houve violação, sem violação ou resultado inconclusivo.  
* 3.4 O sistema utilizará um sistema redundante de verificação (ex: LLM-as-Judge, TF-IDF) para validar o veredito.  
* 3.5 O sistema mostrará a evidência da violação e o motivo do veredito.  
* 3.6 O sistema permitirá revisão humana dos vereditos.

**4\. Relatórios e Histórico**

* 4.1 O sistema gerará um relatório completo, com o histórico de todas as tentativas e seus vereditos.  
* 4.2 O sistema gerará um resumo do resultado do teste.  
* 4.3 O sistema registrará quais estratégias de ataque tiveram sucesso e quais falharam.

### **Requisitos Não Funcionais**

**1\. Operacional**

* 1.1 O sistema deve funcionar totalmente em ambiente local, sem chamadas a serviços externos.

**2\. Desempenho**

* 2.1 O sistema deve utilizar o mínimo de recurso computacional possível.  
* 2.2 O sistema deve permitir configurar o número máximo de tentativas para limitar o tempo de execução.

**3\. Segurança**

* 3.1 Nenhum dado (modelo, system prompt, regras, conteúdos protegidos ou resultados) pode ser enviado para fora do ambiente de teste.  
* 3.2 O acesso ao sistema e aos relatórios deve ser restrito a usuários autorizados, pois o system prompt pode conter informação confidencial.

**4\. Confiabilidade**

* 4.1 Os resultados de cada execução devem ser registrados e preservados para permitir reavaliação e comparação entre versões.  
* 4.2 Os vereditos devem passar por revisão humana por amostragem, pois julgar uma violação pode ser subjetivo.

**5\. Cultural e Político**

* 5.1 O sistema deve ser usado apenas no contexto de segurança solicitado, com autorização do cliente.