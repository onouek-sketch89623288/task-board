# task-board — タスク管理ボードアプリ

## プロジェクト概要

HTML/CSS/JavaScriptで構築するタスク管理ボードアプリ（いわゆるカンバンボード）。
バニラJSのみで実装し、ドラッグ＆ドロップによるタスク移動などを提供する。

## 技術スタック

| ライブラリ／ツール | バージョン | 用途 |
|---|---|---|
| React | ^18.3.1 | UIコンポーネント |
| React DOM | ^18.3.1 | DOMレンダリング |
| Vite | ^6.0.0 | 開発サーバー・ビルド |
| @vitejs/plugin-react | ^4.3.4 | JSX変換（Babel） |

- 状態管理：React 組み込みの `useState` / `useEffect`（外部ライブラリ不使用）
- データ永続化：`localStorage`
- スタイリング：プレーン CSS（CSS Modules・Tailwind 等は使用しない）

## ディレクトリ構成

```
task-board/
├── index.html                  # エントリーポイント
├── vite.config.js              # Vite設定
├── package.json
├── css/
│   └── style.css               # グローバルスタイル
├── js/
│   ├── main.jsx                # ReactDOMマウント
│   └── App.jsx                 # 全コンポーネント定義
└── .github/
    └── workflows/
        └── deploy.yml          # GitHub Pagesデプロイ
```

## コンポーネント命名規約

### ファイル名
- コンポーネントを含むファイルは `.jsx` 拡張子を使う
- ファイル名はコンポーネント名と一致させる（例: `App.jsx`）

### コンポーネント名
- **PascalCase** を使う（例: `TaskItem`、`TaskList`）
- 機能を表す名詞または「名詞＋役割」の形にする

### 現在のコンポーネント構成

```
App                    # ルート。state管理とロジックを担う
├── TaskInput          # テキスト入力フォーム。タスク追加のみ担当
└── TaskList           # タスク一覧の描画
    └── TaskItem       # 個々のタスク（チェックボックス・削除ボタン）
```

### props命名
- イベントハンドラは `on` プレフィックスを使う（例: `onAdd`、`onToggle`、`onDelete`）
- 真偽値は `is` / `has` プレフィックスを使う（例: `isCompleted`）

## 開発ルール

- React以外の外部ライブラリは使用しない
- ファイルはすべてUTF-8（BOMなし）で保存する
- CSSはモバイルファーストで記述する
- JavaScriptは`const`/`let`を使い、`var`は使わない
- 関数は単一責任の原則に従い小さく保つ

## Git運用ルール

コードを変更するたびに、以下の手順でGitHubへプッシュする。

1. 変更をステージングする
   ```bash
   git add <変更ファイル>
   ```
2. コミットメッセージをつけてコミットする
   ```bash
   git commit -m "変更内容を端的に記述したメッセージ"
   ```
3. リモートリポジトリへプッシュする
   ```bash
   git push origin main
   ```

- コミットメッセージは日本語でも英語でもよいが、変更内容が一目でわかる粒度にする
- 1つの意味ある変更ごとに1コミットを心がける（大きすぎる差分をまとめてコミットしない）
- プッシュ前に `git status` と `git diff` で差分を確認する

## 禁止事項

- `package.json` の依存パッケージを無断で追加・変更しない
- `.env` ファイルを読んだり変更したりしない

## GitHubリポジトリ

https://github.com/onouek-sketch89623288/task-board

## デプロイ先

https://onouek-sketch89623288.github.io/task-board/
