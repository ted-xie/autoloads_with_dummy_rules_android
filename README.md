# Autoloads behave strangely when the main module is a rule repo?

With bazel 8.0.0-rc1:

```
$ USE_BAZEL_VERSION=8.0.0rc1 bazelisk build :foo
ERROR: /usr/local/google/home/tedx/.cache/bazel/_bazel_tedx/3b8ef939374b9d3dc5ff22f3722d9924/external/bazel_worker_java+/src/main/java/com/google/devtools/build/lib/worker/BUILD.bazel:3:13: @@bazel_worker_java+//src/main/java/com/google/devtools/build/lib/worker:work_request_handlers: no such attribute 'srcs' in 'java_library' rule
ERROR: /usr/local/google/home/tedx/.cache/bazel/_bazel_tedx/3b8ef939374b9d3dc5ff22f3722d9924/external/bazel_worker_java+/src/main/java/com/google/devtools/build/lib/worker/BUILD.bazel:3:13: @@bazel_worker_java+//src/main/java/com/google/devtools/build/lib/worker:work_request_handlers: no such attribute 'deps' in 'java_library' rule
ERROR: /tmp/dummy_rules_android/BUILD:9:13: Target '@@bazel_worker_java+//src/main/java/com/google/devtools/build/lib/worker:work_request_handlers' contains an error and its package is in error and referenced by '//:foo'
ERROR: Analysis of target '//:foo' failed; build aborted: Analysis failed
```

With bazel 7.4.0:

```
$ USE_BAZEL_VERSION=7.4.0 bazelisk build :foo
Starting local Bazel server and connecting to it...
INFO: Analyzed target //:foo (155 packages loaded, 5131 targets configured).
INFO: Found 1 target...
Target //:foo up-to-date:
  bazel-bin/libfoo.jar
INFO: Elapsed time: 12.575s, Critical Path: 0.47s
INFO: 1 process: 1 internal.
INFO: Build completed successfully, 1 total action
```
