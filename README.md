
## Comandos de DML basicos: ⚡️


<details>
  <summary>Clique aqui para ver mais informações</summary>
<p></p>

<br>
INSERT: Adiciona novos registros em uma tabela.<p></p>

```sql
INSERT INTO tabela_nome (coluna1, coluna2, coluna3) VALUES (valor1, valor2, valor3);
```
<p></p>
UPDATE: Atualiza os dados existentes em uma tabela.<p></p>

```sql
UPDATE tabela_nome SET coluna1 = novo_valor WHERE condicao;
```
<p></p>

DELETE: Exclui registros de uma tabela.<p></p>

```sql
DELETE FROM tabela_nome WHERE condicao;
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
</details>
<br>

## Comandos de DML com Tratamentos:✨
<details>
<summary>Clique aqui para ver mais informações</summary>
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
Outro exemplo:<p></p>
	
```sql
SELECT * FROM tabela WHERE campo REGEXP '^([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+\.[a-zA-Z]{2,})$';
```
Esse comando irá selecionar todas as linhas da tabela onde o valor do campo corresponde à expressão regular especificada. A expressão regular usada nesse exemplo é "^([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+.[a-zA-Z]{2,})$", que é uma expressão regular para validação de email.

## STRING
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




## Funções Matematicas
<p></p>
Adição de números: Para adicionar números, podemos usar o operador "+". Por exemplo, para somar o salário de todos os
funcionários:<p></p>
	
```sql
SELECT SUM(salario) as 'Total Salário' FROM tabela;
```
<p></p>	
Subtração de números: Para subtrair números, podemos usar o operador "-". Por exemplo, para calcular a diferença entre
as vendas de dois meses:<p></p>
	
```sql	
SELECT (SELECT SUM(vendas) FROM tabela WHERE mes = 'jan') - (SELECT SUM(vendas) FROM tabela WHERE mes = 'dez') as
'Diferença de Vendas';
```
<p></p>	
Multiplicação de números: Para multiplicar números, podemos usar o operador "*". Por exemplo, para calcular o preço
total de uma compra:<p></p>
	
```sql
SELECT quantidade * preco as 'Total' FROM tabela;
```
<p></p>	
Divisão de números: Para dividir números, podemos usar o operador "/". Por exemplo, para calcular a média de vendas por
mês:<p></p>
	
```sql
SELECT SUM(vendas) / COUNT(DISTINCT mes) as 'Média de Vendas' FROM tabela;
```
<p></p>
Aqui está um exemplo de como combinar operações matemáticas de soma, divisão e subtração em uma única conta em uma
consulta My:<p></p>
	
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
WHERE EXISTS (SELECT 1 FROM tabela2 WHERE tabela1.coluna_relacionada=tabela2.coluna_relacionada AND condicao);
```

NOT EXISTS: Verifica se não existem valores correspondentes em uma subquery. 
<p></p>
	
```sql
SELECT coluna1, coluna2 
FROM tabela1
WHERE NOT EXISTS (SELECT 1 FROM tabela2 WHERE tabela1.coluna_relacionada=tabela2.coluna_relacionada AND condicao); 
```
<br>
</details>
<br>


## Comandos DML de União para MySQL:📌
<details>
<summary>Clique aqui para ver mais informações</summary>

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

UNION: Combina resultados de várias consultas SELECT.<p></p>
	
```sql
SELECT tabela1.coluna1
FROM tabela1
WHERE condicao
UNION
SELECT tabela2.coluna2
FROM tabela2
WHERE condicao;
```

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

OUTER JOIN: Retorna os dados de ambas as tabelas, incluindo os registros que não possuem correspondência entre as
tabelas relacionadas.<p></p>
	
```sql
SELECT tabela1.coluna1, tabela2.coluna2
FROM tabela1
LEFT OUTER JOIN tabela2 ON
tabela1.coluna_relacionada = tabela2.coluna_relacionada
WHERE condicao;
```


Exemplos de consultas DML mais complexas:


JOIN com subquery: Utiliza uma subquery para selecionar dados de uma tabela relacionada antes de juntá-los à tabela
principal.<p></p>
	
```sql
SELECT tabela1.coluna1, tabela2.coluna2 
FROM tabela1
JOIN (SELECT coluna2, coluna3 FROM tabela2 WHERE condicao) AS tabela2 ON tabela1.coluna_relacionada = tabela2.coluna_relacionada
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

INNER JOIN com ON e USING: Utiliza duas condições de junção, uma com ON e outra com USING, para recuperar dados de várias tabelas relacionadas. 
<p></p>
	
```sql
SELECT tabela1.coluna1, tabela2.coluna2 
FROM tabela1 a
INNER JOIN tabela2 b ON a.coluna1 = b.coluna2
WHERE a.coluna3 = 'valor';
```
<details>
<summary><p align="center">DIAGRAMA LEFT JOIN</p></summary>
<p align="center">
  <img src="https://raw.githubusercontent.com/DiogovBortolotti/MySQL-Cheat-Sheet/main/Imagens/LEFT%20JOIN.png" width="620" height="420"/>
</p>
</details>




Observação estes exemplos de join podem ser utilizando não somente em SELECT mas tambem em UPDATE,DELETE ao utilizar deve-se tomar muito cuidado pois pode dar
perda de dados importantes.

<br>
</details>
<br>
