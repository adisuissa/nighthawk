licenses(["notice"])  # Apache 2

load(
    "@envoy//bazel:envoy_build_system.bzl",
    "envoy_cc_library",
    "envoy_package",
)

envoy_package()

envoy_cc_library(
    name = "request_impl_lib",
    hdrs = [
        "request_impl.h",
    ],
    repository = "@envoy",
    visibility = ["//visibility:public"],
    deps = [
        ":nighthawk_common_lib",
        "//include/nighthawk/common:request_lib",
    ],
)

envoy_cc_library(
    name = "request_stream_grpc_client_lib",
    srcs = ["request_stream_grpc_client_impl.cc"],
    hdrs = ["request_stream_grpc_client_impl.h"],
    repository = "@envoy",
    deps = [
        ":request_impl_lib",
        "//api/client:base_cc_proto",
        "//api/request_source:grpc_request_source_service_lib",
        "//include/nighthawk/common:base_includes",
        "//include/nighthawk/common:request_lib",
        "@envoy//include/envoy/grpc:async_client_interface_with_external_headers",
        "@envoy//include/envoy/grpc:async_client_manager_interface_with_external_headers",
        "@envoy//include/envoy/upstream:cluster_manager_interface_with_external_headers",
        "@envoy//source/common/common:assert_lib_with_external_headers",
        "@envoy//source/common/common:minimal_logger_lib_with_external_headers",
        "@envoy//source/common/grpc:typed_async_client_lib_with_external_headers",
        "@envoy//source/common/http:header_map_lib_with_external_headers",
        "@envoy//source/common/http:headers_lib_with_external_headers",
    ],
)

envoy_cc_library(
    name = "request_source_impl_lib",
    srcs = [
        "request_source_impl.cc",
    ],
    hdrs = [
        "request_source_impl.h",
    ],
    repository = "@envoy",
    visibility = ["//visibility:public"],
    deps = [
        ":nighthawk_common_lib",
        ":request_impl_lib",
        ":request_stream_grpc_client_lib",
        "//include/nighthawk/common:request_source_lib",
    ],
)

envoy_cc_library(
    name = "nighthawk_common_lib",
    srcs = [
        "phase_impl.cc",
        "rate_limiter_impl.cc",
        "sequencer_impl.cc",
        "statistic_impl.cc",
        "termination_predicate_impl.cc",
        "uri_impl.cc",
        "utility.cc",
        "version_info.cc",
        "worker_impl.cc",
    ],
    hdrs = [
        "cached_time_source_impl.h",
        "frequency.h",
        "phase_impl.h",
        "platform_util_impl.h",
        "rate_limiter_impl.h",
        "sequencer_impl.h",
        "statistic_impl.h",
        "termination_predicate_impl.h",
        "uri_impl.h",
        "utility.h",
        "version_info.h",
        "worker_impl.h",
    ],
    repository = "@envoy",
    visibility = ["//visibility:public"],
    deps = [
        "//api/client:base_cc_proto",
        "//api/client:grpc_service_lib",
        "//include/nighthawk/client:client_includes",
        "//include/nighthawk/common:base_includes",
        "@com_google_absl//absl/random",
        "@dep_hdrhistogram_c//:hdrhistogram_c",
        "@envoy//source/common/common:assert_lib_with_external_headers",
        "@envoy//source/common/common:lock_guard_lib_with_external_headers",
        "@envoy//source/common/common:macros_with_external_headers",
        "@envoy//source/common/common:minimal_logger_lib_with_external_headers",
        "@envoy//source/common/common:thread_lib_with_external_headers",
        "@envoy//source/common/common:version_includes_with_external_headers",
        "@envoy//source/common/http:utility_lib_with_external_headers",
        "@envoy//source/common/network:utility_lib_with_external_headers",
        "@envoy//source/common/protobuf:utility_lib_with_external_headers",
        "@envoy//source/common/stats:stats_lib_with_external_headers",
        "@envoy//source/exe:envoy_common_lib_with_external_headers",
        "@envoy//source/server/config_validation:server_lib_with_external_headers",
    ],
)
