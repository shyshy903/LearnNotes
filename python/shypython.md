---
type: blog
title: Python学习笔记
categories: python
date: 2019-11-23
tags: python
---
# Shypython-learn-notes
## 1. python 数据类型
### 1.1 变量
**1.1.1 算术运算符**
```python
- 加减乘除+、-、*、/
- 取余、取整、取绝对值 %、//、abs()
- 最小、最大值 min()、max()
- 复数 complex(re,im)
- 取共轭 c.conjugate()
- 返回商和余数 divmod(x,y)  
```

**1.1.2 布尔运算符**
```python
-  小于、大于 < 、 >
- 等于、不等于 == 、 != 
- 与、或、非 and 、or 、not
```
**1.1.3 赋值运算符**
```python
- a=a+b  is  a+=b
- a=a-b  is  a-=b
- a=a*/b  is  a*/b
- a=a**(//)b  is  a**(//)=b
```

**1.1.4 位运算符**
```python
- 与或 & 、 |  
- 异或、取反 ^ 、~ 
- 左位移、右位移  <<   、 >>
```

**1.1.5 转义符**
```python
- 续行符 \
- 反斜杠符号 \\
- 引号 \'
- 响铃 \a
- 退格 \b
- 转义 \e
- 空 \000
- 换行 \n
- 纵向制表符 \v
- 横向制表符 \t
- 回车 \r
- 换页 \f
- 八进制 \oyy
- 十六进制 \xyy
```

### 1.2 字符串(不可变类型)
**1.2.1 切片操作**
```python
# 当索引为正数时，从0开始，当索引为负数时，从-1开始（从右往左）
- newstr = s[a:b:c]  从索引a开始到b ,每隔c取一个值，左开右闭
- newstr = s[0:]  
- newstr = s[:]  和上面的式子等价
- newstr = s[::-1] 实现字符串的逆序
```
**1.2.2 字符串运算及方法**
```python 
str = 'I LOVE PYTHON!!'
- 标准化字符串 r'str' 或者 repr(str)
- x in s 子字符串 
- s1 + s2 字符串连接 
- s*n 字符串副本的拼接 
- s[i] 字符串索引 
- str.index('s') 获得字符串s字符的索引位置
- len(s) 字符串长度 
- ord(str) 字符串的编码 
- chr(number) 返回某个编码得到的字符 
- str.spilt(', ') 字符串的分割 ,返回值是一个列表
- chr.join(list)  字符串编码的连接 , " ".join(list)
str = "www.runoob.com"
- print(str.upper())  把所有字符中的小写字母转换成大写字母
- print(str.lower())  把所有字符中的大写字母转换成小写字母
- print(str.capitalize()) 把第一个字母转化为大写字母，其余小写
- print(str.title())  把每个单词的第一个字母转化为大写，其余小写 
```
**1.2.3深入研究字符串的方法**
```python
str.find(x)  返回x的第一个字符出现的索引位置
str.count(x)  返回x出现的次数
str.replace('top','bot')  返回一个修改的副本
str.spilt()
tabel = str.maketrans('xyz','uvw') ; str.translate(table)  返回一个映射后的副本
str.strip()  返回字符串的一个副本，并且消除前后空格
```
### 1.3 列表（可变类型）
**1.3.1 list的内置方法**
```python
lst = [1,3,a,[4,5],6]
- list.append(x)  在尾部增加一个元素
- list.insert(x,i)  在索引i处添加一个元素
- list.index(x)  获得元素x的索引
- list.remove(x)  删除列表的原色
- list.pop(i)  弹出索引为i的元素并在列表中删除它
- list.clear() 清楚列表
- list.count(x) 返回列表x出现的次数
- list.sort() 对列表直接排序， 区别于排序函数 sorted()
- list.reverse() 对列表进行反转
- len(list)
- for item in list:   对列表的遍历
 ```
 **1.3.2 列表和字符串的相互转化**
 ```python 
 1. str >>>list 

str1 = "12345"
list1 = list(str1)
print list1
 
str2 = "123 sjhid dhi"
list2 = str2.split() #or list2 = str2.split(" ")
print list2
 
str3 = "www.google.com"
list3 = str3.split(".")
print list3
 
输出为：
['1', '2', '3', '4', '5']
['123', 'sjhid', 'dhi']
['www', 'google', 'com']

2. list >>>str
str4 = "".join(list3)
print str4
str5 = ".".join(list3)
print str5
str6 = " ".join(list3)
print str6
输出为：
wwwgooglecom
www.google.com
www google com
```
### 1.3 元组类型（不可变类型）
**1.3.1 元组的运算及操作**
```python
# 元组为不可修改的字符串
tuple = (2019,'a',(b,c),'science')
```
**1.3.2 元组与列表的转换**
```python
tuple = tuple(list)
list  = list(touple)
```
### 1.4 集合类型（消除关系重复元素）
```python
myset = ['nature','science']
set.add(x)
set.remove(X)
set.discard(X)
set.clear()
set.pop()
len(set)
in / not in
set.issubset(set2)  判断set是否是set2的子集，返回bool类型
set.isuperset(set2)  
set.union(set2)  计算并集
set.intersection(set2)  计算交集
set.difference(set2)  计算差集
set.symmetric_difference(set2)  计算对称差集
```

### 1.5 字典类型（键值对）
```python
mydict = {'a':1,'b':2,'c':3}
len(dict)
str(dict)
dict('a')  访问字典中键为a的值
dict.clear()
dict.items() 以列表形式返回可遍历的（键，值）元素数组
dict.keys() 以列表形式返回一个字典中的所有键
dict.values() 以字典形式返回一个字典中的所有值
``` 

## 2. 语句类型
### 2.1 if 语句
```python 
if <条件>：
    pass
elif <条件>：
    pass
else:
    pass
```
### 2.2 while语句
```python
while <条件>：
    pass
# 死循环
while 1:
    pass
```
### 2.3 for 语句
```python
for item in list:
    pass

# 在for循环中使用内置函数 range()
range(a,b,c)  返回一个数字区间的所有整数

# 简单的冒泡排序算法S
for i in range(len(n)-1):
    for j in range(len(n)-i-1):
        if n[j] > n[i]:
            n[j], n[j+1] = n[j+1], n[j]

# 在for循环中使用内置函数zip()
zip(x,y)  将多序列生成一个新的序列，每个序列的元素以元组形式存储数据

for t1,t2 in zip(x,y):
    print(t1,t2)
```
### 2.4 控制语句
```python
break  跳出循环
continue  终止当前一次循环、继续进行下一次循环
pass 什么都不做，保持结构完整性
```
## 3. 格式化输入与输出
### 3.1 格式化输入
```python 
a = input(<info>)
a = input(repr(str))
```
### 3.2 格式化输出
**3.2.1 print语句**
```python
print(a, b)   同行以空格隔开输出
print(a, b,s ep=',')  以逗号隔开进行输出
print(s, ewp='\n')   以换行隔开进行输出
print(name, end='!')  每个输出都要添加!
print(' i love %s ' % s)  print 格式化输出
# 对字符串的每个元素进行换行输出
for item in list:
    print(item)  
```
**3.2.2 字符串方法format()**
```python 
print('{0} : {1} : {2}'.format(hour, minute, second))
# 按照对齐格式化进行排列
print('{0:3},{1:5}'.format(12, 534)) :后面的内容为只等的格式，表示占位数，如果不够，在前面用空格补齐
```
**3.2.3 数据输出的格式类型**
```python
# a表示占位，不够，按照原长度打印，多了左侧空格补齐，小数点后面为保留几位小数，f位数据类型
print('i love %a.bf', num)
- b 以二进制形式输出
- c 输出证书值对应的unicode字符
- d 以十进制形式输出数值
- e 以科学计数法形式输出
- o 以八进制形式输出
- x 以小写形式的十六进制输出
- X 以大写形式的十六进制输出
```

## 4. 函数
### 4.1 函数定义及调用函数
```python
- def funname(para1, para2,*，para3...):
    函数体
# 在参数列表中使用（*），代表调用函数时，在（*）后面的参数都必须指定参数名称，如下
funname(para1, para2，para3=2...)   调用函数
- def fun(strname, age=32)：   后面的参数位默认形参，默认形参必须放在后面
- 对元组和列表进行解包
def fun(*person):
fun('shy','21')
mylist = ['shy','21']
fun(*mylist)
- 对字典进行解包定义参数及调用
def fun(**person)
print('姓名',person['name'],'年纪',person['age'])
fun('shy','21')
mydict = {'name':'shy','age':21}
fun(**mydict)
```
### 4.2 函数类型
**4.2.1 python内置函数**

下图python3.8官方文档给出的内置函数库：
<div style="align: center">
<img src="https://img.vim-cn.com/5f/bd7267b5d93389d33733905d3bb7216a43d7c1.png"/>
</div>

官方中文文档的连接：[https://docs.python.org/zh-cn/3/library/functions.html](https://docs.python.org/zh-cn/3/library/functions.html)

**4.2.2 匿名函数与可迭代函数**
- **匿名函数**
```python
# 匿名函数
lambda para1, para2... : 表达式
r = lambda x,y:x*y

# 匿名函数与reduce函数的组合应用
reduce(fun, seq, initial)  #用序列值依次调用fun
from funtools import reduce
a = reduce(lambda x,y:x + y, range(1,101))  #实现求1~100的和

# 匿名函数与map函数的组合应用
map(fun, seq[,seq,])  #将seq内部的元素作为参数依次调用
t = map(lambda x:x**2,[1,2,3,4,5])  #返回一个map对象
print(list(t))   #打印值为[1,4,9,16,25]
y =map(lambda x,y:x+y,[1,2,3],[4,5,6])
print(list(t))   # 打印值为[5,7,9]

# 匿名函数与filter函数的组合应用
filter(fun or none, seq)  #将序列对象依次放到fun中，如果返回true就留下
t = filter(lambda x:x%2==0, [1,2,3,4,5,6])
print(list(t))   # 打印值为[2,4,6]

```
- **可迭代函数**
```python
# 每个生成器对象会有一个__next__()方法
t = filter(lambda x:x%2==0, [1,2,3,4,5,6])
print(t.__next__())  # 打印2
print(t.__next__())  # 打印4
```
**4.2.3 生成器函数与工厂函数**
- **生成器函数**
```python
# 生成器与迭代器不同，迭代器的内容存在内存里，用next函数遍历，生成器用完立即销毁
def Reverse(data):
    for idx in range(len(data)-1,-1,-1):
        yield data[idx]   # 生成器函数用yield返回
for c in Reverse('Python'):
    print(c, end = ' ')  # 打印 n o h t y P

# 生成器表达式
mylist = [x*x for x in range(3)]  # 使用生成器表达式返回一个对象
```
- **工厂函数**
```python
# 闭合函数
def wrapperfun(strname):
    def recorder(age)：
        print(strname,age)
    return recorder

fun = wrapperfun('shy')
fun(37)    # 打印 shy 37

# 装饰器属性：在原有的函数包一个函数，不改变原代码的基础上，添加新功能
def checkParams(fn):    # 装饰器函数
    def wrapper(strname):
        if isinstance(strname.(str))：
            return fn(strname)  # 判断字符串类型
        print ('error')  
        return
    return wrapper

def wrapperfun(strname):
    def recorder(age)：
        print(strname,age)
    return recorder
wrapperfun2 = checkParams(wrapperfun)
fun = wrapperfun('shy')
fun(37)  # 打印 shy 37
fun = wrapperfun2(37)  # 输入不合法
```
- **@修饰符**
```python
def checkParams(fn):    # 装饰器函数
    def wrapper(strname):
        if isinstance(strname.(str))：
            return fn(strname)  # 判断字符串类型
        print ('error')  
        return
    return wrapper

@checkParams   # 使用装饰器函数对wrapperfun函数进行修饰
def wrapperfun(strname):
    def recorder(age)：
        print(strname,age)
    return recorder

fun = wrapperfun('shy')
fun(37)  # 打印 shy 37
fun = wrapperfun2(37)  # 输入不合法

```
**4.4.4 偏函数与递归函数**
- **偏函数**
```python
# 偏函数是重新定义一个函数，并指定了默认参数值
from funtools import partial
partial(fun, *args, **keywords)
```
- **递归函数**
```python
# 递归函数是自己调用自己的函数，所有的函数调用都是压栈的过程，所以耗内存，栈空间有限，如果程序栈空间地址写满，程序最后会崩溃
def fun(n):
    return n*fun(n-1)
```
**4.4.5 eval 和 exec函数**
- **eval函数**
```python
# exec执行不返回结果，eval执行返回结果
dic = {}
dic['b'] = 3
exec('a=4',dic)
print(dic.keys())   #打印dict_keys(['a','__builtins__','b'])
# 使用这两个函数第一个参数一定是可执行代码
```
### 4.3 变量的作用域
**4.3.1 global语句**
```python
# global 可以把局部声明为全局
a = 6
def func():
    global a
    a = 5
print(a)   # 打印5
```
**4.3.2 nonlocal语句**
```python
# nonlocal可以把全局往下一作用域调用
a = 6
def func():
    a = 7
    def nested():
        nonlocal a
            a+=1
    nested()
    print('本地:',a)   #打印 8
func()
print('全局',a)  # 打印6
print(a)   # 打印5
```
## 5. 面向对象的程序设计
### 5.1 类的结构
```python 
class MyClass：
    def __init__(self,属性):  # 构造函数
        self.属性 = 属性
        pass
    def getname(self):
        return self.name
    ......

myc = MyClass(属性)   # 初始化实例对象，构造函数的属性
a = myc.getname()   

# 类还具有一些内置属性
__name__   名称
__doc__  类的文档字符串
__nodule__ 类的模块
if __name__ == '__main__':

```
### 5.2 类方法
```python
@classmthod  # 声明为类方法，可以直接用类名进行调用，当然初始化实例对象进行调用也是正确的
def fun(cls):
@staticmethod  # 等同于普通函数，只是被封装在类中，独立于整个类
def fun()  # 同上的调用方式，且参数没有限制要求
```
### 5.3 类的私有化属性
```python
# 私有化属性方法，在类的属性前面加双下划线，同时会提供一个私有化属性的访问函数，不可以被修改,但可以针对具体实例进行对象修改
clas MyClass:
    __Occupation = 'scientist'

    def __init__(sefl,name,age)；
    def getOccupation(self):
        return self.__Occupation
# 使用装饰器函数实现类的私有化
clas MyClass:
    __Occupation = 'scientist'

    def __init__(sefl,name,age)；
    @property  # 装饰为属性，使类的私有化属性也可以被访问
    def getOccupation(self):
        return self.__Occupation
```
### 5.4 类的继承
**5.4.1 继承结构体**
```python
class DerivedClass(FatherClass1, FatherClass2)：
    pass
```
```python
class Record:
    """ A record class """
    __Ocuupation = "scientist"
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def showrecode(self):
        print("Occupation:",self.getOccupation())
    
    def getOccupation(self):
        return self.__Occupation

class GirlRecord(Record):
    """ A girlrecord class """
    def showrecode(self):
        Record.showrecode(self)
        print("the girl:", self.name, "age:", self.age)

myc = GirlRecord("Anaa", 21)
myc.showrecode()
```
**5.4.2 super()函数**
```python
# 保障了调用父类方法时只调用一次
class Record:
    """ A record class """
    __Ocuupation = "scientist"
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def showrecode(self):
        print("Occupation:",self.getOccupation())
    
    def getOccupation(self):
        return self.__Occupation

class GirlRecord(Record):
    """ A girlrecord class """
    def showrecode(self):
        super().showrecode(self)
        print("the girl:", self.name, "age:", self.age)

class MaleRecord(Record):
    """ A girlrecord class """
    def showrecode(self):
        super().showrecode(self)
        print("the girl:", self.name, "age:", self.age)
        
class ThisRecord(GirlRecord, MaleRecord):
    """ A girlrecord class """
    def showrecode(self):
        super().showrecode(self)
        print("the girl:", self.name, "age:", self.age)
myc = ThisRecord("Anaa", 21)
myc.showrecode()
```
### 5.5 类相关的内置函数
- **判断实例（isinstance)**
```python 
isinstance(object, class_name)
```
- **判断字类（issubclass)**
```python 
issubclass(class1, class2)
```
- **判断类实例中是否包含某一个属性（hasattr)**
```python 
hasattr(object, name)
```
- **获得类实例中的某一个属性（getattr)**
```python 
getattr(object, name[,default])
```
- **设置类实例中的某一个属性值（setattr)**
```python 
setattr(object, name, value)
```
### 5.6 重载运算符
```python
class MyClass:
    """ A record class"""
    def __init__(self, name, age):
        self.name = name
        self.age = age
    def __str__(self):  # 将值转化为字符串进行输出
        retrun "name:"+self.name;"age:"+str(self.age)
    
    __repr__ = __str__  # 转化为解释器读取的形式

    def __lt__(self, record):  #重载比较运算符
        if self.age < record.age:
            return True
        else:
            return False

    def __add__(self, record):   #重载加号运算符
        return MyClass(self.name, self.age+record.age)

myc = MyClass("A", 42)
myc1 = MyClass("B", 23)

print(repr(myc))  
print(myc)
print(str(myc))
print(myc<myc1)
print(myc+myc1)
```
- **运算符重载**
```python
 方法名                  运算符和表达式      说明
__add__(self,rhs)        self + rhs        加法
__sub__(self,rhs)        self - rhs         减法
__mul__(self,rhs)        self * rhs         乘法
__truediv__(self,rhs)    self / rhs          除法
__floordiv__(self,rhs)   self //rhs          地板除
__mod__(self,rhs)        self % rhs       取模(求余)
__pow__(self,rhs)        self **rhs         幂运算
合赋值算术运算符的重载:
方法名                  运算符和表达式      说明
__iadd__(self,rhs)       self += rhs        加法
__isub__(self,rhs)       self -= rhs         减法
__imul__(self,rhs)       self *= rhs         乘法
__itruediv__(self,rhs)   self /= rhs        除法
__ifloordiv__(self,rhs)  self //=rhs        地板除
__imod__(self,rhs)       self %= rhs     取模(求余)
__ipow__(self,rhs)       self **=rhs       幂运算

比较算术运算符的重载:
方法名                  运算符和表达式      说明
__lt__(self,rhs)       self < rhs        小于
__le__(self,rhs)       self <= rhs       小于等于
__gt__(self,rhs)       self > rhs        大于
__ge__(self,rhs)       self >= rhs       大于等于
__eq__(self,rhs)       self == rhs       等于
__ne__(self,rhs)       self != rhs       不等于
        

位运算符重载
方法名              运算符和表达式        说明
__and__(self,rhs)       self & rhs           位与
__or__(self,rhs)        self | rhs           位或
__xor__(self,rhs)       self ^ rhs           位异或
 __lshift__(self,rhs)    self <<rhs           左移
 __rshift__(self,rhs)    self >>rhs           右移

反向位运算符重载

方法名            运算符和表达式       说明
__and__(self,lhs)       lhs & rhs        位与
__or__(self,lhs)         lhs | rhs       位或
__xor__(self,lhs)       lhs ^ rhs        位异或
__lshift__(self,lhs)    lhs <<rhs        左移
__rshift__(self,lhs)    lhs >>rhs        右移

复合赋值位相关运算符重载
方法名              运算符和表达式          说明
__iand__(self,rhs)       self & rhs       位与
__ior__(self,rhs)        self | rhs       位或
__ixor__(self,rhs)       self ^ rhs       位异或
__ilshift__(self,rhs)    self <<rhs       左移
__irshift__(self,rhs)    self >>rhs       右移

一元运算符的重载
方法名              运算符和表达式       说明
__neg__(self)         - self           负号
__pos__(self)         + self           正号
__invert__(self)      ~ self           取反
```
## 6 错误异常与文件读写
### 6.1 错误异常捕捉
**6.1.1 异常语句结构**
```python
try:
    pass
except(ZeroDivisionError, ValueError):
    print('错误')
except:
    print('其它异常’)
except Exception as e:  # 捕捉未知异常
    print(e)
else:
    pass   # 没有异常发生时执行
finally:
    pass  # 最终处理语句，无论是否有异常，都要执行这个语句
```
**6.1.2 异常类型**
```python
# 异常名称	         异常解释
AttributeError	试图访问一个对象没有的树形，比如foo.x，但是foo没有属性x
IOError	输入/输出异常；基本上是无法打开文件
ImportError	无法引入模块或包；基本上是路径问题或名称错误
IndentationError	语法错误（的子类） ；代码没有正确对齐
IndexError	下标索引超出序列边界，比如当x只有三个元素，却试图访问x[5]
KeyError	试图访问字典里不存在的键
KeyboardInterrupt	Ctrl+C被按下
NameError	使用一个还未被赋予对象的变量
SyntaxError	Python代码非法，代码不能编译(个人认为这是语法错误，写错了）
TypeError	传入对象类型与要求的不符合
UnboundLocalError	
试图访问一个还未被设置的局部变量，基本上是由于另有一个同名的全局变量，导致你以为正在访问它
ValueError	传入一个调用者不期望的值，即使值的类型是正确
BaseException                        　　　　所有异常的基类
SystemExit　　　　　　　　 　　　　解释器请求退出
KeyboardInterrupt　　　　　 　　　　用户中断执行(通常是输入^C)
Exception　　　　　　　　　　　　 常规错误的基类
StopIteration 　　　　　　　　　　　　迭代器没有更多的值
GeneratorExit 　　　　　　　　　　生成器(generator)发生异常来通知退出
StandardError　　　　　　　　 　　所有的内建标准异常的基类
ArithmeticError　　　　　　　　　　 所有数值计算错误的基类
FloatingPointError 　　　　　　　　浮点计算错误
OverflowError 　　　　　　　　　　数值运算超出最大限制
ZeroDivisionError　　　　　　 　　除(或取模)零 (所有数据类型)
AssertionError　　　　　　　　 　　断言语句失败
AttributeError 　　　　　　　　　　对象没有这个属性
EOFError 　　　　　　　　　　　　没有内建输入,到达EOF 标记
EnvironmentError　　　　　　 　　操作系统错误的基类
IOError　　　　　　　　　　　　 输入/输出操作失败
OSError　　　　　　　　　　　　 操作系统错误
WindowsError 　　　　　　　　　　系统调用失败
ImportError　　　　　　　　　　 导入模块/对象失败
LookupError　　　　　　　　　　 无效数据查询的基类
IndexError 　　　　　　　　　　序列中没有此索引(index)
KeyError　　　　　　　　　　　　 映射中没有这个键
MemoryError　　　　　　　　　　 内存溢出错误(对于Python 解释器不是致命的)
NameError 　　　　　　　　　　未声明/初始化对象 (没有属性)
UnboundLocalError 　　　　　　　　访问未初始化的本地变量
ReferenceError　　　　　　　　 弱引用(Weak reference)试图访问已经垃圾回收了的对象
RuntimeError　　　　　　　　　　 一般的运行时错误
NotImplementedError 　　　　　　　　尚未实现的方法
SyntaxError Python　　　　　　　　 语法错误
IndentationError　　　　　　　　　　 缩进错误
TabError Tab　　　　　　　　　　 和空格混用
SystemError 　　　　　　　　　　　　一般的解释器系统错误
TypeError　　　　　　　　　　　　 对类型无效的操作
ValueError 　　　　　　　　　　　　传入无效的参数
UnicodeError Unicode　　　　　　　　 相关的错误
UnicodeDecodeError Unicode　　　　 解码时的错误
UnicodeEncodeError Unicode　　　　 编码时错误
UnicodeTranslateError Unicode 　　　　转换时错误
Warning　　　　　　　　　　　　　　 警告的基类
DeprecationWarning　　　　　　　　 关于被弃用的特征的警告
FutureWarning 　　　　　　　　　　　　关于构造将来语义会有改变的警告
OverflowWarning　　　　　　　　　　　 旧的关于自动提升为长整型(long)的警告
PendingDeprecationWarning　　　　　　 关于特性将会被废弃的警告
RuntimeWarning 　　　　　　　　　　　可疑的运行时行为(runtime behavior)的警告
SyntaxWarning　　　　　　　　　　 可疑的语法的警告
UserWarning 　　　　　　　　　　用户代码生成的警告
```
### 6.2 文件读写与导入
**6.2.1 语句结构**
```python
f = open('new/test.txt','a+',encoding='utf-8')
f.write('\n今天天气很好')
f.close()
f = open('new/test.txt','rb')
w=f.read().decode('utf-8')
print(w)

f = open('workfile', 'w')
with open('workfile') as f:
    read_data = f.read()
f.close()
文件常见的读写模式
w     以写方式打开，
W     文件若存在，首先要清空，然后（重新）创建
a     以追加模式打开 (从 EOF 开始, 必要时创建新文件)
r+     以读写模式打开
w+     以读写模式打开 (参见 w )
a+     以读写模式打开 (参见 a )
rb     以二进制读模式打开
wb     以二进制写模式打开 (参见 w )
ab     以二进制追加模式打开 (参见 a )
rb+    以二进制读写模式打开 (参见 r+ )
wb+    以二进制读写模式打开 (参见 w+ )
ab+    以二进制读写模式打开 (参见 a+ )
```
**6.2.1 文件读写方法**
```python
f.read()
f.read(size)
f.readline()  # 读取一行
f.readlines()  # 读取所有行，每一行存储为列表的每一个元素
for line in f:
    print(line, end='')
>>> f.write('This is a test\n')
15
f.tell() # 返回一个整数，给出文件对象在文件中的当前位置，表示为二进制模式下时从文件开始的字节数，以及文本模式下的不透明数字。

# 要改变文件对象的位置，请使用 f.seek(offset, whence)。 通过向一个参考点添加 offset 来计算位置；  
# 参考点由 whence 参数指定。  
# whence 的 0 值表示从文件开头起算，1 表示使用当前文件位置，2 表示使用文件末尾作为参考点。   
# whence 如果省略则默认值为 0，即使用文件开头作为参考点。

>>>
>>> f = open('workfile', 'rb+')
>>> f.write(b'0123456789abcdef')
16
>>> f.seek(5)      # Go to the 6th byte in the file
5
>>> f.read(1)
b'5'
>>> f.seek(-3, 2)  # Go to the 3rd byte before the end
13
>>> f.read(1)
b'd'
```
### 6.3 常见文件类型的读取方式
- **csv文件**
```python
with open('C:/users/lenovo/desktop/student_score.csv','r') as f:
    for line in f.readlines(): #逐行读取
        print(line)

# 更加高效的是使用panda读取数据，存为一个矩阵的形式
import panda as pd
data = pd.read_csv(sys.argv[1])
```
- **txt文件**
```python
with open('my_file.txt') as f:
	for line in f:      #逐行读取
		print(line.strip())  #使用strip删除空格和空行，否则会有\n在最后

# 更加高效的是使用numpy读取数据,转化一个数组
import numpy as np
dataset = np.loadtxt('路径')
dataset.shape( )  # 查看数组维度
newset = reshape(dataset, (100,3))  # 转化为100行 3列的数组
```
- **excle文件**
```python
import numpy as np
import xlrd   #使用库函数

workbook = xlrd.open_workbook('C:/users/lenovo/desktop/student_score.xlsx')  #读取路径
sheet = workbook.sheet_by_name('Sheet1')     #读取excel中的第一个sheet

data_name = sheet.col_values(0)    #按列读取，读取第一列
#data_name1 = sheet.row_values(0)  #按行读取，读取第一行
data_st_ID = sheet.col_values(1)
data_st_score = sheet.col_values(2)


# 更加高效的是使用panda读取数据
import pandas as pd
test_df = pd.read_excel(r'G:\test.xlsx')
```
- **mat文件**
```python
import numpy as np 
import os 
os.chdir(r'F:/data')

import scipy.io as scio
data = scio.loadmat('97.mat')
print(data)

de = data['X097_DE_time']

读取的结果是一个字典
or 
from mat4py import loadmat
import numpy as np
data = np.array(loadmat('test.mat')['dictKey']).astype('float')

```
### 6.3 使用json保存结构化数据
```python
>>> import json
>>> json.dumps([1, 'simple', 'list'])
'[1, "simple", "list"]'
```
**6.3.1 将数据保存为json文件**
```python

model={} #数据
with open("./hmm.json",'w',encoding='utf-8') as json_file:
    json.dump(model,json_file,ensure_ascii=False)

```
**6.3.2 从json文件读取数据**
```python

model={} #存放读取的数据
with open("./hmm.json",'r',encoding='utf-8') as json_file:
    model=json.load(json_file)

读取返回的为python字典
or 

import json
 
str_file = './960x540/config.json'
with open(str_file, 'r') as f:
    print("Load str file from {}".format(str_file))
    r = json.load(f)
print(type(r))
print(r)
print(r['under_game_score_y'])
```
## 7. python标准库

<div align=" center">
<img src="https://img.vim-cn.com/47/19c6e06be5f16f01de1a5d1ef6733fd9129648.png">
</div>


**也可以查看标准库文档**  
[https://docs.python.org/zh-cn/3/tutorial/index.html](https://docs.python.org/zh-cn/3/tutorial/index.html)
[https://docs.python.org/zh-cn/3/library/index.html](https://docs.python.org/zh-cn/3/library/index.html)