# Golang Revel のセットアップ方法

## Revel のインストール

- Revel ライブラリ を Github からインストール

  ```sh
  go get -u github.com/revel/revel
  ```

- Revel のコマンドラインツールをインストール

  ```sh
  go get -u github.com/revel/cmd/revel
  ```

- Revel コマンドを実行出来るように環境変数設定

  ```sh
  export PATH="$PATH:$GOPATH/bin"
  ```

- コマンド実行確認

  ```sh
  $ revel
        Usage:
        C:\Users\linda\workspace\go\bin\revel.exe [OPTIONS] <command>

        Application Options:
        /v, /debug               If set the logger is set to verbose
            /historic-run-mode   If set the runmode is passed a string not json
        /X, /build-flags:        These flags will be used when building the application. May be specified multiple times, only applicable for Build, Run, Package, Test commands

        Available commands:
        build
        clean
        new
        package
        run
        test
        version
  ```

- プロジェクトを新規作成

  ```sh
  revel new myApp
  ```
