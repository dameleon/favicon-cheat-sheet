ファビコン・カンニング・ペーパー
================================

ファビコンのサイズや形式についての読むと頭が痛くなる偏執的なカンニング・ペーパーです。以下のURLを参考にしました:

  * http://mathiasbynens.be/notes/rel-shortcut-icon <-- special thanks [@mathiasbynens][1]
  * http://mathiasbynens.be/notes/touch-icons <-- special thanks [@mathiasbynens][1]
  * http://www.jonathantneal.com/blog/understand-the-favicon/
  * https://en.wikipedia.org/wiki/Favicon.ico
  * http://snook.ca/archives/design/making\_a\_good\_favicon
  * http://www.netmagazine.com/features/create-perfect-favicon
  * http://www.ravelrumba.com/blog/android-apple-touch-icon/
  * http://msdn.microsoft.com/en-us/library/ie/gg491740(v=vs.85).aspx


HTMLでのマークアップ
--------------------

### 基本

メインになるファビコンについては各ブラウザーでの互換性を考慮して[HTMLでは特に指定しないのが望ましい][2]です。単に`favicon.ico`という名前でドメインのルートに配置するだけで構いません。

こうするとIE6も含め全てのデスクトップ向けブラウザーのすべてのバージョン(SeaMonkey以外)でうまくいきます。


### 推奨

以下のコードは指定しておくと良いかもしれません:

  1. iOS 2.0以降とAndroid 2.1以降向けのタッチ・アイコン:

     ```html
     <link rel="apple-touch-icon-precomposed" href="path/to/favicon-152.png">
     ```

  2. IE10のMetroタイル・アイコン(Metroにおけるタッチ・アイコンのようなもの):

     ```html
     <meta name="msapplication-TileColor" content="#FFFFFF">
     <meta name="msapplication-TileImage" content="/path/to/favicon-144.png">
     ```

     あなたの好きな色で`#FFFFFF`は置き換えましょう。


### 任意(偏執的な方だけどうぞ)

ありとあらゆるものをカバーしたいのならば以下のようにすることになります:

  1. [Appleのデバイス向けタッチ・アイコン][4]の全サイズ:

     ```html
     <!-- For iPad with high-resolution Retina display running iOS ≥ 7: -->
     <link rel="apple-touch-icon-precomposed" sizes="152x152" href="/path/to/favicon-152.png">

     <!-- For iPad with high-resolution Retina display running iOS ≤ 6: -->
     <link rel="apple-touch-icon-precomposed" sizes="144x144" href="/path/to/favicon-144.png">

     <!-- For iPhone with high-resolution Retina display running iOS ≥ 7: -->
     <link rel="apple-touch-icon-precomposed" sizes="120x120" href="/path/to/favicon-120.png">

     <!-- For iPhone with high-resolution Retina display running iOS ≤ 6: -->
     <link rel="apple-touch-icon-precomposed" sizes="114x114" href="/path/to/favicon-114.png">

     <!-- For first- and second-generation iPad: -->
     <link rel="apple-touch-icon-precomposed" sizes="72x72" href="/path/to/favicon-72.png">

     <!-- For non-Retina iPhone, iPod Touch, and Android 2.1+ devices: -->
     <link rel="apple-touch-icon-precomposed" href="/path/to/favicon-57.png">
     ```

  2. 上記でカバーできないサイズ:

     ```html
     <link rel="icon" href="/path/to/favicon-32.png" sizes="32x32">
     ```

     *訳注:* `sizes`属性を使ってサイズを教えてやるということです。


画像の作成
----------

最低でも以下のものは作りましょう:

|サイズ       |ファイル名 |目的                                                                                     |
|-------------|-----------|-----------------------------------------------------------------------------------------|
|16x16 & 32x32|favicon.ico|IEがデフォルトで必要とします。残念ながらChromeとSafariはpngよりicoを優先してしまいます。|

`favicon.ico`について詳しくは後述しますが、ひとつのファイルで複数のサイズをまかなえます。

iOSやAndroidへ簡単に対応したい場合は以下のサイズで作成します:

|サイズ |ファイル名     |目的                                                  |
|-------|---------------|------------------------------------------------------|
|152x152|favicon-152.png|iOSやAndroidで使われ、デバイス側で適切に縮小されます。|

しかしながら複雑なアイコンの場合、デバイス側の縮小がきれいに行われないことがあることは頭に入れておいた方が良いでしょう。きれいに縮小されるように細かい修正を行う必要があるかもしれません。

偏執狂のあなたは以下のサイズも作りましょう:

|サイズ |ファイル名     |目的                                                                         |
|-------|---------------|-----------------------------------------------------------------------------|
|32x32  |favicon-32.png |特定の古いかといって古過ぎもしないChromeがicoを適切に扱わないバグへの対応    |
|57x57  |favicon-57.png |非RetinaであるiOSのホーム・スクリーン(iPod TouchやiPhoneの第一世代から3Gまで)|
|72x72  |favicon-72.png |iPadのホーム・スクリーン                                                     |
|96x96  |favicon-96.png |GoogleTVのアイコン                                                           |
|120x120|favicon-120.png|Retina iPhoneのタッチ・アイコン(iOS 7で114x114から変更)                      |
|128x128|favicon-128.png|Chrome ウェブストアのアイコン                                                |
|144x144|favicon-144.png|IE10のピン留めされたサイト向けタイル・アイコン                               |
|152x152|favicon-152.png|Retina iPadのタッチ・アイコン (iOS 7で144x144から変更)                       |
|195x195|favicon-195.png|Operaのスピード・ダイヤル・アイコン                                          |


ICOファイル
-----------

`ico`ファイルはサイズの違う`.bmp`や`.png`のアイコンを複数まとめることができるフォーマットです。`favicon.ico`では以下のサイズを最低限作成しておけばよいでしょう:

|サイズ|目的                                                                                    |
|------|----------------------------------------------------------------------------------------|
|16x16 |IE9のアドレス・バーやピン留めされたサイト、ジャンプ・リスト、ツールバー、オーバーレイ   |
|32x32 |IEの新しいタブやWidows 7以降のタスクバー・ボタン、Safariのリーディングリスト・サイドバー|
|48x48 |Windowsサイト・アイコン                                                                 |

偏執狂のあなたは1–3KBのファイルサイズの増加を気にしないのなら、以下のサイズも`favicon.ico`に含めると良いでしょう:

|サイズ|目的                                                                               |
|------|-----------------------------------------------------------------------------------|
|24x24 |IE9のピン留めされたサイトでブラウザーウィンドウに表示されるアイコン                |
|64x64 |高解像度デバイスでのWindowsサイト・アイコンやSafariのリーディングリスト・サイドバー|

まずきっちりと`.png`を作り、それを元にして`.ico`を作成しましょう。

*TODO:* IE9以降で`.png`を`.ico`に含められることについての確認([Issue #9][5])


お役立ちツール
--------------

オススメなのは以下の2つです:

  1. [OptiPNG][6]: `.ico`にまとめる前に`.png`を最適化
  2. [ImageMagick][7]: [複数の`.png`ファイルをまとめて`.ico`に変換][8]

試したわけではありませんが、以下のツールも役に立つでしょう:

  * Ubuntu/Debianのパッケージである`icoutil`は`.png`から`.ico`を作成するツールが含まれています。
  * MSDNは[web-based .ico creator][9]の利用を推奨しています
  * リサイズには[Faviconer][10]が良いでしょう。
  * [icon][11]もリサイズに向いたツールです。
  * JavaScriptを利用して動的にファビコンを変更する[favicon-setter][12]というツールもあります。
  * ファイル・アップロードのプログレス表示などをファビコンで行える[piecon][13]というツールも面白いでしょう。
  * [Web Icon][14]は12種類のサイズのファビコンを一気に作成してくれるシェルスクリプトです。
  * [Icon Slate app][15] (OS X)
  * [png2ico wrapper for ImageMagick][16]


ファビコンの強制的な再読み込み
------------------------------

通常は必要ありません。開発中にうまくファビコンが再読み込みされずイライラする時だけ試してみましょう:

  * ブラウザーのキャッシュをクリアする(Ctrl+F5またはCtrl+Shift+R)
  * IEの場合はブラウザーを再起動する
  * それでもダメな場合は新しいタブを開くか、[複雑な手順][17]をこなす
  * 一時的にマークアップを変更してクエリ文字列を追加する。必ず後で削除しましょう:

    ```html
    <link rel="shortcut icon" href="http://www.yoursite.com/favicon.ico?v=2">
    <link rel="icon" sizes="16x16 32x32" href="/favicon.ico?v=2">
    ```

大きな変更を加えたバージョンの公開時には全ての訪問者のファビコンを強制的に再読み込みさせたいこともあるでしょう:

  * 以下のようなマークアップ(`sizes`属性の変更を忘れずに)を加えて、バージョン番号をファイル名に入れるようにしましょう:

    ```html
    <link rel="shortcut icon" href="/favicon-v2.ico">
    <link rel="icon" sizes="16x16 32x32" href="/favicon-v2.ico">
    ```

    *TODO:* このマークアップがうまくいかないケースのさらなる調査([Issue #3][18]).


よくある質問
------------

### `favicon.ico`と`favicon.png`の両方がルートにあるとどうなりますか？

`favicon.ico`のみを設置し、`favicon.png`は置かない方が良いと思います。その理由は:

  * `.ico`形式は複数の`.bmp`や`.png`のためのコンテナー・フォーマットです。`favicon.png`を1つ定義し、`favicon.ico`の代わりに`favicon.png`を使うようにすると、ブラウザーのリサイズ機能にすべて任せることになり、ファビコンが違う解像度でどのように表示されるかコントロールできなくなります。例えば64x64のアイコンでは文字を表示したいが、16x16のアイコンでは読めなくなるであろうことから文字は表示したくないというようなケースにも対応できます。
  * HTML5仕様には`favicon.ico`については出てきますが、`favicon.png`については出てきません。[現在のHTML仕様によると][3]:
    > 'In the absence of a link with the icon keyword, for Documents obtained over HTTP or HTTPS, user agents may instead attempt to fetch and use an icon with the absolute URL obtained by resolving the URL "/favicon.ico" against the document's address, as if the page had declared that icon using the icon keyword.'

このことについて詳しくは[似たような質問に対してのStackOverflowでの答え][19]を参照すると良いでしょう(注: アルファ・チャンネルという点での優位性を説明した答えは間違っているので、2つ目の答えを読んでください)。


### ファビコンはルートに置くべきというのは本当ですか？

いいえ、それはブラウザーやデバイスごとにファビコンのパスを指定した`<link>`タグを明示的に書かなかった場合に限った話です。Wikipediaの[Favicon.ico記事][20]も参照してください。

もし`favicon.ico`をルートに置いていないなら、置くかHTTPステータス・コードで`204`を返すようにしましょう。多くのツールやサービス(ブックマークやフィード・リーダー、検索エンジンのクローラーなど)がルートに`favicon.ico`があるとしてリクエストしてきますが、もし無いとHTTPステータス・コードとして`404`を受け取ることになります。最悪の場合、ファビコンよりも何倍もサイズの大きいカスタム・エラー・ページを返す羽目になるかもしれません。


### PNGの場合は`favicon.ico`という名前にする必要があるというのは本当ですか？

いいえ、私が偏執的に調べたところによるとそういった事実はまったくありません。


### ICOの場合は`favicon.ico`という名前にする必要があるというのは本当ですか？

もし明示的に`<link>`タグを書かないのならばその通りです。明示的に書くのが一番確実なので、`favicon.ico`という名前にして明示的に`<link>`タグを書くようにしています。


### なぜ"apple-touch-icon"を頭に付けないのですか？

`<link>`タグを書かない場合、iOSは勝手に`apple-touch-icon`か`apple-touch-icon-precomposed`が頭についたファイルを探します。HTML5 Boilerplateなど多くがこの挙動に依存しています。しかし:

  * 明示的に`<link>`タグを書く方がよりわかりやすく、Appleがサポートしている形です。
  * ファイル名を`apple-touch-icon`のように決め打ちしないことにより、同じサイズのアイコンの再利用性が高まります。例えば`favicon-144.png`をWindowsのピン留めされたサイトに再利用する場合など。


### なぜiOS向けにprecomposedアイコンを指定するのですか？

  * iOSは編集済みでないアイコンに角丸と影、反射の特殊効果を付け加えます。一見それで良さそうですが、実際にはそううまくいかず、特にデザイナーには納得の行くような結果にはなりません。
  * 編集済みでないアイコンにAndroid 2.1は対応していません。


### なぜ絶対パスを使うのですか？

Firefoxの古いバージョンで絶対パスである必要があります。また絶対パスならば全てのブラウザーでサポートされているので、最も無難な選択でしょう。


### なぜクエリ文字列を追加して全ての訪問者に強制的に再読み込みさせないのですか？

いくつかのプロクシーやロード・バランサーでクエリ文字列の解釈に失敗するケースが確認されています。


是非、寄稿を！
--------------

もし他の文書の引用や根拠の提示のために追加や変更を加えたい場合はプル・リクエストを送ってください。この文書が充実させてくれることを楽しみにしています！


[1]:  https://github.com/mathiasbynens
[2]:  http://mathiasbynens.be/notes/rel-shortcut-icon
[3]:  http://www.w3.org/html/wg/drafts/html/CR/links.html#rel-icon
[4]:  http://mathiasbynens.be/notes/touch-icons
[5]:  https://github.com/audreyr/favicon-cheat-sheet/issues/9
[6]:  http://optipng.sourceforge.net/
[7]:  http://www.imagemagick.org/Usage/thumbnails/#favicon
[8]:  http://blog.morzproject.com/convert-multiple-png-images-into-a-single-icon-file/
[9]:  http://www.xiconeditor.com
[10]: http://faviconer.com
[11]: https://github.com/abrkn/icon
[12]: https://github.com/HenrikJoreteg/favicon-setter
[13]: https://github.com/component/piecon
[14]: https://github.com/emarref/webicon
[15]: https://itunes.apple.com/us/app/icon-slate/id439697913
[16]: https://github.com/bebraw/png2ico
[17]: http://stackoverflow.com/questions/2208933/how-do-i-force-a-favicon-refresh/5239747#5239747
[18]: https://github.com/audreyr/favicon-cheat-sheet/issues/3
[19]: http://stackoverflow.com/questions/1344122/favicon-png-vs-favicon-ico-why-should-i-use-pngs-instead-of-icos/1344379#1344379
[20]: https://en.wikipedia.org/wiki/Favicon.ico
