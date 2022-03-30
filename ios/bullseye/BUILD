load("@build_bazel_rules_apple//apple:ios.bzl", "ios_application", "ios_unit_test")
load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library")

#config_setting(
#    name = "is_release",
#    values = { "define" : "release=true" }
#)

swift_library(
    name = "sources",
    module_name = "Bullseye",
    srcs = glob(["Bullseye/Sources/*.swift"]),
    data = [
       "Bullseye/App/Assets.xcassets",
    ],
    visibility = ["//visibility:public"],
)

swift_library(
    name = "tests",
    srcs = glob(["BullseyeTests/*.swift"]),
    visibility = ["//visibility:public"],
    deps = [":sources"],
    module_name = "BullseyeTests",
)

ios_unit_test(
    name = "ios_tests",
    deps = [":tests"],
    minimum_os_version = "14.0",
    test_host = ":app",
    platform_type = "ios",
    visibility = ["//visibility:public"]
)

ios_application(
    name = "app",
    deps = [ ":sources" ],
    bundle_id = "com.example.bullseye",
    families = [
        "iphone",
        "ipad",
    ],
    infoplists = ["Bullseye/App/Info.plist"],
    minimum_os_version = "14.0",
    visibility = ["//visibility:public"],
)