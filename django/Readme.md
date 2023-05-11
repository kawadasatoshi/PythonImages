

## commands:コマンド入力


### 1. clone this repo

本リポジトリのソースコードをダウンロードします。

```sh
git clone https://github.com/kawadasatoshi/PythonImages.git
```


### 2. move to "django" directory

djangoディレクトリにcdコマンドで移動します。

```sh
cd PythonImages/django/
```


### 3. build django image

djangoイメージをbuildします。

```sh
docker image build -t django .
```


### 4. run django container

- (for mac or linux user):先ほど作成した、djangoイメージコンテナをrunします。

```sh
docker run -it -p 80:80 -v ./code:/code django bash
```

- (for windows user):なお、windowsの方は次のコマンドでフルパスでボリュームをマウントします。

```sh
docker run -it -p 80:80 -v ${PWD}/code:/code django bash
```


### 5. スクリプト実行起動

コンテナの内部に入ったら、pythonコードを実行しましょう

```sh
django-admin startproject mysite
python mysite/manage.py startapp myapp
python mysite/manage.py migrate
```


### 6. runserver

```sh
python mysite/manage.py runserver 0.0.0.0:80
```


### 7.アクセス

ブラウザから http://localhost/

にアクセスしてみてください。
    





