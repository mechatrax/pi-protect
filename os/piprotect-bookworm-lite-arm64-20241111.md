# piprotect-bookworm-lite-arm64-20241111
Raspberry Pi OS (64-bit) Lite October 22nd 2024 を元に変更を加えています。

## イメージファイル
イメージファイルは次のリンクからダウンロードできます。  
[piprotect-bookworm-lite-arm64-20241111.img.xz](https://mechatrax.com/data/pi-protect/piprotect-bookworm-lite-arm64-20241111.img.xz)  

イメージファイルの SHA256 ハッシュ値は次のとおりです。
```
d2d6fa4ce00ce44966c6d8eff77a7189d213d695d3a612ae2a4f7f786d79a1b8
```

## 変更内容
Raspberry Pi OS からの変更内容は次のとおりです。
  * 4GPi 用パッケージをインストール
  * ファイアウォールに ufw を使用（デフォルトは許可、wwan0 と ppp0 のみ受信拒否）
  * シリアルコンソールを有効化
  * rootfs で ext4 の 64bit オプションを有効化
  * ハードウェアウォッチドッグタイマの監視に systemd を使用
  * APT::Periodic の無効化
  * avahi-daemon で ppp0 と wwan0 を無視
  * slee-Pi3 用パッケージをインストール
  * 簡易 UPS 基板を使用するために sleepi3-monitor の設定を変更
  * NetworkManager の radio 設定にて WiFi を無効化
  * パッケージを 20241111 時点の最新版に更新

## インストールパッケージ
  * Raspbian パッケージ  
    jo  
    jq  
    ufw

  * 独自パッケージ  
    4gpi-utils  
    4gpi-net-mods  
    4gpi-networkmanager  
    mechatrax-archive-keyring  
    python-sleepi  
    sleepi3-utils  
    sleepi3-monitor  
    sleepi3-firmware

  * その他パッケージ  
    soracom

## 削除パッケージ  
  * 常駐プロセス削減のため削除  
    triggerhappy  
    udisks2

