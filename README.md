# Instantale Output Viewer

https://flossian.github.io/instantale-output-viewer/

ゲーム『Instantale』が出力する `output_data` フォルダ内の JSON
（LLM の入出力ログ）を、ブラウザ上で**分類・閲覧・検索**するためのビューアです。

`output_data` は次の階層構造を前提とします:

```
output_data/
├─ <ワールド名>/
│  └─ <キャラクター名>/
│     └─ <カテゴリ名>/        例: narrator, create_character, conversation_facilitator ...
│        ├─ 1.json
│        ├─ 2.json
│        └─ ...
```

各 JSON は `messages`（LLM への入力。role 別の会話）と `response`（出力）を持ちます。

> ⚠️ このリポジトリには **データ（`output_data` の JSON）は含まれていません**。
> 各自の手元にある `output_data` を読み込んで使用してください。

---

## 主な機能

- **ツリー絞り込み**: ワールド → キャラクター → カテゴリ（各階層に件数表示）
  - 最上部の「すべて表示」でいつでも選択を解除して全件に戻せます
- **一覧**: 各 JSON の `response` から自動抽出した 1 行プレビュー
- **タイムライン**: output 全体（または選択中の範囲）をファイルの更新日時順に並べて閲覧
  - 「新しい順 / 古い順」をワンクリックで切り替え
  - 全文検索やツリーでの絞り込みと併用可能
- **詳細表示**: `messages` を role 別（system / user / assistant）に色分け表示
  - 長文（300字超）は折り畳み。ヘッダのクリックで開閉、「全て展開／折りたたむ」も可
  - `response` も整形表示＆折り畳み対応
- **全文検索**: `messages` と `response` の本文まで対象（カテゴリ名も）
- **ダッシュボード**: 総数カード＋ワールド別／カテゴリ別の件数バーチャート（クリックで絞り込み）

---

## 使い方

### A. ブラウザで直接開く（おすすめ・ダウンロード不要）

GitHub Pages で公開しているので、次のURLを開くだけで使えます:

**<https://flossian.github.io/instantale-output-viewer/>**

1. 上記URLをブラウザで開く（**Chrome / Edge / Firefox / Safari** など主要ブラウザに対応）。
2. 「📁 output_data フォルダを選択」を押し、自分の `output_data` フォルダを選ぶ。

> HTTPS 配信のため File System Access API も問題なく動作します。
> ページのコード以外は何も読み込まれず、**`output_data` の中身は外部に送信されません**（すべてブラウザ内で処理）。

### B. ファイルをローカルで開く（オフライン）

1. `index.html` をダウンロード（または Release のzipを解凍）して、好きな場所に置く。
2. `index.html` をブラウザで開く。
3. 「📁 output_data フォルダを選択」を押し、自分の `output_data` フォルダを選ぶ。

- Python 不要・サーバ不要。データは外部に送信されません（すべてブラウザ内で処理）。
- Chrome / Edge では File System Access API を、Firefox / Safari などでは
  `<input webkitdirectory>` によるフォルダ選択を自動で使い分けます。
- データが更新されたら、フォルダを選び直すだけで最新が反映されます。

---

## 注意

- ゲームのプロンプト等が含まれるデータの取り扱い・再配布は、ゲームの利用規約に従ってください。
