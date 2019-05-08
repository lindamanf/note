# PostgreSQL9.1インストール方法

※CentOSの場合ver6以下

#### インストール

* PostgreSQL9.1のRPMパッケージを取得して実行
  
```bash
wget http://yum.postgresql.org/9.1/redhat/rhel-6-i386/pgdg-centos91-9.1-4.noarch.rpm
sudo rpm -ivh pgdg-centos91-9.1-4.noarch.rpm
```

* インストール

```bash
sudo yum --disableplugin=priorities install postgresql91-server
```

※（最新版はyumで直接取得できる）

```bash
sudo yum -y install postgresql-server
```

#### 初期設定


* データベースの初期化
  ※/var/lib/pgsql/dataに設定ファイルなどが配置される。

```bash
sudo service postgresql-9.1 initdb
```

* スーパーユーザーへ変更

```bash
su
```

* 外部アクセスを許可する為にコンフィグファイルへパラメータ追加

```bash
cd /var/lib/pgsql/9.1/data
cp postgresql.conf postgresql.conf.org
echo "listen_addresses = '*'" >> /var/lib/pgsql/9.1/data/postgresql.conf
diff -u postgresql.conf.org postgresql.conf
cp pg_hba.conf pg_hba.conf.org
echo "# PostgreSQL Client Authentication Configuration File" >  ./pg_hba.conf
echo "# ===================================================" >> ./pg_hba.conf
echo "local all all              trust"                      >> ./pg_hba.conf
echo "host  all all 0.0.0.0/0    trust"                      >> ./pg_hba.conf
echo "host  all all ::1/128      trust"                      >> ./pg_hba.conf
```

* 設定を適用させる為にサービスを再起動

```bash
sudo service postgresql-9.1 restart
```

* 自動起動を有効化

```bash
sudo chkconfig postgresql-9.1 on
```

#### PostgreSQL操作

* ログイン

```bash
psql -U postgres -h 127.0.0.1 -w
```

* 初期設定（例）

```bash
ALTER ROLE postgres WITH PASSWORD 'P@ssw0rd';
CREATE DATABASE testdb encoding 'UTF8';
```