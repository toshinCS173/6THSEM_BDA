**command to start all hadoop daemons**

```
start-all.sh

WARNING: Attempting to start all Apache Hadoop daemons as hadoop in 10 seconds.
WARNING: This is not a recommended production deployment configuration.
WARNING: Use CTRL-C to abort.
Starting namenodes on [localhost]
Starting datanodes
Starting secondary namenodes [bmscecse-HP-Elite-Tower-600-G9-Desktop-PC]
Starting resourcemanager
Starting nodemanagers
```

**to check if all daemons have loaded**

```
jps

9056 Jps
7475 ResourceManager
6709 NameNode
7160 SecondaryNameNode
7659 NodeManager
6875 DataNode
```

**mkdir command**

```
hdfs dfs -mkdir /bda
```

**ls command**

```
hadoop fs -ls /
Found 4 items
drwxr-xr-x   - hadoop supergroup          0 2023-05-08 09:40 /abc
drwxr-xr-x   - hadoop supergroup          0 2023-05-11 13:57 /bda
drwxr-xr-x   - hadoop supergroup          0 2023-05-04 12:49 /inputbda
drwxr-xr-x   - hadoop supergroup          0 2023-04-27 11:44 /siri
```

**to append text in a file in hdfs**

```
echo "<Text to append>" | hdfs dfs -appendToFile - /user/hduser/myfile.txt OR

hdfs dfs -appendToFile - /user/hduser/myfile.txt 
and then type the text on the terminal. Once you are done typing then hit 'Ctrl+D'
```

**cat command**

```
echo "hello world bda lab" | hdfs dfs -appendToFile - /bda/hello.txt

hdfs dfs -cat /bda/hello.txt
hello world bda lab
```

**put & copyFromLocal command**

```
hdfs dfs -put Desktop/hadooplocal.txt /bda/hadoop.txt

hdfs dfs -copyFromLocal Desktop/hadooplocal.txt /bda/hadoop.txt

hdfs dfs -cat /bda/hadoop.txt
local file created in the desktop
```

**get command**

```
hdfs dfs -touchz /bda/labfile.txt

echo "copying hdfs file to a local file using get command" | hdfs dfs -appendToFile - /bda/labfile.txt

hdfs dfs -cat /bda/labfile.txt
copying hdfs file to a local file using get command

hdfs dfs -get /bda/labfile.txt Desktop/getcmd.txt
```

**Contents of getcmd.txt file in Desktop is:**

copying hdfs file to a local file using get command

**copyToLocal command**

```
hdfs dfs -touchz /bda/ghost.txt

echo "new hdfs file in hdfs folder" | hdfs dfs -appendToFile - /bda/ghost.txt

hdfs dfs -cat /bda/ghost.txt
new hdfs file in hdfs folder

hdfs dfs -copyToLocal /bda/ghost.txt Desktop/bigdata.txt
```

**Contents of bigdata.txt file in desktop is:**

new hdfs file in hdfs folder

**mv command**

```
hdfs dfs -ls /bda
Found 4 items
-rw-r--r--   1 hadoop supergroup         29 2023-05-11 14:39 /bda/ghost.txt
-rw-r--r--   1 hadoop supergroup         34 2023-05-11 14:26 /bda/hadoop.txt
-rw-r--r--   1 hadoop supergroup         20 2023-05-11 14:11 /bda/hello.txt
-rw-r--r--   1 hadoop supergroup         52 2023-05-11 14:32 /bda/labfile.txt

hadoop fs -mv /bda/hello.txt /dir

hdfs dfs -ls /bda
Found 3 items
-rw-r--r--   1 hadoop supergroup         29 2023-05-11 14:39 /bda/ghost.txt
-rw-r--r--   1 hadoop supergroup         34 2023-05-11 14:26 /bda/hadoop.txt
-rw-r--r--   1 hadoop supergroup         52 2023-05-11 14:32 /bda/labfile.txt

hdfs dfs -ls /dir
-rw-r--r--   1 hadoop supergroup         20 2023-05-11 14:11 /dir
```

**cp command**

```
hadoop fs -cp /bda /rest

hdfs dfs -ls /bda
Found 3 items
-rw-r--r--   1 hadoop supergroup         29 2023-05-11 14:39 /bda/ghost.txt
-rw-r--r--   1 hadoop supergroup         34 2023-05-11 14:26 /bda/hadoop.txt
-rw-r--r--   1 hadoop supergroup         52 2023-05-11 14:32 /bda/labfile.txt

hdfs dfs -ls /rest
Found 3 items
-rw-r--r--   1 hadoop supergroup         29 2023-05-11 14:50 /rest/ghost.txt
-rw-r--r--   1 hadoop supergroup         34 2023-05-11 14:50 /rest/hadoop.txt
-rw-r--r--   1 hadoop supergroup         52 2023-05-11 14:50 /rest/labfile.txt
```
