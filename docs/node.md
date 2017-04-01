# Node 應用開發

---

## Node 簡介

Node 是伺服器的 JavaScript 執行環境，提供 API 與作業系統互動。

主要用途：

- 開發前端應用
- 快速搭建服務
- 架設網站

---

## npm

安裝 Node 的時候，會同時安裝 npm。

```bash
$ npm -v
```

它是 Node 的模組管理器，開發 Node 項目的必備工具。

---

## 課堂練習：Node 的簡單應用

進入`demos/simple-app-demo`目錄，參考[《操作指南》](../demos/README.md#simple-app)，自己動手在 Node 裡面，編寫並編譯一個前端指令碼。

---

## Node 開發前端指令碼的好處

1. 模組機制
1. 版本管理
1. 對外發布
1. 持續整合的標準開發流程

---

## REST API

REST 是瀏覽器與伺服器通訊方式的一種設計風格。

它的全稱是“REpresentational State Transfer”，中文意為”表現層狀態轉換“。

- Resource：資源
- Representation：表現層
- State：狀態
- Transfer：轉換

---

## REST 的核心概念

1. 網際網路上所有可以訪問的內容，都是資源。
1. 伺服器儲存資源，客戶端請求資源。
1. 同一個資源，有多種表現形式。
1. 協議本身不帶有狀態，通訊時客戶端必須通過參數，表示請求不同狀態的資源。
1. 狀態轉換通過HTTP動詞表示。

---

## URL 設計

URL 是資源的唯一識別符。

- /store/1
- /store/2
- /store/1/employee/2

---

## 查詢字元串

查詢字元串表示對所請求資源的約束條件。

- GET /zoos/1/animals?limit=10
- GET /zoos/1/animals?limit=10&offset=10
- GET /animals?zoo_id=1

---

## HTTP 動詞

|操作|SQL方法|HTTP動詞|
|----|-------|--------|
|CREATE|INSERT|POST|
|READ|SELECT|GET|
|UPDATE|UPDATE|PUT/PATCH|
|DELETE|DELETE|DELETE|

```
GET /v1/stores/1234
PUT /v1/stores/1234
POST /v1/stores
DELETE /v1/stores/1234
```

---

## 課堂練習：REST API

開啟`demos/rest-api-demo`，按照[《操作指南》](../demos/README.md#rest-api)，熟悉 REST API 的基本用法。

---

## Express

Express 是最常用的 Node 框架，用來搭建 Web 應用。

![](./images/express.png)

---

## 課堂練習：Express 搭建 Web 應用

進入`demos/express-demo`目錄，按照[《操作指南》](../demos/README.md#express)，學習使用 Express 搭建 Web 應用。

---

定義一個 Web 應用例項，並且啟動它。

```javascript
var express    = require('express');
var app        = express();

var port = process.env.PORT || 8080;

app.listen(port);
console.log('Magic happens on port ' + port);
```

---

定義一個路由

```javascript
var router = express.Router();

router.get('/', function(req, res) {
  res.send('<h1>Hello World</h1>');
});

app.use('/home', router);
```

---

中介軟體：對 HTTP 請求進行加工。

```javascript
router.use(function(req, res, next) {
  console.log('There is a requesting.');
  next();
});
```
