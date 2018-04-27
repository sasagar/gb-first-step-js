---
description: さて、主に登場するシーンはDOM操作。という事で、DOM操作で使う記述を見ていこう。
---

# DOM 操作をする

HTML の要素を操ったり、属性を操ったり。  
スタイルを変更したりするのが、DOM 操作。

まずは対象を絞り込むところから。

## セレクタを使って対象を定める

jQuery だとシンプルに書けたりするんだけど、今回は敢えて純粋な JavaScript でやっていこう。  
いわゆるセレクタで絞り込むのは jQuery と一緒。

```
document.getElementById("ID名") // id属性で絞り込む
document.getElementsByClassName("class名") // class属性で絞り込む
document.getElementsByName("name名") // name属性で絞り込む
```

この辺が利用可能。  
他にもあるけど滅多に使わないと思うので、省略。

JavaScript のスタンダードは **キャメルケース** という命名規則。キャメルケースはらくだのこぶのように、単語の頭文字だけを大文字にしてくっつけることで、1word とする書き方。最初だけは小文字。

そして、Elements は要素という意味なので、id の時は一意に定まる事から Element と記述される。  
ClassName はちょっとややこしいかも知れないけど、プログラム用語で Class があるため混乱しないように ClassName となっている。

こうやったら憶えられそうじゃない？

## 要素の中の文字を変更する

一番シンプルな DOM 操作。要素の文字列を変更するときどうするか...。

`innerHTML` と言うのが登場する。

```
document.getElementById("change").innerHTML = "変更した文字列";
// idがchangeの要素の中身を"変更した文字列"にする
```

こんな感じで、変数に代入するように書ける。対象の要素を決めて、要素の何に対して処理をするのか決めて、代入。簡単でしょ？

## 要素の属性を変更する

次にやることの多そうなのが、属性の変更。  
`img` タグの `src` 属性だけ変えたいとか、そういうとき。

`setAttribute` と言うのが登場する。これは書き方がちょっと変わってくる。

```
let element = document.getElementById("change");
element.setAttribute("src", "./images/changed.png");
// idがchangeの要素のsrc属性を"./images/changed.png"にする
```

このやり方を使えばタグの諸々もいじれるから何でもできそうだね！

## クラス名の変更と追加

### 変更

このほかに登場しそうなのが、クラス名の変更や追加。  
まずは変更を考えてみよう。

```
let element = document.getElementById("change");
element.setAttribute.className = "class1 class2";
// idがchangeの要素のclassを"class1"と"class2"にする
```

さっき登場した代入の仕方と一緒。簡単！

では続いて、追加。

### 追加

```
let element = document.getElementById("change");
element.classList.add("class1", "class2");
// idがchangeの要素のclassに"class1"と"class2"を追加する
```

複数ならカンマ区切り、そうじゃ無ければ一つだけ書けばオッケー。  
要素のクラスのリストに対して、追加という命令をしている感じだね。

### 削除

削除したいこともあるかもしれない。

```
let element = document.getElementById("change");
element.classList.remove("class1");
// idがchangeの要素のclassから"class1"を削除する（元々無ければ何もしない）
```

追加と同じ流れだね。これも簡単じゃないかな。  
コチラも複数ならカンマ区切りで書いてあげればオッケー。

### 切り替え

このクラス名があったら消す、無かったら付けるって言うこともあると思う。こういうのを「トグル」というんだけど、まさにトグルさせよう。

```
let element = document.getElementById("change");
element.classList.toggle("class1");
// idがchangeの要素のclassに"class1"が有れば削除、無ければ追加する
```

これで切り替えができる。ハンバーガーメニューとかはこれで作れそうだね。  
トグルについては、複数同時指定ができないので気をつけて。
