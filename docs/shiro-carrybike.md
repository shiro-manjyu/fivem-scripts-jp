# 🚲 [無料/QBCore] shiro-carrybike - リアルな自転車持ち運びスクリプト

![Banner Image](https://dunb17ur4ymx4.cloudfront.net/packages/images/5e25bc2efc135b5a7be0dab2b294ed30c85a42f0.jpg)

> 🎁 **Notice**: このスクリプトは**無料（FREE）**でご利用いただけます。まずは当ストアの品質と「圧倒的な軽さ」をお試しください！
> 👉 **[Tebex Storeで他のプレミアムスクリプトを見る](https://shiro-development.tebex.io/)**

FiveM (QBCore) サーバーのロールプレイの質を劇的に向上させる、シンプルで超軽量な自転車持ち運びスクリプトです。

## 🎥 プレビュー動画 (Preview)
実際の動作の様子はYouTubeでご確認いただけます。
👉 [ShiroDevelopment 公式YouTube](https://www.youtube.com/@ShiroDevelopment)

---

## 🌟 主な特徴 (Features)

* **🔥 担いだまま車に搭乗可能！**: 自転車を担いだ状態のまま車に乗り込み、運転することが可能です。輸送や移動の手間を省き、より自由なRPを実現します。
* **🔒 鍵の状態を自動判定**: 鍵がかかっている自転車は担ぐことができない、リアルな仕様を搭載しています。
* **👁️ 直感的なサードアイ操作**: `qb-target` に完全対応しており、自然な動作で自転車の持ち運びが可能です。
* **🏃 アクション制限機能**: 重い自転車を担いでいる間の「ダッシュ」や「ジャンプ」を制限するかどうかをConfigで自由に設定できます。
* **⚡ 圧倒的な軽量化 (0.00ms)**: サーバーサイドのループ処理を排除したクライアント完結型。アイドル時の負荷は 0.00ms と、サーバーに全く負担をかけません。
* **⚙️ 自由なカスタマイズ**: `config.lua` から、持ち上げ時の位置・角度（Offset）、許可する自転車のモデル、ターゲット時のラベルテキストなどを簡単に調整できます。

---

## 🛠 必須環境 (Dependencies)

このスクリプトを動かすには、以下の前提リソースが必要です。
* [qb-core](https://github.com/qbcore-framework/qb-core)
* [qb-target](https://github.com/qbcore-framework/qb-target)

---

## 📖 導入手順 (Installation)

1. リソースをダウンロードし、サーバーの `resources` フォルダに配置します。
2. サーバーの `server.cfg` を開き、以下の1行を追記します。
```cfg
ensure shiro-carrybike
```
3. サーバーを再起動、またはコンソールで `refresh` 実行後に `start shiro-carrybike` を入力すれば導入完了です。

---

## 💬 サポート & コミュニティ

導入時のエラー報告や、その他のハイクオリティなスクリプトについては、公式DiscordおよびTebexストアをご確認ください。

* 🛒 **Tebex Store:** [Shiro Development](https://shiro-development.tebex.io/)
* 💬 **Discord Support:** [コミュニティに参加する](https://discord.com/invite/yXdqRYFnFF)

---
*(関連キーワード: FiveM, QBCore, 自転車, 持ち運び, 無料スクリプト, qb-target, ロールプレイ, サーバー最適化)*
