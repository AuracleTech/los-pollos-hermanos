#### windows - build docker environment

```cmd
docker build buildenv -t pollos-buildenv
```

#### windows - enter the docker environment

```cmd
docker run --rm -it -v "%cd%":/root/env pollos-buildenv
```

#### docker environment - build the OS image

```bash
make build-x86_64
```

#### qemu - launch the OS image

```cmd
qemu-system-x86_64 -cdrom dist/x86_64/kernel.iso
```
