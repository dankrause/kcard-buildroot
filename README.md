kcard-buildroot
===============

Buildroot configuration for building a custom rootfs for KeyASIC WifiSD based cards. This does not currently build a kernel, but that is [planned](https://github.com/dankrause/kcard-buildroot/issues/9). Check the [releases](https://github.com/dankrause/kcard-buildroot/releases) section for pre-built images that are ready to use immediately.

To build your own image on Ubuntu/RHEL/Centos derivatives:

```bash
# install buildroot dependencies (this list may be incomplete - contributions welcome)
# Using apt-get:
sudo apt-get install build-essential bison flex gettext libncurses5-dev texinfo autoconf automake libtool
# OR using Yum:
sudo yum install subversion make gcc ncurses-devel bison flex gawk bc vim-common

# clone kcard-buildroot
git clone https://github.com/dankrause/kcard-buildroot.git

# Update submodules
cd kcard-buildroot
git submodule init
git submodule update

# tell buildroot to start using the buildroot conf file that comes with kcard-buildroot
make wifisd_defconfig

# build a rootfs
make
```


Once the build is complete, you should have an image (`output/images/initramfs3.gz`) ready for writing to your device. You still need to grab the kernel from [Dmitry Grinberg](http://dmitry.gr/index.php?r=05.Projects&proj=15.%20Transcend%20WiFiSD) if you haven't already.
