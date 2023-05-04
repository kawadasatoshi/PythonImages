

## commands:コマンド入力


1. clone this repo

本リポジトリのソースコードをダウンロードします。

```sh
git clone https://github.com/kawadasatoshi/PythonImages.git
```


2. move to "flask" directory

flaskディレクトリにcdコマンドで移動します。

```sh
cd PythonImages/flask/
```


3. build flask image

flaskイメージをbuildします。

```sh
docker image build -t flask .
```


4. run flask container

先ほど作成した、flaskイメージコンテナをrunします。

```sh
docker run -it -p 5000:80 -v ./code:/code flask bash
```







