# ansible-sample

AnsibleでAmazon EC2にWordPress環境を構築するサンプルPlaybookです。

## Requirements
- ansible 2.2 or later

## Usage

### Download
適当なディレクトリにPlaybookをダウンロードしてください。

```
$ git clone https://github.com/rednes/ansible-sample.git
$ cd ansible-sample
```

### Edit ssh_config

ssh_config.sampleファイルがあるので、ssh_configにコピーしてください。
```
$ cp ssh_config.sample ssh_config
```

ssh_configに自分の環境に応じて、WordPress環境を構築したいAmazon EC2のホスト名、ユーザー、秘密鍵のパスを記載してください。

```
Host *
  StrictHostKeyChecking no
  UserKnownHostsFile /dev/null

Host aws-ec2
  HostName "XX.XX.XX.XX"
  User "user"
  IdentityFile "XXXXXX.pem"
```

### Execute ansible

ansibleを実行すると、対象としたEC2にWordPress環境が構築できます。

```
$ ansible-playbook site.yml -v
```

### Setup WordPress

構築したWordPressにアクセスしてWordPressのセットアップを行ってください。
MySQLのDB名、ユーザー名、パスワードは以下をデフォルト値にしています。

* データベース名：wordpress
* ユーザー名：wordpress-user
* パスワード：wordpress

```
http://(EC2インスタンスのパブリックDNS)/wordpress/wp-admin/setup-config.php
```