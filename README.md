
Comandos de DML basicos:

<p></p><p></p>
INSERT: Adiciona novos registros em uma tabela.
```
INSERT INTO tabela_nome (coluna1, coluna2, coluna3) VALUES (valor1, valor2, valor3);
```
<p></p>
UPDATE: Atualiza os dados existentes em uma tabela.
```
UPDATE tabela_nome SET coluna1 = novo_valor WHERE condicao;
```
<p></p><p></p>
DELETE: Exclui registros de uma tabela.
```
DELETE FROM tabela_nome WHERE condicao;
```
<p></p><p></p>
SELECT: Busca dados de uma tabela.
```
SELECT coluna1, coluna2 FROM tabela_nome WHERE condicao;
```
<p></p><p></p>
SELECT DISTINCT: Recupera dados únicos de uma tabela.
```
SELECT DISTINCT coluna1 FROM tabela_nome;
```

<p></p><p></p><p></p>
Comandos de DML com Tratamentos:<p></p>

LIKE: Utilizado para buscar valores semelhantes em uma coluna. Por exemplo, para encontrar todos os registros com nomes que começam com "Jo":<p></p>
SELECT * FROM tabela WHERE nome LIKE 'Jo%';


IN: Utilizado para buscar valores específicos em uma coluna. Por exemplo, para encontrar todos os registros com idades entre 20 e 30:<p></p>
SELECT * FROM tabela WHERE idade IN (20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30);


NOT IN: Utilizado para excluir valores específicos em uma coluna. Por exemplo, para encontrar todos os registros com idades que não estão entre 20 e 30:<p></p>
SELECT * FROM tabela WHERE idade NOT IN (20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30);
<p></p><p></p>

-- REGEX
Aqui estão alguns exemplos de como usar expressões regulares para tratar informações em consultas My:<p></p>
REGEXP: Utilizado para buscar valores que correspondem a uma expressão regular específica. Por exemplo, para encontrar todos os registros com e-mails que terminam com "gmail.com":

SELECT * FROM tabela WHERE email REGEXP 'gmail\.com$';

NOT REGEXP: Utilizado para excluir valores que correspondem a uma expressão regular específica. Por exemplo, para encontrar todos os registros com e-mails que não terminam com "gmail.com":

SELECT * FROM tabela WHERE email NOT REGEXP 'gmail\.com$';


RLIKE: É uma forma alternativa para utilizar o operador REGEXP.

SELECT * FROM tabela WHERE email RLIKE 'gmail\.com$';

É importante lembrar que o uso de expressões regulares pode afetar o desempenho de uma consulta, portanto, é recomendável usá-las com moderação e testá-las antes de usá-las em produção.



Concatenação de strings: Para concatenar strings, podemos usar o operador "CONCAT()". Por exemplo, para concatenar o nome e sobrenome de uma pessoa em uma única coluna:

SELECT CONCAT(nome, ' ', sobrenome) as 'Nome Completo' FROM tabela;
SELECT CONCAT('R$', preco) as 'Preço em Reais' FROM tabela;

Aqui está um exemplo de como usar a função "REPLACE()" para substituir uma string em uma consulta My:
SELECT REPLACE(nome, 'J', 'K') as 'Nome Alterado' FROM tabela;

A função REPLACE(nome, 'J', 'K') irá buscar a coluna nome e substituir todas as ocorrências da letra "J" por "K" e retornará o resultado na coluna "Nome Alterado".

Outro exemplo:
UPDATE tabela SET email = REPLACE(email, '@gmail.com', '@hotmail.com');

Esse comando irá buscar todos os valores na coluna email e substituir todas as ocorrências de '@gmail.com' por '@hotmail.com' e essas alterações serão salvas na tabela.

Esses são apenas alguns exemplos simples, mas a função REPLACE() pode ser usada de várias formas para manipular dados. Certifique-se de testar suas consultas e verificar se estão retornando os resultados esperados antes de usá-las em produção.



-- Contas
Adição de números: Para adicionar números, podemos usar o operador "+". Por exemplo, para somar o salário de todos os funcionários:
SELECT SUM(salario) as 'Total Salário' FROM tabela;

Subtração de números: Para subtrair números, podemos usar o operador "-". Por exemplo, para calcular a diferença entre as vendas de dois meses:
SELECT (SELECT SUM(vendas) FROM tabela WHERE mes = 'jan') - (SELECT SUM(vendas) FROM tabela WHERE mes = 'dez') as 'Diferença de Vendas';

Multiplicação de números: Para multiplicar números, podemos usar o operador "*". Por exemplo, para calcular o preço total de uma compra:
SELECT quantidade * preco as 'Total' FROM tabela;

Divisão de números: Para dividir números, podemos usar o operador "/". Por exemplo, para calcular a média de vendas por mês:
SELECT SUM(vendas) / COUNT(DISTINCT mes) as 'Média de Vendas' FROM tabela;

Aqui está um exemplo de como combinar operações matemáticas de soma, divisão e subtração em uma única conta em uma consulta My:

SELECT (SUM(vendas) - SUM(devolucoes)) / COUNT(DISTINCT mes) as 'Média de Lucro' FROM tabela;

Esse comando irá calcular a média de lucro por mês, subtraindo as devoluções das vendas e dividindo o resultado pelo número de meses distintos.

Outro exemplo

SELECT (SUM(quantidade) * preco) - (SUM(quantidade) * preco * desconto/100) as 'Total com Desconto' FROM tabela;

Esse comando irá calcular o total com desconto, multiplicando a quantidade pelo preco e subtraindo o valor do desconto.


Comandos DML avançados para MySQL:


JOIN: Recupera dados de várias tabelas relacionadas.

SELECT
	tabela1.coluna1,
	tabela2.coluna2
FROM
	tabela1
JOIN tabela2 ON
	tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE
	condicao;


UNION: Combina resultados de várias consultas SELECT.

SELECT
	coluna1
FROM
	tabela1
WHERE
	condicao
UNION 
SELECT
	coluna2
FROM
	tabela2
WHERE
	condicao;


SUBQUERY: Utiliza uma consulta dentro de outra consulta.
SELECT
	coluna1
FROM
	tabela1
WHERE
	coluna2 IN (
	SELECT
		coluna2
	FROM
		tabela2
	WHERE
		condicao);


GROUP BY: Agrupa resultados por uma ou mais colunas.
SELECT
	coluna1,
	SUM(coluna2)
FROM
	tabela
GROUP BY
	coluna1;


HAVING: Utilizado com o GROUP BY para filtrar resultados agrupados.
SELECT
	coluna1,
	SUM(coluna2)
FROM
	tabela
GROUP BY
	coluna1
HAVING
	SUM(coluna2) > valor;


LIMIT: Limita o número de resultados retornados.
SELECT
	coluna1,
	coluna2
FROM
	tabela
LIMIT 10;


INNER JOIN: Recupera dados de várias tabelas relacionadas e retorna somente os registros que possuem correspondência entre as tabelas relacionadas.
SELECT
	tabela1.coluna1,
	tabela2.coluna2
FROM
	tabela1
INNER JOIN tabela2 ON
	tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE
	condicao;


OUTER JOIN: Retorna os dados de ambas as tabelas, incluindo os registros que não possuem correspondência entre as tabelas relacionadas.
SELECT
	tabela1.coluna1,
	tabela2.coluna2
FROM
	tabela1
LEFT OUTER JOIN tabela2 ON
	tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE
	condicao;


Esses são apenas alguns exemplos de comandos DML avançados para MySQL. Há muitas outras opções e variações disponíveis para trabalhar com banco de dados MySQL. Sempre é recomendado consultar a documentação oficial e experimentar os comandos em um ambiente de testes antes de usá-los em um ambiente de produção.




Exemplos de consultas DML mais complexas:


JOIN com subquery: Utiliza uma subquery para selecionar dados de uma tabela relacionada antes de juntá-los à tabela principal.
SELECT
	tabela1.coluna1,
	tabela2.coluna2
FROM
	tabela1
JOIN (
	SELECT
		coluna2,
		coluna3
	FROM
		tabela2
	WHERE
		condicao) AS tabela2 ON
	tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE
	condicao;


UNION com ordenação: Combina resultados de várias consultas SELECT e os ordena de acordo com uma coluna específica.


SELECT
	coluna1,
	coluna2
FROM
	tabela1
WHERE
	condicao
ORDER BY
	coluna
UNION 
SELECT
	coluna1,
	coluna2
FROM
	tabela2
WHERE
	condicao
ORDER BY
	coluna2
ORDER BY
	coluna2;


Subquery com JOIN: Utiliza uma subquery para selecionar dados de uma tabela e juntá-los à tabela principal através de um JOIN.

SELECT
	tabela1.coluna1,
	tabela2.coluna2
FROM
	tabela1
JOIN (
	SELECT
		coluna2,
		coluna3
	FROM
		tabela2
	WHERE
		condicao) AS tabela2 ON
	tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE
	tabela1.coluna1 IN (
	SELECT
		coluna4
	FROM
		tabela3
	WHERE
		condicao);



GROUP BY com HAVING: Agrupa resultados por uma ou mais colunas e utiliza o HAVING para filtrar resultados agrupados.

SELECT
	coluna1,
	SUM(coluna2),
	AVG(coluna3)
FROM
	tabela
GROUP BY
	coluna1
HAVING
	SUM(coluna2) > valor
	AND AVG(coluna3) < outro_valor;

EXISTS: Verifica se existem valores correspondentes em uma subquery.
SELECT
	coluna1,
	coluna2
FROM
	tabela1
WHERE
	EXISTS (
	SELECT
		1
	FROM
		tabela2
	WHERE
		tabela1.coluna_relacionada = tabela2.coluna_relacionada
		AND condicao);


NOT EXISTS: Verifica se não existem valores correspondentes em uma subquery.

SELECT
	coluna1,
	coluna2
FROM
	tabela1
WHERE
	NOT EXISTS (
	SELECT
		1
	FROM
		tabela2
	WHERE
		tabela1.coluna_relacionada = tabela2.coluna_relacionada
		AND condicao);


INNER JOIN com ON e USING: Utiliza duas condições de junção, uma com ON e outra com USING, para recuperar dados de várias tabelas relacionadas.

SELECT
	tabela1.coluna1,
	tabela2.coluna2
FROM
	tabela1
INNER JOIN tabela2 ON 	tabel



Observação estes exemplos podem ser utilizando não somente em SELECT mas tambem em UPDATE,DELETE ao utilizar deve-se tomar muito cuidado pois pode dar perda de dados importantes.
