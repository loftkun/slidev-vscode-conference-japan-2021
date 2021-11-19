---
theme: seriph
title: VSCode + Markdownで発表スライドや書籍も書いちゃおう！
download: false
lineNumbers: true
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
---

# VSCode + Markdownで<br>発表スライドや書籍も書いちゃおう！

<br>

2021/11/20 VS Code Conference Japan 2021

@loftkun ( 甲斐 新悟 )

---

<h2>$ whoami</h2>

<div class="grid grid-cols-[30%,70%] gap-4"><div>

@loftkun ( 甲斐 新悟 )
<img src="/loftkun.jpg"/>

</div><div>

<br>

```markdown
- IT Specialist at IBM ( ex Yahoo! )
  - RHEL / OSS ( OpenShift, etc )
- IT lecturer at Kyushu University Lab
  - Python ( Anaconda )
- C / C++ / C# / Java / Go / PHP / Ruby / Python / Bash

- Staff of VSCodeConJP

- Presentation at
  - OpenShift.Run Winter 2020
  - プログラミング生放送勉強会 第61回
  - ふくばねてす (皆勤)
  - etc ( please see speakerdeck.com/loftkun )

- Piano ( YouTuber )、観る将＆指す将
```

</div></div>

<div class="grid grid-cols-[30%,70%] gap-4"><div>

<img src="/ex280.png"/>

</div><div>
Twitter : <img src="/qr_code.png" class="h-34 inline"/>
本資料 : <img src="/netlify.png" class="h-34 inline"/>

</div></div>

<!--
ネット上ではloftkunという名前で活動しています。
Twitterのフォローいただけると幸いです。
発表資料はこちらにUPしております。
仕事はIBMでLinux OSや各種OSSの検証やトラブルシューティングをしています
また、副業で大学で研究室向けにPythonの講義をしています
今回の発表はこのPythonの講義でMarkdownを使ってスライドとか書籍として講義資料を執筆していいる経験を元にお話したいと思っています。
今回のカンファレンスの実行委員をしております。各種勉強会などで発表もしています。
趣味は音楽ピアノや将棋を見たり指したりすることです。
-->

---

<h2>Agenda</h2>

<br>
<br>

<h3>1. MarkdownのHappy Extensions!</h3>

<br>

- VSCodeでMarkdownを書く際に便利な拡張機能を紹介します

<br>
<br>

<h3>2. Markdownでスライドを書く</h3>

<br>

- Slidevを活用して、Markdownでスライドを書く方法やテクニックを紹介します
- この発表スライドもMarkdownで書いてSlidevでスライド化したものになります

<br>
<br>

<h3>3. Markdownで書籍( epub, mobi )を書く</h3>

<br>

- Pandocを活用して、Markdownで書籍( epub, mobi )を書く方法やテクニックを紹介します

---
layout: cover
background: https://source.unsplash.com/collection/94734566/1920x1080
---

## 1. MarkdownのHappy Extensions!

---

### 1.1. Markdown Preview Enhanced ( [shd101wyy.markdown-preview-enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced) )

<br>

<div class="grid grid-cols-[60%,40%] gap-4"><div>

![](/ext/01.gif)

</div><div>

<br>

図や数式を表示できます

- mermaid
- PlantUML
- LaTeX

その他、ファイル形式の変換機能などもあります

VSCode標準のプレビュー機能よりも高機能なのでおすすめです

</div></div>

---

### 1.2. markdownlint ( [DavidAnson.vscode-markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) )

<br>

<div class="grid grid-cols-[60%,40%] gap-4"><div>

![](/ext/02.gif)

</div><div>

<br>
<br>

PROBLEMSパネルに文法の指摘が表示されます

- 不要なスペースの存在
- 空行がない
- 他いろいろ

修正することで綺麗なMarkdownを書けます

Markdownのお作法を知ることができるのでおすすめです

</div></div>

---

### 1.3. Auto Markdown TOC ( [xavierguarch.auto-markdown-toc](https://marketplace.visualstudio.com/items?itemName=xavierguarch.auto-markdown-toc) )

<br>

<div class="grid grid-cols-[60%,40%] gap-4"><div>

![](/ext/03.gif)

</div><div>

<br>
<br>

- 章番号を自動で振ってくれます
- 目次を自動生成してくれます
- 途中に章を挿入した場合も振り直せます
- 章番号や目次の手作業によるメンテが不要になります

手順書など章の構成が重要な資料を書く際に便利です

</div></div>

---

### 1.4. Table Formatter ( [shuworks.vscode-table-formatter](https://marketplace.visualstudio.com/items?itemName=shuworks.vscode-table-formatter) )

<br>

<div class="grid grid-cols-[60%,40%] gap-4"><div>

![](/ext/04.gif)

</div><div>

<br>
<br>

- セルの幅を見やすく調整してくれます
- 不足している - や | を保管してくれます

Formatterの支援があると表を楽に書くことができます

</div></div>

---

### 1.5. Draw.io Integration ( [hediet.vscode-drawio](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio) )

<br>

<div class="grid grid-cols-[60%,40%] gap-4"><div>

![](/ext/05.gif)

</div><div>

<br>
<br>

- オフラインで Draw.io ( app.diagrams.net ) の描画ツールが使えます
- 対応するファイル名は `*.drawio.svg` などいくつか規則があります
- Markdownには通常の画像として表示できます

構成図などを描く際に便利です

</div></div>

---
layout: cover
background: https://source.unsplash.com/collection/94734566/1920x1080
---

## 2. Markdownでスライドを書く

---

### 2.1. Markdownでスライドを書くには

<br>

- スライドの文章をMarkdownで書き、ツールでMarkdownをスライドとして表示させます
  - スライドとしてのデザインや機能はツールに依存します
  - Markdwon側でも多少のレイアウトの指定は可能です

<br>

- 発表の内容(文章)を書くことに専念し、短時間でまとまった量のアウトプットを出したい場合におすすめです
  - 私の場合、本業の合間に副業のPythonの講義資料を作るための目的に合っていました

<br>

- 様々なツールがありますが、今回は、Slidevを紹介したいと思います！
  - [reveal.js](https://revealjs.com/)
  - [Marp](https://marp.app/)
  - [Slidev](https://sli.dev/)

---

### 2.2. Slidevとは

Markdownでスライドを記述できるエンジニア向けプレゼンテーションツールです

<div class="grid grid-cols-[65%,35%] gap-4"><div>

![](/slidev/01.png)

</div><div>

<Tweet id="1423923567465439237"/>

</div></div>

---

### 2.3. Slidevの導入

<div class="grid grid-cols-[50%,50%] gap-4"><div>

```log
$ npm init slidev@latest

  ●■▲
  Slidev Creator  v0.27.15

✔ Project name: … demo
✔ Package name: … demo
  Scaffolding project in demo ...
  Done.

✔ Install and start it now? … yes
✔ Choose the agent › npm

  ●■▲
  Slidev  v0.27.15

  theme   @slidev/theme-seriph
  entry   /home/loft/slidev-demo/slides.md

  slide show      > http://localhost:3030/
  presenter mode  > http://localhost:3030/presenter
  remote control  > pass --remote to enable

  shortcuts       > restart | open | edit
```

</div><div>

- これだけでOK ( 要 `Node.js >=14.0` )
- ブラウザで閲覧できます( `localhost:3030` )
- あとは slides.md を執筆していくだけ！
- プレビューにも動的に反映されます

![](/slidev/01.png)

</div></div>


---

### 2.4. サンプルMarkdownとLive Demo

|                 |                                                                                |                               |
| :-------------: | :----------------------------------------------------------------------------- | :---------------------------- |
|    Markdown     | [github.com/loftkun/slidev-example](https://github.com/loftkun/slidev-example) | slides.md をご参照ください    |
| Live Demo (SPA) | [loftkun-slidev-example.netlify](https://loftkun-slidev-example.netlify.app)   | Netlify にデプロイしたSPAです |

<div class="grid grid-cols-[55%,35%] gap-15"><div>

![](/slidev/02.png)

</div><div>

<Tweet id="1423923567465439237"/>

</div></div>

---

### 2.5. おすすめポイント1: レイアウトが柔軟

Gridレイアウトによりコンテンツを柔軟に配置できます

<br>
<center>ここは横幅いっぱい使えるよ</center>
<br>
<br>
<br>

<div class="grid grid-cols-[33%,33%,33%] gap-4"><div>

<center>左グリッド</center>
<br>
<br>

</div><div>

<center>中央グリッド</center>

</div><div>

<center>右グリッド</center>

</div></div>

<br>
<center>ここは横幅いっぱい使えるよ</center>
<br>

```html
ここは横幅いっぱい使えるよ
<div class="grid grid-cols-[33%,33%,33%] gap-4"><div>
左グリッド
</div><div>
中央グリッド
</div><div>
右グリッド
</div></div>
ここは横幅いっぱい使えるよ
```

---

### 2.6. おすすめポイント2: コードブロックのシンタックスハイライトと行番号表示ができる

ソースコードやコマンドの実行結果などのコードブロックを綺麗に表示できます

Pythonソースコードの表示例 : 

<div class="grid grid-cols-[50%,50%] gap-4"><div>
before

```python {4-}
import os
test_path = os.path.join("data", "data-01.txt")

f = open(test_path, "a", encoding="utf-8")
f.write("this is new append line\n")
f.close()
```

</div><div>
after

```python {4-}
import os
test_path = os.path.join("data", "data-01.txt")

with open(test_path, "a", encoding="utf-8") as f:
    f.write("this is new append line\n")
```

</div></div>

特徴

- 行番号の表示ができるため、行番号での意思疎通できて便利です
- 着目して欲しい行を強調できます ( 上記の例では 4行目以降 )
- 画像ではなくテキストなので、文字列のコピーや検索も可能です
- 上記のように、Gridレイアウトを使うことで左右で比較、のような表現も可能です

---

### 2.7. おすすめポイント3: 拡張機能もあります ( [antfu.slidev](https://marketplace.visualstudio.com/items?itemName=antfu.slidev) )

<br>

<div class="grid grid-cols-[60%,40%] gap-4"><div>

![](/slidev/03.gif)

</div><div>

<br>

- プレビュー表示ができる
  - Markdownの編集が即反映されます
- スライドのタイトル一覧表示、ジャンプができる
  - 順序の変更ができます

</div></div>

---
layout: cover
background: https://source.unsplash.com/collection/94734566/1920x1080
---

## 3. Markdownで書籍( epub, mobi )を書く

---

### 3.1. Markdownで書籍( epub, mobi )を書くには

- 書籍の文章をMarkdownで書き、ツールでMarkdownを電子書籍のフォーマットに変換します
  - 画像の挿入や表もMarkdown記法で書くことができます

- 私はPandocというツールを使用しています
  - 様々なドキュメントのフォーマット変換ができるコンバーターです

- PandocでMarkdownから変換できるフォーマットの例 :
  - html
  - pdf
  - pptx
  - epub
  - などなど、様々なフォーマットに対応しています
    - 詳細は [pandoc.org](https://pandoc.org/) をご参照ください

---

### 3.2. サンプル

<style>
.language-bash span.line { /* bashのコード */
  margin-left: -40px; /* 左に40px移動して行番号を隠す(邪道) */
}
</style>

|                                                                                      |                 |                  |
| :----------------------------------------------------------------------------------- | :-------------- | ---------------- |
| [github.com/loftkun/markdown-to-ebook](https://github.com/loftkun/markdown-to-ebook) | book.md         | Markdownファイル |
|                                                                                      | ebook/book.epub | epubファイル     |

Markdownからepubに変換するコマンドの例 : 

```bash
$ pandoc --from markdown --to epub3 book.md --output book.epub --toc --epub-cover-image=img/cover.png
```

|                  |                        |
| ---------------- | ---------------------- |
| from             | 変換元のフォーマット   |
| to               | 変換先のフォーマット   |
| output           | 出力ファイルのパス     |
| toc              | 目次出力を有効化       |
| epub-cover-image | 表紙画像ファイルのパス |

---

### 3.3. Kindleでも読めます

[Kindle Previewer](https://kdp.amazon.co.jp/ja_JP/help/topic/G202131170) を使うとepubをmobi形式に変換でき、Kindleでも閲覧できます

<div class="grid grid-cols-[60%,40%] gap-10"><div>

![](/epub/03.gif)

- epub 閲覧やmobiへの変換が可能
- mobiはKindleで閲覧できます

</div><div>

Kindle Paperwhite で表示した例

<img src="/epub/02.jpg" class="h-80">

</div></div>

---

## 4. まとめ

<br>

<h3>MarkdownのHappy Extensions!</h3>

<br>

- VSCodeと拡張機能を活用することでMarkdownを効率よく書くことができます

<br>

<h3>Markdownでスライドや書籍( epub, mobi )を書く</h3>

<br>

- SlidevやPandocなどの外部ツールも組み合わせることで、Markdownの活用範囲が広がります

<br>
<br>

<h3>今回の発表が、VSCodeでMarkdownを書き、<br>Markdownを活用する際のご参考となりましたら幸いです！</h3>

---
layout: cover
background: https://source.unsplash.com/collection/94734566/1920x1080
---

<h1>ご視聴ありがとうございました！</h1>
