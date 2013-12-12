#【jQuery】スクロールすると現れるページトップへボタンの設置方法

ある程度ページをスクロールすると、ふわっと出現する「上へ」ボタンを作成する方法です。
ボタンを押すと上までするーっとスクロールします。

## デモ

<a href="http://klutche.github.io/pageTop/" target="_blank" class="link">デモページ</a>

上椎葉ダムの奈落から天端に戻る事ができます。

## HTML


`<a href="#top" class="page_top">PAGE TOP ▲</a>`


今回はページ最上部まで戻すので body に id="top" を設定してあります。
ボタンには class="page_top" を設定します。

### Javascript

jQuery 依存のスクリプトなので、まず jQuery を読み込んでおきます。


`<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>`


その下に Javascript の処理を記載します。

	<script type="text/javascript">
	$(function() {
		var pageTop = $('.page_top');
		pageTop.hide();
		$(window).scroll(function () {
			if ($(this).scrollTop() > 600) {
				pageTop.fadeIn();
			} else {
				pageTop.fadeOut();
			}
		});
	    pageTop.click(function () {
			$('body, html').animate({scrollTop:0}, 500, 'swing');
			return false;
	    });
	});
	</script>

「600」の部分が表示の条件となるスクロール量です。
上から600px分スクロールしたらボタンを表示します。

「500」がスクロール速度です。
数字が小さいほどシャッと動きます。

## CSS

	.page_top {
		position:fixed;
		bottom:10px;
		right:10px;
		padding:10px 20px;
		color:#fff;
		font-size:20px;
		text-decoration:none;
		background:#000;
	}
	.page_top:hover {
		background:#e74c3c;
	}

position:fixed; で画面下部に固定します。
あとの見た目はお好みで･･･

### サンプルファイル一式

<a href="https://github.com/klutche/pageTop" target="_blank" class="link">https://github.com/klutche/pageTop</a>
