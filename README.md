# How to replicate the bug:
```
git clone https://github.com/Toldry/jacoco-aggregation-lockfiles-bug-replicator.git
cd jacoco-aggregation-lockfiles-bug-replicator
gradle resolveAndLockAll --write-locks
```

# Expected output:
```
Persisted dependency lock state for buildscript of project 'null'
Persisted dependency lock state for project ':'
> Task :resolveAndLockAll FAILED

FAILURE: Build failed with an exception.

* Where:
Build file '/Users/aloneitan/workspace2/jacoco-aggregation-lockfiles-bug-replicator/build.gradle' line: 44

* What went wrong:
Execution failed for task ':resolveAndLockAll'.
> Could not resolve all files for configuration ':allCodeCoverageReportSourceDirectories'.
   > Could not resolve com.google.guava:guava:+.
     Required by:
         project : > project :utilities
      > No matching variant of com.google.guava:guava:31.1-jre was found. The consumer was configured to find a component of category 'verification', and its dependencies declared externally, as well as attribute 'org.gradle.verificationtype' with value 'main-sources' but:
          - Variant 'compile' capability com.google.guava:guava:31.1-jre:
              - Incompatible because this component declares a library and the consumer needed a component of category 'verification'
              - Other compatible attributes:
                  - Doesn't say anything about how its dependencies are found (required its dependencies declared externally)
                  - Doesn't say anything about org.gradle.verificationtype (required 'main-sources')
          - Variant 'enforced-platform-compile' capability com.google.guava:guava-derived-enforced-platform:31.1-jre:
              - Incompatible because this component declares an enforced platform and the consumer needed a component of category 'verification'
              - Other compatible attributes:
                  - Doesn't say anything about how its dependencies are found (required its dependencies declared externally)
                  - Doesn't say anything about org.gradle.verificationtype (required 'main-sources')
          - Variant 'enforced-platform-runtime' capability com.google.guava:guava-derived-enforced-platform:31.1-jre:
              - Incompatible because this component declares an enforced platform and the consumer needed a component of category 'verification'
              - Other compatible attributes:
                  - Doesn't say anything about how its dependencies are found (required its dependencies declared externally)
                  - Doesn't say anything about org.gradle.verificationtype (required 'main-sources')
          - Variant 'javadoc' capability com.google.guava:guava:31.1-jre declares a component, and its dependencies declared externally:
              - Incompatible because this component declares documentation and the consumer needed a component of category 'verification'
              - Other compatible attribute:
                  - Doesn't say anything about org.gradle.verificationtype (required 'main-sources')
          - Variant 'platform-compile' capability com.google.guava:guava-derived-platform:31.1-jre:
              - Incompatible because this component declares a platform and the consumer needed a component of category 'verification'
              - Other compatible attributes:
                  - Doesn't say anything about how its dependencies are found (required its dependencies declared externally)
                  - Doesn't say anything about org.gradle.verificationtype (required 'main-sources')
          - Variant 'platform-runtime' capability com.google.guava:guava-derived-platform:31.1-jre:
              - Incompatible because this component declares a platform and the consumer needed a component of category 'verification'
              - Other compatible attributes:
                  - Doesn't say anything about how its dependencies are found (required its dependencies declared externally)
                  - Doesn't say anything about org.gradle.verificationtype (required 'main-sources')
          - Variant 'runtime' capability com.google.guava:guava:31.1-jre:
              - Incompatible because this component declares a library and the consumer needed a component of category 'verification'
              - Other compatible attributes:
                  - Doesn't say anything about how its dependencies are found (required its dependencies declared externally)
                  - Doesn't say anything about org.gradle.verificationtype (required 'main-sources')
          - Variant 'sources' capability com.google.guava:guava:31.1-jre declares a component, and its dependencies declared externally:
              - Incompatible because this component declares documentation and the consumer needed a component of category 'verification'
              - Other compatible attribute:
                  - Doesn't say anything about org.gradle.verificationtype (required 'main-sources')

* Try:
> Run with --stacktrace option to get the stack trace.
> Run with --info or --debug option to get more log output.
> Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 398ms
10 actionable tasks: 1 executed, 9 up-to-date
```

# Note
This project was derived from this example project by Gradle:

https://docs.gradle.org/current/samples/sample_jvm_multi_project_with_code_coverage_standalone.html