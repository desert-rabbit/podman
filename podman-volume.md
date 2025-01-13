![Podman](imgs/podman-3-logo-95w-90h.webp)
# ホストOSのディレクトリをpodmanコンテナにマウントする

podman desktopでマウントの設定をしようとしたら以下のエラー.  
![1](imgs/スクリーンショット%202025-01-05%2013.27.38.png)

ターミナルから実行しても以下のエラー.
![2](imgs/スクリーンショット%202025-01-05%2013.31.12.png)

事前にpodman machineをinitする際に以下を実行しておく必要がある.  
なぜ最初にこれをやらないといけないのか謎.  
また, podman desktopで指定する場所がない, 変更する手段がないのも微妙.
```bash
% cd {マウントしたいフォルダ}
% podman machine init -v $(pwd)
```
![3](imgs/スクリーンショット%202025-01-05%2013.42.18.png)

既に作成済みの場合はmachineを以下コマンドにて削除する.
```bash
% podman machine rm
```

ホストOSで以下のコマンドを実行する.
```bash
% cd {マウントしたいフォルダ}
% podman run -it -v $(pwd):/workspace docker.io/library/python(*1)
```
* *1 - image名

または, Podman Desktopで以下の設定を行ってcontainerを起動する.
* VolumesのPath on the host(左)にマウント元のホストOSのパスを設定
* Path inside the container(右)にマウント先のcontainer内のパスを設定
* Start Containerボタンをクリックしてcontainerを起動
![4](imgs/スクリーンショット%202025-01-05%2013.53.02.png)


# 環境
* podman version 5.3.1
* MacOS 15.2

# 参考
* [【2022年】MacOS で Podman のバインドマウントを使おう](https://qiita.com/hankehly/items/2ec340f927c244559677)
* [macOS + Podman V5では--volumeでのMac上パス指定における/mntが不要に](https://qiita.com/hiroyuki_onodera/items/a82de91752cbfa8339e6)
* [Cannot bind local volume on macOS](https://github.com/containers/podman/issues/13944)

# 変更履歴
* 2025.01.04 - 新規作成

-EOF-