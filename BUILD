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
load("@score_cr_checker//:cr_checker.bzl", "copyright_checker")

platform(
    name = "x86_64_qnx",
    constraint_values = [
        "@platforms//cpu:x86_64",
        "@platforms//os:qnx",
    ],
    visibility = ["//visibility:public"],
)

test_suite(
    name = "format.check",
    tests = ["//tools/format:format.check"],
)

alias(
    name = "format.fix",
    actual = "//tools/format:format.fix",
)

copyright_checker(
    name = "copyright",
    srcs = [
        ".github",
        "BUILD",
        "MODULE.bazel",
        "tests",
        "toolchain",
        "tools",
    ] + glob([
        "*.bzl",
    ]),
    config = "@score_cr_checker//resources:config",
    offset = 24,
    template = "@score_cr_checker//resources:templates",
    visibility = ["//visibility:public"],
)

exports_files(
    [
        "MODULE.bazel",
    ],
    visibility = [
        "//tools/format:__pkg__",
    ],
)
