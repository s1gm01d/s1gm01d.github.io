---
title: .text + 0x0
published: true
---

`DM_VERITY`

> dd if=/dev/zero of=rootfs.img bs=1M count=128

> mkfs.ext4 data.img

> mkfs.ext4 -b 4096 rootfs.img

> veritysetup format rootfs.img rootfs.dmverity > dmverity

> veritysetup verify rootfs.img rootfs.dmverity $HASH

> veritysetup create rootfs rootfs.img rootfs.dmverity $HASH

> mount -o noatime /dev/mapper/rootfs.img /rootfs 


`DM_INTEGRITY`

> dd if=/dev/zero of=data.img bs=1M count=32
>
> integritysetup format data.img --debug

> integritysetup open data.img data

> integritysetup status data
>
> mkfs.ext4 /dev/mapper/data

> mount /dev/mapper/data /data

> umount /data

> integritysetup close data (remove data from mapper) 


`runc`

> runc create container

> runc list

> runc exec container sh -i


* * *
