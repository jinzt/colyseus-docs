# JavaScript客户端

## 平台兼容性

JavaScript客户端兼容：

- 主要浏览器环境 ([Electron](https://github.com/electron/electron), Chrome, Firefox, Safari, Opera, etc)
- [React Native](https://github.com/facebook/react-native) ([with some caveats](#react-native-compatibility))
- [Cocos Creator](http://www.cocos2d-x.org/creator) ([instructions](#cocos-creator-instructions))
- [NodeJS](https://nodejs.org/)

不知道如何使用NodeJS `webpack`的构建系统? 只需将 [JavaScript distribution file](https://github.com/colyseus/colyseus.js/raw/master/dist/colyseus.js) 保存并拖放到您的项目中，然后忽略`import`文档中此处显示的语句。

## 使用

### 安装模块

```
npm install --save colyseus.js
```

### 连接到服务器：

```ts
import * as Colyseus from "colyseus.js";

var client = new Colyseus.Client('ws://localhost:2567');
```

### 加入房间：

```ts
client.join("room_name").then(room => {
    console.log(room.sessionId, "joined", room.name);
}).catch(e => {
    console.log("JOIN ERROR", e);
});
```

### 房间事件

房间状态已更新：

```ts
room.onStateChange((state) => {
  console.log(room.name, "has new state:", state);
});
```

从服务器广播或直接广播到此客户端的消息：

```ts
room.onMessage((message) => {
  console.log(client.id, "received on", room.name, message);
});
```

发生服务器错误：

```ts
room.onError(() => {
  console.log(client.id, "couldn't join", room.name);
});
```

客户离开房间：

```ts
room.onLeave(() => {
  console.log(client.id, "left", room.name);
});
```

## React Native 兼容性

该客户端与React Native一起使用。您需要安装一些其他依赖项以实现兼容性并将其分配`window.localStorage`给 `AsyncStorage`。

- `npm install buffer`

```js
// App.js
import { AsyncStorage } from 'react-native';
import { Buffer } from "buffer";
window.localStorage = AsyncStorage;
global.Buffer = Buffer;
```

## Cocos Creator 指引

- 从Github下载最新新的构建文件[colyseus.js](https://raw.githubusercontent.com/colyseus/colyseus.js/master/dist/colyseus.js)。
- 将其保存到项目的 `scripts` 文件夹中。
- 导入使用 `const Colyseus = require('colyseus.js')`
