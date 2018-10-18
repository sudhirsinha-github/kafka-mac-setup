# kafka-setup
Step by step for Kafka setup in mac in simple way


Prerequisite -> Homebrew is installed and updated (https://brew.sh/ )


1. Install Kafka (Zookeeper will be installed as part of this)
    ```
    brew install kafka
    
    ```

2. Start the ZooKeeper service

    ```
    brew services start zookeeper    
    ```

3. Start the Kafka service

    ```
    brew services start kafka    
    ```
    
4. Make sure services are started

```
brew services list
```

```
Name           Status  User   Plist
docker-machine stopped
elasticsearch  stopped
kafka          started sudhir /Users/sudhir/Library/LaunchAgents/homebrew.mxcl.kafka.plist
mongodb        stopped
mysql          stopped
rabbitmq       stopped
redis          stopped
zookeeper      started sudhir /Users/sudhir/Library/LaunchAgents/homebrew.mxcl.zookeeper.plist

```

5. Create a topic named “channel”

```
kafka-topics --create --zookeeper localhost:2181 --replication-factor 1 --partitions 4 --topic channel

Created topic "channel".

```

6. Start the producer in a Terminal 

```
kafka-console-producer --broker-list localhost:9092 --topic channel

> type new message 
> hi
```

7. Let the producer terminal opened and create a new terminal for consumer terminal 

```
kafka-console-consumer --bootstrap-server localhost:9092 --from-beginning --topic channel

type new message 
hi
// all messages typed /copied on producer terminal will be received.
```


* Working steps , let me know if you are facing issue here. 
