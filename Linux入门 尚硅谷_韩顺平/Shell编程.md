> Linux系列整理自尚硅谷_韩顺平老师

## shell 脚本的执行方式

脚本格式要求

脚本以 `#!/bin/bash` 开头

脚本需要有可执行权限

## 常用执行方式

赋予脚本 x 权限，然后执行脚本

```bash
chmod 744 myShell.sh
./myShell.sh
```

## shell 变量

### 变量介绍

系统变量`$HOME`, `$PWD`, `$SHELL`, `$USER` 等用户自定义变量 显示当前所有变量 `set`

### shell 变量的定义

#### 基本语法

定义变量：`变量=值`

撤销变量：`unset 变量`

声明静态变量：`readonly 变量`

注意：静态变量不能 `unset`

#### 应用实例

定义变量/撤销变量

```bash
A=100
echo "A=$A"
unset A
```

声明静态变量

```bash
readonly A=99
echo "A=$A"
```

### 定义变量的规则

变量名称可以由字母、数字和下划线组成，但是不能以数字开头

等号两侧不能有空格

变量名称一般习惯大写

### 将命令的返回赋给变量

```bash
A=`ls -la` 反引号，把结果返回给变量 A
A=\$(ls -la) 等价于反引号
```

## 设置环境变量

```bash
export 变量名=变量值 （将 shell 变量输出为环境变量）
source 配置文件（让修改后的配置信息立即生效）
echo $ 变量名（查询环境变量的值）
```

为了让`/etc/profile` 的环境变量生效，需要使用 `source/etc/profile` 重启系统或注销用户

应用实例

在`/etc/profile` 文件中定义 `TOMCAT_HOME` 环境变量

```bash
TOMCAT_HOME=/opt/tomcat
export TOMCAT_HOME
```

查看环境变量 `TOMCAT_HOME` 的值

```bash
echo $TOMCAT_HOME
```

在另一个 shell 程序中使用 `TOMCAT_HOME`

```bash
echo "tomcathome=\$TOMCAT_HOME"
```

## 位置参数变量

### 介绍

当我们执行一个 shell 脚本时，如果希望获取到命令行的参数信息，就可以使用到位置参数变量

### 基本语法

| 位置参数 | 功能描述                                                     |
| :------- | :----------------------------------------------------------- |
| `$n`     | n 为数字，$0 代表命令本身，`$1-$9` 代表第一到第九个参数，十以上的参数，十以上的参数需要用大括号包含，如 `${10}`。 |
| `$*`     | 这个变量代表命令行中所有的参数，`\$*`把所有的参数看成一个整体。 |
| `$@`     | 这个变量也代表命令行中所有的参数，不过 `$@`把每个参数区分对待。 |
| `$#`     | 这个变量代表命令行中所有参数的个数。                         |

### 应用实例

```bash
在一个 shell 脚本中简单使用一下预定义变量
#!bin/bash
#获取到各个参数
echo "$0 $1 $2"
echo "$*"
echo "$@"
echo "参数个数=\$#"
```

## 预定义变量

### 基本介绍

| 预定义变量 | 功能描述                                                     |
| :--------- | :----------------------------------------------------------- |
| `$$`       | 当前进程的进程号 PID                                         |
| `$!`       | 后台运行的最后一个进程的进程号                               |
| `$?`       | 最后一次执行的命令的返回状态。如果变量值为 0，证明上一个变量正确执行；如果非 0，则执行不正确 |

### 应用实例

在一个 shell 脚本中简单使用一下预定义变量

```bash
#!bin/bash
echo "当前的进程号=$$"
#后台的方式运行 myShell.sh
./ myShell.sh &
echo "最后的进程号=$!"
echo "执行的值=$?"
```

## 运算符

基本语法

```bash
$((运算式)) 或 $[运算式]
expr m + n //运算符间要有空格
expr \*, /, % //乘，除，取余
```

应用实例

计算 (2+3)*4

```bash
#!bin/bash
RESULT1=$(((2+3)*4))
echo "result1=$RESULT1"

RESULT2=$[(2+3)*4]
echo "result2=$RESULT2"

TEMP=`expr 2 + 3`
RESULT3=`expr $TEMP \* 4`
echo "result3=$RESULT3"
```

## 条件判断

基本语法

```bash
[ condition ] #注意condition前后要有空格
// 非空返回true，可用 $?验证（0为true，非0为false）
```

应用实例

```bash
[ atguigu ] #返回true
[] # 返回false
[ condition ] && echo OK || echo notok #条件满足，执行后面的语句
```

### 常用的条件判断

#### 两个整数的比较

| 条件判断 | 功能描述   |
| :------- | :--------- |
| =        | 字符串比较 |
| -lt      | 小于       |
| -le      | 小于等于   |
| -eq      | 等于       |
| -gt      | 大于       |
| -ge      | 大于等于   |
| -ne      | 不等于     |

#### 按照文件权限进行判断

| 条件判断 | 功能描述     |
| :------- | :----------- |
| -r       | 有读的权限   |
| -w       | 有写的权限   |
| -x       | 有执行的权限 |

#### 按照文件类型进行判断

| 条件判断 | 功能描述                     |
| :------- | :--------------------------- |
| -f       | 文件存在并且是一个常规的文件 |
| -e       | 文件存在                     |
| -d       | 文件存在并是一个目录         |

#### 应用实例

案例 1："ok"是否等于"ok"

```bash
if [ "ok100" = "ok" ]
then
  echo "equal"
fi
```

案例 2：23 是否大于等于 22

```bash
if [ 23 -ge 22 ]
then
  echo "大于"
fi
```

案例 3：/root/shell/aaa.txt 目录中的文件是否存在

```bash
if [ -e /root/shell/aaa.txt ]
then
  echo "存在"
fi
```

## 流程控制

### if 判断

基本语法

```bash
if [ 条件判断式 ]
then
  程序
elif [ 条件判断式 ]
then
  程序
fi
//注意：[ 条件判断式 ]，中括号和条件判断式之间必须有空格
```

应用实例

编写一个 shell 程序，如果输入的参数，大于等于 60，则输出 "及格了"，如果小于 60，则输出 "不及格"

```bash
#!/bin/bash
if [ $SCORE -ge 60 ]
then
  echo "及格了"
elif [ $SCORE -l 60 ]
then
  echo "不及格"
fi
```

### case 语句

基本语法

```bash
case $ 变量名 in
"值1"）
  如果变量的值等于值1，则执行程序1
;;
"值2"）
  如果变量的值等于值2，则执行程序2
;;
…省略其他分支…
*）
  如果变量的值都不是以上的值，则执行此程序
;;
esac
```

应用实例

当命令行参数是 1 时，输出 "周一", 是 2 时，就输出"周二"， 其它情况输出 "other"

```bash
case $1 in
"1")
  echo "周一"
;;
"2")
  echo "周二"
;;
*)
  echo "other"
esac
```

### for 循环

基本语法 1

```bash
for 变量 in 值1 值2 值3…
do
  程序
done
```

基本语法 2

```bash
for (( 初始值;循环控制条件;变量变化))
do
  程序
done
应用实例
```

案例 1 ：打印命令行输入的参数[这里可以看出$*和$@的区别

```bash
for i in "$*"
do
  echo "the sum is $i"
done

  echo "=====分割线====="
for j in "$@"
do
  echo "the sum is $j"
done
```

案例 2 ：从 1 加到 100 的值输出显示

```bash
SUM=0
for((i=1;i<=100;i++))
do
  SUM=$[$SUM+$i]
done
echo "sum=$SUM"
```

### while 循环

基本语法

```bash
while [ 条件判断式 ]
do
  程序
done
```

应用实例

从命令行输入一个数 n，统计从 1+...+ n 的值是多少？

```bash
SUM=0
i=0
while [ $i -le $1 ]
do
  SUM=$[$SUM+$i]
i=$[$i+1]
done
echo "sum=$SUM"
```

## 读取控制台输入 read

### 基本语法

```bash
read [选项] (参数)
```

| 选项 | 功能描述                                                     |
| :--- | :----------------------------------------------------------- |
| -p   | 指定读取值时的提示符                                         |
| -t   | 指定读取值时等待的时间（秒），如果没有在指定的时间内输入，就不再等待了 |

参数：指定读取值的变量名

### 应用实例

读取控制台输入一个 num 值，在 10 秒内输入。

```bash
read -t 10 -p "请输入一个数num2=" NUM2
echo "你输入的值是num2=$NUM2"
```

## 函数

### 系统函数

#### basename

功能：返回完整路径最后/ 的部分，常用于获取文件名 

基本语法

```bash
basename [pathname] [suffix]
basename [string] [suffix] #basename命令会删掉所有的前缀包括最后一个（‘/’）字符，然后将字符串显示出来。
```

suffix 为后缀，如果 suffix 被指定了，basename 会将 pathname 或 string 中的 suffix 去掉。

应用实例

请返回 `/home/aaa/test.txt` 的 "test.txt" 部分

```bash
basename /home/aaa/test.txt
basename /home/aaa/test.txt .txt
```

#### dirname

功能：返回完整路径最后/ 的前面的部分，常用于返回路径部分

基本语法

```bash
dirname 文件绝对路径 #从给定的包含绝对路径的文件名中去除文件名（非目录的部分），然后返回剩下的路径（目录的部分）
```

应用实例

请返回 `/home/aaa/test.txt` 的 `/home/aaa`

```bash
dirname /home/aaa/test.txt
```

### 自定义函数

基本语法

```bash
[ function ] funname[()]
{
Action;
[return int;]
}
调用直接写函数名：funname [值]
```

应用实例

计算输入两个参数的和，getSum

```bash
#!/bin/bash
function getSum() {
SUM=$[$n1+$n2]
echo "和是 $SUM"
}
read -p "请输入第一个数n1" n1
read -p "请输入第二个数n2" n2
#调用getSum $na $n2
```

