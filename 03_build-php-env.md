# 03.PHP実行環境の構築

## 概要

xxx

## 手順

### [1] PHPのパッケージをインストール

### [2] Apacheの設定を変更

### [3] Apacheの再起動

### [4] PHPの動作確認

#### PHPが動く仕組み

### [5] PHPでプログラミング

#### [5-1] 現在の時刻を表示

```php
<html>
<head>
  <meta charset="utf-8">
  <title>Current Date</title>
</head>
<body>
<h1><?php date('l jS \of F Y h:i:s A'); ?></h1>
</body>
</html>
```

#### [5-2] 簡単なフォーム

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
