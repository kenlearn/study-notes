# Simple SBT project

## From scratch

### build.sbt: 

```scala
// file: build.sbt

name := "Simple App"
version := "1.0"
scalaVersion := "2.12.4"
libraryDependencies += "org.apache.spark" %% "spark-sql" % "2.2.1"
```

### dir structure
```bash
./build.sbt
./src
./src/main
./src/main/scala
./src/main/scala/SimpleApp.scala
```

## Using giter8 seed

```bash
sbt new sbt/scala-seed.g8
# or
sbt new https://github.com/sbt/scala-seed.g8
```

> SBT use ```git://``` as default. In some situation, need to use ```https://```
