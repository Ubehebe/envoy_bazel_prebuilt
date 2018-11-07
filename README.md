# envoy_bazel_prebuilt

[Envoy](https://envoyproxy.io) is the [recommended proxy](https://github.com/grpc/grpc-web#proxy-interoperability)
for gRPC-Web applications.

Envoy can be built with [Bazel](https://bazel.build) (its repo provides a top-level `cc_binary`
target), but it is not as simple as `bazel build <envoy>`. The Envoy build process [requires](https://github.com/envoyproxy/envoy/blob/master/bazel/README.md#quick-start-bazel-build-for-developers)
several tools to be installed on the system that Bazel doesn't know about. As a result, building the
Envoy binary with [--experimental_strict_action_env](https://docs.bazel.build/versions/master/command-line-reference.html#flag--experimental_strict_action_env)
fails. For Bazel-based projects that mandate `--experimental_strict_action_env`, this is a problem.

This repository provides artifacts that are the result of building `@envoy//source/exe:envoy-static`.