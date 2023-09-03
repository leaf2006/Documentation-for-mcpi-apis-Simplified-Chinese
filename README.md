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

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/><img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```python
#使用默认地址和端口
mc = minecraft.Minecraft.create()
#指定IP地址和端口
mc = minecraft.Minecraft.create("192.168.1.1", 4711)
```

### .getBlock(x,y,z)

"Get block (x,y,z) => id:int"

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/><img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```python
#检索0,0,0处块的块类型
blockType = mc.getBlock（0，0，0）
```

### .getBlocks(x0,y0,z0,x1,y1,z1)

“获取长方体块（x0，y0，z0，x1，y1，z1） => [id：int]”

<img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```python
#get the block id's in a cuboid
blocks = mc.getBlocks(-1,-1,-1,1,1,1)
for block in blocks:
    print block
```

### .getBlockWithData(x,y,z)

“获取数据块（x，y，z）=>块”

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/><img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```python
#在方块0,0,0处检索块对象
blockObj = mc.getBlockWithData(0,0,0)
```

### .setBlock(x,y,z)

“设置方块(x,y,z,id,[data])”

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/><img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```python
#将x、y、z坐标处的方块设置为特定类型
mc.setBlock(0,0,0,block.DIRT.id)
#将块设置为特定类型和'子类型'
mc.setblock(0,0,0,block.WOOD.id, 1)
```

### .setBlocks(x0,y0,z0,x1,y1,z1,blockType, blockData)

“设置长方体块(x0,y0,z0,x1,y1,z1,id,[data])”

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/><img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```python
#一次设置多个方块，填补两组x、y、z坐标之间的空白
mc.setBlocks(-1, -1, -1, 1, 1, 1, block.STONE.id)
```

### .getHeight(x,z)

“获取世界的高度(x,z) => int”

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/><img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```python
#找到代表“最高”(非空气)块的x, z坐标的y(垂直)
y = mc.getHeight(0,0)
```

### .getPlayerEntityIds()

“获取已连接玩家的实体id=> [id:int]”

<img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```python
#获取玩家名为“martinohanlon”的实体id
entityId = mc.getPlayerEntityId("martinohanlon")
print entityId
```

### .saveCheckpoint()

“保存可用于恢复世界的检查点”

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/>

```python
mc.saveCheckpoint()
```

### .restoreCheckpoint()

“将世界状态恢复到检查点”

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/>

```python
mc.restoreCheckpoint()
```

### .postToChat(message)

“在游戏聊天窗口中发布信息”

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/><img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```python
输入“你好我的世界世界”到聊天窗口
mc.postToChat("Hello Minecraft World")
```

### .setting(setting, status)

“设置世界设置（设置、状态）。钥匙: 世界不可更改（world_immutable）, 名称标签可见（nametags_visible）”

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/>

```python
#开启世界不可更改
mc.setting("world_immutable", True)
#关闭名称标签可见
mc.setting("nametags_visible", False)
```

## Minecraft.player

### .getPos()

“获取玩家在世界中的坐标(由浮点数(小数)组成的Vec3)，如果玩家在块x5中，则返回”

<img src="https://3.bp.blogspot.com/-jfHVu6wzJ8A/VLZrZRxHviI/AAAAAAAAKnc/QkMuqztRYP8/s1600/Raspi_logo_small.png"/><img src="https://3.bp.blogspot.com/-kTbsdFgeL4E/VLZrwiMGWZI/AAAAAAAAKnk/AYCZdsaR-Vg/s1600/bukkit_logo_small.png"/>

```python
#获取玩家坐标作为浮点数
playerPos = mc.player.getPos()
```