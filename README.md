# kbuild-progress

Show progress information for Kbuild as below.

```
18.78% ETA 0:04:56   CC      net/netfilter/nf_conntrack_proto_udp.o
18.86% ETA 0:04:56   CC      lib/list_sort.o
18.86% ETA 0:04:56   AS      arch/x86/lib/memset_64.o
18.94% ETA 0:04:56   CC      arch/x86/lib/misc.o
18.94% ETA 0:04:56   AS      arch/x86/lib/putuser.o
19.02% ETA 0:04:56   CC      lib/uuid.o
19.02% ETA 0:04:56   AS      arch/x86/lib/retpoline.o
19.10% ETA 0:04:56   CC      arch/x86/lib/usercopy.o
19.18% ETA 0:04:56   CC      lib/iov_iter.o
19.26% ETA 0:04:53   CC      net/ipv4/ip_input.o
19.34% ETA 0:04:53   CC      fs/direct-io.o
19.42% ETA 0:04:53   CC      drivers/acpi/fan.o
```

## Usage

`./kbuild-progress [make args]`

Use `./kbuild-progress` instead of `make` command

### Example

```
$ cd linux-x.x.x
$ ./(path to kbuild-progress dir)/kbuild-progress -j4 vmlinux
```

## How it works

1. Use the `-n` option of the `make` command to know in advance what kind of work is required for C compilation of kernel build. This work takes 1 second (`make allnoconfig`)\* to 14 seconds (`make allyesconfig`)\*, often 2.5 seconds(`make defconfig`)\*.
1. Run the actual build without the `-n` option. Based on this information and the messages displayed in the actual build, kbuild-progress displays progress information.

\*Measured with [my ThinkPad E14](./my-thinkpad-e14-spec.log)

# Licence

GPL-2.0
