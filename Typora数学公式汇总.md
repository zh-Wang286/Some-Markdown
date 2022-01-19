**Typora数学公式汇总**

[toc]



### 插入公式块 

Ctrl+Shift+M 或 $$

### 基础运算

a+b-c\*d $(a+b)-c*d$

a\div{b} $a\div{b}$

a\pm{b} $a\pm{b}$

\frac{a}{b} $\frac{a}{b}$

\sqrt{s} $\sqrt{s}$

\log_2^{10} $\log_2^{10}$

\ln15 $\ln15$

\pm \times \div \neq \leq \geq

$\pm$   $\times$   $\div$   $\neq$   $\leq$   $\geq$  

### 三角函数

\sin{\alpha} $\sin{\alpha}$

\cos{\beta} $\cos\beta$

\tan{\theta} $\tan\theta$

### 上下标

x^2 $x^2$

x_1 $x_1$

### 无穷

\infty $\infty$

-\infty $-\infty$

### 统计

\overline{x} $\overline{x}$

\hat{Y} $\hat{Y}$

### 向量

\vec{a}\cdot\vec{b} $\vec{a}\cdot\vec{b}$

### 微积分

\int_3^2 x^2{\rm d}x $\int_3^2 x^2{\rm d}x$

\iint $\iint$

\iiinf $\iiint$

\oint $\oint$

\partial^2y $\partial^2y$

### 方程组

```tex
\begin{cases}
3x+5y+z\\
7x-y+3\\
-6x+3y+9z
\end{cases}
```

$$
\begin{cases}
3x+5y+z\\
7x-y+3\\
-6x+3y+9z
\end{cases}
$$

```Tex
f(n)=
\begin{cases}
n/2, & \text{if $n$ is even}\\
3n+1,& \text{if $n$ is odd}
\end{cases}
```

$$
f(n)=
\begin{cases}
n/2, & \text{if $n$ is even}\\
3n+1,& \text{if $n$ is odd}
\end{cases}
$$



### 大型运算符

\sum_{i=1}^{n}{a_i}  
$$
\sum_{i=1}^{n}{a_i}
$$


\prod_{i_1}^{n}{a_1} 
$$
\prod_{i_1}^{n}{a_i}
$$
\lim_{a\rightarrow+\infty}{a+b}
$$
\lim_{a\rightarrow+\infty}{a+b}
$$

### 矩阵

```tex
\begin{matrix}
1 & 2 & 3 \\
4 & 8 & 10\\
9 & 1 & 9
\end{matrix}
```


$$
\begin{matrix}

1 & 2 & 3 \\

4 & 8 & 10\\

9 & 1 & 9

\end{matrix}
$$

#### 带左右括号的矩阵

在`\begin{}`之前和`\end{}`之后添加左右括号的代码。{} [] ()

```tex
 \left[
 \begin{matrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{matrix}
  \right]
```

$$
\left[
 \begin{matrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{matrix}
  \right]
$$

#### 带分割符号的矩阵

```tex
\left[
    \begin{array}{cc|c}
      1&2&3\\
      4&5&6
    \end{array}
\right]
```

$$
\left[
    \begin{array}{cc|c}
      1&2&3\\
      4&5&6
    \end{array}
\right]
$$

#### 包含希腊字母与省略号的矩阵

```tex
 \left\{
 \begin{matrix}
 1      & 2        & \cdots & 5        \\
 6      & 7        & \cdots & 10       \\
 \vdots & \vdots   & \ddots & \vdots   \\
 \alpha & \alpha+1 & \cdots & \alpha+4 
 \end{matrix}
 \right\}
```

$$
 \left\{
 \begin{matrix}
 1      & 2        & \cdots & 5        \\
 6      & 7        & \cdots & 10       \\
 \vdots & \vdots   & \ddots & \vdots   \\
 \alpha & \alpha+1 & \cdots & \alpha+4 
 \end{matrix}
 \right\}
$$

#### 省略号

\dots	\cdots	\vdots	\ddots

$\dots$	$\cdots$	$\vdots$	$\ddots$

#### 行列式

```tex
 \left|
 \begin{matrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{matrix}
  \right|
```

$$
\left|
 \begin{matrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{matrix}
  \right|
$$



### 表

#### 简易表格

```tex
\begin{array}{|c|c|c|}
	\hline 2&9&4\\
	\hline 7&5&3\\
	\hline 6&1&8\\
	\hline
\end{array}
```


$$
\begin{array}{|c|c|c|}
	\hline 2&9&4\\
	\hline 7&5&3\\
	\hline 6&1&8\\
	\hline
\end{array}
$$

#### 框线表

```tex
\begin{array}{c|lcr}
n & \text{左对齐} & \text{居中对齐} & \text{右对齐} \\
\hline
1 & 0.24 & 1 & 125 \\
2 & -1 & 189 & -8 \\
3 & -20 & 2000 & 1+10i
\end{array}
```

$$
\begin{array}{c|lcr}
n & \text{左对齐} & \text{居中对齐} & \text{右对齐} \\
\hline
1 & 0.24 & 1 & 125 \\
2 & -1 & 189 & -8 \\
3 & -20 & 2000 & 1+10i
\end{array}
$$







### 附录：相关链接

[LaTeX支持手册Supported TeX/LaTeX commands](http://docs.mathjax.org/en/latest/input/tex/macros/index.html)

[LaTeX公式手册(全网最全)](https://www.cnblogs.com/1024th/p/11623258.html)

[Tex介绍文档（英文）](http://www.ctan.org/tex-archive/info/gentle/gentle.pdf)

[手画符号搜索 LaTeX 代码](http://detexify.kirelabs.org/classify.html)

