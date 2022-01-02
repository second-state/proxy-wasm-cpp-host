load("@rules_foreign_cc//foreign_cc:defs.bzl", "cmake")

licenses(["notice"])  # Apache 2

package(default_visibility = ["//visibility:public"])

filegroup(
    name = "srcs",
    srcs = glob(["**"]),
)

cmake(
    name = "wasmedge_lib",
    cache_entries = {
        # "LLVM_DIR": "$EXT_BUILD_DEPS/copy_llvm/llvm/lib/cmake/llvm",
        "WASMEDGE_BUILD_AOT_RUNTIME": "Off",
        "WASMEDGE_BUILD_SHARED_LIB": "Off",
        "WASMEDGE_BUILD_STATIC_LIB": "On",
        "WASMEDGE_BUILD_TOOLS": "Off",
        "WASMEDGE_FORCE_DISABLE_LTO": "On",
    },
    env_vars = {
        # Workaround for the -DDEBUG flag added in fastbuild on macOS,
        # which conflicts with DEBUG macro used in LLVM.
        "CFLAGS": "-UDEBUG",
        "CXXFLAGS": "-UDEBUG",
        "ASMFLAGS": "-UDEBUG",
    },
    generate_args = ["-GNinja"],
    lib_source = ":srcs",
    out_static_libs = [
        "libwasmedge_c.a"
    ],
)
