---
layout: single
title: "[プレミアム/QBCore] shiro-foodmenu - オリジナル料理開発・飲食店システム"
description: "FiveM (QBCore) サーバー向け。飲食店のボスがゲーム内でオリジナルメニューを開発・申請できる、超高機能な料理システムの導入マニュアルです。"
---

# 🍳 [QBCore] shiro-foodmenu - オリジナル料理開発・飲食店システム

![Banner Image](https://dunb17ur4ymx4.cloudfront.net/packages/images/0414f81695cad72ba1c41a79dbf51cbb9720eb0b.jpg)

> 🎁 **Notice**: 本スクリプトは FiveM Asset Escrow にて安全に暗号化保護されています。

<br>
<a href="https://shiro-development.tebex.io/package/7504706" style="display: inline-block; padding: 12px 28px; background-color: #2b2b2b; color: #d4af37; text-decoration: none; border-radius: 2px; font-weight: bold; border: 1px solid #555; box-shadow: 0 4px 6px rgba(0,0,0,0.3);">👉 Tebex Storeで購入する</a>
<br><br>

`shiro-foodmenu` は、飲食店のボス（店長）などのプレイヤーが、**ゲーム内で独自の料理や飲み物を開発し、サーバーに申請できる**高度な飲食店向けシステムです。
プレイヤーの「自分だけのメニューを作りたい！」というロールプレイを叶えつつ、サーバー運営の負担を極限まで減らす設計になっています。

---

* 目次
{:toc}

---

## 🎥 プレビュー動画 (Preview)
実際のゲーム内UIや開発申請の様子はこちらからご覧ください。

<br>
<a href="https://youtu.be/VFewOHetsJ0?si=aNWv6VNtWOcLZkHb" style="display: inline-block; padding: 12px 28px; background-color: #cc0000; color: #ffffff; text-decoration: none; border-radius: 2px; font-weight: bold; box-shadow: 0 4px 6px rgba(0,0,0,0.3);">▶️ YouTubeでプレビュー動画を見る</a>
<br><br>

---

## ✨ サーバー管理者に選ばれる理由（主な機能）

### 🛠️ 管理者の負担は「実質ゼロ」
従来、新しい料理を追加するにはLuaやデータベースの書き換えが必要でした。本スクリプトではプレイヤーがゲーム内で料理を申請するため、管理者の作業は**「申請を承認する」ことと「アイテム画像を1枚追加する」ことのみ**です！

### 📝 ゲーム内UIによる直感的な料理開発システム
飲食店のボスは、専用UIから「料理名」「説明文」「回復効果」「必要な素材アイテム」などを自由に設定し、オリジナルメニューとして開発申請を出せます。

### 📦 標準メニューとオリジナルメニューの完全分離
各ジョブにあらかじめ用意された「標準メニュー」と、データベースに保存されて増えていく「オリジナルメニュー」の2層構造を採用し、店舗ごとに特色のある経営が可能です。

### 🛡️ チーターを許さない強固なセキュリティ
* **増殖バグ（Dupe）対策:** クラフト時にマイナス値を入力する等のチートを完全ブロック。
* **XSS保護:** UIへの悪意あるHTML/JSタグの埋め込みを防止するサニタイズ処理。
* **サーバーサイド検証:** 回復効果の処理をサーバー側で行い、チーターによる不正なステータス回復を完全に遮断します。

### 🔗 マルチインベントリ＆ターゲット対応
主要なインベントリ（`qb-inventory`, `ox_inventory`, `lj-inventory` 等）の画像パスに柔軟に対応。また、`qb-target` と `ox_target` の両方をネイティブサポートしています。

### 💬 Discord Webhook リアルタイム通知
新しい料理が申請された際、Discordの指定チャンネルにリッチな埋め込み（Embed）通知を自動送信します。

---

## 📋 必須リソース (Dependencies)

本スクリプトの動作には以下の前提リソースが必要です。
* `qb-core` (最新のコアオブジェクト推奨)
* `oxmysql` (データベース接続用)
* `qb-target` または `ox_target`
* お使いのインベントリシステム (`qb-inventory`, `ox_inventory` など)

---

## 🚀 導入手順 (Installation)

1. **データベースのセットアップ**
   同梱されている `custom_recipes.sql` ファイルを、お使いのデータベース（HeidiSQLやphpMyAdminなど）で実行（インポート）します。
2. **リソースの配置**
   ダウンロードした `shiro-foodmenu` フォルダを、サーバーの `resources` フォルダ内に配置します。
3. **Configの設定**
   `config.lua` を開き、ご自身のサーバー環境に合わせてインベントリのパスやDiscord WebhookのURLを設定します。
4. **サーバー起動設定**
   `server.cfg` を開き、以下の記述を追記します。
   *(※必ず `qb-core` 等のコアシステムよりも**後**に読み込まれるように記述してください)*
```cfg
ensure shiro-foodmenu
