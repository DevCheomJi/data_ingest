
#Creating a Kafka Topic
<pre><code>


[training@localhost ~]$ kafka-topics --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic weblogs
Created topic "weblogs".

[training@localhost ~]$ kafka-topics --list \
> --zookeeper localhost:2181
weblogs

[training@localhost ~]$ kafka-topics --describe weblogs \
> --zookeeper localhost:2181

Topic:weblogs	PartitionCount:1	ReplicationFactor:1	Configs:
	Topic: weblogs	Partition: 0	Leader: 0	Replicas: 0	Isr: 0
</code></pre>



#Producing and Consuming Messages
<pre><code>

[training@localhost ~]$ kafka-console-producer \
> --broker-list localhost:9092 \
> --topic weblogs
test weblog entry 1
test weblog entry 2



[training@localhost ~]$ kafka-console-consumer \
> --zookeeper localhost:2181 \
> --topic weblogs \
> --from-beginning

test weblog entry 1
test weblog entry 2

</code></pre>
