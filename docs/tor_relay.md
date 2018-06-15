# torのリレーサーバの設定

## 設定ファイルを編集する
 ファイルは`/etc/tor/torrc`にあるので編集します

 torは世界中のユーザが接続して、様々なに通信経路をホップするので、発信者が誰だかわからなくなる機能があって、そのネットワークは有志のコンピュータリソースによってなりったています。  

 torrcの設定をこのようにして使っています。  

 殆どがコメントアウトされていますが、ちゃんと記述するべきところは少ないです。  

```console
SOCKSPort 9050
ControlSocket 0
ControlPort 9051
ORPort 9001
Nickname hogeeeeeeeeee
ExitRelay 0
ExitPolicy reject *:*
```

## torを再起動する

```console
$ sudo systemctl restart tor
```

## 接続をテストする

```console
$ curl --socks5-hostname localhost:9050 https://check.torproject.org | head -n 10
```
ここで成功と出ていればOKです
```console
<html lang="en_US">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>
      Congratulations. This browser is configured to use Tor.
1</title>
```

## nyxで使用状況を見る
torネットワークのステータスnyxで確認することができます  

nyxは`tor-arm`というパッケージに組み込まれています
```console
$ sudo apt install tor-arm
```
実行  
```console
$ sudo nyx
```

<div align="center">
  <img width="700px" src="https://user-images.githubusercontent.com/4949982/41478912-6770a38e-7104-11e8-9fb1-49187c243b67.png">
</div>
