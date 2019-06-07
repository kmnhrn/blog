---
title: 文字コードを一括で変換する【Mac】
date: 2019-03-06 11:36:58
tags: Tec
---


## Homebrewからnkfをインストール

【前提】Homebrewのインストール
インストールがまだの方は[こちら](https://brew.sh/index_ja)からインストールしてください。

文字コードを変換するのに、Homebrew経由で``nkf``をインストールします。

```
$ brew install nkf
```

## nkfのオプション一覧

文字コードの変換
```
-j  JISに変換する
-e  EUCに変換する
-s  Shift-JISに変換する
-w  UTF8に変換する
```

その他よく使うオプション
```
-g 文字コードの結果を表示
–overwrite 引数のファイルに直接上書き
```


## 一括変換

``cd``でカレントディレクトリまで移動した後、入力することでそこに存在するファイルをすべてを書き換えます。


### Shift-JISに変換

```
$ nkf -s --overwrite ./*
```

### UTF8に変換する

```
$ nkf -w --overwrite ./*
```

## 変換されたかの確認

```
$ nkf -g hoge.html
```

期待通りの文字コードの結果が返ってきていれば成功です。
