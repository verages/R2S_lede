<!--
 * @Author: wayne
 * @LastEditors: wayne
 * @email: linzhihui@szarobots.com
 * @Date: 2022-06-20 13:58:02
 * @LastEditTime: 2022-12-27 14:16:13
 * @Description: 
-->
# Actions-OpenWrt

# 说明

1. 该项目基于[P3TERX/Actions-OpenWrt](https://github.com/P3TERX/Actions-OpenWrt)修改，仅保留actions部分。
2. 集成了大量第三方脚本，该项目脚本仅保留我所需要的脚本。
3. 如需查看固件内所继承的脚本，可复制.config自行查看。
4. 将该仓库导入自己github下，点击 [这里](https://github.com/verages/R2S_lede/generate)。

## 本地编译设置环境方法
可通过clash同时通过export声明环境变量完成科学上网设置

## 本地导出或查看.config文件(以下操作在能科学上网UBuntu20.04进行)并编译

```bash
sudo apt update -y
sudo apt full-upgrade -y
sudo apt install -y ack antlr3 aria2 asciidoc autoconf automake autopoint binutils bison build-essential \
bzip2 ccache cmake cpio curl device-tree-compiler fastjar flex gawk gettext gcc-multilib g++-multilib \
git gperf haveged help2man intltool libc6-dev-i386 libelf-dev libglib2.0-dev libgmp3-dev libltdl-dev \
libmpc-dev libmpfr-dev libncurses5-dev libncursesw5-dev libreadline-dev libssl-dev libtool lrzsz \
mkisofs msmtp nano ninja-build p7zip p7zip-full patch pkgconf python2.7 python3 python3-pip libpython3-dev qemu-utils \
rsync scons squashfs-tools subversion swig texinfo uglifyjs upx-ucl unzip vim wget xmlto xxd zlib1g-dev
mkdir ~/openwrt && cd ~/openwrt
git clone https://github.com/coolsnowwolf/lede && git clone https://github.com/verages/R2S_lede
cd lede
sed -i '$a src-git kenzo https://github.com/kenzok8/openwrt-packages' feeds.conf.default
sed -i '$a src-git small https://github.com/kenzok8/small' feeds.conf.default
./scripts/feeds update -a && ./scripts/feeds install -a
#复制本仓库中的.config文件到lede源码中查看修改
cp ../R2S_lede/r2s.config ./.config
make menuconfig
#编译 本地编译
make -j8 download V=s
make -j1 V=s

```

## action操作

- 在actions页面选择 `Build OpenWrt`.
- 点击 `Run workflow`.
- 固件在`releases`处下载。

## 其他操作可参考

- [lede源码](https://github.com/coolsnowwolf/lede)
- [actions源码](https://github.com/P3TERX/Actions-OpenWrt)
- [第三方集成](https://github.com/kenzok8/openwrt-packages)

