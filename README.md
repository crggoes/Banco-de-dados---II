# Banco-de-dados---II
Exercício - Pratico

Desenvolva um banco de dados e relacione tabelas através de chaves estrangeiras ou nomes de colunas iguais. Siga as instruções:
crie uma base de dados; 
crie tabelas nessa base de dados;
em cada tabela, adicione atributos;
insira dados em cada tabela;
utilize os comandos Joins para realizar consultas nas tabelas. 


RESOLUÇÃO


Passo 1: Criar uma base de dados Vamos começar criando uma base de dados chamada "empresa". Executamos o seguinte comando SQL:

CREATE DATABASE empresa;
Passo 2: Criar tabelas Vamos criar duas tabelas: "funcionarios" e "departamentos".

USE empresa;

CREATE TABLE funcionarios (
    id INT PRIMARY KEY,
    nome VARCHAR(100),
    departamento_id INT,
    salario DECIMAL(8,2),
    FOREIGN KEY (departamento_id) REFERENCES departamentos(id)
);

CREATE TABLE departamentos (
    id INT PRIMARY KEY,
    nome VARCHAR(100)
);
Passo 3: Inserir dados nas tabelas Vamos inserir alguns dados nas tabelas que criamos.

INSERT INTO departamentos (id, nome)
VALUES (1, 'RH'), (2, 'Vendas'), (3, 'Financeiro');

INSERT INTO funcionarios (id, nome, departamento_id, salario)
VALUES (1, 'João', 1, 5000.00),
       (2, 'Maria', 2, 4000.00),
       (3, 'Pedro', 2, 4500.00),
       (4, 'Ana', 3, 6000.00);
Passo 4: Realizar consultas através de Joins Vamos realizar algumas consultas para mostrar como usar Joins para relacionar as tabelas.

Consulta para obter o nome do departamento de cada funcionário:
SELECT funcionarios.nome, departamentos.nome AS departamento
FROM funcionarios
JOIN departamentos ON funcionarios.departamento_id = departamentos.id;
Resultado:

nome	departamento
João	RH
Maria	Vendas
Pedro	Vendas
Ana	Financeiro
Consulta para obter o nome e salário de todos os funcionários, juntamente com o nome do departamento:
SELECT funcionarios.nome, funcionarios.salario, departamentos.nome AS departamento
FROM funcionarios
JOIN departamentos ON funcionarios.departamento_id = departamentos.id;
Resultado:

nome	salario	departamento
João	5000.00	RH
Maria	4000.00	Vendas
Pedro	4500.00	Vendas
Ana	6000.00	Financeiro
Esses são apenas exemplos básicos de como usar Joins em consultas para relacionar tabelas em um banco de dados. Existem diferentes tipos de Joins, como Inner Join, Left Join, Right Join, Full Outer Join, que podem ser usados dependendo da necessidade da consulta.
