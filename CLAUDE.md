# task-board

タスク管理ボードのWebアプリケーション。

## デプロイ先

https://yns1number-bit.github.io/task-board/

`main` ブランチへのプッシュで GitHub Actions が自動デプロイする。

## プロジェクト概要

React + Vite で構築したシンプルなタスクボードアプリ。タスクの追加・完了・削除ができ、localStorage でデータを永続化する。

## 技術スタック

- フレームワーク: React 18
- ビルドツール: Vite 6
- パッケージマネージャ: npm
- スタイリング: CSS Modules なし（グローバル CSS: `App.css` / `index.css`）
- データ永続化: localStorage
- デプロイ: GitHub Pages（GitHub Actions 経由）

## 開発コマンド

```bash
# 依存関係インストール
npm install

# 開発サーバー起動
npm run dev

# ビルド
npm run build

# テスト
npm test

# Lint
npm run lint
```

## Git 運用ルール

**コードを変更するたびに、必ず以下の手順でGitHubへプッシュすること。**

### 変更ごとの必須フロー

1. 変更内容を確認する
   ```bash
   git diff
   git status
   ```

2. 変更ファイルをステージングする（機密ファイル `.env` 等は除く）
   ```bash
   git add <変更ファイル>
   ```

3. コミットメッセージは「なぜ変えたか」を端的に書く
   ```bash
   git commit -m "変更内容の要約"
   ```

4. **GitHub へ即プッシュする**
   ```bash
   git push origin <現在のブランチ>
   ```

### ブランチ戦略

- `main` — リリース済みの安定版。直接コミット禁止。
- `develop` — 統合ブランチ。機能が揃ったら `main` へマージ。
- `feature/<機能名>` — 機能開発ブランチ。完成したら `develop` へ PR を作成。
- `fix/<バグ名>` — バグ修正ブランチ。

### コミットメッセージ規約

```
<type>: <要約（日本語可）>

type 一覧:
  feat     新機能
  fix      バグ修正
  refactor リファクタリング（動作変更なし）
  style    フォーマット・コードスタイルのみの変更
  test     テスト追加・修正
  docs     ドキュメントのみの変更
  chore    ビルド設定・依存関係の更新等
```

### 禁止事項

- `--no-verify` でフックをスキップしない
- `git push --force` を `main` / `develop` に対して実行しない
- `.env` やシークレットキーをコミットしない

## コーディング規約

- コメントは「なぜ」が非自明な箇所のみ書く（「何をしているか」は書かない）
- 型は可能な限り明示する
- 1 PR = 1 目的（複数の変更を混ぜない）

## コンポーネント命名規約

- コンポーネントファイル名・関数名ともに **PascalCase**（例: `TaskItem.jsx`, `export default function TaskItem`）
- カスタムフックは **`use` プレフィックス + camelCase**（例: `useTasks.js`）
- イベントハンドラは **`handle` プレフィックス + camelCase**（例: `handleKeyDown`, `handleAddTask`）
- CSS クラス名は **kebab-case**（例: `.task-list`, `.input-row`）

## ディレクトリ構成

```
task-board/
├── src/
│   ├── components/   # UIコンポーネント
│   ├── pages/        # ページ
│   ├── hooks/        # カスタムフック
│   ├── lib/          # ユーティリティ・API呼び出し
│   └── types/        # 型定義
├── public/
├── CLAUDE.md
└── package.json
```
