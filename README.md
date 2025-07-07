CREATE DATABASE IF NOT EXISTS FastFood;
USE FastFood;

-- Tabela Clientes
CREATE TABLE IF NOT EXISTS Clientes (
    idClientes INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    NomeClientes VARCHAR(100) NOT NULL,
    Telefone VARCHAR(20),
    Email VARCHAR(100) NOT NULL,
    Endereco VARCHAR(250) NOT NULL
);

-- Inserção de dados na tabela Clientes
INSERT INTO Clientes (NomeClientes, Telefone, Email, Endereco) VALUES 
('Augusto','45 99769-6578','augusto2006@gmail.com','Rua Otávio Portes 2765'),
('Bruno','45 99969-5578','bruno.do.grau@gmail.com','Rua Francisco Fernandes 1495'),
('Fernando','45 99799-5418','fernandinho@gmail.com','Rua Conceição da Maria 5675'),
('Henrique','45 99976-1083','henrique.silva09@gmail.com','Rua Catanduva Mendes 4927'),
('Natan','45 99779-6578','natan@gmail.com','Rua Constantino bananinha 7777'),
('Pedro','45 98997-5868','pedrinho@gmail.com','Rua mandinga da cruz 9628'),
('Daniel','45 99829-6118','danielzinhofado2002@gmail.com','Rua Javier dos santos 7775');

-- Tabela Produtos
CREATE TABLE IF NOT EXISTS Produtos (
    idProdutos BIGINT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    NomeProduto VARCHAR(150) NOT NULL,
    preco DECIMAL(6,2) NOT NULL
);

-- Tabela Pedidos
CREATE TABLE IF NOT EXISTS Pedidos (
    idPedidos INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    idCliente INT NOT NULL,
    idProduto BIGINT NOT NULL,
    status ENUM('Pronto', 'Em preparo', 'Cancelado', 'Entregue'),
    FOREIGN KEY (idCliente) REFERENCES Clientes(idClientes),
    FOREIGN KEY (idProduto) REFERENCES Produtos(idProdutos)
);
