
## Comandos de DML basicos: ⚡️


<details>
  <summary>Basico</summary>
<p></p>

<br>
INSERT: Adiciona novos registros em uma tabela.<p></p>

```sql
INSERT INTO tabela_nome (coluna1, coluna2, coluna3) VALUES (valor1, valor2, valor3);
```
<p></p>
SELECT: Busca dados de uma tabela.<p></p>

```sql
SELECT coluna1, coluna2 FROM tabela_nome WHERE condicao;
```
<p></p>
SELECT DISTINCT: Recupera dados únicos de uma tabela.<p></p>

```sql
SELECT DISTINCT coluna1 FROM tabela_nome;
```
<br>
<p></p>
	
:warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: 
	
**Ao realizar atualizações e exclusões em banco de dados, é fundamental ter extrema atenção, uma vez que o risco de causar danos irreparáveis é muito alto. Em especial, ao executar os comandos sem a utilização da cláusula WHERE, todos os registros na tabela serão afetados. Para preservar a integridade dos dados, é recomendado sempre utilizar transações, que permitem o uso dos comandos `COMMIT` e `ROLLBACK`. Quando se trata de operações em grande escala, a prudência deve ser ainda maior.**

	
<p></p>
UPDATE: Atualiza os dados existentes em uma tabela.<p></p>

```sql
UPDATE tabela_nome SET coluna1 = novo_valor WHERE condicao;
```
A palavra `set` será utilizada para definir a substituição informações na coluna selecionada por uma nova informação.
<p></p>

DELETE: Exclui registros de uma tabela.<p></p>

```sql
DELETE FROM tabela_nome WHERE condicao;
```	

	
<br><br>
<p></p>	
<br>
<details>
<summary>Transações(COMMIT/ROLLBACK)</summary>
<br>
Em banco de dados, uma transação é uma unidade lógica de trabalho que agrupa uma série de operações que devem ser executadas de forma atômica, ou seja, se todas as operações da transação forem bem-sucedidas, as alterações serão confirmadas, caso contrário, serão desfeitas.
<p>

`COMMIT` é um comando utilizado para confirmar as alterações realizadas durante uma transação. A partir do momento em que um COMMIT é executado, as alterações são permanentes e ficam disponíveis para outras transações.

`ROLLBACK` é um comando utilizado para desfazer as alterações realizadas durante uma transação. Se uma transação não for bem-sucedida, o ROLLBACK pode ser executado para desfazer as alterações e restaurar o banco de dados ao seu estado anterior.

Em resumo, a utilização de transações com COMMIT e ROLLBACK ajuda a garantir a integridade dos dados em um banco de dados, permitindo que as operações sejam executadas de forma segura e controlada.
</details>	
	
<br>
</details>
<br>

## Comandos de DML com Tratamentos:✨
<details>
<summary>Intermediário</summary>
<br>
<p></p>
LIKE: Utilizado para buscar valores semelhantes em uma coluna. Por exemplo, para encontrar todos os registros com nomes
que começam com "Jo" a "%" serve para pegar tudo apos aquela informação:<p></p>
	
```sql
SELECT * FROM tabela WHERE nome LIKE 'Jo%';
```
<p></p>
IN: Utilizado para buscar valores específicos em uma coluna. Por exemplo, para encontrar todos os registros com idades
entre 20 e 30:<p></p>
	
```sql
SELECT * FROM tabela WHERE idade IN (20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30);
```
<p></p>
NOT IN: Utilizado para excluir valores específicos em uma coluna. Por exemplo, para encontrar todos os registros com
idades que não estão entre 20 e 30:<p></p>
	
```sql
SELECT * FROM tabela WHERE idade NOT IN (20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30);
```
<p></p>
	
## REGEX
	
<p></p>
REGEXP: Utilizado para buscar valores que correspondem a uma expressão regular específica. Por exemplo, para encontrar
todos os registros com e-mails que terminam com "gmail.com":<p></p>
	
```sql
SELECT * FROM tabela WHERE email REGEXP 'gmail\.com$';
```
NOT REGEXP: Utilizado para excluir valores que correspondem a uma expressão regular específica. Por exemplo, para
encontrar todos os registros com e-mails que não terminam com "gmail.com":<p></p>
	
```sql
SELECT * FROM tabela WHERE email NOT REGEXP 'gmail\.com$';
```
<p></p>
RLIKE: É uma forma alternativa para utilizar o operador REGEXP.<p></p>
	
```sql
SELECT * FROM tabela WHERE email RLIKE 'gmail\.com$';
```
<p></p>
	
```sql
SELECT * FROM tabela WHERE campo REGEXP '^[A-Z]{2}[0-9]{4}[A-Z]{2}$';
```
Esse comando irá selecionar todas as linhas da tabela onde o valor do campo corresponde à expressão regular especificada. A expressão regular usada nesse exemplo é "^[A-Z]{2}[0-9]{4}[A-Z]{2}$", que significa:

"^" indica o início da string
"[A-Z]{2}" significa que há duas letras maiúsculas consecutivas
"[0-9]{4}" significa que há quatro números consecutivos
"[A-Z]{2}" significa que há duas letras maiúsculas consecutivas
"$" indica o final da string
Essa expressão regular corresponde a uma string que começa e termina com duas letras maiúsculas e contém quatro números consecutivos no meio, como "AB1234CD".
<p></p>
	
```sql
SELECT * FROM tabela WHERE campo REGEXP '^([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+\.[a-zA-Z]{2,})$';
```
Esse comando irá selecionar todas as linhas da tabela onde o valor do campo corresponde à expressão regular especificada. A expressão regular usada nesse exemplo é "^([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+.[a-zA-Z]{2,})$", que é uma expressão regular para validação de email.
	
## STRING	
<p></p>
O MySQL possui várias funções de string que podem ser usadas para manipular o conteúdo de colunas. Algumas das funções mais comuns incluem:

* `AS`: é uma palavra reservada no MySQL que permite que você atribua um alias a uma coluna ou tabela.<p></p>
* `UPPER`: Converte todas as letras em uma string para maiúsculas.<p></p>
* `LOWER`: Converte todas as letras em uma string para minúsculas.<p></p>
* `INITCAP`: Converte a primeira letra de cada palavra em uma string para maiúscula.<p></p>
* `CONCAT`: Concatena duas ou mais strings.<p></p>
* `SUBSTRING`: Extrai uma porção de uma string.<p></p>
* `LENGTH`: Retorna o comprimento de uma string.<p></p>
* `TRIM`: Remove espaços em branco ou outros caracteres de uma string.<p></p>
* `REPLACE`: Substitui uma parte de uma string por outra.
<p></p>
Estas são apenas algumas das funções de string disponíveis no MySQL. É importante ressaltar que o uso correto dessas funções depende do contexto em que estão sendo utilizadas e é importante ler a documentação oficial do MySQL para entender seu uso correto.
	
<p></p>
Alem das consultas dos campos podemos utilizar a função REGEXP_REPLACE no comando SELECT para tratar a informação de acordo com a expressão regular especificada. Por exemplo, o seguinte código remove todos os caracteres que não são números de uma string
<p></p>	
	
```sql
SELECT REGEXP_REPLACE('Exemplo de 123 string', '[^0-9]', '') AS resultado;
```
<p></p>	
A função REGEXP_REPLACE é uma poderosa ferramenta de tratamento de strings no MySQL, permitindo a substituição de padrões específicos com facilidade, tornando possível realizar tarefas como remover caracteres indesejados, substituir espaços por sublinhados, entre outras aplicações criativas.

<p></p>
Concatenação de strings: Para concatenar strings, podemos usar o operador "CONCAT()". Por exemplo, para concatenar o
nome e sobrenome de uma pessoa em uma única coluna:
<p></p>
	
```sql
SELECT CONCAT(nome, ' ', sobrenome) as 'Nome Completo' FROM tabela;
SELECT CONCAT('R$', preco) as 'Preço em Reais' FROM tabela;
```
<p></p>	
Aqui está um exemplo de como usar a função "REPLACE()" para substituir uma string em uma consulta My:<p></p>
	
```sql
SELECT REPLACE(nome, 'J', 'K') as 'Nome Alterado' FROM tabela;
```
<p></p>	
A função REPLACE(nome, 'J', 'K') irá buscar a coluna nome e substituir todas as ocorrências da letra "J" por "K" e
retornará o resultado na coluna "Nome Alterado".<p></p>
	
```sql
UPDATE tabela SET email = REPLACE(email, '@gmail.com', '@hotmail.com');
```
<p></p>	
Esse comando irá buscar todos os valores na coluna email e substituir todas as ocorrências de '@gmail.com' por
'@hotmail.com' e essas alterações serão salvas na tabela.
<p></p>




## Funções Matemáticas
<p></p>
Adição de números: Para adicionar números, podemos usar o operador "+". Por exemplo, para somar o salário de todos os funcionários:<p></p>
	
```sql
SELECT SUM(salario) as 'Total Salário' FROM tabela;
```
<p></p>	
Subtração de números: Para subtrair números, podemos usar o operador "-". Por exemplo, para calcular a diferença entre as vendas de dois meses:<p></p>
	
```sql	
SELECT (SELECT SUM(vendas) FROM tabela WHERE mes = 'jan') - (SELECT SUM(vendas) FROM tabela WHERE mes = 'dez') as
'Diferença de Vendas';
```
<p></p>	
Multiplicação de números: Para multiplicar números, podemos usar o operador "*". Por exemplo, para calcular o preço total de uma compra:<p></p>
	
```sql
SELECT quantidade * preco as 'Total' FROM tabela;
```
<p></p>	
Divisão de números: Para dividir números, podemos usar o operador "/". Por exemplo, para calcular a média de vendas por mês:<p></p>
	
```sql
SELECT SUM(vendas) / COUNT(DISTINCT mes) as 'Média de Vendas' FROM tabela;
```
<p></p>
Aqui está um exemplo de como combinar operações matemáticas de soma, divisão e subtração em uma única conta :<p></p>

```sql
SELECT (SUM(vendas) - SUM(devolucoes)) / COUNT(DISTINCT mes) as 'Média de Lucro' FROM tabela;
```
<p></p>	
Esse comando irá calcular a média de lucro por mês, subtraindo as devoluções das vendas e dividindo o resultado pelo
número de meses distintos.
<p></p>
	
```sql
SELECT (SUM(quantidade) * preco) - (SUM(quantidade) * preco * desconto/100) as 'Total com Desconto' FROM tabela;
```
Esse comando irá calcular o total com desconto, multiplicando a quantidade pelo preco e subtraindo o valor do desconto.
<p></p>
	
```sql
SELECT (quantidade * preco) - desconto AS total_com_desconto FROM tabela;	
```
<p></p>
Esse comando irá calcular o  calcular as vendas de um vendedor por dia.
<p></p>
	
```sql
SELECT data, vendedor, SUM(valor_venda) AS 'total_vendido'
FROM tabela
GROUP BY data, vendedor;
```
<p></p>
Nessa consulta, a cláusula GROUP BY agrupa as vendas por data e vendedor, e a função SUM soma o valor de cada venda. O resultado será uma tabela com a data, o nome do vendedor e o total de vendas para cada combinação de data e vendedor.
	
## Outros

SUBQUERY: Utiliza uma consulta dentro de outra consulta.<p></p>
	
```sql
SELECT coluna1
FROM tabela1
WHERE coluna2 IN ( SELECT coluna2 FROM tabela2 WHERE condicao);
```

GROUP BY: Agrupa resultados por uma ou mais colunas.
<p></p>
	
```sql
SELECT coluna1, SUM(coluna2) 
FROM tabela
GROUP BY coluna1;
```

HAVING: Utilizado com o GROUP BY para filtrar resultados agrupados.<p></p>
	
```sql
SELECT coluna1, SUM(coluna2)
FROM tabela
GROUP BY coluna1 
HAVING SUM(coluna2) > valor;
```

LIMIT: Limita o número de resultados retornados.
<p></p>
	
```sql
SELECT coluna1, coluna2
FROM tabela
LIMIT 10;
```	

	
Subquery com JOIN: Utiliza uma subquery para selecionar dados de uma tabela e juntá-los à tabela principal através de um
JOIN.
<p></p>
	
```sql
SELECT tabela1.coluna1, tabela2.coluna2
FROM tabela1
JOIN (SELECT coluna2, coluna3 FROM tabela2 WHERE condicao) AS tabela2 ON tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE tabela1.coluna1 IN (SELECT coluna4 FROM tabela3 WHERE condicao);
```


GROUP BY com HAVING: Agrupa resultados por uma ou mais colunas e utiliza o HAVING para filtrar resultados agrupados.
<p></p>
	
```sql
SELECT coluna1, SUM(coluna2), AVG(coluna3) 
FROM tabela
GROUP BY coluna1
HAVING SUM(coluna2) > valor AND AVG(coluna3) < outro_valor; 
```

EXISTS: Verifica se existem valores correspondentes em uma subquery. 
<p></p>
	
```sql
SELECT coluna1, coluna2 
FROM tabela1 
WHERE EXISTS (SELECT * FROM tabela2 WHERE tabela1.coluna_relacionada=tabela2.coluna_relacionada AND condicao);
```

NOT EXISTS: Verifica se não existem valores correspondentes em uma subquery. 
<p></p>
	
```sql
SELECT coluna1, coluna2 
FROM tabela1
WHERE NOT EXISTS (SELECT * FROM tabela2 WHERE tabela1.coluna_relacionada=tabela2.coluna_relacionada AND condicao); 
```
<br>
</details>
<br>


## Comandos DML de Ligação:📌
<details>
<summary>Avançado</summary>
	
<br></br>
Existem 4 tipos de junções (joins) diferentes que você pode usar para combinar dados de duas ou mais tabelas: `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN` e `FULL OUTER JOIN`.
<p></p>

* `INNER JOIN`: Este tipo de junção retorna somente as linhas que correspondem a ambas as tabelas. É o tipo de junção mais comum.<p></p>
* `LEFT JOIN (OUTER)`: Este tipo de junção retorna todas as linhas da tabela à esquerda (especificada primeiro na cláusula FROM), incluindo as linhas que não correspondem à tabela à direita. As colunas não correspondentes da tabela à direita são preenchidas com NULL.<p></p>
* `RIGHT JOIN (OUTER)`: Este tipo de junção é o oposto do LEFT JOIN, retornando todas as linhas da tabela à direita e as linhas não correspondentes da tabela à esquerda são preenchidas com NULL.<p></p>
* `FULL OUTER JOIN`: Este tipo de junção retorna todas as linhas de ambas as tabelas, independentemente se existe ou não correspondência entre elas. Se uma linha não corresponde, as colunas correspondentes são preenchidas com NULL.<p></p>
	

<details>
<summary><p align="center">DIAGRAMA LEFT JOIN ---[EM CONSTRUÇÃO]</p></summary>
<p align="center">
  <img src="https://raw.githubusercontent.com/DiogovBortolotti/MySQL-Cheat-Sheet/main/Imagens/LEFT%20JOIN.png" width="620" height="420"/>
</p>
</details>

	
	
	
<br></br>
JOIN: Recupera dados de várias tabelas relacionadas.<p></p>
	
```sql
SELECT
tabela1.coluna1, tabela2.coluna2
FROM tabela1 
JOIN tabela2 ON
tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE condicao;
```


JOIN com subquery: Utiliza uma subquery para selecionar dados de uma tabela relacionada antes de juntá-los à tabela
principal.<p></p>
	
```sql
SELECT tabela1.coluna1, tabela2.coluna2 
FROM tabela1
JOIN (SELECT coluna2, coluna3 FROM tabela2 WHERE condicao) AS tabela2 ON tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE condicao;
```

A cláusula UNION é usada para combinar resultados de duas ou mais consultas SELECT em uma única tabela de resultados. A sintaxe básica do UNION é a seguinte<p></p>
	
```sql
SELECT tabela1.coluna1
FROM tabela1
WHERE condicao
UNION
SELECT tabela2.coluna2
FROM tabela2
WHERE condicao;
```

OUTER JOIN: Retorna os dados de ambas as tabelas, incluindo os registros que não possuem correspondência entre as
tabelas relacionadas.<p></p>
	
```sql
SELECT tabela1.coluna1, tabela2.coluna2
FROM tabela1
LEFT OUTER JOIN tabela2 ON
tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE condicao;
```

UNION com ordenação: Combina resultados de várias consultas SELECT e os ordena de acordo com uma coluna específica.<p></p>
	
```sql
SELECT a.coluna1, a.coluna2, a.coluna3
FROM tabela1 a
WHERE a.coluna3 = 'valor1'
UNION
SELECT b.coluna1, b.coluna2, b.coluna3
FROM table2 b
WHERE b.column4 = 'valor2'
ORDER BY coluna1 ASC;
```
<p></p>
INNER JOIN: Recupera dados de várias tabelas relacionadas e retorna somente os registros que possuem correspondência
entre as tabelas relacionadas.
<p></p>
	
```sql
SELECT tabela1.coluna1, tabela2.coluna2
FROM tabela1
INNER JOIN tabela2 ON
tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE condicao;
```
<p></p>
INNER JOIN com ON e USING: Utiliza duas condições de junção, uma com ON e outra com USING, para recuperar dados de várias tabelas relacionadas. 
<p></p>
	
```sql
SELECT tabela1.coluna1, tabela2.coluna2 
FROM tabela1 a
INNER JOIN tabela2 b ON a.coluna1 = b.coluna2
WHERE a.coluna3 = 'valor';
```

<p></p>
LEFT JOIN: une todas as linhas da tabela da esquerda com as correspondentes da tabela da direita, preenchendo com valores NULL caso não haja correspondência.

```sql
SELECT clientes.id_cliente, clientes.nome, pedidos.id_pedido
FROM clientes
LEFT JOIN pedidos
ON clientes.id_cliente = pedidos.id_cliente;
RIGHT JOIN:
```
<p></p>
RIGHT JOIN: une todas as linhas da tabela da direita com as correspondentes da tabela da esquerda, preenchendo com valores NULL caso não haja correspondência.

```sql
SELECT clientes.id_cliente, clientes.nome, pedidos.id_pedido
FROM clientes
RIGHT JOIN pedidos
ON clientes.id_cliente = pedidos.id_cliente;
```
<p></p>

Tanto o `LEFT JOIN` quanto o `RIGHT JOIN` são usados para unir as tabelas clientes e pedidos pela coluna id_cliente. A diferença é que, no LEFT JOIN, todas as linhas da tabela da esquerda (clientes) serão incluídas no resultado, enquanto que, no RIGHT JOIN, todas as linhas da tabela da direita (pedidos) serão incluídas no resultado. Se uma linha na tabela da esquerda ou da direita não tiver correspondência na tabela oposta, o valor dessas colunas será NULL.
<p></p>



<p></p>
Aqui está um exemplo de consulta SQL com múltiplos joins:
<p></p>
Esta consulta seleciona informações de nome de cliente, data do pedido, nome do produto, quantidade do produto e preço do produto de uma tabela de clientes, tabela de pedidos e tabela de itens de pedidos. A consulta faz um INNER JOIN das três tabelas com base nas chaves estrangeiras, e usa uma cláusula WHERE para filtrar os resultados para o nome "Diogo" e a data entre 01/01/2022 e 31/12/2022.
<p></p>

```sql
SELECT clientes.nome, pedidos.data, itens_pedido.produto, itens_pedido.quantidade, itens_pedido.preco
FROM clientes
INNER JOIN pedidos ON clientes.id = pedidos.id_cliente
INNER JOIN itens_pedido ON pedidos.id = itens_pedido.id_pedido and pedidos.data_fiscal = itens_pedido.data_fiscal
WHERE clientes.nome = 'Diogo' AND pedidos.data BETWEEN '2022-01-01' AND '2022-12-31'
```
<p></p>INNER JOIN: Recupera dados de várias tabelas relacionadas e retorna somente os registros que possuem correspondência entre as tabelas relacionadas.
Para melhorar a eficiência e clareza do código, é uma boa prática utilizar nomes abreviados das tabelas nas consultas.
<p></p>

```sql
SELECT cl.nome, ped.data, itp.produto, itp.quantidade, itp.preco
FROM clientes cl
INNER JOIN pedidos ped ON cl.id = ped.id_cliente
INNER JOIN itens_pedido itp ON ped.id = itp.id_pedido
WHERE cl.nome = 'Diogo' AND ped.data BETWEEN '2022-01-01' AND '2022-12-31'
```
<p></p>


<p></p>
Extras:mag::
<p></p>

Para garantir a efetividade da consulta e preservar a performance do banco de dados, é importante limitar a quantidade de informações retornadas pela consulta e realizar as ligações entre as tabelas de forma adequada. Uma boa prática é sempre adicionar o comando `limit` no final da consulta para limitar o número de resultados retornados.
<p></p>

E possivel a utilização de JOINs em operações de `update` e `delete` e devem ser realizadas com muita atenção, já que pode haver perda de dados importantes.

<br>
</details>
<br>


