---
title: Hexoのテーマ：icarusインストール時に出たエラーの解決法
date: 2019-03-03 23:20:53
category: Tec
tag: Hexo
thumbnail:
---

<!-- toc -->

## icarusの導入時につまずく

themesディレクトリにicarusをインストールしたまではよかったものの、

```bash
$ hexo server
```

すると、以下のようなエラーを吐いてしまいました。

```bash
ERROR Script load failed: themes/icarus/scripts/index.js
/Users/xxxx/project/blog/blog/themes/icarus/includes/specs/config.spec.js:14
    ...require('./meta.spec'),
    ^^^
SyntaxError: Unexpected token ...
    at Object.exports.runInThisContext (vm.js:76:16)
    at Module._compile (module.js:542:28)
    at Object.Module._extensions..js (module.js:579:10)
    at Module.load (module.js:487:32)
    at tryModuleLoad (module.js:446:12)
    at Function.Module._load (module.js:438:3)
    at Module.require (module.js:497:17)
    at require (internal/module.js:20:19)
    at Object.<anonymous> (/Users/xxxx/project/blog/blog/themes/icarus/includes/tasks/check_config.js:8:18)
    at Module._compile (module.js:570:32)
    at Object.Module._extensions..js (module.js:579:10)
    at Module.load (module.js:487:32)
    at tryModuleLoad (module.js:446:12)
    at Function.Module._load (module.js:438:3)
    at Module.require (module.js:497:17)
    at require (/Users/xxxx/project/blog/blog/node_modules/hexo/lib/hexo/index.js:227:21)
    at /Users/xxxx/project/blog/blog/themes/icarus/scripts/index.js:3:1
    at fs.readFile.then.script (/Users/xxxx/project/blog/blog/node_modules/hexo/lib/hexo/index.js:240:12)
    at tryCatcher (/Users/xxxx/project/blog/blog/node_modules/bluebird/js/release/util.js:16:23)
    at Promise._settlePromiseFromHandler (/Users/xxxx/project/blog/blog/node_modules/bluebird/js/release/promise.js:512:31)
    at Promise._settlePromise (/Users/xxxx/project/blog/blog/node_modules/bluebird/js/release/promise.js:569:18)
    at Promise._settlePromise0 (/Users/xxxx/project/blog/blog/node_modules/bluebird/js/release/promise.js:614:10)
```

## nodeをアップデート

どうやらnodeのバージョンが古いためエラーを吐いている様子なので、nodebrewでアップデート。


```bash
$ nodebrew use latest
```

```use v11.10.0```にすることで、無事コンパイルが通りました。

