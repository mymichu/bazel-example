# Copyright 2017 The Bazel Authors. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("@io_bazel_rules_docker//container:container.bzl", "container_image")
load("@io_bazel_rules_docker//contrib:test.bzl", "container_test")

container_image(
    name = "basic_ubuntu",
    base = "@ubuntu_22_04_amd64//image",
    cmd = ["Hello Michel!"],
    entrypoint = ["echo"],
)

# Tests
container_test(
    name = "basic_ubuntu_bazel_test",
    configs = ["//docker-ubuntu/test_configs:basic_ubuntu.yaml"],
    image = ":basic_ubuntu",
)

#container_test(
#    name = "basic_ubuntu_dockerfile_test",
#    configs = ["//docker-ubuntu/test_configs:basic_ubuntu_2.yaml"],
#    driver = "tar",
#    image = "@basic_ubuntu_dockerfile//image:dockerfile_image",
#)
