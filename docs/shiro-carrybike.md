---
layout: single
title: "[無料/QBCore] shiro-carrybike - リアルな自転車持ち運びスクリプト"
description: "FiveM (QBCore) サーバー向け。自転車を担いだまま車に搭乗可能な、完全無料の超軽量自転車持ち運びスクリプトの導入マニュアルです。"
---

# 🚲 [無料/QBCore] shiro-carrybike - リアルな自転車持ち運びスクリプト

![Banner Image](https://dunb17ur4ymx4.cloudfront.net/packages/images/5e25bc2efc135b5a7be0dab2b294ed30c85a42f0.jpg)

> 🎁 **Notice**: このスクリプトは**無料（FREE）**でご利用いただけます。まずは当ストアの品質と「圧倒的な軽さ」をお試しください！

<br>
<a href="https://shiro-development.tebex.io/" style="display: inline-block; padding: 12px 28px; background-color: #2b2b2b; color: #d4af37; text-decoration: none; border-radius: 2px; font-weight: bold; border: 1px solid #555; box-shadow: 0 4px 6px rgba(0,0,0,0.3);">👉 Tebex Storeでプレミアムスクリプトを見る</a>
<br><br>

FiveM (QBCore) サーバーのロールプレイの質を劇的に向上させる、シンプルで超軽量な自転車持ち運びスクリプトです。

---

* 目次
{:toc}

---

## 🎥 プレビュー動画 (Preview)
実際の動作の様子はYouTubeでご確認いただけます。

<br>
<a href="https://www.youtube.com/@ShiroDevelopment" style="display: inline-block; padding: 12px 28px; background-color: #cc0000; color: #ffffff; text-decoration: none; border-radius: 2px; font-weight: bold; box-shadow: 0 4px 6px rgba(0,0,0,0.3);">▶️ ShiroDevelopment 公式YouTubeで動画を見る</a>
<br><br>

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
