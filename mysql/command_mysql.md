# MySQL備忘録

#### MySQLの操作

* ログイン

```bash
mysql -u [[user]] -p[[password]]
```

* rootと同等の権限を持つユーザー作成

```bash
grant all privileges on *.* to [[user]]@'%' identified by '[[password]]' with grant option;
```

* DB作成(utf8で)

```bash
create database [[db_name]] default character set utf8;
```

* コマンドラインからSQLファイルを実行

```sh
mysql -u [[user]] -p[[password]] -h [[host] hc2db < [[file_path]]
```

* テーブルの文字コード確認

```bash
show variables like '%char%';
```

* テーブルの文字コード変更

```bash
alter table [[db_name]] default character set utf8mb4;
```

* データベースの文字コード変更

```bash
ALTER DATABASE [[db_name]] CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
```

#### dumpコマンド

* テーブル定義のdump取得

```bash
mysqldump -u [[user]] -p[[password]] -h [[host]] [[db_name]] -d -n > [file_path]
````

* 特定のテーブル定義のみのdump取得

```bash
mysqldump -u [[user]] -p[[password]] -h [[host]] [[db_name]] [[table_name]] -d -n > [[file_path]]
```

* データとテーブル定義のdump取得

```bash
mysqldump -u [[user]] -p[[password]] -h [[host]] [[db_name]] > [[file_path]]
```
