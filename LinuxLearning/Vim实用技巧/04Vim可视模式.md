## 可视模式

### 技巧20 深入理解可视模式

**“选区”操作**

​	Vim的可视模式允许我们在自己选中的一个文本区域上进行操作，普通模式中的许多操作命令都可以在可视模式中生效，但是也存在一些操作上的细微变化。插入模式中有**操作符+动作命令**完成一个操作，可视模式中也是通过操作符确定操作类别，但是不是通过动作命令确定作用范围，而是与普通模式相反的逻辑，它先有了被选中的区域然后在使用操作符命令完成操作。

**使用示例**

​	例如，当需要将文本中的单词`March`替换成`April`时，一般情况下，我们会考虑使用退格键删除单词再输入新内容，或者鼠标双击选中单词再用退格键删除再添加内容。这一问题在可视模式下可以选择鼠标双击的处理逻辑，把光标移动到目标单词后，使用`v`命令进入可视模式，然后使用`iw`命令选中目标单词，然后使用`c`命令删除选中内容并切换到插入模式，接着就可以输入`April`完成修改操作了。

### 技巧21 选择高亮选区

**可视模式的三种子模式**

​	可视模式有面向字符、面向行、面想列块三种子模式，它们可以分别用于处理不同类型的文本。从普通模式切换到这三种子模式的命令如下表所示。

|   命令   |          用途          |
| :------: | :--------------------: |
|   `v`    | 进入面向字符的可视模式 |
|   `V`    |  进入面向行的可视模式  |
| `Ctrl v` | 进入面向列块的可视模式 |
|   `gv`   |  返回到上次的高亮选区  |
|   `o`    |  切换高亮选区的活动端  |

​	其中的`gv`和`o`命令是可视模式的操作命令，`gv`命令撤销当前的高亮选区回退到上一个高亮选区，而`o`命令则是在构造高亮选区时可以更加灵活的控制活动端，当发现选区划分错误时，使用`o`命令改变活动端然后重新调整选区边界。

### 技巧22 重复对高亮选区进行操作

**针对选区重复操作**

​	在可视模式中，每当执行以此操作命令之后，会被切换到普通模式下，如果想再次对该选区进行操作，避免重复划定选区可以使用`gv`命令直接回到相同范围的高亮选区。有些应用场景也可以使用`·`命令完成重复操作，例如想将一个文本块缩进多次，在可视模式下选择文本块之后使用`>`命令缩进一次文本块，之后可以直接使用`·`命令完成重复缩进任务。

### 技巧23 操作符命令优先级高于可视命令

**能用操作符命令不用可视命令**

​	和数字前缀的次数命令与`.`命令之间的抉择一样，能用操作符命令完成的任务不用可视命令完成，因为在**一键操作，一键移动**的范式之中，操作符命令更易实践。可视命令中高亮选区的固定可能在一些操作中缺乏灵活性，导致在使用`.`命令重复操作时作用范围不能够灵活改变，而由**操作符+动作命令**完成的操作在作用范围上具有一定灵活性，更具优势。

### 技巧24-26 运用面向列块的可视模式

**用面向列块的可视模式编辑表格数据**

​	例如，想要在三行内容中间为他们添加`|`符号，构成一个表格。先使用`Ctrl v`命令进入面向列块的可视模式，然后使用`j/k`命令划分列块选区，最后使用`r|`命令为三行内容都添加`|`符号。

```c
one       1
tow       2
three     3
```

**修改列文本**

​	例如，想要修改同列块中的相同内容，可以直接使用`Ctrl v`命令进入列块可视模式，然后使用`h/l`命令选择文本，再用`j/k`命令选择列块，然后使用`c`命令替换内容并输入新的内容，所有行的内容都会被同时修改。

**在长短不一的高亮块后添加文本**

​	例如，多行长短不一的代码都需要添加`;`，前面已经使用过`A;`然后使用`j.`**一键移动，一键操作**完成内容添加工作。这一工作使用列块可视模式可以更加方便的完成，使用`Ctrl v`进入可视模式，然后使用`j/h`以及移动至行尾`$`命令选中所有行末端文本，然后使用`A;`命令完成文本添加工作。