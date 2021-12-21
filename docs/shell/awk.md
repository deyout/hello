### 1 awk是用来截取列的

awk编程,相对于cut功能更加强大，cut有的awk都有,但比较复杂

`awk '条件1{动作1} 条件2{动作22}...'` 文件名

##### 1.1 cut

cut -d "分隔符" -f 第几列

cut -d "%" -f 1

##### 1.2BEGIN

BEGIN:在执行真正的处理之前执行的动作,所有的动作都要用单引号个起来。

```shell
[root@VM-16-9-centos ~]# df -h|grep vda1|awk 'BEGIN{printf"this is a trancript\n"}{print $5}'|cut -d "%" -f 1
this is a trancript
8
```

**处理第一行的时候加入BEGIN**

```
[root@VM-16-9-centos ~]# awk 'BEGIN{FS=":"}{print $1 "\t" $3}' /etc/passwd
root    0
bin     1
daemon  2
adm     3
lp      4
```

##### 1.3 END

**所有数据处理完了之后，会再执行一个动作**

> 随便写，写哪都行!!!





##### 1.5 grep

grep -v str,  -v 取反



```
grep是处理行的，你的需求要配合awk
格式是awk '{print $n,$m}' nm是自然数，列值。
例如：ls -l | awk '{print $9}'

上面是默认列分隔符为空格或者TAB的，如果分隔符是其他的字符，还需要加上-F
例如：
echo "a/b/c/d/e " |awk -F "/" '{print $1,$3}'
输出结果：a c
```





```
10.10.10.11 ansible_ssh_user=root ansible_ssh_pass=12 ansible_ssh_port=22
10.10.10.12 ansible_ssh_user=root ansible_ssh_pass=12 ansible_ssh_port=22
10.10.10.13 ansible_ssh_user=root ansible_ssh_pass=12 ansible_ssh_port=22
```

### 2.sort命令用法

> sort -t : -k1,1 /etc/passwd   ---以用户名称排序
> sort -t : -k3nr /etc/passwd   ---反向UID的排序
> -k3nr，3  ----从字段3起始开始，以数值类型反向排序，并结束于字段3的结尾
> sort -t ：-k4n -k3n  /etc/passwd ---以GID和UID排序
> sort -t : -k4n -u /etc/passwd    ---以唯一的GID排序
>
> 选项
> -u ：就是在输出行中去除重复行
> -r ：改成降序排序
> -o ：重定向文件
> -n ：按数值类排序

### 3.wc计算行数，字符数，字数

```
-l 行数
-w 字数
-c 字符数
```

### 4.提取开头或者结尾的行数

```
前10行
head -10
sed 10q
后10行
tail -10
tail -f 动态查看
```





