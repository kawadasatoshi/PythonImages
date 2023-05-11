

## commands:コマンド入力


1. clone this repo

本リポジトリのソースコードをダウンロードします。

```sh
git clone https://github.com/kawadasatoshi/PythonImages.git
```


2. move to "django" directory

djangoディレクトリにcdコマンドで移動します。

```sh
cd PythonImages/django/
```


3. build django image

djangoイメージをbuildします。

```sh
docker image build -t django .
```


4. run django container

先ほど作成した、djangoイメージコンテナをrunします。

```sh
docker run -it -p 80:80 -v ./code:/code django bash
```

コンテナの内部に入ったら、pythonコードを実行しましょう


```sh
python main.py
```

ブラウザから http://localhost/

にアクセスしてみてください。
    





