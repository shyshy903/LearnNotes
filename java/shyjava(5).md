---
type: blog
title: Java学习笔记（五）
categories: java
data: 2019-11-26 23:30
tags: java
---

# 方法
## 方法的定义
```java
MethodDeclaration:
	MethodHeader MethodBody
MethodHeader:
	Modifiersopt ResultType Identifier(FormalParameterListopt) Throwsopt
Modifiers:
	public protected private static abstract final
	synchronized native strictfp
ResultType:
	Type
	void
MethodBody:
	{ statements }

public static int max(int num1, int num2) {
    int result = 0;
    if(num1 > num2)
        result = num1;
    else
        result = num2;

    return result;
}

```
- 方法签名(Method Signature)指方法名称、参数类型、参数数量和返回类型。一个类中不能包含签名相同或仅返回类型不同的多个方法。
- 方法头中声明的变量称为形参(formal parameter)。当调用方法时，可向形参传递一个值，这个值称为实参(actual parameter / argument)。形参可以使用final进行修饰，表示方法内部不允许修改该参数。
- 形参不允许有默认值，最后一个可为变长参数（可用…或数组定义，参见第7章数组）。方法不允许static局部变量。
- 方法可以有一个返回值(return value)。如果方法没有返回值，返回值类型为void，但构造函数确实没有返回值。

## 方法的调用
- 声明方法只给出方法的定义。要执行方法，必须调用(call/invoke)方法。
- 如果方法有返回值，通常将方法调用作为一个值来处理（可放在一个表达式里）。
```java
int large = max(3, 4) * 2;  
System.out.println(max(3,4));
如果方法没有返回值，方法调用必须是一条语句。
System.out.println(“Welcome to Java!”);
```
- 当调用方法时，程序控制权转移至被调用的方法。当执行return语句或到达方法结尾时，程序控制权转移至调用者。
- 调用当前类中的静态方法：可直接用“方法名”，也可用”类名.方法名“；实例函数中也可用” 方法名“或”this.方法名“调用。
- 调用其它类中的静态方法：必须用”类名.方法名“或”对象.方法名“调用；子类实例函数也可用” super.方法名“调用父类方法。
- 所有静态方法提倡用”类名.方法名“调用。如`Math.sin(3.0)`

```java
public class TestMax {
	public static void main(String[] args) {
		int i = 5;
		int j = 2;
		int k = max(i, j);
		System.out.println("The maximum between " + i + " and " + j + " is " + k);
	}

	public static int max(int num1, int num2) {
		int result;
		result = (num1 > num2) ?num1:num2;
		return result ;
	}
}
```
## 调用程序栈
每当调用一个方法时，系统将参数、局部变量存储在一个内存区域中，这个内存区域称为调用堆栈(call stack)。当方法结束返回到调用者时，系统自动释放相应的调用栈。
<div align = center>
<img src = "https://img.vim-cn.com/9c/1276a008ebc0f1d635060c80096666064be1de.png">
</div>

## 方法的参数传递
- 如果方法声明中包含形参，调用方法时，必须提供实参。
实参的类型必须与形参的类型兼容：如父类形参可用子类实参。
实参顺序必须与形参的顺序一致。
```java
public static void nPrintln(String message, int n) {  
  for (int i = 0; i < n; i++)
    System.out.println(message);
}

nPrintln(“Hello”, 3); //正确
nPrintln(3, “Hello”); //错误
```

- 当调用方法时，基本数据类型的实参值的副本被传递给方法的形参。方法内部对形参的修改不影响实参值。(Call by value)
对象类型的参数是引用调用（Call by reference）

```java
public class TestPassByValue {
	
	public static void main(String[] args) {
		int num1 = 1;
		int num2 = 2;
		System.out.println("调用swap方法之前：num1 = " + num1 + "，num2 = " + num2);
		
		swap(num1, num2);
		System.out.println("调用swap方法之后：num1 = " + num1 + "，num2 = " + num2);
	}

	public static void swap(int n1, int n2) {
		System.out.println("\t在swap方法内：");
		System.out.println("\t\t交换之前：n1 = " + n1 + "，n2 = " + n2);

		int temp = n1;
		n1 = n2;
		n2 = temp;

		System.out.println("\t\t交换之后：n1 = " + n1 + "，n2 = " + n2);
	}
}

```
## 方法的重载
- 方法重载(overloading)是指方法名称相同，但方法签名不同的方法，仅返回类型不同的方法不可重载。一个类中可以包含多个重载的方法。
- 当调用方法时，Java编译器会根据实参的个数和类型寻找最合适的方法进行调用。
- 调用时匹配成功的方法可能多于一个，则会产生编译二义性错误，称为歧义调用(ambiguous invocation）
**重载示例**
```java
public class TestMethodOverloading {
	
	/** Return the max between two int values */
    public static int max(int num1, int num2) {
        public class TestMethodOverloading {
        
        /** Return the max between two int values */
            public static int max(int num1, int num2) {
                    return (num1 > num2) ？num1:num2; 	
            }

        /** Return the max between two double values */
            public static double max(double num1, double num2) {
                    return (num1 > num2) ？num1:num2;
            }

            /** Return the max among three double values */
            public static double max(double num1, double num2, double num3) {
                    return max(max(num1, num2), num3);
            }
        }
    }
}
public class TestMethodOverloading {
	 /** Main method */
	public static void main(String[ ] args) {
		// Invoke the max method with int parameters
		System.out.println("The maximum between 3 and 4 is "
				+ max(3, 4));

		// Invoke the max method with the double parameters
		System.out.println("The maximum between 3.0 and 5.4 is " 
				+ max(3.0, 5.4));

		// Invoke the max method with three double parameters
		System.out.println("The maximum between 3.0, 5.4, and 10.14 is " 
				+ max(3.0, 5.4, 10.14));
	} 	
}

```
**有歧义的重载**
```java
public class AmbiguousOverloading {
        public static void main(String[ ] args) {
	//System.out.println(max(1, 2));  //该调用产生歧义
        }        //以下任一函数的参数都相容（都能自动转换），编译无法确定用哪个函数

        public static double max(int num1, double num2) {
		if (num1 > num2)
			return num1;
		else
			return num2;
        }
       public static double max(double num1, int num2) {
		if (num1 > num2)
			return num1;
		else
			return num2;
	}
}
```

## 局部变量的作用域
方法内部声明的变量称为局部变量(local variable)。
局部变量的作用域(scope)指程序中可以使用该变量的部分。局部变量的生命期和其作用域相同。
局部变量的作用域从它的声明开始，直到包含该变量的程序块结束。局部变量在使用前必须先赋值。
在方法中，可以在不同的非嵌套程序块中以相同的名称多次声明局部变量。但不能在嵌套的块中以相同的名称多次声明局部变量：无法访问外部块变量。
在for语句的初始动作部分声明的变量，作用域是整个循环。在for语句循环体中声明的变量，作用域从变量声明开始到循环体结束
```java
public class TestLocalVariable {
	public static void method1( ) {
		int x = 1; int y = 1;
		for (int i = 1; i < 10; i++) {
			x += i;  
		}
		for (int i = 1; i < 10; i++) {
			y += i;              //正确：两个循环未嵌套，都可用i
		}
	}
	//错误，变量i在嵌套的语句块中声明
	public static void method2( ) {
//		int i = 1;
//		int sum = 0;
//		for (int i = 1; i < 10; i++) {//java不允许函数的局部变量或参数的作用域被覆盖
//			sum += i;          //无法访问外部块局部变量
//		}
	}
}
```
**全局变量的声明与使用**
```java
public  class args {  
     public static String username; // 全局变量
     public static String password; //全局变量
}
>> args.username
>> args.password
```