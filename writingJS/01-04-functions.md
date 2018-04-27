---
description: 関数を作れる様になるといろいろな処理をまとめていける。そうすれば初心者から脱するのも近い！
---

# 関数定義

関数は JavaScript 自体が持っている物もたくさんあるけど、自分で書くことも多い。  
どんな形で書くのか憶えておこう。

## 古き良き JavaScript スタイル

### 基本形

シンプルに、呼び出して実行するだけの関数を作るとしたら...。

```
function example() {
	// 命令を書く
}
```

これで作れたので、実行するときにはこんな感じ。

```
example();
```

ほら、簡単でしょ？

このとき処理の中で `return` を使ってあげると、結果を「返す」って言うことも可能。

```
function example() {
	return 50;
}

const test = example();
console.log( test );
// 出力内容: 50
```

こんな感じで結果を伝えて、その情報を利用することが殆どじゃないかな...。  
複雑になると、勿論処理だけってこともあるけどね。

### 引数を使うパターン

何かしら情報を渡して実行したいという場合にはこんな感じになる。

```
function example( val ) {
	return val * 10;
}

const test = example( 5 );
console.log( test );
// 出力結果: 50
```

値が複数なら

```
function example( val1, val2 ) {
	return val1 * val2;
}

const test = example( 7, 8 );
console.log( test );
// 出力結果: 56
```

こんな感じね。割と簡単でしょ？

## ES 記法

最近登場した ES 記法。これになるとちょっと記述が変わる。  
解説によってはこの書き方をされていることもあると思うので、一応整理しておこう。

### 基本形

ES では、アロー関数という方法を採る。  
アロー関数は、処理を変数に入れ込むというイメージで書かれるので、こんな感じ。

```
const example () => {
	// ココに処理を書く
}
```

使い方は一緒。

```
example();
```

これで使える。わかれば簡単。

### 引数を使うパターン

古き良き JavaScript でも括弧の中に引数を入れたのと同じように書ける。

```
example ( val ) => {
	return val * 10;
}

const test = example( 5 );
console.log( test );
// 出力結果: 50
```

ただ、この場合、引数が一つなので、括弧を省略できるというルールがある。

```
example val => {
	return val * 10;
}

const test = example( 5 );
console.log( test );
// 出力結果: 50
```

これでも同じということね。文字数が減った！

で、複数になったら、元の形を拡張しよう。

```
example ( val1, val2 ) => {
	return val1 * val2;
}

const test = example( 7, 8 );
console.log( test );
// 出力結果: 56
```

この違いを理解できていたらとても幸せ！  
資料が見つかったときに意味がわかりそうだね。
