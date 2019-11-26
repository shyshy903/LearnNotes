---
type: blog
title: Java学习笔记（四）
categories: java
data: 2019-11-26 23:00
tags: java
---
# 循环
## while循环
```java
int i = 0;
while (i < 100) {
    System.out.println(“Welcome to Java!”);
    i++;     //必须有语句改变循环条件
}

```

## do while循环
```java
"""
循环体至少执行一次
"""
do
		statement or block
	while (loop-continuation-condition);

```

## for 循环
```java
for (int i = 0; i < 100; i++) {
    System.out.println(“Welcome to Java!”);
}

for循环头中的每个部分可以是零个或多个以逗句分隔的表达式。
for (int i = 0, j = 0; i + j < 10; i++, j++) {
    System.out.println(“Welcome to Java!”);
}

如果for循环中的loop-continuation-condition被省略，则隐含为真。
for (;;) {                   while(true) {
    //do something  等价于        //do something
}                            }

```
## break 与 continue
```java
break //跳出循环
continue //跳出当前循环，继续循环
```

## JDK1.5 增强的for循环
```java
JDK 1.5引入新的for循环，可以不用下标就可以依次访问数组元素。语法：

for(elementType value : arrayRefVar) {
}

例如
for(int i = 0; i < myList.length; i++) {
	 sum += myList[i];
}

for(double value : myList) {
	sum += value;
}

```