
命名規則
========

- 意味の分かる名前を使うこと。
- 見た目を反映したものやそれが何を表しているかではなく、目的や役割を反映した名前を付ける。
- 短くしすぎて意味がわからなくなるようなのは NG。


### ID

- すべて小文字で、単語はアンダースコア `_` でつなげる (スネークケース)。

```scss
#global_header
```

### class

- すべて小文字で、単語はダッシュ `-` でつなげる。

```scss
.menu-item
```




シンタックスルール
==================

インデント
----------

- 半角スペース2つ分でインデントする。
- タブを使ったり、タブとスペースを混在させるのは NG。


ブロック単位のインデント
------------------------

- その階層がわかるようにブロック単位でコードをインデントする。

```scss
// OK
.title {
  color: #fff;
}

#global_header {
  header {
    nav {
      // ...
    }
  }
}


// NG
.title { color: #fff; }

#global_header {
header {
  nav {
    // ...
  }
}
}
```


セレクタ
--------

- セレクタとブロックの開始ブレースの間には1つスペースを入れる。

```scss
// OK
.foo {
  // ...
}

.foo{
  // ...
}
```

- 1セレクタは1行で書く。

```scss
// OK
.foo,
.bar {
  // ...
}

// NG
.foo, .bar {
  // ...
}
```


CSS ルールの分離
----------------

- 別々の CSS ルールは改行して一行間を空けて書く。

```scss
html {
  background: #fff;
}

body {
  margin: auto;
  width: 50%;
}
```


プロパティと値
--------------

- 1プロパティは1行で書く。

```scss
// OK
.foo {
  font-weight: bold;
  color: #000;
}

// NG
.foo {
  font-weight: bold; color: #000;
}
```

- すべてのプロパティの終端はセミコロンを書く。

```scss
// OK
.foo {
  color: #fff;
}

// NG
.foo {
  color: #fff
}
```

- プロパティと値の間の、コロンは後に1つだけスペースを入れる。

```scss
// OK
.foo {
  color: #fff;
}

// NG
.foo {
  color:#fff;
  color :#fff;
  color : #fff;
}
```

- 値が長かったり、複数の値を持つときは、改行する。

```scss
.foo {
  box-shadow:
    inset 0 1px 0 #000,
    0 1px 0 #666,
    1px 0 0 #fff;
}
```


コメント
--------

- セクションごとにタイトルコメントを記述する。
- タイトルコメントは以下のスニペットを使用すること。


```scss
/*=== 大見出し
==============================================================================================*/
```

```scss
/*  小見出し
-----------------------------------------------*/
```



スタイルルール
==============

タイプセレクタの記述
--------------------

- ID とクラス名にタイプセレクタは記述しない。
- パフォーマンスを考慮して不要な子孫セレクタは避ける。

```scss
// OK
#id {}
.class {}

// NG
ul#id {}
div.class {}
```


ショートハンドプロパティ
------------------------

- 可能な限りショートハンドでプロパティを書く。
- 一つだけ、違う値にオーバーライドする場合は例外とする。

```scss
// OK
border-top: 0;
padding: 0 10px 20px;

// NG
border-top-style: none;
padding-bottom: 20px;
padding-left: 10px;
padding-right: 10px;
padding-top: 0;
```

```scss
// OK
padding: 10px;
padding-left: 0;
```


単位
----

- 値が「0」なら単位を省略する。

```scss
margin: 0;
padding: 0;
```


小数点
------

- 小数点の頭の「0」は省略する。

```scss
font-size: .8em;
```


url の引用符
------------

- `url()` での指定においては引用符を省略すること。

```scss
@import url(/path/to/file);
```


カラーコード
------------

- カラーコードは全て小文字の16進数で表記する。
- 可能な場合は、3文字のショートコードで書く。
- 色名は使用しない。


```scss
// OK
color: #fff;
color: #c00;
color: #efefef;

// NG
color: white;
color: #cc0000;
color: #EFEFEF;
```


プロパティの記述順序
--------------------

- アルファベットの順に記述する。
- ベンダープレフィックスは無視する。
- ベンダープレフィックスの順序は以下のようにする。

```scss
border: 1px solid;
-webkit-border-radius: 4px;
color: black;
text-align: center;
```

```scss
-webkit-border-radius: 4px; // WebKit
-moz-border-radius: 4px;    // Firefox
-ms-border-radius: 4px;     // IE
-o-border-radius: 4px;      // Opera
border-radius: 4px;         // No prefix
```



