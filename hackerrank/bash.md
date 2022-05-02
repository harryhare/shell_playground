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
字符串运输用 { }
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





