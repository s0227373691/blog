---
layout: 作品集
title: 作品集 - 使用React模仿ETQ Amsterdam
date: 2021-10-17 01:41:03
tags:
  - 作品集
  - React
  - express
---

<!-- @format -->

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

## 設定 Port

為避免 Express 與 React 使用同一個 port，這邊我將 Express port 設為 8000，React 維持 3000.

```js
// ./bin/www
var port = normalizePort(process.env.PORT || '8000');
```

### `開發環境設定`

在開發過程中使用 `localhost:3000` 為主要呈現網站 port，另外在 `package.json` 新增 proxy 去取得與 `localhost:8000` 溝通管道.

```json
// package.json
"proxy": "http://localhost:8000/"
```

### `部署環境設定`

當訪問網站時，透過 `localhost:8000` 回傳打包好的前端畫面.

```js
// app.js
app.use(express.static(path.join(__dirname, 'client/build')));

app.get('/*', (req, res) => {
  res.sendFile(path.join(__dirname, 'client/build', 'index.html'));
});
```

進入部署階段，要送上去 `Heroku` 之前要先新增幾項指令:

- `build-client` 到 client 資料夾進行 `React` 打包
- `install-client` 到 client 資料夾進行安裝 `node_modules`
- `heroku-postbuild` 執行上述兩項指令

```json
"build-client": "cd client && npm run build",
"install-client": "cd client && npm install",
"heroku-postbuild": "npm run install-client && npm run build-client",
```

到這邊 Heroku 就能顯示網站的畫面啦~~~

![p1](https://i.imgur.com/oNNkidn.png)

&nbsp;

## 畫面製作

![p2](https://i.imgur.com/PPRgKlW.png)
![p3](https://i.imgur.com/zABeCvh.jpg)
![p4](https://i.imgur.com/66U73dU.png)
![p5](https://i.imgur.com/obKz1AL.jpg)
![p6](https://i.imgur.com/u4pHT31.png)
