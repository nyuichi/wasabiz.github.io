---
layout: post
title: Emacs on WindowsでCtrl + 右Alt + keyが効かない
---

[EmacsWiki: Alt Gr Key](www.emacswiki.org/emacs/AltGrKey)

WindowsにGNU Emacsをインストールした後色々いじっているとCtrl+右alt+Keyが効かないことを発見。
Ctrl+左Altだと問題ない上に右Alt+keyでも問題はなく動く。最初はHHK特有の問題かと思ってごにょごにょするも解決ならず。
いろいろ調べていたところ上のWikiにたどり着いた。

曰くWindowsがCtrl+AltGr+keyのイベントを持ち逃げしてしまうとのことでOSレベルの問題とのこと。
結局、キーをリマップするという最終手段で対処するしかないようだったのでその方法で解決。
リマップにはSharpKeysというソフトを使った。

[SharpKeys - Home](http://sharpkeys.codeplex.com/)

Right AltをLeft Altにリマップして再起動。問題なく動いた。
