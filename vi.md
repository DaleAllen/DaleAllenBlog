# vi使用

<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [vi使用](#vi使用)
  * [使用 vi](#使用-vi)
  * [命令模式](#命令模式)
  * [插入模式](#插入模式)
  * [末行模式](#末行模式)
  * [在终端中使用 vi](#在终端中使用-vi)
  * [锁死](#锁死)

<!-- tocstop -->


## 使用 vi ##

`vi <filename>`  打开文件,如果文件不存在则自动创建
`vi +n <filename>` 打开文件,自动跳转到第 n 行
`view <filename>` 以只读模式打开文件

打开文件后,首先进入的命令模式(command mode),在该模式下可以输入命令控制光标的移动,文件内容的增删改的快捷操作

## 命令模式 ##
- 光标跳转:
  - `k|j|h|l`上下左右,终端命令行`vi`模式下显示上下条历史命令  
  - `b|w`跳转到上一个单词开始,或者下一个单词开始  
  - `B|W`跳转到上一个字符串开始,或者下一个字符串开始  
  - `()`跳转到上一个句子或者下一个句子  
  - `{}`跳转到上一个段落或者下一个段落  
  - `0|^`跳转到行首  
  - `$`跳转到行尾  
  - `gg`跳转到第一行行首  
  - `G`跳转到最后一行行首  

- 删除操作:
  - `x`从左往右按字符删除
  - `*x`从左往右删除 x 个字符
  - `dw`光标位置向后删除一个单词
  - `dW`光标位置向后删除一个字符串
  - `dd`删除光标所在行
  - `*dd`向下删除*行(包括光标所在行)
  - `D`删除光标位置之后到行尾所有内容

- 复制粘贴
  - `yy`复制当前行
  - `p`将复制的文本粘贴到下一行
  - `*p`将促织的文本粘贴*次到下一行

- 恢复
  - `u`恢复在命令模式下的上一步操作
  - `U`恢复在命令模式下对这一行的所有操作,前提是光标没有移动出该行
  - `UU`撤销命令`U`的恢复

- 大小写切换 ~

## 插入模式 ##
输入`a|i|o`等命令,从命令模式进入插入模式(Insert mode),该模式和普通的文件没有什么不同

其中进入不同命令进入插入模式的区别如下:

- `i`从当前目标所在处插入，`I`:从目前所在行的第一个非空格符处开始插入
- `a`:从当前目标所在的下一个字符处开始插入,`A`:从光标所在行的最后一个字符处开始插入
- `o`:在目前光标所在的下一行处插入新的一行,`O`:在目前光标所在处的上一行插入新的一行
- `Esc`:返回命令模式

## 末行模式 ##
从命令模式进入末行模式(last line mode),最常用的功能有保存,退出,查找,跳转行

* 保存和退出
  - `:w`    保存
  - `:q`    退出
  - `:q!`   强制退出,不保存
  - `:x`    保存并退出
  - `:wq`   保存并退出,与:x的区别是当文件没有内容修改时,仍会更新文件修改时间

* 行号
  - `:n` 跳转到第 n 行
  - `:set nu` 显示行号

* 搜索和替换
  - `/<parameter>` 向下查找
  - `?<parameter>` 向上查找
  检索到之后:
  - `n`下一个匹配对象
  - `N`上一个匹配对象
  - `:%s/<原对象>/<替换对象>/g`全部替换


## 在终端中使用 vi ##
有终端的地方就有 vi,输入`set -o vi`就可以在当前会话中使用 vi 命令

- 双击`esc`进入vi模式中的命令模式
- 使用`k|j`显示上下条历史命令
- `/<parameter>`可以对历史命令进行检索
- 将`set -o vi`写入配置文件`~/.bashrc`中
- 进入命令模式后,输入`vi|va|vo`等进入一个临时文件,保存退出后内容作为命令立即执行

## 锁死 ##

`ctrl+s` 会导致假死
`ctrl+q` 退出

---------
![脑图](vi使用.png)
