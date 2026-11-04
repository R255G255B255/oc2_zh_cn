# 红石接口
![Everything Red](block:oc2:redstone_interface)

红石接口提供了一个全向总线，用于接收和发出红石信号。

可用它与原始设备交互，例如门、灯或者其他提供红石协议的机械设备。

它可以通过 Lua 使用[高级 API](../hlapi.md)控制，也可以在[Z80](../item/cpu_z80.md)上通过[中级 API](../mlapi.md)控制。默认 Linux 发行版为前者提供 Lua 库。例如：  
`local d = require("devices")`  
`local r = d:find("redstone")`  
`r:setRedstoneOutput("up", 15)`

## API
程序通过 `redstone` 设备控制红石接口。有关其方法以及各面的命名方式，请参见[红石设备](../device/redstone.md)参考。
