load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "27d53c1d646fc9537a70427ad7b034734d08a9c38924cc6357cc973fed300820",
    strip_prefix = "rules_docker-0.24.0",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.24.0/rules_docker-v0.24.0.tar.gz"],
)


load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)
container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_pull",
)
load("@io_bazel_rules_docker//contrib:dockerfile_build.bzl", "dockerfile_image")


container_pull(
    name = "alpine_linux_amd64",
    digest = "sha256:954b378c375d852eb3c63ab88978f640b4348b01c1b3456a024a81536dafbbf4",
    registry = "index.docker.io",
    repository = "library/alpine",
    # tag field is ignored since digest is set
    tag = "3.8",
)


container_pull(
    name = "ubuntu_22_04_amd64",
    digest = "sha256:cd3d86f1fb368c6a53659d467560010ab9e0695528127ea336fe32f68f7ba09f",
    registry = "index.docker.io",
    repository = "library/ubuntu",
    # tag field is ignored since digest is set
    tag = "22.04",
)

dockerfile_image(
    name = "basic_alpine_dockerfile",
    dockerfile = "//docker-alpine:Dockerfile",
)
dockerfile_image(
    name = "basic_ubuntu_dockerfile",
    dockerfile = "//docker-ubuntu:Dockerfile",
)

