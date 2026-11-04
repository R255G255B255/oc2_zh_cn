# 电脑专家手册

你好啊! 你翻开这页，要么你是偶然翻到的，要么你是对 [组装你的第一台电脑](getting_started.md) 感兴趣，要么你正在寻找有关特定 [方块](block/index.md) 或者 [物品](item/index.md) 的信息。

## 概述
[电脑](block/computer.md) 可以给你提供多种用途，从娱乐到大规模、高度可定制的自动化设备。


CPU 和操作系统（OS）是每台计算机的核心。为 [RISC-V 架构](item/cpu_riscv.md) 提供的操作系统是一个非常基础的 Linux 发行版，只提供最基本的命令行工具，以及编写和运行 Lua 程序的功能。

Lua 在与高级接口设备([HLAPI](hlapi.md)) 交互时起到关键作用，例如 [红石接口](block/redstone_interface.md)。 默认的操作系统附带一些实用程序库来启用与此类设备的交互，特别是`devices`库。

与之相对的就是原生设备，例如 [硬盘](item/hard_drive.md) 和 [网卡](item/network_interface_card.md)。 这些设备都由原生 Linux 驱动程序控制，并且在添加或删除时还需要重新启动系统。 不过，平常使用的设备几乎都是 HLAPI 设备。

对于更具冒险精神的人，还有 [Z80 架构](item/cpu_z80.md) ，它提供了一个成本更低但功能也更有限的环境，操作系统是 CP/M。它可以与中级设备([MLAPI](mlapi.md))交互，例如[红石接口方块](block/redstone_interface.md)。这个操作系统附带一些实用工具，特别是 `DEVLIB.INC` 和 `OCAPI.INC` 库。

## 快速入门
如果你只想马上使用电脑，请阅读 [入门指南](getting_started.md)。 它讲了如何组装你的第一台 [电脑](block/computer.md) 和如何使用。 

## 参考
本手册包含计算机相关方块和物品的参考信息。

如果您正在寻找有关特定的方块或物品的信息，请查看相应的术语表：
- [方块列表](block/index.md)
- [物品列表](item/index.md)
- [设备列表](device/index.md)

如果您对某个特定主题感兴趣，有一些更常见的概述条目：
- [基本](basics.md)
- [HLAPI(高级接口)](hlapi.md)
- [MLAPI(中级接口)](mlapi.md)
- [机器人技术](robotics.md)
- [网络](networking.md)

