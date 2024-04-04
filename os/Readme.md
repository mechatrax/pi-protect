# OS イメージ
ここでは、Pi-protect 用の SD カードの OS イメージに関する技術資料等を公開しています。

## 概要
OS には Raspberry Pi OS (Raspbian) を採用し、Pi-protect の動作に必要なツールをセットアップしています。  

4G/LTE のネットワークの管理に NetworkManager を使用しています。  
使用する SIM に応じて[接続設定](https://github.com/mechatrax/4gpi/wiki/%E3%81%9D%E3%81%AE%E4%BB%96#%E6%8E%A5%E7%B6%9A%E8%A8%AD%E5%AE%9A)を行ってください。

ファイアウォールに ufw を使用しています。  
標準で 4GPi の受信ポートをブロックしています。

詳細についてはリリースノートのリンク先を参照してください。

ansible を使用して同等の環境を構築することもできます。  
詳細はリンク先を参照してください。  
https://github.com/mechatrax/ansible-mechatrax-playbook

## 初期ログイン情報カード
Pi-protect 用 microSD カードに付属している初期ログイン情報カードの .pdf ファイルを公開しています。  
次のリンクから直接ファイルをダウンロードできます。  
[初期ログイン情報カード](../../../raw/main/os/login_20221003.pdf)

piprotect-bullseye-lite-20221003 以降のリリースでは初期ユーザーが変更されています。  
2022/10/3 より前に出荷された製品の初期ログイン情報カードは次のリンクからダウンロードできます。  
[旧初期ログイン情報カード（20221003リリース前）](../../../raw/main/os/login.pdf)

## リリースノート
Pi-protect 用 microSD カードにインストールされている OS イメージのリリースノートを公開しています。

* ### piprotect-bookworm-lite-arm64-20240327
  2024/03/27  以降に出荷された製品には本リリースの OS イメージがインストールされています。  
  詳細は、[piprotect-bookworm-lite-arm64-20240327.md](./piprotect-bookworm-lite-arm64-20240327.md) を参照してください。

* ### piprotect-bookworm-lite-arm64-20240222
  2024/02/22  以降に出荷された製品には本リリースの OS イメージがインストールされています。  
  詳細は、[piprotect-bookworm-lite-arm64-20240222.md](./piprotect-bookworm-lite-arm64-20240222.md) を参照してください。

* ### piprotect-bullseye-lite-armhf-20230511
  2023/05/11  以降に出荷された製品には本リリースの OS イメージがインストールされています。  
  詳細は、[piprotect-bullseye-lite-armhf-20230511.md](./piprotect-bullseye-lite-armhf-20230511.md) を参照してください。

* ### piprotect-bullseye-lite-armhf-20230403
  2023/04/03  以降に出荷された製品には本リリースの OS イメージがインストールされています。  
  詳細は、[piprotect-bullseye-lite-armhf-20230403.md](./piprotect-bullseye-lite-armhf-20230403.md) を参照してください。

* ### piprotect-bullseye-lite-armhf-20221124
  2022/11/24  以降に出荷された製品には本リリースの OS イメージがインストールされています。  
  詳細は、[piprotect-bullseye-lite-armhf-20221124.md](./piprotect-bullseye-lite-armhf-20221124.md) を参照してください。

* ### piprotect-bullseye-lite-armhf-20221003
  2022/10/03  以降に出荷された製品には本リリースの OS イメージがインストールされています。  
  詳細は、[piprotect-bullseye-lite-armhf-20221003.md](./piprotect-bullseye-lite-armhf-20221003.md) を参照してください。

* ### piprotect-bullseye-lite-20220209
  2022/02/09  以降に出荷された製品には本リリースの OS イメージがインストールされています。  
  詳細は、[piprotect-bullseye-lite-20220209.md](./piprotect-bullseye-lite-20220209.md) を参照してください。

* ### piprotect-bullseye-lite-20220107
  20220107 の記載があるものは本リリースの OS イメージがインストールされています。  
  詳細は、[piprotect-bullseye-lite-20220107.md](./piprotect-bullseye-lite-20220107.md) を参照してください。
