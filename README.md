# intel-gpgpu-debian-arm64
scratchpad area; intel-compute-runtime / intel-graphics-compiler packaging for debian bookworm arm64
---

I'm currently in the middle of trying to get an Intel ARC A380 graphics card working with OpenCL on a Raspberry Pi 5

This was the recipe I used to get packages built in a Raspbian/Debian Bookworm chroot c/o qemu-static-aarch64

---

1) Get all the build deps, libraries, and sources

```
apt-get build-dep intel-opencl-icd intel-graphics-compiler ...

apt-get source intel-graphics-runtime intel-compute-runtime libze-dev
```
2) Replace files in the source directories with what's in this repo.

Note: Nothing major has changed other than ensuring things are compiled correctly for arm64 -- and unit tests for intel-graphics-runtime is disabled.
For whatever reason it kept making qemu-static-aarch64 bomb out (SIGABRT!) pre-packaging.

3) debuild / dpkg-buildpackage away. Disable gpg signing.

Good luck, have fun!

-morb
