# Qiita記事管理

Qiita CLIを使った記事管理リポジトリ。GitHub Actionsで自動公開する。

## 構成

```
qiita/
├── CLAUDE.md               # Claudeへの指示・ルール
├── KNOWLEDGE.md            # 記事執筆・運用の学び
├── TODO.md                 # タスク管理
├── _template.md            # 記事テンプレート
├── public/                 # Qiita CLI管理（記事はフラットに配置）
│   ├── aws-lambda-dynamodb.md
│   └── ...
├── images/                 # 画像（記事ごとにディレクトリ）
│   ├── aws-lambda-dynamodb/
│   └── ...
├── samples/                # サンプルコード（記事ごとにディレクトリ）
│   ├── aws-lambda-dynamodb/
│   └── ...
├── .devcontainer/          # Dev Container設定
│   └── devcontainer.json
├── .github/
│   └── workflows/          # GitHub Actions
└── package.json
```

`images/`と`samples/`のディレクトリ名は`public/`の記事ファイル名（拡張子なし）と揃える。

## 記事公開のワークフロー

```
ブランチ作成 → 記事を書く → PR作成 → mainにマージ → Qiitaに公開
```

| タイミング | 何が起きるか | 公開される？ |
|---|---|---|
| ブランチで作業中 | 何も起きない | No |
| PRを作成 | **preview.yml**: 変更記事の一覧がJob Summaryに表示 | No |
| mainにマージ | **publish.yml**: `public/`の記事がQiitaに公開・更新 | **Yes** |

mainへの直pushはブランチ保護で禁止されている。必ずPR経由で行う。

### 記事の公開/非公開の制御

記事ファイルのヘッダーで`published: false`にすれば、mainにマージしても公開されない（下書き状態）。

## フロントマター

記事ファイルの先頭にYAML形式のメタデータを記述する。`_template.md`を参照。

| フィールド | 説明 | 入力 |
|---|---|---|
| title | 記事タイトル | 要入力 |
| tags | タグ（リスト形式） | 要入力 |
| private | true: 限定共有 / false: 公開 | 必要に応じて変更 |
| updated_at | 投稿後に自動設定される | 編集不要 |
| id | 投稿後に自動設定される（新規はnull） | 編集不要 |
| organization_url_name | Organization名（不要ならnull） | 通常そのまま |
| slide | true: スライドモード | 必要に応じて変更 |
| ignorePublish | true: publishコマンドで処理しない | 必要に応じて変更 |

## セットアップ

1. VS Codeで本ディレクトリを開く
2. コマンドパレット → 「Dev Containers: Reopen in Container」
3. コンテナ内で `npx @qiita/qiita-cli init` を実行
4. GitHubリポジトリのSettings → Secrets に `QIITA_TOKEN` を登録

## Claude Code Skills

| コマンド | 説明 |
|---|---|
| `/new-article <slug>` | 記事の雛形を作成（public/, images/, samples/に一括生成） |
