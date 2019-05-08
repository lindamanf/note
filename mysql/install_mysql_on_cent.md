# MySQLのインストール方法

#### インストール

* dev.mysqlから対象バージョンのRPMパッケージを取得してインストール

```bash
sudo rpm -ivh http://dev.mysql.com/get/mysql57-community-release-el7-8.noarch.rpm
sudo yum install mysql-community-server
```

#### 初期設定

* mysqlのコンフィグ追記

```bash
sudo vi /etc/my.cnf
---
[mysqld]
.
.
.
character-set-server = utf8
default_password_lifetime = 0
---
```

* サービスを起動

```bash
sudo systemctl start mysqld.service
```

* サービスを自動起動可に

```bash
sudo systemctl enable mysqld.service
```

* パスワードの確認

```bash
sudo cat /var/log/mysqld.log | grep password
```

#### MySQLの操作

* ログイン

```bash
mysql -u root -p
```

* rootと同等の権限を持つユーザー作成

```bash
grant all privileges on *.* to admin@'%' identified by '!Adm1nPassword' with grant option;
```

* utf8でDB作成

```bash
create database admindb default character set utf8;
```