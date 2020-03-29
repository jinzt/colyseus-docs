您可以通过在`onAuth()`或`onJoin()`方法期间抛出错误来拒绝玩家连接。

何时拒绝玩家连接的实现取决于您的用例。

在下面，您可以看到一个示例，该示例验证[@colyseus/social](/authentication/#server-side-api) 身份验证令牌，并检索 `Hero` 与用户ID链接的记录。

```typescript
export class BattleRoom extends Room {

  onCreate(options) {
    this.levelRequired = 10;
  }

  async onAuth(client, options) {
    const userId = verifyToken(options.token)._id;
    const hero = await Hero.findOne({ userId });

    if (!hero) {
      throw new Error("'Hero' not found in the database!");

    } else if (hero.level < this.levelRequired) {
      throw new Error("player do not have the level required to be on this room.");

    }

    return hero;
  }

}
```

尝试加入房间时，客户端将收到错误消息：

```typescript
client.joinOrCreate("battle", {}).then(room => {
  // ...
}).catch(e => {
  console.log(e) // "'Hero' not found in the database!"
})
```