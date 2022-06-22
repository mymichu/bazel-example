load("@io_bazel_rules_docker//container:container.bzl", "container_image")
load("@io_bazel_rules_docker//docker/util:run.bzl","container_run_and_extract")
container_image(
    name = "app_image",
    # References container_pull from WORKSPACE (above)
    base = "@basic_ubuntu_dockerfile//image:dockerfile_image.tar",
    files = ["//app:main.cpp","//app:CMakeLists.txt"],
    directory = "/app"
)

container_run_and_extract(
    name = "app_build",
    commands = [
        "cd /app",
        "cmake -G Ninja -S . -B build",
        "cmake --build build",  
    ],
    extract_file = "/app/build/app",
    image = ":app_image.tar"
)