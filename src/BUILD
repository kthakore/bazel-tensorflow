# Description:
#   Tensorflow C++ inference example for labeling images.

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

cc_binary(
    name = "label_image",
    srcs = ["main.cc"],
    linkopts = ["-lm"],
    deps = [
        "@tf//tensorflow/cc:cc_ops",
        "@tf//tensorflow/core:tensorflow",
    ],
)

filegroup(
    name = "all_files",
    srcs = glob(
        ["**/*"],
        exclude = [
            "**/METADATA",
            "**/OWNERS",
            "bin/**",
            "gen/**",
        ],
    ),
    visibility = ["@tf//tensorflow:__subpackages__"],
)
