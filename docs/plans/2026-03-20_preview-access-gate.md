# プレビュー用アクセスゲート（localStorageベース）

## 概要

オープン前の修正段階として `index.html` を一般訪問者から非表示にし、`admin.html` でトークン入力済みのブラウザでのみ通常表示する。

## 仕組み

- `admin.html` が `localStorage` に保存する `gh_admin_token` を `index.html` がチェック
- トークンあり → `body` の `visibility: hidden` を解除、通常ページ表示
- トークンなし → 「ただいま準備中です」メンテナンス画面を表示

## 変更箇所（index.html 内の3ブロック）

1. `<!-- PREVIEW GATE CSS -->` — body非表示 + メンテナンス画面スタイル
2. `<!-- PREVIEW GATE SCREEN -->` — メンテナンス画面HTML
3. `<!-- PREVIEW GATE SCRIPT -->` — localStorage判定ロジック
4. `<body class="pg-main-content">` — ゲート用クラス

## オープン時の解除手順

1. 上記3つのコメントブロックを削除
2. `<body class="pg-main-content">` を `<body>` に戻す
