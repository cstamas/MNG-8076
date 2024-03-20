# MNG-8076

https://issues.apache.org/jira/browse/MNG-8076

First step after checkout (local repo empty):

```
$ mvn -s settings-bad.xml package
```

It will download all from repo "something".
Next step:

```
$ mvn -s settings-good.xml package
```

Build WORKS, everything will be rechecked
against Maven Central.
