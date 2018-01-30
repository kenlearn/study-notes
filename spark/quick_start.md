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
```scala
// scala
import org.apache.spark.sql.SparkSession

object SimpleApp {

    def main(args: Array[String]) {
        val logF = "/home/vagrant/opt/spark/README.md"
        val spark = SparkSession.builder.appName("Simple Application").getOrCreate()
        val logData = spark.read.textFile(logF).cache()

        val countA = logData.filter(line => line.contains("a")).count()

        println(s"Lines with \'a\': $countA")

        spark.stop()
    }    
}
```

```scala
// file: build.sbt
name := "Simple App"
version := "1.0"
scalaVersion := "2.11.12"
libraryDependencies += "org.apache.spark" %% "spark-sql" % "2.2.1"
```

```bash
## shell
sbt package
spark-submit \
  --class SimpleApp \
  --master local[2] \
  target/scala-2.11/simple-app_2.11-1.0.jar
```
