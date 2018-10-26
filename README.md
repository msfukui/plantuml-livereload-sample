# PlantUML Livereload Sample

## Description (What's this?)

PlantUML を Guard で Livereload する環境のサンプルです。

PlantUML を Vim で書く際に Livereload 機能が欲しかったので作りました。

変更して反映までのタイムラグはあるので、あんまり実用的ではないかも。

ちゃんとしたい場合は IntelliJ IDEA など使いましょう。

## Tested Environments

* Client
    * macOS Mojave
    * Google Chrome
    * LiveReload plugin (Google Chrome Extentions)
* Server
    * ruby 2.5.3
        * guard-livereload 2.5.2
        * guard-shell 0.7.1
    * Java openjdk 11
        * PlantUML 1.2018.12

## Usage

### Setup

事前に Google Chrome と Extentions の [LiveReload](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei) をインストールしておきます。

インストール後、「拡張機能を管理」から LiveReload のG「ファイルの URL へのアクセスを許可する」をオンにしておきます。（ローカルにあるファイルを file//.. で参照する場合に LiveReload を有効にするために必要です。）

本レポジトリを git clone した先のディレクトリで bundle install を実行してください。

```
$ bundle install --path=vendor/bundle
```

### Run

Guard を起動すると、

```
$ bundle exec guard
20:40:39 - INFO - LiveReload is waiting for a browser to connect.
20:40:39 - INFO - Guard is now watching at '/Users/msfukui/work/plantuml'
[1] guard(main)> 
```

.uml のファイルを監視して待ち受けます。

別ターミナルで PlantUML ファイルを拡張子 .uml でファイルを作成・更新すると、その度に Guard が PlantUML を実行して同じファイル名の .png と .html を作り直します。

Chrome で html を参照して、LiveReload のボタンを押すと、Guard に以下のログが出て、

```
20:41:54 - INFO - Browser connected.
```

LiveReload のボタンの中心の◯が●に変わります。（これが少々わかりにくいです..。）

.uml ファイルを更新する度に、Guard に以下のログが出て、

```
20:42:06 - INFO - Reloading browser: sample.html
```

Chrome の html が自動リロードされ、更新内容が反映されます。

## Notes

* 「ファイルの URL へのアクセスを許可する」の設定がされていないと、ローカルにあるファイルが LiveReload されなくて悩むことになるのでご注意ください。

* PlantUML が画像生成に失敗した場合のケアを何もしていないので変な結果になるかもしれません。

## License

本レポジトリのコードは PlantUML の jar ファイルを除いて [MIT License](http://opensource.org/licenses/MIT "MIT License") の元で配布します。

本レポジトリに含まれている PlantUML は GPL ライセンスのものです。

PlantUML の配布ライセンスは GPL ですが、他のライセンスのバージョンも利用できるそうです。(c.f. http://plantuml.com/faq)

## References URL

以下のサイトを参考にさせていただきました。ありがとうございます。

* [PlantUML](http://plantuml.com)

* [AsciiDoc を手軽にプレビューする方法(フェンリル|デベロッパーズプログ)](https://blog.fenrir-inc.com/jp/2017/03/asciidocpreview.html)

* [guard-livereloadを使う - Qiia](https://qiita.com/TAKAyuki_atkwsk/items/737066dd15b9886f5dad)

## Otherwise

PlantUML ってロゴとかシンボルマークとかないんですね。

![植物系統図の一例 - Wikipedia](https://ja.wikipedia.org/wiki/%E6%A4%8D%E7%89%A9#/media/File:Plant_phylogeny.png "植物系統図の一例")

公式ページ、怪しさMaxな感じで、もうちょっとなんとかできるといいなあって思いました。

[EOF]
