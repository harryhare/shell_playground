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


 