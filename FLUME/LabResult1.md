##bigdata engineering  교육 2차시 수강생:정수현
## Config  파일(기존 예제 파일에서 정보들 추가)
<img src="https://github.com/pjpjpjq/data_ingest/blob/master/FLUME/config.JPG?raw=true"></img>

<pre><code>
# spooldir.conf: A Spooling Directory Source

# Name the components on this agent
agent1.sources = webserver-log-source
agent1.sinks = hdfs-sink
agent1.channels = memory-channel

# Describe/configure the source
agent1.sources.webserver-log-source.type = Netcat
agent1.sources.webserver-log-source.bind = localhost
agent1.sources.webserver-log-source.port = 44444
agent1.sources.webserver-log-source.spoolDir = /flume/weblogs_spooldir
agent1.sources.webserver-log-source.channels = memory-channel

# Describe the sink
agent1.sinks.hdfs-sink.type = logger
agent1.sinks.hdfs-sink.hdfs.path = /loudacre/weblogs_flume/
agent1.sinks.hdfs-sink.channel = memory-channel
agent1.sinks.hdfs-sink.hdfs.rollInterval = 0
agent1.sinks.hdfs-sink.hdfs.rollSize = 524288
agent1.sinks.hdfs-sink.hdfs.rollCount = 0
agent1.sinks.hdfs-sink.hdfs.fileType = DataStream

# Use a channel which buffers events in memory
agent1.channels.memory-channel.type = memory
agent1.channels.memory-channel.capacity = 1000
agent1.channels.memory-channel.transactionCapacity = 100
</code></pre>

## agent 커맨드 및 결과
<img src="https://github.com/pjpjpjq/data_ingest/blob/master/FLUME/agent.JPG?raw=true" width="90%"></img>

<pre><code>

</code></pre>

## telnet 결과
<img src="https://github.com/pjpjpjq/data_ingest/blob/master/FLUME/telnetResult.JPG?raw=true" width="90%"></img>

<pre><code>

</code></pre>
