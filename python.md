## Python3 基础语法

- Python 的实际工作场景往往是 Unix 或者 Linux。而代码开头的 `$` 表示 UNIX 或 Mac OS 操作系统命令提示符。`$`的意思就是 “提示用户输入命令行”，`$` 本身不在输入的命令语句中。`$` 是不需要输入的。
- Python 的编程模式分为两种：**交互式**，**脚本式**。
- 交互式编程，需要我们打开 cmd 窗口（命令提示符窗口），在窗口中键入`python`,回车，这样就进入了交互式编程。此时我们直接输入 python 语句，就可以得到运行的结果： ![img](https://static.runoob.com/images/mix/8683310-9291d88f53fd5b44.webp)
- 脚本式编程，就是我们先把 python 语句写好，保存在后缀为 .py 的文件里，然后从外部调用这个文件。它也可以使用 cmd 窗口进行调用，**与交互式编程不同的是，不要在cmd窗口内输入python加回车来进入交互模式**
- 如果我们要在cmd窗口调用test.py文件，只需要将**cmd路径目录转入test.py所在的文件夹，然后输入命令即可**
- 假设我们的test.py文件放在D盘，路径为：D:\Python27\Mytest\test.py 那么要在cmd窗口调用这个文件，我们需要将目录路径切换到D:\Python27\Mytest。使用**cd命令**即可做到。
  ![img](https://static.runoob.com/images/mix/8683310-d74ba3bfcab55d17.webp)

以下是简单的补充：
cmd 窗口打开方式：右键开始菜单，选择‘命令提示符（管理员）’即可。或者从开始菜单->运行->输入cmd，回车。
关于 cd 命令：用于改变当前目录路径。使用方式：cd[空格][路径]
例如 cd d:/Python27/Mytest 转到该路径下
注意：如果当前盘符不是 D 盘，需要先转到 D 盘，输入 d: 回车即可。然后才可以使用 cd d:/Python27/Mytest

![img](https://static.runoob.com/images/mix/8683310-d9297c7283d814e2.webp)

python中数字有四种类型：整数、布尔型、浮点数和复数。

Python 中单引号 **'** 和双引号 **"** 使用完全相同

反斜杠可以用来转义，使用 **r** 可以让反斜杠不发生转义。 如 **r"this is a line with \n"** 则 **\n** 会显示，并不是换行

**print** 默认输出是换行的，如果要实现不换行需要在变量末尾加上 **end=""**：

在 python 用 **import** 或者 **from...import** 来导入相应的模块。

将整个模块(somemodule)导入，格式为： **import somemodule**

从某个模块中导入某个函数,格式为： **from somemodule import somefunction**

从某个模块中导入多个函数,格式为： **from somemodule import firstfunc, secondfunc, thirdfunc**

将某个模块中的全部函数导入，格式为： **from somemodule import \***

将模块换个别名，例如：**import time as abc**，在引用时格式为：**abc.sleep(1)**。

| 操作符 | 描述                                                         |              实例               |
| :----- | :----------------------------------------------------------- | :-----------------------------: |
| +      | 字符串连接                                                   |  a + b 输出结果： HelloPython   |
| *      | 重复输出字符串                                               |    a*2 输出结果：HelloHello     |
| []     | 通过索引获取字符串中字符                                     |       a[1] 输出结果 **e**       |
| [ : ]  | 截取字符串中的一部分，遵循**左闭右开**原则，str[0:2] 是不包含第 3 个字符的。 |     a[1:4] 输出结果 **ell**     |
| in     | 成员运算符 - 如果字符串中包含给定的字符返回 True             |   **'H' in a** 输出结果 True    |
| not in | 成员运算符 - 如果字符串中不包含给定的字符返回 True           | **'M' not in a** 输出结果 True  |
| r/R    | 原始字符串 - 原始字符串：所有的字符串都是直接按照字面的意思来使用，没有转义特殊或不能打印的字符。 原始字符串除在字符串的第一个引号前加上字母 **r**（可以大小写）以外，与普通字符串有着几乎完全相同的语法。 | `print( r'\n' ) print( R'\n' )` |
| %      | 格式字符串                                                   |        请看下一节内容。         |

Python 的元组与列表类似，不同之处在于元组的元素不能修改。

元组使用小括号 **( )**，列表使用方括号 **[ ]**。

元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可。

元组中只包含一个元素时，需要在元素后面添加逗号 **,** ，否则括号会被当作运算符使用：

不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住	

可以使用大括号 **{ }** 或者 **set()** 函数创建集合，注意：创建一个空集合必须用 **set()** 而不是 **{ }**，因为 **{ }** 是用来创建一个空字典

集合（set）是一个无序的不重复元素序列。对于数据量很小的集合并且数字很少的时候，确实是做了一个排序

- **s.update( {"字符串"} )** 将字符串添加到集合中，有重复的会忽略。
-  **s.update( "字符串" )** 将字符串拆分单个字符后，然后再一个个添加到集合中，有重复的会忽略。

```
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> print(thisset)
{'Google', 'Runoob', 'Taobao'}
>>> thisset.update({"Facebook"})
>>> print(thisset) 
{'Google', 'Runoob', 'Taobao', 'Facebook'}
>>> thisset.update("Yahoo")
>>> print(thisset)
{'h', 'o', 'Facebook', 'Google', 'Y', 'Runoob', 'Taobao', 'a'}
>>>
```



Python 中用 **elif** 代替了 **else if**，所以if语句的关键字为：**if – elif – else**。

Python 3.10 增加了 **match...case** 的条件判断，不需要再使用一连串的 **if-else** 来判断了。

**case _:** 类似于 C 和 Java 中的 **default:**，当其他 case 都无法匹配时，匹配这条，保证永远会匹配成功。

一个 case 也可以设置多个匹配条件，条件使用 **｜** 隔开，

如果 while 后面的条件语句为 false 时，则执行 else 的语句块。

如果你的while循环体中只有一条语句，你可以将该语句与while写在同一行中

```
flag = 1
 
while (flag): print ('欢迎访问菜鸟教程!')
 
print ("Good bye!")
```

## **什么情况下需要使用 yield？**

一个函数 f，f 返回一个 list，这个 list 是动态计算出来的（不管是数学上的计算还是逻辑上的读取格式化），并且这个 list 会很大（无论是固定很大还是随着输入参数的增大而增大），这个时候，我们希望每次调用这个函数并使用迭代器进行循环的时候一个一个的得到每个 list 元素而不是直接得到一个完整的 list 来节省内存，这个时候 yield 就很有用。

**yield**后面可以加多个数值（可以是任意类型），但返回的值是元组类型的。

python字符串格式化符号 %f 可指定小数点后的精度。

```
>>> num=18.7254
>>> print("the price  is  %.2f" %num)
the price  is  18.73
```

---

在 python 中，strings, tuples, 和 numbers 是不可更改的对象，而 list,dict 等则是可以修改的对象。

加了星号 ***** 的参数会以元组(tuple)的形式导入，存放所有未命名的变量参数。

声明函数时，参数中星号 ***** 可以单独出现，例如:

```
def f(a,b,*,c):
    return a+b+c
```

如果单独出现星号 *****，则星号 ***** 后的参数必须用关键字传入：

```
>>> def f(a,b,*,c):
...     return a+b+c
... 
>>> f(1,2,3)   # 报错
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: f() takes 2 positional arguments but 3 were given
>>> f(1,2,c=3) # 正常
6
>>>
```

Python3.8 新增了一个函数形参语法 / 用来指明函数形参必须使用指定位置参数，不能使用关键字参数的形式。

在以下的例子中，形参 a 和 b 必须使用指定位置参数，c 或 d 可以是位置形参或关键字形参，而 e 和 f 要求为关键字形参:

```
def f(a, b, /, c, d, *, e, f):
    print(a, b, c, d, e, f)
```

以下使用方法是正确的:

```
f(10, 20, 30, d=40, e=50, f=60)
```



默认参数必须放在最后面，否则会报：

```python
SyntaxError: non-default argument follows default argument
# 可写函数说明
def printinfo( age=35,name):   # 默认参数不在最后，会报错
    "打印任何传入的字符串"
    print("名字: ", name)
    print("年龄: ", age)
    return
```

lambda 匿名函数也是可以使用"**关键字参数**"进行参数传递

```python
>>> g= lambda x,y : x**2+y**2
>>> g(2,3)
13
>>> g(y=3,x=2)
13
```

如果引用了还没更新的值则会报错 :

```python
a = 10
def sum ( n ) :
   n += a
   a = 11
   print ('a = ', a, end = ' , ' )
   print ( 'n = ', n )
  
sum(3)
```

输出 :

...

```python
UnboundLocalError: local variable 'a' referenced before assignment
```

可以加上 global 引用以更新变量值 :

```python
a = 10
def sum ( n ) :
   global a
   n += a
   a = 11
   print ('a = ', a, end = ' , ' )
   print ( 'n = ', n )

sum ( 3 )
print ( '外 a = ', a )
```

```python
#函数也可以以一个函数为其参数:

def hello () :
  print ("Hello, world!")

def execute(f):
  "执行一个没有参数的函数"
  f()

execute(hello)
```

函数返回值的注意事项: 不同于 C 语言，Python 函数可以返回多个值，多个值以元组的方式返回:

```
def fun(a,b):    
    "返回多个值，结果以元组形式表示"
    return a,b,a+b
print(fun(1,2))
```

输出结果为：

```
(1, 2, 3)
```

## **函数的装饰器**

在不改变当前函数的情况下, 给其增加新的功能:

```python
def log(pr):#将被装饰函数传入
    def wrapper():
        print("**********")      
        return pr()#执行被装饰的函数
    return wrapper#将装饰完之后的函数返回（返回的是函数名）
@log
def pr():
    print("我是小小洋")

pr()
```

回调函数和返回函数的实例就是装饰器。

在编写函数的过程中，可以显式指定函数的参数类型及返回值类型：

```python
#!/usr/bin/env python3
# -*- coding: UTF-8 -*-

def function_demo(param_A: int, param_B: float, param_C: list, param_D: tuple) -> dict:
    pass
```

这种 **“将数据类型写死在代码中”** 的行为在集成开发环境/代码编辑器时尤为方便，通过显式地指定函数的参数类型和返回值，能够让智能补全组件提前获知标识符的数据类型，提供有利的辅助开发功能。

---



Python中列表是可变的，这是它区别于字符串和元组的最重要的特点，一句话概括即：列表可以修改，而字符串和元组不能。

```python
>>> vec1 = [2, 4, 6]
>>> vec2 = [4, 3, -9]
>>> [x*y for x in vec1 for y in vec2]
[8, 6, -18, 16, 12, -36, 24, 18, -54]
>>> [x+y for x in vec1 for y in vec2]
[6, 5, -7, 8, 7, -5, 10, 9, -3]
>>> [vec1[i]*vec2[i] for i in range(len(vec1))]
[8, 12, -54]
```

```python
>>> [str(round(355/113, i)) for i in range(1, 6)]
['3.1', '3.14', '3.142', '3.1416', '3.14159']
```

使用 del 语句可以从一个列表中根据索引来删除一个元素，而不是值来删除元素。这与使用 pop() 返回一个值不同。可以用 del 语句从列表中删除一个切割，或清空整个列表（我们以前介绍的方法是给该切割赋一个空列表）。

元组由若干逗号分隔的值组成

```python
>>> t = 12345, 54321, 'hello!'
>>> t[0]
12345
>>> t
(12345, 54321, 'hello!')
>>> # Tuples may be nested:
... u = t, (1, 2, 3, 4, 5)
>>> u
((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
```

集合是一个无序不重复元素的集。基本功能包括关系测试和消除重复元素。

```python
>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
>>> print(basket)                      # 删除重复的
{'orange', 'banana', 'pear', 'apple'}
>>> 'orange' in basket                 # 检测成员
True
>>> 'crabgrass' in basket
False

>>> # 以下演示了两个集合的操作
...
>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  # a 中唯一的字母
{'a', 'r', 'b', 'c', 'd'}
>>> a - b                              # 在 a 中的字母，但不在 b 中
{'r', 'd', 'b'}
>>> a | b                              # 在 a 或 b 中的字母
{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
>>> a & b                              # 在 a 和 b 中都有的字母
{'a', 'c'}
>>> a ^ b                              # 在 a 或 b 中的字母，但不同时在 a 和 b 中
{'r', 'd', 'b', 'm', 'z', 'l'}
```

在字典中遍历时，关键字和对应的值可以使用 items() 方法同时解读出来：

```python
>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
>>> for k, v in knights.items():
...     print(k, v)
...
gallahad the pure
robin the brave
```

在序列中遍历时，索引位置和对应值可以使用 enumerate() 函数同时得到：

```python
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
...     print(i, v)
...
0 tic
1 tac
2 toe
```

同时遍历两个或更多的序列，可以使用 zip() 组合：

```python
>>> questions = ['name', 'quest', 'favorite color']
>>> answers = ['lancelot', 'the holy grail', 'blue']
>>> for q, a in zip(questions, answers):
...     print('What is your {0}?  It is {1}.'.format(q, a))
...
What is your name?  It is lancelot.
What is your quest?  It is the holy grail.
What is your favorite color?  It is blue.
```

要反向遍历一个序列，首先指定这个序列，然后调用 reversed() 函数：

```python
>>> for i in reversed(range(1, 10, 2)):
...     print(i)
...
9
7
5
3
1
```

使用小括号包裹推导式会生成生成器对象，而不是元组。

##  元组的装包和拆包

```python
a=1
b=2
a,b=b,a   //等价于  (a,b)=(b,a)自动装包,等价于a,b=(b,a)  (a,b)=b,a
print(a,b)
```

***模块***

Python 的搜索路径，搜索路径是由一系列目录名组成的，Python 解释器就依次从这些目录中去寻找所引入的模块。

“Windows 命令行窗口”下清屏，可用下面两种方法。

第一种方法，在命令行窗口输入：

```
>>> import os
>>> i=os.system("cls")
```

第二种方法，在命令行窗口输入：

```
>>> import subprocess
>>> i=subprocess.call("cls", shell=True)
```

## 包

在导入一个包的时候，Python 会根据 sys.path 中的目录来寻找这个包中包含的子目录。

目录只有包含一个叫做 __init__.py 的文件才会被认作是一个包，主要是为了避免一些滥俗的名字（比如叫做 string）不小心的影响搜索路径中的有效模块。

最简单的情况，放一个空的 :file:__init__.py就可以了。当然这个文件中也可以包含一些初始化代码或者为（将在后面介绍的） __all__变量赋值。

导入语句遵循如下规则：如果包定义文件 **__init__.py** 存在一个叫做 **__all__** 的列表变量，那么在使用 **from package import \*** 的时候就把这个列表中的所有名字作为包内容导入。

![image-20221214223820624](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221214223820624.png)

![image-20221214223911310](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221214223911310.png)

## 读和写文件

open() 将会返回一个 file 对象，基本语法格式如下:

```python
open(filename, mode)
```

- filename：包含了你要访问的文件名称的字符串值。
- mode：决定了打开文件的模式：只读，写入，追加等。所有可取值见如下的完全列表。这个参数是非强制的，默认文件访问模式为只读(r)。

![image-20221214231728654](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221214231728654.png)



**f.readline()** 会从文件中读取单独的一行。

当处理一个文件对象时, 使用 **with** 关键字是非常好的方式。在结束后, 它会帮你正确的关闭文件。

### f.seek()

如果要改变文件指针当前的位置, 可以使用 f.seek(offset, from_what) 函数。

from_what 的值, 如果是 0 表示开头, 如果是 1 表示当前位置, 2 表示文件的结尾，例如：



- seek(x,0) ： 从起始位置即文件首行首字符开始移动 x 个字符
- seek(x,1) ： 表示从当前位置往后移动x个字符
- seek(-x,2)：表示从文件的结尾往前移动x个字符

from_what 值为默认为0，即文件开头。下面给出一个完整的例子：

```python
>>> f = open('/tmp/foo.txt', 'rb+')
>>> f.write(b'0123456789abcdef')
16
>>> f.seek(5)     # 移动到文件的第六个字节
5
>>> f.read(1)
b'5'
>>> f.seek(-3, 2) # 移动到文件的倒数第三字节
13
>>> f.read(1)
b'd'
```



通过pickle模块的序列化操作我们能够将程序中运行的对象信息保存到文件中去，永久存储。

通过pickle模块的反序列化操作，我们能够从文件中创建上一次程序保存的对象。

基本接口：

```
pickle.dump(obj, file, [,protocol])
```

有了 pickle 这个对象, 就能对 file 以读取的形式打开:

```
x = pickle.load(file)
```

为了保证无论是否出错都能正确的关闭文件，可以使用 **try...finally** 来实现：

```
try:
    f = open('/path/to/file', 'r')
    print(f.read())
finally:
    if f:
        f.close()
```

**获取文件后缀：**

```
def getfile_fix(filename):
     return filename[filename.rfind('.')+1:]
print(getfile_fix('runoob.txt'))
```

## 错误与异常

try 语句按照如下方式工作；

- 首先，执行 try 子句（在关键字 try 和关键字 except 之间的语句）。
- 如果没有异常发生，忽略 except 子句，try 子句执行后结束。
- 如果在执行 try 子句的过程中发生了异常，那么 try 子句余下的部分将被忽略。如果异常的类型和 except 之后的名称相符，那么对应的 except 子句将被执行。
- 如果一个异常没有与任何的 except 匹配，那么这个异常将会传递给上层的 try 中。

一个 try 语句可能包含多个except子句，分别来处理不同的特定的异常。最多只有一个分支会被执行。

处理程序将只针对对应的 try 子句中的异常进行处理，而不是其他的 try 的处理程序中的异常。

一个except子句可以同时处理多个异常，这些异常将被放在一个括号里成为一个元组，例如:

**except** (RuntimeError, TypeError, NameError):
  **pass**

![image-20221215233513852](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221215233513852.png)

## 用户自定义异常

你可以通过创建一个新的异常类来拥有自己的异常。异常类继承自 Exception 类，可以直接继承，或者间接继承

## 类

类的方法与普通的函数只有一个特别的区别——它们必须有一个额外的**第一个参数名称**, 按照惯例它的名称是 self。

```
class Test:
    def prt(self):
        print(self)
        print(self.__class__)
 
t = Test()
t.prt()
```

self 代表的是类的实例，代表当前对象的地址，而 self.class 则指向类。self 不是 python 关键字，我们把他换成 runoob 也是可以正常执行的

在类的内部，使用 **def** 关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 self, 且为第一个参数，self 代表的是类的实例。

```
class DerivedClassName(modname.BaseClassName):  #基类定义在另外一个模块
```

## super函数

```
#      ---> B ---
# A --|          |--> D
#      ---> C ---
#使用 super() 可以很好地避免构造函数被调用两次。

class A():
    def __init__(self):
        print('enter A')
        print('leave A')


class B(A):
    def __init__(self):
        print('enter B')
        super(B,self).__init__()
        print('leave B')


class C(A):
    def __init__(self):
        print('enter C')
        super(C,self).__init__()
        print('leave C')


class D(B, C):
    def __init__(self):
        print('enter D')
        super().__init__()
        print('leave D')


d = D()
```

Python3 中继承遵循广度优先原则：

```
class A:
    def __init__(self):
        print("Enter A")
        print(self)
        print("Leave A")


class B(A):
    def __init__(self):
        print("Enter B")
        print(self)
        super(B, self).__init__()
        print("Leave B")


class C(A):
    def __init__(self):
        print("Enter C")
        print(self)
        super(C, self).__init__()
        print("Leave C")


class D(B, C):
    def __init__(self):
        print("Enter D")
        print(self)
        super(D, self).__init__()
        print("Leave D")


d = D()
```

1.创建 D 类的对象 d 时，自动调用 D 类的初始化方法 **__init()__**，此时的 self 指向 D 类创建的实例对象 d；

2.调用原则：D->B->C->A

3.在调用到 B 时，首先输出 “Enter B”，但是**运行到父类 A 的初始化方法时不立即调用**，反而时转向广度优先级高的 C 类，因为 A 类对于 B 类来说是深度遍历。





如果重写了**__init__** 时，要继承父类的构造方法，可以使用 **super** 关键字：

```
super(子类，self).__init__(参数1，参数2，....)
```

还有一种经典写法：

```
父类名称.__init__(self,参数1，参数2，...)
```

总结:

情况一：**子类需要自动调用父类的方法：**子类不重写__init__()方法，实例化子类后，会自动调用父类的__init__()的方法。

情况二：**子类不需要自动调用父类的方法：**子类重写__init__()方法，实例化子类后，将不会自动调用父类的__init__()的方法。

情况三：**子类重写__init__()方法又需要调用父类的方法：**使用super关键词：

```
super(子类，self).__init__(参数1，参数2，....)
class Son(Father):
  def __init__(self, name):   
    super(Son, self).__init__(name)
```

设置为私有的标志是,__name,即代表私有

所有专有方法中，__init__()要求无返回值，或者返回 None

类的专有方法中，也是存在默认优先级的，多个方法都有返回值，但一般优先取 __str__() 的返回值

在类的方法中直接修改 self 是无效操作，即使 self 变量的地址与实例地址相同：

```
class C:
  def __init__(self, a):
    self.a = a
  def construct(self, a):
    c = C(a)
    self = c
  def getid(self):
    return id(self)

if __name__ == '__main__':
  c1 = C(2)
  c1.construct(3) # c1.a == 2
  print(id(c1) == c1.getid()) # True
```

**Python3 类方法总结**

-  普通方法：**对象访问**
-  私有方法：两个下划线开头，只能在**类内部访问**
-  静态方法：**类和对象访问**，不能和其他方法重名，不然会相互覆盖，后面定义的会覆盖前面的
-  类方法：**类和对象访问**，不能和其他方法重名，不然会相互覆盖，后面定义的会覆盖前面的
-  多继承情况下：从左到右查找方法，找到为止，不然就抛出异常

## 命名空间/作用域

Python 中只有**模块（module**），**类（class）**以及**函数（def、lambda）**才会引入新的作用域，其它的代码块（如 if/elif/else/、try/except、for/while等）是不会引入新的作用域的，也就是说这些语句内定义的变量，外部也可以访问

当内部作用域想修改外部作用域的变量时，就要用到 global 和 nonlocal 关键字了。

```
a = 10
def test():
    a = a + 1   #报错,test中的a为局部变量未定义
    print(a)
test()
======================
a = 10
def test():
    global a  #需要global声明变量
    a = a + 1
    print(a)
test()
```

nonlocal是跳到enclosing 作用域，外层非全局作用域）中的变量

