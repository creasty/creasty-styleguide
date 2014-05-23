
命名規則
========

- 意味の分かる名前を使うこと。
- 見た目を反映したものやそれが何を表しているかではなく、目的や役割を反映した名前を付ける。
- 短くしすぎて意味がわからなくなるようなのは NG。

ID
--

- すべて小文字で、単語はアンダースコア `_` でつなげる (スネークケース)。

```scss
#global_header
```


class
-----

- すべて小文字で、単語はダッシュ `-` でつなげる。

```scss
.menu-item
```


mixin / function
----------------

- すべて小文字で、単語はダッシュ `-` でつなげる。

```scss
@mixin some-mixin($arg) {
  // ...
}

@function some-func($arg) {
  // ...
}
```


variables
---------

- すべて小文字で、単語はダッシュ `-` でつなげる。

```scss
$some-var: 1;
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


行末のスペース
--------------

- 行末のスペースを削除する。


セレクタ
--------

- セレクタとブロックの開始ブレースの間には1つスペースを入れる。

```scss
// OK
.foo {
  // ...
}

// NG
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

- `+, >, ~` の前後には、スペースを入れる。

```scss
.one + .other {
  // ...
}
.parent > .child {
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




スタイルルール
==============

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


引用符
------

- ダブルクオーテーション `"` を使用する。


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
- 単位が秒 `s` である場合は、例外とする。

```scss
margin: 0;
padding: 0;
@include transition(color 0s 3s ease-in-out);
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
background: url(/path/to/file);
```


カラーコード
------------

- カラーコードは全て小文字の hex コードで表記する。
- 可能な場合は、3文字のショートコードで書く。
- 色名は使用しない。
- rgba を使う場合、色の引数には、hex コードを使う。

```scss
// OK
color: #fff;
color: #c00;
color: #efefef;
color: rgba(#000, .5);

// NG
color: white;
color: #cc0000;
color: #EFEFEF;
color: rgba(0, 0, 0, .5);
```


リスト、関数呼び出し
--------------------

- コンマ `,` の後にスペースを入れる。

```scss
@include some-mixin(10px, 20px);
$sizes: 10px, 20px;
```


ルールブロック内の記述順序
--------------------------

### プロパティ

- アルファベットの順に記述する。
- ベンダープレフィックスは無視する。

```scss
border: 1px solid;
-webkit-border-radius: 4px;
color: black;
text-align: center;
```

- ベンダープレフィックスの順序は以下のようにする。

```scss
-webkit-border-radius: 4px; // WebKit
-moz-border-radius: 4px;    // Firefox
-ms-border-radius: 4px;     // IE
-o-border-radius: 4px;      // Opera
border-radius: 4px;         // No prefix
```

### extend

- `@extend()` は、プロパティのブロックの最初にまとめる。
- 他のプロパティとの間には、空行をあける。

```scss
.foo {
  @extend %bar;

  color: #fff;
}
```


### include

- 順番は mixin の内容によるため、指定はない。
- 他のプロパティとの間には、空行をあける**必要はない**。

```scss
.foo {
  color: #fff;
  @include box-shadow(0 0 1px #000);
}
```

- 引数が2つ以上の場合は、named argument を使用する。
- 1行が長くなる場合は、改行する。

```scss
// OK
@include some-mixin(
  $size: 10px,
  $base-color: #fff,
  $hover-color: #fff
);

// NG
@include some-mixin(10px, #fff, #fff);
```


### & (親参照)

- セレクタが & ではじまるブロックは、原則プロパティの後、他のルールブロックの前に書く。

```scss
.foo {
  color: #fff;

  &.alt {
    // ...
  }

  & + .foo {
    // ...
  }

  .bar {
    // ...
  }

  .baz {
    // ...
  }
}
```


制御構文
--------

### @if, @elseif @else

```scss
// OK
@if $var1 == foo {
  // ...
} @elseif $var2 == bar {
  // ...
} @else {
  // ...
}

// NG
@if $var1 == foo {
  // ...
}
@else {
  // ...
}
```

### @each

```scss
@each $color in $colors {
  // ...
}
```

### @for

```scss
@for $n from 1 through 10 {
  // ...
}
```

### @while

```scss
@while $var < 10 {
  // ...
}
```


