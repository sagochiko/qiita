---
name: new-article
description: 新しいQiita記事の雛形を作成する
disable-model-invocation: true
arguments:
  - name: slug
    description: 記事のスラッグ（ファイル名、拡張子なし）
    required: true
---

# 新しい記事を作成する

以下の手順で記事の雛形を作成する。

1. `_template.md` を `public/<slug>.md` にコピーする
2. `images/<slug>/` ディレクトリを作成する
3. `samples/<slug>/` ディレクトリを作成する
4. 作成したファイルのパスを表示する
