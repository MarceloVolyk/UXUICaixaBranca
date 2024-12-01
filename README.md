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



<h1>ETAPA 3</h1>

Grafo: https://drive.google.com/file/d/1qzjWGttkDvLfFmwmTK4xA282ygWhqSzw/view?usp=sharing

<h2>Cálculo Complexidade Ciclomática:</h2>
V(G): Complexidade Ciclomática
E: Número de Arestas
N: Número de Nós
V(G) = E - N + 2

V(G) = 14 - 12 + 2

V(G) = 4;

<h2>Caminhos possíveis:</h2>
<h3>Caminho 1 (Sucesso na autenticação):</h3>
1 → 2 → 3 → 4 → 5 → 7 → 6 → 8 → 9 → 11 → 12 → 10
<p>Descrição: Segue o fluxo completo sem exceções, encontra o usuário no banco e retorna true</p>

<h3>Caminho 2</h3>
1 → 2 → 3 → 4 → 6 → 8 → 10
<p>Descrição: Falha ao tentar conectar com o banco de dados, caindo no primeiro catch e retornando false</p>

<h3>Caminho 3</h3>
1 → 2 → 3 → 4 → 5 → 7 → 6 → 8 → 10
<p>Descrição: Consegue conectar ao banco, mas falha ao executar a query, caindo no segundo catch e retornando false</p>

<h3>Caminho 4</h3>
1 → 2 → 3 → 4 → 5 → 7 → 6 → 8 → 9 → 11 → 10
<p>Descrição: Executa todo o fluxo com sucesso, mas não encontra o usuário (rs.next() retorna false) e retorna false</p>
