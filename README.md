# Qiita記事管理

Qiita CLIを使った記事管理リポジトリ。GitHub Actionsで自動公開する。

## 構成

```
qiita/
├── CLAUDE.md               # プロジェクト共通ルール
├── KNOWLEDGE.md            # 記事執筆・運用の学び
├── TODO.md                 # タスク管理
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
│   └── workflows/          # GitHub Actionsで自動公開
├── package.json
└── README.md
```

`images/`と`samples/`のディレクトリ名は`public/`の記事ファイル名（拡張子なし）と揃える。

## セットアップ

1. VS Codeで本ディレクトリを開く
2. コマンドパレット → 「Dev Containers: Reopen in Container」
3. コンテナ内で `npx @qiita/qiita-cli init` を実行
