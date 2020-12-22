# Development Environment with Docker
Quickly Set-up your development environment with docker. All containers are **temporary**, no volume mounted, if you want to persistent containers [see how to mount volume](https://docs.docker.com/storage/volumes/) to containers.

Table of contents:

- [Databases](#databases)
  - [SQL Server](#sql-server)
  - [PostgreSQL](#postgresql)
  - [MongoDB](#mongodb)
- Distributed Caches
  - [Redis](#redis)
- Event Bus
  - [RabbitMQ](#rabbitmq)

---
# Databases

## SQL Server
```shell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=12345678Aa' -p 1433:1433 -d mcr.microsoft.com/mssql/server:2017-CU8-ubuntu
```
- Then go your management IDE and try to connect to `localhost:1433` with **username:** `SA` and **password:** `12345678Aa` 

## PostgreSQL
```shell
docker run --restart unless-stopped --name local-postgres -e POSTGRES_PASSWORD=12345678Aa -p 5432:5432 -d postgres
```
- Then go your management IDE and try to connect to `localhost:5432` with **username:** `postgres` and **password:** `12345678Aa` 

## MongoDB
```shell
docker run --name tmp-mongo --restart unless-stopped -p 27017:27017 -d mongo:latest
```
- Then go your NoSQL Management IDE and try to connect to `localhost:27017` without any credentials.

# Distributed Caches

## Redis

```shell
docker run -p 6379:6379 -d --restart unless-stopped redis
```

# Event Bus

## RabbitMQ

```shell
docker run -d --restart unless-stopped -p 15672:15672 -p 5672:5672 rabbitmq:3-management
```

 - Go [localhost:15672](http://localhost:15672) to check is rabbitmq dashboard works properly.

- Default login credentials: username: guest password: guest
