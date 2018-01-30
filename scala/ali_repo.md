# Aliyun Maven Repo

In ```$HOME/.sbt``` dir, create ```repositories```
```
[repositories]
local
aliyun: http://maven.aliyun.com/nexus/content/groups/public
jcenter: http://jcenter.bintray.com
typesafe: http://repo.typesafe.com/typesafe/ivy-releases/, [organization]/[module]/(scala_[scalaVersion]/)(sbt_[sbtVersion]/)[revision]/[type]s/[artifact](-[classifier]).[ext], bootOnly
```

> Aliyun mirror provide faster access to Maven repo in China
