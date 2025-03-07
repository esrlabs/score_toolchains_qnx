# Bazel toolchains for QNX

This module implements support for [QNX SDP 8.0](https://www.qnx.com/products/everywhere/index.html)

## Usage

MODULE.bazel
```
bazel_dep(name = "score_toolchains_qnx", version = "0.1")

toolchain_qcc = use_extension("@score_toolchains_qnx//:extensions.bzl", "toolchain_qcc")
toolchain_qcc.sdp(
    url = "http://example.com/qnx800.tar.gz",
    sha256 = "<package sha256>",
)

use_repo(toolchain_qcc, "toolchain_qcc_sdp")
use_repo(toolchain_qcc, "toolchain_qcc")

register_toolchains("@toolchain_qcc//:qcc_x86_64")
```

.bazelrc
```
build:x86_64_qnx --incompatible_strict_action_env
build:x86_64_qnx --platforms=@score_toolchains_qnx//:x86_64_qnx
build:x86_64_qnx --sandbox_writable_path=/var/tmp
```

```/var/tmp``` needs to be writeable inside of the sandbox because of the license management done by the QNX tools.

## Where to obtain the QNX 8.0 SDP

Follow the tutorial to obtain the SDP and corresponding license and install SDP via Software Center: 
- https://www.youtube.com/watch?v=DtWA5E-cFCo
- https://www.youtube.com/watch?v=s8_rvkSfj10

The QNX SDP is by default installed to ```~/qnx800```.
The archive of this directory is the input for the toolchain_qcc extension.

It is currently assumed that the license is deployed to ```/opt/score_qnx/license/licenses```.
By default QNX tooling installs the license in ```~/.qnx/license/licenses```.
