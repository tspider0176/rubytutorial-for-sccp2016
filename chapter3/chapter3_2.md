## 3.2 ブロック付きメソッドとイテレータ


これまでに、いくつかの配列のメソッドについて触れた。
ここで配列のブロック付きメソッドとイテレータについて説明をする。

以下がブロック付きメソッドとイテレータの例である。

```ruby
# -*- coding: utf-8 -*-

arr = ['a', 'b', 'c']
arr.each do |item|
  print item + " " #=> a, b, c
end
```

まず初めに配列は、*each*と言う名前のメソッドを呼び出している。
eachメソッドは、ブロックを引数として受け取る。
ブロックにあたるのが、*do*から*end*キーワードまでである。
ブロックは引数を持つことができ、|引数, …|という形で書くことができる。
引数は、イテレータにより配列の要素が一つ一つ送り込まれ、ブロックの中の文が評価される。
図で書くと以下のような形だ。

```ruby
   ↓
['a', 'b', 'c']
['b', 'c']   ->  item = |"a"|  ->   print "a"
['c']        ->  item = |"b"|  ->   print "b"
[]           ->  item = |"c"|  ->   print "c"
```

配列の添字が必要なケースがある場合は、*each_with_index*メソッドを使おう。
このメソッドはブロックの最初の引数が配列から来た値で、2つ目の引数が添字になっている。
```ruby
arr.each_with_index do |item, index|
  p [item, index]
end
#=> ["a", 0]
#=> ["b", 1]
#=> ["c", 2]
```

配列の各々の要素に対して何か処理を施して、その結果を再び配列としてまとめたい場合がある。
そのときは*map*メソッドを使う。最後に評価された値が再び配列の要素となる。

```ruby
arr = ['abc', 'def', 'ghi']
arr.map do |item|
  item.upcase
end
p arr #=> ["ABC", "DEF", GHI]
```

また、do ~ endの構文は波括弧で記述することもできる。

```ruby
p arr.map{|item| item.upcase}
```

さらに、省略して書くこともできます。

```ruby
p arr.map{&:upcase}
```

mapメソッドの動きを図にすると以下の様な形になる。

```ruby
['abc', 'def', 'ghi']
['def', 'ghi']   ->  item = |"abc"|  ->   ['ABC']
['ghi']  	       ->  item = |"def"|  ->   ['ABC', 'DEF']
[]               ->  item = |"ghi"|  ->   ['ABC', 'DEF', 'GHI']
```

最後に畳み込みを行う*inject*メソッドを紹介する。
畳み込みとは配列を順に見ていくときに、用意した値に対して配列の要素を演算していく(畳み込んでいく)。
例えば、足し込んで行く場合は以下のようになる。

```ruby
puts (1..100).to_a.inject { |sum, n| sum + n} # 5050 nが用意した値。初期値として0が代入されている。
```
以下のように省略することもできる。
```ruby
puts (1..100).to_a.inject(:+)
```

以上で配列は終わりとなる。多くの便利なメソッドが用意され、非常に柔軟な処理ができることがわかったと思う。
最後に配列に関する問題を用意するので、解いてみてほしい。

- http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_4_D (全て畳み込み演算で求めてみよう。)
- http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=0102&lang=jp