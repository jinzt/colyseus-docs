## 步骤1： 允许 matchmaker 识别到 `"password"` 字段.

在`filterBy()`方法内部定义字段`"password"`。

```typescript
gameServer
  .define("battle", BattleRoom)
  .filterBy(['password'])
```


## 步骤2：将房间设为不公开

如果为 `create()` 或者 `joinOrCreate()`设置了密码, 请将房间属性设置为私有的:

```typescript
export class BattleRoom extends Room {

  onCreate(options) {
    if (options.password) {
      this.setPrivate();
    }
  }

}
```
