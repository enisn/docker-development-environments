# Development Environment with Docker
Quickly Set-up your development environment with docker. All containers are **temporary**, no volume mounted, if you want to persistent containers [see how to mount volume](https://docs.docker.com/storage/volumes/) to containers.

Table of contents:

- [Databases](#databases)
  - [SQL Server](#sql-server)
  - [PostgreSQL](#postgresql)
  - [MySQL](#mysql)
  - [MongoDB](#mongodb)
- Distributed Caches
  - [Redis](#redis)
- Event Bus
  - [RabbitMQ](#rabbitmq)

---
# Databases

## SQL Server
Original Windows Version:
```shell
docker run --name tmp-sqlserver --restart unless-stopped -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=1q2w3E*' -p 1433:1433 -d mcr.microsoft.com/mssql/server:2017-CU8-ubuntu
```

SqlServer Linux Version:
```shell
docker run --name tmp-sqlserver -d --restart unless-stopped -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=1q2w3E*' -p 1433:1433 microsoft/mssql-server-linux
```

Azure-Sql for Apple M1 (Silicon)
```shell
docker run --name tmp-sqlserver --restart unless-stopped -d --cap-add SYS_PTRACE -e 'ACCEPT_EULA=1' -e 'MSSQL_SA_PASSWORD=1q2w3E*' -p 1433:1433 mcr.microsoft.com/azure-sql-edge
```

- Then go your management IDE and try to connect to `localhost:1433` with **username:** `SA` and **password:** `1q2w3E*` 

## PostgreSQL
```shell
docker run --name tmp-postgres --restart unless-stopped -e POSTGRES_PASSWORD=1q2w3E* -p 5432:5432 -d postgres
```
- Then go your management IDE and try to connect to `localhost:5432` with **username:** `postgres` and **password:** `1q2w3E*` 

## MySql
```shell
docker run --name tmp-mysql --restart unless-stopped -e 'MYSQL_ROOT_PASSWORD=12345678Aa' -p 3306:3306 -d mysql:5.7
```

For Apple M1 (Silicon)
```Shell
docker run --name tmp-mysql --restart unless-stopped -e 'MYSQL_ROOT_PASSWORD=1q2w3E*' -p 3306:3306 --platform linux/x86_64 -d mysql:5.7
```

- Then open management IDE and try to connect to `localhost:3306` with **username:** root and **password:** `1q2w3E*`

## MongoDB
```shell
docker run --name tmp-mongo --restart unless-stopped -p 27017:27017 -d mongo:latest
```
- Then go your NoSQL Management IDE and try to connect to `localhost:27017` without any credentials.

# Distributed Caches

## Redis

```shell
docker run --name tmp-redis -p 6379:6379 -d --restart unless-stopped redis
```

# Event Bus

## RabbitMQ

```shell
docker run --name tmp-rabbitmq -d --restart unless-stopped -p 15672:15672 -p 5672:5672 rabbitmq:3-management
```

 - Go [localhost:15672](http://localhost:15672) to check is rabbitmq dashboard works properly.

- Default login credentials: username: guest password: guest
