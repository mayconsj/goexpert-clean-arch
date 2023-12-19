# Desafio Go Expert - Clean Architecture

Agora é a hora de botar a mão na massa. Pra este desafio, você precisará criar o usecase de listagem das orders.

Esta listagem precisa ser feita com:

- Endpoint REST (GET /order)

- Service ListOrders com GRPC

- Query ListOrders GraphQL

Não esqueça de criar as migrações necessárias e o arquivo api.http com a request para criar e listar as orders.

## Executar Projeto

Iniciar o ambiente com MySQL e do RabbitMQ:

```bash
docker-compose up -d
```

Executar as migrações do banco de dados no diretório goexpert-clean-arch:
obs: Instalar CLI https://github.com/golang-migrate/migrate/tree/master/cmd/migrate

```bash
make migration
```

## Iniciar API

Executar no diretório goexpert-clean-arch:

```bash
cd cmd/ordersystem && go run main.go wire_gen.go
```


- Rest em http://localhost:8000:
    - Request no diretório `/api`;
    - Extensão VSCode utilizada REST Client

- GraphQL em http://localhost:8080:
    ```graphql
    mutation createOrder {
        createOrder(input: {
            id: "change-id",
            Price: 10.0,
            Tax: 0.5
        }) {
            id Price Tax FinalPrice
        }
    }

    query orders {
        listOrders {
            id Price Tax FinalPrice
        }
    }
    ```

- gRPC na porta 50051:
    - CLI gRPC https://github.com/ktr0731/evans.