# GitLesson

<h2 id="contents-list">■ 項目</h2>

- __<a href="#ttl">gitとは</a>__
- __<a href="#ttl0">インストール</a>__
- __<a href="#ttl1">git Lesson１</a>__

---

<h2 id="ttl">■ gitとは</h2>

バージョン管理システム  

- 公式サイト  
    [git](https://git-scm.com/)
- 必要知識  
    - Linux
    - コマンド

### バージョン管理の流れ

1. ファイル作成・修正
1. ある程度のまとまりにする
1. 履歴データベースの保存する

---

1. 作業ディレクトリ
1. ステージングエリア(index)
    作業経過を保存しておく
1. リポジトリ(ローカル・リモート)

<p><a href="#contents-list">↑項目一覧へ</a></p>

<h2 id="ttl0">■ ０, インストール</h2>

- Mac

    ``` shell
    $brew install git
    ```

- Windows  
    [https://gitforwindows.org](https://gitforwindows.org)からmsysgitの最新版のインストール

<p><a href="#contents-list">↑項目一覧へ</a></p>

<h2 id="ttl1">■ git Lesson１</h2>

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

## ● 1-2, gitを使う準備

1. まずはディレクトリを作ろう。

    ``` shell
    $mkdir gitLesson
    $cd gitLesson
    ```

1. gitを使う準備をします。

    ``` shell
    $git init
    ```

これで準備は終了です。  
`git init` で、ファイルの変更や履歴の情報をつかさどる「リポジトリ」が作成される。  
リポジトリは、.gitというディレクトリで管理される。  
つまり.gitを削除するとリポジトリの情報は消えるということ。

## ● 1-3, ファイルを追加する

### コミット

``` shell
$git add .
$git commit -m "コミットメッセージ"
```

ファイルを記録し、履歴として参照できる状態にすることを、**コミット**と言います。  
`commit`の直前に行っている`add`は、ファイルをコミットの対象に追加するという感じ。  
`add`していない修正は、`commit`を実行してもコミットされない。

1. 新規ファイルの作成

    ``` shell
    $echo "Hello git ver2" > Sample02.txt
    ```

1. __コミット__ : Sample.txtをコミット

    ``` shell
    $git add Sample02.txt
    $git commit -m "Add Sample02.txt"
    ```

## ● 1-4, ファイルを修正する

1. ファイルを修正  
    `/Sample.txt` を開いて修正してください。  

1. コミットする

    ``` shell
    $git add Sample.txt
    $git commit -m "Add Sample.txt"
    ```

これで修正したファイルを記録できました。

## ● 1-5, ファイルを削除する

1. ファイルを削除する

``` shell
$rm -i Sample02.txt
```

<p><a href="#contents-list">↑項目一覧へ</a></p>
