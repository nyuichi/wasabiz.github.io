---
layout: post
title: WindowsでgitとEmacs(magit)のセットアップをする
---
# インストールするもの

- Emacs
- git
- magit

# できるようになること
Windowsでmagit経由でgitを快適に使う。特にssh周辺が大事。

# やること

1. Windowsを用意する

2. chocolateyをインストールする

3. Emacsとmsysgitをインストールする

4. Emacsでpackage-installを使ってmagitをインストールする

5. msysgitをインストールするとなぜかgit-bashなるものも一緒にインストールされるのでgit-bashを起動してssh-keygenする

	- このときパスフレーズをNULL(空文字列)にしておく

	- .sshを置く場所をEmacsのホームディレクトリにする。多分`%APPDATA\.ssh`に置けばOK

6. magitが正しくpushできることを確認して完了

# コメント

この一連の操作でインストールしないとmagitがsshのパスフレーズを聞いてくれずずっとハングしたままになってつらぽよになる。
一番大事なのは操作5で、ここさえクリアすれば問題ない(はず)。ちなみに操作5はsshのパスフレーズを設定してしまったり.sshの置く場所をデフォルトのままにしてしまった場合でも後から修正できる。

- パスフレーズを設定してしまった場合

		$ ssh-keygen -p -P old_passphrase -N new_passphrase -f keyfile
	
	でおｋ。新しい鍵をつくることなくパスフレーズのみ更新することができる。

- .sshをデフォルトの場所に作ってしまった場合

	そもそも.sshの場所を動かすのはEmacsのホームディレクトリとgit-bashのホームディレクトリが違うため。なので.sshを別の場所に作ってしまったとしても後から単純にリンクを貼ればいい。
	
	Emacsの`*scratch*`なりで

		(cd "~")
		"c:/Users/wasabiz/AppData/Roaming/"
	
	git-bashで
	
		$ cd ~; pwd
		/c/Users/wasabiz/

	だったとするとC:\Users\wasabiz\.sshをC:\Users\wasabiz\AppData\Roaming\にリンクする。

	もしくはリンクができない場合(リンクを張るソフトがない等)単純にコピーしてしまえばいい。
	
# Ref

[Doesn't ask for password on Windows](https://github.com/magit/magit/issues/188)
