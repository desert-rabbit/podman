![Podman](imgs/podman-3-logo-95w-90h.webp)
# container内で日本語フォルダ名が文字化けする
日本語含むフォルダをcontainerにマウントした後, containerでlsコマンドを実行したり,
VSCodeで参照しようとすると文字化けする事象が発生.  
以下の手順で確認・設定を行う.

1. 以下のコマンドを実行し,localeのリストを表示する.
    ```bash
    % locale -a
    ```

1. 実行結果にC.utf-8が存在していること確認.

1. VSCodeでコンテナ内のホームディレクトリにある.bashrcファイルを開く.

1. 末尾に以下を追記して保存.
    ```bash
    export LANG=C.UTF-8
    ```

1. コンテナを再起動し,文字化けが解消していることを確認する.

# 環境
* podman version 5.3.1
* MacOS 15.2

# 参考
* [Dockerではコンテナのlocaleの再確認を](https://qiita.com/kazuyoshikakihara/items/0cf74c11d273b0064c83)

# 変更履歴
* 2025.01.20 - 新規作成

-EOF-