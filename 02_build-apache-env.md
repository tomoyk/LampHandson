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

コマンド実行後に以下のメッセージが出た場合は確認して `y` を入力してEnterを押します。

```
Do you want to continue? [Y/n] y
```

#### パッケージマネージャについて

Ubuntuには様々なソフトウェアがパッケージによってインストールされています。例えばWebブラウザを使いたい場合、Firefoxのパッケージをインストールします。
パッケージによってソフトウェアを導入することで、ソースコードからビルドを行う場合に比べてバージョン管理やアンインストールを容易に行えます。

今回はUbuntuに導入されているパッケージ管理コマンド apt を利用してパッケージの操作を行います。

### [2] Apache HTTP Serverのインストール

Webサーバを構築します。今回はサーバーソフトウェアとしてApache HTTP Serverを利用します。Apache HTTP ServerはApacheが提供するWebサーバーソフトウェアの1つです。

```shell
$ sudo apt -y install apache2
```

### [3] Apache HTTP Serverの起動・停止・再起動

インストールすると直後にWebサーバーが起動します。

#### 現在の状態: `$ sudo systemctl status apache2`

```shell
$ sudo systemctl status apache2
● apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: 
  Drop-In: /lib/systemd/system/apache2.service.d
           └─apache2-systemd.conf
   Active: active (running) since Mon 2019-05-27 14:04:07 UTC; 1min 50s ago
 Main PID: 14790 (apache2)
    Tasks: 55 (limit: 1113)
   CGroup: /system.slice/apache2.service
           ├─14790 /usr/sbin/apache2 -k start
           ├─14792 /usr/sbin/apache2 -k start
           └─14793 /usr/sbin/apache2 -k start

May 27 14:04:07 saba systemd[1]: Starting The Apache HTTP Server...
May 27 14:04:07 saba apachectl[14763]: AH00558: apache2: Could not reliably dete
May 27 14:04:07 saba systemd[1]: Started The Apache HTTP Server.
```

#### 停止: `$ sudo systemctl stop apache2`

試しにAoache HTTP Serverを停止してみます。

```shell:
$ sudo systemctl stop apache2
$
$ sudo systemctl status apache2
● apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: 
  Drop-In: /lib/systemd/system/apache2.service.d
           └─apache2-systemd.conf
   Active: inactive (dead) since Mon 2019-05-27 14:07:01 UTC; 2min 34s ago
  Process: 15040 ExecStop=/usr/sbin/apachectl stop (code=exited, status=0/SUCCES
 Main PID: 14790 (code=exited, status=0/SUCCESS)

May 27 14:04:07 saba systemd[1]: Starting The Apache HTTP Server...
May 27 14:04:07 saba apachectl[14763]: AH00558: apache2: Could not reliably dete
May 27 14:04:07 saba systemd[1]: Started The Apache HTTP Server.
May 27 14:07:01 saba systemd[1]: Stopping The Apache HTTP Server...
May 27 14:07:01 saba apachectl[15040]: AH00558: apache2: Could not reliably dete
May 27 14:07:01 saba systemd[1]: Stopped The Apache HTTP Server.
```

#### 起動: `$ sudo systemctl start apache2`

停止していたApache HTTP Serverを起動してみます。

```shell
$ sudo systemctl start httpd
$
$ sudo systemctl status apache2
● apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: 
  Drop-In: /lib/systemd/system/apache2.service.d
           └─apache2-systemd.conf
   Active: active (running) since Mon 2019-05-27 14:11:02 UTC; 2s ago
  Process: 15040 ExecStop=/usr/sbin/apachectl stop (code=exited, status=0/SUCCES
  Process: 15065 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCC
 Main PID: 15083 (apache2)
    Tasks: 55 (limit: 1113)
   CGroup: /system.slice/apache2.service
           ├─15083 /usr/sbin/apache2 -k start
           ├─15085 /usr/sbin/apache2 -k start
           └─15086 /usr/sbin/apache2 -k start

May 27 14:11:02 saba systemd[1]: Starting The Apache HTTP Server...
May 27 14:11:02 saba apachectl[15065]: AH00558: apache2: Could not reliably dete
May 27 14:11:02 saba systemd[1]: Started The Apache HTTP Server.
```

#### 再起動: `$ sudo systemctl restart apache2`

Apache HTTP Serverを再起動してみます。

```shell
$ sudo systemctl restart httpd
$
$ sudo systemctl status apache2
● apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: 
  Drop-In: /lib/systemd/system/apache2.service.d
           └─apache2-systemd.conf
   Active: active (running) since Mon 2019-05-27 14:13:26 UTC; 2s ago
  Process: 15150 ExecStop=/usr/sbin/apachectl stop (code=exited, status=0/SUCCES
  Process: 15155 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCC
 Main PID: 15173 (apache2)
    Tasks: 55 (limit: 1113)
   CGroup: /system.slice/apache2.service
           ├─15173 /usr/sbin/apache2 -k start
           ├─15174 /usr/sbin/apache2 -k start
           └─15175 /usr/sbin/apache2 -k start

May 27 14:13:26 saba systemd[1]: Starting The Apache HTTP Server...
May 27 14:13:26 saba apachectl[15155]: AH00558: apache2: Could not reliably dete
May 27 14:13:26 saba systemd[1]: Started The Apache HTTP Server.
```

### [4] Apache HTTP Serverの動作をLinuxコマンドで確認

#### ◯ポートについて

コンピュータがネットワークで接続された他のコンピュータとやり取りを行うには、データ（パケット）の出入りが必要です。この出入り口はポートと呼ばれます。

ポートには0〜65535の範囲で番号が割り当てられています。一般にHTTPでは80番(TCP), HTTPSでは443番(TCP)が利用されます。
以下のサイトにわかりやすいイラストがありました。

[「ポートとソケットがわかればインターネットがわかる」を書きました:Geekなぺーじ](http://www.geekpage.jp/blog/?id=2016-11-10-1)

より細かな仕様についてはRFC 1340に英語で書かれています。

[RFC 1340](https://tools.ietf.org/html/rfc1340#page-9)

#### ◯開いているポートの確認

```shell
$ ss -anut | grep LISTEN
tcp  LISTEN 0      128                         127.0.0.53%lo:53         0.0.0.0:*                                                                               
tcp  LISTEN 0      128                               0.0.0.0:22         0.0.0.0:*                                                                               
tcp  LISTEN 0      128                                     *:80               *:*                                                                               
tcp  LISTEN 0      128                                  [::]:22            [::]:*                                                     
```

#### ◯プロセスについて

あああ

#### ◯稼働プロセスの確認

```shell
$ ps aux | grep apache
root     15173  0.0  0.4  78192  4948 ?        Ss   14:13   0:00 /usr/sbin/apache2 -k start
www-data 15174  0.0  0.4 1289240 4868 ?        Sl   14:13   0:00 /usr/sbin/apache2 -k start
www-data 15175  0.0  0.4 1289240 4868 ?        Sl   14:13   0:00 /usr/sbin/apache2 -k start
john     15251  0.0  0.1  13136  1048 pts/0    S+   14:18   0:00 grep --color=auto apache
```

### [5] WebブラウザからApache HTTP Serverへアクセス

WindowsからWebブラウザを起動して「`http://x.x.x.x/`」へアクセスします。

TODO: スクショ

### [6] 表示されるページを内容を変更

#### ◯VSCode + SSH

#### ◯HTML

#### ◯CSS

### [7] Apache HTTP Serverの設定変更

#### ◯portを変更

#### ◯configテストを行う

```shell
$ apachectl configtest
```

#### ◯再起動

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
