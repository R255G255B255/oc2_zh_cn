# 入门指南
本文描述了组装和运行 [电脑](block/computer.md) 所需的步骤，并举例说明如何使用它与设备交互。我们以 [RISC-V处理器](item/cpu/riscv.md) 为例，但组装一台 [Z80](item/cpu_Z80.md) 电脑的方式是一样的，只是所需的零件不一样，虽然Z80架构电脑成本更低，但缺少很多RISC-V架构的功能。

## 组装
首先，您需要一台电脑，以及几个配件。 如果你还没有，得制作这些：
- 1x [电脑](block/computer.md)
- 1x [RISC-V处理器](item/cpu_riscv.md)
- 1x **Linux固件[闪存](item/flash_memory.md)**
- 1x **Linux文件系统[硬盘](item/hard_drive.md)**
- 3x 4M [内存](item/memory.md)

搜集好配件后，放置电脑，对着使用螺丝刀扳手打开装机面板。 或者，对着电脑打开终端屏幕，然后使用左侧的切换按钮切换到装机面板。 在这里，放入你准备的处理器、闪存固件、内存和硬盘。

![装机面板](../img/getting_started_inventory.png)

## 运行
要启动刚组装完的电脑，得为其提供能源。 查看终端或装机面板左侧的能量条。 它会显示您当前存储在 电脑中的能量，以及每刻（tick）运行所需的能量。

![能量信息](../img/getting_started_energy.png)

当确认能量足以运行后，切换到终端屏幕并按左上角的电源按钮。或者在潜行状态下使用电脑。电脑现在应该启动了！

接下来屏幕上显示的内容取决于你安装的处理器。继续阅读这里：[RISC-V](item/cpu_riscv.md) 或 [Z80](item/cpu_z80.md)。


祝你好运，最重要的是，玩得开心！