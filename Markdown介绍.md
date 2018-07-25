# Markdown介绍

## 介绍

Markdown是一种书写语言，目标是易读易写。同时它也兼容于HTML, 不属于md的标签, 也可以直接在文档里面使用HTML书写(但`<div>`等最好加上空行隔开)。

> HTML中的md标签不会被处理

## 区块

md大多数的区块都需要在两个空行之间, 区块包含如下内容

- 段落
- 标题
- 引用
- 列表
- 代码
- 分隔线

### 段落

由一个或是多个连续的文本组成, 它的前后都要有一个以上的空行. 相邻的文本, 如果中间没有空行, 会显示在一行中.

段落的首行缩进可以使用HTML的空格来表示, 如: &emsp;前面有一个空格.

### 标题

使用`#`符号来表示标题, 可以支持1到6个, 表示从第一次到第6级(H1~H6)

`# 一级标题`, `## 二级标题`

### 引用

区块引用类似于emial中的`>`引用方式, 它是可以嵌套的, 可以在大部分的内容前面加引用符号

#### 多行与嵌套

多行引用时, 可以在每行前面加`>`, 如果内容需要换行, 则可以在引用内容中加一个空行. 嵌套时, 多加`>`即可实现.

> 这
>> 是
>>> 一
>>>> 个引用

#### 引用中的其它语法

区块引用中也可以使用其它的md语法, 包含: 标题, 列表, 代码等

> ## 这是一个标题。
>
> 1. 这是第一行列表项。
> 2. 这是第二行列表项。
>
> 给出一些例子代码：
>
>     return shell_exec("echo $input | $markdown_script");

### 列表

#### 列表标记

md支持有序以及无序列表

无序列表使用*, +或是-做为标记.

* Red
* Green
* Blue

+ Red
+ Green
+ Blue

- Red
- Green
- Blue

有序列表使用数字加一个英文句号, 但是列表不标记使用的数字并不影响输出的结果

1. red
1. green
1. blue

8. red
3. green
3. blue

#### 列表生成

如果列表项目间使用空行分开, 在输出HTML时md针将项目使用`<p>`标签包起来

```html
*   Bird
*   Magic

会被转换为：

<ul>
<li>Bird</li>
<li>Magic</li>
</ul>
但是这个：

*   Bird

*   Magic
会被转换为：

<ul>
<li><p>Bird</p></li>
<li><p>Magic</p></li>
</ul>
```

#### 列表嵌套

1. 第一层
    * 1-1
    * 1-2
2. 无序列表和有序列表可以随意相互嵌套
    1. 2-1
    2. 2-2

#### 列表中的其它md语法

列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符：

1. This is a list item with two paragraphs. Lorem ipsum dolor
    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
    mi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
    sit amet velit.
1. Suspendisse id sem consectetuer libero luctus adipiscing.

如果要在列表项目内放进引用，那 > 就需要缩进：

* A list item with a blockquote:

    > This is a blockquote
    > >inside a list item.

如果要放代码区块的话，该区块就需要缩进两次，也就是 8 个空格或是 2 个制表符：

* 一列表项包含一个列表区块：

        var a = 0

### 代码区块

md会使用`<pre>`或是`<code>`标签把代码区块包起来. 要在 Markdown 中建立代码区块很简单，只要简单地缩进 4 个空格或是 1 个制表符就可以. 一个代码区块会一直持续到没有缩进的那一行（或是文件结尾）。 但是推荐还是使用```符号将代码区块包含起来

```c#
var c = 0;
```

如果要标记一小段行内代码，你可以用反引号把它包起来（`）

Use the `printf()` function.

如果要在代码区段内插入反引号，可以用多个反引号来开启和结束代码区段：

``There is a literal backtick (`) here.``

`&#8212;` is the decimal-encoded equivalent of `&mdash;`.

代码高亮

```js
var j = [];
```

### 分隔线

你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

* * *

***

*****

- - -

---------------------------------------

## 区段元素

### 链接

md支持两种形式的链接语法： 行内式和参考式两种形式。不管是哪一种，链接文字都是用 [方括号] 来标记。

要建立一个行内式的链接，只要在方块括号后面紧接着圆括号并插入网址链接即可，如果你还想要加上链接的 title 文字，只要在网址后面，用双引号把 title 文字包起来即可

This is [an example](http://example.com/ "Title") inline link.

如果是要链接到同样主机的资源，你可以使用相对路径：

See my [About](/about/) page for details.

参考式的链接是在链接文字的括号后面再接上另一个方括号，而在第二个方括号里面要填入用以辨识链接的标记：

This is [an example][id] reference-style link.

[id]: http://example.com/  "Optional Title Here"

链接内容定义的形式为：

* 方括号（前面可以选择性地加上至多三个空格来缩进），里面输入链接文字
* 接着一个冒号
* 接着一个以上的空格或制表符
* 接着链接的网址
* 选择性地接着 title 内容，可以用单引号、双引号或是括弧包着

[foo]: http://example.com/  "Optional Title Here"
[foo]: http://example.com/  'Optional Title Here'
[foo]: http://example.com/  (Optional Title Here)

隐式链接标记功能让你可以省略指定链接标记，这种情形下，链接标记会视为等同于链接文字，要用隐式链接标记只要在链接文字后面加上一个空的方括号，如果你要让 "Google" 链接到 google.com，你可以简化成：

[Google][]

[Google]: http://google.com/

I get 10 times more traffic from [Google] [1] than from
[Yahoo] [2] or [MSN] [3].

  [1]: http://google.com/        "Google"
  [2]: http://search.yahoo.com/  "Yahoo Search"
  [3]: http://search.msn.com/    "MSN Search"

自动链接

使用`<>`包括的URL或是邮箱地址会被自动转换为超链接

### 强调

使用星号（*）和底线（_）作为标记强调字词的符号，被 * 或 _ 包围的字词会被转成用`<em>` 标签包围，用两个 * 或 _ 包起来的话，则会被转成`<strong>`

*single asterisks*

_single underscores_

**double asterisks**

__double underscores__

### 图片

使用一种和链接很相似的语法来标记图片，同样也允许两种样式： 行内式和参考式。

* 一个惊叹号 !
* 接着一个方括号，里面放上图片的替代文字
* 接着一个普通括号，里面放上图片的网址，最后还可以用引号包住并加上 选择性的 'title' 文字。

![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg "Optional title")

到目前为止， Markdown 还没有办法指定图片的宽高，如果你需要的话，你可以使用普通的 `<img>` 标签。

## 其它

支持以比较简短的自动链接形式来处理网址和电子邮件信箱

<http://example.com/>

<address@example.com>

可以利用反斜杠来插入一些在语法中有其它意义的符号

```
\   反斜线
`   反引号
*   星号
_   底线
{}  花括号
[]  方括号
()  括弧
#   井字号
+   加号
-   减号
.   英文句点
!   惊叹号
```

## 扩展语法

这就是 ~~删除线~~

在表头下方的分隔线标记中加入 :，即可标记下方单元格内容的对齐方式：

:--- 代表左对齐
:--: 代表居中对齐
---: 代表右对齐

left|center|right
:--- | :----: | ----:
aaaa | bbbbbb | ccccc
a    | b | c


- [ ] Eat
- [x] Code
  - [x] HTML
  - [x] CSS
  - [x] JavaScript
- [ ] Sleep

## vscode 有用扩展

* markdown pdf: 转化为PDF(但是好像不支持其它括件的扩展, 如流程图)
* markdown preview github styling: 按github的样式预览
* markdown preview mermail support: 流程图与时序图支持
* markdownlint: 书写语法检查
* markdowncheckbox: checkbox

```mermaid
graph TD;
A-->B;
A-->C;
B-->D;
C-->D;
```

* [x] 你好

帮助: ~~http://xianbai.me/learn-md/article/syntax/paragraphs-and-line-breaks.html~~