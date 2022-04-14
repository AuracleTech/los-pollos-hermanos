== build docker environment
docker build buildenv -t myos-buildenv

== enter docker build environment
docker run --rm -it -v "%cd%":/root/env myos-buildenv

== build
make build-x86_64

== launch iso
qemu-system-x86_64 -cdrom dist/x86_64/kernel.iso

<!--

# BUILD KERNEL FROM RUST FILES
$(kernel_object_files): build/kernel/%.o : src/impl/kernel/%.rs
	mkdir -p $(dir $@) && \
	rustc $(patsubst build/kernel/%.o, src/impl/kernel/%.rs, $@) --emit=obj --out-dir build/kernel/

# THIS IS FOR DOCKER
RUN apt-get install -y \
    build-essential \
    curl
RUN apt-get update
RUN curl https://sh.rustup.rs -sSf | bash -s -- -y
RUN echo 'source $HOME/.cargo/env' >> $HOME/.bashrc

-->
