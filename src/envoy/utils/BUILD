# Copyright 2016 Istio Authors. All Rights Reserved.
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
#
################################################################################
#

load(
    "@envoy//bazel:envoy_build_system.bzl",
    "envoy_cc_library",
    "envoy_cc_test",
)

envoy_cc_library(
    name = "authn_lib",
    srcs = [
        "authn.cc",
    ],
    hdrs = [
        "authn.h",
    ],
    repository = "@envoy",
    visibility = ["//visibility:public"],
    deps = [
        ":filter_names_lib",
        ":utils_lib",
        "//include/istio/utils:attribute_names_header",
        "//src/istio/authn:context_proto_cc",
        "//src/istio/utils:attribute_names_lib",
        "//src/istio/utils:utils_lib",
        "@envoy//source/exe:envoy_common_lib",
    ],
)

envoy_cc_library(
    name = "utils_lib",
    srcs = [
        "config.cc",
        "grpc_transport.cc",
        "mixer_control.cc",
        "stats.cc",
        "utils.cc",
    ],
    hdrs = [
        "config.h",
        "grpc_transport.h",
        "header_update.h",
        "mixer_control.h",
        "stats.h",
        "trace_headers.h",
        "utils.h",
    ],
    repository = "@envoy",
    visibility = ["//visibility:public"],
    deps = [
        "//external:mixer_client_config_cc_proto",
        "//src/istio/control/http:control_lib",
        "//src/istio/mixerclient:mixerclient_lib",
        "@envoy//source/exe:envoy_common_lib",
    ],
)

envoy_cc_test(
    name = "authn_test",
    srcs = [
        "authn_test.cc",
    ],
    repository = "@envoy",
    deps = [
        ":authn_lib",
        "@envoy//test/test_common:utility_lib",
    ],
)

envoy_cc_test(
    name = "utils_test",
    srcs = [
        "utils_test.cc",
    ],
    repository = "@envoy",
    deps = [
        ":utils_lib",
        "@envoy//test/mocks/network:network_mocks",
        "@envoy//test/mocks/ssl:ssl_mocks",
        "@envoy//test/mocks/stream_info:stream_info_mocks",
        "@envoy//test/test_common:utility_lib",
    ],
)

envoy_cc_test(
    name = "mixer_control_test",
    srcs = [
        "mixer_control_test.cc",
    ],
    repository = "@envoy",
    deps = [
        ":utils_lib",
        "@envoy//test/test_common:utility_lib",
    ],
)

cc_library(
    name = "filter_names_lib",
    srcs = [
        "filter_names.cc",
    ],
    hdrs = [
        "filter_names.h",
    ],
    visibility = ["//visibility:public"],
)
