---
type: blog
title: Java学习笔记（一）
categories: java
data: 2019-11-24
tags: java
---

**从今天开始复习java**

# Shy-Learnjava（1）基础
## 0 编程风格
- **注释**
    1. 类和方法前使用文档注释
    2. 方法步骤前使用行注释。
- **命名**
    1. 变量和方法名使用小写，如果有多个单词，第一个单词首字母小写，其它单词首字母大写。
    2. 类名的每个单词的首字母大写。
    3. 常量使用大写，单词间以下划线分隔。
    4. 缩进、空格、块样式（在eclipse中使用ctrl+shift+f）

## 1 基本程序设计
- 编写一个程序
```java
public class ComputeArea{
    public static void main(String[] args){
        double raidus;
        double area;
        area = radius * raidus * 3.14
        System.out.println("The area of the circle of raius" + radius + "is" + area);
    }
}
```
### 1.1 标准输入与输出
- 标准输入
```java
System.out //标准输出流类OutputStrem的对象
System.in //标准输入流类InputStrem的对象
```
- Scanner类
```java
import java.util.Scanner
Scanner input = new Scanner(System.in)
double d = input.nextDouble();
// 方法有
nextByte()
nextShort()
nextInt()
nextLong()
nextFloat()
nextDouble()
next()  // 读入一个字符串
```
### 1.2 标识符、常量与变量
- 标识符命名规则
    * 标识符是由字母、数字、下划线(_)、美元符号($)组成的字符序列。
    * 标识符必须以字母、下划线(_)、美元符号($)开头。不能以数字开头。标识符不能是保留字。
    * 标识符不能为true、false或null等事实上的保留字（参见英文维基网）
    * 标识符可以为任意长度，但编译通常只接受前128字符
    * 例如：$2, area, radius, showMessageDialog是合法的标识符；2A, d+4是非法的标识符
- java保留字
```java
abstract	       default 		if	        	package	       	this   
assert       	        do              goto            	private         	throw   
boolean	        	double          implements	protected 	throws        
break 	        	else	        import	        	public	        	transient(非序列化)
byte	        	enum		instanceof	return        	true
case	        	extends		int	        	short	        	try
catch	        	false	        interface       	static	        	void
char	        	final           long            	strictfp(严格浮点)   	volatile          
class                 	finally		native(本地方法)     	super	        	while
const	        	float	        new     		switch	        
continue	        	for                     	null 	        	synchronized	 
```
- java常量
```java
final datatype CONSTANT_NAME = value;
//注意常量的声明和初始化必须同时完成
final double PI = 3.14159;
// 避免重复输入
// 便于程序修改
// 便于程序阅读
```
### 1.3 赋值语句与基本表达式
- 赋值语句
```java
// 赋值语句右读
i = j = k = 1;
//不要认为i, j, k的值不变，volatile类型的变量值可变
k = 1;
j = k;  
i = j;

//语法
datatype variable = expression;
//例如：
int x = 1;   //某些变量在申明时必须同时初始化：final int m=0;
int x = 1, y = 2;
//局部变量在使用前必须赋值。
int x, y;     //若是成员变量，x, y有默认值=0
y = x + 1; //局部变量无默认值则错error
```
### 1.4 java 数据类型
<div align=center>
<img src="https://img.vim-cn.com/bc/a351f0120d3312145a6fe46f6a96aa7a61273e.png">
</div>

- 数值数据类型
```java
整数
byte	8位带符号整数(-128 到 127)
short	16位带符号整数(-32768 到 32767)
int	32位带符号整数(-2147483648 到 2147483647)
long	64位带符号整数(-9223372036854775808 到9223372036854775807)

浮点数
float	32位浮点数(负数  -3.4×1038到-1.4×10-45 
                  正数  1.4×10-45到3.4×1038 )
double	64位浮点数(负数  -1.8×10308到-4.9×10-324
                 正数  4.9×10-324到1.8×10308)

加(+)、减(-)、乘(*)、除(/)、求余(%)：注意+，-的优先级较低
int a = 34 + 1;		// 35
double b = 34.0 – 0.1;	// 33.9
long c = 300 * 30;	            // 9000
double d = 1.0 / 2.0;	// 0.5: 此处为浮点除
int e = 1 / 2;		// 0: 此处为整除
byte f = 20 % 3;		// 2: 取余数
整数相除的结果还是整数，省略小数部分。
int i = 5 / 2			// 2
int j = -5 / 2 		// -2

字面值是直接出现在程序中的常量值。
int i = 34;
long k = 100000L; 
整数字面值
以0开头表示八进制，如035；以0x或0X开头表示十六进制，如0x1D,0X1d；以1-9开头表示十进制，如29
后缀字母：以l或L结尾表示long类型，如29L；其它表示int类型。
浮点数字面值
浮点数是包含小数点的十进制数，后跟可选的指数部分。如
	18.  1.8e1 .18E2
后缀字母：以d或D结尾或者无后缀表示double类型；以f或F结尾表示float类型

```
- 操作运算符
```java
常用简洁操作符, 结果均为右值。
	操作符		举例			等价于
	+=		i += 8			i = i + 8
	-=		f -= 8.0			f = f - 8.0
	*=		i *= 8			i = i * 8
	/=		i /= 8			i = i / 8
	%=		i %= 8			i = i % 8
递增和递减运算符：++, --。结果均为右值。
前缀表示先加(减)1后使用
后缀表示先使用后加(减) 1
    int i =10;             //i=++i + ++i; 结果为23
    int newNum= 10 * i++; 	//newNum = 100, i = 11
    int newNum= 10 * ++i; 	//newNum = 110, i = 11

```

- 数值类型转换
```java
如果二元操作符的两个操作数的数据类型不同，那么根据下面的规则对操作数进行转换：
如果有一个操作数是double类型，另一个操作数转换为double类型。
否则，如果有一个操作数是float类型，另一个操作数转换为float类型。
否则，如果有一个操作数是long类型，另一个操作数转换为long类型。
否则，两个操作数都转换为int类型。
数据转换总是向较大范围的数据类型转换，避免精度损失
long k = i * 3 + 4; //i变成int参与右边表达式计算，计算结果转long
double d = i * 3.1 + k / 2; //i转double， k/2转double


将值赋值给较大取值范围的变量时，自动进行类型转换。
byte → char→ short → int → long → float → double 
将值赋值给较小取值范围的变量时，必须使用强制类型转换(type casting)。语法：
	(datatype)variableName
	例如：
	float f = (float)10.1;		// 10.1是double类型
	int i = (int)f;			// 10
	int j = (int)-f;			// -10


``

- 字符数据类型
```java
char表示16位的单个Unicode字符。
char类型的字面值
以两个单引号界定的单个Unicode字符。如:'男','女'
可以用\uxxxx形式表示， xxxx为十六进制。如:'\u7537', '\u5973'
转义字符表示：\n   \t  \b  \r   \f   \\   \'   \"
例如：
char letter = 'A';
char numChar = '4';
如果想打印带””的信息 He said “Java is fun “
      System.out.println(“He said \”Java is fun \””); 
String表示一个字符序列，注意字符串是String类实现的，是引用类型
字符串的字面值是由双引号界定的零个或多个字符。
	"Welcom to java!"                 ""
连接运算：+, +=
加号用于连接两个字符串。如果其中一个不是字符串，则先将该操作数转换成字符串，再执行连接操作。
String message = "Welcome " + "to " + "java";  // Welcome to Java
String s = “Chapter” + 2; 		          // Chapter2：不能都是数值
String s1 += "Supplement" + 'B'; 		          // SupplementB  
message += " and Java is fun";  		// Welcome to Java and Java is fun
int i = 1;
int j = 2;
System.out.println("i + j = "  + i + j);	          // i+j=12
System.out.println("i + j = "  + (i + j));	          // i+j = 3

```
