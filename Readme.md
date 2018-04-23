# spiderman

## 在线直接使用（online）

> PS：在线直接使用，适用于不需要登录验证的页面，而需要登录验证的页面则需要通过调用SDK脚本来爬取。

```bash
Route: GET /o
Query: { 
  url: 'http://xxx.com/xxx',
  xpath: '//p',
}
```

## 接入SDK（script）

```javascript
const Ssman = require('ssman');

const authorized = new Ssman({
  // 注册服务，在你的账号里面可以找到，完全免费。任意使用，只要你不作恶。
  appKey: '',
  appSecret: '',
  
  // 基础配置
  base: 'https://xxx.com', // 可选。当这个值设置值的时候，后续所有 API 的 url 链接都会自动加上

  // 需要登录的情况下填写以下参数，不需要登录则不必填写
  loginUrl: 'http://xxx.com/xxx',
  account: 'kiruya',
  accountXpath: `//input[@class='account']`,
  password: '123456',
  passwordXpath: `//input[@class='password']`,
  submitXpath: `//button[@type='submit']`
});
// 待爬取的页面配置
const options = {
  // 必选
  xpath: '//p',

  // 可选。附带参数
  header: {
    key: 'value',
    // headers...
  },
  cookie: {
    key: 'value',
    // cookies...
  },

  // 可选。如果有翻页，则填写：
  pageCurrent: 1, // 当前页数
  pageUrl: 'http://xxx.com/info/{page}', // {page} 为页面翻页参数，自动替换
  pageTotal: 20 // 总页数，一次性页数过大的时候，接口返回耗时可能会很长，请自行优化处理。
}
const getResults = await authorized.get('url', options);
const postResults = await authorized.post('url', options);
```

## 名字来源（origin）

电影《蜘蛛侠》，希望他也能像蜘蛛侠拯救人于为难之中一样，能在现在互联网这张大网上精确且快速的『救』出你需要的『信息』。
```javascript
ssman => Super Spiderman
```

## 免责申明

该项目的所有功能均用于技术交流，一旦不正当使用造成法律纠纷，该项目的使用者将永久失去该项目的使用权，项目不承担任何责任，且可能会对不正当使用者进行合法的维权申述，请使用者注意，项目中不再详细说明。
