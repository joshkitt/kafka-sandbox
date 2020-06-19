## Kafka streaming sandbox
See documentation: https://kafka.apache.org/25/documentation/streams/tutorial

## Notes
compile and run with Java 8
```shell script
mvn clean pacakge
```

## Start Zookeeper and Kafka
```shell script
zookeeper-server-start /usr/local/etc/kafka/zookeeper.properties & kafka-server-start /usr/local/etc/kafka/server.properties
```

## Start producer
```shell script
kafka-console-producer --bootstrap-server localhost:9092 --topic streams-plaintext-input
```

## Run examples
Each example has a main class. Run with Maven, Run in IDE, etc.

## Start consumers
Start consumers in different shells
```shell script
kafka-console-consumer --bootstrap-server localhost:9092 --topic streams-linesplit-output

kafka-console-consumer --bootstrap-server localhost:9092 --topic streams-pipe-output

kafka-console-consumer --bootstrap-server localhost:9092 \
    --topic streams-wordcount-output \
    --from-beginning \
    --formatter kafka.tools.DefaultMessageFormatter \
    --property print.key=true \
    --property print.value=true \
    --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer \
    --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer
```
