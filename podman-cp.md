![Podman](imgs/podman-3-logo-95w-90h.webp)
# PodmanとホストOS間でファイルコピー
ホストOSで以下のコマンドを実行する.
```bash
% podman cp wonderful_grothendieck{*1}:/home/...省略.../src/adventofcode{*2} .{*3}
```
* *1 - コンテナ名
* *2 - コピー元のコンテナ内のパス
* *3 - コピー先のホストOSのパス

# 環境
* podman version 5.3.1
* MacOS 15.2

# 参考
[コンテナとホスト間のファイルコピー](https://qiita.com/Nao_Ishimatsu/items/f1b20b34b09e3611696e#-実行例-11)

# 変更履歴
* 2025.01.02 - 新規作成

-EOF-