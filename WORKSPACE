http_archive(
    name = "io_bazel_rules_go",
    sha256 = "af4281751a0e3b5d87fb6a52c83d358871b4f83d7acbe6e65a901fba6612a03e",
    strip_prefix = "rules_go-bdf2df58c0d352ffa262ae4b36c7a1a2d6e3f0c9",
    urls = ["https://github.com/bazelbuild/rules_go/archive/bdf2df58c0d352ffa262ae4b36c7a1a2d6e3f0c9.tar.gz"],
)

http_archive(
    name = "io_kubernetes_build",
    sha256 = "f4946917d95c54aaa98d1092757256e491f8f48fd550179134f00f902bc0b4ce",
    strip_prefix = "repo-infra-c75960142a50de16ac6225b0843b1ff3476ab0b4",
    urls = ["https://github.com/kubernetes/repo-infra/archive/c75960142a50de16ac6225b0843b1ff3476ab0b4.tar.gz"],
)

http_archive(
    name = "bazel_skylib",
    sha256 = "bbccf674aa441c266df9894182d80de104cabd19be98be002f6d478aaa31574d",
    strip_prefix = "bazel-skylib-2169ae1c374aab4a09aa90e65efe1a3aad4e279b",
    urls = ["https://github.com/bazelbuild/bazel-skylib/archive/2169ae1c374aab4a09aa90e65efe1a3aad4e279b.tar.gz"],
)

ETCD_VERSION = "3.2.14"

new_http_archive(
    name = "com_coreos_etcd",
    build_file = "third_party/etcd.BUILD",
    sha256 = "f77398f558ff19b65a0bf978b47868e03683f27090c56c054415666b1d78bf42",
    strip_prefix = "etcd-v%s-linux-amd64" % ETCD_VERSION,
    urls = ["https://github.com/coreos/etcd/releases/download/v%s/etcd-v%s-linux-amd64.tar.gz" % (ETCD_VERSION, ETCD_VERSION)],
)

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "c440717ee9b1b2f4a1e9bf5622539feb5aef9db83fc1fa1517818f13c041b0be",
    strip_prefix = "rules_docker-8bbe2a8abd382641e65ff7127a3700a8530f02ce",
    urls = ["https://github.com/bazelbuild/rules_docker/archive/8bbe2a8abd382641e65ff7127a3700a8530f02ce.tar.gz"],
)

load("@bazel_skylib//:lib.bzl", "versions")

versions.check(minimum_bazel_version = "0.10.0")

load("@io_bazel_rules_go//go:def.bzl", "go_rules_dependencies", "go_register_toolchains", "go_download_sdk")
load("@io_bazel_rules_docker//docker:docker.bzl", "docker_repositories", "docker_pull")

go_rules_dependencies()

go_register_toolchains(
    go_version = "1.9.3",
)

docker_repositories()

http_file(
    name = "kubernetes_cni",
    sha256 = "f04339a21b8edf76d415e7f17b620e63b8f37a76b2f706671587ab6464411f2d",
    url = "https://storage.googleapis.com/kubernetes-release/network-plugins/cni-plugins-amd64-v0.6.0.tgz",
)

docker_pull(
    name = "debian-iptables-amd64",
    digest = "sha256:fb18678f8203ca1bd2fad2671e3ebd80cb408a1baae423d4ad39c05f4caac4e1",
    registry = "k8s.gcr.io",
    repository = "debian-iptables-amd64",
    tag = "v10",  # ignored, but kept here for documentation
)

docker_pull(
    name = "debian-hyperkube-base-amd64",
    digest = "sha256:fc1b461367730660ac5a40c1eb2d1b23221829acf8a892981c12361383b3742b",
    registry = "k8s.gcr.io",
    repository = "debian-hyperkube-base-amd64",
    tag = "0.8",  # ignored, but kept here for documentation
)

docker_pull(
    name = "official_busybox",
    digest = "sha256:4cee1979ba0bf7db9fc5d28fb7b798ca69ae95a47c5fecf46327720df4ff352d",
    registry = "index.docker.io",
    repository = "library/busybox",
    tag = "latest",  # ignored, but kept here for documentation
)
