---
type: blog
title: Java学习笔记（一）
categories: java
data: 2019-11-24
tags: java
---
# Shy-Learnjava（2）基础
## 2 选择
### 2.1 布尔类型和逻辑运算符
```java
boolean类型的值有真(true)或假(false)。
关系运算符: <, <=, >, >=, ==, !=
关系运算符的计算结果是boolean类型
boolean类型不能与其它数据类型混合运算
布尔运算符: !, &&, ||, ^, &, | 
&& , ||为条件逻辑运算符: (x>0) && (x<9)
&，|为无条件逻辑运算符，同时也是位操作符
^ 异或
```
<div align = center>
<img src = "https://img.vim-cn.com/80/4f17375d3236c4af37f9a0803b9272b11b99c5.png">
</div>

### 2.2 if语句
```java
if (radius >= 0) {
  area = radius * radius * PI;
  System.out.println("The area for the circle of radius " 
    + radius + " is " + area);
}

if (radius >= 0) {   
  area = radius * radius * 3.14159;
  System.out.println("The area for the circle of radius " 
    + radius + " is " + area);
} 
else {  System.out.println("Negative input");   }

if (score > 90.0)
    grade = ‘A’;
else if (score >= 80.0)
    grade = ‘B’;
else if (scroe >= 70.0)
    grade = ‘C’;
else if (score >= 60.0)
    grade = ‘D’;
else
    grade = ‘F’

// 高手的if
if (number % 2 == 0)
    even = true;
else
    even = false;//新手
等价于
even = (number % 2 == 0);//高手

if (even == true)
    System.out.println(“It is even.”);
等价于
if (even)
    System.out.println(“It is even.”);

```
### 2.3 条件语句
- swith语句
```java
switch(expression) {
    case value1 : 
        statement(s)
        break;
    case value2 : 
        statement(s)
        break;
    …
    default : 
        statement(s)
}
```

- 条件表达式
```java

max = (num1 > num2) ? num1 : num2;
```
### 2.4 操作符的优先级和表达式规则
```java
括号优先级最高，如果括号有嵌套，内部括号优先执行。
如果没有括号，则根据操作符的优先级和结合规则确定执行顺序。
如果相邻的操作符有相同的优先级，则根据结合规则确定执行顺序。
除赋值运算符之外的二元运算符都是左结合的。
赋值运算符和?:运算符是右结合的。
例如：
a+b-c+d  等价于 ((a+b)-c)+d
a=b+=c=5 等价于 a=(b+=(c=5))

操作符的优先级和结合规则只规定了操作符的执行顺序。操作数从左至右进行运算。
二元操作符左边的操作数比右边的操作数优先运算。例如：
int a = 0;
int x = a + (++a);
x的结果为1

int a = 0;
int x = (++a) + a;
x的结果为2
```
- 表达式规则
```java
规则
可能的情况下，从左向右计算所有子表达式
根据运算符的优先级进行运算
优先级相同的运算符，根据结合方向进行运算
3 + 4 * 4 > 5 * (4 + 3) - 1 的执行顺序为：
 3 + 4 * 4 > 5 * (4 + 3) - 1 
 3 + 4 * 4 > 5 * 7 – 1
 3 + 16 > 5 * 7 – 1
 3 + 16 > 35 – 1
 19 > 35 – 1
 19 > 34
 false
```