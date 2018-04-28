---
description: 今度は自分でおみくじをしてくれる物を作ってみよう。
---

# おみくじプログラムの要件

    - ボタンを押すとおみくじが引かれる
    - 結果として「大吉」「中吉」「吉」「凶」「大凶」がある
    - それぞれの結果に合わせて、一文を表示させる（内容は任意）
    - 結果が表示されるまでに少し待ちがある（「おみくじの結果は...」等と表示させたい）
    - もう一回引くためにはリセットボタンを押さないといけない

## いけたらやりたいこと

    - おみくじの画像を利用したりしたい
    - 凶と大凶だったら、「結ぶ」という動作（ボタン操作）でもう一回引ける
    - 音も出せるかな？

# サンプルコード

## HTML

```
<!doctype html>
<html>
<head>
	<title>おみくじ</title>
	<script src="omikuji.js"></script>
</head>
<body>
	<input type="button" value="おみくじを引く！" onclick="omikuji();" id="playBtn">

	<div>
		<div id="msgHeading" style="opacity: 0;">おみくじの結果は...</div>
		<div id="msg1"></div>
		<div id="msg2"></div>
	</div>

	<input type="button" value="リセット！" id="resetBtn" onclick="reset();" disabled="disabled">
</body>
</html>
```

## JavaScript (omikuji.js)

```
function omikuji() {
	let msg1;
	let msg2;
	let random1;
	let random2;

	random1 = Math.floor(Math.random() * 5);
	console.log(random1);

	const result = ['大吉', '中吉', '吉', '凶', '大凶'];

	msg1 = result[random1];

	random2 = Math.floor(Math.random() * 10);
	console.log(random2);

	const resultMsg = [
		'新タマネギを食べるとおいしいでしょう。',
		'ポテチを食べましょう。',
		'バックアップを取っておきましょう。',
		'忘れ物をしないように気をつけて。',
		'怪我するでしょう。',
		'結婚するでしょう。',
		'お金を無くすでしょう。',
		'電車が遅延するでしょう。',
		'ﾜｯｼｮｲヽ(ﾟ∀ﾟ)メ(ﾟ∀ﾟ)メ(ﾟ∀ﾟ)ノﾜｯｼｮｲ',
		'スタバの新作を飲みましょう。',
	];

	msg2 = resultMsg[random2];

	document.getElementById('msgHeading').setAttribute('style', 'opacity: 1;');
	setTimeout(function() {
		document.getElementById('msg1').innerHTML = msg1;
	}, 1000);
	setTimeout(function() {
		document.getElementById('msg2').innerHTML = msg2;
	}, 2000);
	document.getElementById('playBtn').setAttribute('disabled', 'disabled');
	document.getElementById('resetBtn').removeAttribute('disabled');
}

function reset() {
	document.getElementById('msgHeading').setAttribute('style', 'opacity: 0;');
	document.getElementById('msg1').innerHTML = '';
	document.getElementById('msg2').innerHTML = '';
	document.getElementById('playBtn').removeAttribute('disabled');
	document.getElementById('resetBtn').setAttribute('disabled', 'disabled');
}
```
