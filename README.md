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

# Env

Am using this:

```
[cstamas@blondie MNG-8076 (main)]$ mvn -v
Apache Maven 3.9.6 (bc0240f3c744dd6b6ec2920b3cd08dcc295161ae)
Maven home: /home/cstamas/.sdkman/candidates/maven/current
Java version: 21.0.2, vendor: Eclipse Adoptium, runtime: /home/cstamas/.sdkman/candidates/java/21.0.2-tem
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "6.7.9-200.fc39.x86_64", arch: "amd64", family: "unix"
[cstamas@blondie MNG-8076 (main)]$ 
```
