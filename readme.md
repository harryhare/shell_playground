# 参考
https://wangdoc.com/bash/index.html

##
set
-u 不存在的变量报错
-x 打印语句
-e error 退出
-E -e的情况下error 会被trap 捕获
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
delare -p 所有变量
declare -F  查看所有函数名
declare -f 查看完整函数
set 查看所有变量和函数

 