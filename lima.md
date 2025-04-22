the lima project. short for "linux machines". easy and clean way to make a linux VM on macOS using apple native hypervisor "vz"

dont bother with UTM

```
limactl create \
--plain \
--vm-type vz \
--name ubuntu2410 \
--arch aarch64 \
template://ubuntu-24.10
```
