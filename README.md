# mount\_uzip - Mount utility for uzip and ulzma on FreeBSD

  * package name: mount\_uzip
  * author: dearblue
  * license: public domain
  * project status: terminated with throwing
  * issue report to: /dev/null

Using ``mdconfig`` in ``mount_uzip``.


## How to usage

First, load ``geom_uzip`` and ``geom_uncompress``.

``` shell:shell
# kldload geom_uzip geom_uncompress
```

### Mount uzip'd UFS (from the creation to the mount)

``` shell:shell
$ makefs -o version=2 -o label=FreeBSD-10.2-src ~/uzip/FreeBSD-10.2-src /usr/src
$ mkuzip -s 65536 ~/uzip/FreeBSD-10.2-src
# mount_uzip ~/uzip/FreeBSD-10.2-src.uzip /usr/src
```

### Mount ``.iso.ulzma``

``` shell:shell
# mount_uzip -t cd9660 ~/uzip/FreeBSD-10.2-src.iso.ulzma /usr/src
```

### Describe ``/etc/fstab`` for ``.iso.ulzma``

``` conf:/etc/fstab
/usr/home/dearblue/uzip/FreeBSD-10.2-src.iso.ulzma  /usr/src  dummy_name  ro,-t=cd9660,mountprog=/usr/local/bin/mount_uzip  0 0
```
