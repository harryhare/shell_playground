### SHELL6 去掉空行

awk '{if($0){print $0}}'

### SHELL7 打印字母数小于8的单词
a=(`cat`)
for x in ${a[@]}; do
    if ((${#x}<8)); then
        echo $x
    fi
done

### SHELL8 统计所有进程占用内存大小的和
awk '{a+=$6}END{print a}'

### SHELL9 统计每个单词出现的个数
tr " " "\n"|sort|uniq -c|awk '{print $2" "$1}'|sort -n -k2
### SHELL10 第二列是否有重复
cut -d " " -f 2|sort|uniq -cd|sort -n -k1

### SHELL11 转置文件的内容
cut -d " " -f 1 nowcoder.txt| tr "\n" " "
cut -d " " -f 2 nowcoder.txt| tr "\n" " "

awk '{print $1}' nowcoder.txt | xargs
awk '{print $2}' nowcoder.txt | xargs

awk 'BEGIN{str1="";str2=""}{str1=str1$1" ";str2=str2$2" "}END{print(str1,"\n",str2)}' 


awk '{
    for(i=1;i<=NF;i++){rows[i]=rows[i]$i" "}
} END{
    for(line in rows){print rows[line]}
}'

### SHELL12 打印每一行出现的数字个数
-F "" 和在BEGIN 中设置 FS="" 一样

awk -F "[1-5]" '
BEGIN{
    sum=0
} 
{    
    print "line"NR" number:"(NF-1) ;
    sum+=(NF-1)
}
END{
    print "sum is "sum 
}
'

awk -F "" 'BEGIN{count=0; sum=0}
{
    count=0;
    for(i=1;i<=NF;++i){
        if($i==1 || $i==2 || $i==3 || $i==4 || $i==5){
            count+=1;
        }
    }
     sum += count;
     printf("line%d number:%d\n",NR,count);
}
END{
    printf("sum is %d\n",sum);
}'



awk 'BEGIN{FS="";count=0; sum=0}
{
    count=0;
    for(i=1;i<=NF;++i){
        if($i==1 || $i==2 || $i==3 || $i==4 || $i==5){
            count+=1;
        }
    }
     sum += count;
     printf("line%d number:%d\n",NR,count);
}
END{
    printf("sum is %d\n",sum);
}'

### SHELL13 去掉所有包含this的句子
grep -ivw "this"

### SHELL14 求平均值
read n
let sum=0
for ((i=0;i<n;i++)); do
    read x
    sum=$(($sum+$x))
done
echo $sum/$n|printf "%.3f" `bc -l`


awk '{if(NR!=1)sum+=$0}END{printf("%.3f",sum/(NR-1))}'

### SHELL15 去掉不需要的单词
grep -iv b

### SHELL16 判断输入的是否为IP地址
awk -F "." '{
    str="yes";
    if(NF!=4){
        str="error";
    }else{
        for(i=1;i<=4;i++){
            if($i>=256){
                str="no";
                break;
            }
        }
    }
    print(str);
}'

### SHELL17 将字段逆序输出文件的每行
awk -F ":" '{line=$1;for(i=2;i<=NF;i++){line=$i":"line};print(line)}'

awk 'BEGIN{FS=OFS=":"}{for(i=NF;i>1;i--){printf $i":"}print $1}'


### SHELL18 域名进行计数排序处理
sed -E 's/^http:\/\/([^/]*)\/.*$/\1/'|sort|uniq -c|cut -c7-|sort -k 1 -nr

### SHELL19 打印等腰三角形
echo '    *'
echo '   * *'
echo '  * * *'
echo ' * * * *'
echo '* * * * *'

### SHELL20 打印只有一个数字的行
grep -E '^[^0-9]*[0-9][^0-9]*$'

### SHELL21 格式化输出
printf "%'d\n"  `cat`

这个没看懂
sed -E ':a; s/([[:digit:]])([[:digit:]]{3})\>/\1,\2/; ta'

### SHELL22
awk -F ":" '{
    array[$1]=array[$1]"\n"$2
}END{
    for(i in array){
        print "["i"]" array[i]
    }
}'

awk -F ":" '{
    res[$1] = (res[$1] == "" ? $2 : (res[$1] "\n" $2))
}END{
    for(k in res){
        print "["k"]"
        print res[k]
    }
}'


### SHELL23 nginx日志分析1-IP统计
grep "23/Apr/2020"|cut -d " " -f1|sort|uniq -c|cut -c7-|sort -k1 -nr

### SHELL24 nginx日志分析2-统计某个时间段的IP
grep "23/Apr/2020:2[0-3]"|cut -d " " -f1|sort -u|wc -l

### SHELL25 nginx日志分析3-统计访问3次以上的IP
cut -d ' ' -f1| sort -r |uniq -c|awk '{if($1>3){print $1" "$2}}'

### SHELL26 nginx日志分析4-查询某个IP的详细访问情况
grep '192.168.1.22'|cut -d " " -f7|sort|uniq -c|cut -c7-

### SHELL27 nginx日志分析5-统计爬虫抓取404的次数
grep "Baiduspider"|grep 404|wc -l

### SHELL28 nginx日志分析6-统计每分钟的请求数
cut -d " " -f 4|cut -c14-18|sort|uniq -c|cut -c7-|sort -rn -k1

### SHELL29 netstat练习1-查看各个状态的连接数
read
tr -s " "|cut -d " " -f6|grep -E 'ESTABLISHED|TIME_WAIT|LISTEN'|sort|uniq -c|awk '{print $2" "$1}'|sort -rn -k2


### SHELL30 netstat练习2-查看和3306端口建立的连接
grep 3306|grep -i established|tr -s " "|cut -d " " -f 5|cut -d ":" -f1 |sort|uniq -c|awk '{print $1" "$2}'|sort -rn


awk -F "[ :]+" '/3306.*ESTABLISHED/{array[$6]++}END{for(i in array) print array[i],i}' | sort -nrk1

### SHELL31 netstat练习3-输出每个IP的连接数
awk -F "[ :]+" '/tcp/{array[$6]++}END{for(i in array){print i,array[i]}}'|sort -nrk2

### SHELL32 netstat练习4-输出和3306端口建立连接总的各个状态的数目
awk -F "[ :]+" '/3306.*ESTABLISHED/{array[$6]++;link++}END{printf("TOTAL_IP %d\nESTABLISHED %d\nTOTAL_LINK %d",length(array),link,link)}' 


### SHELL33 业务分析-提取值
echo -n serverVersion: 
grep "Server version" nowcoder.txt|cut -d ":" -f4
echo -n serverName: 
grep "Server number" nowcoder.txt|cut -d ":" -f4
echo -n osName: 
grep "OS Name" nowcoder.txt|cut -d ":" -f4|cut -d"," -f1 
echo -n osVersion: 
grep "OS Version" nowcoder.txt|cut -d ":" -f5

### SHELL34 ps分析-统计VSZ,RSS各自总和
awk '{vsz+=$5;rss+=$6}END{printf("MEM TOTAL\nVSZ_SUM:%.1fM,RSS_SUM:%.3fM",vsz/1024,rss/1024)}'