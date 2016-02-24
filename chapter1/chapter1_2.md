## 1.2 スクリプトの実行
スクリプト言語の特徴を持ったRubyのプログラムを書いて実行する場合の手順は、コンパイラ言語とそう変わりはない。
「rb」の付いた拡張子のファイルを作成し、エディタを使ってスクリプトを記述する。

hello.rb
```
# -*- coding: utf-8 -*-

puts 'HelloWorld!'  #=> HelloWorld! と出力される。
```
上のようにスクリプトが記述できたら、以下のように実行をしてみよう。
```
$ ruby hello.rb
HelloWorld!
```
スクリプトの一行目は、スクリプト中に日本語を使うためのおまじないである。日本語を特に使わない場合は付けなくても構わない。
付けない場合は実行エラーになってしまうので注意が必要だ。putsは、文字列を出力するメソッド(関数のこと)で、末尾に改行を自動的に付けてくれる。
改行を末尾に付けないprintメソッドも用意されている。# から始まると、以降はコメントとしてみなされる。
資料では #=> と書いた場合は、プログラムの実行結果をあらわす。Rubyの練習では、AOJと呼ばれるオンラインジャッジシステムを使っていく。
確認の意味を込めて、以下の問題を解いてみよう。

http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_1_A 

Rubyは以上のようにファイルにプログラムを書く以外にも、プログラムを実行する対話型シェル(REPL)を備えている。
REPLは*irb*とターミナルに打つことで起動ができる。
```
$ irb
irb(main):001:0> 1+1
=> 2
irb(main):002:0> puts 'Hello'
Hello
=> nil
irb(main):003:0> 123.to_s
=> "123"
irb(main):004:0> exit
$
```
REPLでは任意のプログラムを打つことができ、実行結果が => の後に出力される。C-d、もしくは'exit', 'quit'とタイプすれば終了できる。
単なる高度な計算機として使うことや知らないオブジェクトやメソッドの挙動を確かめるときに、型などを確認できるので非常に便利である。
この資料でも、プログラムの挙動を確かめるときにはREPLを積極的に使用していく。