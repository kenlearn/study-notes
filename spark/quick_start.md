# Spark Quick Start


### start spark-shell
```bash
spark-shell --master local[2]
```
- ```--master``` specify master URL
- ```local[N]``` run locally with N thread


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

### Usage of identity
```scala
def sqif(test: Boolean) = List(1,2,3,4,5).map(
    if (test) x => x*x else identity _)

def sqif(test: Boolean) = List(1,2,3,4,5).map(
    if (test) x => x*x else x => x)

def sqif(test: Boolean) = List(1,2,3,4,5).map(
    x => if(test) x*x else x)

```
