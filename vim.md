# MacVimでcpsmが動かない

* asdfへのPATHを消して、SystemのPythonを使って cpsm をインストールすれば解決した
* vimrcの先頭で `if has('python3') endif` などと書く
* 参考
  * [http://ravelll.hatenadiary.jp/entry/2016/03/14/234454](http://ravelll.hatenadiary.jp/entry/2016/03/14/234454)
    * `otool` コマンドと言うものを知る
  * [http://qiita.com/tmsanrinsha/items/cd2c276f7f1a16aeeaea](http://qiita.com/tmsanrinsha/items/cd2c276f7f1a16aeeaea)
    * python3 を先に読み込まないと、MacVimでpython3は使えない



