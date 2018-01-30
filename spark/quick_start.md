# Spark Quick Start
- [Spark 2.2.1](https://spark.apache.org/docs/latest/quick-start.html)

### start spark-shell
```bash
spark-shell --master local[2]
```
- ```--master``` specify master URL
- ```local[N]``` run locally with N thread

### test on spark shell console
```scala
val textFile = spark.read.textFile("opt/spark/README.md")

textFile.count()    // size of the dataset

textFile.columns    // list columns
textFile.show       // show 20 rows

// filter
val filtered = textFile.filter(line => line.contains("Spark"))

// map reduce, largest word count of line
textFile.map(line => line.split(" ").size).reduce((a,b) => if (a > b) a else b)

// group by
val wordCounts = textFile.flatMap(line => line.split(" ")).groupByKey(identity).count()
val wordCounts = textFile.flatMap(line => line.split(" ")).groupByKey(x => x.toLowerCase).count()

```

### build a simple app and submit to spark
[self contained application](https://spark.apache.org/docs/latest/quick-start.html#self-contained-applications)
