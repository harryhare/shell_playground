# 游戏地址
https://www.hackerrank.com/domains/shell

## text
### 1
```bash
while read str; do
	echo ${str:2:1} 
done


cut -c3 $1

cut -c3

```
### 2
```bash
while read str; do
    echo ${str:1:1}${str:6:1} 
done


cut -c2,7

```

### 3
```bash
cut -c2-7
```

### 4
```bash
cut -c0-4
```

### 5
默认分割符是 tab
```bash
cut -f1-3
```
### 6

```bash
cut -c13-
```
### 7
```bash
cut  -d ' ' -f4
```

### 8
```bash
cut -d ' ' -f-3
```

### 9
```bash
cut -f2-
```

### 10

```bash
head -n 20
```

### 11
```bash
head -c 20
```

### 12
head 的 减号-是 除掉尾部 的行数
tail 的 加号+是 除掉头部 的行数

```bash
head -n 22|tail -n 11

head -n 22|tail -n +12
```
### 13
```bash
tail -n 20
```
### 14
```bash
tail -c 20
```

### 15 替换字符
```bash
tr "()" "[]"
```

### 16 删除字符
```bash
tr -d "a-z" 
```

### 17 压缩空格
```bash
tr -s " "
```

### 18 字母序
```bash
sort
```

### 19 字母倒序
```bash
sort
```
### 20 大小排序
```bash
sort -n
```
### 21 大小倒序
```bash
sort -nr 
```
### 22 指定分隔符，某一列
```bash
sort -t $'\t' -k 2 -rn
```
### 23
```bash
sort -t $'\t' -k2 -n
```

### 24
```bash
sort -t $'|' -k2 -rn
```

### 25
```bash
uniq
```

### 26
```bash
uniq -c | cut -c7-
```
### 27 忽略大小写
```bash
uniq -ic | cut -c7-
```

### 28 只出现一次
```bash
uniq -u
```
对应的还有只保留多次的
uniq -d

### 29 

```bash
tr '\n' '\t'

paste -s

```
### 30 三个一行
```bash
paste - - -
```

### 31用分号分割
```bash
paste -d ';' -s
```
### 32
```bash
paste -d ';' - - -
```