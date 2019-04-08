
[training@localhost sqoop import --connect jdbc:mysql://localhost/loudacre --username training --password training --table accounts --where "state='CA'" --columns "acct_num, first_name, last_name" --fields-terminated-by "\t" --target-dir /loudacre/accounts/CA --as-avrodatafile --compression-codec org.apache.hadoop.io.compress.SnappyCodec


19/04/07 23:18:17 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 23:18:17 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 23:18:17 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/07 23:18:17 INFO tool.CodeGenTool: Beginning code generation
19/04/07 23:18:18 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:18:18 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:18:18 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/a7fb5f63c6037f9389cb790dc866b637/accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/07 23:18:20 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/a7fb5f63c6037f9389cb790dc866b637/accounts.jar
19/04/07 23:18:20 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/07 23:18:20 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/07 23:18:20 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/07 23:18:20 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/07 23:18:20 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/07 23:18:20 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/07 23:18:20 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/07 23:18:21 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:18:21 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:18:21 INFO mapreduce.DataDrivenImportJob: Writing Avro schema file: /tmp/sqoop-training/compile/a7fb5f63c6037f9389cb790dc866b637/accounts.avsc
19/04/07 23:18:21 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/07 23:18:21 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/07 23:18:23 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/07 23:18:23 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts` WHERE ( state='CA' )
19/04/07 23:18:23 INFO db.IntegerSplitter: Split size: 32439; Num splits: 4 from: 1 to: 129760
19/04/07 23:18:23 INFO mapreduce.JobSubmitter: number of splits:4
19/04/07 23:18:24 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554697650481_0010
19/04/07 23:18:24 INFO impl.YarnClientImpl: Submitted application application_1554697650481_0010
19/04/07 23:18:24 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554697650481_0010/
19/04/07 23:18:24 INFO mapreduce.Job: Running job: job_1554697650481_0010
19/04/07 23:18:32 INFO mapreduce.Job: Job job_1554697650481_0010 running in uber mode : false
19/04/07 23:18:32 INFO mapreduce.Job:  map 0% reduce 0%
19/04/07 23:18:38 INFO mapreduce.Job:  map 25% reduce 0%
19/04/07 23:18:44 INFO mapreduce.Job:  map 50% reduce 0%
19/04/07 23:18:51 INFO mapreduce.Job:  map 75% reduce 0%
19/04/07 23:18:57 INFO mapreduce.Job:  map 100% reduce 0%
19/04/07 23:18:57 INFO mapreduce.Job: Job job_1554697650481_0010 completed successfully
19/04/07 23:18:57 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=563552
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=470
		HDFS: Number of bytes written=1350990
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=18229
		Total vcore-seconds taken by all map tasks=18229
		Total megabyte-seconds taken by all map tasks=4666624
	Map-Reduce Framework
		Map input records=92416
		Map output records=92416
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=289
		CPU time spent (ms)=6690
		Physical memory (bytes) snapshot=611889152
		Virtual memory (bytes) snapshot=8288874496
		Total committed heap usage (bytes)=251920384
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=1350990
19/04/07 23:18:57 INFO mapreduce.ImportJobBase: Transferred 1.2884 MB in 35.4198 seconds (37.2483 KB/sec)
19/04/07 23:18:57 INFO mapreduce.ImportJobBase: Retrieved 92416 records.


avro-tools tojson hdfs://localhost/loudacre/accounts/CA/part-m-00000.avro | tail
log4j:WARN No appenders could be found for logger (org.apache.hadoop.metrics2.lib.MutableMetricsFactory).
log4j:WARN Please initialize the log4j system properly.
log4j:WARN See http://logging.apache.org/log4j/1.2/faq.html#noconfig for more info.
{"acct_num":{"int":32426},"first_name":{"string":"Dorothy"},"last_name":{"string":"Thompson"}}
{"acct_num":{"int":32428},"first_name":{"string":"Philip"},"last_name":{"string":"Gamble"}}
{"acct_num":{"int":32429},"first_name":{"string":"Marvin"},"last_name":{"string":"Potts"}}
{"acct_num":{"int":32431},"first_name":{"string":"Judith"},"last_name":{"string":"Lindgren"}}
{"acct_num":{"int":32432},"first_name":{"string":"Darlene"},"last_name":{"string":"Gonzales"}}
{"acct_num":{"int":32435},"first_name":{"string":"Marjorie"},"last_name":{"string":"Morrison"}}
{"acct_num":{"int":32436},"first_name":{"string":"Helen"},"last_name":{"string":"Perez"}}
{"acct_num":{"int":32438},"first_name":{"string":"Violet"},"last_name":{"string":"Searcy"}}
{"acct_num":{"int":32439},"first_name":{"string":"Eunice"},"last_name":{"string":"Myers"}}
{"acct_num":{"int":32440},"first_name":{"string":"Robert"},"last_name":{"string":"Huskey"}}
[training@localhost ~]$ avro-tools tojson hdfs://localhost/loudacre/accounts/CA/part-m-00001.avro | tail
log4j:WARN No appenders could be found for logger (org.apache.hadoop.metrics2.lib.MutableMetricsFactory).
log4j:WARN Please initialize the log4j system properly.
log4j:WARN See http://logging.apache.org/log4j/1.2/faq.html#noconfig for more info.
{"acct_num":{"int":64866},"first_name":{"string":"Jimmie"},"last_name":{"string":"McLemore"}}
{"acct_num":{"int":64867},"first_name":{"string":"Marie"},"last_name":{"string":"Flowers"}}
{"acct_num":{"int":64870},"first_name":{"string":"Robert"},"last_name":{"string":"McGaughey"}}
{"acct_num":{"int":64873},"first_name":{"string":"Jacob"},"last_name":{"string":"Harvey"}}
{"acct_num":{"int":64874},"first_name":{"string":"Clara"},"last_name":{"string":"Safford"}}
{"acct_num":{"int":64875},"first_name":{"string":"Erica"},"last_name":{"string":"Oleary"}}
{"acct_num":{"int":64877},"first_name":{"string":"Jermaine"},"last_name":{"string":"Harmon"}}
{"acct_num":{"int":64878},"first_name":{"string":"Mary"},"last_name":{"string":"Hanson"}}
{"acct_num":{"int":64879},"first_name":{"string":"Richard"},"last_name":{"string":"Alligood"}}
{"acct_num":{"int":64880},"first_name":{"string":"Florence"},"last_name":{"string":"Guevara"}}
[training@localhost ~]$ avro-tools tojson hdfs://localhost/loudacre/accounts/CA/part-m-00002.avro | tail
log4j:WARN No appenders could be found for logger (org.apache.hadoop.metrics2.lib.MutableMetricsFactory).
log4j:WARN Please initialize the log4j system properly.
log4j:WARN See http://logging.apache.org/log4j/1.2/faq.html#noconfig for more info.
{"acct_num":{"int":97307},"first_name":{"string":"Maria"},"last_name":{"string":"Metz"}}
{"acct_num":{"int":97308},"first_name":{"string":"Frank"},"last_name":{"string":"Clabaugh"}}
{"acct_num":{"int":97309},"first_name":{"string":"Sharon"},"last_name":{"string":"Haney"}}
{"acct_num":{"int":97310},"first_name":{"string":"Edward"},"last_name":{"string":"Braithwaite"}}
{"acct_num":{"int":97312},"first_name":{"string":"Margaret"},"last_name":{"string":"Dengler"}}
{"acct_num":{"int":97313},"first_name":{"string":"Yvonne"},"last_name":{"string":"Grier"}}
{"acct_num":{"int":97314},"first_name":{"string":"Eloy"},"last_name":{"string":"Murphy"}}
{"acct_num":{"int":97315},"first_name":{"string":"Beatrice"},"last_name":{"string":"Dodson"}}
{"acct_num":{"int":97317},"first_name":{"string":"Marc"},"last_name":{"string":"Stock"}}
{"acct_num":{"int":97319},"first_name":{"string":"Leona"},"last_name":{"string":"Stannard"}}
[training@localhost ~]$ avro-tools tojson hdfs://localhost/loudacre/accounts/CA/part-m-00003.avro | tail
log4j:WARN No appenders could be found for logger (org.apache.hadoop.metrics2.lib.MutableMetricsFactory).
log4j:WARN Please initialize the log4j system properly.
log4j:WARN See http://logging.apache.org/log4j/1.2/faq.html#noconfig for more info.
{"acct_num":{"int":129749},"first_name":{"string":"Sharon"},"last_name":{"string":"Sommers"}}
{"acct_num":{"int":129750},"first_name":{"string":"Enrique"},"last_name":{"string":"Thomas"}}
{"acct_num":{"int":129751},"first_name":{"string":"Sylvia"},"last_name":{"string":"Boykin"}}
{"acct_num":{"int":129752},"first_name":{"string":"Gary"},"last_name":{"string":"Johnson"}}
{"acct_num":{"int":129753},"first_name":{"string":"Fernando"},"last_name":{"string":"Tarrant"}}
{"acct_num":{"int":129755},"first_name":{"string":"John"},"last_name":{"string":"Hale"}}
{"acct_num":{"int":129756},"first_name":{"string":"Danny"},"last_name":{"string":"Graf"}}
{"acct_num":{"int":129757},"first_name":{"string":"John"},"last_name":{"string":"McCall"}}
{"acct_num":{"int":129758},"first_name":{"string":"Robert"},"last_name":{"string":"Pitt"}}
{"acct_num":{"int":129760},"first_name":{"string":"Zola"},"last_name":{"string":"Tedder"}}
