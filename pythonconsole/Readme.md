

## commands:コマンド入力


1. clone this repo

本リポジトリのソースコードをダウンロードします。

```sh
git clone https://github.com/kawadasatoshi/PythonImages.git
```


2. move to "pythonconsole" directory

pythonconsoleディレクトリにcdコマンドで移動します。

```sh
cd PythonImages/pythonconsole/
```


3. build pythonconsole image

pythonconsoleイメージをbuildします。

```sh
docker image build -t pythonconsole .
```

- `docker image build`では、dockerイメージをビルドし、コンテナを作成する基本的なコマンド

- `-t`フラグで、`pythonconsole`という名前をつけています。


4. run pythonconsole container

先ほど作成した、pythonconsoleイメージコンテナをrunします。

```sh
docker run -it -v ./code:/code pythonconsole bash
```

- `docker run `は、dockerコンテナを実行するコマンドです。

- `-it`フラグは、**コンテナ内部とやりとりするためのコマンド**で、`bash`コマンドと組み合わせることで、ssh接続されたかのように、コンテナ内部からLinuxコマンドを実行することができます。




