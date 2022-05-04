## array

### 1
```bash

a=`cat`
echo $a


readarray a
a=(`cat`)
a=($(cat))
cat| read -a a
+
echo ${a[*]}
echo ${a[@]}


```



### 2
```bash
a=(`cat`)
echo ${a[@]:3:5}
```
### 3 字符串元素过滤
```bash
grep -vi a

arr=($(cat))
echo ${arr[@]/*[aA]*/}

```

### 4
```bash
array=($(cat))
echo ${array[@]} ${array[@]} ${array[@]}
```

### 5
```bash
a=(`cat`)
echo ${a[3]}
```

### 6
```bash
wc -l

a=(`cat`)
echo ${#a[*]}
```
## 7 字符串元素过滤 替换
```bash
a=(`cat`)
echo ${a[@]/[A-Z]/.}
```

### 8
```bash
read n
a=(`cat`)
for x in ${a[@]}; do
   # echo $x
   sum=$((sum^x))
done
echo $sum

read 
a=(`cat`)
a=${a[@]}
echo $((${a// /^}))
```
