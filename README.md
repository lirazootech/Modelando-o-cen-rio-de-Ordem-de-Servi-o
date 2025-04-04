# Modelando o Cenário de Ordem de Serviço

## 📋 Descrição do Projeto
Este projeto tem como objetivo modelar e implementar um sistema de **ordem de serviço** usando boas práticas de modelagem de dados. A ideia é criar um banco de dados estruturado que gerencie clientes, pedidos, responsáveis e serviços, com relacionamentos claros entre essas entidades.

## 📐 Estrutura Conceitual
A modelagem segue os seguintes conceitos principais:
- **Cliente**: Responsável por iniciar o processo com a realização de um pedido.
- **Pedido**: Representa a solicitação do cliente, que será analisada e resultará em serviços específicos.
- **Responsável**: Designado para analisar os pedidos e supervisionar os serviços.
- **Serviço**: Representa as tarefas executadas com base nos pedidos analisados.

## 🛠️ Entidades e Relacionamentos
### **Entidades**
- **Cliente**: Contém informações como nome, endereço, telefone e e-mail.
- **Pedido**: Inclui descrição, status, data e horário do pedido, além de um vínculo com o cliente.
- **Responsável**: Registra o responsável por cada pedido e os serviços relacionados.
- **Serviço**: Contém os dados das atividades executadas, vinculadas ao pedido e ao responsável.

### **Relacionamentos**
- **Cliente gera Pedido** (1:N).
- **Pedido é analisado por Responsável** (N:N).
- **Pedido gera Serviço** (1:N).
- **Serviço é supervisionado por Responsável** (1:N).

## 📦 Tecnologias Utilizadas
- **MySQL**: Banco de dados relacional para criar e gerenciar tabelas e relacionamentos.
- **Workbench**: Ferramenta gráfica para modelagem e execução de comandos SQL.

## 💡 Arquitetura do Banco de Dados
As tabelas possuem características como:
- Chaves primárias auto incrementadas.
- Chaves estrangeiras para garantir integridade referencial.
- Tipos de dados otimizados (VARCHAR, TIMESTAMP, ENUM, etc.).
- Estrutura escalável para suportar futuras alterações e expansões.

## 📄 Comandos Importantes
Alguns exemplos dos comandos SQL que eu utilizei, como:
### Criação de Tabelas com Chaves Primárias e Estrangeiras:
```sql
CREATE TABLE Responsavel (
    ID_responsavel INT NOT NULL AUTO_INCREMENT,
    nome VARCHAR(100),
    cargo VARCHAR(50),
    contato VARCHAR(50),
    ID_pedido INT NOT NULL,
    PRIMARY KEY (ID_responsavel),
    FOREIGN KEY (ID_pedido) REFERENCES Pedido(ID_pedido)
);
```
- Definição de chaves primárias e estrangeiras.
- Uso de opções como `NOT NULL`, `UNIQUE` e `FOREIGN KEY`.

### Destaque: Uso de ON DELETE CASCADE e ON UPDATE CASCADE:

```sql
CREATE TABLE Cliente (
    ID_cliente INT NOT NULL AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    telefone VARCHAR(15),
    PRIMARY KEY (ID_cliente)
);

CREATE TABLE Pedido (
    ID_pedido INT NOT NULL AUTO_INCREMENT,
    descricao VARCHAR(500),
    data_horario TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    ID_cliente INT NOT NULL,
    PRIMARY KEY (ID_pedido),
    FOREIGN KEY (ID_cliente) REFERENCES Cliente(ID_cliente) ON DELETE CASCADE ON UPDATE CASCADE
);
```

**ON DELETE CASCADE:** Garante que, ao excluir um cliente, todos os pedidos associados a ele também sejam excluídos automaticamente.

**ON UPDATE CASCADE:** Atualiza automaticamente o valor da chave estrangeira em Pedido caso o ID_cliente seja alterado na tabela Cliente. 


## 🌟 Contribuições
Sinta-se à vontade para sugerir melhorias ou compartilhar suas ideias!

  <p align="center">
  Copyright © 2024. Desenvolvido com 🧡 por <a  href="https://lirazootech.vercel.app/">Thays Lira</a>.
  </p>
