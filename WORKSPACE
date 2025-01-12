workspace(name = "nene")

android_sdk_repository(
    name = "androidsdk",
    api_level = 31,
    # This is the latest version with dx.jar
    build_tools_version = "30.0.3",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_jar")

RULES_JVM_EXTERNAL_TAG = "4.2"

RULES_JVM_EXTERNAL_SHA = "cd1a77b7b02e8e008439ca76fd34f5b07aecb8c752961f9640dea15e9e5ba1ca"

http_archive(
    name = "rules_jvm_external",
    sha256 = RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    urls = [
        "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
    ],
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "androidx.activity:activity:1.4.0",
        "androidx.appcompat:appcompat:1.3.1",
        "androidx.browser:browser:1.4.0",
        "androidx.core:core-ktx:1.8.0",
        "androidx.fragment:fragment-ktx:1.4.1",
        "androidx.preference:preference:1.1.1",
        "com.google.android.material:material:1.6.1",
    ],
    maven_install_json = "@nene//:maven_install.json",
    repositories = [
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
    version_conflict_policy = "pinned",
)

load("@maven//:defs.bzl", "pinned_maven_install")

pinned_maven_install()

RULES_KOTLIN_TAG = "v1.6.0"

RULES_KOTLIN_SHA = "a57591404423a52bd6b18ebba7979e8cd2243534736c5c94d35c89718ea38f94"

http_archive(
    name = "io_bazel_rules_kotlin",
    sha256 = RULES_KOTLIN_SHA,
    urls = [
        "https://github.com/bazelbuild/rules_kotlin/releases/download/%s/rules_kotlin_release.tgz" % RULES_KOTLIN_TAG,
    ],
)

load("@io_bazel_rules_kotlin//kotlin:repositories.bzl", "kotlin_repositories")

kotlin_repositories()

register_toolchains("//:kotlin_toolchain")

BUNDLE_TOOL_TAG = "1.10.0"

BUNDLE_TOOL_SHA = "a5eee8fd22628c3f45662492498d3da38faf2bf2c64d425911492a5db6bc081c"

http_jar(
    name = "android_bundletool",
    sha256 = BUNDLE_TOOL_SHA,
    urls = [
        "https://github.com/google/bundletool/releases/download/%s/bundletool-all-%s.jar" % (BUNDLE_TOOL_TAG, BUNDLE_TOOL_TAG),
    ],
)

RULES_OPPIA_ANDROID_TAG = "v0.6"

RULES_OPPIA_ANDROID_SHA = "1d465ed74c32b98472401373305d57daca22de940ba5469acde4b0380c0cda4f"

http_archive(
    name = "rules_oppia_android",
    sha256 = RULES_OPPIA_ANDROID_SHA,
    strip_prefix = "oppia-android-%s" % RULES_OPPIA_ANDROID_TAG[1:],
    urls = [
        "https://github.com/oppia/oppia-android/archive/%s.zip" % RULES_OPPIA_ANDROID_TAG,
    ],
)
