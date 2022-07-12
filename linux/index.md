## user & group

相关文件
```text
/etc/passwd # 用户
/etc/group	# 组
/etc/shadow # 密码
/etc/skel/  # 创建用户时会copy到home目录中内容
```

让 passwd 的内容不晃眼
```text
cat /etc/paswd|column -t -s :
```

useradd
useradd -m xxx # 同时创建home 目类
userdel
usermod -a -G group username
passwd # 设置密码
passwd -l username # 锁定
passwd -u username # 解锁


groupadd
groupdel

visudo


