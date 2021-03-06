# Description:
#   Contains ops for evaluation metrics and summary statistics.
#   APIs here are meant to evolve over time.

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

package(default_visibility = ["//tensorflow:__subpackages__"])

load("//tensorflow:tensorflow.bzl", "cuda_py_tests")

py_library(
    name = "metrics_py",
    srcs = ["__init__.py"] + glob(["python/ops/*.py"]) + glob(["python/metrics/*.py"]),
    srcs_version = "PY2AND3",
)

cuda_py_tests(
    name = "metrics_ops_test",
    size = "medium",
    srcs = glob(["python/kernel_tests/*_test.py"]),
    additional_deps = [
        ":metrics_py",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:platform_test",
    ],
)

py_test(
    name = "classification_test",
    srcs = ["python/metrics/classification_test.py"],
    srcs_version = "PY2AND3",
    deps = [
        ":metrics_py",
        "//tensorflow:tensorflow_py",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:platform_test",
    ],
)

py_test(
    name = "metric_ops_test",
    srcs = ["python/ops/metric_ops_test.py"],
    srcs_version = "PY2AND3",
    deps = [
        ":metrics_py",
        "//tensorflow:tensorflow_py",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:platform_test",
    ],
)

filegroup(
    name = "all_files",
    srcs = glob(
        ["**/*"],
        exclude = [
            "**/METADATA",
            "**/OWNERS",
        ],
    ),
    visibility = ["//tensorflow:__subpackages__"],
)
