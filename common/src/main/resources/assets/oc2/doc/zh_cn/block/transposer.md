# 转置器
![Less posing, more rights](block:oc2:transposer)

转置器会在相邻容器之间移动物品和流体，包括箱子、炼药锅，以及支持自动化的机器。从未封堵的一侧移动时，物品会掉进世界中，再被拾起；流体也会被填充或抽取。

它可以同时通过[高级 API](../hlapi.md)和[中级 API](../mlapi.md)控制。例如：  
`local d = require("devices")`  
`local t = d:find("transposer")`  
`print(t:moveItems("north", 0,`  
`                  "south", 0, 64))`

## API
程序通过 `transposer` 设备控制转置器。有关其方法，请参见[转置器设备](../device/transposer.md)参考。
