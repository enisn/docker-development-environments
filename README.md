# Docker Development Environments
Quickly Set-up your development environment with docker.

Table of contents:

- [Databases](#databases)
 - [SQL Server](#sql-server)
 - [PostgreSQL](#postgresql)
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

## PostgreSQL
```shell
docker run --restart unless-stopped --name local-postgres -e POSTGRES_PASSWORD=12345678Aa -p 5432:5432 -d postgres
```

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
