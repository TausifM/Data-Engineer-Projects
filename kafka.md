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


## AWS SSH Kafka Installation and Java
1. wget https://archive.apache.org/dist/kafka/3.0.0/kafka_2.13-3.0.0.tgz
2. tar -xvf kafka_2.13-3.0.0.tgz
4. cd kafka_2.13-3.0.0
3. java -version
4. sudo yum install java-1.8.0-amazon-corretto.x86_64


cd kafka_2.13-3.0.0

Start Zoo-keeper:
-------------------------------
bin/zookeeper-server-start.sh config/zookeeper.properties

Open another window to start kafka
But first ssh to to your ec2 machine as done above


Start Kafka-server:
----------------------------------------
Duplicate the session & enter in a new console --
export KAFKA_HEAP_OPTS="-Xmx256M -Xms128M"
cd kafka_2.13-3.0.0
bin/kafka-server-start.sh config/server.properties

It is pointing to private server , change server.properties so that it can run in public IP 

To do this , you can follow any of the 2 approaches shared belwo --
Do a "sudo nano config/server.properties" - change ADVERTISED_LISTENERS to public ip of the EC2 instance


Create the topic:
-----------------------------
Duplicate the session & enter in a new console --
cd kafka_2.13-3.0.0
bin/kafka-topics.sh --create --topic demo_testing2 --bootstrap-server 18.209.66.89:9092 --replication-factor 1 --partitions 1

Start Producer:
--------------------------
bin/kafka-console-producer.sh --topic demo_testing2 --bootstrap-server 18.209.66.89:9092 

Start Consumer:
-------------------------
Duplicate the session & enter in a new console --
cd kafka_2.13-3.0.0
bin/kafka-console-consumer.sh --topic demo_testing2 --bootstrap-server 18.209.66.89:9092