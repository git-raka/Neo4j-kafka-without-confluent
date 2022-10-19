# Kafka stream neo4j without confluent platform
In this tutorial you can see how to stream data from postgresql to neo4j database

### Preparation 
Assume you has done installed kafka,If not done yet you can view this link for set up kafka :
[Kafka Installation](https://github.com/git-raka/Kafka-without-confluent#kafka-without-confluent-ad-optional-kafdrop)

### Set up kafka connect 
```
mkdir /home/kafka/connect
```

### Download plugin connector
this plugin connect is from [conker84](https://github.com/neo4j-contrib/neo4j-streams/releases) thanks to creating this awesome plugin
```
wget https://github.com/neo4j-contrib/neo4j-streams/releases/download/4.1.2/neo4j-kafka-connect-neo4j-2.0.2-kc-oss.zip 
unzip neo4j-kafka-connect-neo4j-2.0.2-kc-oss.zip
```

### Download Debezium Connector
```
cd /home/kafka/connect 
wget https://repo1.maven.org/maven2/io/debezium/debezium-connector-postgres/1.9.6.Final/debezium-connector-postgres-1.9.6.Final-plugin.tar.gz
```

### Set up connect configuration
a properties file you can find in <kafka_home>/config
```
cp connect-distributed.properties stream.properties
```
edit stream.properties file, and append this row to connect directory

```
vi /home/kafka/config/stream.properties
```
and append this row to connect directory
```
plugin.path=/home/kafka/connect
```
### Run kafka connect 
```
./home/kafka/bin/connect-distributed.sh /home/kafka/config/testing.properties
```
### Create debezium and neo4j configuration
This file is create for connection string to postgresql and neo4j database

Create configuration file called *postgresql.conf* and append this line :

https://github.com/git-raka/Neo4j-kafka-without-confluent/blob/a27752ad91deb35d6b3d8b7c4d7228571aead690/postgresql.json#L1-L19

Create configuration file called *neo4j.conf* and append this line :

https://github.com/git-raka/Neo4j-kafka-without-confluent/blob/a27752ad91deb35d6b3d8b7c4d7228571aead690/neo4j.json#L1-L22





