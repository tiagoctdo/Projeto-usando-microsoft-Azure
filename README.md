# Projeto-usando-microsoft-Azure
 criação de tabelas, procedures e scripts estarão armazenados.
 SQL (schema.sql) para criar uma tabela no Azure SQL Database
-- schema.sql

-- Cria a tabela Clientes para armazenar informações dos assinantes do serviço digital
CREATE TABLE Clientes (
    ClienteID INT PRIMARY KEY IDENTITY(1,1),  -- Identificador único autoincremental
    Nome NVARCHAR(100) NOT NULL,              -- Nome completo do cliente
    Email NVARCHAR(100) NOT NULL UNIQUE,      -- Email do cliente (único)
    DataCadastro DATETIME DEFAULT GETDATE(),  -- Data de cadastro com valor padrão para o momento da inserção
    Status NVARCHAR(20) DEFAULT 'ativo'       -- Status do cliente (ativo por padrão)
);
Com o schema definido, podemos utilizá-lo em um cenário de Sistema de Gestão de Assinaturas.
-- Exemplo de clientes na base
INSERT INTO Clientes (Nome, Email, Status)
VALUES 
('João Silva', 'joao.silva@email.com', 'ativo'),
('Maria Oliveira', 'maria.oliveira@email.com', 'inativo'),
('Pedro Santos', 'pedro.santos@email.com', 'ativo');
Com esses dados inseridos, podemos realizar consultas para obter informações sobre os clientes.

Consultas SQL

Selecionar todos os clientes com status ativo
sql
-- Seleciona todos os clientes ativos
SELECT ClienteID, Nome, Email, DataCadastro
FROM Clientes
WHERE Status = 'ativo';

Encontrar um cliente pelo e-mail cadastrado

-- Encontrar cliente pelo email
SELECT ClienteID, Nome, DataCadastro, Status
FROM Clientes
WHERE Email = 'maria.oliveira@email.com';

Contar o número de clientes ativos e inativos

-- Contar número de clientes ativos e inativos
SELECT Status, COUNT(*) AS Total
FROM Clientes
GROUP BY Status;
As consultas fornecem insights importantes sobre o comportamento dos clientes e ajudam na gestão eficiente do banco de dados.
