# 参考
https://wangdoc.com/bash/index.html

##
set
-u 不存在的变量报错
-x 打印语句
-e error 退出
-E -e的情况下error 会被trap 捕获
-f 字符串扩展，-o noglob
-o pipefail pipeline 中间的error 也会被捕获


##
函数内生命的变量是全局变量，局部变量用 local 声明
和 python 刚好相反，python 的全局变量要用 global 声明

##
type  用来查看命令本身的类型
which

##
子bash 不继承环境变量，所以 source 和 直接运行才有区别
source 是在当前 bash 中运行，所以当前bash变量不用export
而直接运行是 在子bash 中运行，所以当前的bash 变量需要export 才能被读到


##
alias 查看所有别名
declare -p 所有变量
declare -F  查看所有函数名
declare -f 查看完整函数
set 查看所有变量和函数

##
echo 识别转义字符需要加选项 -e 
echo -e "\ta"
 
 
##
ls -- "-a"

##
let 可以声明 整型变量
let a=1

##
pushd
popd
dirs

##
'': 所有转义都无效
"": $ `` \ 依然生效

##
Here 文档
<<
<<<

<< token
text
token

$ md5sum <<< 'ddd'
 等同于
$ echo 'ddd' | md5sum


##
文件名扩展 ？* [] [[:class:]] 量词
[a,b,c] [a-z]

注：
{} 不是文件名扩展

{a..z}{0..9}{9..0}

$ echo {001..5}
001 002 003 004 005

##
字符类 [[:class:]]

[[:alnum:]]：匹配任意英文字母与数字
[[:alpha:]]：匹配任意英文字母
[[:blank:]]：空格和 Tab 键。
[[:cntrl:]]：ASCII 码 0-31 的不可打印字符。
[[:digit:]]：匹配任意数字 0-9。
[[:graph:]]：A-Z、a-z、0-9 和标点符号。
[[:lower:]]：匹配任意小写字母 a-z。
[[:print:]]：ASCII 码 32-127 的可打印字符。
[[:punct:]]：标点符号（除了 A-Z、a-z、0-9 的可打印字符）。
[[:space:]]：空格、Tab、LF（10）、VT（11）、FF（12）、CR（13）。
[[:upper:]]：匹配任意大写字母 A-Z。
[[:xdigit:]]：16进制字符（A-F、a-f、0-9）。

###
量词
?(pattern-list)：模式匹配零次或一次。
*(pattern-list)：模式匹配零次或多次。
+(pattern-list)：模式匹配一次或多次。
@(pattern-list)：只匹配一次模式。
!(pattern-list)：匹配给定模式以外的任何内容。
 