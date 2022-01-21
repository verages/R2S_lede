# Actions-OpenWrt

# 说明

1. 该项目基于[P3TERX/Actions-OpenWrt](https://github.com/P3TERX/Actions-OpenWrt)修改，仅保留actions部分。
2. 集成了大量第三方脚本，该项目脚本仅保留我所需要的脚本。
3. 如需查看固件内所继承的脚本，可复制.config自行查看。
4. 将该仓库导入自己github下，点击 [这里](https://github.com/verages/R2S_lede/generate)。

## 本地导出或查看.config文件(以下操作在能科学上网的桌面版UBuntu20.04进行)并编译

```bash
sudo apt-get update
sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch python3 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf wget curl swig rsync
git clone https://github.com/coolsnowwolf/lede
cd lede
sed -i '$a src-git kenzo https://github.com/kenzok8/openwrt-packages' feeds.conf.default
sed -i '$a src-git small https://github.com/kenzok8/small' feeds.conf.default
./scripts/feeds update -a
./scripts/feeds install -a
make menuconfig
#或复制本仓库中的.config文件到lede源码中查看修改
cd ../
git clone https://github.com/verages/R2S_lede
cp ./R2S_lede/.config ./lede/
make menuconfig
#编译 本地编译
make -j8 download V=s
make -j1 V=s
#action 编译
gedit .config 
#全选复制内容到本仓库的.config内进行替换
```

## action操作

- 在actions页面选择 `Build OpenWrt`.
- 点击 `Run workflow`.
- 固件在`releases`处下载。

## 其他操作可参考

- [lede源码](https://github.com/coolsnowwolf/lede)
- [actions源码](https://github.com/P3TERX/Actions-OpenWrt)
- [第三方集成](https://github.com/kenzok8/openwrt-packages)

