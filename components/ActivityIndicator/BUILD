# Copyright 2017-present The Material Components for iOS Authors. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("//:material_components_ios.bzl",
     "mdc_public_objc_library",
     "mdc_objc_library")
load("@build_bazel_rules_apple//apple:swift.bzl", "swift_library")
load("@build_bazel_rules_apple//apple:ios.bzl", "ios_unit_test")

licenses(["notice"])  # Apache 2.0

mdc_public_objc_library(
    name = "ActivityIndicator",
    bundles = [":Bundle"],
    sdk_frameworks = [
        "QuartzCore",
        "UIKit",
    ],
    deps = [
        "//components/Palettes",
        "//components/private/Application",
        "@material_internationalization_ios//:MDFInternationalization",
        "@motion_interchange_objc//:MotionInterchange",
        "@motion_animator_objc//:MotionAnimator",
    ],
)

filegroup(
    name = "BundleFiles",
    srcs = glob([
        "src/MaterialActivityIndicator.bundle/**",
    ]),
)

objc_bundle(
    name = "Bundle",
    bundle_imports = [":BundleFiles"],
)

swift_library(
    name = "unit_test_swift_sources",
    srcs = glob(["tests/unit/*.swift"]),
    deps = [":ActivityIndicator"],
    visibility = ["//visibility:private"],
)

mdc_objc_library(
    name = "unit_test_sources",
    testonly = 1,
    srcs = glob(["tests/unit/*.m"]),
    hdrs = glob(["tests/unit/*.h"]),
    sdk_frameworks = [
        "UIKit",
        "XCTest",
    ],
    deps = [":ActivityIndicator"],
    visibility = ["//visibility:private"],
)

ios_unit_test(
    name = "unit_tests",
    deps = [
      ":unit_test_sources",
      ":unit_test_swift_sources"
    ],
    minimum_os_version = "8.0",
    visibility = ["//visibility:private"],
)
