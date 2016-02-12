load("BUILD.generated", "ssl_headers")
load("BUILD.generated", "ssl_internal_headers")
load("BUILD.generated", "ssl_sources")
load("BUILD.generated", "crypto_headers")
load("BUILD.generated", "crypto_internal_headers")
load("BUILD.generated", "crypto_sources")
load("BUILD.generated", "tool_sources")
load("BUILD.generated", "crypto_sources_linux_aarch64")
load("BUILD.generated", "crypto_sources_linux_arm")
load("BUILD.generated", "crypto_sources_linux_x86")
load("BUILD.generated", "crypto_sources_linux_x86_64")
load("BUILD.generated", "crypto_sources_mac_x86")
load("BUILD.generated", "crypto_sources_mac_x86_64")
load("BUILD.generated", "crypto_sources_win_x86")
load("BUILD.generated", "crypto_sources_win_x86_64")

config_setting(
    name = "linux_aarch64",
    values = {"cpu": "aarch64"},
)

config_setting(
    name = "linux_arm",
    values = {"cpu": "arm"},
)

config_setting(
    name = "linux_x86",
    values = {"cpu": "piii"},
)

config_setting(
    name = "linux_x86_64",
    values = {"cpu": "k8"},
)

cc_library(
    name = "crypto",
    srcs = crypto_internal_headers + crypto_sources + select({
        ":linux_aarch64": crypto_sources_aarch64,
        ":linux_arm": crypto_sources_linux_arm,
        ":linux_x86": crypto_sources_linux_x86,
        ":linux_x86_64": crypto_sources_linux_x86_64,
        "//conditions:default": crypto_sources_x86_64,
    }),
    hdrs = crypto_headers,
    includes = ["src/include"],
    visibility = ["//visibility:public"],
)

cc_library(
    name = "ssl",
    srcs = ssl_internal_headers + ssl_sources,
    hdrs = ssl_headers,
    includes = ["src/include"],
    visibility = ["//visibility:public"],
    deps = [
        ":crypto",
    ],
)

