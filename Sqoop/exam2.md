
## table 로부터  hdfs에 저장
<pre><code>
[training@localhost ~]$ sqoop import
--connect jdbc:mysql://localhost/loudacre
--username training --password training --table accounts
--target-dir /loudacre/accounts/user_compressed
--columns "acct_num, first_name, last_name"
--fields-terminated-by "\t"
--as-parquetfile
--compression-codec org.apache.hadoop.io.compress.SnappyCodec



19/04/07 23:12:18 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 23:12:18 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 23:12:18 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/07 23:12:18 INFO tool.CodeGenTool: Beginning code generation
19/04/07 23:12:18 INFO tool.CodeGenTool: Will generate java class as codegen_accounts
19/04/07 23:12:19 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:12:19 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:12:19 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/5a2a96766198595920ac0bd8d4a1673f/codegen_accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/07 23:12:21 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/5a2a96766198595920ac0bd8d4a1673f/codegen_accounts.jar
19/04/07 23:12:21 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/07 23:12:21 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/07 23:12:21 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/07 23:12:21 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/07 23:12:21 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/07 23:12:21 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/07 23:12:21 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/07 23:12:22 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:12:22 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:12:23 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/07 23:12:23 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/07 23:12:25 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/07 23:12:25 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/04/07 23:12:25 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/04/07 23:12:25 INFO mapreduce.JobSubmitter: number of splits:4
19/04/07 23:12:25 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554697650481_0009
19/04/07 23:12:26 INFO impl.YarnClientImpl: Submitted application application_1554697650481_0009
19/04/07 23:12:26 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554697650481_0009/
19/04/07 23:12:26 INFO mapreduce.Job: Running job: job_1554697650481_0009
19/04/07 23:12:34 INFO mapreduce.Job: Job job_1554697650481_0009 running in uber mode : false
19/04/07 23:12:34 INFO mapreduce.Job:  map 0% reduce 0%
19/04/07 23:12:41 INFO mapreduce.Job:  map 25% reduce 0%
19/04/07 23:12:48 INFO mapreduce.Job:  map 50% reduce 0%
19/04/07 23:12:56 INFO mapreduce.Job:  map 75% reduce 0%
19/04/07 23:13:03 INFO mapreduce.Job:  map 100% reduce 0%
19/04/07 23:13:03 INFO mapreduce.Job: Job job_1554697650481_0009 completed successfully
19/04/07 23:13:03 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=565908
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=25234
		HDFS: Number of bytes written=1305047
		HDFS: Number of read operations=272
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=40
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=23154
		Total vcore-seconds taken by all map tasks=23154
		Total megabyte-seconds taken by all map tasks=5927424
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=507
		CPU time spent (ms)=8160
		Physical memory (bytes) snapshot=645279744
		Virtual memory (bytes) snapshot=8296488960
		Total committed heap usage (bytes)=251920384
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=0
19/04/07 23:13:03 INFO mapreduce.ImportJobBase: Transferred 1.2446 MB in 39.5385 seconds (32.2334 KB/sec)
19/04/07 23:13:03 INFO mapreduce.ImportJobBase: Retrieved 129761 records.


[training@localhost ~]$ parquet-tools head \
> hdfs://localhost/loudacre/accounts/user_compressed
acct_num = 32441
first_name = Peter
last_name = Zachary

acct_num = 32442
first_name = Duane
last_name = Ruiz

acct_num = 32443
first_name = Desiree
last_name = Beall

acct_num = 32444
first_name = Molly
last_name = Pinder

acct_num = 32445
first_name = Melissa
last_name = Carlson


</pre></code>
