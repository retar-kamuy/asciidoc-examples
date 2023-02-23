# AsciiDoc

## Asciidoctorで図キャプションを図に合わせる
[https://qiita.com/momoyamas/items/598c5a7fd181234f015b](https://qiita.com/momoyamas/items/598c5a7fd181234f015b)

## asciidoctor-pdf で図と図タイトルを中央寄せにする
* image と caption の align を center にする。
```yml
extends: default
image:
  align: center
caption:
  align: center
```

## asciidoctor-pdf 
* 以下コマンドオプションを付けてエクスポートする。
* [default-with-font-fallbacks-theme.yml](https://github.com/asciidoctor/asciidoctor-pdf/blob/main/data/themes/default-with-fallback-font-theme.yml) の内容を theme に記述することでも対応できる。
```sh
asciidoctor-pdf Document.adoc -a scripts=cjk -a pdf-theme=default-with-fallback-font
```



## スタイルシートの適用方法
* github.css をプレビューへ適用することで、プレビュー背景を白色にできる。
* 以下のリポジトリの css から適用したいスタイルシートをコピーする。
[https://github.com/darshandsoni/asciidoctor-skins](https://github.com/darshandsoni/asciidoctor-skins)

* html へのエクスポート時に stylesheet オプションを付けることでスタイルシートを反映できる。
```sh
asciidoctor -a stylesheet=css/adoc-github.css sample.adoc
```

* VS Code プレビューへスタイルシートを反映させるには settings.json へ以下を設定する。
```json
{
    "asciidoc.preview.style": "css/adoc-github.css"
}
```

## キャプションの日本語化
* 以下を設定する。

```adoc
:figure-caption: 図
:table-caption: 表
:example-caption: 例
```

## 目次の自動作成と章題へ番号を付ける

```adoc
:toc:
:sectnums: // '==' で記載した章題へ番号を付ける
:toclevels: 5
:toc-title: 目次
```