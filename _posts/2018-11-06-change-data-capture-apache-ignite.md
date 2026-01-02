---
title: Change Data Capture --> Kafka --> Go Consumer --> Apache Ignite --> Zeppelin
layout: post
tags: ["tech"]
---

Setting up a realtime reporting framework with MySQL, Kafka Connect, Apache Kafka, Golang Consumer, Apache Ignite, Apache Zeppelin
<!--excerpt-->

### Kafka, Zookeeper on Docker, consuming from Go program in Docker

#### Get IP

`ipconfig getifaddr en0`

#### IP 

`10.251.69.52`


### Run Zookeeper

`docker run -d --name zookeeper -p 2181:2181 jplock/zookeeper`

#### Run Kafka

`docker run -d --name kafka -p 7203:7203 -p 9092:9092 -e KAFKA_ADVERTISED_HOST_NAME=10.251.69.52 -e ZOOKEEPER_IP=10.251.69.52 ches/kafka`

#### Create Topic

`docker run --rm ches/kafka kafka-topics.sh --create --topic senz --replication-factor 1 --partitions 1 --zookeeper 10.251.69.52:2181`

#### List Topics

`docker run --rm ches/kafka kafka-topics.sh --list --zookeeper 10.251.69.52:2181`

#### Create Publisher

`docker run --rm --interactive ches/kafka kafka-console-producer.sh --topic senz --broker-list 10.251.69.52:9092`

or

`kafka-console-producer --topic senz --broker-list 10.251.69.52:9092`

#### Create Consumer

`docker run --rm ches/kafka kafka-console-consumer.sh --topic senz --from-beginning --zookeeper 10.251.69.52:2181`


#### Build Golang Docker consumer

```
cd /repos/irl/consumer
docker build --tag zexyphantom/conzumer:1.0 .
```

#### Run Golang Docker Consumer

`docker run -it --name conzumer zexyphantom/conzumer:1.0`

-------------------------



### Debezium 

#### Start Zookeeper

`docker run -it --rm --name zookeeper -p 2181:2181 -p 2888:2888 -p 3888:3888 debezium/zookeeper:0.8`


#### Start Kafka
`docker run -it --rm --name kafka -p 9092:9092 --link zookeeper:zookeeper debezium/kafka:0.8`

#### Start MySQL
`docker run -it --rm --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=debezium -e MYSQL_USER=mysqluser -e MYSQL_PASSWORD=mysqlpw debezium/example-mysql:0.8`

#### Start Kafka Connect

`docker run -it --rm --name connect -p 8083:8083 -e GROUP_ID=1 -e CONFIG_STORAGE_TOPIC=my_connect_configs -e OFFSET_STORAGE_TOPIC=my_connect_offsets --link zookeeper:zookeeper --link kafka:kafka --link mysql:mysql debezium/connect:0.8`

#### Activate the connector
```
curl -X POST \
  http://localhost:8083/connectors/ \
  -H 'Accept: application/json' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 53a55b1b-eb22-49f3-8fbf-a80d485ff348' \
  -d '{ "name": "inventory-connector", "config": { "connector.class": "io.debezium.connector.mysql.MySqlConnector", "tasks.max": "1", "database.hostname": "mysql", "database.port": "3306", "database.user": "debezium", "database.password": "dbz", "database.server.id": "184054", "database.server.name": "dbserver1", "database.whitelist": "inventory", "database.history.kafka.bootstrap.servers": "kafka:9092", "database.history.kafka.topic": "dbhistory.inventory" } }'
  ```
  
  or in Postman call `localhost:8083/connectors/`
  ```
  { "name": "inventory-connector", "config": { "connector.class": "io.debezium.connector.mysql.MySqlConnector", "tasks.max": "1", "database.hostname": "mysql", "database.port": "3306", "database.user": "debezium", "database.password": "dbz", "database.server.id": "184054", "database.server.name": "dbserver1", "database.whitelist": "inventory", "database.history.kafka.bootstrap.servers": "kafka:9092", "database.history.kafka.topic": "dbhistory.inventory" } }
  ```


### Start Ignite
```
/repos/ignite-go-client/testdata
rm -rf /repos/apache-ignite-fabric-2.6.0-bin/work/ && /repos/apache-ignite-fabric-2.6.0-bin/bin/ignite.sh ./custom-realtime.xml
```

### Activate Ignite
```
cd /repos/apache-ignite-fabric-2.6.0-bin/bin
./control.sh --activate --user ignite --password ignite
```

### Start Zeppelin
```
/repos/zeppelin-0.8.0-bin-all/bin
./zeppelin-daemon.sh start
```

### Start Docker Consumer
```
/repos/irl/consumer
docker run --rm --name rtconz   zexyphantom/conzumer
```

### Stop Docker Containers
```
docker stop rtconz connect mysql kafka zookeeper
```
