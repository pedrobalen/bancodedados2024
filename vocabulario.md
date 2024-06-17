# Avaliação final
Alunos: Pedro Balen e Miguel Toller 

- sistema gerenciador de banco de dados: 
	SGBD é um software dente de banco de dados que permite criar, gerenciar e manipular banco de dados
	de maneira eficiente e segura.

- restrições em banco de dados: 
	São regras que garantem a integridade dos dados presentes na tabela, por exemplo 
	chave primária, chave estrangeira, NOT NULL, UNIQUE, CHECK, e DEFAULT.

- modelo relacional: 
	Modelo de dados que organiza os dados em tabela, ou seja, criando as relações através de linhas e colunas.

- modelagem conceitual: 
	Fase inicial do desenvolvimento do banco, onde se define a estrutura lógica do sistema através do
	diagrama de Entidade-Relacionamento.
	
- modelagem lógica: 
	O modelo conceitual é transformado em um esquema lógico, detalhando as tabelas, colunas e relações.
	
- modelagem física: 
	Converte o modelo logico em um esquema fisico específico de um SGBD, por exemplo MySQL.
	
- linguagem SQL: 
	Linguagem padrão para manipulação e gerenciamento de banco relacional, possui comandos para
	definição, manipulação e controle de dados.
	
- Data Definition Language (DDL): 
	Métodos dentro do SQL que auxilia na definição da estrutura do banco de dados, por exemplo CREATE,
	DROP, ALTER, TRUNCATE.
	
- Data Manipulation Language (DML): 
	Métodos dentro do SQL que auxilia na manipulação da estrutura do banco de dados, por exemplo SELECT,
	INSERT, UPDATE, DELETE.

- Boas práticas em modelagem de banco de dados: 
	Evitar o uso de ON DELETE CASCADE.
	Criação de tabelas de acordo com o relacionamento dos dados.
	Evitar redundâncias.
	Respeitar o tipo de dado.
	

# Todos os clientes armazenados no sistema:
SELECT * FROM cliente;


# Exiba os veículos que tenham final 3 no número da placa
SELECT * FROM veiculo WHERE placa LIKE '%3';


# Mostre os clientes que residem no RS e que não possuam telefone
SELECT * FROM cliente WHERE uf_cnh = 'RS' AND telefone IS NULL;


# Exiba o código dos clientes que alugaram veículos por mais de 90 dias.
SELECT id_cliente FROM contrato_aluguel WHERE duracao > 90;


# Quantos veículos há cadastrados no sistema
SELECT COUNT(*) AS total_veiculos FROM veiculo;


# Mostre o veículo alugado por Alexandre Zamberlan.
SELECT v.*
FROM veiculo v
WHERE v.id_veiculo IN (
    SELECT ca.id_veiculo
    FROM contrato_aluguel ca
    JOIN cliente c ON ca.id_cliente = c.id_cliente
    WHERE c.nome = 'Alexandre Zamberlan'
);


# Mostre os clientes e os escritórios associados no contrato de aluguel.
SELECT c.nome AS cliente_nome, e.nome AS escritorio_nome
FROM contrato_aluguel ca
JOIN cliente c ON ca.id_cliente = c.id_cliente
JOIN escritorio e ON ca.id_escritorio = e.id_escritorio;

