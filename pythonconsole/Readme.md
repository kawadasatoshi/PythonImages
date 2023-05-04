

## commands:コマンド入力

1. move to "pythonconsole" directory（pythonconsoleディレクトリにcdコマンドで移動してください。）



2. build pythonconsole image

```sh
docker image build -t pythonconsole .
```

3. run pythonconsole container

```sh
docker run -it -v ./code:/code pythonconsole bash
```






## 

