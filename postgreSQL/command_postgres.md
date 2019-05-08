# PostgreSQL備忘録

#### PostgreSQLの操作

* ログイン

```bash
psql -U postgres -h 127.0.0.1 -w
```

* 初期設定（例）

```bash
ALTER ROLE postgres WITH PASSWORD 'P@ssw0rd';
CREATE DATABASE testdb encoding 'UTF8';
```

#### dump

* テーブル指定した定義のみのdump

```bash
pg_dump -U [[user]] -h [[host]] -t [[table_name]] --schema-only --no-owner --no-privileges --disable-dollar-quoting [[db_name]]  > [[path]]

```

* データのみのdump取得

```bash
pg_dump -U [[user]] -h [[host]] -t [[table_name]] --schema-only --no-owner --no-privileges --disable-dollar-quoting [[db_name]]  > [[path]]
```

* コマンドラインからファイルの実行

```bash
psql -U postgres -d testdb -h 127.0.0.1 -f ./test.dump
```
