

## commands:コマンド入力


1. clone this repo

```sh
git clone https://github.com/kawadasatoshi/PythonImages.git
```


2. move to "pythonconsole" directory

pythonconsoleディレクトリにcdコマンドで移動してください。

```sh
cd PythonImages/pythonconsole/
```


3. build pythonconsole image

```sh
docker image build -t pythonconsole .
```

4. run pythonconsole container

```sh
docker run -it -v ./code:/code pythonconsole bash
```



