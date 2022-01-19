**第2章 Java基本语法**

> Java系列整理自尚硅谷_宋红康老师

[TOC]

# 2.1 关键字和保留字

关键字：被Java 语言赋予了特殊含义，用做专门用途的字符串（单词）。关键字中所有字母都为小写。

| 类型                                     | 示例                                                         |
| ---------------------------------------- | ------------------------------------------------------------ |
| 定义数据类型的关键字                     | class interface enum byte short int long float double char boolean void |
| 定义流程控制的关键字                     | if else switch case default while do for break continue return |
| 定义访问权限修饰符的关键字               | private protected public                                     |
| 定义类，函数，变量修饰符的关键字         | abstract final static synchronized                           |
| 定义类与类之间关系的关键字               | extends implements                                           |
| 定义建立实例及引用实例，判断实例的关键字 | new this super instanceof                                    |
| 异常处理的关键字                         | try catch finally throw throws                               |
| 其他修饰符关键字                         | package import                                               |



保留字：现有Java版本尚未使用，但以后版本可能会作为关键字使用。自己命名标识符时要避免使用这些保留字

# 2.2 标识符

Java 对各种**变量**、 **方法**和**类**等要素命名时使用的字符序列称为标识符

合法标识符规则

- 由26 个英文字母大小写，0-9  ，_ 或 $  组成

- 数字不可以开头。

- 不可以使用关键字和保留字，但能包含关键字和保留字。

- Java 中严格区分大小写，长度无限制。

- 标识符不能包含空格。

Java名称命名规范

- 包类：多单词组成时所有字母小写。xxxyyyzzz
- 类名、接口名：多单词组成时，所有单词的首字母大写。XxxYyyZzz
- 变量名、方法名：多单词组成时，第一个单词首字母小写。第二个单词开始时每个单词首字母大写。xxxYyyZzz
- 常量名：所有字母大写。多单词时每个单词用下划线连接。XXX_YYY_ZZZ

# 2.3 变量

## 2.3.1基本数据类型

### 变量的概念

- 内存中的一个存储区域
- 该区域的数据可以在同一类型范围内不断变化
- 变量是程序中最基本的存储单元。包含变量类型、变量名和存储的值

使用注意

- **Java中每个变量必须先声明，后使用**
- 使用变量名来访问这块区域的数据
- 变量的作用域：其定义所在的一对{ }内
- 变量只有在其作用域内才有效
- 同一个作用域内，不能定义重名的变量

声明变量

- 语法：<数据类型> <变量名称>


```java
int var;
```

变量赋值

- 语法：<变量名称> = <值>


```java
var = 10;
```

声明和赋值变量

- 语法：<数据类型> <变量名称> = <初始化值>


```java
int var = 10;
```

### 变量的分类-按数据类型

对于每一种数据都定义了明确的具体数据类型（强类型语言），在内存中分
配了不同大小的内存空间。

![数据类型](D:\Typora\Java 尚硅谷_宋红康\第2章 Java基本语法\数据类型.png)

#### 整数类型：byte, short, int, long

- Java整型常量默认为int型，声明long型常量后须加'l'或'L'

- Java程序中**整型变量通常默认声明为int型**，除非不足以表示较大的数，才用long

  ```java
  public class Variable Test {
      public static void main(String[] args) {
          int number1;
          number1 = 10;
  
          int number2;
          number2 = 20;
  
         int number3;
         number3 = number1 + number2;
         System.out.println("Number3 = " + number3);
   
         int number4 = 50;
         int number5 = number4 - number3;
         System.out.println("Number5 = " + number5);
      }
  }
  ```

#### 浮点类型：float, double

- 浮点型常量有两种表示方式

  十进制数形式：5.12 512.0f .512

  科学计数法形式：5.12e2 512E2 100E-2

- flout：单精度，尾数可以精确到7位有效数字。声明float型时，须后加'f'或'F'。
- double：双精度，精度是float的两倍。**Java浮点型默认采用此类型**。

#### 字符型：char

Java中所有字符都是用Unicode编码，UI个字符可以储存一个字母、一个汉字，或其他书面语的一个字符。

三种表现形式

- 字符常量是用单引号(' ')括起来的单个字符。

  ```java
  char ca = 'a';
  char c2 = '中';
  char c2 = '9';
  ```

- Java中允许使用转义字符‘\’来将其后的字符转变为特殊字符型常量

  ```java
  char c4 = '\n'; //'\n'表示换行符
  ```

- 直接使用Unicode值‘\uXXXX’来表示字符型常量

  ```java
  char c5 = '\u000a'; //'\n'
  ```

  | 转义字符 | 说明   |
  | -------- | ------ |
  | \b       | 退格符 |
  | \n       | 换行符 |
  | \r       | 回车符 |
  | \t       | 制表符 |
  | \\"      | 双引号 |
  | \\'      | 单引号 |
  | \\\      | 反斜线 |

#### 字符串类型：String

String不是基本数据类型，属于引用数据类型，使用方式与基本数据类型一致。

```java
String str = 'abcd';
```

一个字符串可以串接另一个字符串，也可以直接串接其他类型的数据

```java
str = str + 'xyz';
int n = 100;
str = str + n;
```

String Test类

```java
public class String Test {
    public static void main(String[] args) {
        int no = 10;
        String str = "abcdef";
        String str1 = str + “xyz” + no;

        str1 = str1 + "123";
        char c = '国';

        double pi = 3.1416;
        str1 = str1 + pi;
        boolean b = false;
        str1 = str1 + b;
        str1 = str1 + c;

	System.out.println("str1 = " + str1);
    }
}
```

#### 布尔类型：boolean

boolean类型用来判断逻辑条件，一般用于程序流程控制：

- if条件控制语句
- while循环控制语句
- do-while循环控制语句
- for循环控制语句

boolean类型数据只允许取值true/false，无null

- 不可以使用0/非0代替false/true，这点与C语言不同。
- JVM中没有任何供boolean值专用的字节码指令，Java语言表达所操作的boolean值，在编译之后都使用java虚拟机中的int数据类型来代替：true用1表示，false用0表示。

### 变量的分类-按声明位置不同（第4章面向对象）

在方法体外，类体内声明的变量称为成员变量。

在方法体内部声明的变量称为局部变量

![所有变量](D:\Typora\Java 尚硅谷_宋红康\第2章 Java基本语法\所有变量.png)

二者在初始化值方面的异同

- 同：都有生命周期

- 异：局部变量除形参外，需显式初始化

## 2.3.2基本数据类型变量间转换

### 自动类型转换

- 容量小的类型自动转换为容量大的数据类型。
- 数据类型容量排序：char=byte=short<int<long<float<double
- **byte,short,char之间不会相互转换**，他们三者在计算时首先转换为int类型。
- boolean类型不能与其它数据类型运算。
- 当把任何基本数据类型的值和字符串(String)进行连接运算时(+)，基本数据类型的值将自动转化为字符串(String)类型。

### 强制类型转换

- 自动类型转换的逆过程，将容量大的数据类型转换为容量小的数据类型。使用时要加上强制转换符：()，但可能造成精度降低或溢出,格外要注意。

- 通常，字符串不能直接转换为基本类型，但通过基本类型对应的包装类则可以实现把字符串转换成基本类型。

- boolean类型不可以转换为其它的数据类型。

  ```java
  /* 判断是否能通过编译 */
  //1
  short  s = 5;
  s = s-2;                       //判断：no 结果应该是int型
  
  //2
  byte b = 3;
  b = b + 4; //判断：no
  b = (byte)(b+4); //判断：yes
  
  //3
  char c = ‘a’;
  int i = 5;
  float d = .314F;
  double result = c+i+d;     //判断：yes
  
  //4
  byte b = 5;
  short s = 3;
  short t = s + b; //判断：no
  ```

  

## 2.3.3 String类型变量的使用

- String属于引用数据类型

- 声明String类型变量时，使用一对 “ ”

- String可以和8种基本数据类型变量做运算，且运算只能是连接运算

  ```java
  class String Test {
      public static void main(String[] args) {
          String s1 = "Hello World!";
          System.out.println(s1);
          String s2 = "a";
          String s3 = " ";     
      }
  }
  ```

## 2.3.4 基本数据类型与String间转换

```java
class String Test {
    public static void main(String[] args) {
        int number = 1001;
        String numberStr = "学号：";
        boolean b1 = true;
        String info = numberStr + number + b1; // +：连接运算
        System.out.println(info);
        
      	//练习1
        char c = 'a';
        int num = 10;
        String str = "hello";
        System.out.println(c + num + str);  // 107hello ASCⅡ a=97
        System.out.println(c + str + num); // ahello10
        System.out.println(c + (num + str)); // a10hello
        System.out.println((c + num) + str); // 107hello
        System.out.println(str + num + c); // hello10a
        
        //练习2
        //输出“*	*”
        System.out.println("*	*"); //*	*
        System.out.println('*' + '\t' + '*'); //93
        System.out.println('*' + "\t" + '*'); //*	*
        System.out.println('*' + '\t' + "*"); //51*
        System.out.println('*' + ('\t' + "*"));//*	*
    }
}
```



## 2.3.5 进制与进制间的转换

| 进制     | 表示方法         |
| -------- | ---------------- |
| 二进制   | 以0b或0B开头表示 |
| 八进制   | 以0开头表示      |
| 十进制   |                  |
| 十六进制 | 以0x或0X开头表示 |



# 2.4 运算符

运算符是一种特殊符号，用以表示数据的运算、复制和比较等。

## 2.4.1 算术运算符

| 运算符 | 运算         |
| ------ | ------------ |
| +      | 正号         |
| -      | 负号         |
| +      | 加           |
| -      | 减           |
| *      | 乘           |
| 、     | 除           |
| %      | 取模（取余） |
| ++     | 自增         |
| --     | 自减         |
| +      | 字符串连     |

- 如果对负数取模，可以把模数负号忽略不记，如：5%-2=1。 但被模数是负数则不可忽略。此外，取模运算的结果不一定总是整数。
- 对于除号“/”，它的整数除和小数除是有区别的：整数之间做除法时，只
  保留整数部分而舍弃小数部分。 例如：int x=3510;x=x/1000*1000;  x的结果是？
- “+”除字符串相加功能外，还能把非字符串转换成字符串.例如：System.out.println(“5+5=”+5+5);  //打印结果是？ 5+5=55 ?

## 2.4.2 赋值运算符

符号：= 

- 当“=”两侧数据类型不一致时，可以使用自动类型转换或使用强制类型转换原则进行处理。
- 支持连续赋值。
- 扩展赋值运算符： +=, -=, *=, /=, %=

## 2.4.3 比较运算符（关系运算符）

| 运算符     | 运算               |
| ---------- | ------------------ |
| ==         | 等于               |
| !=         | 不等于             |
| <          | 小于               |
| >          | 大于               |
| <=         | 小于等于           |
| >=         | 大于等于           |
| instanceof | 检查是否是类的对象 |

- 比较运算符的结果都是boolean型，也就是要么是true，要么是false。

## 2.4.4 逻辑运算符

| 逻辑运算符 | 运算     |
| ---------- | -------- |
| &          | 逻辑与   |
| \|         | 逻辑或   |
| !          | 逻辑非   |
| ^          | 逻辑异或 |
| &&         | 短路与   |
| \|\|       | 短路或   |

真值表

| a     | b     | a&b   | a\|b  | a^b   | a&&b  | a\|\|b |
| ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| true  | true  | true  | true  | false | true  | true   |
| true  | false | false | true  | true  | false | true   |
| false | true  | false | true  | true  | false | true   |
| false | false | false | false | false | false | false  |

- 逻辑运算符用于连接布尔型表达式，在Java中不可以写成3<x<6，应该写成x>3 & x<6 。
- “&”和“&&”的区别
  - 单&时，左边无论真假，右边都进行运算；
  - 双&时，如果左边为真，右边参与运算，如果左边为假，那么右边不参与运算(惰性运算)
- “|”和“||”的区别同理，||表示：当左边为真，右边不参与运算。
- 异或( ^ )是：当左右都为true时，结果为false；左右都为false时，结果为true

## 2.4.5 位运算符

| 位运算符 | 运算       | 范例                  |
| -------- | ---------- | --------------------- |
| <<       | 左移       | 3<<2=12 -> 3\*2\*2=12 |
| >>       | 右移       | 3>>1=1 -> 3/2=1       |
| >>>      | 无符号右移 | 3>>>1=1 -> 3/2=1      |
| &        | 与运算     | 6&3=2                 |
| \|       | 或运算     | 6\|3=7                |
| ^        | 异或运算   | 6^3=5                 |
| ~        | 取反运算   | ~6=7                  |



## 2.4.6 三元运算符

- 语法：( 条件表达式)? 表达式1 ：表达式2 ；

  - 表达式1 和表达式2 为 同种类型
  - 三元运算符与if-else 的联系与区别：
    - 三元运算符可简化if-else语句
    - 三元运算符要求必须返回一个结果。
    - if后的代码块可有多个语句

  运算符的优先级

  | 最高 |        | .   ()    {}    ;    ,         |
  | :--: | ------ | ------------------------------ |
  |      | R -> L | *    /    %                    |
  |      | L -> R | +    -                         |
  |      | L -> R | <<    >>    >>>                |
  |      | L -> R | <    >  <=    >=    instanceof |
  |      | L -> R | ==    !=                       |
  |      | L -> R | &                              |
  |      | L -> R | ^                              |
  |      | L -> R | !                              |
  |      | L -> R | &&                             |
  |      | L -> R | \|\|                           |
  |      | R -> L | ?  :                           |
  |      | R -> L | =    *=     /=    %=           |
  |      |        | +=    -=    <<=    >>=         |
  | 最低 |        | >>>=    &=    ^=    \|=        |

  

# 2.5 程序流程控制

## 2.5.1 顺序结构

Java中定义成员变量时采用合法的前向引用。

## 2.5.2 分支结构

### if-else 结构

- 三种语法格式

```java
//1
if(条件表达式){
    执行代码块;
}

//2
if(条件表达式){
    执行代码块1;
}
else{
    执行代码块2;
}

//3
if(条件表达式1){
    执行代码块1;
}
else if(条件表达式2){
    执行代码块2;
}
......
else{
    执行代码块n;
}
```

- 条件表达式必须是布尔表达式（关系表达式或逻辑表达式）、布尔变量
- 当多个条件是“互斥”关系时，条件判断语句及执行语句间顺序无所谓；
  当多个条件是“包含”关系时，“小上大下 / 子上父下”

```java
//案例
public class AgeT est{
    public static void main(String args[]){
        int age = 75;
        if (age< 0) {
        	System.out.println("不可能！");
        } else if (age>250) {
        	System.out.println("是个妖怪！");
        } else {
        	System.out.println(“人家芳龄 " + age +" ,马马乎乎啦！");
        }
    }
}
```

### switch-case 结构

- 语法

```java
switch( 表达式){
case 常量1:
    语句1;
    // break;
case 常量2:
    语句2;
    // break;
… …
case 常量N:
    语句N;
    // break;
default:
    语句;
    // break;
} 
```

- switch(表达式)中表达式的值 必须是下述几种类型之一：byte ，short ，char ，int ， 枚举 (jdk 5.0) ，String (jdk 7.0)
- case子句中的值必须是 常量，不能是变量名或不确定的表达式值；
-  default子句是 可任选 的。同时，位置也是灵活的。当没有匹配的case时，执行default
- 使用switch-case的，都可以改写为if-else

```java
//案例
String season = "summer";
switch (season) {
case "spring":
	System.out.println("春暖花开");
	break;
case "summer":
	System.out.println("夏日炎炎");
	break;
case "autumn":
	System.out.println("秋高气爽");
	break;
case "winter":
	System.out.println("冬雪皑皑");
	break;
default:
	System.out.println("季节输入有误");
	break;
}
```

## 2.5.3 循环结构

在某些条件满足的情况下，反复执行特定代码的功能

### for循环

- 语法

```java
for ( 初始化部分;  循环条件部分;  迭代部分) ｛
	 循环体部分;
 ｝
```

```java
//案例
public class ForLoop {
    public static void main(String args[]) {
        int result = 0;
        for (int i = 1; i <= 100; i++) {
            result += i;
        }
        System.out.println("result=" + result);
    }
}
```

### while循环

- 语法

```java
初始化部分
while( 循环条件部分) ｛
 循环体部分;
 迭代部分;
}
```

```java
//案例
public class WhileLoop {
    public static void main(String args[]) {
        int result = 0;
        int i = 1;
        while (i <= 100) {
            result += i;
            i++;
        }
        System.out.println("result=" + result);
    }
}
```

### do-while循环

- 语法

```java
初始化部分;
do{
 循环体部分
 迭代部分
}while( 循环条件部分);
```

- do-while 循环至少执行一次循环体 。

```java
//案例
public class DoWhileLoop {
    public static void main(String args[]) {
        int result = 0, i = 1;
        do {
            result += i;
            i++;
        } while (i <= 100);
        System.out.println("result=" + result);
    }
}
```

## 2.5.4特殊关键字的使用

### break

- break语句用于终止某个语句块的执行。
- break语句出现在多层嵌套的语句块中时，可以通过标签指明要终止的是哪一层语句块

### continue

- continue只能使用在循环结构中
- continue语句用于跳过其所在循环语句块的 一 次执行，继续下一次循环
- continue语句出现在多层嵌套的循环语句体中时，可以通过标签指明要跳过的是哪一层循环

### return

-  return并非专门用于结束循环的，它的功能是结束一个方法。当一个方法执行到一个return语句时，这个方法将被结束。
- 与break和continue不同的是，return直接结束整个方法，不管这个return处于多少层循环之内。