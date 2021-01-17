# 我的 2021 日程记录

## 已完成内容

* (Day 4) YuLang 编译成功，可以正常使用
* (Day 4) GeeOS 编译成功
* (Day 5) GeeOS 在 QEMU 中运行成功
* (Day 13) Fuxi SoC 生成 bitstream 成功

## Before 2021

在 2020 年的最后一天，提前给将要到来的 2021 年制定一下计划，并尽量按计划每天记录下来，希望自己能达到想要的目标。

### 上半年计划

战线拉太长了不好，就先定半年的计划吧

1. 报名参加 OSCOMP 比赛，选题 [proj5-fuxi-full-system-with-cpu-compiler-os](https://github.com/oscomp/proj5-fuxi-full-system-with-cpu-compiler-os)
2. 学习 Chisel、YuLang，学习编译原理、网络原理，深入学习操作系统
3. 以 [RVM](https://github.com/rcore-os/RVM) 代码为基础，学习 CPU 虚拟化技术
4. 学有余力的情况下，跟 ICPC 的队友准备明年的区域赛，多用真题训练，提升自己的代码能力

大概先这样(?)，更具体的内容之后再补充吧

### Day 1 计划

1. 学习 Scala 及 Chisel
2. 配置 Linux 下的 FPGA 开发板的开发环境
3. 尝试写一些简单的 Chisel 小程序，然后烧到 FPGA 板子上并调试

#### 学习资料

* [Chisel 教程汇总 - csdn](https://blog.csdn.net/qq_34291505/article/details/86744581)
* [Chisel-Bootcamp](https://github.com/freechipsproject/chisel-bootcamp)
* FPGA 开发板文档（某宝店送的资料，在某度网盘里）

### 扯点别的

今天就是 2020 年的最后一天了，我也是刚从学校回到家，挺累的

所以——就先放纵一下吧，打打游戏看看跨年晚会啥的，明天正式开始学 Chisel（虽然之前已经接触过一丢丢了）

总结一下我的这一年吧，上半年摸鱼上网课，暑假爆肝做项目，下半年放弃考研找工作，年底事业爱情双丰收

在此还是要感谢一下陈老师和向老师给了我参加暑期活动的机会，凭我之前的经历写出的简历只能在济南勉强找到月入 5.5k 的工作，但有了暑假的项目后我成功拿到了字节跳动的 offer，我的感激之情无以言表

我选择记录我的 2021 日程，并参加 OSCOMP 的比赛，也是受到陈老师和向老师的影响，希望我也可以为开源社区贡献一份力量

2020 年唯一的遗憾可能就是放弃考研了吧，因为焦虑被迫放弃。虽然最后找工作的结果也还不错，但是我还是更向往能去贵系读研究生的生活

说得有点多了，嗯...就先这样吧

2021，我来了

## Day 1 2021-01-01

Chisel 基础学习完成，还没开始上手敲代码。今天完成的主要工作是配置 Chisel 环境并编译 Fuxi 处理器

`sbt` 第一次编译好慢，下载 Xilinx ISE DS 好慢，好多时间都用在这上面了，我应该一边配环境一边学习的

我之前有买过 FPGA 的板子，也参考一些书籍写过 MIPS 的 CPU，但是只在电脑上仿真过，并没有烧到板子上调试，所以这方面我也不是很懂，要从头开始学起

根据我参考的书，应该做的事情如下：

1. 完成 CPU 的代码（废话）
2. 为 CPU 编写 SoC 代码（不然只有处理器没有内存没有 ROM 什么的也用不成）（个人理解）
3. 安装 Xilinx ISE WebPACK 和 UrJTAG 软件
   * 其中，ISE WebPACK 包括 ISE Project Navigator 和 iMPACT，作用分别为：将 Verilog 源程序转换为 BIT 文件、将 BIT 文件转换成 SVF 文件，及将 BIT 文件转换为 MCS 文件再转换为 SVF 文件
   * UrJTAG 的作用为，将 BIT 直接生成的 SVF 文件写入 FPGA，并将 MCS 文件生成的 SVF 文件写入 ROM
4. 这样似乎就可以运行了(?)

但是我又在考虑要不要先在本地仿真来完善功能，比如编译一下 OpenSBI 或者 RustSBI，用之前写 CPU 的小工具把 SBI 的可执行文件转化成可以导入 Fuxi 处理器运行的（存着十六进制指令的）文本文件

思考了一下，也看了下这个 Project 中导师的预期目标，还是决定烧到 FPGA 里面会比较好一些

本来想第一个移植 luojia 大佬的 RustSBI，结果发现 release 里面只有 QEMU 和 K210 的版本，所以我先用 OpenSBI 试试 Fuxi SoC 的基本功能，等 OpenSBI 适配好了再尝试移植 RustSBI 试试～

然而...安装 Xilinx ISE WebPACK 的时候发现，我的 Linux 空间不够用了，这软件需要 23G，但是我的系统只有 1G 了，所以被迫去用 Windows 了，而且 Scala 和 Chisel 的环境还需要再重新配一遍...

先 push 一下，今晚还有些事情，定一下明天的计划就先撤了，虽然今天的计划没怎么完成...

### Day 1 进展

* 发现自己电脑硬盘不够用，没有进展

### Day 2 计划

1. 在 Windows 下配置 Chisel 以及 FPGA 所需环境
2. 将 Fuxi SoC 及 OpenSBI 烧录到 FPGA 板子上
3. 调试运行 OpenSBI

前两条估计很快就能解决，第三条战线可能会比较长了

## Day 2 2021-01-02

在 Windows 下折腾了大半天 `sbt` 和 ISE WebPACK，最终发现 Windows 的 ISE WebPACK 极其不稳定，打开文件都闪退

考虑了一番换硬盘还是换电脑的问题后，我决定换电脑，然后当即在某宝下单一台 ITX 整机，但是发货还要一段时间

这段时间我先把自己电脑重装掉，只留 Linux，先凑合用着，计划还是要进行的嘛，等主机到货之后就把现在用的电脑再格式化回 Windows，然后就这么用着吧，毕竟开学后还是要写毕业论文的，Windows 必不可少

### Day 2 进展

几乎没有进展

* 发现 Windows 下的 ISE 不好用
* 发现 32 位的 OpenSBI 编译很麻烦，而 release 里的二进制不知道能不能直接使用

### Day 3 计划

1. 把电脑全盘格式化成 Linux，为开发让路
2. 将 Fuxi SoC 及 OpenSBI 烧录到 FPGA 板子上
3. 有必要的话，将 OpenSBI 编译到 RV32ima 平台
4. 调试运行 OpenSBI

## Day 3 2021-01-03

配环境越来越熟练了，只用了一个小时就装好了 Linux 和 `sbt` 以及 ISE WebPACK，然后把 Fuxi SoC 编译成 Verilog 代码，综合没有问题，布线过程出了些错误，具体报错如下：

```
ERROR:Pack:2309 - Too many bonded comps of type "IOB" found to fit this device.
ERROR:Map:237 - The design is too large to fit the device.  Please check the Design Summary section to see which resource requirement for
   your design exceeds the resources available in the device. Note that the number of slices reported may not be reflected accurately as
   their packing might not have been completed.
```

查了下 Design Summary，发现：

```
IO Utilization:
  Number of bonded IOBs:                       664 out of     160  415% (OVERMAPPED)
```

由内容并结合 Google 查询，我认为报错的意思是，代码中的 IO 端口数量超过了 FPGA 板子可以设置的数量，但是如何解决，我一点头绪也没有...

最终经过了半个小时的 Google，找到了这样一个帖子：[Using Xilinx ISE 14.7, PCIe core implementation problem](https://www.edaboard.com/threads/using-xilinx-ise-14-7-pcie-core-implementation-problem.356126/)

4 楼有解释可能的原因，可能是因为一些需要写在内部的 IO 端口，都给放外边去了

经过一阵思考，我认为，整个 CPU 需要被 SoC 封装起来，目前不需要有对外的接口，但是 SoC 代码我看不懂，也不知道怎么用...就很尴尬

我还是去翻书吧，一些自制 CPU 的书籍，参考一下最上层的代码应该怎么封装

有必要的话，也可以参考一下 Rocket 或者 BOOM 的代码，如果里面有可以参考的内容的话...

20210103 傍晚补充：我觉得应该装一个 Vivado，而不是 ISE，然而 Vivado 用 Windows 就可以，没必要把电脑重装，也没必要买新电脑...

罢了罢了，Linux 开发更舒服，而且新电脑也可以玩赛博朋克，计划通(x

20210103 晚上补充：Vivado 装完了，可以直接打开 `soc` 目录里的工程文件，解决了大部分问题，但是综合报了一大堆错，而且我发现最新版 Vivado 并不支持我 Spartan-6 的板子...

查了下，原话是这样的：

```
The Vivado tool has been created for the 7 Series devices (Virtex-7, Kintex-7, Artix-7, and Zynq-7000). 

To support the Spartan-6 devices (or any non 7 Series devices), you will need to use the latest ISE design tools, which work best regardless of the complexity of the design.
```

好了，买新板子还是折腾 ISE 二选一吧

### Day 3 进展

* 知道了 Fuxi SoC 的使用方法，也知道了我的板子不适合拿来搞这个...

### Day 4 计划

1. 买板子，然后等收货
2. 编译 YuLang
3. 用 YuLang 编译 GeeOS，并在 QEMU 里跑起来

## Day 4 2021-01-04

昨晚下单了新板子，Artix-7 系的，没想到今天上午就发货了，意想不到的快。那么趁新主机和新板子都还没到的时间，先折腾下 YuLang 好了

此外，装 VS Code 的时候有点新发现，MaxXing 大佬已经制作了 YuLang 的 VS Code 高亮插件，可以用 VS Code 搞开发了

但是，编译 YuLang 的过程中也遇到了一些问题，YuLang 的 README 里写需要用 `llvm 8.0 or later`，但是我用的 LLVM 11，遇到了一些小问题，比如：

1. `src/back/llvm/objgen.cpp` 需要再 `#include "llvm/Support/Host.h"`；
2. `src/back/llvm/generator.cpp` 调用的 `CreateCall` 函数参数更新了，需要把 `llvm::Value *` 改成 `llvm::Callee *`，把 `std::Vector` 改成 `llvm::ArrayRef`；

20210104 下午补充：换成 LLVM 10 就没有问题了，看来是 LLVM 11 的新 feature，但是又遇到一些新的问题：

1. `make[3]: /usr/local/opt/llvm/bin/llc: 没有那个文件或目录`，解决方法：修改 `toolchain.mk`，把 `export LLC := $(LLVM_HOME)/llc $(LLCFLAGS)` 改成 `export LLC := llc $(LLCFLAGS)`
2. `clang` 没装会报个错，小问题
3. 装上 `clang` 之后会报：
   ```
   making example "array\_test"...
   /usr/bin/ld: /home/yukiteru/github/YuLang/build/obj/examples/array\_test.yu.o: relocation R\_X86\_64\_32 against symbol `out' can not be used when making a PIE object; recompile with -fPIE
   /usr/bin/ld: /home/yukiteru/github/YuLang/build/libyu.a(io.yu.o): warning: relocation in read-only section `.text'
   clang-11: error: linker command failed with exit code 1 (use -v to see invocation)
   ```
   是用 `clang` 编译时出现的链接问题，解决方法：在 `toolchain.mk` 里，给 `LDFLAGS` 加上 `-no-pie`

解决掉这些问题后，`yuc` 就成功被编译出来了～然后顺手 `ln -s` 到 `~/.local/bin` 里面，运行起来也方便

但是——GeeOS 的编译又出了不少问题：

1. `mkfs` 工具使用了 C++17 的类 `string_view`，并将 `string_view` 隐式传入需要 `string` 参数的函数，然而编译器报了错
   解决方法：将 `string_view` 变量套上 `string()` 或者在其后面添加 `.data()`，推荐后者
2. LLVM 工具链的路径问题，改 `toolchain.mk` 即可，还有找不到 `ld.lld`，装一个 `lld` 就好了
3. `objdump` 识别不了 RV32 的 elf 文件，给 `objdump` 加上 prefix 即可
4. `bin2coe.py` 无法直接运行，可能是我终端的问题，在 `src/Makefile` 里给加上 `python3` 就好了

经过以上改动，`geeos.elf` 就编译出来了，但是运行又出了问题。`cd` 进 `build`，然后照 README 写的命令运行，会报：

```
rom: requested regions overlap (rom phdr #0: build/geeos.elf. free=0x000000008000f2c0, addr=0x0000000080000000)
qemu-system-riscv32: rom check and register reset failed
```

网上查了下，看到了 openEuler 那边的 [issue](https://bugs.launchpad.net/qemu/+bug/1429841)，这可能是最新版 QEMU 才会出的问题，好像 4.x 版本的 QEMU 不会有问题

我是不是不该用 ArchLinux 的，LLVM 版本太新了，QEMU 版本也太新了...

唉，明天再重装系统吧，换成 Ubuntu 20.04，或者 18.04 也行，毕竟比赛最终编译是在这上面进行的

### Day 4 进展

* YuLang 编译成功，看起来一切正常
* GeeOS 编译成功，但是运行不起来

### Day 5 计划

1. 重装系统，把 ArchLinux 换成 Windows 10 + Ubuntu 18.04 (?)
2. 编译 YuLang + GeeOS，然后在 QEMU 上跑起来
3. fork 一份 YuLang 和 GeeOS，把一些跟比赛无关的内容，比如 `Makefile` 啥的改改，提交一份 PR，比赛有关的就先放自己仓库里，等结束了再提交
4. 把 GeeOS 在 QEMU 里运行起来好像也不是什么难事，那就先学下 YuLang，在 FPGA 板子到货之前先写着线程调度

## Day 5 2021-01-05

今天的时间都用在装系统上了。装了 Ubuntu 18.04，发现 `cmake` 版本太旧、`vim` 版本太旧、`g++` 默认版本太旧，受不了折腾这些东西，我就换了 Ubuntu 20.04

Ubuntu 20.04 基本一切正常，除了`apt` 里面的 QEMU 没有 RISCV 版本，我又自己从源码编译了一份 `qemu-system-riscv32`，4.2.1 的版本，运行一切正常，唯一的问题是我忘记该怎么退出 QEMU 了...

然后我又装上了 Windows，又在 Windows 下挂机装 Vivado，顺便学一下 YuLang。直到现在 Vivado 都还没装完，先睡觉！

明天估计我的板子就能到了，但是电脑还要大概一周才能到。就先用我的电脑凑合整吧，熟悉一下 Vivado 先，等新电脑到了就全部在 Linux 上开发了，还是 Linux 搞开发舒服啊

（另外，有机会可以学一下 Vim 插件怎么写，我整一个 Vim 的 YuLang 高亮插件也不错，不过自动补全可能有点难

### Day 5 进展

* GeeOS 运行成功
* fork 了 YuLang 和 GeeOS，并改了下 `Makefile` 啥的，先不 PR 了，感觉没啥必要(?)

### Day 6 计划

1. 熟悉 Vivado 的使用
2. 生成 Fuxi SoC 和 OpenSBI 的 SVF 文件
3. 板子收货之后把 SVF 文件烧进去，进度快的话就先调试着

线程调度之后再说吧，昨天的计划就先推迟一下(x

此外我仔细想了一下，移植 RustSBI 也不是不行，照 QEMU 版本编译然后烧进去理论上是可以的，但是可能有点小问题

Rust 的 RISC-V 32 环境似乎只有 RV32imac 和 RV32gc，而 Fuxi 处理器目前只支持 RV32ima，并不支持 C 扩展，所以暂时是没办法使用的，等写完了 C 扩展再移植 RustSBI 也不迟

OpenSBI 必须自己编译了，在编译参数里声明一下用 RV32ima 指令编译，这样应该就可以勉强运行起来，如果 `mstatus` 寄存器不出什么问题的话

## Day 6 2021-01-06

根据 Xilinx 官网的推荐，我装好了最新版本的 Vivado 2020.2，然后熟练地用 Vivado 打开 `Fuxi/soc/soc.xpr`，综合，还是之前一样的错误

这次我仔细看了一下，是文件的缺失，是找不到 `Fuxi\soc\soc.srcs\sources_1\bd\soc\ipshared` 的问题，我到上层目录看了下 `.gitignore`，发现一堆目录被 ignore 掉了

结合文件名以及 `.gitignore`，我觉得这个目录应该是由 Vivado 自动生成的，IP Core 相关的功能，但是我的 Vivado 的 IP INTEGRATOR 板块只能选择 Create 和 Open，还有一个 Generate Block Design 的按钮是灰色的，不能点，然后我就去网上查，并没有查到什么

这时我突然想起 Fuxi 的 README 里有提到，作者用的是 Vivado 2018.3，要不我也装一个试试？

装完之后，打开 `soc.xpr`，发现 Generate Block Design 是可以点的，解决了一个大问题，但是综合的时候又闪退了...就很难受

经过了一番折腾，我发现 Vivado 2020.2 不能 Generate Block Design 是因为调用的 Vivado 的 IP Core 版本太旧了(?)，需要 Upgrade，更新一下就又可以 Generate 了

为了保持稳定，我没有改设置里的 Project Device，综合、布线，一切正常，但是改成我的板子型号之后，报错了：

```
[xilinx.com:ip:mig_7series:4.2-0] soc_mig_7series_0_0: Target FPGA device 'xc7a200t' provided in the mig project did not match with the selected FPGA device 'xc7a35t' in project settings. Please cross check the mig project loaded or review the project settings
```

看起来是换板子型号产生的问题了，根据字面意思需要修改 mig project，也算是一切正常。不过我觉得改 SoC 应该没有我想象的那么简单，毕竟板子端口什么的布置就很不一样

搜索 `mig`，然后用记事本打开 `mig.prj` 文件，我发现第四行写着：

```xml
<!-- IMPORTANT: This is an internal file that has been generated by the MIG software. Any direct editing or changes made to this file may result in unpredictable behavior or data corruption. It is strongly advised that users do not edit the contents of this file. Re-run the MIG GUI with the required settings if any of the options provided below need to be altered. -->
```

看来这个是自动生成的了，查了一下需要在 Vivado 的 IP Catalog 里选择 Memory Interface Generator 生成 mig，但是照默认配置生成 mig 之后再选 Upgrade，会报 `Selected IPs can't be upgraded`，选择需要升级的 IP Core 时不全选，只选择必须升级的 IP Core，这时候升级会闪退

换成 Vivado 2018.3，改完 Project Device 之后，Generate Block Design 也变成灰色，不能点了，怪不得我之前没注意到这个问题

然后我问某宝店家要到了我现在板子的配套资料，里面有 MicroBlaze 处理器的构建教程，可以参考这个来整一遍

此外，我也查了一下 IP Core 的定义，感觉跟我经过以上操作之后的理解差不多：

> IP (Intellectual Property) 在嵌入式 FPGA 设计中，指的是某些设计好的模块，分为软件模块和硬件模块。这些模块，一般都是已经测试好，所有功能完善的，由一些用户自己设计的。有些模块是免费的，也有收费的模块。所有用户都可以将这些 IP 核 (IP Core) 导入到自己的工程中，同样，所有用户也都可以定制自己的IP核。

20210106 晚上补充：我照开发板的手册重新设置了一遍 mig 的管脚号 (Pin Number)，完成之后意外的没问题了，我还以为要把所有 IPC 的管脚号都要设置一遍的

现在已经全部 Upgrade 了，SoC 也可以在我的板子配置下正常综合了，今天就先到这，早睡早起身体好

### Day 6 进度

* 对 Vivado 的基本使用相对熟悉一些了
* Fuxi SoC 综合成功，布线成功，其实最后生成 Bitstream 也成功了，但是不知道给生成到哪去了，这个明天再说x

### Day 7 计划

1. 前面的步骤都完成了，明天真的该把 SoC 烧到板子上了
2. 在 Linux 下编译 RV32ima 的 OpenSBI，烧到板子上
3. debug

## Day 7 2021-01-07

参考 MicroBlaze 的文档，找到了生成 BIT 文件并烧写到 FPGA 上的步骤，但是奇了个怪了，综合、布线都不报错，生成 BIT 文件报没有布线：

```
ERROR: [Common 17-70] Application Exception: Unable to get BIT file from implementation run. Please ensure implementation has been run all the way through Bitstream generation. Aborting write_hw_platform..
```

20210107 下午补充：布线没报错，但是也没成功，其实要等很久之后才会报错，报错内容看不懂，也查不出来

有没有必要把 SoC 重新做一遍呢...

20210107 傍晚补充：有必要，毕竟板子不同，板子上的硬件不同，硬件对应的管脚号也不同。就算不重做，也要把 `xdc` 文件重新写一遍

20210107 晚上补充：开始重做！

20210107 深夜补充：放弃重做！先照 MicroBlaze 的教程熟悉一下 SoC 的构建方法！

### Day 7 进展

* 对 SoC 构建的基本操作相对熟悉一些了

综合没有问题，布线还是有问题，或许一些约束和一些模块需要针对特定板子重写

### Day 8 计划

1. 完成 Fuxi SoC 在我的板子上的构建

## Day 8 2021-01-08

今天开始参考 Fuxi SoC 在龙芯 FPGA 上的配置以及 MicroBlaze SoC 在我的 FPGA 上的配置

我觉得大部分配置都是可以参考的，按键、LED 还有最麻烦的 HDMI 需要重写，因为龙芯是用 VGA 的，ALINX 是用 HDMI 的，这里接口和协议都不一样，不过好像不是必须的，先跳过这部分也行

按键和 LED 先给用 wire 连上，HDMI 先略过，之后再参考板子给的 demo 和 Fuxi 的 VGA 写 HDMI

进行到现在，一个小问题是：大部分 IP Core 的功能我看一眼就知道是做什么的，但是我很难理解 AXI Interconnect 这个 IP Core 的使用方法，大体查了一下，是使用 AXI4 总线协议进行总线仲裁的，这就涉及到我的知识盲区了，因为我学的组成原理对总线仲裁只是停留在原理，并没有深入到具体的硬件、协议层面

AXI Interconnect 参考资料：

1. [AXI Interconnect](https://www.xilinx.com/products/intellectual-property/axi_interconnect.html)
2. [总线仲裁 - 百度百科](https://baike.baidu.com/item/%E6%80%BB%E7%BA%BF%E4%BB%B2%E8%A3%81)

算了，就强行连吧...

此外，我在万能的 bilibili 上找到了用 MicroBlaze 连 HDMI 输出视频的一个小教程：[Nexys Video 基于 Microblaze 的 OV5640 视频输出](https://www.bilibili.com/read/cv5242447/)，但是这个似乎用了几个我找不到的 IP Core；还有，我也在板子附送的 demo 里找到了 HDMI 输出的样例，但是先不折腾了吧，先老老实实折腾 SoC

20210108 傍晚补充：经过了一天的折(连)腾(线)，虽然连生成 Wrapper 都没有完成，但是我了解了 SoC 的构造，这简直是太妙了，一个 SoC 就是一个完整的主板，总线`sys_bus`、南北桥(`peri_bus`, `mem_bus`)、中断发生器、内存、显卡、网卡，一应俱全，虽然这里不应该称作显卡、网卡，因为并没有实际的卡存在，只是嵌入到板子上的电路

此外我也庆幸自己没有选择使用古老的 Spartan-6 系 FPGA 配合 ISE 自己写 SoC，每个 IP Core 都够我写半天的（除了 `Constant`）

经过这么久的折腾，我也知道如何移植 SoC 了：把板子上没有的模块（如 VGA）剔除掉、把板子上有的模块（如 HDMI）加上、把板子上都有的但不同模块（如晶振、内存）进行修改、适配

虽然上面都是废话，但是也确实是我走了一天的弯路所得出来的结论

今天也是失败的一天呢

### Day 8 进展

* 对 SoC 的基本结构相对熟悉一些了

但是我也发现前几天我的 repo 里 commit 的代码不能生成 Block Design，打算最近再整一份可以生成 bd 的，适配我板子的 project

20210108 深夜补充：重新 commit 了一遍，好像跟之前一样，还是不能生成 bd...

### Day 9 计划

1. 让 SoC 可以生成 Block Design
2. 完成 Fuxi SoC 在我板子上的构建

（题外话：我的计划从一个远大的目标变得越来越...嗯...不那么远大了，但是这也说明我的进展在不断深入，我的工作在不断细化，这也是好事）

## Day 9 2021-01-09

偶然在 GitHub 发现了 [基于龙芯 FPGA 开发板的计算机系统综合实验](https://github.com/oscourse-tsinghua/LoongsonCsprj2020)，感觉可能有一些参考价值

然后，又经过了一天的连线，在 CPU 没有连接外设的情况下，可以生成 BD 并综合了，但是布线还是有一些问题，会报错：`DRC PDRC-34` 和 `DRC PDRC-43`，有两个时钟频率不匹配，应该不难解决

然而，Google 出的结果没有参考价值，龙芯板子上的 Fuxi SoC 参考了并没有起作用，板子附送的 demo 参考价值也不大

报错内容主要说的是，计算出的 MMCM 和 PLL 的 VCO 频率（`CLKIN1_PERIOD`）不在其要求的周期范围内

计算公式为：`CLKIN1_PERIOD = (CLKFBOUT_MULT_F * 1000 / (CLKINx_PERIOD * DIVCLK_DIVIDE))`

需要调整 MMCM 和 PLL 配置中的 输入周期(`CLKINx_PERIOD`)、乘法因子(`CLKBOUT_MULT_F`) 或者 除法因子(`DIVCLK_DIVIDE`)，使得两者的 VCO 频率落在设备的范围内

一晚上过去了，并没有解决，因为不知道该调整什么地方...

20210109 深夜补充：应该调整 Clocking Wizard 的配置，改 Output Clocks 部分让 MMCM 变化，应该就能解决了

今晚大部分时间都用在生成输出(Generate Block Design)、综合和布线上了，在跑程序的过程中顺便了刷了一下哈工大的编译原理，毕竟还是要折腾 YuLang 的

### Day 9 进展

* 半成品 SoC 生成输出、综合成功，卡在布线上
* 学习了编译原理的绪论部分以及词法分析的前半部分

### Day 10 计划

1. 解决 Error，让半成品 SoC 可以布线
2. 完善 SoC，尽量让完整的 SoC 可以生成 Bitstream

## Day 10 2021-01-10

半成品 SoC 布线成功！而且是 commit 之后重新 clone 的 project！这次真的没有问题了吧，布线之后都能看到线网了

好了！开始加外设！

报错 `Runs 36-527`，`soc.gen` 目录下的一个以太网相关的文件缺失，但是这个目录下的文件不应该是自动生成的吗...

然而，百度出的解决方案没用，再次卡住，只能先把以太网模块删掉了

SPI 模块设置管脚的时候也注意到有一些名字不对应的问题，比如 Vivado 中需要的是：`SPI_FLASH_ss_io`, `SPI_FLASH_sck_io`；而板子文档中给的名字是：`QSPI_CLK`, `QSPI_CS`，经过一段时间的查询，我找到了 Xilinx 的[文档](https://www.xilinx.com/support/documentation/application_notes/xapp586-spi-flash.pdf)，里面给出管脚的别名，这才解决 SPI 的问题

此外，我在查文档的时候发现 SD Card 有 SPI 模式，可以当作一个 SPI 进行读写操作，实在是妙啊

然后，综合一切正常，布线报错，`DRC UTLZ-1`，看了下字面意思是 LUT（逻辑单元?）不够用了，当前的设计需要 20828 个 LUT，但是目标设备中只有 20800 个，把 AXI Interconnect 的 优化策略从最高性能改成常规，甚至改成最小面积都没用

完整的错误内容：

```
[DRC UTLZ-1] Resource utilization: LUT as Logic over-utilized in Top Level Design (This design requires more LUT as Logic cells than are available in the target device. This design requires 20828 of such cell types but only 20800 compatible sites are available in the target device. Please analyze your synthesis results and constraints to ensure the design is mapped to Xilinx primitives as expected. If so, please consider targeting a larger device. Please set tcl parameter "drc.disableLUTOverUtilError" to 1 to change this error to warning.)
```

卡在这了，就很难受

拿原版 Fuxi SoC 修改，遇到 MII 有几个管脚端口名字不对应，又查到一个 Xilinx 的[文档](https://www.xilinx.com/support/documentation/ip_documentation/tri_mode_ethernet_mac/v9_0/pg051-tri-mode-eth-mac.pdf)，但是管脚始终是缺三个...

最终分配管脚，

* MII 缺 `MII_col`, `MII_crs`, `MII_rx_er`
* SD 卡的 SPI 缺 `SPI_ss_io`，可能需要改 
* SPI Flash 的 `SPI_sck_io` 的 L12 管脚分配不上
* UART 的管脚只有 `UART_rxd` 和 `UART_txd`，但是需要的管脚共有 14 个，少 12 个，可能需要改

MII 可以没有，不上网也没关系；SD 卡可以没有，不读 SD 卡也没关系，UART 可以没有，不读 UART 也没关系，但是没有 SPI Flash，固件往哪整...

而且最后还是报错，`DRC UTLZ-1`，一样的错误

我在考虑要不要再买个板子，这次不用 XC7A35T 芯片的 FPGA 了，换 XC7A100T 芯片，这个 LUT 够多，而且 ALINX 用 XC7A100T 芯片的板子有 VGA 接口，MII 部分 `MII_col` 和 `MII_crs` 还有 `MII_rx_er` 都有，UART 部分只有 `RXD` 和 `TXD`，这个应该是需要改配置了

我有注意到 demo 里给的 MicroBlaze 用 UART 的 IP Core 是 AXI Uartlite，而 Fuxi SoC 默认用的是 AXI UART 16550，这个应该换一下 IP Core 就好

现在的板子已经申请退款了，明天开始用新板子的配置开发，等布线啥的差不多了再下单也不迟。XC7A100T 芯片的 LUT 是 XC7A35T 的三倍多，总不会再不够用了吧

羡慕龙芯的板子，直接上 XC7A200T 了

20210110 深夜补充：查了一晚上关于 HDMI 的资料，发现了一篇[很有价值的文章](https://numato.com/kb/simple-hdmi-vga-framebuffer-design-example-on-neso-artix-7-fpga-board/)，写了一个用 MicroBlaze 输出 HDMI 的 demo，用 AXI4-Stream to Video Out 从 AXI4-Stream 转成 RGB，再写一个 rgb2dvi 模块，直接对外输出 tmds 和 tmdsb 就好了（其中，AXI4-Stream to Video Out 这一 IP Core 需要由 Video Timing Controller 传入一个 vtiming_out 信号）

HDMI 还是 VGA，这还是个问题。不过，现在选输出接口是不是有点太早了，毕竟没有 BIOS，也没法往屏幕上画黑框框写字

等等，突然想起 MaxXing 大佬的毕设，用 YuLang 写了个[幻灯片播放器](https://github.com/MaxXSoft/Fuxi-Soft/tree/master/src/slideshow)，应该是用的 DMA 方式(?)，直接往内存里写，就可以让显示器实时显示。在 YuLang 里还有 `lib.soc` 的标准库，直接往 `VGA_ADDR ` 这一地址 `writeWord`，简直是太妙了

所以，我选择 VGA

### Day 10 进展

* 发现自己的板子 LUT 不够用，已申请退货
* 更加熟悉 SoC 的构建过程了
* 学完了编译原理的词法分析和正则表达式部分

### Day 11 计划

1. 在 XC7A100T 芯片上，参考 ALINX 板子的管脚配置，重新移植 Fuxi SoC
2. 综合！布线！

## Day 11 2021-01-11

今天又仔细读了下 NonTrivialMIPS 的最终文档，发现我对 SPI 的理解有些误区，CFG Flash 才是板子内置的存储，上电会从 CFG Flash 中读取 bitstream；而 SPI Flash 是可插拔的那种，在龙芯的板子上体现为可插拔的 Flash，而在 ALINX 的板子上体现为 SD 卡，所以在 bd 中的两个 Flash 都不需要删除

此外，ALINX 的板子也可以用 40-pin，TFT 协议的 LCD 屏，所以 LCD 模块也可以保留，那么使用了这块板子的话，在 bd 方面需要对 Fuxi SoC 进行的改动只有删除 `confreg` 模块，以及修改时钟频率了

所以说啊，选对板子可以少走很多弯路

然后今天我的新电脑到货了，今天先折腾那边的环境，就当摸鱼了x

### Day 11 进展

* 对 SoC 和 FPGA 的理解更深了一些
* 配环境的时候把新番都看了一遍(x)

### Day 12 计划

1. 继续配环境！
2. 在新电脑上开发！新硬盘够大，可以在 Linux 里装 Vivado 了，在 Vivado 跑着的时候可以同时折腾 YuLang 和 GeeOS 了！
3. 买赛博朋克 2077 (x)

## Day 12 2021-01-12

折腾 LCD 的时候发现龙芯板子上的 LCD 是 34 pin，16 位色的，而 ALINX 的板子和 LCD 都是 40 pin，24 位色的，所以并不兼容，战略性放弃 LCD 模块

（题外话：偶然发现 Fuxi SoC 里的 LCD 模块跟 NonTrivialMIPS 里的一样，都是 Harry Chen 大佬写的，也就是说 Vivado 没有原生的 LCD 模块，需要的话只能自己写）

此外，我也突然知道，原来不用的端口可以不写到顶层模块上，比如 UART 的端口有很多，但是只用到了 `UART_rxd` 和 `UART_txd`，所以其它的就可以不写到 Verilog 里面，配置管脚的时候也就不用配了...

还有一件事...我发现现在的电脑是 8 核的，所以用 Vivado 跑的时候每次都开 8 个 Job，但是经常会闪退。用 `htop` 看了下，8 个 Job 一起跑的话 8G 的内存会不够用，所以还是只能一次性跑 4 个 Job

配管脚的时候，我发现文档里提到 SD 卡支持 SPI 模式和 SD 模式，但是只列出了 SD 模式的管脚，并没有列出 SPI 模式的管脚，于是我又查了一下资料，找到了[一篇文章](http://blog.csdn.net/ming1006/article/details/7281597)，这篇文章提到，SPI 模式下只需要接上 时钟、片选信号、MISO、MIOS，其它管脚放空就可以了，所以我又改了下 `SoC.v`，把 IO2 和 IO3 给删掉了

还有，文档中写 VGA 是 24 位色的，也就是说 RGB 都是 8 位的，但是 Fuxi SoC 中只有 4 位，IP Core 的输出只有 6 位，最终我只使用了 6 位来输出

BD 和管脚配好了，综合没有报错，布线报了错：`DRC BIVC-1`，字面意思没太看明白，查了一下才知道，同一个 Bank 的管脚电平应该相等。另外由于 ALINX 的板子是差分晶振，我把时钟改成差分的了

之后又报了一个错：`Place 30-574`，报错没看懂，网上查了下说是 Vivado 把我的时钟当成不是晶振产生的了...我也没太明白，加了两条约束就好了...其中一条是关于时钟的，这个在 Fuxi SoC 里面也有，还有一条是关于以太网的，在 Fuxi 里面没有发现，但是我还是加上了

解决这一问题之后，又双叒叕报错了，是熟悉的 `DRC PDRC-34` 和 `DRC PDRC-43`，把时钟产生的频率调高就好了

然而，又报错了，外设频率调到 400 MHz 之后，超过了 UART 的使用频率范围，那该咋整...

另外这也有点奇怪了，为什么用 50 MHz 的晶振跟 200 MHz 的晶振报错内容跟具体数值都是完全一样的，然而假设跟晶振频率无关的话，那么为什么龙芯的板子用 100 MHz 的晶振就没有问题呢

[一个回答](https://forums.xilinx.com/t5/Implementation/version-up-implimentation-error/td-p/810729)里说，这个问题会出现在较新版本的 Vivado 上，而旧版本会忽略这一问题

我觉得需要改 MIG 的配置，而不是改 Clocking Wizard 了。明天再折腾吧，该睡了

### Day 12 进展

* 配好了新电脑的 Ubuntu 开发环境
* 解决了 SoC 的一堆 bug，综合成功，就差布线了

### Day 13 计划

1. 尽量布线完成
2. 布线成功的话，学习如何生成 bitstream，然后下单

## Day 13 2021-01-13

实践证明，MIG 的配置需要改，Clocking Wizard 的配置也需要改。毕竟报错是报在 MIG 上的，错误内容是跟 Clocking Wizard 有关的，两者都有问题

今天经过一上午的折腾终于布线成功了，中午歇会儿，下午研究生成 bitstream，顺利的话晚上下单板子，然后等板子到货期间折腾一下 OpenSBI 和 GeeOS

晚上的话，需要跟学校刷牛客的题目，为下学期的 ICPC 做准备。有必要的话，去 AcWing 报一下网课也可以（晚上补充：老师记错了，是 15 号的练习赛）

生成 bitstream 一切正常，看来是时候下单了

另外，我又找了几篇[文章](https://cloud.tencent.com/developer/article/1770529)，研究了一下 u-boot 和 SBI 的关系，SBI 是一个运行在 M 态的 runtime，而 u-boot 是一个运行在 S 态的 BootLoader，一般的 SBI 是集成了 u-boot 的，所以需要做的是下载 u-boot 和 OpenSBI 的代码，然后用 RV32ima 指令集编译，先在本地用 QEMU 测试一下能不能用，能用的话再搬到板子上去

我也参考了几篇讲如何编译 OpenSBI 的文章：[OpenSBI 编译和运行](https://zhuanlan.zhihu.com/p/72340428)，以及 [u-boot 的文档](https://github.com/u-boot/u-boot/blob/master/doc/board/emulation/qemu-riscv.rst)

编译 u-boot 的时候，需要添加以下环境变量：

```shell
export CROSS_COMPILE=riscv64-linux-gnu-
export PLATFORM_CPPFLAGS=-march=rv32ima
```

然后：

```shell
make qemu-riscv32_smode_defconfig
make
```

但是，报错了...亲测编译 RV64 的 u-boot 不会报错，但是 RV32 的就会。报错内容为，`undefined reference to __lshrdi3` 之类的，查了下这些是 `libgcc` 里的函数，但是 Ubuntu 的源里只有 64 位的交叉编译工具链，并没有 32 位的工具链，就很尴尬

看了下，整 RV32 的工具链挺麻烦的，我再给原来电脑装个 ArchLinux 吧，在那上面编译，今天就先到这

现在用上 Ubuntu 了，又想起 ArchLinux 的好了，源里面什么都有，虽然版本都是最新的，可能兼容性上会出一些小问题

### Day 13 进展

* Fuxi SoC 在我将要买的板子上综合、布线、生成 bitstream 成功
* 板子已下单

### Day 14 计划

1. 给旧电脑装 Manjaro 以及 RV32 工具链
2. 编译 RV32ima 指令集的 u-boot 和 OpenSBI
3. 在 QEMU 里调试 GeeOS，进度快的话先做着第二题，写线程调度

## Day 14 2021-01-14

事实证明，是我记错了，ArchLinux 的源里面只有 RV32 的 QEMU，并没有 RV32 的 GCC，因此需要手动编译了

但是，我尝试 clone 了一下 `riscv-gcc` 的仓库，发现这个仓库太大了，而我 clone 的速度又巨慢，只能想别的办法了

我找到了这样一个网站：[Cross-compilation toolchains for Linux](https://toolchains.bootlin.com/)，在这里可以下载 Linux 下交叉编译的工具链，试一下 `riscv32-ilp32d` 的工具链吧

```
riscv32-linux-ld.bfd: libgcc.a(_lshrdi3.o): can't link double-float modules with soft-float modules
```

我觉得这是 `ilp32d` 的问题，但是我在编译参数里指定 `-mabi=ilp32` 之后也不行，而且看了下 u-boot 的 README，里面有提到 RISC-V 并不会用浮点数寄存器

在 `riscv-gnu-toolchain` 里找到一个 [issue](https://github.com/riscv/riscv-gnu-toolchain/issues/356)，一个哥们用 `rv64ima` 编译 OpenCV 遇到了类似的问题，我觉得这个有一定参考价值，所以开始慢慢 clone 这个仓库吧

然而，由于众所周知的原因，

```
fatal: 远端意外挂断了
fatal: 过早的文件结束符（EOF）
fatal: index-pack 失败
fatal: 无法克隆 'https://github.com/riscv/riscv-gcc.git' 到子模组路径 'riscv-gnu-toolchain/riscv-gcc'
第二次尝试克隆 'riscv-gcc' 失败，退出
```

然后我去 `riscv-gcc` 仓库的 release 部分下载代码，这个真的快多了，但是编译了一个小时后报错：`#include <sys/ustat.h>` 找不到文件，查了一下这个文件已经被取代了，说明我下载的源码版本太旧了...我又看了下时间，2018 年的，确实够旧了，但是新的我 clone 不下来，就很难受

网上搜了一会，找到了 GitHub 的一个镜像：[Gitee 极速下载](https://gitee.com/mirrors)，在这里找到了 `riscv-gcc` 的镜像，虽然 clone 的速度也不是很快，毕竟家里的网速就比学校里慢好多，但是至少没有 GitHub 那么慢了

编译失败，挂在一个 `assert` 上了。看来只能 clone 那个最大的仓库：`riscv-gnu-toolchain` 了。我注意到，这个仓库的 README 里提了一句：

**Warning: git clone takes around 6.65 GB of disk and download size**

就很慌

`git submodule update --init --recursive` 失败了好多次，在网上查的时候偶然发现一个大佬给整理了一个仓库，并写了一个[教程](https://my.oschina.net/yushulx/blog/4649006)，救了我一命

睡前终于编译 u-boot 成功了！还是官方的 `riscv-gnu-toolchain` 好用。编译 toolchain 的方法为：

```sh
./configure --prefix=/opt/riscv --with-arch=rv32ima --with-abi=ilp32
make
```

编译 u-boot 的方法（提前配好 toolchain 的 PATH）：

```sh
export CROSS_COMPILE=riscv32-unknown-linux-gnu-
export PLATFORM_CPPFLAGS="-march=rv32ima -mabi=ilp32"
make qemu-riscv32_smode_defconfig
make
```

然后编译 OpenSBI 也是一切顺利：

```sh
export CROSS_COMPILE=riscv32-unknown-linux-gnu-
make PLATFORM=generic FW_PAYLOAD_PATH=(path_to_uboot)/u-boot.bin PLATFORM_RISCV_ISA=rv32ima
```

最后测试 QEMU 以及 `objdump`，一切顺利：

```sh
qemu-system-riscv32 -M virt -m 256M -nographic -bios build/platform/generic/firmware/fw_payload.elf
riscv32-unknown-linux-gnu-objdump -M rv32ima -d build/platform/generic/firmware/fw_payload.elf | less
```

`objdump` 得到的结果也是很明显可以看出，没有用 RVC 扩展，这下应该可以在 Fuxi SoC 上跑了吧，如果 SoC 不出什么问题的话。毕竟 SoC 只是可以综合可以布线，不代表硬件上没有问题，这个调试起来可就麻烦咯

然而——让 QEMU 启动 OpenSBI 引导 u-boot 来运行 GeeOS 则报了错

```sh
qemu-system-riscv32 -nographic -machine virt -m 256M -bios fw_payload.elf -kernel build/geeos.elf
```

错误内容：

```
rom: requested regions overlap (rom phdr #0: build/geeos.elf. free=0x000000008000a018, addr=0x0000000080000000)
qemu-system-riscv32: rom check and register reset failed
```

一个熟悉的错误。把 `-bios fw_payload.elf` 换成 `-bios default` 也会报同样的错误，这可能是 GeeOS 的问题了，看字面意思是 ROM 地址重叠，应该是因为 OpenSBI 和 GeeOS 都是从 0x8000000 启动的吧

翻了下 rCore-Tutorial 得知：

> OpenSBI 所做的一件事情就是把 CPU 从 M Mode 切换到 S Mode，接着跳转到一个固定地址 `0x80200000`，开始执行内核代码。

那么，只需要改一下 `GeeOS/src/linker.ld`，把系统的入口点从 `0x80000000` 改为 `0x80200000` 即可

重新编译了一下，确实不报错了，但是 GeeOS 也没有反应了

大致读了一下代码，发现 GeeOS 是自带 bootloader 的，`src/arch/target` 目录里也对 Fuxi SoC 和 QEMU 做了适配，也就是说原本的 GeeOS 并不需要 OpenSBI，是我画蛇添足了

所以说，我的任务并不是让 SoC 可以用 OpenSBI 引导 GeeOS 启动，而是让 SoC 可以用 OpenSBI 引导其它操作系统，如 xv6 或者 rCore

目标更明确了，那么就开始制定下一步的规划

### Day 14 进展

* 构建 rv32ima-ilp32 的工具链成功
* 编译 rv32ima 指令集的 u-boot 和 OpenSBI 成功

### Day 15 计划

1. 使用 rv32ima 指令集编译并测试 [xv6-riscv](https://github.com/mit-pdos/xv6-riscv)
2. 读 OpenSBI 代码，探究可以对 Fuxi CPU 进行的改动（如 stdio 相关）
3. 上一条进行不顺利，或者没有明确目标的话，就先给 GeeOS 写线程调度，等板子到货
4. 晚上去牛客打比赛，这边的任务也暂且搁置一下

## Day 15 2021-01-15

突然发现 xv6-riscv 是 RV64 的，要移植到 Fuxi SoC 的话还需要改成 RV32 才能运行，而且 xv6-riscv 也是不需要 bios，也就是 SBI 和 u-boot 的，那我编译了个寂寞...

此外，我在读 xv6-riscv 的 `Makefile` 过程中发现了，用 QEMU 运行的时候添加了一个参数 `-bios none`，我又重新编译了一下 QEMU-5.2.0，发现最新版本的 `qemu-system-riscv` 默认就是用 OpenSBI 启动的，所以之前才会出现那样的错误，在 GeeOS 的 `Makefile` 里也加上这个参数就可以在最新版本的 QEMU 里运行了

在 GitHub 闲逛，找到了 [michaelengel / xv6-rv32](https://github.com/michaelengel/xv6-rv32)，亲测可用。就决定是你了！

读了下 `GeeOS/src/arch/target/` 里面的几个文件，发现 Fuxi SoC 和 QEMU 之间的区别挺大的呀，QEMU 的 UART 可以直接用数组索引，但是 Fuxi SoC 只能用地址访问。而且在 Fuxi SoC 里，UART 的地址明明是 `0x11040000`，可 UART 的管脚都是从 `0x11041000` 开始偏移的，而且应该是占 1 字节的管脚变成了占 4 字节的，想改这个但是不知道从哪下手

我觉得，如果要把 GeeOS 改成在 Fuxi SoC 里面运行的状态，应该修改 `src/arch/arch.yu`，修改 30 行的 `import` 语句即可。此外，`src/arch/target/fuxi.yu` 的 UART 时钟频率应该也要改

又搜索了一下，外设的物理地址是在 `Fuxi/soc/soc.srcs/sources_1/bd/soc/soc.bd` 这个文件里分配的，折腾了一下发现可以在 Vivado 的 Address Editor 界面编辑，就不动这个了吧

至于 UART 输出字节的问题，对比了一下 NonTrivialMIPS，并没有发现 UART 部分有什么区别。读了一下 OpenSBI 的代码，发现 UART 可以设置 `reg_width`，也就是说 QEMU 使用 UART 的 `reg_width=1`，而 Fuxi SoC 使用 UART 的 `reg_width=4`，所以说这是 UART 的区别咯

此外，我发现 OpenSBI 只能针对特定芯片编译，因为外设的地址不同。比如之前编译的就设置了 `PLATFORM=generic`，这代表编译到 QEMU 上使用。所以要想移植到 Fuxi SoC 上，还需要为 OpenSBI 在 `platform` 目录下写针对 Fuxi SoC 的配置才可以

### Day 15 进展

* 编译并运行 `xv6-rv32` 成功

### Day 16 计划

1. 上午 fork 一份 OpenSBI，编写针对 Fuxi SoC 平台的代码并尝试编译
2. 下午板子应该能到货，收到之后把我移植的 SoC 烧进去测试，debug

说起来，我买的 VGA 线还没到，先用串口跟 [Fuxi-Soft](https://github.com/MaxXSoft/Fuxi-Soft) 里面的小软件调试吧

这两项可能都需要好几天来完成，加油！

## Day 16 2021-01-16

OpenSBI 的配置好像也不难嘛，复制一份模板，改一下就好了。不过配置里面的 `HART_COUNT` 有点难理解，查了一下才明白 RISC-V 里面把 CPU 的 Core 称为 HART，参考文献：[RISC-V64 opensbi启动过程](https://my.oschina.net/u/4239621/blog/4779185)

不过 u-boot 的配置比较麻烦，配好一份 `defconfig` 文件后，编译也出了不少问题，查不到解决方案，那就编译 OpenSBI 的时候不要 `FW_PAYLOAD` 就好了

板子收到货了，然而我用 Vivado 来 Generate BD 的时候又报错...然后不知道怎么回事，瞎点了几下又莫名其妙好了，重新 commit, push, rm, clone，还是同样的错误，再乱点几下又好了，Vivado 真神奇啊

然而，布线又双叒叕报错，`DRC INBB-3`，查了下网上报这个错都是因为换电脑、移动文件夹、更换 Vivado 版本之类的原因造成的，应该问题不大

["\[DRC INBB-3\] Black Box Instances." Unable to instantiate user created IP's](https://forums.xilinx.com/t5/Design-Entry/quot-DRC-INBB-3-Black-Box-Instances-quot-Unable-to-instantiate/td-p/801905)

折腾了一下午，终于找到解决方案了：把出问题的 IPC 删掉再重新加上，一切正常

到了晚上终于把 Fuxi SoC 给烧到 FPGA 里了，但是又折腾了一晚上，还是不知道该怎么把 ELF 文件烧到 Flash 里面，只能呆呆地看着 Vivado 里面 ILA 传来的波形

顺便吐槽一下，运行起来的 FPGA 芯片真的好烫

### Day 16 进展

* 针对 Fuxi SoC 编译 rv32ima 指令集的 OpenSBI 成功，虽然并没有测试
* 板子到货，成功把 Fuxi SoC 烧进 FPGA，虽然并没有测试

### Day 17 计划

1. 研究如何把 ELF 烧到 Flash 里
2. 调试 GeeOS 和 OpenSBI

## Day 17 2021-01-17

查了一上午资料，还是不知道该如何把 ELF 烧到 Flash 里...因为查到的资料都太旧了，都是用的 Xilinx SDK，而我用的是 Vivado 2020.2，Xilinx SDK 已经被 Vitis 取代了，而里面我又找不到跟 SDK 对应的菜单

参考导师 MaxXing 给我提的建议，可以使用串口调试 GeeOS，但是我用串口把 `geeos.elf` 用 `utils/uart.py` 写进去之后没有任何事情发生，说明 SoC 还是有问题的，但是问题不知道出在哪，也不知道怎么调试...

找到了 [Vitis HDL 的文档](https://www.xilinx.com/html_docs/xilinx2020_1/vitis_doc/index.html)，但是似乎并没有什么用

20210117 傍晚补充：犯了个低级错误...把 ELF 烧到 Flash 里需要用的是 Vitis，但我装 Vivado 的时候默认装的是 Vitis HLS，Vitis 跟 Vitis HLS 似乎不是同一个东西...就很尴尬

再挂机一晚上装 Vitis 吧，下载的时候读一下 GeeOS 的代码，准备写线程调度

20210117 晚上补充：挂机下载 Vitis，去休息了会，回来发现下载速度变慢了，重开安装器之后提示硬盘空间不足，因为我只给 Linux 分配了 200G 的空间，Vitis 需要 140G，可用的空间只有 130G 了。但是问题是，有一部分被占用的空间里面存着已经下好的 Vitis 安装文件和已经装好、不用再安装的 Vivado 啊，为什么要忽略这些

被迫切回 Windows，用迅雷下载 Vitis 吧，倒是也不影响读 GeeOS 的代码，只是不能编译调试了，毕竟 Windows 下配环境太麻烦了

### Day 17 进展

今天就查资料、折腾 Vivado、折腾 Vitis HDL，基本没有进展。非要说的话，进展如下：

* 用串口下载测试得知，现在的 Fuxi SoC 在我的板子上并不能正常运行 GeeOS，还需要再修改
* 查了一整天资料，最后才知道把 ELF 烧到 Flash 里还需要 Vitis，需要下载安装

此外，我发现板子掉电重启之后，烧进去的 Fuxi SoC 又变回出厂时的按键控制 LED 的程序了。参考 NonTrivialMIPS，上面说 `*.bit` 文件也要写到 Flash 里面。等我切回 Windows 读一下板子配套的文档再研究研究吧

### Day 18 计划

1. 安装 Vitis，把 Fuxi SoC 和准备好的 ELF 烧到 Flash 里
2. 调试 Fuxi-Soft, GeeOS 和 OpenSBI

