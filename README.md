transient
---------

`transient` is a utility for runing QEMU with existing disk images and shared folders.
Currently `transient` only supports [Vagrant](https://www.vagrantup.com/) images.

Usage
-----

`transient` is primarily a wrapper for QEMU. It supplies a small set of flags that
are used to add additional features to the VM being started. As the name implies,
it is almost completely stateless. This avoids problems that can sometimes occur
with `libvirt` based tools becoming 'unsynchronized' with the real system state.

For example, in the following command, the flags before the `--` are passed to
`transient`. The remaining arguments are passed directly to QEMU. This example
will cause `transient` to download and run a Centos7 VM (from the Vagrant Cloud)
with 1GB of memory using a text console. The `name` parameter is used to allow
subseqent invocations to use the same disk image, so changes will persist.

```
python -m transient \
   -name test-vm \
   -image centos/7:2004.01 \
   -- \
   -nographic -enable-kvm -m 1G
```