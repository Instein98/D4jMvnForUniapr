# D4jMvnForUniapr

This project aims to make the profiler of Uniapr produce the same test result as defects4j.

## Requirements

1. Java 1.8
2. Defects4J 2.0.0

## Usage

```shell
python setupProj.py
```

The script will
1. Use defects4j to checkout all projects
2. Copy the prepared pom.xml to the project directories
3. Apply patches to the projects' source code if necessary
4. Use defects4j to compile the project (Closure-106 needs maven to compile)
5. Run `defects4j test` to generate file `all_tests` and `failing_tests` (`all_tests` will be used by Uniapr to run the same set of tests)
6. Check whether `defects4j test` fails the expected tests using the information in `failing_tests` and `defects4j info` 

## Note

- Please note that Unipar can not validate the patches for Mockito-5 now (it requires that the validating JVM does not load the class junit.framework.ComparisonFailure).
- For Closure-106, please make sure to
    - run `mvn clean && defects4j compile` to compile first, if you want to run `defects4j test`.
    - run `mvn test-compile` to compile first, if you want to run Uniapr.