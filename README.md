# Apache-Kafka

- Start up the Zookeeper

zookeeper-server-start.bat ..\..\config\zookeeper.properties

- Start up the Kafka Broker.

kafka-server-start.bat ..\..\config\server.properties

- Topic Creation

kafka-topics.bat --create --topic test-topic -zookeeper localhost:2181 --replication-factor 1 --partitions 4

- List all topics

kafka-topics.bat --bootstrap-server localhost:9092 --list
kafka-topics.bat --bootstrap-server localhost:9092 --describe --topic <topic-name>
  
- Alter the partitions of a topic
  
kafka-configs.bat --bootstrap-server localhost:9092 --alter --topic test-topic --partitions 40
  
- Instantiate a Console Producer
 
  Without Key 
  <br/>  kafka-console-producer.bat --broker-list localhost:9092 --topic test-topic

  With Key
  <br/> kafka-console-producer.bat --broker-list localhost:9092 --topic test-topic --property "key.separator=-" --property "parse.key=true"
  
- Instantiate a Console Consumer 
  
  Without Key
   <br/> kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic test-topic --from-beginning
  
  With Key
   <br/> kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic test-topic --from-beginning -property "key.separator= - " --property "print.key=true"
