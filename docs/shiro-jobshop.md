---
layout: single
title: "[プレミアム/QBCore] shiro-jobshop - プレイヤー主導型ジョブショップシステム"
description: "FiveM (QBCore) サーバー向け。プレイヤー自身が店舗の在庫や価格を管理し、売上の引き出しまで行える、高機能で洗練されたジョブショップシステムの導入マニュアルです。"
---

# 🏪 [QBCore] shiro-jobshop - プレイヤー主導型ジョブショップシステム

![Banner Image](https://dunb17ur4ymx4.cloudfront.net/packages/images/9e3dab6f4e0c61f8d21c6c15013126d47290ad8c.png)

> 🎁 **Notice**: 本スクリプトは FiveM Asset Escrow にて安全に暗号化保護されています。（Config、UI、言語ファイルは自由に編集可能です）

<br>
<a href="https://shiro-development.tebex.io/" style="display: inline-block; padding: 12px 28px; background-color: #2b2b2b; color: #d4af37; text-decoration: none; border-radius: 2px; font-weight: bold; border: 1px solid #555; box-shadow: 0 4px 6px rgba(0,0,0,0.3);">👉 Tebex Storeで購入する</a>
<br><br>

`shiro-jobshop` は、特定のジョブに就いているプレイヤーが、**自身のインベントリからお店に在庫を補充し、自由に価格を設定して販売できる**画期的なジョブショップシステムです。
プレイヤー間の経済活動を活性化させ、「自分たちで店を回している」というリアルなロールプレイ体験を提供します。

---

* 目次
{:toc}

---

## 🎥 プレビュー動画 (Preview)
実際のゲーム内UIや、在庫追加・購入の様子はこちらからご覧ください。

<br>
<a href="https://ご自身のYouTubeリンクを入れてください" style="display: inline-block; padding: 12px 28px; background-color: #cc0000; color: #ffffff; text-decoration: none; border-radius: 2px; font-weight: bold; box-shadow: 0 4px 6px rgba(0,0,0,0.3);">▶️ YouTubeでプレビュー動画を見る</a>
<br><br>

---

## ✨ サーバー管理者に選ばれる理由（主な機能）

### 💼 プレイヤー主導の完全な経済サイクル
指定されたジョブの従業員は、専用の「お店の管理」タブにアクセス可能。手持ちのアイテムを在庫として補充し、需要に合わせてワンクリックで販売価格を変更できます。売上はUIにリアルタイムで反映され、ジョブ口座または個人の銀行口座へ即座に送金可能です。

### 🎨 サーバーの世界観に合わせる「選べるUIテーマ」
UIデザインはConfigから一瞬で切り替え可能。
* **Cute テーマ:** ポップで親しみやすい丸みを帯びたデザイン。
* **Dark テーマ:** GTAのアンダーグラウンドな世界観にマッチする、マットな質感とゴールドのアクセントを取り入れたラグジュアリーなデザイン。

### 🛡️ 徹底されたチート・不正対策
* **マイナス値ブロック:** 購入数や補充数にマイナスの数値を入力してお金を増殖させる（Dupe）手法を完全に遮断。
* **権限チェック:** イベント実行時にサーバーサイドでジョブ権限を再確認し、悪意あるNUIポストによる価格改ざんや不正アクセスを防ぎます。
* **BIGINT対応:** 経済がインフレしているサーバーでもエラーが起きないよう、数十億ドルの取引にも耐えうるデータベース構造を採用。

### 🔗 驚異の互換性とカスタマイズ性
環境に合わせて `config.lua` を書き換えるだけで、様々な外部スクリプトと連携します。
* **インベントリ:** `qb-inventory`, `ox_inventory` に対応。
* **銀行システム:** `okokBanking`, `qb-management`, `Renewed-Banking` に対応（売上の入金先をジョブ口座か個人口座か選択可能）。
* **アクセス方式:** 従来の「3Dテキスト＋マーカー（色変更可能）」と、モダンな「`qb-target` / `ox_target`」の両方をネイティブサポート。

### 🌍 マルチ言語対応 (Multi-Language)
標準で「日本語 (ja)」と「英語 (en)」の翻訳ファイルを同梱。Configで指定するだけでUIから通知まで一括で切り替わります。

---

## 📋 必須リソース (Dependencies)

本スクリプトの動作には以下の前提リソースが必要です。
* `qb-core` (最新のコアオブジェクト推奨)
* `oxmysql` (データベース接続用)
* お使いのインベントリシステム (`qb-inventory` または `ox_inventory`)
* **[任意]** お使いの銀行スクリプト (`okokBanking`, `qb-management`, `Renewed-Banking` 等)
* **[任意]** `qb-target` または `ox_target` (ターゲットシステムを使用する場合)

---

## 🚀 導入手順 (Installation)

1. **データベースのセットアップ**
   同梱されている `playershop.sql` ファイルを、お使いのデータベース（HeidiSQLやphpMyAdminなど）で実行（インポート）します。
2. **リソースの配置**
   ダウンロードした `shiro-jobshop` フォルダを、サーバーの `resources` フォルダ内に配置します。
3. **Configの設定**
   `config.lua` を開き、ご自身のサーバー環境に合わせてインベントリのシステム、銀行システム、ターゲットの使用有無などを設定します。
   （デフォルトでは `mechanic` と `burger` のショップがサンプルとして用意されています）
4. **サーバー起動設定**
   `server.cfg` を開き、以下の記述を追記します。
   *(※必ず `qb-core` や `oxmysql` 等のコアシステムよりも**後**に読み込まれるように記述してください)*
   ```cfg
   ensure shiro-jobshop
   ```
---
## ⚠️ 導入時の注意点 (Important Notes)

* **データベースの実行忘れにご注意ください**
  サーバーを起動する前に、必ず同梱の `playershop.sql` をデータベースにインポートしてください。テーブルが存在しない場合、購入や在庫追加時にエラースパムが発生します。
* **ジョブ名・アイテム名の完全一致**
  `config.lua` で設定するジョブ名（`job`）やアイテム名（`allowedItems` 内のキー）は、サーバーに登録されている正確なID（システム名）を指定してください。存在しないアイテムを指定するとUIが正常に開かない場合があります。
* **画像パスの正しい設定**
  お使いのインベントリ（`qb-inventory` や `ox_inventory` 等）に合わせて、Configの `InventoryImageRoute` のパスを正しく設定してください。パスが間違っているとアイテムの画像が透明（非表示）になります。
* **スクリプトの起動順序**
  `server.cfg` では、必ず `qb-core` や `oxmysql` などの前提リソースが読み込まれた**後**に `ensure shiro-jobshop` を記述してください。
---

## 💬 サポート & その他のスクリプト
サポートやバグ報告、その他高品質なスクリプトについては、DiscordおよびTebexストアをご確認ください！

* **Tebex Store:** [https://shiro-development.tebex.io/](https://shiro-development.tebex.io/)
* **Discord サポート:** [https://discord.com/invite/yXdqRYFnFF](https://discord.com/invite/yXdqRYFnFF)

© 2026 Shiro. All rights reserved.
