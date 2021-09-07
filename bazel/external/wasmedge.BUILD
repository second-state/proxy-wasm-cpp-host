load("@rules_cc//cc:defs.bzl", "cc_library")

licenses(["notice"])  # Apache 2

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "wasmedge_lib",
    srcs = ["lib64/libwasmedge_c.so"],
    hdrs = ["include/wasmedge.h"],
    strip_include_prefix = "include/",
)
