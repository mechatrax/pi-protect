# piprotect-trixie-lite-arm64-20260608
Raspberry Pi OS (64-bit) Lite April 21st 2026 を元に変更を加えています。

## イメージファイル
イメージファイルは次のリンクからダウンロードできます。  
[piprotect-trixie-lite-arm64-20260608.img.xz](https://mechatrax.com/data/pi-protect/piprotect-trixie-lite-arm64-20260608.img.xz)  

イメージファイルの SHA256 ハッシュ値は次のとおりです。
```
efb33c43c327a84b87e4f41b1cad98918e3e4e8f4b58a64d17da1a2f31890bdc
```

## 変更内容
Raspberry Pi OS からの変更内容は次のとおりです。
  * 4GPi 用パッケージをインストール
  * ファイアウォールに ufw を使用（デフォルトは許可、wwan0 と ppp0 のみ受信拒否）
  * シリアルコンソールを有効化
  * USB ポートの電流制限を緩和する設定を有効化
  * rootfs で ext4 の 64bit オプションを有効化
  * ハードウェアウォッチドッグタイマの監視に systemd を使用
  * APT::Periodic の無効化
  * avahi-daemon で ppp0 と wwan0 を無視
  * slee-Pi3 用パッケージをインストール
  * 簡易 UPS 基板を使用するために sleepi3-monitor の設定を変更
  * パッケージを 20260608 時点の最新版に更新

## インストールパッケージ
  * Raspbian パッケージ  
    jo  
    jq  
    ufw

  * 独自パッケージ  
    4gpi-utils  
    4gpi-net-mods  
    4gpi-networkmanager  
    python-sleepi  
    sleepi3-utils  
    sleepi3-monitor  
    sleepi3-firmware  
    sleepi3-dkms

  * その他パッケージ  
    soracom

## 削除パッケージ  
  * 常駐プロセス削減のため削除  
    udisks2
