# UXUICaixaBranca

<h1>Erros encontrados:</h1>

<h2>1.Erro na definição do driver do MySQL</h2>
O nome da classe do driver está incorreto. O driver correto para o MySQL é com.mysql.cj.jdbc.Driver, e não com.mysql.Driver.Manager

<h2>2.Uso incorreto de parâmetros na URL de conexão</h2>
A URL de conexão está formatada de forma inadequada. O padrão correto para fornecer credenciais de usuário e senha é através de propriedades de conexão, não diretamente na URL. Além disso, o nome do banco de dados (neste caso, test) deve ser separado por uma barra (/).

<h2>3.Falta de tratamento de exceções</h2>
Os blocos catch estão vazios, o que é uma prática ruim. Isso impede que o desenvolvedor identifique o motivo de falhas em tempo de execução. Ao capturar exceções, deve-se registrar ou exibir uma mensagem de erro.

<h2>4.Concorrência de Strings SQL</h2>
A construção da query dessa forma é vulnerável a ataques de SQL Injection e também pode gerar erros de concatenação ou formatação. A forma correta seria usar PreparedStatement para prevenir esses problemas e melhorar a legibilidade do código.

<h2>5.Falha na verificação de conexão com o banco de dados</h2>
Não há verificação se a conexão foi bem-sucedida antes de tentar executar a consulta SQL. Caso a conexão falhe, o código pode lançar uma exceção em tempo de execução.

<h2>6. Falta de fechamento de recursos (Conexão, Statement, ResultSet)</h2>
Não há fechamento de recursos após a execução da consulta, o que pode causar vazamento de memória e problemas de desempenho. É importante garantir que Connection, Statement e ResultSet sejam fechados após o uso.

<h2>7. Uso inadequado de variáveis globais</h2>
As variáveis nome e result são definidas como membros da classe e estão sendo usadas de maneira global. Isso pode gerar problemas de concorrência e tornar o código menos modular. Elas poderiam ser definidas como variáveis locais no método verificarUsuario.

<h2>8. Erro de nomenclatura (Conformidade com convenções Java)</h2>
Problema: Embora não seja um erro técnico, é uma boa prática nomear classes e métodos de acordo com as convenções do Java. A classe User pode ser mais bem nomeada de acordo com seu contexto (como Usuario ou algo mais específico), e o método verificarUsuario poderia seguir o padrão de nomeação camelCase.