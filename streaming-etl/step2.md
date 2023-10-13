## Create the MySQL connector

Now that Redpanda and Debezium's up and running, let's go ahead and create the MySQL connector.

```
docker-compose exec debezium curl -i -X POST -H "Accept:application/json" -H "Content-Type:application/json" localhost:8083/connectors/ -d '
 {
  "name": "mysql-connector",
  "config": {
    "connector.class": "io.debezium.connector.mysql.MySqlConnector",
    "tasks.max": "1",
    "database.hostname": "mysql",
    "database.port": "3306",
    "database.user": "debezium",
    "database.password": "dbz",
    "database.server.id": "184054",
    "topic.prefix": "dbz",
    "database.include.list": "masterclass",
    "schema.history.internal.kafka.bootstrap.servers": "redpanda:9092",
    "schema.history.internal.kafka.topic": "schemahistory.inventory",
    "transforms":"unwrap",
    "transforms.unwrap.type":"io.debezium.transforms.ExtractNewRecordState",
    "transforms.unwrap.drop.tombstones":false,
    "transforms.unwrap.delete.handling.mode":"rewrite"
  }
}'
```{{exec}}