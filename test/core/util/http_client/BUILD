# Copyright 2016 gRPC authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("//bazel:grpc_build_system.bzl", "grpc_cc_library", "grpc_cc_test", "grpc_package")
load("//test/core/test_util:grpc_fuzzer.bzl", "grpc_fuzzer")

grpc_package(name = "test/core/util/http_client")

licenses(["notice"])

grpc_fuzzer(
    name = "response_fuzzer",
    srcs = ["response_fuzzer.cc"],
    corpus = "response_corpus",
    language = "C++",
    tags = ["no_windows"],
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/test_util:grpc_test_util",
    ],
)

grpc_fuzzer(
    name = "request_fuzzer",
    srcs = ["request_fuzzer.cc"],
    corpus = "request_corpus",
    language = "C++",
    tags = ["no_windows"],
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/test_util:grpc_test_util",
    ],
)

# Copyright 2017 gRPC authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

licenses(["notice"])

grpc_cc_library(
    name = "httpcli_test_util",
    testonly = True,
    srcs = ["httpcli_test_util.cc"],
    hdrs = ["httpcli_test_util.h"],
    external_deps = [
        "absl/log:check",
        "absl/log:log",
    ],
    deps = [
        "//:gpr",
        "//:subprocess",
        "//test/core/end2end:ssl_test_data",
        "//test/core/test_util:grpc_test_util",
        "//test/core/test_util:grpc_test_util_base",
    ],
)

grpc_cc_test(
    name = "httpcli_test",
    srcs = ["httpcli_test.cc"],
    data = [
        "python_wrapper.sh",
        "test_server.py",
        "//src/core/tsi/test_creds:server1.key",
        "//src/core/tsi/test_creds:server1.pem",
    ],
    external_deps = [
        "absl/log:check",
        "absl/log:log",
        "gtest",
    ],
    language = "C++",
    tags = ["no_windows"],
    deps = [
        ":httpcli_test_util",
        "//:gpr",
        "//:grpc",
        "//:subprocess",
        "//test/core/end2end:ssl_test_data",
        "//test/core/test_util:fake_udp_and_tcp_server",
        "//test/core/test_util:grpc_test_util",
        "//test/cpp/util:test_util",
    ],
)

grpc_cc_test(
    name = "httpscli_test",
    srcs = ["httpscli_test.cc"],
    data = [
        "python_wrapper.sh",
        "test_server.py",
        "//:subprocess",
        "//src/core/tsi/test_creds:ca.pem",
        "//src/core/tsi/test_creds:server1.key",
        "//src/core/tsi/test_creds:server1.pem",
    ],
    external_deps = [
        "absl/log:check",
        "absl/log:log",
        "gtest",
    ],
    language = "C++",
    tags = ["no_windows"],
    deps = [
        ":httpcli_test_util",
        "//:gpr",
        "//:grpc",
        "//src/core:channel_args",
        "//src/core:closure",
        "//test/core/end2end:ssl_test_data",
        "//test/core/test_util:fake_udp_and_tcp_server",
        "//test/core/test_util:grpc_test_util",
        "//test/cpp/util:test_util",
    ],
)

grpc_cc_test(
    name = "parser_test",
    srcs = ["parser_test.cc"],
    external_deps = ["gtest"],
    language = "C++",
    uses_event_engine = False,
    uses_polling = False,
    deps = [
        "//:gpr",
        "//:grpc",
        "//test/core/end2end:ssl_test_data",
        "//test/core/test_util:grpc_test_util",
        "//test/core/test_util:grpc_test_util_base",
    ],
)

grpc_cc_test(
    name = "format_request_test",
    srcs = ["format_request_test.cc"],
    external_deps = ["gtest"],
    language = "C++",
    deps = [
        "//:gpr",
        "//:grpc",
        "//src/core:slice",
        "//test/core/end2end:ssl_test_data",
        "//test/core/test_util:grpc_test_util",
        "//test/core/test_util:grpc_test_util_base",
    ],
)
