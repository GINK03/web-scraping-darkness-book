
# 必要ソフトウェアと環境

## OS
 - Ubuntu Linux(このドキュメントでは、UbuntuLinuxを仮定しています)
 - Python 3.6

## Pythonモジュール
 - requests
 - beautifulsoup
 - selenium
 - Google Chrome
 - ChromeDriver
 - tor
 - pysocks

## Ubuntu Linuxのインストール
  UbuntuはDebian系のLinuxの一種で、使用者多いのと、アカデミック用途で使われることが多いということで、学術系のソフトウェアとライブラリが、RHEL系より豊富な印象があります。  
  DebianとUbuntuがありますが、Ubuntuはインストールが楽なので、初心者におすすめです。  

## Python3をインストールする
　最新のUbuntuではデフォルトで入っている気がしますが、一昔前のバージョンを使っていたりすると、入っていなかったりします。  

　ターミナルという黒い画面から、pipというパッケージマネージャソフトも入れましょう。  
```console
$ sudo apt install python3
$ sudo apt install python3-pip
```

## Pythonのモジュールを追加する
pipというコマンドでモジュールを追加管理できます  

```console
$ sudo pip3 install bs4
$ sudo pip3 install selenium
```

## Google Chromeのインストール
 ターミナルからのインストールは少し面倒で、aptのレポジトリにgoogleのソフトウェアを参照できるように設定します  
```console
$ wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```
google-chrome-stableをインストール
```console
$ sudo apt update
$ sudo apt install google-chrome-stable
```

## chromedriverをインストール
このサイトから最新版をダウンロードします  

http://chromedriver.chromium.org/downloads

例えば、このzip圧縮されたものを用いると、
```console
$ wget https://chromedriver.storage.googleapis.com/2.40/chromedriver_linux64.zip
$ unzip chromedriver_linux64.zip
$ sudo mv chromedriver /usr/local/bin
```

## torをインストール
torは匿名化ソフトで発信元を隠すのに最適なソフトウェアです  
```console
$ sudo apt install tor
```
torのローカルホストの匿名のサーバが立ち上がるので、試しにアクセスしてみます
```console
$ curl -sL --socks5 127.0.0.1:9050 ipinfo.io
{
  "ip": "176.10.104.243",
  "hostname": "tor2e1.digitale-gesellschaft.ch",
  "city": "",
  "region": "",
  "country": "CH",
  "loc": "47.1449,8.1551",
  "org": "AS51395 SOFTplus Entwicklungen GmbH"
```
