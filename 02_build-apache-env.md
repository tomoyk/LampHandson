# 02.Apache HTTP Serverの構築

## 概要

前回、Linuxをインストールした仮想マシンを作成しました。
今回はそのLinux環境へApache HTTP Serverとよばれるソフトウェアをインストールして、Webページを公開することを目標とします。
また、HTMLやCSSを使った静的なWebページの簡単な作り方を学びます。

## 手順

### [1] システムのアップデート

システムのアップデートを行います。

```shell
$ sudo apt update
$ sudo apt upgrade
```

#### パッケージマネージャについて

Ubuntuには様々なソフトウェアがパッケージによってインストールされています。例えばWebブラウザを使いたい場合、Firefoxのパッケージをインストールします。
パッケージによってソフトウェアを導入することで、ソースコードからビルドを行う場合に比べてバージョン管理やアンインストールを容易に行えます。

今回はUbuntuに導入されているパッケージ管理コマンド apt を利用してパッケージの操作を行います。

### [2] Apache HTTP Serverのインストール

Webサーバを構築します。今回はサーバーソフトウェアとしてApache HTTP Serverを利用します。Apache HTTP ServerはApacheが提供するWebサーバーソフトウェアの1つです。

```shell
$ sudo apt install apache2
```

### [3] Apache HTTP Serverの起動・停止・再起動

起動:

```shell
$ sudo systemctl start httpd
```

停止:

```shell
$ sudo systemctl stop httpd
```

再起動:

```shell
$ sudo systemctl restart httpd
```

#### ポートについて

コンピュータがネットワークで接続された他のコンピュータとやり取りを行うには、データ（パケット）の出入りが必要です。この出入り口はポートと呼ばれます。

ポートには0〜65535の範囲で番号が割り当てられています。一般にHTTPでは80番(TCP), HTTPSでは443番(TCP)が利用されます。
以下のサイトにわかりやすいイラストがありました。

[「ポートとソケットがわかればインターネットがわかる」を書きました:Geekなぺーじ](http://www.geekpage.jp/blog/?id=2016-11-10-1)

より細かな仕様についてはRFC 1340に英語で書かれています。

[RFC 1340](https://tools.ietf.org/html/rfc1340#page-9)

#### プロセスについて

あ

### [4] WebブラウザからApache HTTP Serverへアクセス

WindowsからWebブラウザを起動して「`http://x.x.x.x/`」へアクセスします。

TODO: スクショ

### [5] 表示されるページを内容を変更

#### VSCode + SSH

#### HTML

#### CSS

### [6] Apache HTTP Serverの設定変更

#### [6-1] configテストを行う

```shell
$ apachectl configtest
```

#### [6-2] restart

再起動の前後で比較できるコマンド例を貼る

```shell
```

#### [6-3] web browserからアクセス

## 演習

### 演習1. 画像を表示

ヒント: curl, imgタグ

### 演習2. NotFoundページの書き換え

ヒント: ErrorDocument

## まとめ

やったこと:

- xxx

キーワード:

- xxx
