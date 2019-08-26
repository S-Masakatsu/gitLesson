# GitLesson

## ■ gitとは

バージョン管理システム  

- 公式サイト  
    [git](https://git-scm.com/)
- 必要知識  
    - Linux
    - コマンド

## バージョン管理の流れ

1. ファイル作成・修正
1. ある程度のまとまりにする
1. 履歴データベースの保存する

---

1. 作業ディレクトリ
1. ステージングエリア(index)
    作業経過を保存しておく
1. リポジトリ(ローカル・リモート)

## ■ gitの設定

``` shell
# 設定
$git config --global user.name "Name"
$git config --global user.email "E-Mail"
# 任意
$git config --global color.ui true
# 確認
$git config -l
```

- ヘルプ

``` shel
$git config --help
$git help config
```

