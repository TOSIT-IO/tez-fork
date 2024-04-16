# TDP Tez Notes

The version 0.10.2-1.0 of Apache Hive is based on the `branch-0.10.4` tag of the Apache [repository](https://github.com/apache/tez/tree/branch-0.10.4).

## Jenkinfile

The file `./Jenkinsfile-sample` can be used in a Jenkins / Kubernetes environment to build and execute the unit tests of the Tez project. See []() for details on the environment.

## Making a release

```
mvn clean install -pl \!tez-ui -Phadoop28 -P\!hadoop27 -DskipTests
```

The command generates a `.tar.gz` file of the release at `./tez-dist/target/tez-0.10.4-0.0.tar.gz`.

## Testing parameters

```
mvn test -pl \!tez-ui -Phadoop28 -P\!hadoop27 -DskipTests --fail-never
```

- -pl \!tez-ui: Disable `tez-ui` maven project
- -Phadoop28: Activates the necessary Maven profile for Hadoop > 2.8 (as mentionned in `tez/BUILDING.txt`)
- -P\!hadoop27: De-activates the Maven profile for Hadoop < 2.8
- --fail-never: Does not interrupt the tests if one module fails

