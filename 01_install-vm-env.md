# 01.仮想環境と仮想マシンの構築

## 概要

Linuxの環境をWindows上にインストールした仮想化ソフトウェア(VMWare Workstation Player)によって構築します。

実機へのインストール（デュアルブート）は操作ミスによりWindows環境を破壊する恐れがあり、授業への支障を考え断念しました。
仮想環境であれば仮に操作ミスをしても仮想マシンの再作成で済むため影響範囲を最小限に抑えることができるため採用しています。

## 手順

### [1] Linuxのインストールイメージのダウンロード

以下のURLから Ubuntu 18.04.2 LTS をダウンロードしてください。

http://ftp.riken.jp/Linux/ubuntu-releases/bionic/ubuntu-18.04.2-desktop-amd64.iso

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

### [5] 仮想マシンの起動

### [6] インストール作業

### [7] 仮想マシンへVMWare Toolsをインストール

### [8] WindowsへSSHクライアントのインストール

### [9] WindowsからLinuxへSSH接続

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
