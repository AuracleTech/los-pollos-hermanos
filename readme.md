== build docker environment
docker build buildenv -t myos-buildenv

== enter docker build environment
docker run --rm -it -v "%cd%":/root/env myos-buildenv

== build
make build-x86_64

== launch iso
qemu-system-x86_64 -cdrom dist/x86_64/kernel.iso
