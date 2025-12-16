# 学んだこと

## SSHとは？

・SSh = サーバーに遠隔でログインする仕組み。

・EC2は画面（GUI）がない ⇒ 基本はSSH操作。

・鍵（キーペア）で本人確認するため、ID/パスワードより安全。

イメージ：鍵（pem）を持っている人だけが、２２番ポートの玄関からサーバーに入れる。

## SGとは？

・EC2に付くファイアウォール。

・許可した通信しか通らない。

ポート：22

用途：SSH

許可元：自分のIP

ポート：80

用途：HTTP

許可元：0.0.0.0/0

# 実践

### SSHでEC2にログイン

コマンド例（Amazon Linux）：

ssh -i my-key.pem ec2-user@xx.xx.xx.xx

・-i : 使う秘密鍵。

・ec2-user : Amazon Linuxのユーザー名。

・xx.xx.xx.xx : EC2のpublic IP。

成功すると：

[ec2-user@ip-xx-xx-xx-xx ~]$

この表示が出る = サーバーに入れた状態。

### 最初にやる基本操作

#### パッケージ更新

sudo yum update -y

・sudo : 管理者権限。

・yum : ソフト管理ツール。

最初に必ずやる癖をつける。

#### Webサーバーを入れてみる

1.nginx or Apacheをインストール。

・nginx例：

sudo yum install nginx -y

・Apache例：

sudo yum install httpd -y

2.サービス起動

sudo systemctl start nginx

3.状態確認（重要）

systemctl status nginx

・active(running) ⇒ 正常

・inactive / failed ⇒ 何かがおかしい

systemctl statusは必ず見る。

#### ブラウザから確認

・EC2のpublic IPをブラウザから開く。

・nginx/Apacheのデフォルト画面が出れば成功。

※出ない場合

・SGで８０番ポートが許可されていない。

・サービスが起動していない。
