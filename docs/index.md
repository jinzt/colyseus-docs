Colyseus是Node.js的权威多人游戏服务器。它使您可以专注于自己的游戏玩法，而不必为网络烦恼。

该框架的任务是成为使用JavaScript创建自己的多人游戏的最简单解决方案。

<center>
  <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSjJtmU-SIkng_bFQ5z1000M6nPSoAoQL54j0Y_Cbg7R5tRe9FXLKaBmcKbY_iyEpnMqQGDjx_335QJ/embed?start=false&loop=false&delayms=3000" frameborder="0" width="680" height="411" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</center>

## Colyseus为您提供的内容：

- 基于WebSocket的通信
- 服务器端和客户端中的简单API
- 服务器和客户端之间的自动状态同步
- 对接会客户进入游戏环节
- 垂直或水平扩展

## Colyseus不提供的内容：

- 游戏引擎：Colyseus与您使用的引擎无关。需要物理学吗？添加您自己的逻辑/包。
- 数据库：由您决定是否配置和选择要使用的数据库。

## 思维

权威的游戏服务器思维方式非常简单。服务器验证用户的动作，而客户端则是当前游戏状态的虚拟表示。

服务器应处理游戏中涉及的所有数据，例如位置，速度，碰撞等。

制作多人游戏通常很棘手，因为您的游戏玩法必须考虑多个延迟-其他客户端将数据发送到服务器，而服务器将数据发送回所有客户端。伪造已经发生的事情的艺术实际上是在当前玩家观看和玩游戏时发生的事情。

这是在Colyseus上的“多人游戏循环”的样子：

- 客户端向服务器发送一条消息，请求更改其状态。
- 输入必须由您的房间管理员验证。
- 房间状态已更新。
- 所有客户端都会收到游戏状态的最新版本。
- 游戏状态的视觉表示已更新。

### 简图

```
              room.send({ action: "left" })

                           |
      +------------+       |       +-----------------------------------+
+-----+ Client #1  +-------|       |  Room handler #1                  |
|     +------------+       |       |                                   |
|     +------------+       |       |  onMessage (client, data) {       |
|-----+ Client #2  |       --------+    if (data.action === "left") {  |
|     +------------+               |      // update the room state     |
|     +------------+               |    }                              |
|-----+ Client #3  |               |  }                                |
|     +------------+               +-----------------------------------+
|                                                    |
|        patch state broadcast (binary diff)         |
|----------------------------------------------------+
```

## 人们对Colyseus说什么？?

!!! Quote "[@bmovement](https://twitter.com/bmovement)"
    "Thanks again for this framework... it allowed someone like me who just wants the server to be a black box to focus on my game instead of getting bogged down learning a whole new skill set!"

!!! Quote "[@sagestudios](https://github.com/sagestudios)"
    Loved the framework. Exactly what we are looking for in terms of features.

## 外部链接

- [💬 &nbsp; Chat / Discord](https://discord.gg/RY8rRS7)
- [💬 &nbsp; 论坛](http://discuss.colyseus.io/)
- [💰 &nbsp; 支持项目](https://www.patreon.com/endel)
- [🌐 &nbsp; 网站](https://colyseus.io)
