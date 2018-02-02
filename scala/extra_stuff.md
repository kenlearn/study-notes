# Extra Stuff

### string split, filter, group, count
```scala
val s = "  Some  interesting  stuff to do, hello   "

val x = s.toLowerCase()
    .replaceAll("[^\\w]", " ")
    .split(" ")
    .filter(w => w.trim.length >=1)
    .groupBy(identity)
    .mapValues(_.size)
```

### Usage of identity
```scala
def sqif(test: Boolean) = List(1,2,3,4,5).map(
    if (test) x => x*x else identity)

// equal to this
def sqif(test: Boolean) = List(1,2,3,4,5).map(
    if (test) x => x*x else identity _)

// also to this
def sqif(test: Boolean) = List(1,2,3,4,5).map(
    if (test) x => x*x else x => x)

// this also works
def sqif(test: Boolean) = List(1,2,3,4,5).map(
    x => if(test) x*x else x)

```
