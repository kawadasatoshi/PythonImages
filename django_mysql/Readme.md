

## 本記事で解説すること

- ソースコードの入手
- Djangoプロジェクトの作成
- `docker-compose build`を使用したコンテナ作成
- `docker-compose up`による起動
- `docker-comopse exec ... bash`によるコンテナ内部へのログイン
- Djangoプロジェクトの起動確認
- Djangoプロジェクトのアカウント作成
- mysqlコンテナの確認


## commands:コマンド入力


### 1. ソースコードの入手（clone this repo）

本リポジトリのソースコードをダウンロードします。

```sh
git clone https://github.com/kawadasatoshi/PythonImages.git
```


### 2. カレントディレクトリ移動（move to "django_mysql" directory）

djangoディレクトリにcdコマンドで移動します。

```sh
cd PythonImages/django_mysql/
```


### 3. Djangoプロジェクトファイルを作ろう（move to "django" and create projectfile）

- djangoディレクトリに移動

```sh
cd django
```

- djangoイメージファイルをビルド

```sh
docker image build -t django .
```

- djangoを起動してコンテナ内部に入る

```sh
# for mac or linux user
docker run -it -p 80:80 -v ./code:/code django bash
```

```sh
# for windows user
docker run -it -p 80:80 -v ${PWD}/code:/code django bash
```

- コンテナ内部では以下のコマンドを実行

```sh
django-admin startproject mysite
python mysite/manage.py startapp myapp
python mysite/manage.py migrate
```

**ファイルが作成されればプロジェクトファイルの作成は完了です！**

`exit`コマンドでコンテナを抜け、`docker-compose.yml`があるディレクトリまで`cd ..`で戻る。



### 4. `docker-compose`でイメージを`build`する

```sh
docker-compose build
```


### 5. `docker-compose up`でコンテナ起動

```sh
docker-compose up
```


### 6. アクセスしてみる

ブラウザから http://localhost/

にアクセスしてみてください。

確認ができたら一度サービスを抜けましょう。

1. `Ctrl+C`からサーバーを止めて
2. `exit`コマンドでサーバーから脱出します。

```sh
docker-compose down -v
```

## mysqlとdjangoを結びつける

### 7. djangoのコードをmysqlに接続するように書き換え

djangoのコードを書き換えます。

書き換える対象は:`django_mysql/django/code/mysite/mysite/settings.py`で、既に存在する変数`DATABASES`を以下のように書き換えてください。

```py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'django',
        'USER': 'root',
        'PASSWORD': 'root',
        'HOST': 'db',
        'PORT': '3306',
    }
}
```

### 8. サービス起動

その後サービスを再度起動し

```sh
docker-compose up -d
```

### 9. マイグレーションを行い、データベースにdjangoのデータを登録

django側のコンテナに入ります。

```sh
docker-compose exec app bash
```

コンテナに入った後は以下のコマンドでマイグレーションを行い、ユーザーデータの作成などを行います。

```sh
python mysite/manage.py migrate
python mysite/manage.py createsuperuser
```

### 10. サーバーを起動

```sh
python mysite/manage.py runserver 0.0.0.0:80
```


## 11. バックグランド起動


```sh
docker-compose up db -d
```

2秒後ぐらいに...


```sh
docker-compose up app -d
```












