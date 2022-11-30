# How to replicate the bug:
```
git clone https://github.com/Toldry/jacoco-aggregation-lockfiles-bug-replicator.git
cd jacoco-aggregation-lockfiles-bug-replicator
gradle resolveAndLockAll --write-locks
```

Expected output:
```
Persisted dependency lock state for buildscript of project 'null'
Persisted dependency lock state for project ':'
> Task :resolveAndLockAll FAILED

FAILURE: Build failed with an exception.

* Where:
Build file 'REDACTED/jacoco-aggregation-lockfiles-bug-replicator/build.gradle' line: 32

* What went wrong:
Execution failed for task ':resolveAndLockAll'.
> Could not resolve all files for configuration ':testCodeCoverageReportExecutionData'.
   > Could not resolve org.junit.jupiter:junit-jupiter:5.7.2.
     Required by:
         project : > project :application
         project : > project :list
         project : > project :utilities
      > No matching variant of org.junit.jupiter:junit-jupiter:5.7.2 was found. The consumer was configured to find a component of category 'verification', as well as attribute 'org.gradle.verificationtype' with value 'jacoco-coverage', attribute 'artifactType' with value 'binary', attribute 'org.gradle.testsuite.type' with value 'unit-test' but:
          - Variant 'apiElements' capability org.junit.jupiter:junit-jupiter:5.7.2:
              - Incompatible because this component declares a library and the consumer needed a component of category 'verification'
              - Other compatible attributes:
                  - Doesn't say anything about artifactType (required 'binary')
                  - Doesn't say anything about org.gradle.testsuite.type (required 'unit-test')
                  - Doesn't say anything about org.gradle.verificationtype (required 'jacoco-coverage')
          - Variant 'javadocElements' capability org.junit.jupiter:junit-jupiter:5.7.2:
              - Incompatible because this component declares documentation and the consumer needed a component of category 'verification'
              - Other compatible attributes:
                  - Doesn't say anything about artifactType (required 'binary')
                  - Doesn't say anything about org.gradle.testsuite.type (required 'unit-test')
                  - Doesn't say anything about org.gradle.verificationtype (required 'jacoco-coverage')
          - Variant 'runtimeElements' capability org.junit.jupiter:junit-jupiter:5.7.2:
              - Incompatible because this component declares a library and the consumer needed a component of category 'verification'
              - Other compatible attributes:
                  - Doesn't say anything about artifactType (required 'binary')
                  - Doesn't say anything about org.gradle.testsuite.type (required 'unit-test')
                  - Doesn't say anything about org.gradle.verificationtype (required 'jacoco-coverage')
          - Variant 'sourcesElements' capability org.junit.jupiter:junit-jupiter:5.7.2:
              - Incompatible because this component declares documentation and the consumer needed a component of category 'verification'
              - Other compatible attributes:
                  - Doesn't say anything about artifactType (required 'binary')
                  - Doesn't say anything about org.gradle.testsuite.type (required 'unit-test')
                  - Doesn't say anything about org.gradle.verificationtype (required 'jacoco-coverage')

* Try:
> Run with --stacktrace option to get the stack trace.
> Run with --info or --debug option to get more log output.
> Run with --scan to get full insights.

* Get more help at https://help.gradle.org

Deprecated Gradle features were used in this build, making it incompatible with Gradle 8.0.

You can use '--warning-mode all' to show the individual deprecation warnings and determine if they come from your own scripts or plugins.

See https://docs.gradle.org/7.5.1/userguide/command_line_interface.html#sec:command_line_warnings

BUILD FAILED in 475ms
```

# Note
This project was derived from this example project by Gradle:

https://docs.gradle.org/current/samples/sample_jvm_multi_project_with_code_coverage_standalone.html