# 01.仮想環境と仮想マシンの構築

## 概要

Linuxの環境をWindows上にインストールした仮想化ソフトウェア(VMWare Workstation Player)によって構築します。

実機へのインストール（デュアルブート）は操作ミスによりWindows環境を破壊する恐れがあり、授業への支障を考え断念しました。
仮想環境であれば仮に操作ミスをしても仮想マシンの再作成で済むため影響範囲を最小限に抑えることができるため採用しています。

## 手順

### [1] Linuxのインストールイメージのダウンロード

以下のURLから Ubuntu 18.04.2 LTS をダウンロードしてください。

http://ftp.riken.jp/Linux/ubuntu-releases/bionic/ubuntu-18.04.2-live-server-amd64.iso

#### Linuxについて

Linuxとは当時、大学生であったLinus Torvaldsが開発したOS(オペレーティングシステム)です。UNIX互換のOSとして開発されました。Linuxのプログラムの特徴としてライセンス形態が挙げられます。Linuxのプログラムには`GPL(GNU General Public License)`というライセンス形式が付与されています。これには以下の内容が含まれています。

> - プログラムを実行する自由
> - ソースの改変の自由
> - 利用・再配布の自由
> - 改良したプログラムをリリースする権利
>
> (Linux標準教科書より引用)

こうした自由な形態を採用した為、限られた組織や個人によって独占されることなく広く普及し発展しました。

#### ディストリビューションについて

Linuxはディストリビューションとばれる利用者が使いやすい形式で配布されています。開発者により数多くのディストリビューションが作成されています。代表的なディストリビューションには、Ubuntu, CentOS, Arch Linux, Debian, Fedora, Linux Mint, OpenSUSEなどがあります。

参考: [ディストリビューションのツリー](https://upload.wikimedia.org/wikipedia/commons/1/1b/Linux_Distribution_Timeline.svg)

### [2] VMWare Workstation Playerをダウンロード

以下のリンクからVMWare Workstation Playerをダウンロードしてください。

[ダウンロード VMware Workstation Player](https://my.vmware.com/jp/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/15_0)

<img src="images/01/download-vmware.png">

### [3] VMWare Workstation Playerのインストール

手順[2]でダウンロードしたインストーラを起動すると、以下のウィンドウが表示されます。「次へ」をクリックします。

<img src="images/01/inst01.png">

規約に同意しないとインストールできないので、「同意します」にチェックをいれて「次へ」をクリックします。

<img src="images/01/inst02.png">

インストール先はこのままで「次へ」をクリックします。

<img src="images/01/inst03.png">

「カスタマー・エクスペリエンス向上プログラムに参加します」のチェックを外して「次へ」をクリックします。

<img src="images/01/inst04.png">

このまま「次へ」をクリックします。

<img src="images/01/inst05.png">

インストールを行なうので「インストール」をクリックします。

<img src="images/01/inst06.png">

インストールが終わるまでしばらく待ちます。

<img src="images/01/inst07.png">

インストールが終わると以下が表示されます。「完了」をクリックして終了してください。

<img src="images/01/inst08.png">

### [4] 仮想マシンの作成

VMWare Workstation Playerを起動します。

<img src="images/01/vmware01.png">

「後でOSをインストール」を選択して「次へ」をクリックします。

<img src="images/01/vmware03.png">

ゲストOSを「Linux」、バージョンを「Ubuntu 64ビット」に設定して「次へ」をクリックします。

<img src="images/01/vmware04.png">

仮想マシン名を「LAMP」にして「次へ」をクリックします。

<img src="images/01/vmware05.png">

そのまま「次へ」をクリックします。

<img src="images/01/vmware06.png">

ここでは設定を変更せず「完了」をクリックします。

<img src="images/01/vmware07.png">

「仮想マシン設定の編集」をクリックして仮想マシンの設定をします。

<img src="images/01/vmware08.png">

「ハードウェア」タブから「CD/DVD(SATA)」をクリックします。「デバイスのステータス」にある「**起動時に接続**」のチェックを入れます。「接続」から「**ISOイメージファイルを使用する**」を選び、あらかじめダウンロードしたISOファイルを選択します。

<img src="images/01/vmware09.png">

仮想マシンの設定を以下に変更して最後に「OK」をクリックします。

- メモリ: 1GB
- プロセッサ: 2 (コア)
- 「サウンドカード」を削除
- 「プリンタ」を削除
- 「ディスプレイ」の「3Dグラフィックスのアクセラレーション」のチェックを外す

<img src="images/01/vmware10.png">

### [5] 仮想マシンの起動とOSインストール

「仮想マシンの再生」をクリックして仮想マシンを起動します。

<img src="images/01/vmware11.png">

しばらく待つと以下の画面が表示されるので、EnglishのままEnterを押します。

<img src="images/01/vmware12.png">

キーボードの設定を以下に設定して「Done」を選択します。

- Layout: Japanese
- Variant: Japanese

<img src="images/01/vmware13.png">

「Install Ubuntu」を選択します。

<img src="images/01/vmware14.png">

ネットワーク設定は変更せず「Done」を選択します。

<img src="images/01/vmware15.png">

変更せず「Done」を選択します。

<img src="images/01/vmware16.png">

ミラーサーバーの設定を理研に変更します。Mirror addressへ「**http://ftp.riken.go.jp/Linux/ubuntu/**」を入力して「Done」を選択します。理研以外のミラーサーバーの一覧は [ここ](https://www.ubuntulinux.jp/ubuntu/mirrors) から確認できます。

<img src="images/01/vmware17.png">

「Use An Entire Disk」を選択します。パーティションの設定を細かく設定することも出来ますが、今回はディスク全体を使用します。

<img src="images/01/vmware18.png">

インストール先のディスクを選択します。そのままEnterを押します。

<img src="images/01/vmware19.png">

ファイルシステムのセットアップ確認が表示されます。そのまま「Done」を選択します。

<img src="images/01/vmware20.png">

警告が出るので「Continue」を選択します。

<img src="images/01/vmware21.png">

ユーザー名やパスワード、サーバー名の設定を行います。例では以下の設定を行っています。設定が終わったら「Done」を選択します。

- 氏名: john
- サーバー名: saba
- ログイン名: john
- パスワード: pass

<img src="images/01/vmware22.png">

「Install OpenSSH server」を選択して「Done」を選択します。

<img src="images/01/vmware23.png">

追加でのソフトウェアはないので、「Done」を選択します。

<img src="images/01/vmware24.png">

インストールが終わるまで待ちます。

<img src="images/01/vmware25.png">

インストールが終わったら「Reboot Now」を選択します。

<img src="images/01/vmware26.png">

「Please remove the installation medium, then press ENTER:」と表示されたらEnterを押します。本来はインストールメディアを外す作業を行いますが、今回は割愛します。

<img src="images/01/vmware27.png">

起動中の様子が以下です。

<img src="images/01/vmware28.png">

ディスプレイに「Ubuntu 18.04.2 LTS ...」の表示がされたら、先程作成したユーザー名とパスワードでログインを行います。パスワードは入力時にディスプレイに何も表示されないので注意が必要です。

<img src="images/01/vmware29.png">

ログインに成功すると以下の画面が表示されます。表示されている文字列の中から「**IP address for ens33: ...**」を探してメモします。

以下の例では「192.168.88.129」をメモします。

<img src="images/01/vmware30.png">

### [6] WindowsからLinuxへSSH接続

ここまでの手順で 仮想マシンの作成、OSのインストール を行いました。これによって仮想マシン上にLinuxサーバーを構築しました。

ここからはWindowsからLinuxサーバーへ接続してコマンドラインでの操作を行います。

<img src="images/01/ssh01.png">

### [7] Linuxコマンドによるファイル操作

## まとめ

やったこと:

- VMWare Workstation Playerのインストール
- 仮想マシンへLinuxのインストール
- WindowsへSSHクライアントソフトウェアをインストール
- WindowsからLinuxへSSH接続

キーワード:

- 仮想化
- Linux
- SSH
