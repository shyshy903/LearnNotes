---
type: blog
title: Java学习笔记（三）
categories: java
data: 2019-11-25 23:00
tags: java
---
# Shy-Learnjava（3）基础
## 3 数学函数、字符与字符串
### 3.1 数学函数
**Math是final类：在java.lang.Math中，所有数学函数都是静态方法**
```java
# Math类中定义了常用的数学常量，如
PI : 3.14159265358979323846
E : 2.7182818284590452354
# 方法:注意都是静态函数
# 三角函数
sin, cos, tan, asin, acos, atan,toRadians,toDigrees
# 指数
exp, log, log10，pow, sqrt
# 取整
ceil, floor, round
# 其它
min, max, abs, random（[0.0,1.0))
```

**Math.random方法生成[0.0,1.0)之间的double类型的随机数**
```java
如：
（int）(Math.random( )*10);		//[0,10)
50+(int)(Math.random( )*50);		//[50,100)
一般地
a+(int)(Math.random( )*b)              //返回[a, a+b)
a+(int)(Math.random( )*（b+1）)       //返回[a, a+b]
```
**编写生成随机字符的方法**
```java
Java中每个字符对应一个Unicode编码从0000到FFFF。  
在生成一个随机字符，就是产生一个从0到65535之间的随机数。  
所以, 计算表达式为：

(int)(Math.random( ) * (65535 + 1)) 。

英文大、小写字母的Unicode是一串连续的整数，如
‘a’的统一码是:   	
(int)‘a’=97
由于char类型可自动地被转换为int类型，所以我们可以对应使用如下整数值：
‘a’=97, ‘b’=98， …, ‘z’=122

因此，随机生成从‘a’-‘z’之间的字符就等于生成‘a’-‘z’之间的随机数，可用
‘a’+（int）(Math.Random( ) * (‘z’-’a’+1))

将上面讨论一般化，按如下表达式，可以生成任意2个字符ch1和ch2（ch1<ch2）之间的随机字符

(char)(ch1+(int)(Math.rabdom()*(ch2-ch1+1)))

```
### 3.2 字符数据类型
**Unicode和ASCII码**
```java
Java对字符采用16位Unicode编码，因此char类型的大小为二个字节
16位的Unicode用以\u开头的4位16进制数表示，范围从’\u0000’到’\uffff’,不能少写位数
Unicode包括ASCII码，从’\u0000’到’\u007f’对应128个ASCII字符
JAVA中的ASCII字符也可以用Unicode表示，例如
char letter = ‘A’；
char letter = ‘\u0041’；//等价，\u后面必须写满4位16进制数
++和--运算符也可以用在char类型数据上，运算结果为该字符之后或之前的字符，例如下面的语句显示字符b
char ch = ‘a’;
System.out.println(++ch);  //显示b
```
**特殊字符转义**
```java
和C++一样，采用反斜杠(\)后面加上一个字符或者一些数字位组成转义序列，一个转义序列被当做一个字符
如\n  \t  \b  \r  \f  \\  \'  \"

如果想打印带””的信息 He said “Java is fun “
System.out.println(“He said \”Java is fun \””); 
```
**字符型和数据型的转换**
```java
char类型数据可以转换成任意一种数值类型，反之亦然。将整数转换成char类型数据时，只用到该数据的低16位，其余被忽略。例如
char ch = （char）0xAB0041；
       System.out.println(ch);	//显示A
要将浮点数转成char时，先把浮点数转成int型，然后将整数转换成char
       char ch = （char）65.25；
       System.out.println(ch);	//显示A
当一个char型转换成数值型时，这个字符的Unicode码就被转换成某种特定数据类型
       int i = （int）‘A’；
       System.out.println(i);		//显示65

如果转换结果适用于目标变量（不会有精度损失），可以采用隐式转换；否则必须强制类型转换
 int i = ‘A’；
 byte b = （byte）‘\uFFF4’;  //取低8位二进制数
所有数值运算符都可以用在char型操作数上，  
如果另一个操作数是数值，那么char型操作数就自动转换为数值；  
如果另外一个操作数是字符串，那么char型操作数会自动转换成字符串再和另外一个操作数字符串相连
      int i = ‘2’+ ‘3’;
      System.out.println（i）；  // i为50+51=101
      int j = 2 + ‘a’；	       //j = 99
      System.out.println(j + “ is the Unicode of ”+ (char)j);//99 is the Unicode of  c

```
**字符的比较测试**
```java
两个字符可以通过关系运算符进行比较，如同比较二个数值：通过字符的Unicode值进行比较
Java为每个基本类型实现了对应的包装类，char类型的包装类是Character类。注意包装类对象为引用类型，不是值类型
Character类的作用
将char类型的数据封装成对象
包含处理字符的方法和常量
方法
isDigit方法判断一个字符是否是数字
isLetter方法判断一个字符是否是字母
isLetterOrDigit方法判断一个字符是否是字母或数字
isLowerCase方法判断一个字符是否是小写
isUpperCase方法判断一个字符是否是大写
toLowerCase方法将一个字符转换成小写
toUpperCase方法将一个字符转换成大写

```
## 3.3 String 类，一个final类
```java
java.lang.String表示一个固定长度的字符序列，实例化后字符不能改。
构造函数
长度(length)
获取字符(charAt)
连接(concat)
截取(substring)
比较(equals, equalsIgnoreCase, compareTo, startWith),
endWith, regionMatch)
转换(toLowerCase, toUpperCase, trim, replace)
查找(indexOf, lastIndexOf)
字符串和数组间转换(getChars, toCharArray), getChars返回void,超出长度就异常
字符串和数字间转换(valueOf)

```
**String类对象的构造**
```java
从字面值创建字符串
String newString = new String(stringLiteral);
例如：
String message = new String("Welcome to Java");
由于字符串经常使用，java提供了创建字符串的简写形式。
String newString = stringLiteral;
例如：
String m1 = “Welcome”;  //m1和m2中的字符都是不可修改的
String m2 = “Welcome”;  //故m1和m2可以优化引用同一常量：m1==m2
String m3 = "Wel" +"come";//m1==m2==m3  
String m4 = "Wel" +new String("come"); //m1!=m4

字符串对象创建之后，其内容是不可修改的。
String s = “java”;
s = “HTML”;
String t =s; 

```

**字符串的比较**
```java
equals方法用于比较两个字符串是否包含相同的内容（字符序列）:
两个字符串内容相同，返回true
两个字符串内容不同，返回false
比较字符串内容不能直接比较二个引用变量，比较二个引用变量只是判断这二个引用变量是否指向同一个对象
equalsIngnoeCase忽略大小写比较内容是否相同
regionMatch比较部分内容是否相同
startsWith判断是否以某个字符串开始
endsWith判断是否以某个字符串结束
compareTo方法用于比较两个字符串的大小，即第一个不同字符的差值。s1.compareTo(s2)的返回值:
当两个字符串相同时，返回０
当s1按字典排序在s2之前，返回小于０的值
当s1按字典排序在s2之后，返回大于０的值
String s0 = "Java";
String s1 = "Welcome to " + s0;
String s2 = "Welcome to Java";
String s3 = "welcome to java";
String s6 = "Welcome to Java";

// equals用于比较两个字符串的内容是否相同
System.out.println("s1.equals(s2) is " + s1.equals(s2)); //true

// equalsIgnoreCase忽略大小写
System.out.println("s2.equals(s3) is " + s2.equals(s3)); //false
System.out.println("s2.equalsIgnoreCase(s3) is " + s2.equalsIgnoreCase(s3)); //true

// regionMatches比较部分字符串: 给定两个串的起始位置和长度
System.out.println("s2.regionMatches(11, s0, 0, 4) is " + s2.regionMatches(11, s0, 0, 4)); //true
System.out.println("s3.regionMatches(11, s0, 0, 4) is " + s3.regionMatches(11, s0, 0, 4));//false
System.out.println("s3.regionMatches(true, 11, s0, 0, 4) is " + s3.regionMatches(true, 11, s0, 0, 4));//true,忽略大小写
String s0 = "Java";
String s1 = "Welcome to " + s0;
String s2 = "Welcome to Java";
String s3 = "welcome to java";
String s6 = "Welcome to Java";

// startsWith判断是否以某个字符串开始
// endsWith判断是否以某个字符串结束
System.out.println("s2.startsWith(s0) is " + s2.startsWith(s0));//false
System.out.println("s2.endsWith(s0) is " + s2.endsWith(s0));  //true
        
// compareTo根据字典排序比较两个字符串
String s4 = "abc";
String s5 = "abe";
System.out.println("s4.compareTo(s5) is " + s4.compareTo(s5));//-2
```
**字符串方法**
```java
调用length( )方法可以获取字符串的长度。
例如：
message.length( )返回15
charAt(index)方法可以获取指定位置的字符。index必须在0到s.length()-1之间。
例如：
message.charAt(0)返回字符’W’
concat方法用于连接两个字符串。例如：
String s3 = s1.concat(s2);
使用加号(+)连接两个字符串。例如：
String s3 = s1 + s2;
s1 + s2 + s3 等价于s1.concat(s2).concat(s3)
连接操作返回一个新的字符串：因为String类型的实例不可修改。
substring用于截取字符串的一部分，返回新字符串。
public String substring(int beginIndex, int endIndex)
返回字符串的子串。子串从beginIndex开始，直到endIndex-1
public String substring(int beginIndex)
返回字符串的子串。子串从beginIndex开始，直到字符串的结尾。
toLowerCase将字符串转换成小写形式，得到新串
toUpperCase将字符串转换成大写形式，得到新串
trim删除两端的空格，得到新串
replace字符替换，得到新串
String s0 = "Java";
String s1 = " Welcome to Java ";

// toLowerCase将字符串转换成小写形式
System.out.println("s1.toLowerCase() is " + s1.toLowerCase());
        
// toUpperCase将字符串转换成大写形式
System.out.println("s1.toUpperCase() is " + s1.toUpperCase());
        
// trim删除两端的空格
System.out.println("s1.trim() is " + s1.trim( ));
        
// replace字符替换
System.out.println(“s1.replace(s0, \”HTML\“) is ” + s1.replace(s0, “HTML”)); //Welcome to HTML
// indexOf返回字符串中字符或字符串匹配的位置，返回-1表示未找到。
"Welcome to Java".indexOf('W') returns 0
"Welcome to Java".indexOf('x') returns -1
"Welcome to Java".indexOf('o‘,5) returns 9
"Welcome to Java".indexOf("come") returns 3
"Welcome to Java".indexOf("Java", 5) returns 11
"Welcome to Java".indexOf("java", 5) returns -1
"Welcome to Java".lastIndexOf('a') returns 14
```
```java
toCharArray将字符串转换成字符数组
	String s = “Java”;
	char[ ] charArray = s.toCharArray( );// charArray.length=4
将字符数组转换成字符串
使用String的构造函数，可同时初始化
	new String(new char[ ] {‘J’,‘a’,‘v’,‘a’} );
使用valueOf方法
	String.valueOf(new char[ ] {‘J’,‘a’,‘v’,‘a’});
	String.valueOf(2.34);
valueOf方法将基本数据类型转换为字符串。例如
	String s1 = String.valueOf(1.0);  //“１.0”
	String s2 = String.valueOf(true); //“true”
字符串转换为基本类型
	Double.parseDouble(str)
	Integer.parseInt(str)
	Boolean.parseBoolean(str)
回文是指顺读和倒读都一样的词语。例如“mom”,  “dad”, ”noon”都是回文。编写程序，判断一个字符串是否是回文。

public class CheckPalindrome {
    public static boolean isPalindrome(String s) {		
	// The index of the first character in the string		
	int low = 0;		
	// The index of the last character in the string		
	int high = s.length( ) - 1;		
	while (low < high) {			
		if (s.charAt(low) != s.charAt(high)) return false; // Not a palindrome	
		low++;			
		high--;		
	}		
	return true; // The string is a palindrome	
    }
}
public class CheckPalindrome {
	/** Main method */	
	public static void main(String[] args) {		
		// Prompt the user to enter a string		
		String s = JOptionPane.showInputDialog("Enter a string:");		
		String output = "";		
		if (isPalindrome(s))			
			output = s + " is a palindrome";		
		else			
			output = s + " is not a palindrome";		
		// Display the result		
		JOptionPane.showMessageDialog(null, output);	
	}
}
```
**StringBuilder与StringBuffer**
```java
String类一旦初始化完成，字符串就是不可修改的。
StringBuilder与StringBuffer(final类）初始化后还可以修改字符串。
StringBuffer修改缓冲区的方法是同步的，更适合多任务环境。
StringBuilder在单任务模式下与StringBuffer工作机制类似。
由于可修改字符串， StringBuilder 与StringBuffer 增加了String类没有的一些函数，例如：append、insert、delete、replace、reverse、setCharAt等。
仅以StringBuilder为例：
StringBuilder  stringMy=new StringBuilder( );
StringMy.append(“Welcome to”);
      StringMy.append(“ Java”);
StringBuffer用于处理可变内容的字符串。
append方法在字符串的结尾追加数据
insert方法在指定位置上插入数据
reverse方法翻转字符串
replace方法替换字符
toString方法返回String对象
capacity方法返回缓冲区的容量
length方法返回缓冲区中字符的个数
setLength方法设置缓冲区的长度
charAt方法返回指定位置的字符
setCharAt方法设置指定位置的字符
所有对StringBuffer对象内容进行修改的方法，都返回指向相同StringBuffer对象的引用
StringBuffer bf = new StringBuffer();
StringBuffer bf1 = bf.append("Welcome "); 
StringBuffer bf2 = bf.append("to ");
StringBuffer bf3 = bf.append("Java");
assert(bf==bf1 && bf==bf2 && bf == bf3);
因此以上语句可以直接写成：
bf.append("Welcome ").append("to ").append("Java");
// 追加
StringBuffer bf = new StringBuffer();
bf.append(“Welcome”);
bf.append(‘ ‘);
bf.append(“to ”);
bf.append(“Java”);
System.out.println(bf.toString()); //Welcome to Java
//插入
bf.insert(11,”HTML and ”) //Welcome to HTML and JAVA
//删除
bf.delete(8,11); //Welcome Java
bf.deleteCharAt(8);//Welcome o Java
bf.reverse(); //avaJ ot emocleW
bf.replace（11，15，“HTML”）;//Welcome to HTML
bf.setCharAt(0,’w’);//welcome to java

toString(): 从缓冲区返回字符串
capacity()：返回缓冲区容量。length <= capacity
    当字符串长度超过缓冲区容量，capacity会自动增加
length()：返回缓冲区中字符数量
setLength(newLength)：设置缓冲区长度
charAt(index)：返回下标为index的字符

// 编写程序，检查回文，并忽略不是字母和数字的字符。
解决方案
创建一个新的StringBuffer，将字符串的字母和数字添加到StringBuffer中，返回过滤后的String对象。
翻转过滤后的字符串，并与过滤后的字符串进行比较，如果内容相同则是回文。

public static boolean isPalindrome(String s) {		
		
// Create a new string that is the reversal of s
	String s2 = reverse(s);		
// Compare if the reversal is the same as the original string		return s2.equals(s);	
}

public static String reverse(String s) {		
	StringBuffer strBuf = new StringBuffer(s);		
	strBuf.reverse();		
	return strBuf.toString();	
}

```

## 3.4 格式化控制台输入输出
```java
JDK1.5提供了格式化控制台输出方法
System.out.printf(format, item1, item2, …);
格式化字符串
String.format(format, item1, item2, …);
格式描述符
%b 布尔值
%c 字符
%d 十进制整数
%f 浮点数
%e 科学计数法
%s 字符串
String.format(“格式$：%1$d,%2$s”, 99,“abc”); //结果”格式$：99，abc“

public class TestPrintf {
    public static void main(String[] args) {
        System.out.printf("boolean : %6b\n", false);
        System.out.printf("boolean : %6b\n", true);
        System.out.printf("character : %4c\n", 'a');
        System.out.printf("integer : %6d, %6d\n", 100, 200);
        System.out.printf("double : %7.2f\n", 12.345);
        System.out.printf("String : %7s\n", "hello");
    }
}
```