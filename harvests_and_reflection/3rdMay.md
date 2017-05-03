今天完成的是进一步熟悉了linux的相关命令以及讲Android系统从最底层的BootLoader，到中间的linux kernel，在最上层的Android的相关源码进行了编译。

以下逐项来进行说明：

# linux相关常用命令
以下内容是根据个人理解认为较为常用的命令的复习：

- cd 切换目录, 有 ., .., ./, empty等等的区别;
- rm -rf ./ 强制删除某文件
- ls [-al] ls为显示该文件夹目录，-a表示显示隐藏文件,-l表示的是完整类型的文件
- chmod  设置不同的权限，其中777为可读可写
- cp  拷贝文件，前者为待拷贝文件，后者为拷贝目标，如果不存在则重新创建
- reboot 重启
- shutdown 关机
- mkdir, touch 分别创建文件夹和文件
- cat 查看文件
- vi 以可修改模式查看文件
- clear 清屏
- tar [解]压缩，其中-c为创建包，-x释放包，-v显示过程，-z表示压缩包
- df 查看磁盘剩余空间
- mv 移动文件

# Android系统编译
Android系统的底层由三部分构成，分别为BootLoader，kernel和Android。其中Android有一个较为通用的BootLoader--u-boot，其硬件的初始化等等操作基本不需要做过多的修改工作。

对应的编译过程如下：

## u-boot编译与运行
- export PAHT=/usr/your route/bin:$PATH
- make distclean
- make

最后会生成u-boot.bin文件，是一个二进制文件，这个也就是u-boot的编译结果。

## kernel编译与运行
- export PATH=/usr/your route/bin:$PATH
- make distclean
- cd ebmv210.config .config
- make zImage

在boot目录下运行之后会生成zImage映像文件。

## Android系统的编译与运行
- export PATH=/usr/your route/bin:$PATH
- source ./build_env
- source ./build/envsetup.sh
- choosecombo [some needed default setup, remember to set product choice to embv210]
- make [almost one hour]
- ./make_embv210_yaffs2_image.sh

最后一行命令就是在编译之后生成系统的映像文件。
