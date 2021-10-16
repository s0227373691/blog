---
layout: 作品集
title: 作品集 - 使用React模仿ETQ Amsterdam
date: 2021-10-17 01:41:03
tags: 
    - 作品集
    - React
    - express
---

## 作品相關連結
[`作品網站`](https://mimic-web-etq-amsterdam.herokuapp.com/)
[`原始碼`](https://github.com/s0227373691/mimic-web-ETQ-Amsterdam)


&nbsp;
## 環境建置
 
下載 `express-generator` 產生後端環境
```bash
$ npm install -g express-generator

$ express --version // 確認版本
4.16.1

$ express -e --ejs mimic-web-ETQ-Amsterdam // 產生 mimic-web-ETQ-Amsterdam 專案
```

產生 `React`
```bash
$ npx create-react-app client
```


&nbsp;
## 設定Port 

為避免Express與React使用同一個port，這邊我將Express port設為8000，React維持3000.
```js
// ./bin/www
var port = normalizePort(process.env.PORT || "8000");
```

### `開發環境設定`
在開發過程中使用 `localhost:3000` 為主要呈現網站port，另外在 `package.json` 新增proxy去取得與 `localhost:8000` 溝通管道.
```json
// package.json
"proxy": "http://localhost:8000/"
```

### `部署環境設定`
當訪問網站時，透過 `localhost:8000` 回傳打包好的前端畫面.
```js
// app.js
app.use(express.static(path.join(__dirname, 'client/build')));

app.get('/*', (req,res) => {
  res.sendFile(path.join(__dirname, 'client/build', 'index.html'));
});
```

