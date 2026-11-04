# 终端
![Remote viewing](block:oc2:terminal)

终端是一台独立的显示器和键盘，没有计算机主体本身，它通过[网络连接器](network_connector.md)接入串行总线。它会按原样读取和写入串行数据。要让计算机能与它交互，需要在计算机中使用[串口卡](../item/serial_interface_card.md)。

在 Linux 上，可以使用 `getty` 在终端上创建一个会话：  
`setsid getty -L ttyS1 9600 screen &`

在 CP/M 上，可以这样切换到外部终端：  
`STAT CON:=TTY:`。

## 配置
在其设置界面中配置终端地址和波特率。要访问这个界面，可以用[扳手](../item/wrench.md)打开终端，或者使用终端屏幕左侧的切换按钮切到设置界面。
