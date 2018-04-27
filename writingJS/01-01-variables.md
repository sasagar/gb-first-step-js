---
description: プログラムのことはわかった。じゃぁ、JavaScriptを書いてみようと思ったところで、解説を見るといろいろな書き方をされているJavaScript。新しいECMAScriptの仕様のせいでこんなことが起きているんだけど、最終的にどうするべきなの？ってのはそのとき次第。まずは違いを理解しよう
---

# 変数の宣言

プログラムでは変数を用意するに当たって、準備が必要。それを「宣言」という。  
＼この変数が有ります！／ って言っているという事。

その宣言の書き方が JavaScript だと 3 種類ある。

## var で宣言

書き方は簡単。 `var` の後ろに変数名を書くだけ。

```
var example;
```

こんな感じ。変数名には数字・アルファベットと一部の記号が使えるけど、最初が数字になってはいけない。  
他に予約語...つまりはプログラムで使う事が前提の文字列は指定出来ないので注意が必要。

この var は古き良き JavaScript の書き方。今はあまり使わない方が良いとされている。

その理由はこんなことが出来ちゃうから。

```
var example = 10;
var example = 20;

// 今のexampleは20
```

あらまぁ、宣言し直せちゃった。これはプログラムを書いていく中でミスに繋がるバグの温床。そりゃ使わない方が良いかもしれないね。

では、他の宣言を見てみよう。

## let で宣言

var に一番近いのが let。使い方は var と一緒。

```
let example;
```

これでオッケー。

ポイントは var との違いだけど、再宣言はできなくなっているという点が違う。

```
let example = 10;
// 今のexampleは10
example = 20;
// 今のexampleは20

let example = 30;
// エラーが出る: Identifier 'example' has already been declared.
```

エラーを見ると大変そうに思うかも知れないけど言っていることはシンプル。declared は「宣言した」という意味なので、「example は既に宣言されています」というエラー。  
エラーメッセージって実はちゃんと書かれてるんです。Google 翻訳さんに頼ってでも見てみるとわかることがあるかもね。

もう一つの宣言は...？

## const で宣言

宣言の仕方は今まで通り。

```
const example;
```

今度は再宣言だけで無く、再代入すらできない。

```
let example = 10;
// 今のexampleは10
example = 20;
// エラーが出る: TypeError: Assignment to constant variable.
```

const が constant の略なので、定数という意味。  
定数には代入出来ませんっていうエラーですね。

# これからは let と const を使っていこう

そんなこんなで ES2015 で登場した let と const。プログラムを書き続ける中でエラーの温床となり得る部分を取り払ってくれるとても良い書き方なので、できるだけこれを使っていった方が良いと思う。  
さよなら var！

ちなみに、これらが使えないって言われたら `"use strict";` を一行目に足してあげると良いみたい。  
これは strict モードを使いますよという宣言。大抵の現行ブラウザでは必要ないことが多いけど、必要な場合もあるかも知れないので、頭の片隅に入れておくと良いかも。