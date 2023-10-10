# Soggy

Author is LDAsuku, this is only a zh-cn translated version

一款游戏服务器的模拟器，叫什么呢....?猜猜看叭~~~ 

![soggy cat](static/soggy_cat.png "soggy cat")

[设置步骤与文档］(https://nitter.pussthecat.org/sillysoggycat/)

## 在 GNU/Linux 上构建

```sh
# 安装依赖项（ubuntu）
apt install build-essential cmake libprotobuf-dev protobuf-compiler liblua5.3-dev
# 安装依赖项（arch linux）
pacman -S cmake protobuf lua
# 准备构建
cmake -B build
# 构建
cmake --build build -j8
```

## 在 Microsoft Windows 上使用 Visual Studio 构建

确保你在 Visual Studio 安装器中已选择 "C++ CMake tools for Windows"。

按照[vcpkg的文档](https://vcpkg.io/en/getting-started.html)安装 vcpkg。

```powershell
# 安装依赖项（vcpkg）
vcpkg install protobuf lua[cpp]:x64-windows
```

在 Visual Studio 中打开文件夹并构建。

## 在 Microsoft Windows 上使用 MSYS2/MinGW 构建

使用 MINGW64 终端。

```sh
# 安装依赖项
pacman -S ${MINGW_PACKAGE_PREFIX}-{toolchain,cmake,protobuf,lua}
# 准备构建
cmake -B build -G "Unix Makefiles"
# 构建
cmake --build build -j8
```

## 在 Microsoft Windows上使用WSL2的Ubuntu 22.04.2构建
使用微软商店(Microsoft Store)下载Ubuntu 22.04.2
clone本仓库并cd soggy-CHS
像正常在GNU/Linux平台上一样构建程序
修改soggy.cfg中ip为你的Ubuntu子系统分配的ip
IP能用```sh CMD ipconfig ```  查询
ping 一下保证连通
打开浏览器地址栏输入```sh 127.0.0.1:8099 ``` 若看到sogging cat 就表示成功。


## 运行

将 `resources` 目录和 `soggy.cfg` 放在当前工作目录中并运行 soggy。在交互提示符中输入 `help` 以查看命令列表。

`dispatch.py` 已经过时。游戏服务器现在有内置的调度服务器。

资源可以在仓库wiki中找到。

## 客户端补丁

```
=== GS.exe
# 禁用 AC
(VA=0x140ef5080, fileoffset=0xef4480) = c3

=== GS_Data/Native/UserAssembly.dll
# 冲刺无CD（能用ML的GmTalk开启无限体力infinite stamina on）
(VA=0x1802d1ef0, fileoffset=0x2d12f0) = b0 01 c3
# skill （技能无CD）
(VA=0x181ac998c, fileoffset=0x1ac8d8c) = 66 0f ef ff
# 跳过更新检查以稍微加快加载时间
(VA=0x18213221b, fileoffset=0x213161b) = 90 90 90 90 90 90
# 撅晕派蒙（去红圈地图边界）
(VA=0x182083430, fileoffset=0x2082830) = c3
```
