---
description: まずはみんなでじゃんけんするプログラムを作ってみよう。
---

# じゃんけんするプログラムの要件

    - 自分がグー・チョキ・パーのいずれかのボタンを押すとじゃんけんができる
    - プログラム側ではランダムにいずれかを選んで、一つ手を決める
    - 最終的に比べた結果で勝敗を判断する
    - また、ボタンを押せば次のじゃんけんができる

## いけたらやりたいこと

    - 自分が出した手と相手の出した手を画像で表示させてみたい
    - 押した後、「じゃん」「けん」「ぽん」の表示をして、その後で結果が表示される
    - 勝敗表を出せる
    	- まずは何回勝ってるかわかればオッケー
    	- 更に余裕があれば、一回毎の勝敗を出したい

# シンプルな回答例

## HTML

```
<!doctype html>
<html>
<head>
	<title>じゃんけんアプリ</title>
	<script src="./script.js"></script>
</head>
<body>
	<input type="button" value="グー" onclick="rsp(0);">
	<input type="button" value="チョキ" onclick="rsp(1);">
	<input type="button" value="パー" onclick="rsp(2);">

	<div>
		<div id="player"></div>
		<div id="computer"></div>
		<div id="resultMsg"></div>
	</div>

</body>
</html>
```

## JavaScript (script.js)

```
/*
 * じゃんけんの手
 * 0: グー
 * 1: チョキ
 * 2: パー
 * として処理する
 */
function rsp(playerSelect) {
	let result;
	let playerSelectHand;
	let comSelectHand;
	let resultString;
	let random = Math.random();
	let comSelect = Math.floor(random * 3);
	console.log(comSelect);
	console.log(playerSelect);

	/*
	 * 勝ち負けは（プレイヤーが）
	 * 0: 負け
	 * 1: 勝ち
	 * 2: あいこ
	 */

	if (playerSelect == comSelect) {
		// 一緒だったらあいこ
		result = 2;
	} else {
		// 違うので条件によって勝敗を振り分ける
		if (playerSelect == 0) {
			// プレイヤーはグー
			if (comSelect == 1) {
				// コンピューターはチョキ
				result = 1;
			} else {
				// コンピューターはパー
				result = 0;
			}
		} else if (playerSelect == 1) {
			// プレイヤーはチョキ
			if (comSelect == 0) {
				// コンピューターはグー
				result = 0;
			} else {
				// コンピューターはパー
				result = 1;
			}
		} else {
			// プレイヤーはパー
			if (comSelect == 0) {
				// コンピューターはグー
				result = 1;
			} else {
				// コンピューターはチョキ
				result = 0;
			}
		}
	}
	console.log(result);

	if (playerSelect == 0) {
		playerSelectHand = 'グー';
	} else if (playerSelect == 1) {
		playerSelectHand = 'チョキ';
	} else {
		playerSelectHand = 'パー';
	}

	if (comSelect == 0) {
		comSelectHand = 'グー';
	} else if (comSelect == 1) {
		comSelectHand = 'チョキ';
	} else {
		comSelectHand = 'パー';
	}

	if (result == 0) {
		resultString = '負け';
	} else if (result == 1) {
		resultString = '勝ち';
	} else {
		resultString = 'あいこ';
	}

	document.getElementById('player').innerHTML = 'あなたは ' + playerSelectHand;
	document.getElementById('computer').innerHTML =
		'コンピューターは ' + comSelectHand;
	document.getElementById('resultMsg').innerHTML = '結果は ' + resultString;
}
```
