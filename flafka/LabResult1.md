## bigdata engineering  교육 2차시 수강생:정수현

$DEVSH/scripts/catchup.sh

Please enter the number of the exercise that you want to do.
This script will reset your system to the start state for that exercise.

...
16 Send Web Server Log Messages from Apache Flume to Apache Kafka
17 Write an Apache Spark Streaming Application
18 Process Multiple Batches with Apache Spark Streaming
19 Process Apache Kafka Messages with Apache Spark Streaming

16
Cleaning up your system
Deleted /loudacre
* Advancing through Exercise 1: Query Hadoop Data with Apache Impala
* Advancing through Exercise 2: Access HDFS with the Command Line and Hue
* Advancing through Exercise 3: Run a YARN Job
* Advancing through Exercise 4: Import Data from MySQL Using Apache Sqoop
* Advancing through Exercise 5: Explore RDDs Using the Spark Shell
* Advancing through Exercise 6: Process Data Files with Apache Spark
* Advancing through Exercise 7: Use Pair RDDs to Join Two Datasets
* Advancing through Exercise 8: Write and Run an Apache Spark Application
* Advancing through Exercise 9: Configure an Apache Spark Application
* Advancing through Exercise 10: View Jobs and Stages in the Spark Application UI
* Advancing through Exercise 11: Persist an RDD
* Advancing through Exercise 12: Implement an Iterative Algorithm with Apache Spark
* Advancing through Exercise 13: Use Apache Spark SQL for ETL
* Advancing through Exercise 14: Produce and Consume Apache Kafka Messages
Created topic "weblogs".
* Advancing through Exercise 15: Collect Web Server Logs with Apache Flume

You can now perform the Send Web Server Log Messages from Apache Flume to Apache Kafka exercise.

## Run the Flume Agent
<pre><code>
[training@localhost ~]$ flume-ng agent
--conf /etc/flume-ng/conf
--conf-file $DEVSH/exercises/flafka/spooldir_kafka.conf
--name agent1
-Dflume.root.logger=INFO,console

Info: Sourcing environment configuration script /etc/flume-ng/conf/flume-env.sh
Info: Including Hadoop libraries found via (/usr/bin/hadoop) for HDFS access
Info: Excluding /usr/lib/hadoop/lib/slf4j-api-1.7.5.jar from classpath
Info: Excluding /usr/lib/hadoop/lib/slf4j-log4j12.jar from classpath
Info: Including HBASE libraries found via (/usr/bin/hbase) for HBASE ac

.............
</code></pre>

## Test the Flume Agent Kafka Sink
<pre><code>
[training@localhost ~]$ kafka-console-consumer
--zookeeper localhost:2181
--topic weblogs


[training@localhost flume]$ $DEVSH/exercises/flume/copy-move-weblogs.sh
/flume/weblogs_spooldir

/flume/weblogs_spooldir exists and is not empty, delete contents? (y/n)
y
Copying and moving files to /flume/weblogs_spooldir
</code></pre>

## Kafka Consumer 에서 동작
<pre><code>
234.178.182.138 - 183 [15/Mar/2014:00:01:46 +0100] "GET /KBDOC-00044.html HTTP/1.0" 200 3728 "http://www.loudacre.com"  "Loudacre CSR Browser"
234.178.182.138 - 183 [15/Mar/2014:00:01:46 +0100] "GET /theme.css HTTP/1.0" 200 671 "http://www.loudacre.com"  "Loudacre CSR Browser"
17.47.5.64 - 11435 [15/Mar/2014:00:01:37 +0100] "GET /KBDOC-00026.html HTTP/1.0" 200 15817 "http://www.loudacre.com"  "Loudacre Mobile Browser iFruit 1"
17.47.5.64 - 11435 [15/Mar/2014:00:01:37 +0100] "GET /theme.css HTTP/1.0" 200 17662 "http://www.loudacre.com"  "Loudacre Mobile Browser iFruit 1"
12.92.63.115 - 74968 [15/Mar/2014:00:01:29 +0100] "GET /KBDOC-00261.html HTTP/1.0" 200 14431 "http://www.loudacre.com"  "Loudacre Mobile Browser Titanic 4000"
12.92.63.115 - 74968 [15/Mar/2014:00:01:29 +0100] "GET /theme.css HTTP/1.0" 200 16736 "http://www.loudacre.com"  "Loudacre Mobile Browser Titanic 4000"
227.1.159.172 - 9 [15/Mar/2014:00:01:16 +0100] "GET /KBDOC-00192.html HTTP/1.0" 200 5937 "http://www.loudacre.com"  "Loudacre CSR Browser"
227.1.159.172 - 9 [15/Mar/2014:00:01:16 +0100] "GET /theme.css HTTP/1.0" 200 16316 "http://www.loudacre.com"  "Loudacre CSR Browser"
22.252.151.164 - 23251 [15/Mar/2014:00:00:30 +0100] "GET /KBDOC-00150.html HTTP/1.0" 200 19203 "http://www.loudacre.com"  "Loudacre Mobile Browser Sorrento F11L"
22.252.151.164 - 23251 [15/Mar/2014:00:00:30 +0100] "GET /theme.css HTTP/1.0" 200 10684 "http://www.loudacre.com"  "Loudacre Mobile Browser Sorrento F11L"
</code></pre>
