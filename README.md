# Basic Commands for Apache Kafka

## Install Kafka and ZooKeeper
### Option 1: Download from the official website
[Download Kafka](https://kafka.apache.org/downloads)
### Option 2: Using a package manager
#### Linux
sudo apt-get update  
sudo apt-get install zookeeper  
sudo apt-get install kafka
#### macOS (using Homebrew)
brew install kafka  
brew install zookeeper

## Start the Services
### Start the ZooKeeper service
bin/zookeeper-server-start.sh config/zookeeper.properties
### Start the Kafka broker service
bin/kafka-server-start.sh config/server.properties

## Topic Management
### Create a topic to store events
bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic quickstart-events
##### To change parameters, modify the file \"config/server.properties\" in the Kafka directory

### Check topic creation
bin/kafka-topics.sh --list --bootstrap-server localhost:9092  
bin/kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092

## Produce Events
### Write events into the topic
bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092  
Event1  
Event2  

## Consume Events
### Read the events
#### From the beginning
bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092
#### Only new events
bin/kafka-console-consumer.sh --topic quickstart-events --bootstrap-server localhost:9092
