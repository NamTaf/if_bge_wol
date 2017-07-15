# if_bge_wol
Patch to enable Wake on LAN for the if_bge driver on FreeBSD 11.1. Tested on HP Proliant Microserver N36L on 11.1-RELEASE-p9

### Instructions
* cd /usr/src/sys/dev/bge/
* patch if_bge.c < if_bge.c.patch
* cd /usr/src/sys/modules/bge/
* make
* make install
* cp ./if_bge.ko /kernel/modules/
* clean

To test:
* shutdown -r now
* 'ifconfig bge0' should show `WOL_MAGIC` under `OPTIONS`

### History
* Update of my previous PR for 10.1-RELEASE [here](https://bitbucket.org/w4w/bge-wol-freebsd-10.1-patch/pull-requests/1/patch-to-fix-for-svn-version-282752-and/diff).

### Credits
* Thanks to Nicola T (w4w) for the BitBucket patch & explanation [here](https://bitbucket.org/w4w/bge-wol-freebsd-10.1-patch).
* Thanks to zoon01 & daoyama for the original NAS4Free 9.1 patch [here](https://sourceforge.net/p/nas4free/code/HEAD/tree/branches/9.1.0.1/build/kernel-patches/bge/files/patch-if_bge.diff#l25).
