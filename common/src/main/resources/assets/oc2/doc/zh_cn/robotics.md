# 机器人技术
[机器人](item/robot.md)本质是能动的[电脑](bolck/computer.md)，在[基础](basics.md)和[HLAPI](hlapi.md)/[MLAPI](MLAPI.md)中的内容也适用于它们，关于完整的**方法**参考，参见[机器人](item/robot.md)条目。

## 组装一台机器人
机器人的配置很像电脑，但有两处不同。

它无法连接[总线线缆](block/bus_cable.md)，所以所有设备都必须安装在机器人内部，取代扩展卡的是模块，比如[方块操作模块](item/block_operations_module.md)。

它有两个“库存”，一个是装机面板，用于内部组件：处理器、内存、模块，需要手动维护。另一个是机器人的物品栏，用于自动化交互，比如使用漏斗的时候。它还有一个内置的液箱，可以实现液体的自动化，比如使用转运器。

## 能量
机器人在内部电脑运行时会从内部储能中消耗能量，消耗功率取决于已安装的组件。在此基础上，移动和转向不额外消耗能量。当能量耗尽时，无论机器人身处何处，内部电脑都会以能量耗尽错误停止运行

使用[充电器](block/charger.md)给机器人充电。机器人可以自行移动到充电器上，因此可以轻松编写无人看管的充电脚本。拆除机器人并拾取它会保留其能量、库存，包括安装的组件和液箱。

## 动作队列
`move` 和 `turn` 并不会同步移动机器人。它们只是把一个动作添加到队列中，并返回队列是否有空间。然后机器人会一次执行队列中的一个动作。移动一格需要一秒，转九十度也需要一秒。

每个队列中的动作都会有一个 id，可以通过 `getLastActionId()` 获得。一旦机器人完成该动作，`getActionResult(id)` 会返回 `SUCCESS` 或 `FAILURE`，同时电脑会收到一个包含相同信息的 `robotActionCompleted` 事件。在此之前，结果是 `INCOMPLETE`。系统只保留最近的十六条结果。

碰到障碍物的移动不会提前被拒绝。机器人开始移动，撞到障碍物后返回原位并报告 `FAILURE`。关闭电脑会清空队列和已保存的结果。

## 方向与侧面（Directions and Sides）

机器人移动和模块操作使用不同的术语。

机器人移动使用“方向”：平移为 `forward`（前方）、`backward`（后方）、`upward`（上方）、`downward`（下方）；旋转为 `left`（左方）、`right`(右方)；
模块操作使用“侧面”：取 `front`（前面）、`up`（上面）、`down`（下面） 之一。
`forward` 不是侧面名，`front` 也不是方向名。

两者都可以使用缩写。移动可以用 `up`、`down`、`back` 和 `ahead`，而对应字母 `f`、`b`、`u`、`d`、`l` 和 `r` 可在任何需要全称的地方使用。 

## 位置
机器人有一个内置的指南针，可以记录它们的位置。`getFacing()` 会报告机器人的朝向： `north`（北）、`east`（东）、`south`（南）或 `west`（西）。`getPosition()` 会报告机器人原点的偏移量（以方块为单位）：`x` 向东增加，`y` 向上增加，`z` 向南增加。

原点在放置机器人时初始化。`calibratePosition()` 会将原点重置为机器人当前的位置。即使机器人被外力移动，位置仍然保持正确。

## 机器人库
手动控制动作队列很繁琐，所以默认的 Linux 发行版提供了一个 `robot` 库，用于等待动作完成：

`local r = require("robot")`
`r.move("forward")`
`r.turn("left")`

`move` 和 `turn` 会阻塞直到动作完成，并返回动作是否成功。`moveAsync` 和 `turnAsync` 只会阻塞到动作被加入队列为止。这四个函数都可以选择性地设置毫秒级超时，默认值为三十秒，如果超时则返回 `false`。对于异步版本，超时意味着队列在这段时间里一直满员。

Micropython 也有一个等效的库。

## 示例
下面的例子让机器人绕着一个三乘三的正方形行走：

`local r = require("robot")`
`for _ = 1, 4 do`
` for _ = 1, 3 do r.move("forward") end`
` r.turn("left")`
`end`

下面的例子挖掘一条直通的隧道，如果无法继续则停止。它需要一个方块操作模块，并且在选定槽位里放置一把镐子：

`local d = require("devices")`  
`local r = require("robot")`  
`local m = assert(d:find("block_operations"),`
`                 "no block operations module")`  
`for _ = 1, 16 do`  
`  m:excavate("front")`  
`  if not r.move("forward") then break end`  
`end`

一次移动需要一秒，这通常足够让模块冷却完成。如果方块需要更长时间挖掘，下一个 `excavate` 会直接返回 `false` 而不执行任何操作，紧接着的移动失败，循环也会提前停止。重新尝试挖掘就可以把它们也挖掉。