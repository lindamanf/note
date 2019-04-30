# Git Command

## Remoteのリポジトリからソースをコピー

- ソースのクローン

```sh
git clone hogehoge.git
```

## Remoteへ新規でプッシュ

- gitのイニシャライズ(gitを使うファイルを指定)

```sh
cd <対象パス>
git init 
```

- ローカルリポジトリに全てのファイルを追加

```sh
git add -A
```

- 変更のコミット

```sh
git commit -m "Initial Commit"
```

- [Github](https://github.com/lindamanf?tab=repositories)にてリポジトリ作成

- Remoteリポジトリの追加

```sh
git remote add origin https://github.com/lindamanf/qanda.git
```

- Remoteリポジトリの向き先変更

```sh
git remote set-url origin https://github.com/lindamanf/microblog.git
```

- リモートリポジトリへ登録

```sh
git push -u origin master
```

## その他コマンド

- ステータスの確認

```sh
git status
```
