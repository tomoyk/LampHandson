# 03.PHP実行環境の構築

## 概要

PHPの実行環境

## 手順

### [1] PHPのパッケージをインストール

必要なパッケージは依存関係によりインストールされます。

```shell
sudo apt install php
```

### [2] PHPの設定を変更

PHPのタイムゾーン設定を変更します。

```shell
cd /etc/php/7.2/apache2/
sudo cp php.ini php.ini.bck  # バックアップ
```

設定ファイルをnanoエディタで編集します。

```
$ sudo nano php.ini
```

変更前:

```
[Date]
; Defines the default timezone used by the date functions
; http://php.net/date.timezone
;date.timezone =
```

変更後:

```
[Date]
; Defines the default timezone used by the date functions
; http://php.net/date.timezone
date.timezone = "Asia/Tokyo"
```

変更した設定を反映させるために、Apacheを再起動します。

```
$ sudo systemctl restart apache2
```

### [3] 時刻を返すWebアプリを作る

サーバーの現在の時刻を表示するWebアプリケーションを作成します。

`/var/www/html/`に以下の内容で`time.php`を作成する。

```
$ sudo nano /var/www/html/time.php
```

```php
<html>
<head>
  <meta charset="utf-8">
  <title>Current Date</title>
</head>
<body>
<h1><?php echo date('l jS \of F Y h:i:s A'); ?></h1>
</body>
</html>
```

Webブラウザを起動して `http://127.0.0.1/time.php` へアクセスする。

#### ★演習1

 `http://127.0.0.1/time.php` と `http://127.0.0.1/index.html` のそれぞれへアクセスして違いを比較してください。

ヒント: ページを更新するたびに表示される内容がどうなるか？

#### ★演習2

PHPの`date()`関数の日付フォーマットを変更して表示形式を `2019/06/09 23:45` へ変更してみてください。

### [4] 簡易的なWebフォームを作る

```php
<?php
function h($text) {
  echo htmlspecialchars($text, ENT_QUOTES);
}
?>
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>Sample APP</title>
</head>
<body>
  <h1>サンプル　Webアプリ</h1>

  <?php 
    $input_email = filter_input(INPUT_GET, 'email', FILTER_VALIDATE_EMAIL);
    if (is_string($input_email) === true):
  ?>
  <h2>メールアドレスは <?php h($input_email); ?> ですね!</h2>
  <br>
  <a href="<?php h(basename(__FILE__)); ?>">戻る</a>

  <?php else: ?>
  <form action="<?php h(basename(__FILE__)); ?>" method="get">
    <input type="text" name="email" placeholder="john@example.com">
    <button type="submit">送信</button>
  </form>
  <?php endif ?>
</body>
</html>
```

#### [5-3] メモ帳

### [6] セキュリティ

### [7] PHPの設定

- error
- timezone

## まとめ

やったこと:

- xxx

キーワード:

- xxx
