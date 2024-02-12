# はじめに
このリポジトリはPHPの最低限の動作環境をDockerで構築するためのコードを保管する目的で使用します。
2024/02/12現在。最低限のPHP動作を確認していますが、DB周りの確認はできていません。

少しずつ動作確認、環境を整備していく予定です。

# 使用方法

1. PHPのコード設置箇所を作成

    ```shell
     mkdir -p src
    ```

2. srcディレクトリ直下に`index.???`を作成する（アクセス時の最初に表示されるページ）
???の部分を`html`にするか`php`にするかは任せる。
ただし`php`にする場合は以下ファイルの設定を修正すること。

    ```plaintext
     infra/docker/nginx/default.conf
    ```

    ```conf
     #省略

     server {
         listen 80;
         listen [::]:80;
         # 省略

         # アクセス時に開かれるファイル名の設定
         # index index.html;
         index index.php; # .phpに変更

         # 省略
     }
    ```

3. makeコマンドで事前に書かれた設定値を読み込ませてPHP環境を構築する
    ```shell
     make create-project
    ```

4. [http://localhost](http://localhost)にアクセスする

