# 培訓準備

參加培訓的學員，事先應該做好以下準備工作。

## 知識準備

- 掌握 HTML、CSS、JS 的基本用法
- 掌握命令列的基本用法

## 安裝 Git

請到官網 [git-scm.com](https://git-scm.com/) 或國內的下載站，下載安裝包。

## 安裝 Node

請到 Node 官網[nodejs.org](https://nodejs.org)，或者國內映象[npm.taobao.org/mirrors/node](https://npm.taobao.org/mirrors/node)，下載安裝包。推薦安裝最新的穩定版，目前是v6.x。

安裝完成後，命令列執行下面的命令，確認是否安裝成功。

```bash
$ node -v
v6.9.1
```

Node 的模組管理器 npm 會一起安裝好。由於 Node 的官方模組倉庫網速太慢，模組倉庫需要切換到阿里的源。

```bash
$ npm config set registry https://registry.npm.taobao.org/
```

執行下面的命令，確認是否切換成功。

```bash
$ npm config get registry
```

## 安裝 Postman

Postman 是一個 HTTP 通訊測試工具，REST API 的練習會用到它。

請到官網 [GetPostman.com](https://www.getpostman.com/) 下載獨立安裝包；也可以參考這篇文章[www.cnblogs.com/mafly/p/postman.html](http://www.cnblogs.com/mafly/p/postman.html)，下載 Chrome 瀏覽器的外掛，它們的效果一樣。

## 安裝示例庫

所有的講義和練習源碼，都是開源的，網址是 [github.com/ruanyf/jstraining](https://github.com/ruanyf/jstraining)。執行下面的命令，將這個庫拷貝到你的硬碟上。

```bash
# Linux & Mac
$ git clone git@github.com:ruanyf/jstraining.git

# Windows
$ git clone https://github.com/ruanyf/jstraining.git
```

如果因為種種原因，Git 命令列無法使用，也可以直接下載壓縮包，地址是 https://github.com/ruanyf/jstraining/archive/master.zip 。
