# 游戏地址
https://www.hackerrank.com/domains/shell

## bash
### 1
```bash
echo HELLO
```

### 2
```bash
for (( i=1; i<100; i=i+2 )); do
  echo $i
done

```

### 3
```bash
read name
echo Welcome $name
```

### 4
有无空格均可
```bash
for ((i=1;i<=50;i=i+1)); do
  echo $i
done
```


### 5
```bash
read x
read y
echo $(($x+$y))
echo $(($x-$y))
echo $(($x*$y))
echo $(($x/$y))
```



### if 的说明

表达式本身的值 和 表达式的返回值 不同

$ true
$ echo $?
0
$ false
$ echo $?
1


$ ((3>2))
$ echo $?
0
$ ((3<2))
$ echo $?
1


$ if false; then echo test; fi
$ if true; then echo test; fi
test

算数表达式可以直接做判断
$ if ((3>2)); then echo true; fi
true

### 6
```bash
read x
read y

if (($x<$y)); then
    echo X is less than Y
elif (($x>$y)); then
    echo X is greater than Y
else
    echo X is equal to Y    
fi
```

### 字符串说明
算数逻辑运算用 (( ))
字符串 和 数组 用 { }
正则用 [[ ]]

$ x=Aa
$ echo ${x,,}
aa
 echo ${x^^}
AA


### 7

```bash
# 方法一： 转换大小写
read c
if [ ${c,,} == "y" ]; then
    echo YES
elif [ ${c,,} == "n" ]; then
    echo NO
fi 

# 方法二： 正则
read c
if [[ $c =~ ^[Y|y]$ ]]; then
    echo YES
elif [[ $c =~ ^[N|n]$ ]]; then
    echo NO
fi 
```

### 8
```bash
read x
read y
read z

if (($(($x==$y))&&$(($y==$z)))); then
	echo EQUILATERAL
elif  (($(($x==$y))||$(($y==$z))||$(($z==$x)))); then
	echo ISOSCELES
else
	echo SCALENE
fi
```

### 9
```bash
# 只支持整数
read exp
echo $(($exp))

# 精度不对
read exp
echo "scale=3; $exp"|bc

# 别人的答案
read num
echo $num | bc -l | xargs printf "%.3f"

printf "%.3f" "$(bc -l)"
```


### 10

```bash
read n
sum=0
for (( i=0; i<$n; i=i+1 )); do
  read x
  sum=$(($sum+$x))
done
echo "$sum/$n" | printf "%.3f" "$(bc -l)"

```
### 11
```bash
function make_empty_row() {
    local empty_row
    for ((i=0;i<100;i++)); do
        empty_row+="_"
    done
    echo $empty_row
}

function set_string_i(){
    str=$1
    n=$2
    t=$3
    echo ${str:0:n}$3${str:n+1}
}
function make_empty_graph(){
    for ((i=0;i<63;i++)); do
        graph[i]=$(make_empty_row)
    done
}

function print_graph(){
    for r in ${graph[@]}; do
        echo $r
    done
}
function fill_graph(){
    local begin=$1
    local step=$2
    local phase=$3
    local center=$4
    for ((i=0;i<step;i++)); do
        current=${graph[begin]}
        new=$(set_string_i $current $center 1)
        graph[begin]=$new
        begin=$begin-1
    done
    local left=$center
    local right=$center
    for ((i=0;i<step;i++)); do
        left=$left-1
        right=$right+1
        line=${graph[begin]}
        line=$(set_string_i $line $left 1)
        line=$(set_string_i $line $right 1)
        graph[begin]=$line
        begin=$begin-1
    done
    phase=$(($phase-1))
    if (($phase>=1));then
        step=$(($step/2))
        fill_graph $begin $step $phase $left
        fill_graph $begin $step $phase $right
    fi
}
# a=$(make_empty_row)

# echo $a

# b=$(set_string_i $a 2 1)

# echo $b

make_empty_graph
#print_graph|cat
read n
fill_graph 62 16 $n 49
print_graph|cat

```






