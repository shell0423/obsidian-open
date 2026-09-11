# obsidian-open — Discord通知 → Obsidian ワンタップ中継ページ

Discord に流した通知から Obsidian のノートをワンタップで開くための、GitHub Pages 静的中継ページ。

## なぜ必要か

Discord はメッセージ本文中の `http/https` しか自動リンク化しない（`obsidian://` はプレーンテキスト表示＝タップ不可。2026-07-13 実機確認）。そこで https の本ページを経由し、JS で `obsidian://open?vault=…&file=…` へ転送する。

## 使い方

```
https://shell0423.github.io/obsidian-open/?v=<vault名>&f=<vault相対パス>
例: https://shell0423.github.io/obsidian-open/?v=MyVault&f=notes/2026-01-01
```

- `v`（vault 名）と `f`（vault 相対パス）は呼び出し側が必ず付ける（既定値は持たない）
- 開くと即 `obsidian://` へ自動転送（ブロックされた場合のためボタンとコピー用URIも表示）
- 呼び出し元は自分用の通知スクリプトの deep-link 行

## プライバシー

- 完全に静的（HTML 1枚）。**何も収集・送信・保存しない**（外部リソースの読み込みもゼロ）
- URL のクエリにノートの**パス**（日付・ファイル名）は載るが、ノートの**中身**は一切載らない
- `noindex` 指定済み

## 変更するとき

`index.html` を編集して push するだけ（GitHub Pages が自動デプロイ）。
