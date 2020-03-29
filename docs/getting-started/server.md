# 入门

Colyseus需要[Node.js](https://nodejs.org/) v8.0 或更高版本。

## 从实例项目开始

通过克隆[示例项目](https://github.com/colyseus/colyseus-examples) 并在本地运行，可以查看一些实际的示例。

```
git clone https://github.com/colyseus/colyseus-examples.git
cd colyseus-examples
npm install
```

要运行http + websocket服务器，请运行 `npm start`。


## 创建一个标准的Colyseus服务器

使用 `npm init colyseus-app` 命令生成准系统Colyseus服务器。您可以选择TypeScript（推荐），JavaScript和Haxe作为服务器的选择语言。

```
npm init colyseus-app ./my-colyseus-app
```

请参阅项目模板的内容：

- [TypeScript](https://github.com/colyseus/create-colyseus-app/tree/typescript)
- [JavaScript](https://github.com/colyseus/create-colyseus-app/tree/javascript)

## 推荐的NodeJS游戏包

在NodeJS和浏览器上开发游戏时，这些模块很有用。

- [@gamestdio/mathf](https://github.com/gamestdio/mathf) - 从Unity3D的API借用的数学函数
- [@gamestdio/timer](https://github.com/gamestdio/timer) - 可靠的计时事件
- [@gamestdio/keycode](https://github.com/gamestdio/keycode) - 键盘按键代码的常量 (`event.which`)

这些模块只能在浏览器中使用：

- [@gamestdio/pixi-engine](https://github.com/gamestdio/pixi-engine)
