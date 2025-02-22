## Vim 全局替换

**语法**为 :[addr]s/源字符串/目的字符串/[option]  
全局替换命令为：`:%s/源字符串/目的字符串/g`

**[addr]** 表示检索范围，省略时表示当前行。  
如：“1，20” ：表示从第1行到20行；  
“%” ：表示整个文件，同“1,”；“.,” ：从当前行到文件尾；

**s** : 表示替换操作

**[option]** : 表示操作类型  
如：g 表示全局替换;  
c 表示进行确认  
p 表示替代结果逐行显示（Ctrl + L恢复屏幕）；  
省略option时仅对每行第一个匹配串进行替换；  
如果在源字符串和目的字符串中出现特殊字符，需要用”\”转义

## Vim 文本替换

[VIM文本替换命令_@Turbo@的博客-CSDN博客](https://blog.csdn.net/weixin_41920367/article/details/126936912)

**替换命令的完整形式：**`:[range]s/src/dest/[flags]`

**[range]**

> 不写range ：默认为光标所在的行。
> `.` ：光标所在的行。
> `1` ：第一行。
> `$` ：最后一行。
> `33` ：第33行。
> `'a` ：标记a所在的行（之前要使用ma做过标记）。
> `.+1` ：当前光标所在行的下面一行。
> `$-1` ：倒数第二行。（这里说明我们可以对某一行加减某个数值来取得相对的行）。
> `22,33` ：第22～33行。
> `1,$` ：第1行 到 最后一行。
> `1,.` ：第1行 到 当前行。
> `.,$` ：当前行 到 最后一行。
> `'a,'b` ：标记a所在的行 到 标记b所在的行。
> `%` ：所有行（与 1,$ 等价）。
> `?chapter?` ：从当前位置向上搜索，找到的第一个chapter所在的行。其中chapter可以是任何字符串或者正则表达式。
> `/chapter/` ：从当前位置向下搜索，找到的第一个chapter所在的行。其中chapter可以是任何字符串或者正则表达式。

**[flags]**

> 无 ：只对指定范围内的第一个匹配项进行替换。
> `g` ：对指定范围内的所有匹配项进行替换。
> `c` ：在替换前请求用户确认。
> `e` ：忽略执行过程中的错误。

## Vim 多行同时操作

首先，在VIM的命令行模式下，按 Ctrl + v 即可进入区块模式。用方向键可以选择需要操作的文本区域。该模式下常用于多行的文本增删操作，如Tab、注释等

**操作**

- 多行复制、粘贴：按y复制，按p粘贴

- 多行插入：按I（大写i）进入插入模式

- 多行删除：按d即可

- 多行替换：按s即可

操作完毕即可按Esc退出区块模式

## Vim 快捷删除括号内所有文本

选中`",(,[,{`左括弧

输入命令`di`+`",(,[,{`其中的字符

## Vim 回到上一次编辑的位置

有些时候，我们需要快速回到上次打开文件的位置，下面是两种不同场景下的实现方式：

1. 已经打开上次编辑的文件，需要回到上次编辑的位置，可以直接使用命令`gi`

2. 已经打开上次编辑的文件，但是要打开更早编辑的文件，可以使用命令`^Coo`

即按住 `Ctrl+o`，这条命令可以重复使用，打开更多历史编辑过的文件。

`Ctrl+i`，是上诉命令的方向操作
