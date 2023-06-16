### Using RDD and FlaMap count how many times each word appears in a file and write out a list of words whose count is strictly greater than 4 using Spark.

```
scala> val textFile = sc.textFile("swati/word.txt")
textFile: org.apache.spark.rdd.RDD[String] = swati/word.txt MapPartitionsRDD[1] at textFile at <console>:24
```

```
scala> val counts = textFile.flatMap(line => line.split(" ")).map(word => (word, 1)).reduceByKey(_ + _)
counts: org.apache.spark.rdd.RDD[(String, Int)] = ShuffledRDD[4] at reduceByKey at <console>:25
```

```
scala> import scala.collection.immutable.ListMap
import scala.collection.immutable.ListMap
```

```
scala> val sorted=ListMap(counts.collect.sortWith(_._2 > _._2):_*)// sort in descending order based
sorted: scala.collection.immutable.ListMap[String,Int] = ListMap(hello -> 6, world -> 5, this -> 2, is -> 2, lab -> 2, BDA -> 2, word -> 1)
```

```
scala> println(sorted)
ListMap(hello -> 6, world -> 5, this -> 2, is -> 2, lab -> 2, BDA -> 2, word -> 1)
```

```
scala> for((k,v)<-sorted){ 
     | if(v>4)
     | {
     | print(k+",")
     | print(v)
     | println()
     | }
     | }
hello,6
```
