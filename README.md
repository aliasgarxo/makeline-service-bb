
# Makeline Service for BestBuy

This is a Golang-based API designed for the Best Buy order management system. It processes customer orders from the RabbitMQ queue and updates their status in the database.

## Prerequisites

- [Go](https://golang.org/doc/install)
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [MongoSH](https://docs.mongodb.com/mongodb-shell/install/)

## Message Queue Options

The app supports RabbitMQ or Azure Service Bus using AMQP 1.0. To connect, provide the appropriate environment variables.

### Option 1: RabbitMQ

To use RabbitMQ, run the Docker Compose file included in the project.

```bash
docker compose up -d
```

Set the RabbitMQ environment variables:

```bash
export ORDER_QUEUE_URI=amqp://localhost
export ORDER_QUEUE_USERNAME=username
export ORDER_QUEUE_PASSWORD=password
export ORDER_QUEUE_NAME=orders
```

### Option 2: Azure Service Bus

Follow the steps to configure Azure Service Bus as described in the full documentation.

## Database Options

The service supports MongoDB or Azure CosmosDB. Configure the database using the appropriate environment variables.

### Option 1: MongoDB

```bash
export ORDER_DB_URI=mongodb://localhost:27017
export ORDER_DB_NAME=orderdb
export ORDER_DB_COLLECTION_NAME=orders
```

### Option 2: Azure CosmosDB

Follow the detailed CosmosDB configuration steps from the project documentation.

## Running the app

Clone the repository, navigate to the `makeline-service` directory, and run:

```bash
go get .
go run .
```

The app will start and display:

```text
[GIN-debug] Listening and serving HTTP on :3001
```

Use the `test-makeline-service.http` file to test the API with the REST Client extension in VS Code.

## Viewing Orders

### MongoDB

```bash
mongo

# Switch to the database
use orderdb

# List collections and view orders
db.orders.find()
```
