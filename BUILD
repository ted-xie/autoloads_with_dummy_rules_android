load("@rules_java//java:java_library.bzl", "java_library")

genrule(
  name = "Foo_java",
  outs = ["Foo.java"],
  cmd = "echo > $@",
)

java_library(
  name = "foo",
  srcs = [":Foo_java"],
  deps = [
    "@bazel_worker_java//src/main/java/com/google/devtools/build/lib/worker:work_request_handlers"
  ],
)
