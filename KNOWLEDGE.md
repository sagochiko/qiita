# ナレッジ

Qiita記事執筆・運用で得た学びを蓄積する。

## Qiita CLI
- 記事は`public/`直下にフラットに配置する（サブディレクトリは非対応の可能性が高い）
- 画像はQiitaサーバーにアップロードしてURL参照する方式。ローカルの`images/`はバックアップ・整理用
- `npx qiita publish --all` で全記事を一括公開・更新できる
- `npx @qiita/qiita-cli init` で初期化すると`.github/workflows/publish.yml`も自動生成される（今回は先に手動作成済み）

## GitHub
- GitHub Freeではプライベートリポジトリにブランチ保護を設定できない
- 記事リポジトリはパブリックで問題ない（記事自体が公開前提）
- ブランチ保護はRulesets APIで設定可能
