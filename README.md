# Microserviço de Compra e Pagamento

Este repositório contém dois microserviços: **ms-compra** e **ms-pagamento**, que funcionam de forma independente e se comunicam via RabbitMQ, para testar a funcionalidade de Doação.

## Configuração do Banco de Dados

### Criar Bancos de Dados no MySQL
Execute os seguintes comandos no MySQL para criar os bancos de dados:

```sql
CREATE DATABASE ms_compra;
CREATE DATABASE ms_pagamento;
````

## Executando o Microserviço de Compra

### Passos:
1. Rodar o arquivo **MsCompraApplication**.
2. Testar a funcionalidade de doação em um pedido via Swagger:

   - **URL:** [http://localhost:8081/api](http://localhost:8081/api)

### Exemplo de requisição JSON:

```json
{
    "usuarioId": 1,
    "total": 50,
    "itensPedido": [
        {
            "nome": "Camisa Preta",
            "preco": 40.00,
            "quantidade": 1,
            "doacao": false
        },
        {
            "nome": "Doação para ONG",
            "preco": 10.00,
            "quantidade": 1,
            "doacao": true
        }
    ]
}
````

## Executando o Microserviço de Pagamento

### Passos:
1. Rodar o arquivo **MsPagamentoApplication**.
2. Testar a funcionalidade de doação direta no pagamento via Swagger:

   - **URL:** [http://localhost:8082/api](http://localhost:8082/api)

### Exemplo de requisição JSON:

```json
{
  "nomeDoador": "Erick Calazães",
  "documentoDoador": "14019044759",
  "valor": 150
}
````

## Configuração do RabbitMQ

### Subir o RabbitMQ no Docker

Execute o seguinte comando para iniciar o RabbitMQ via Docker:

```sh
docker run -d --name rabbitmq -p 15672:15672 -p 5672:5672 rabbitmq:management
````

### Acessando o painel de gerenciamento do RabbitMQ

- **URL:** [http://localhost:15672/](http://localhost:15672/)  
- **Usuário:** `guest`  
- **Senha:** `guest`  



