# GitLesson

<h1 id="contents-list">■ 項目</h1>

- __<a href="#ttl">gitとは</a>__
- __<a href="#ttl0">インストール</a>__
- __<a href="#ttl1">git Lesson１</a>__

---

<h1 id="ttl">■ gitとは</h1>

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

<h1 id="ttl0">■ ０, インストール</h1>

- Mac

    ``` shell
    $brew install git
    ```

- Windows  
    [https://gitforwindows.org](https://gitforwindows.org)からmsysgitの最新版のインストール

<p><a href="#contents-list">↑項目一覧へ</a></p>

<h1 id="ttl1">■ git Lesson１</h1>

<h2 id="ttl1-1">● 1-1, gitの設定</h2>

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

1. ファイル削除をコミットする

    ``` shell
    $git rm Sample02.text
    $git commit -m "remove Sample02.txt"
    ```

これでファイルを削除し、コミットすることができる。

## ● 1-6, 修正履歴(ログ)を確認する

1. ログを確認する

    ``` shell
    $git log
    ```

    修正履歴(ログ)を確認することができる。  
    ページが１ページで収まらない時は、  
    `スペース`で改ページ、`q` で終了する。

### ● ログの見方

``` shell
commit 5cdb8db1fcf49d00d264bea2d04efc56a6cede59 #①
Author: hoge <gitLesson@gmail.com>              #②
Date:   Tue Sep 3 21:01:16 2019 +0900           #③

    Add Hello git   #④

```

1. Revision : コミット番号  
    修正の履歴を一意に特定するハッシュ値が割り振られる。
1. Author : 修正者の情報  
    <a href="#ttl1-1">1-1, gitの設定</a>の`config`で設定できる。
1. Date : コミットした時刻
1. Message : コミットメッセージ  
    修正内容の概要

## ● 1-7, ステータスを確認する

1. ステータスを確認する

    ``` shell
    $git status
    ```

    現在の作業状況を確認できる。  
    ファイルの追加・修正・削除・addを行ってstatusがどう変化するか確認する。

### ● statusの見方

``` shell
On branch master    # ①
Your branch is up to date with 'origin/master'.

Changes to be committed:    # ②
  (use "git restore --staged <file>..." to unstage)
	modified:   hoge.text

Changes not staged for commit:  # ③
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)

	modified:   Sample.txt

Untracked files:    # ④
  (use "git add <file>..." to include in what will be committed)

	a.txt
```

1. 作業ブランチ
1. `Changes to be committed:`  
    コミットする準備ができた修正。(addしたもの)  
    ステージングされてインデックスに登録された修正をリストアップされる。
1. `Changes not staged for commit:`  
    ステージングされていない、インデックス未登録のワーキングツリーの修正がリストアップされる。(addされる前)
1. `Untracked files:`  
    gitで管理する対象になっていない新しいファイル。

<p><a href="#contents-list">↑項目一覧へ</a></p>
