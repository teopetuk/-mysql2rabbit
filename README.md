# -mysql2rabbit

Конфиги для прототипа публикации в рэббит изменений в мускуле.

Содержит 3 отдельных контейнера:
  - debezium-server
  - mysql
  - rabbit

## Как запустить

Старт контейнеров -- ```docker-compose up -d``` для каждого контейнера.
  
Дополнительно создавал отдельную docker-сеть, куда прокидывал все 3 контейнера:
```
    docker network create common-network
    docker network connect common-network debezium-server
    docker network connect common-network mysql
    docker network connect common-network rabbitmq
    docker network inspect common-network
```

## Создание стендовой базы из sql-файла
```
    docker exec -it mysql sh
    mysql -u root -p12345678 --database mysqlxz < /docker-entrypoint-initdb.d/testhouses.sql

```
