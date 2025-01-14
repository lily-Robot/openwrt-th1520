![image1](https://raw.githubusercontent.com/chainsx/openwrt-th1520/main/lpi4a.png)

## Getting started

### Prepare your environment

#### Install depend

```
sudo apt update -y
sudo apt install -y ack antlr3 asciidoc autoconf automake autopoint binutils bison build-essential \
bzip2 ccache cmake cpio curl device-tree-compiler fastjar flex gawk gettext gcc-multilib g++-multilib \
git gperf haveged help2man intltool libc6-dev-i386 libelf-dev libglib2.0-dev libgmp3-dev libltdl-dev \
libmpc-dev libmpfr-dev libncurses5-dev libncursesw5-dev libreadline-dev libssl-dev libtool lrzsz \
mkisofs msmtp nano ninja-build p7zip p7zip-full patch pkgconf python2.7 python3 python3-pyelftools \
libpython3-dev qemu-utils rsync scons squashfs-tools subversion swig texinfo uglifyjs upx-ucl unzip \
vim wget xmlto xxd zlib1g-dev
```

#### Clone OpenWrt source code

```
git clone https://github.com/chainsx/openwrt-th1520 --depth=1
```

#### Update feeds

```
cd openwrt-th1520/riscv-openwrt
./scripts/feeds update -a
./scripts/feeds install -a
cd ..
```

#### Apply build configure

```
cp lpi4a.config riscv-openwrt/
cd riscv-openwrt && make defconfig
```

#### Build openwrt

```
make download V=s -j$(nproc) && make V=s -j$(nproc)
```

### Simply start with the build script

```
bash build_all.sh
```

## How to flash

Reference [here](https://github.com/chainsx/fedora-riscv-builder/blob/main/doc/install-guild-licheepi4a.md).

### Flash openwrt image to micro SD card

The openwrt image will be generated under `riscv-openwrt/bin/target`, decompress it and write it to micro SD card.

## How to enable WiFi

```
wifi config
reboot
```

## Thanks

[Rabenda aka revy](https://github.com/Rabenda)

[saeziae](https://github.com/saeziae)
