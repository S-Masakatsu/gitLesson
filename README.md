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

## ■ ０, インストール

- Mac

    ``` shell
    $brew install git
    ```

- Windows  
    [https://gitforwindows.org](https://gitforwindows.org)からmsysgitの最新版のインストール

## ■ git Lesson１

---

## ● 1-1, gitの設定

- コミット時のAuthorの変更

    ``` shell
    # 設定
    $git config --global user.name "<任意のユーザ名>"
    $git config --global user.email "<任意のメールアドレス>"
    ```

- 出力を色付けしてくれる設定

    ``` shell
    # 任意
    $git config --global color.ui true
    ```

- 安全対策

    ``` shell
    $git config --global push.default current
    ```

- 設定の確認 => `-l`オプション使用

    ``` shell
    $git config -l
    $git config -l --global
    ```

- ヘルプ

    ``` shell
    $git config --help
    # もしくは
    $git help config
    ```

