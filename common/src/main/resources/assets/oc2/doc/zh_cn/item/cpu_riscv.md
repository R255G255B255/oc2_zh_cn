# RISC-V处理器
![进行思考的那部分](item:oc2:cpu_riscv)

处理器是[电脑](../block/computer.md)和[机器人](robot.md)中实际用来计算的东西，如果处理器插槽中没有处理器，机器是无法启动的。

这是64位RISC-V处理器，它运行电脑自带的的Linux系统,本手册中记录的所有扩展卡、机器人模块、驱动器都是为它设计的。

或者看看[Z80处理器](cpu_z80.md)

##启动
根据[入门指南](../getting_started.md)组装一台机器，使用以下零件：
- 1x [电脑](block/computer.md)
- 1x RISC-V处理器
- 1x **Linux固件[闪存](item/flash_memory.md)**
- 1x **Linux文件系统[硬盘](item/hard_drive.md)**
- 3x 4M [内存](item/memory.md)

上电，开机，然后等它提示你登录

![登录提示](../../img/getting_started_login.png)

输入“root”作为用户名登录，然后按下Enter，现在你有一台可以用的电脑了，干得漂亮！

你可以根据需要添加更多设备，关于如何控制设备，请查看 [HLAPI](../hlapi.md)