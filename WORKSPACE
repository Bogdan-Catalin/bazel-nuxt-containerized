load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# NodeJS
http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "f533eeefc8fe1ddfe93652ec50f82373d0c431f7faabd5e6323f6903195ef227",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/3.3.0/rules_nodejs-3.3.0.tar.gz"],
)

load("@build_bazel_rules_nodejs//:index.bzl", "node_repositories", "yarn_install")

node_repositories(
    package_json = ["//app:package.json"]
)

yarn_install(
    name = "npm",
    package_json = "//app:package.json",
    yarn_lock = "//app:yarn.lock",
)

# Docker
http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "95d39fd84ff4474babaf190450ee034d958202043e366b9fc38f438c9e6c3334",
    strip_prefix = "rules_docker-0.16.0",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.16.0/rules_docker-v0.16.0.tar.gz"],
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)

container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()