# Documentation-for-mcpi-apis-Simplified-Chinese

#### Warning: This document is translated from https://www.stuffaboutcode.com/p/minecraft-api-reference.html . This translation is for learning only. If there is any infringement, please contact me at any time to delete it.

#### 警告：本文档翻译自https://www.stuffaboutcode.com/p/minecraft-api-reference.html。 本翻译仅供学习，如有侵权可随时联系我删除.

## Minecraft API

这是 Minecraft Python API 库的参考，该库在 Minecraft： Pi 版和使用 <a href="http://www.stuffaboutcode.com/2014/10/minecraft-raspberryjuice-and-canarymod.html">RaspberryJuice</a>插件的 PC 版本上受支持。

如果你想了解有关如何使用API的更多信息，包括教程，请参阅我的项目和下载代码，请访问我的<a href="http://www.stuffaboutcode.com/p/minecraft.html">Minecraft</a>页面。

## 结构

- minecraft.py

- &nbsp;&nbsp;&nbsp;&nbsp;Minecraft类-用于连接游戏和与游戏互动的主类

- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;camera类-更改相机的角度和位置

- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;player类-获取和更改玩家位置和设置

- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;entity类-获取和更改实体位置和设置

- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;events类-检索游戏中发生的事件

- block.py

- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Block类-方块的定义，特别是其类型

- event.py

- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BlockEvent类-方块事件的定义，特别是什么事件，什么方块和什么玩家

- vec3.py

- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Vec3类-用于管理三维向量（即x，y，z）的通用类

- connection.py-API使用的内部模块

- util.py - API 使用的内部模块

## 兼容性

并非所有函数和块类型在所有版本的 API 上都可用，通过每个函数，您将看到一个徽标，显示该功能是否可用：

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/>在Minecraft： Pi上可用

<img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>在RaspberryJuice上可用

## Minecraft

“用于与 Minecraft 世界交互的主类，包括用于创建连接、修改玩家和块以及捕获事件的函数”

<br />

### .create(address = "localhost", port = 4711)

“创建与Minecraft 的连接（地址、端口）=> Minecraft 对象”

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/>
<img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```bash
#使用默认地址和端口
mc = minecraft.Minecraft.create()
#指定IP地址和端口
mc = minecraft.Minecraft.create("192.168.1.1", 4711)
```

### .getBlock(x,y,z)

"Get block (x,y,z) => id:int"

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/>
<img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```bash
#检索0,0,0处块的块类型
blockType = mc.getBlock（0，0，0）
```