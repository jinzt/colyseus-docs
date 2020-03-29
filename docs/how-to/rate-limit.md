您最终可能会发现恶意用户利用Colyseus的牵线搭桥充斥您的服务器房间，导致您的服务器创建和删除房间而没有实际使用玩家。

建议使用`express-rate-limit`中间件阻止来自同一源的太多请求。在[`express-rate-limit`'s README](https://github.com/nfriedly/express-rate-limit)中查看更多详细信息；

```
npm install --save express-rate-limit
```

## 使用

```typescript fct_label="TypeScript"
import rateLimit from "express-rate-limit";

const apiLimiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100
});
app.use("/matchmake/", apiLimiter);
```

```javascript fct_label="JavaScript"
const rateLimit = require("express-rate-limit");

const apiLimiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100
});
app.use("/matchmake/", apiLimiter);
```


如果你使用了反向代理 (例如) Heroku, Bluemix, AWS ELB, Nginx, etc)，还需要启用 `"trust proxy"` 

```javascript
// see https://expressjs.com/en/guide/behind-proxies.html
app.set('trust proxy', 1);
```