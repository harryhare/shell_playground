##

### grep 1
grep '\bthe\b'
grep -w 'the'

### grep 2
grep -i '\bthe\b'
grep -iw 'the'

### grep 3
grep -iv '\bthat\b'
grep -iwv 'that'


### grep 4
有括号的地方要加E
grep -Eiw '(the|that|then|those)'

### grep 5
grep '\([0-9]\) *\1'
grep -E '([0-9]) *\1' # 本地测试正确

### sed 1
sed 's/the /this /'
### sed 2
sed  's/thy /your /ig'

### sed 3
sed  's/thy/{&}/ig'
sed  -E 's/(thy)/{\1}/ig'

### sed 4
sed -E 's/\d{4} /**** /g'

### sed 5
sed -E 's/(\d{4}) (\d{4}) (\d{4}) (\d{4})/\4 \3 \2 \1/g'


### awk 1
awk '{if (NF < 4){print "Not all scores are available for "$1}}'

### awk2
awk '{if ($2>=50&&$3>=50&&$4>=50){print $1" : Pass"}else{print $1" : Fail"}}'

### awk3
awk '{avg=($2+$3+$4)/3; if(avg>=80){t="A"}else if(avg>=60){t="B"}else if(avg>=50){t="C"}else{t="FAIL"}; print $0" : "t}'

### awk4
paste -d ";" - -
awk 'ORS=NR%2?";":"\n"'

