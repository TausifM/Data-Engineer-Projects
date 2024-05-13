# Kafka Configurations

1. Download Scala Kafka Files from https://kafka.apache.org/downloads
2. Go to server.properties file in config change logs file location to c:/kafka/kafka-logs
3. Go to zookeeper.properties file their dataDir path change to c:/kafka/zookeeper-logs
4. In kafka folder in cmd .\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
5. In kafka folder in cmd .\bin\windows\kafka-server-start.bat .\config\server.properties
6. Go to bin/windows create topic kafka-topics.bat --create --bootstrap-server localhost:9092 --topic test
7. Start Consumer kafka-console-consumer.bat --topic test --bootstrap-server localhost:9092 --from-beginning
8. Start Producer kafka-console-producer.bat --broker-list localhost:9092 --topic test
9. Do not close any cmd window
