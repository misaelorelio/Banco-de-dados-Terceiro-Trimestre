# Banco-de-dados-Terceiro-Trimestre

/* 
Link videoaula JOIN → https://www.youtube.com/watch?v=wm3e7rICW2I&list=PLg5-aZqPjMmC69aUbYfCHiXIPbb5MwMmw&index=10
caso queira treinar na prática link script ddl e dml: https://github.com/heliokamakawa/curso_bd/blob/master/00-estudo%20de%20caso-loja_bebida-script.sql
*** JOIN - LISTA 01 ***

Sintaxe de uma consulta com JOIN:
SELECT 
    {nome_coluna1}
    ,{nome_coluna2}
    , [... outras colunas]
FROM {nome_tabela1}, {nome_tabela2}
WHERE pk = fk;

Sintaxe
1.	Escreva o comando que liste os nomes de todas as cidades e as respectivas siglas do estado.

SELECT cidade.nome, estado.sigla
FROM cidade, estado
WHERE estado.id = cidade.estado_id ;

2.	Escreva o comando que liste os nomes das cidades ativas e as respectivas siglas do estado. 

SELECT  cidade.nome, cidade.ativo, estado.sigla
FROM cidade, estado
WHERE estado.id = cidade.estado_id 
AND cidade.ativo = 'S';

3.	Escreva o comando que liste os nomes dos cliente e os nomes das respectivas cidades. 
SELECT cliente.nome, cidade.nome
FROM cliente, cidade 
WHERE cidade.id = cliente.cidade_id;

4.	Escreva o comando que liste os nomes dos cliente e os nomes das respectivas cidades. Liste somente os clientes que moram na cidade de Paranavaí.
SELECT cliente.nome,cidade.nome
FROM cliente, cidade 
WHERE cliente.id = cliente.cidade_id 
AND cidade.nome = 'PARANAVAÍ';

5.	Escreva o comando que liste os nomes das cidades e as respectivas siglas do estado. Liste somente as cidades ativas.
SELECT cidade.nome, estado.sigla
FROM  cidiade, estado
WHERE cidade.estado_id = estado.id
AND cidade.ativo = 'S';

6.	Escreva o comando que liste os nomes dos funcionários e os nomes das respectivas cidades.
SELECT funcionario.nome, cidade.nome
FROM funcionario, cidade
WHERE funcionario.cidade_id = cidade.id;
 
7.	Escreva o comando que liste os nomes dos funcionários e a sigla do respectivo estado.
SELECT funcionario.nome,estado.sigla
FROM funcionario, estado
WHERE funcionario.estado_id = estado.id; 
(Não existe relacionamento entre funcionario e estado)
 
8.	Escreva o comando que liste os nomes dos cliente e os nomes das respectivas cidades. Liste somente os clientes que moram na região sul.
SELECT cliente.nome, cidade.nome 
FROM cliente, cidade 
WHERE cliente.cidade_id = cidade_id ;
(Não existe região na tabela)

9.	Escreva o comando que liste os nomes dos estados com cadastros ativos que possuem algum cliente cadastrado.
SELECT estado.nome, estado.ativo, 
FROM  estado
WHERE estado.ativo = ativo ;
(Não existe dependencia de estado para cliente.)

10.	Escreva o comando que liste todas as vendas e o nome do respectivo funcionário que a realizou.

SELECT  r.id AS ID_VENDA, 
        r.valor AS VALOR,  
        r.total_final AS TOTAL, 
        r.ativo AS ATIVO, 
        r.numero_parcelas AS PARCELAS, 
        fu.nome AS NOME_FUNCIONARIO 
FROM recebimento r
INNER JOIN venda v
INNER JOIN item_caixa ic
INNER JOIN caixa ca 
INNER JOIN funcionario fu
ON r.venda_id = v.id 
AND ca.id = ic.caixa_id
AND ca.funcionario_id = fu.id

11.	Liste o nome dos produtos, o preço de venda e o nome da unidade de medida.

SELECT nome, 
    descricao, 
    preco 
FROM  produto 

12.	Liste o nome dos produtos da marca "Coca-cola".

SELECT *  
FROM  
    produto 
WHERE 
    nome 
LIKE 
    '%Coca-Cola%'
   
----------------------------------OU
Descobrir o ID da "Coca-Cola" e fazer um filtro por ID EX:

SELECT *
FROM produto
WHERE id = x

13. DESAFIO!!! Liste os nomes dos clientes do estado de São Paulo que já compraram o produto 'REFRIGERANTE COCA-COLA GARRAFA PET 3 L'.

select distinct pd.nome, cli.nome, es.nome from venda v
    inner join item_venda iv 
    inner join produto pd
    inner join cliente cli
    inner join estado es
    inner join cidade ci
where v.id = iv.venda_id and
    pd.id = iv.produto_id and
    cli.id = v.cliente_id and
    cli.cidade_id = ci.id and
    ci.estado_id = es.id and
    pd.id = 10 and
    es.nome = "SÃO PAULO"

Semântica
1.	Em que caso devemos utilizar o JOIN? Quais tabelas podem ser utilizando em um comando JOIN?
    R: Quando vamos realizar junção de específicas colunas de diferentes tabelas, aonde ocorre a referência de uma tabela com outra, sendo PK como principal de cada uma e FK para referenciar.
2.	No caso do JOIN, o que é condição de junção. Qual cuidado devemos ter. 
    R: É um caso aonde ocorre a comparação de tabelas, nesse caso a relação de uma com a outra. Deve-se ter cuidado ao unir as tabelas, para evitar o produto cartesiano de todos os itens combinados.
3.	Em relação a sintaxe, em um JOIN não é necessário utilizarmos condições (WHERE) - o comando irá executar normalmente. Porém, em questão de semântica, a cada junção  necessário ter ao menos 1 condição. Explique.
    R: Para realizar uma consulta em específica entre duas tabelas, é necessário uma condição de referência que combina ambas, quer dizer que, a cada junção entre 2 tabelas vai 1 condição. Se por exemplo tiver que realizar a consulta de 10 tabelas em específica, irá precisar de t-1 para referênciar.
5.	O que é produto cartesiano? Como funciona? Qual a relação com o JOIN.
    R: 
6.	Na elaboração de um consulta que envolve 1587 tabelas, serão necessários, quantas condições de junção?
    R: 

 */

