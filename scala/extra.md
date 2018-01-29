# Extra Stuff


### Usage of identity
```scala
def sqif(test: Boolean) = List(1,2,3,4,5).map(
    if (test) x => x*x else identity _)

def sqif(test: Boolean) = List(1,2,3,4,5).map(
    if (test) x => x*x else x => x)

def sqif(test: Boolean) = List(1,2,3,4,5).map(
    x => if(test) x*x else x)

```
