# GitLesson

<h1 id="contents-list">■ 項目</h1>

- __<a href="#ttl">gitとは</a>__
- __<a href="#ttl0">インストール</a>__
- __<a href="#ttl1">git Lesson１</a>__
- __<a href="#ttl2">git Lesson２</a>__

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
    $ brew install git
    ```

- Windows  
    [https://gitforwindows.org](https://gitforwindows.org)からmsysgitの最新版のインストール

<p><a href="#contents-list">↑項目一覧へ</a></p>

<h1 id="ttl1">■ git Lesson１</h1>

<h2 id="ttl1-1">● 1-1, gitの設定</h2>

- コミット時のAuthorの変更

    ``` shell
    # 設定
    $ git config --global user.name "<任意のユーザ名>"
    $ git config --global user.email "<任意のメールアドレス>"
    ```

- 出力を色付けしてくれる設定

    ``` shell
    # 任意
    $ git config --global color.ui true
    ```

- 安全対策

    ``` shell
    $ git config --global push.default current
    ```

- 設定の確認 => `-l`オプション使用

    ``` shell
    $ git config -l
    $ git config -l --global
    ```

- ヘルプ

    ``` shell
    $ git config --help
    # もしくは
    $ git help config
    ```

## ● 1-2, gitを使う準備

1. まずはディレクトリを作ろう。

    ``` shell
    $ mkdir gitLesson
    $ cd gitLesson
    ```

1. gitを使う準備をします。

    ``` shell
    $ git init
    ```

これで準備は終了です。  
`git init` で、ファイルの変更や履歴の情報をつかさどる「リポジトリ」が作成される。  
リポジトリは、.gitというディレクトリで管理される。  
つまり.gitを削除するとリポジトリの情報は消えるということ。

## ● 1-3, ファイルを追加する

### ・ コミット

    ``` shell
    $ git add .
    $ git commit -m "コミットメッセージ"
    ```

ファイルを記録し、履歴として参照できる状態にすることを、**コミット**と言います。  
`commit`の直前に行っている`add`は、ファイルをコミットの対象に追加するという感じ。  
`add`していない修正は、`commit`を実行してもコミットされない。

1. 新規ファイルの作成

    ``` shell
    $ echo "Hello git ver2" > Sample02.txt
    ```

1. __コミット__ : Sample.txtをコミット

    ``` shell
    $ git add Sample02.txt
    $ git commit -m "Add Sample02.txt"
    ```

## ● 1-4, ファイルを修正する

1. ファイルを修正  
    `/Sample.txt` を開いて修正してください。  

1. コミットする

    ``` shell
    $ git add Sample.txt
    $ git commit -m "Add Sample.txt"
    ```

これで修正したファイルを記録できました。

## ● 1-5, ファイルを削除する

1. ファイルを削除する

    ``` shell
    $ rm -i Sample02.txt
    ```

1. ファイル削除をコミットする

    ``` shell
    $ git rm Sample02.text
    $ git commit -m "remove Sample02.txt"
    ```

これでファイルを削除し、コミットすることができる。

<h2 id="ttl1-6"> ● 1-6, 修正履歴(ログ)を確認する</h2>

1. ログを確認する

    ``` shell
    $ git log
    ```

    修正履歴(ログ)を確認することができる。  
    ページが１ページで収まらない時は、  
    `スペース`で改ページ、`q` で終了する。

### ・ ログの見方

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

<a href="#ttl2-7">いろいろな方法で修正履歴(ログ)を確認する</a>

## ● 1-7, ステータスを確認する

1. ステータスを確認する

    ``` shell
    $ git status
    ```

    現在の作業状況を確認できる。  
    ファイルの追加・修正・削除・addを行ってstatusがどう変化するか確認する。

### ・ statusの見方

``` shell
On branch master    # ①
Your branch is up to date with 'origin/master'.

Changes to be committed:    # ②
  (use "git restore --staged <file>..." to unstage)
	modified:   hoge.txt

Changes not staged for commit:  # ③
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)

	modified:   Sample.txt

Untracked files:    # ④
  (use "git add <file>..." to include in what will be committed)

	hoge_hohe.txt
```

1. 作業ブランチ
1. `Changes to be committed:`  
    コミットする準備ができた修正。(addしたもの)  
    ステージングされてインデックスに登録された修正をリストアップされる。
1. `Changes not staged for commit:`  
    ステージングされていない、インデックス未登録のワーキングツリーの修正がリストアップされる。(addされる前)
1. `Untracked files:`  
    gitで管理する対象になっていない新しいファイル。

### ・ 状態の遷移

`git status` で修正がどのように扱われている状態なのか確認できます。  
ファイルが修正されコミットされるまでの間に、gitでは３つの状態を行き来します。  
`commit`の前に`add`があるのはそのため。

- __ワーキングツリー__  
    現在作業している実ファイル。
- __インデックス__  
    コミットするための情報を登録する場所を指す。  
    インデックスに登録されたものだけがコミットできる。
- __ローカルリポジトリ__  
    コミットの情報が記録される場所。

<h2 id="ttl1-8"> ● 1-8, 差分を確認する</h2>

1. 差分の確認

    ``` shell
    $ git diff
    ```

必ずファイルを修正した状態でコミットする前に差分を必ず確認しましょう。  
`git diff` でワーキングツリーとリポジトリとのファイルの差分、修正の内容が確認できる。  
コミット前に、修正内容が間違っていないか差分をチェックする癖をつけておこう。  
<a href="#ttl2-6">いろいろな差分を見る</a>

<p><a href="#contents-list">↑項目一覧へ</a></p>

---

<h1 id="ttl2">■ git Lesson２</h1>

## ● 2-1, コマンドを調べる

``` shell
$ git help
$ git help -a
$ git help <command>
```

- 例)addってなんだっけ...

    ``` shell
    $ git help add
    ```

## ● 2-2, 設定(config)の種類と場所

`git config` には以下の３種類の設定が存在する。

|範囲|オプション|場所|
|---|---|---|
|システム全体|`--system`|`/etc/gitconfig`|
|特定のユーザー|`--global`|`~/gitconfig` or `~/.config/git/config`|
|リポジトリ固有|`--local`(デフォルト)|`repository/.git/config`|

設定は、  
【システム】=>【ユーザー】=>【リポジトリ】  
の順番で組み込まれる。  
同じ項目は後で組み込まれた設定が優先され設定される。

共通で設定したい場合は、  
`git config --global user.name <ユーザー名>`  
リポジトリ固有で設定したい場合は、  
`git config user.name <ユーザー名>`  
と指定するとよい。  
また、ファイルを直接書き換えることでも設定を変更できる。

## ● 2-3, gitで管理しないファイルを指定する

gitで管理しないファイルを指定するには、`.gitignore` というファイルを作成する。  
下記に例題を紹介する。

### ・ Macの .DS_Storeを除外する

1. .gitignoreの作成

    ``` shell
    $ mkdir .gitignore
    ```

1. .DS_Storeを除外する  

    `/.gitignore`

    ``` .gitignore
    # mac用
    .DS_Store
    ```

### ・ 空ディレクトリ

gitは空のディレクトリを管理の対象にしない。  
空ディレクトリをコミットしたい場合は、`.gitkeep`という名前の空ファイルを作成しておくのが一般的。

## ● 2-4, gitで管理外のファイルを削除する

ビルドによる生成ファイルなどを削除する場合は、`git clean` を使用する。

``` shell
# 対象外ファイルの確認
$ git clean -n

# 指定のファイルを削除
$ git clean -f <ファイルパス>

# カレントディレクトリのファイルを削除
$ git clean -f

# ディレクトリの削除
$ git clean -d
```

`-x`をつけると、`.gitignore`で無視される設定のファイルも消すことが出来る。

## ● 2-5, addを省略してコミットをする

``` shell
$ git commit -a
# コミットメッセージ付き
$ git commit -am "Add Message"
```

新規ファイルは個別に`add`する必要があるので注意。

<h2 id="ttl2-6"> ● 2-6, いろいろな方法で差分を見る</h2>

【 <a href="#ttl1-8">1-8, 差分を確認する</a> 】で差分の確認を学んだが、ここではいろいろな差分の見方を紹介する。

- ワーキングツリーとリポジトリの差分を表示

    ``` shell
    $ git diff
    ```

- インデックスとリポジトリの差分を表示

    ``` shell
    $ git diff --cached
    ```

- ワーキングツリー＆インデックス と リポジトリの差分を表示

    ``` shell
    $ git diff HEAD
    ```

- 単語単位で差分表示

    ``` shell
    $ git diff -w
    ```

- 特定のブランチとの差分

    ``` shell
    $ git diff <BranchName>
    ```

<h2 id="ttl2-7"> ● 2-7, いろいろな方法で修正履歴(ログ)を確認する</h2>

【 <a href="#ttl1-6">1-6, 修正履歴(ログ)を確認する</a> 】で修正履歴について学んだが、ここではいろいろな修正履歴(ログ)を紹介する。

- ログの表示

    ``` shell
    $ git log
    ```

- コンパクトに表示

    ``` shell
    $ git log --oneline
    ```

- ログと変更された場所

    ``` shell
    $ git log -p
    ```

- どのファイルが何箇所変更されたか確認できる

    ``` shell
    $ git log --stat
    ```

## ● 2-8, リビジョンを移動する

1. まずはログを確認する。

    ``` shell
    $ git log
    ```

ここで見るのはコミットのハッシュ値(リビジョン番号)

### ・ 一つ前のリビジョンに戻る

``` shell
$ git checkout HEAD^
```

ファイルの状態が一つ前の状態になり、`git log` や`git diff` の出力が変わったことが確認できます。

- 二つ前の状態

    ``` shell
    $ git checkout HEAD^^
    # または
    $ git checkout HEAD~2
    ```

### ・ HEADについて

HEADは現在の作業ブランチの先頭コミットの別称。  
つまり`HEAD^` は先頭ブランチから一つ前の名称。

### ・ リビジョン番号を指定して移動する

``` shell
$ git checkout <RevisionNumber>
```

<p><a href="#contents-list">↑項目一覧へ</a></p>
