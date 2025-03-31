# *******************************************************************************
# Copyright (c) 2025 Contributors to the Eclipse Foundation
#
# See the NOTICE file(s) distributed with this work for additional
# information regarding copyright ownership.
#
# This program and the accompanying materials are made available under the
# terms of the Apache License Version 2.0 which is available at
# https://www.apache.org/licenses/LICENSE-2.0
#
# SPDX-License-Identifier: Apache-2.0
# *******************************************************************************
load(":cc_toolchain_config.bzl", "cc_toolchain_config")

filegroup(
    name = "all_files",
    srcs = [
        "@%{toolchain_sdp}//:all_files",
    ],
)

filegroup(
    name = "empty",
)

cc_toolchain_config(
    name = "qcc_toolchain_config",
    ar_binary = "@%{toolchain_sdp}//:ar",
    cc_binary = "@%{toolchain_sdp}//:qcc",
    cxx_binary = "@%{toolchain_sdp}//:qpp",
    strip_binary = "@%{toolchain_sdp}//:strip",
    qnx_host = "@%{toolchain_sdp}//:host_dir",
    qnx_target = "@%{toolchain_sdp}//:target_dir",
    cxx_builtin_include_directories = "@%{toolchain_sdp}//:cxx_builtin_include_directories",
)

cc_toolchain(
    name = "qcc_toolchain",
    all_files = ":all_files",
    ar_files = ":all_files",
    as_files = ":all_files",
    compiler_files = ":all_files",
    dwp_files = ":empty",
    linker_files = ":all_files",
    objcopy_files = ":empty",
    strip_files = ":all_files",
    toolchain_config = ":qcc_toolchain_config",
)

toolchain(
    name = "qcc_x86_64",
    exec_compatible_with = [
        "@platforms//cpu:x86_64",
        "@platforms//os:linux",
    ],
    target_compatible_with = [
        "@platforms//cpu:x86_64",
        "@platforms//os:qnx",
    ],
    toolchain = ":qcc_toolchain",
    toolchain_type = "@bazel_tools//tools/cpp:toolchain_type",
    visibility = [
        "//:__pkg__",
    ]
)
