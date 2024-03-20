# MNG-8076

https://issues.apache.org/jira/browse/MNG-8076

First step after checkout (local repo empty):

```
$ mvn -s settings-bad.xml package
```

It will download all from repo "something".
The `_remote.repositories` of `junit:junit:4.13.2` looks like this:

```
#NOTE: This is a Maven Resolver internal implementation file, its format can be changed without prior notice.
#Wed Mar 20 08:49:37 CET 2024
junit-4.13.2.jar>something=
junit-4.13.2.pom>something=
```

Next step:

```
$ mvn -s settings-good.xml package
```

Build WORKS, everything will be rechecked
against Maven Central.

The `_remote.repositories` of `junit:junit:4.13.2` now looks like this:

```
#NOTE: This is a Maven Resolver internal implementation file, its format can be changed without prior notice.
#Wed Mar 20 08:50:40 CET 2024
junit-4.13.2.jar>central=
junit-4.13.2.jar>something=
junit-4.13.2.pom>central=
junit-4.13.2.pom>something=
```
