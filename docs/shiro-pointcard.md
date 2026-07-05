---
layout: single
title: "[プレミアム/QBCore] shiro-pointcard - マルチ店舗対応ポイントカードシステム"
description: "FiveM (QBCore) サーバー向け。複数店舗のポイントカードを1つのUIに統合し、ゲーム内から店舗情報が編集可能な高機能ポイントカードシステムの導入マニュアルです。"
---

# 💳 [QBCore] shiro-pointcard - マルチ店舗対応 オールインワンポイントカードシステム

![Banner Image](https://dunb17ur4ymx4.cloudfront.net/packages/images/a8f1029417b820761d292233d0a7e7b859dad8ff.jpg)

> 🎁 **Notice**: 本スクリプトは FiveM Asset Escrow にて安全に暗号化保護されています。

<br>
<a href="https://shiro-development.tebex.io/package/7501433" style="display: inline-block; padding: 12px 28px; background-color: #2b2b2b; color: #d4af37; text-decoration: none; border-radius: 2px; font-weight: bold; border: 1px solid #555; box-shadow: 0 4px 6px rgba(0,0,0,0.3);">👉 Tebex Storeで購入する</a>
<br><br>

`shiro-pointcard` は、サーバー内に存在する複数店舗のポイントカードを、1つの洗練された専用アプリUIに統合する次世代のポイントシステムです。

インベントリを大量のカードアイテムで圧迫することなく、プレイヤーは自身のポイント残高をスマートに確認でき、店舗側は安全かつ確実にポイントの付与・減算操作を行うことができます。

---

* 目次
{:toc}

---

## 🎥 プレビュー動画 (Preview)
実際のゲーム内UIや、店員と客のポイント付与のやり取りはこちらからご覧ください。

<br>
<a href="https://youtu.be/JYf2TQXgoJk?si=UKjsAmL9n8IZs1_j" style="display: inline-block; padding: 12px 28px; background-color: #cc0000; color: #ffffff; text-decoration: none; border-radius: 2px; font-weight: bold; box-shadow: 0 4px 6px rgba(0,0,0,0.3);">▶️ YouTubeでプレビュー動画を見る</a>
<br><br>

---

## ✨ サーバー管理者に選ばれる理由（主な機能）

### 📱 オールインワンの洗練されたUI
複数店舗のポイントカード情報が1つのUIにまとまっています。プレイヤーはタブを切り替えるだけで、各店舗の現在のサービス内容や、自分のポイント残高をスムーズに確認できます。

### 📝 【ボス限定】ゲーム内での店舗情報エディター
**サーバー管理者のConfig編集作業はもう必要ありません！**
店舗のボス（店長）は、ゲーム内のUIから直接「現在のサービス内容」や「ポイント特典」のテキストを編集・保存できます。変更内容はデータベースと即座に同期されるため、店舗主導でリアルタイムなキャンペーン等を展開できます。

### 🛡️ ロールプレイを守る強固なチート・不正対策
* **増殖・マイナス値ブロック:** サーバー側の厳格な検証により、不正な数値を入力してポイントを増殖させるチートを完全にブロックします。
* **距離チェック機能（遠隔操作防止）:** 店員とお客様（ターゲット）が一定の距離内にいないとポイント操作ができないよう、サーバー側で保護されています。
* **ジョブ権限の厳密な確認:** アクションの実行者が「本当にその店舗の従業員（指定ジョブ）であるか」をサーバー側でチェックし、権限のないプレイヤーによる不正操作を防ぎます。

### 🌐 完全日本語対応 ＆ UIカスタマイズ可能
メッセージやUIは標準で日本語に対応（英語への切り替えも可能）。スクリプトの根幹ロジックは保護されていますが、Config、言語ファイル、UI（HTML/CSS/JS）は自由にカスタマイズ可能です。

---

## 📋 必須リソース (Dependencies)

本スクリプトの動作には以下の前提リソースが必要です。
* `qb-core`
* `oxmysql` (データベース接続用)

---

## 🚀 導入手順 (Installation)

1. **データベースのセットアップ**
   同梱されている `pointcards.sql` ファイルを、お使いのデータベース（HeidiSQLやphpMyAdminなど）で実行（インポート）します。
2. **アイテムの追加（※オプション）**
   Config設定で `Config.UseItem = true` （アイテムとして使用する）に設定する場合は、お使いのコアのアイテムリスト（例: `qb-core/shared/items.lua`）に `pointwallet` というアイテムを追加してください。
3. **サーバー起動設定**
   `server.cfg` を開き、以下の記述を追記します。
```cfg
ensure shiro-pointcard
