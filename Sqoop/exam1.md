<pre><code>
## table 로부터  hdfs에 저장
[training@localhost ~]$ sqoop eval --connect jdbc:mysql://localhost/loudacre
--username training --password training --query "DESC accounts"


19/04/07 22:22:09 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 22:22:09 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 22:22:09 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
---------------------------------------------------------------------------------------------------------
| Field                | Type                 | Null | Key | Default              | Extra                |
---------------------------------------------------------------------------------------------------------
| acct_num             | int(11)              | NO  | PRI | (null)               |                      |
| acct_create_dt       | datetime             | NO  |     | (null)               |                      |
| acct_close_dt        | datetime             | YES |     | (null)               |                      |
| first_name           | varchar(255)         | NO  |     | (null)               |                      |
| last_name            | varchar(255)         | NO  |     | (null)               |                      |
| address              | varchar(255)         | NO  |     | (null)               |                      |
| city                 | varchar(255)         | NO  |     | (null)               |                      |
| state                | varchar(255)         | NO  |     | (null)               |                      |
| zipcode              | varchar(255)         | NO  |     | (null)               |                      |
| phone_number         | varchar(255)         | NO  |     | (null)               |                      |
| created              | datetime             | NO  |     | (null)               |                      |
| modified             | datetime             | NO  |     | (null)               |                      |
---------------------------------------------------------------------------------------------------------


[training@localhost ~]$ sqoop import
--connect jdbc:mysql://localhost/loudacre
--username training
--password training
--table accounts
--target-dir /loudacre/accounts/user_info
--columns "acct_num, first_name, last_name"
--fields-terminated-by "\t"

19/04/07 22:30:19 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 22:30:19 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 22:30:19 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/07 22:30:19 INFO tool.CodeGenTool: Beginning code generation
19/04/07 22:30:20 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 22:30:20 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 22:30:20 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/382df890aa207dc1bbabd04b6914ee75/accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/07 22:30:22 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/382df890aa207dc1bbabd04b6914ee75/accounts.jar
19/04/07 22:30:22 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/07 22:30:22 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/07 22:30:22 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/07 22:30:22 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/07 22:30:22 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/07 22:30:22 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/07 22:30:22 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/07 22:30:23 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/07 22:30:23 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/07 22:30:25 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/07 22:30:25 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/04/07 22:30:25 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/04/07 22:30:25 INFO mapreduce.JobSubmitter: number of splits:4
19/04/07 22:30:25 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554697650481_0004
19/04/07 22:30:26 INFO impl.YarnClientImpl: Submitted application application_1554697650481_0004
19/04/07 22:30:26 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554697650481_0004/
19/04/07 22:30:26 INFO mapreduce.Job: Running job: job_1554697650481_0004
19/04/07 22:30:34 INFO mapreduce.Job: Job job_1554697650481_0004 running in uber mode : false
19/04/07 22:30:34 INFO mapreduce.Job:  map 0% reduce 0%
19/04/07 22:30:41 INFO mapreduce.Job:  map 25% reduce 0%
19/04/07 22:30:46 INFO mapreduce.Job:  map 50% reduce 0%
19/04/07 22:30:51 INFO mapreduce.Job:  map 75% reduce 0%
19/04/07 22:30:56 INFO mapreduce.Job:  map 100% reduce 0%
19/04/07 22:30:56 INFO mapreduce.Job: Job job_1554697650481_0004 completed successfully
19/04/07 22:30:56 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=560464
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=470
		HDFS: Number of bytes written=2615920
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=15496
		Total vcore-seconds taken by all map tasks=15496
		Total megabyte-seconds taken by all map tasks=3966976
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=271
		CPU time spent (ms)=3530
		Physical memory (bytes) snapshot=494198784
		Virtual memory (bytes) snapshot=8262221824
		Total committed heap usage (bytes)=251920384
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=2615920
19/04/07 22:30:56 INFO mapreduce.ImportJobBase: Transferred 2.4947 MB in 33.1514 seconds (77.0588 KB/sec)
19/04/07 22:30:56 INFO mapreduce.ImportJobBase: Retrieved 129761 records.



hdfs dfs -ls /loudacre/accounts/user_info
Found 5 items
-rw-rw-rw-   1 training supergroup          0 2019-04-07 22:30 /loudacre/accounts/user_info/ SUCCESS
-rw-rw-rw-   1 training supergroup     638090 2019-04-07 22:30 /loudacre/accounts/user_info/part-m-00000
-rw-rw-rw-   1 training supergroup     649567 2019-04-07 22:30 /loudacre/accounts/user_info/part-m-00001
-rw-rw-rw-   1 training supergroup     649000 2019-04-07 22:30 /loudacre/accounts/user_info/part-m-00002
-rw-rw-rw-   1 training supergroup     679263 2019-04-07 22:30 /loudacre/accounts/user_info/part-m-00003



[training@localhost ~]$ hdfs dfs -tail /loudacre/accounts/user_info/part-m-00000
lsh
32390	Olga	Lipson
32391	Eddie	Hedrick
32392	Alvin	Phillips
32393	Travis	Ainsworth
32394	Allen	Pruitt
32395	Clay	Sherrill
32396	Janice	Padgett
32397	Lisa	Backes
32398	Albert	Walters
32399	Anna	Rathbone
32400	Gwen	Nelson
32401	Judith	Sullivan
32402	Linda	Davis
32403	Deborah	Felipe
32404	Tami	Ketcham
32405	Suzanne	Alexander
32406	Anita	Byrd
32407	Kenneth	Khalil
32408	Jennifer	Merida
32409	Kevin	Gibson
32410	Sheila	Morgan
32411	Kenny	Conger
32412	Angel	Scoggins
32413	Ida	Castro
32414	Tammy	Buxton
32415	James	Ward
32416	Emma	Carmichael
32417	Carmen	Lane
32418	Andrea	Holt
32419	Catherine	Roberts
32420	Erin	Little
32421	Johnny	Graves
32422	Leonard	Lamm
32423	Dennis	Hodge
32424	Nadine	Frias
32425	Juan	Mendel
32426	Dorothy	Thompson
32427	Tara	Jenkins
32428	Philip	Gamble
32429	Marvin	Potts
32430	Stephanie	Wootton
32431	Judith	Lindgren
32432	Darlene	Gonzales
32433	Nicholas	Monger
32434	Anne	Boyle
32435	Marjorie	Morrison
32436	Helen	Perez
32437	Melissa	Hayes
32438	Violet	Searcy
32439	Eunice	Myers
32440	Robert	Huskey
[training@localhost ~]$ hdfs dfs -tail /loudacre/accounts/user_info/part-m-00001
	King
64831	Minnie	Fennell
64832	Mark	Battle
64833	Scott	Goetz
64834	Dale	Curtis
64835	Lynda	Resch
64836	Amanda	Cokley
64837	Nora	Buck
64838	Christopher	Severino
64839	Thomas	Renard
64840	Gail	Partridge
64841	Virginia	Hutchinson
64842	David	Stewart
64843	Dorothy	Wainwright
64844	Justin	Jasso
64845	Michael	Young
64846	Elizabeth	Deaton
64847	Harry	Edwards
64848	Charles	Palmer
64849	Douglas	Cook
64850	Robert	Davis
64851	Lloyd	Troche
64852	Mary	Shrader
64853	David	Parmelee
64854	George	Smith
64855	Zella	Baker
64856	Scott	Paul
64857	Dorothy	Skillings
64858	Muriel	Perkins
64859	Mary	Tope
64860	Martha	Phillips
64861	William	Baum
64862	Steve	Brown
64863	Robert	Ahlstrom
64864	Miguel	Mejia
64865	Pauline	Freeman
64866	Jimmie	McLemore
64867	Marie	Flowers
64868	Mable	Alexander
64869	Cynthia	Bates
64870	Robert	McGaughey
64871	Pedro	Bloom
64872	Roger	Hicks
64873	Jacob	Harvey
64874	Clara	Safford
64875	Erica	Oleary
64876	Leslie	Jeanbaptiste
64877	Jermaine	Harmon
64878	Mary	Hanson
64879	Richard	Alligood
64880	Florence	Guevara
[training@localhost ~]$ hdfs dfs -tail /loudacre/accounts/user_info/part-m-00002
men	Martinez
97271	Mildred	Dietz
97272	John	Schultz
97273	Tracy	Whitty
97274	Bernard	Chambers
97275	Julie	Shull
97276	Theodora	Frost
97277	Kathleen	Robinson
97278	Constance	Gonzalez
97279	Michael	Oneil
97280	Daniel	Hernandez
97281	Jennifer	Wood
97282	Kenneth	Davis
97283	Justin	Dreyer
97284	Daniel	McCracken
97285	Brian	Hargrave
97286	Daniel	Sosa
97287	Mabel	Ballance
97288	Gertrude	Smith
97289	Eric	McKim
97290	Carol	Johnson
97291	James	Owens
97292	Richard	Baker
97293	Thomas	Russell
97294	Ronald	Gibson
97295	Betty	Butler
97296	Elizabeth	Searle
97297	Tyrone	Ebbert
97298	Lillie	Campos
97299	Naomi	Abbott
97300	James	Neil
97301	Ginger	White
97302	Kathryn	Grant
97303	Shellie	Galarza
97304	Doris	Jones
97305	Esther	Sell
97306	Danny	Jones
97307	Maria	Metz
97308	Frank	Clabaugh
97309	Sharon	Haney
97310	Edward	Braithwaite
97311	Michael	Capehart
97312	Margaret	Dengler
97313	Yvonne	Grier
97314	Eloy	Murphy
97315	Beatrice	Dodson
97316	Gayle	Montelongo
97317	Marc	Stock
97318	Roger	Weyand
97319	Leona	Stannard
97320	Bryant	Nemec
[training@localhost ~]$ hdfs dfs -tail /loudacre/accounts/user_info/part-m-00003
Janessa	Lewis
129713	Megan	Silva
129714	Debra	Horner
129715	Angela	Powers
129716	Werner	Torres
129717	Lisa	Mitchell
129718	Darlene	Deluna
129719	Julie	Daniel
129720	Gary	Wang
129721	Bertha	Romero
129722	Josephine	Moe
129723	Tanya	Pacheco
129724	David	Davis
129725	Mikki	Oleson
129726	Richard	Almaraz
129727	Eric	Mitchum
129728	Charles	Farley
129729	Carlton	Boring
129730	Chung	Rodgers
129731	David	Rivera
129732	Lucille	Aucoin
129733	Rose	Lynch
129734	Lori	Smith
129735	Mary	Fowlkes
129736	Darryl	Williams
129737	Bradley	Nilson
129738	Sue	Holland
129739	Jane	Ross
129740	Robert	Newman
129741	Scott	Robinson
129742	Franklin	Walker
129743	Marianna	Brown
129744	Shelton	Mack
129745	Rosario	Sauceda
129746	Mary	Tatum
129747	Justin	Kieffer
129748	Michael	Johnson
129749	Sharon	Sommers
129750	Enrique	Thomas
129751	Sylvia	Boykin
129752	Gary	Johnson
129753	Fernando	Tarrant
129754	Maria	Godoy
129755	John	Hale
129756	Danny	Graf
129757	John	McCall
129758	Robert	Pitt
129759	Deborah	Hutchings
129760	Zola	Tedder
129761	Ruth	Ebersole
</pre></code>
