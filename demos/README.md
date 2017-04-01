# 課堂練習的操作指導

## 目錄

- 前端開發的歷史和趨勢
  - [Backbone](#backbone)
  - [Angular](#angular)
  - [Vue](#vue)
- React 技術棧
  - [JSX](#jsx)
  - [React 元件語法](#react-元件語法)
  - [React 元件的參數](#react-元件的參數)
  - [React 元件的狀態](#react-元件的狀態)
  - [React 元件實戰](#react-元件實戰)
  - [React 元件的生命週期](#react-元件的生命週期)
  - [ReCharts](#recharts)
  - [MobX](#mobx)
  - [Redux](#redux)
- Node 開發
  - [Simple App](#simple-app)
  - [REST API](#rest-api)
  - [Express](#express)
- 前端工程簡介
  - [ESLint](#eslint)
  - [Mocha](#mocha)
  - [Nightmare](#nightmare)
  - [Travis CI](#travis-ci)

## Backbone

### 實驗目的

1. 理解前端框架的路由元件（`router`）的作用

### 操作步驟

1. 瀏覽器開啟[`demos/backbone-demo/index.html`](./backbone-demo/index.html)
1. 點選頁面上的連結，注意瀏覽器 URL 的變化
1. 仔細檢視[`js/main.js`](./backbone-demo/js/main.js)的源碼，看懂 Router 元件的使用方式

## Angular

### 實驗目的

1. 理解 Angular 的雙向繫結機制

### 操作步驟

1. 瀏覽器開啟[`demos/angular-demo/index.html`](./angular-demo/index.html)
1. 在輸入框填入內容，注意頁面變化
1. 檢視[`index.html`](./angular-demo/index.html)的源碼，理解 Angular 對 HTML 標籤的增強

## Vue

### 實驗目的

1. 理解 Vue 的模板與資料的雙向繫結

### 操作步驟

1. 瀏覽器開啟[`demos/vue-demo/index1.html`](./vue-demo/index1.html)
1. 在輸入框填入內容，注意頁面變化
1. 檢視[`app1.js`](./vue-demo/app1.js)，理解 Vue 元件的基本寫法

### 注意事項

1. [`index2.html`](./vue-demo/index2.html)是一個稍微複雜的例子，模板如何繫結資料物件的一個欄位。
2. [`index3.html`](./vue-demo/index3.html)是事件繫結模板的例子。

## JSX

### 實驗目的

1. 掌握 JSX 基本語法

### 操作步驟

1. 瀏覽器開啟`demos/jsx-demo/index.html`，仔細檢視源碼。

### 注意事項

1. `ReactDOM.render`方法接受兩個參數：一個虛擬 DOM 節點和一個真實 DOM 節點，作用是將虛擬 DOM 掛載到真實 DOM。

### 練習

1. 修改源碼，將顯示文字變為 ”Hello React!“。

## React 元件語法

### 實驗目的

1. 掌握 React 元件的基本寫法

### 操作步驟

1. 瀏覽器開啟`demos/react-component-demo/index1.html`，仔細檢視源碼。

### 注意事項

1. `class MyTitle extends React.Component`是 ES6 語法，表示自定義一個`MyTitle`類，該類繼承了基類`React.Component`的所有屬性和方法。
1. React 規定，自定義元件的第一個字母必須大寫，比如`MyTitle`不能寫成`myTitle`，以便與內建的原生類相區分。
1. 每個元件都必須有`render`方法，定義輸出的樣式。
1. `<MyTitle/>`表示生成一個元件類的例項，每個例項一定要有閉合標籤，寫成`<MyTilte></MyTitle>`也可。

## React 元件的參數

### 實驗目的

1. 學會向 React 元件傳參數

### 操作步驟

1. 瀏覽器開啟`demos/react-component-demo/index2.html`，仔細檢視源碼。

### 注意事項

1. 元件內部通過`this.props`物件獲取參數。

### 練習

1. 將元件的顏色，從紅色（`red`）換成黃色（`yellow`）。

## React 元件的狀態

### 實驗目的

1. 學會通過狀態變動，引發元件的重新渲染。

### 操作步驟

1. 瀏覽器開啟`demos/react-component-demo/index3.html`，仔細檢視源碼。

### 注意事項

```javascript
  class MyTitle extends React.Component {
    function Object() { [native code] }(...args) {
      super(...args);
      this.state = {
        name: '訪問者'
      };
    }
    // ...
```

`function Object() { [native code] }`是元件的建構函式，會在建立例項時自動呼叫。`...args`表示元件參數，`super(...args)`是 ES6 規定的寫法。`this.state`物件用來存放內部狀態，這裡是定義初始狀態。

```html
<div>
  <input
    type="text"
    onChange={this.handleChange.bind(this)}
  />
  <p>你好，{this.state.name}</p>
</div>;
```

`this.state.name`表示讀取`this.state`的`name`屬性。每當輸入框有變動，就會自動呼叫`onChange`指定的監聽函數，這裡是`this.handleChange`，`.bind(this)`表示該方法內部的`this`，繫結當前元件。

```javascript
handleChange(e) {
  let name = e.target.value;
  this.setState({
    name: name
  });
}
```

`this.setState`方法用來重置`this.state`，每次呼叫這個方法，就會引發元件的重新渲染。

## React 元件實戰

### 實驗目的

1. 學會自己寫簡單的 React 元件。

### 操作步驟

1. 瀏覽器開啟`demos/react-component-demo/index4.html`。
1. 點選`Hello World`，看看會發生什麼。

### 練習

1. 修改源碼，使得點選`Hello World`後，會顯示當前的日期，比如`Hello 2016年1月1日`。

2. 請在上一步練習的基礎上，進一步修改。現在`Hello World`點選一次，會改變內容，再點選就不會有反應了。請將其改成，再點選一次變回原樣。

### 提示

 練習一、下面的程式碼可以得到當前日期。

```javascript
var d = new Date();
d.getFullYear() // 當前年份
d.getMonth() + 1 // 當前月份
d.getDate() // 當前是每個月的幾號
```

練習二、可以在`this.state`裡面設定一個開關變數`isClicked`。

```javascript
this.state = {
  text: 'World',
  isClicked: false
};
```

然後，在`this.handleClick`方法裡面，做一個`toggle`效果。

```javascript
let isClicked = !this.state.isClicked;
this.setState({
  isClicked: isClicked,
  text: isClicked ? 'Clicked' : 'World'
});
```

## React 元件的生命週期

### 實驗目的

1. 掌握鉤子方法的基本用法
1. 掌握元件如何通過 Ajax 請求獲取資料，並對資料進行處理

### 操作步驟

1. 開啟`demos/react-lifecycle-demo/index.html`，仔細檢視源碼。

### 注意事項

```javascript
componentDidMount() {
  const url = '...';
  $.getJSON(url)
    .done()
    .fail();
}
```

- `componentDidMount`方法在元件載入後執行，只執行一次。本例在這個方法裡向伺服器請求資料，操作結束前，元件都顯示`Loading`。
- `$.getJSON`方法用於向伺服器請求 JSON 資料。本例的資料從 Github API 獲取，可以開啟源碼裡面的連結，看看原始的資料結構。

### 練習

1. 本例的 JSON 資料是 Github 上面最受歡迎的 JavaScript 項目。請在網頁上顯示一個列表，列出這些項目。

### 提示

（1） `this.state.loading`記錄資料載入是否結束。只要資料請求沒有結束，`this.state.loading`就一直是`true`，網頁上顯示`loading`。

（2） `this.state.error`儲存資料請求失敗時的錯誤資訊。如果請求失敗，`this.state.error`就是返回的錯誤物件，網頁上顯示報錯資訊。

（3） `this.state.data`儲存從伺服器獲取的資料。如果請求成功，可以先用`console.log`方法，將它在控制檯裡列印出來，看看資料結構。

```javascript
render() {
  // 加一行列印命令，看看資料結構
  console.log(this.state.data);
  return {
  // ...
```

（4） `this.state.data`裡面的`this.state.data.items`應該是一個陣列，儲存著每個項目的具體資訊。可以使用`forEach`方法進行遍歷處理。

```javascript
var projects = this.state.data.items;
var results = [];
projects.forEach(p => {
  var item = <li>{p.name}</li>;
    results.push(item);
});
```

（5）然後，將上一步的`results`插入網頁即可。

```javascript
<div>
  <ul>{results}</ul>
</div>
```

## ReCharts

### 實驗目的

1. 瞭解如何使用第三方元件庫。

### 操作步驟

1. 瀏覽器開啟`demos/recharts-demo/index.html`，檢視效果。

## MobX

### 實驗目的

1. 理解 MobX 框架

### 操作步驟

（1）瀏覽器開啟`demos/mobx-demo/browser-demo/index.html`，仔細檢視源碼

（2） 命令列進入`demos/mobx-demo/`目錄，執行如下的命令。

```bash
$ npm install
$ npm start
```

（3） 開啟瀏覽器，訪問 http://localhost:8080，檢視結果，並仔細研究`app/`目錄下面的程式碼。

### 注意事項

```javascript
@observer
class App extends React.Component {
  render() {
    // ...
  }
}
```

`@observer`是一種新的語法，叫做“裝飾器”，表示對整個類的行為進行修改，即將`App`類作為參數傳入`observer`函數。這裡的意思是，整個`App`類都是一個“觀察者”，觀察`store`的變化，只要一有變化，立刻重新渲染。

資料儲存在`Store`裡面。`Store`的屬性分成兩種：被觀察的屬性（`@observable`），和自動計算得到的屬性`@computed`。

```javascript
class Store {
  @observable name = 'Bartek';
  @computed get decorated() {
    return `${this.name} is awesome!`;
  }
}
```

`Store`的變化由使用者引發。元件觀察到`Store`的變化，自動重新渲染。

```javascript
<p>
  {this.props.store.decorated}
</p>
<input
  defaultValue={this.props.store.name}
  onChange={
    (event) =>
      this.props.store.name = event.currentTarget.value
  }
/>
```

## Redux

### 實驗目的

1. 理解 Redux 架構

### 操作步驟

（1） 命令列下進入`demos/redux-demo`目錄，執行如下的命令。

```bash
$ npm install
$ npm start
```

（2）開啟瀏覽器，訪問 http://localhost:8080，檢視結果，並仔細研究程式碼。

### 注意事項

（1） Redux 要求 UI 的渲染元件都是純元件，即不包含任何狀態（`this.state`）的元件。

```javascript
<div className="index">
  <p>{this.props.text}</p>
  <input
    defaultValue={this.props.name}
    onChange={this.props.onChange}
  />
</div>
```

（2） 進行資料處理、幷包含狀態的元件，稱為”容器元件“。Redux 使用`connect`方法，自動生成 UI 元件對應的”容器元件“。

```javascript、
// MyComponent 是純的 UI 元件
const App = connect(
  mapStateToProps,
  mapDispatchToProps
)(MyComponent);
```

（3） `mapStateToProps`函數返回一個物件，表示一種對映關係，將 UI 元件的參數對映到`state`。

```javascript
function mapStateToProps(state) {
  return {
    text: state.text,
    name: state.name
  };
}
```

（4） `mapDispatchToProps`函數也是返回一個物件，表示一種對映關係，但定義的是哪些使用者的操作應該當作`Action`，傳給`Store`。

```javascript
function mapDispatchToProps(dispatch) {
  return {
    onChange: (e) => dispatch({
      type: 'change',
      payload: e.target.value
    })
  }
}
```

（5） `reducer`函數用來接收`action`，算出新的`state`。

```javascript
function reducer(state = {
  text: '你好，訪問者',
  name: '訪問者'
}, action) {
  switch (action.type) {
    case 'change':
      return {
        name: action.payload,
        text: '你好，' + action.payload
      };
  }
}
```

`Store`由 Redux 提供的`createStore`方法生成，該方法接受`reducer`作為參數。

```javascript
const store = createStore(reducer);

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.body.appendChild(document.createElement('div'))
);
```

為了把`Store`傳入元件，必須使用 Redux 提供的`Provider`元件在應用的最外面，包裹一層。

## Simple App

### 實驗目的

1. 學會使用 Node 編寫簡單的前端應用。

### 操作步驟

（1）新建一個目錄

```bash
$ mkdir simple-app-demo
$ cd simple-app-demo
```

（2）在該目錄下，新建一個`package.json`檔案。

```bash
$ npm init -y
```

`package.json`是項目的配置檔案。

（3）安裝`jquery`和`webpack`這兩個模組。

```bash
$ npm install -S jquery
$ npm install -S webpack
```

開啟`package.json`檔案，會發現`jquery`和`webpack`都加入了`dependencies`欄位，並且帶有版本號。

（4）在項目根目錄下，新建一個網頁檔案`index.html`。

```html
<html>
  <body>
    <h1>Hello World</h1>
    <script src="bundle.js"></script>
  </body>
</html>
```

（5）在項目根目錄下，新建一個指令碼檔案`app.js`。

```javascript
const $ = require('jquery');
$('h1').css({ color: 'red'});
```

上面程式碼中，`require`方法是 Node 特有的模組載入命令。

（6）開啟`package.json`，在`scripts`欄位裡面，新增一行。

```javascript
"scripts": {
  "build": "webpack app.js bundle.js",
  "test": "...."
},
```

（7） 在項目根目錄下，執行下面的命令，將指令碼打包。

```bash
$ npm run build
```

執行完成，可以發現項目根目錄下，新生成了一個檔案`bundle.js`。

（8）瀏覽器開啟`index.html`，可以發現`Hello World`變成了紅色。

### 練習

1. 修改樣式，將標題變為藍色，然後重新編譯生成打包檔案。

## REST API

### 實驗目的

1. 熟悉 REST API 的基本用法

### 操作步驟

（1） 命令列進入`demos/rest-api-demo`目錄，執行下面的命令。

```bash
$ npm install -S json-server
```

（2） 在項目根目錄下，新建一個 JSON 檔案`db.json`。

```javascript
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}
```

（3） 開啟`package.json`，在`scripts`欄位新增一行。

```javascript
"scripts": {
  "server": "json-server db.json",
  "test": "..."
},
```

（4） 命令列下執行下面的命令，啟動服務。

```bash
$ npm run server
```

（5）開啟 Chrome 瀏覽器的 Postman 應用。依次向`http://127.0.0.1:3000/posts`、`http://127.0.0.1:3000/posts/1`發出`GET`請求，檢視結果。

（6）向`http://127.0.0.1:3000/comments`發出`POST`請求。注意，資料體`Body`要選擇`x-www-form-urlencoded`編碼，然後依次新增下面兩個欄位。

```javascript
body: "hello world"
postId: 1
```

發出該請求後，再向`http://127.0.0.1:3000/comments`發出`GET`請求，檢視結果。

（7） 向`http://127.0.0.1:3000/comments/2`發出`PUT`請求，資料體`Body`要選擇`x-www-form-urlencoded`編碼，然後新增下面的欄位。

```javascript
body: "hello react"
```

發出該請求後，再向`http://127.0.0.1:3000/comments`發出`GET`請求，檢視結果。

（8）向`http://127.0.0.1:3000/comments/2`發出`delete`請求。

發出該請求後，再向`http://127.0.0.1:3000/comments`發出`GET`請求，檢視結果。

## Express

### 實驗目的

1. 學會 Express 搭建 Web 應用的基本用法。

### 操作步驟

（1）進入`demos/express-demo`目錄，命令列執行下面的命令，安裝依賴。

```bash
$ cd demos/express-demo
$ npm install
```

（2）開啟`app1.js`，嘗試看懂這個指令碼。

```javascript
var express    = require('express');
var app        = express();
```

上面程式碼呼叫`express`，生成一個 Web 應用的例項。

```javascript
var router = express.Router();

router.get('/', function(req, res) {
  res.send('<h1>Hello World</h1>');
});

app.use('/home', router);
```

上面程式碼新建了一個路由物件，該物件指定訪問根路由（`/`）時，返回`Hello World`。然後，將該路由載入在`/home`路徑，也就是說，訪問`/home`會返回`Hello World`。

`router.get`方法的第二個參數是一個回撥函數，當符合指定路由的請求進來，會被這個函數處理。該函數的兩個參數，`req`和`res`都是Express 內建的物件，分別表示使用者的請求和 Web 伺服器的迴應。`res.send`方法就表示伺服器迴應所送出的內容。

```javascript
var port = process.env.PORT || 8080;

app.listen(port);
console.log('Magic happens on port ' + port);
```

上面程式碼指定了外部訪問的埠，如果環境變數沒有指定，則埠預設為`8080`。最後兩行是啟動應用，並輸出一行提示文字。

（3）在命令列下，啟動這個應用。

```bash
$ node app1.js
```

瀏覽器訪問`localhost:8080/home`，看看是否輸出`Hello World`。

然後，命令列下按 Ctrl + C，退出這個程序。

（4）通過環境變數，自定義啟動埠。

假定我們指定必須啟動在`7070`埠，命令列可以這樣操作。

```bash
# Linux & Mac
$ PORT=7070 node app1.js

# windows
$ set PORT=7070
$ node app1.js
```

瀏覽器就可以訪問`localhost:7070/home`了。

然後，命令列下按 Ctrl + C，退出這個程序。

思考題：Node 應用能否直接在`80`埠啟動？

（5）開啟`app2.js`，檢視新增的那個路由。

```javascript
router.get('/:name', function(req, res) {
  res.send('<h1>Hello ' + req.params.name + '</h1>');
});
```

上面程式碼新增了一個路由，這個路由的路徑是一個命名參數`:name`，可以從`req.params.name`拿到這個傳入的參數。

在命令列下，啟動這個應用。

```bash
$ node app2.js
```

瀏覽器訪問`localhost:8080/home/張三`，看看是否輸出`Hello 張三`。

然後，命令列下按 Ctrl + C，退出這個程序。

（6）開啟`app3.js`，先檢視頁面頭部新增的兩行程式碼。

```javascript
var express    = require('express');
var app        = express();

// 新增程式碼...
var bodyParser = require('body-parser');
app.use(bodyParser.urlencoded({ extended: true }));

// ...
```

上面程式碼中，`body-parser`模組的作用，是對`POST`、`PUT`、`DELETE`等 HTTP 方法的資料體進行解析。`app.use`用來將這個模組載入到當前應用。有了這兩句，就可以處理`POST`、`PUT`、`DELETE`等請求了。

下面檢視新增的那個路由。

```javascript
router.post('/', function (req, res) {
  var name = req.body.name;
  res.json({message: 'Hello ' + name});
});
```

上面程式碼表示，如果收到了`/`路徑（實際上是`/home`路徑）的`POST`請求，先從資料體拿到`name`欄位，然後返回一段 JSON 資訊。

在命令列下，啟動這個應用。

```bash
$ node app3.js
```

然後，在 Chrome 瀏覽器的 Postman 外掛裡面，向`http://127.0.0.1:8080/home`發出一個`POST`請求。資料體的編碼方法設為`x-www-form-urlencoded`，裡面設定一個`name`欄位，值可以隨便取，假定設為`Alice`。也就是說，發出這樣一個請求。

```
POST /home HTTP/1.1
Host: 127.0.0.1:8080
Content-Type: application/x-www-form-urlencoded

name=Alice
```

如果一切正常，伺服器會返回一段 JSON 資訊。

```javascript
{
  "message": "Hello Alice"
}
```

（7）開啟`app4.js`，檢視在所有路由之前新增的那個函數。

```javascript
var router = express.Router();

// 新增的程式碼
router.use(function(req, res, next) {
  console.log('There is a requesting.');
  next();
});

router.get('/', function(req, res) {
  // ...
```

`router.use`的作用是載入一個函數。這個函數被稱為中介軟體，作用是在請求被路由匹配之前，先進行一些處理。上面這個中介軟體起到 logging 的作用，每收到一個請求，就在命令列輸出一條記錄。請特別注意，這個函數內部的`next()`，它代表下一個中介軟體，表示將處理過的請求傳遞給下一個中介軟體。這個例子只有一箇中介軟體，就進入路由匹配處理（實際上，`bodyparser`、`router`本質都是中介軟體，整個 Express 的設計哲學就是不斷對 HTTP 請求加工，然後返回一個 HTTP 迴應）。

### 練習

1. 請增加一箇中介軟體，伺服器每次收到使用者請求，會在伺服器的控制檯列印出收到請求的時間。

2. URL 的查詢字元串，比如`localhost:8080?name=Alice`裡面的`name`，可以用`req.query.name`拿到。請修改一個路由，使之可以收到查詢字元串，然後輸出`'Hello ' + req.query.name`。

## ESLint

### 實驗目的

1. 學會使用 ESLint 進行程式碼檢查。

### 操作步驟

（1）進入`demos/eslint-demo`目錄，安裝 ESLint。

```bash
$ cd demos/eslint-demo
$ npm install eslint --save-dev
```

（2）通常，我們會使用別人已經寫好的程式碼檢查規則，這裡使用的是 Airbnb 公司的規則。所以，還要安裝 ESLint 這個規則模組。

```bash
$ npm install eslint-plugin-import eslint-config-airbnb-base --save-dev
```

上面程式碼中，`eslint-plugin-import`是執行這個規則集必須的，所以也要一起安裝。

（3）ESLint 的配置檔案是`.eslintrc.json`，放置在項目的根目錄下面。新建這個檔案，在裡面指定使用 Airbnb 的規則。

```javascript
{
  "extends": "airbnb-base"
}
```

（4）開啟項目的`package.json`，在`scripts`欄位裡面新增三個指令碼。

```javascript
{
  // ...
  "scripts" : {
    "test": "echo \"Error: no test specified\" && exit 1",
    "lint": "eslint **/*.js",
    "lint-html": "eslint **/*.js -f html -o ./reports/lint-results.html",
    "lint-fix": "eslint --fix **/*.js"
  },
  // ...
}
```

除了原有的`test`指令碼，上面程式碼新定義了三個指令碼，它們的作用如下。

- `lint`：檢查所有`js`檔案的程式碼
- `lint-html`：將檢查結果寫入一個網頁檔案`./reports/lint-results.html`
- `lint-fix`：自動修正某些不規範的程式碼

（5）執行靜態檢查命令。

```bash
$ npm run lint

  1:5  error    Unexpected var, use let or const instead  no-var
  2:5  warning  Unexpected console statement              no-console

✖ 2 problems (1 error, 1 warning)
```

正常情況下，該命令會從`index.js`指令碼里面，檢查出來兩個錯誤：一個是不應該使用`var`命令，另一個是不應該在生產環境使用`console.log`方法。

（6）修正錯誤。

```bash
$ npm run lint-fix
```

執行上面的命令以後，再檢視`index.js`，可以看到`var x = 1;`被自動改成了`const x = 1;`。這樣就消除了一個錯誤，但是還留下一個錯誤。

（7）修改規則。

由於我們想要允許使用`console.log`方法，因此可以修改`.eslintrc.json`，改變`no-console`規則。請將`.eslintrc.json`改成下面的樣子。

```javascript
{
  "extends": "airbnb-base",

  "rules": {
    "no-console": "off"
  }
}
```

再執行`npm run lint`，就不會報錯了。

```bash
$ npm run lint
```

## Mocha

### 實驗目的

1. 學會使用 Mocha 進行單元測試。

### 操作步驟

（1） 進入`demos/mocha-demo`目錄，安裝 Mocha 和 Chai。

```bash
$ cd demos/mocha-demo
$ npm install -D mocha
$ npm install -D chai
```

（2）開啟`add.js`檔案，檢視源碼，我們要測試的就是這個指令碼。

```javascript
function add(x, y) {
  return x + y;
}

module.exports = add;
```

（3）編寫一個測試指令碼`add.test.js`。

```javascript
var add = require('./add.js');
var expect = require('chai').expect;

describe('加法函數的測試', function() {
  it('1 加 1 應該等於 2', function() {
    expect(add(1, 1)).to.be.equal(2);
  });
});
```

測試指令碼與所要測試的源碼指令碼同名，但是字尾名為`.test.js`（表示測試）或者`.spec.js`（表示規格）。比如，`add.js`的測試指令碼名字就是`add.test.js`。

測試指令碼里面應該包括一個或多個`describe`塊，每個`describe`塊應該包括一個或多個`it`塊。

`describe`塊稱為"測試套件"（test suite），表示一組相關的測試。它是一個函數，第一個參數是測試套件的名稱（"加法函數的測試"），第二個參數是一個實際執行的函數。

`it`塊稱為"測試用例"（test case），表示一個單獨的測試，是測試的最小單位。它也是一個函數，第一個參數是測試用例的名稱（"1 加 1 應該等於 2"），第二個參數是一個實際執行的函數。

上面的測試指令碼里面，有一句斷言。

```javascript
expect(add(1, 1)).to.be.equal(2);
```

所謂"斷言"，就是判斷源碼的實際執行結果與預期結果是否一致，如果不一致就拋出一個錯誤。上面這句斷言的意思是，呼叫`add(1, 1)`，結果應該等於`2`。

所有的測試用例（`it`塊）都應該含有一句或多句的斷言。它是編寫測試用例的關鍵。斷言功能由斷言庫來實現，Mocha本身不帶斷言庫，所以必須先引入斷言庫。

```javascript
var expect = require('chai').expect;
```

斷言庫有很多種，Mocha並不限制使用哪一種。上面程式碼引入的斷言庫是`chai`，並且指定使用它的`expect`斷言風格。

（4）開啟`package.json`檔案，改寫`scripts`欄位的`test`指令碼。

```javascript
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1"
},

// 改成

"scripts": {
  "test": "mocha *.test.js"
},
```

（5）命令列下，執行下面的命令，執行測試用例。

```bash
$ npm test
```

正常情況下，命令列會有提示，表示測試用例已經通過了。

### 練習

1. 請在`add.test.js`裡面新增一個測試用例，測試`3`加上`-3`，`add`函數應該返回`0`。

## Nightmare

### 實驗目的

1. 學會使用 Nightmare 完成功能測試。

### 操作步驟

（1）進入`./demos/nightmare-demo`目錄，安裝依賴。

```bash
$ cd demos/nightmare-demo

# Linux & Mac
$ env ELECTRON_MIRROR=https://npm.taobao.org/mirrors/electron/ npm install

# Windows
$ set ELECTRON_MIRROR=https://npm.taobao.org/mirrors/electron/
$ npm install
```

注意，Nightmare 會先安裝 Electron，而 Electron 的安裝需要下載境外的包，有時會連不上，導致安裝失敗。所以，這裡先設定了環境變數，指定使用國內的 Electron 源，然後才執行安裝命令。

（2）檢視一下瀏覽器自動化指令碼`taobao.test.js`。

```javascript
var Nightmare = require('nightmare');
var nightmare = Nightmare({ show: true });
```

上面程式碼表示新建一個 Nightmare 例項，並且執行功能中，自動開啟瀏覽器視窗。

```javascript
nightmare
  .goto('https://www.taobao.com/')
  .type('#q', '電視機')
  .click('form[action*="/search"] [type=submit]')
  .wait('#spulist-grid')
  .evaluate(function () {
    return document.querySelector('#spulist-grid .grid-item .info-cont')
      .textContent.trim();
  })
  .end()
```

上面程式碼表示，開啟淘寶首頁，在搜尋框鍵入`電視機`，點選”搜尋“按鈕，等待`#spulist-grid`元素出現，在頁面內注入（`evaluate`）程式碼，將執行結果返回。

```javascript
  .then(function (result) {
    console.log(result);
  })
  .catch(function (error) {
    console.error('Search failed:', error);
  });
```

Nightmare 會返回一個 Promise 物件，`then`方法指定操作成功的回撥函數，`catch`方法指定操作失敗的回撥函數。

（3）命令列下執行這個示例指令碼。

```bash
$ node taobao.test.js
```

正常情況下，執行結束後，命令列會顯示淘寶”電視機“搜尋結果的第一項。

（4）瀏覽器開啟`index.html`檔案，這是 React 練習時做過的一個例子，點選`Hello World`，標題會變成`Hello Clicked`。我們就要編寫測試指令碼，測試這個功能。

（5）開啟測試指令碼`test.js`。

```javascript
var Nightmare = require('nightmare');
var expect = require('chai').expect;
var fork = require('child_process').fork;

describe('test index.html', function() {
  var child;

  before(function (done) {
    child = fork('./server.js');
    child.on('message', function (msg) {
      if (msg === 'listening') {
        done();
      }
    });
  });

  after(function () {
    child.kill();
  });
```

上面程式碼中，`before`和`after`是 Mocha 提供的兩個鉤子方法，分別在所有測試開始前和結束後執行。這裡，我們在`before`方法裡面，新建一個子程序，用來啟動 HTTP 伺服器；測試結束後，再殺掉這個子程序。

注意，`before`方法的參數是一個函數，它接受`done`作為參數。`done`是 Mocha 提供的一個函數，用來表示非同步操作完成。如果不呼叫`done`，Mocha 就會認為非同步操作沒有結束，一直停在這一步，不往下執行，從而導致超時錯誤。

子程序指令碼`server.js`的程式碼非常簡單，只有四行。

```javascript
var httpServer = require('http-server');
var server = httpServer.createServer();
server.listen(8080);
process.send('listening');
```

上面程式碼中，我們在`8080`埠啟動 HTTP 伺服器，然後向父程序發訊息，表示啟動完成。

（6）真正的自動化測試指令碼如下。

```javascript
  it('點選後標題改變', function(done) {
    var nightmare = Nightmare({ show: true });
    nightmare
      .goto('http://127.0.0.1:8080/index.html')
      .click('h1')
      .wait(1000)
      .evaluate(function () {
        return document.querySelector('h1').textContent;
      })
      .end()
      .then(function(text) {
        expect(text).to.equal('Hello Clicked');
        done();
      })
  });
```

上面程式碼中，首先開啟網頁，點選`h1`元素，然後等待 1 秒鐘，注入指令碼獲取`h1`元素的文字內容。接著，在`then`方法裡面，做一個斷言，判斷獲取的文字是否正確。

（7）執行這個測試指令碼。

```bash
$ npm test
```

如果一切正常，命令列下會顯示測試通過。

### 練習

1. 請寫一個測試用例，驗證`<h1>`的字型顏色是紅色。（提示：可以使用`Window.getComputedStyle()`方法，獲取元素的最終樣式。）

## Travis CI

### 實驗目的

1. 瞭解持續整合的做法，學會使用 Travis CI。

### 操作步驟

（1）註冊 [Github](https://github.com) 的賬戶。如果你已經註冊過，跳過這一步。

（2）訪問這個程式碼庫[`github.com/ruanyf/travis-ci-demo`](https://github.com/ruanyf/travis-ci-demo)，點選右上角的`Fork`按鈕，將它克隆到你自己的空間裡面。

（3）將你`fork`的程式碼庫，克隆到本地。注意，要將下面網址之中的`[your_username]`改成你的 Github 使用者名稱。

```bash
// Linux & Mac
$ git clone git@github.com:[your_username]/travis-ci-demo.git

// Windows
$ git clone https://github.com:[your_username]/travis-ci-demo
```

（4）使用你的 Github 賬戶，登入 [Travis CI](https://travis-ci.org/auth) 的首頁。然後，訪問 [Profile](https://travis-ci.org/profile) 頁面，選定`travis-ci-demo`程式碼庫執行自動構建。

（5）回到命令列，進入你本地的`travis-ci-demo`目錄，切換到`demo01`分支。

```bash
$ cd travis-ci-demo
$ git checkout demo01
```

項目根目錄下面有一個`.travis.yml`檔案，這是 Travis CI 的配置檔案。如果沒有這個檔案，就不會觸發 Travis CI 的自動構建。開啟看一下。

```bash
language: node_js
node_js:
  - "node"
```

上面程式碼指定，使用 Node 完成構建，版本是最新的穩定版。

指定 Node 的版本號也是可以的。

```javascript
language: node_js
node_js:
  - "4.1"
```

上面程式碼指定使用 Node 4.1 版。

（6）Travis CI 預設依次執行以下九個指令碼。

- `before_install`
- `install`
- `before_script`
- `script`
- `after_success` 或者 `after_failure`
- `after_script`
- `before_deploy`（可選）
- `deploy`（可選）
- `after_deploy`（可選）

使用者需要用到哪個指令碼，就需要提供該指令碼的內容。

對於 Node 項目，以下兩個指令碼有預設值，可以不用自己設定。

```javascript
"install": "npm install",
"script": "npm test"
```

（7）開啟當前分支的`package.json`，可以發現它的`test`指令碼是一個`lint`命令。

```javascript
"scripts": {
  "test": "jshint hello.js"
},
```

（8）在項目根目錄下，新建一個新檔案`NewUser.txt`，內容是你的使用者名稱。提交這個檔案，就會觸發 Travis CI 的自動構建。

```bash
$ git add -A
$ git commit -m 'Testing Travis CI'
$ git push
```

（9）等到 Travis CI 完成自動構建，到頁面上[檢查](https://travis-ci.org/repositories)構建結果。

（10）切換到`demo02`分支，開啟`package.json`，可以看到`test`指令碼，現在需要完成兩步操作了。

```javascript
  "scripts": {
    "lint": "jshint hello.js hello.test.js",
    "test": "npm run lint && mocha hello.test.js"
  },
```

（11）重複上面第 8 步和第 9 步。

### 練習

1. 修改`hello.js`，讓其輸出`Hello Node`。並修改測試用例`hello.test.js`，使之能夠通過 Travis CI 的自動構建。
