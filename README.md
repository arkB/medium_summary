# 動機

Medium.com のブログ記事を [summpy(自分でPython3対応させたもの)](https://github.com/arkB/summpy) を用いて要約させてみたいと考えました。

（もともとは [内田樹のブログ記事](http://blog.tatsuru.com/) を要約したいという動機でしたが、著作権的にNGっぽかったので、自分で Medium.com に寄稿したブログ記事を要約する形で公表することにしました）

## 環境

* [summpy(自分でPython3対応させたもの)](https://github.com/arkB/summpy) インストール済み
* Jupyter Notebook環境で実行させます
* Python 3.6
* **日本語オンリー (Japanese Only) です**

## 使い方

### 1. 要約させたい Medium の（日本語の）記事を探す

[Medium.com](https://medium.com/) から要約させたい日本語の記事を探してきます。

今回は 私自身が寄稿した [「猫カフェはどこへ消えた」](https://medium.com/@arkbb3/%E7%8C%AB%E3%82%AB%E3%83%95%E3%82%A7%E3%81%AF%E3%81%A9%E3%81%93%E3%81%B8%E6%B6%88%E3%81%88%E3%81%9F-9486c89a432e) という記事を5センテンスに要約させてみます。

### 2. Jupyter Notebook 起動

ローカルで Jupyter Notebook を起動し、[medium_summary.ipynb](https://github.com/arkB/medium_summary/blob/master/medium_summary.ipynb) をダウンロードして開きます。

requests.get() の引数に要約させたい Meadium の記事のURLを入力します（下記例）。

```
r = requests.get("https://medium.com/@arkbb3/%E7%8C%AB%E3%82%AB%E3%83%95%E3%82%A7%E3%81%AF%E3%81%A9%E3%81%93%E3%81%B8%E6%B6%88%E3%81%88%E3%81%9F-9486c89a432e")
```

要約するセンテンス数を変更したい場合は `sent_limit=`の右辺の値を変更することで可能です（下記では5文章で要約する設定）。

```
sentences, debug_info = summarize(text_new, sent_limit=5, continuous=True, debug=True)
```

### 3. Jupyter Notebook 実行

Shift+Enter等で適宜実行すると、要約された文章が表示されます（下記要約例）。

```
猫カフェと私じぶんは猫カフェというところに行ったことがない。
経験がないのでその手の話題への感度が低くて、いまいちピンと来ないことが多く、猫カフェに行こうと思ったことがない。
語り得ぬことには沈黙は金（？）猫カフェBot爆誕そんなこんなで来年は猫カフェに一度行ってみたいと考えている。
提案してくれたのは猫のいる休憩所299という猫カフェで地図で確かめると池袋駅から行った方が近かったりする（笑）猫カフェBotの仕組みあらBotの中でやってることは簡単でGoogle Places APIというGoogle Map にあるお店情報を取得できるAPIでタイプに“Cafe”、キーワードに「猫カフェ」として半径1000m指定で検索しているだけである。
（そんな場所に猫カフェなど高尚な施設はなかったのだ？）来年こそはこれで気が向いたときに好きな場所でそこそこ良さそうな猫カフェを手軽に探すことはできそうなので、来年一度行ってみたいと思う。
```

## コメント

* そこそこ要約できてる印象
* 他のサイトで利用したい場合は下記の `class_=` の右辺を適宜変更すればいける場合もあります（もともとやりたかった内田樹ブログは'entry-body'にすればいけました）。

```
for t in soup.findAll(class_='section-inner sectionLayout--insetColumn'):
```
