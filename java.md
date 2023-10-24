### 源文件声明规则

当在一个源文件中定义多个类，并且还有import语句和package语句时，要特别注意这些规则。

+ 一个源文件中只能有一个 public 类
+ 一个源文件可以有多个非 public 类
+ 源文件的名称应该和 public 类的类名保持一致。例如：源文件中 public 类的类名是 Employee，那么源文件应该命名为Employee.java。
+ 如果一个类定义在某个包中，那么 package 语句应该在源文件的首行。
+ 如果源文件包含 import 语句，那么应该放在 package 语句和类定义之间。如果没有 package 语句，那么 import 语句应该在源文件中最前面。
+ import 语句和 package 语句对源文件中定义的所有类都有效。在同一源文件中，不能给不同的类不同的包声明。

---

程序都是从main方法开始执行。为了能运行这个程序，必须包含main方法并且创建一个实例对象。

---

### package 的作用

就是 c++ 的 namespace 的作用，防止名字相同的类产生冲突。Java 编译器在编译时，直接根据 package 指定的信息直接将生成的 class 文件生成到对应目录下。如 **package aaa.bbb.ccc** 编译器就将该 .java 文件下的各个类生成到 **./aaa/bbb/ccc/** 这个目录。

import 是为了简化使用 package 之后的实例化的代码。假设 **./aaa/bbb/ccc/** 下的 A 类，假如没有 import，实例化A类为：**new aaa.bbb.ccc.A()**，使用 **import aaa.bbb.ccc.A** 后，就可以直接使用 **new A()** 了，也就是编译器匹配并扩展了 **aaa.bbb.ccc.** 这串字符串。

---

### **类的构造方法**

1. 构造方法的名字和类名相同，并且没有返回值。

2. 构造方法主要用于为类的对象定义初始化状态。

3. 我们不能直接调用构造方法，必须通过new关键字来自动调用，从而创建类的实例。

4. Java的类都要求有构造方法，如果没有定义构造方法，Java编译器会为我们提供一个缺省的构造方法，也就是不带参数的构造方法。

**new关键字的作用**

> 1、为对象分配内存空间。
>
> 2、引起对象构造方法的调用。
>
> 3、为对象返回一个引用。

---

```java
//一个没有显式声明构造函数的类
Public class People{
    int age = 23;
    Public void getAge(){
        System.out.print("the age is "+age);
    }
}

//用这个类来实例化一个对象
People xiaoMing = new People(); // People() 是People类的默认构造函数，它什么也不干
xiaoMing.getAge();//打印年龄
```

---

### 内部类

内部类：将一个类的定义放在另一个类的定义内部，这就是内部类。

如同一个人是由大脑、肢体、器官等身体结果组成，而内部类相当于其中的某个器官之一，例如心脏：它也有自己的属性和行为（血液、跳动）

显然，此处不能单方面用属性或者方法表示一个心脏，而需要一个类，而心脏又在人体当中，正如同是内部类在外部类当中。

不用内部类：

```java
public class Person {
    private int blood;
    private Heart heart;
}

public class Heart {
    private int blood;
    public void test() {
        System.out.println(blood);
    }
}
```

使用内部类

```java
public class Person {
    private int blood;
    public class Heart {
        public void test() {
            System.out.println(blood);
        }
    }

    public class Brain {
        public void test() {
            System.out.println(blood);
        }
    }
}
```

举例说明

```java
//外部类
class Out {
    private int age = 12;
     
    //内部类
    class In {
        public void print() {
            System.out.println(age);
        }
    }
}
 
public class Demo {
    public static void main(String[] args) {
        Out.In in = new Out().new In();
        in.print();
        //或者采用下种方式访问
        /*
        Out out = new Out();
        Out.In in = out.new In();
        in.print();
        */
    }
}
```

成员内部类可以无条件访问外部类的所有成员属性和成员方法（包括**private成员**和**静态成员**）。

当成员内部类拥有和外部类同名的成员变量或者方法时，会发生隐藏现象，即默认情况下访问的是成员内部类的成员。如果要访问外部类的同名成员，需要以下面的形式进行访问：

```java
外部类.this.成员变量
外部类.this.成员方法
```

虽然成员内部类可以无条件地访问外部类的成员，而外部类想访问成员内部类的成员却不是这么随心所欲了。在外部类中如果要访问成员内部类的成员，必须先创建一个成员内部类的对象，再通过指向这个对象的引用来访问：

```java
class Circle {
    private double radius = 0;
 
    public Circle(double radius) {
        this.radius = radius;
        getDrawInstance().drawSahpe();   //必须先创建成员内部类的对象，再进行访问
    }
     
    private Draw getDrawInstance() {
        return new Draw();
    }
     
    class Draw {     //内部类
        public void drawSahpe() {
            System.out.println(radius);  //外部类的private成员
        }
    }
}
```

局部内部类是定义在一个方法或者一个作用域里面的类，它和成员内部类的区别在于局部内部类的访问仅限于方法内或者该作用域内。

```java
class People{
    public People() {
         
    }
}
 
class Man{
    public Man(){
         
    }
     
    public People getWoman(){
        class Woman extends People{   //局部内部类
            int age =0;
        }
        return new Woman();
    }
}
```

**注意:**局部内部类就像是方法里面的一个局部变量一样，是不能有 public、protected、private 以及 static 修饰符的。

[**匿名内部类**](https://www.runoob.com/w3cnote/java-inner-class-intro.html)

**[静态内部类](https://www.runoob.com/w3cnote/java-inner-class-intro.html)**

[内部类继承问题](https://www.runoob.com/w3cnote/java-inner-class-intro.html)

```java
public class Test{
    public static void main(String[] args){
           // 初始化Bean1
           (1)
           bean1.I++;
           // 初始化Bean2
           (2)
           bean2.J++;
           //初始化Bean3
           (3)
           bean3.k++;
    }
    class Bean1{
           public int I = 0;
    }
 
    static class Bean2{
           public int J = 0;
    }
}
 
class Bean{
    class Bean3{
           public int k = 0;
    }
}
```

```java
(1) Test test=new Test();
	test.Bean1 bean1= test.new Bean1();

(2)Test.Bean2 bean2=new Test.Bean2();

(3)test.Bean bean=test.new Bean();
	bean.Bean3 bean3=bean.new Bean3();
```

### 数据类型转换的补充

**1、包装类过渡类型转换**

一般情况下，我们首先声明一个变量，然后生成一个对应的包装类，就可以利用包装类的各种方法进行类型转换了。例如：

当希望把float型转换为double型时：

```java
float f1=100.00f;
Float F1=new Float(f1);
double d1=F1.doubleValue();//F1.doubleValue()为Float类的返回double值型的方法
```

[更多详情](https://www.runoob.com/java/java-basic-datatypes.html)

---

### java参数变量

方法参数变量的值传递方式有两种：**值传递**和**引用传递**。

+ **值传递：**在方法调用时，传递的是实际参数的值的副本。当参数变量被赋予新的值时，只会修改副本的值，不会影响原始值。Java 中的基本数据类型都采用值传递方式传递参数变量的值。
+ **引用传递：**在方法调用时，传递的是实际参数的引用（即内存地址）。当参数变量被赋予新的值时，会修改原始值的内容。Java 中的对象类型采用引用传递方式传递参数变量的值。



---

### 访问控制

| 修饰符      | 当前类 | 同一包内 | 子孙类(同一包) | 子孙类(不同包)                                               | 其他包 |
| :---------- | :----- | :------- | :------------- | :----------------------------------------------------------- | :----- |
| `public`    | Y      | Y        | Y              | Y                                                            | Y      |
| `protected` | Y      | Y        | Y              | Y/N（[说明](https://www.runoob.com/java/java-modifier-types.html#protected-desc)） | N      |
| `default`   | Y      | Y        | Y              | N                                                            | N      |
| `private`   | Y      | N        | N              | N                                                            | N      |

---

### java修饰符

**受保护的访问修饰符-protected**

protected 可以修饰数据成员，构造方法，方法成员，**不能修饰类（内部类除外）**。

- 基类的 protected 成员是包内可见的，并且对子类可见；
- 若子类与基类不在同一包中，那么在子类中，子类实例可以访问其从基类继承而来的protected方法，而不能访问基类实例的protected方法。

[Java protected 关键字详解](https://www.runoob.com/w3cnote/java-protected-keyword-detailed-explanation.html)

---

### final 修饰符

**final 变量：**

final 表示"最后的、最终的"含义，变量一旦赋值后，不能被重新赋值。被 final 修饰的实例变量必须显式指定初始值。

final 修饰符通常和 static 修饰符一起使用来创建类常量。

```java
public class Test{
  final int value = 10;
  // 下面是声明常量的实例
  public static final int BOXWIDTH = 6;
  static final String TITLE = "Manager";
 
  public void changeValue(){
     value = 12; //将输出一个错误
  }
}
```

**final 方法**

父类中的 final 方法可以被子类继承，但是不能被子类重写。

声明 final 方法的主要目的是防止该方法的内容被修改。

如下所示，使用 final 修饰符声明方法。

**final 类**

final 类不能被继承，没有类能够继承 final 类的任何特性。

### volatile 修饰符

volatile 修饰的成员变量在每次被线程访问时，都强制从共享内存中重新读取该成员变量的值。而且，当成员变量发生变化时，会强制线程将变化值回写到共享内存。这样在任何时刻，两个不同的线程总是看到某个成员变量的同一个值。

### java Number类

（1）Java 会对 **-128 ~ 127** 的整数进行缓存，所以当定义两个变量初始化值位于 **-128 ~ 127** 之间时，两个变量使用了同一地址：

```java
Integer a=123;
Integer b=123;
System.out.println(a==b);        // 输出 true
System.out.println(a.equals(b));  // 输出 true
```

（2）当两个 Integer 变量的数值超出 **-128 ~ 127** 范围时, 变量使用了不同地址：

```java
a=1230;
b=1230;
System.out.println(a==b);        // 输出 false
System.out.println(a.equals(b));  // 输出 true
```

### java String类

String 创建的字符串存储在公共池中，而 new 创建的字符串对象在堆上：

```java
String s1 = "Runoob";              // String 直接创建
String s2 = "Runoob";              // String 直接创建
String s3 = s1;                    // 相同引用
String s4 = new String("Runoob");   // String 对象创建
String s5 = new String("Runoob");   // String 对象创建
```

![image-20231021195009228](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20231021195009228.png)

**面试题一：**

```java
String s1 = "abc";            // 常量池
String s2 = new String("abc");     // 堆内存中
System.out.println(s1==s2);        // false两个对象的地址值不一样。
System.out.println(s1.equals(s2)); // true
```

**面试题二：**

```java
String s1="a"+"b"+"c";
String s2="abc";
System.out.println(s1==s2);
System.out.println(s1.equals(s2));
```

java 中常量优化机制，编译时 **s1** 已经成为 **abc** 在常量池中查找创建，**s2** 不需要再创建。

**面试题三：**

```java
String s1="ab";
String s2="abc";
String s3=s1+"c";
System.out.println(s3==s2);         // false
System.out.println(s3.equals(s2));  // true
```

**String**：字符串常量，字符串长度不可变。Java中String 是immutable（不可变）的。用于存放字符的数组被声明为final的，因此只能赋值一次，不可再更改。

**StringBuffer**：字符串变量（Synchronized，即线程安全）。如果要频繁对字符串内容进行修改，出于效率考虑最好使用 StringBuffer，如果想转成 String 类型，可以调用 StringBuffer 的 toString() 方法。Java.lang.StringBuffer 线程安全的可变字符序列。在任意时间点上它都包含某种特定的字符序列，但通过某些方法调用可以改变该序列的长度和内容。可将字符串缓冲区安全地用于多个线程。

**StringBuilder**：字符串变量（非线程安全）。在内部 StringBuilder 对象被当作是一个包含字符序列的变长数组。

**基本原则：**

- 如果要操作少量的数据用 String ；
- 单线程操作大量数据用StringBuilder ；
- 多线程操作大量数据，用StringBuffer。

不要使用String类的"+"来进行频繁的拼接，因为那样的性能极差的，应该使用StringBuffer或StringBuilder类，这在Java的优化上是一条比较重要的原则。例如：

```java
String result = "";
for (String s : hugeArray) {
    result = result + s;
}

// 使用StringBuilder
StringBuilder sb = new StringBuilder();
for (String s : hugeArray) {
    sb.append(s);
}
String result = sb.toString();

```

### Java StringBuffer 和 StringBuilder 类

在使用 StringBuffer 类时，每次都会对 StringBuffer 对象本身进行操作，而不是生成新的对象，所以如果需要对字符串进行修改推荐使用 StringBuffer。

StringBuilder 类在 Java 5 中被提出，它和 StringBuffer 之间的最大不同在于 StringBuilder 的方法不是线程安全的（不能同步访问）。

java 中 StringBuffer 和 String 是有一定的区别的，首先，String 是被 final 修饰的，他的长度是不可变的，就算调用 String 的 concat 方法，那也是把字符串拼接起来并**重新创建一个对象**，把拼接后的 String 的值赋给新创建的对象，而 **StringBuffer 的长度是可变的**，调用StringBuffer 的 append 方法，来改变 StringBuffer 的长度，并且，相比较于 StringBuffer，String 一旦发生长度变化，是非常耗费内存的！

### Java 数组

首先必须声明数组变量，才能在程序中使用数组。下面是声明数组变量的语法：

```
dataType[] arrayRefVar;   // 首选的方法  
或
dataType arrayRefVar[];  // 效果相同，但不是首选方法
```

```
double[] myList;         // 首选的方法

或

double myList[];         //  效果相同，但不是首选方法
```

多维数组

```java
String[][] s = new String[2][];
s[0] = new String[2];   //每一维的元素个数可以不同
s[1] = new String[3];	//每一维的元素个数可以不同
s[0][0] = new String("Good");
s[0][1] = new String("Luck");
s[1][0] = new String("to");
s[1][1] = new String("you");
s[1][2] = new String("!");
```

---

### Array类

见对应的java程序

---

### java正则表达式

正则表达式是对字符串操作的一种逻辑公式，就是用事先定义好的一些特定字符、及这些特定字符的组合，组成一个"规则字符串"，这个"规则字符串"用来表达对字符串的一种过滤逻辑。

给定一个正则表达式和另一个字符串，我们可以达到如下的目的：

- 1. 给定的字符串是否符合正则表达式的**过滤逻辑（称作"匹配"）**；
- 2. 可以通过正则表达式，从字符串中**获取我们想要的特定部分**。

正则表达式的特点是：

- 1. 灵活性、逻辑性和功能性非常的强；
- 2. 可以迅速地用极简单的方式达到字符串的复杂控制。
- 3. 对于刚接触的人来说，比较晦涩难懂。

注意：正则表达式写好后，没有错对之分，返回结果只是true和false

校验QQ号，要求：必须是5~15位数字，0不能开头。没有正则表达式之前

```java
public class regex {
    public static void main(String[] args) {
        checkQQ("0123134");
    }
    public static void checkQQ(String qq)
    {
        int len = qq.length();
        if(len>=5 && len <=15)
        {
            if(!qq.startsWith("0"))
            {
                try
                {
                    long l = Long.parseLong(qq);
                    System.out.println("qq:"+l);
                }        
                catch (NumberFormatException e)
                {
                    System.out.println("出现非法字符");
                }
            }
            else
                System.out.println("不可以0开头");
        }
        else
            System.out.println("QQ号长度错误");
        }
}
```

使用正则表达式之后的代码：

```java
public class regex {
    public static void main(String[] args) {
            checkQQ2("0123134");
    }
    public static void checkQQ2(String qq) {                                                            
            String reg = "[1-9][0-9]{4,14}";                  
            System.out.println(qq.matches(reg)?"合法qq":"非法qq");                                 
    }
}
```

### java 方法

**main 方法是被 JVM 调用的**，除此之外，main 方法和其它方法没什么区别。

main 方法的头部是不变的，带修饰符 public 和 static,返回 void 类型值，方法名字是 main,此外带个一个 String[] 类型参数。String[] 表明参数是字符串数组。

**方法重载**

如果你调用max方法时传递的是int型参数，则 int型参数的max方法就会被调用；

如果传递的是double型参数，则double类型的max方法体会被调用，这叫做方法重载；

就是说一个类的两个方法拥有相同的名字，但是有不同的参数列表。

Java编译器根据方法签名判断哪个方法应该被调用。

方法重载可以让程序更清晰易读。执行密切相关任务的方法应该使用相同的名字。

重载的方法必须**拥有不同的参数列表**。你不能仅仅依据修饰符或者返回类型的不同来重载方法。

**命令行参数的使用**

有时候你希望运行一个程序时候再传递给它消息。这要靠传递命令行参数给main()函数实现。

命令行参数是在执行程序时候紧跟在程序名字后面的信息。

```java
public class CommandLine {
   public static void main(String[] args){ 
      for(int i=0; i<args.length; i++){
         System.out.println("args[" + i + "]: " + args[i]);
      }
   }
}
```

#### 构造方法

不管你是否自定义构造方法，所有的类都有构造方法，因为 Java 自动提供了一个默认构造方法，默认构造方法的访问修饰符和类的访问修饰符相同(类为 public，构造函数也为 public；类改为 protected，构造函数也改为 protected)。

一旦你定义了自己的构造方法，默认构造方法就会失效。

#### 可变参数

在方法声明中，在指定参数类型后加一个省略号(...) 。

一个方法中只能指定一个可变参数，它必须是方法的最后一个参数。任何普通的参数必须在它之前声明。

```java
typeName... parameterName
```

```java
public static void printMax( double... numbers)
    
printMax(34, 3, 3, 2, 56.5);
printMax(new double[]{1, 2, 3});
```

一个函数至多只能有一个可变参数，且可变参数为最后一个参数。对于可变参数，编译器会将其转型为一个数组，故在函数内部，可变参数名即可看作数组名。

且

```java
void function(String... args);
void function(String [] args);
```

这两个方法的命名是相等的，不能作为方法的重载。

可变参数，即可向函数传递 0 个或多个参数，如：

```java
void function("Wallen","John","Smith");
void function(new String [] {"Wallen","John","Smith"});
```

这两种调用方法效果是一样的。

对于可变参数的方法重载。

```java
void function(String... args);
void function(String args1,String args2);
function("Wallen","John");
```

#### finalize() 方法

Java 允许定义这样的方法，它在对象被垃圾收集器析构(回收)之前调用，这个方法叫做 finalize( )，它用来清除回收对象。

例如，你可以使用 finalize() 来确保一个对象打开的文件被关闭了。

在 finalize() 方法里，你必须指定在对象销毁时候要执行的操作。

```java
protected void finalize()
{
   // 在这里终结代码
}
```

Java 的内存回收可以**由 JVM 来自动完成**。如果你手动使用，则可以使用上面的方法。

---

### Java 流(Stream)、文件(File)和IO

Java.io 包几乎包含了所有操作输入、输出需要的类。所有这些流类代表了输入源和输出目标。

Java.io 包中的流支持很多种格式，比如：基本类型、对象、本地化字符集等等。

一个流可以理解为一个数据的序列。输入流表示从一个源读取数据，输出流表示向一个目标写数据。

---

Java中的字节流处理的最基本单位为**单个字节**，它通常用来处理**二进制数据**。Java中最基本的两个字节流类是**InputStream**和**OutputStream**，它们分别代表了最基本的输入字节流和输出字节流。InputStream是所有字节输入流的祖先，而OutputStream是所有字节输出流的祖先，它们都是抽象类。
**字节流和字符流的区别**

+ 字节流操作的基本单元为字节；字符流操作的基本单元为Unicode码元。
+ 字节流默认不使用缓冲区；字符流使用缓冲区。
+ 字节流在操作的时候本身是不会用到缓冲区的，是与文件本身直接操作的，所以字节流在操作文件时，即使不关闭资源，文件也能输出；字符流在操作的时候是使用到缓冲区的。如果字符流不调用close或flush方法，则不会输出任何内容。
+ 字节流通常用于处理二进制数据，实际上它可以处理任意类型的数据，但它不支持直接写入或读取Unicode码元；字符流通常处理文本数据，它支持写入及读取Unicode码元。
+ 字节流可用于任何类型的对象，包括二进制对象，而字符流只能处理字符或者字符串； 字节流提供了处理任何类型的IO操作的功能，但它不能直接处理Unicode字符，而字符流就可以。

**字节流和字符流的转换**

- 这两个之间通过 **InputStreamReader**,**OutputStreamWriter**来关联，实际上是通过byte[]和String来关联。在从字节流转化为字符流时，实际上就是byte[]转化为String时，而在字符流转化为字节流时，实际上是String转化为byte[]时。

#### InputStream（字节输入流）

- `read()`：返回输入流中下一个字节的数据。返回的值介于 0 到 255 之间。如果未读取任何字节，则代码返回 `-1` ，表示文件结束。
- `read(byte b[ ])` : 从输入流中读取一些字节存储到数组 `b` 中。如果数组 `b` 的长度为零，则不读取。如果没有可用字节读取，返回 `-1`。如果有可用字节读取，则最多读取的字节数最多等于 `b.length` ， 返回读取的字节数。这个方法等价于 `read(b, 0, b.length)`。
- `read(byte b[], int off, int len)`：在`read(byte b[ ])` 方法的基础上增加了 `off` 参数（偏移量）和 `len` 参数（要读取的最大字节数）。
- `skip(long n)`：忽略输入流中的 n 个字节 ,返回实际忽略的字节数。
- `available()`：返回输入流中可以读取的字节数。
- `close()`：关闭输入流释放相关的系统资源。

从 Java 9 开始，`InputStream` 新增加了多个实用的方法：

- `readAllBytes()`：读取输入流中的所有字节，返回字节数组。
- `readNBytes(byte[] b, int off, int len)`：阻塞直到读取 `len` 个字节。
- `transferTo(OutputStream out)`：将所有字节从一个输入流传递到一个输出流。

---

```java
try (InputStream fis = new FileInputStream("input.txt")) {
    System.out.println("Number of remaining bytes:"
            + fis.available());
    int content;
    long skip = fis.skip(2);
    System.out.println("The actual number of bytes skipped:" + skip);
    System.out.print("The content read from file:");
    while ((content = fis.read()) != -1) {
        System.out.print((char) content);
    }
} catch (IOException e) {
    e.printStackTrace();
}

```

一般是不会直接单独使用 `FileInputStream` ，通常会配合 `BufferedInputStream`（字节缓冲输入流，后文会讲到）来使用。

```java
// 新建一个 BufferedInputStream 对象
BufferedInputStream bufferedInputStream = new BufferedInputStream(new FileInputStream("input.txt"));
// 读取文件的内容并复制到 String 对象中
String result = new String(bufferedInputStream.readAllBytes());
System.out.println(result);

```

`DataInputStream` 用于读取指定类型数据，不能单独使用，必须结合其它流，比如 `FileInputStream` 。

```java
FileInputStream fileInputStream = new FileInputStream("input.txt");
//必须将fileInputStream作为构造参数才能使用
DataInputStream dataInputStream = new DataInputStream(fileInputStream);
//可以读取任意具体的类型数据
dataInputStream.readBoolean();
dataInputStream.readInt();
dataInputStream.readUTF();

```

`ObjectInputStream` 用于从输入流中读取 Java 对象（反序列化），`ObjectOutputStream` 用于将对象写入到输出流(序列化)。

```java
ObjectInputStream input = new ObjectInputStream(new FileInputStream("object.data"));
MyClass object = (MyClass) input.readObject();
input.close();
```

另外，用于序列化和反序列化的类必须实现 `Serializable` 接口，对象中如果有属性不想被序列化，使用 `transient` 修饰。

#### OutputStream(字节输出流)

`OutputStream`用于将数据（字节信息）写入到目的地（通常是文件），`java.io.OutputStream`抽象类是所有字节输出流的父类。

`OutputStream` 常用方法：

- `write(int b)`：将特定字节写入输出流。
- `write(byte b[ ])` : 将数组`b` 写入到输出流，等价于 `write(b, 0, b.length)` 。
- `write(byte[] b, int off, int len)` : 在`write(byte b[ ])` 方法的基础上增加了 `off` 参数（偏移量）和 `len` 参数（要读取的最大字节数）。
- `flush()`：刷新此输出流并强制写出所有缓冲的输出字节。
- `close()`：关闭输出流释放相关的系统资源。

```java
try (FileOutputStream output = new FileOutputStream("output.txt")) {
    byte[] array = "JavaGuide".getBytes();
    output.write(array);
} catch (IOException e) {
    e.printStackTrace();
}

```

如果音频文件、图片等媒体文件用**字节流**比较好，如果**涉及到字符的话使用字符流**比较好。

#### Reader（字符输入流）

`Reader`用于从源头（通常是文件）读取数据（字符信息）到内存中，`java.io.Reader`抽象类是所有字符输入流的父类。

`Reader` 用于读取文本， `InputStream` 用于读取原始字节。

`Reader` 常用方法：

- `read()` : 从输入流读取一个字符。
- `read(char[] cbuf)` : 从输入流中读取一些字符，并将它们存储到字符数组 `cbuf`中，等价于 `read(cbuf, 0, cbuf.length)` 。
- `read(char[] cbuf, int off, int len)`：在`read(char[] cbuf)` 方法的基础上增加了 `off` 参数（偏移量）和 `len` 参数（要读取的最大字符数）。
- `skip(long n)`：忽略输入流中的 n 个字符 ,返回实际忽略的字符数。
- `close()` : 关闭输入流并释放相关的系统资源。

`InputStreamReader` 是字节流转换为字符流的桥梁，其子类 `FileReader` 是基于该基础上的封装，可以直接操作字符文件。

```java
// 字节流转换为字符流的桥梁
public class InputStreamReader extends Reader {
}
// 用于读取字符文件
public class FileReader extends InputStreamReader {
}

```

#### 字节缓冲流

IO 操作是很消耗性能的，缓冲流将数据加载至缓冲区，一次性读取/写入多个字节，从而避免频繁的 IO 操作，提高流的传输效率。

字节缓冲流这里采用了装饰器模式来增强 `InputStream` 和`OutputStream`子类对象的功能。

举个例子，我们可以通过 `BufferedInputStream`（字节缓冲输入流）来增强 `FileInputStream` 的功能。

```java
// 新建一个 BufferedInputStream 对象
BufferedInputStream bufferedInputStream = new BufferedInputStream(new FileInputStream("input.txt"));

```

字节流和字节缓冲流的性能差别主要体现在我们使用两者的时候都是调用 `write(int b)` 和 `read()` 这两个一次只读取一个字节的方法的时候。由于字节缓冲流内部有缓冲区（字节数组），因此，字节缓冲流会先将读取到的字节存放在缓存区，大幅减少 IO 次数，提高读取效率。

```java
package com.zhounian.streamfileIO;

import java.io.*;

public class BufferWithFileInput {
    public static void main(String[] args) {
        copy_pdf_to_another_zip_buffer_stream();
        copy_pdf_to_another_zip_stream();

    }
    static void copy_pdf_to_another_zip_buffer_stream() {
        // 记录开始时间
        long start = System.currentTimeMillis();
        try (BufferedInputStream bis = new BufferedInputStream(new FileInputStream("demomusic-java.zip"));
             BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("demomusic-java-copy.zip"))) {
            int content;
            while ((content = bis.read()) != -1) {
                bos.write(content);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
        // 记录结束时间
        long end = System.currentTimeMillis();
        System.out.println("使用缓冲流复制zip文件总耗时:" + (end - start) + " 毫秒");
    }

    static void copy_pdf_to_another_zip_stream() {
        // 记录开始时间
        long start = System.currentTimeMillis();
        try (FileInputStream fis = new FileInputStream("demomusic-java.zip");
             FileOutputStream fos = new FileOutputStream("demomusic-java-copy2.zip")) {
            int content;
            while ((content = fis.read()) != -1) {
                fos.write(content);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
        // 记录结束时间
        long end = System.currentTimeMillis();
        System.out.println("使用普通流复制zip文件总耗时:" + (end - start) + " 毫秒");
    }

}

```

```java
运行结果:
使用缓冲流复制zip文件总耗时:364 毫秒
使用普通流复制zip文件总耗时:47637 毫秒
```

#### 字符缓冲流

`BufferedReader` （字符缓冲输入流）和 `BufferedWriter`（字符缓冲输出流）类似于 `BufferedInputStream`（字节缓冲输入流）和`BufferedOutputStream`（字节缓冲输入流），内部都维护了一个字节数组作为缓冲区。不过，前者主要是用来操作字符信息。

---

`RandomAccessFile` 比较常见的一个应用就是实现大文件的 **断点续传** 。何谓断点续传？简单来说就是上传文件中途暂停或失败（比如遇到网络问题）之后，不需要重新上传，只需要上传那些未成功上传的文件分片即可。分片（先将文件切分成多个文件分片）上传是断点续传的基础。

**FileInputStream**

该流用于从文件读取数据，它的对象可以用关键字 new 来创建。

有多种构造方法可用来创建对象。

可以使用字符串类型的文件名来创建一个输入流对象来读取文件：

```java
InputStream f = new FileInputStream("C:/java/hello");
```

也可以使用一个文件对象来创建一个输入流对象来读取文件。我们首先得使用 File() 方法来创建一个文件对象：

```java
File f = new File("C:/java/hello"); InputStream in = new FileInputStream(f);
```

创建了InputStream对象，就可以使用下面的方法来读取流或者进行其他的流操作。

---

### java Scanner类

```java
import java.util.Scanner; 
 
public class ScannerDemo {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        // 从键盘接收数据
 
        // next方式接收字符串
        System.out.println("next方式接收：");
        // 判断是否还有输入
        if (scan.hasNext()) {
            String str1 = scan.next();
            System.out.println("输入的数据为：" + str1);
        }
        scan.close();
    }
}
```

```java
运行结果:

next方式接收：
runoob com
输入的数据为：runoob
```

```java
import java.util.Scanner;
 
public class ScannerDemo {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        // 从键盘接收数据
 
        // nextLine方式接收字符串
        System.out.println("nextLine方式接收：");
        // 判断是否还有输入
        if (scan.hasNextLine()) {
            String str2 = scan.nextLine();
            System.out.println("输入的数据为：" + str2);
        }
        scan.close();
    }
}
```

```java
运行结果:

nextLine方式接收：
runoob com
输入的数据为：runoob com
```

`next() 与 nextLine() 区别`

next():

- 1、一定要读取到有效字符后才可以结束输入。
- 2、对输入有效字符之前遇到的空白，next() 方法会自动将其去掉。
- 3、只有输入有效字符后才将其后面输入的空白作为分隔符或者结束符。
- next() 不能得到带有空格的字符串。

nextLine()：

- 1、以Enter为结束符,也就是说 nextLine()方法返回的是输入回车之前的所有字符。
- 2、可以获得空白。

### java 异常处理

异常发生的原因有很多，通常包含以下几大类：

- 用户输入了非法数据。
- 要打开的文件不存在。
- 网络通信时连接中断，或者JVM内存溢出。

[异常的分类](https://www.runoob.com/java/java-exceptions.html)

#### 捕获异常

使用 try 和 catch 关键字可以捕获异常。try/catch 代码块放在异常可能发生的地方。

try/catch代码块中的代码称为保护代码，使用 try/catch 的语法如下：

```java
try
{
   // 程序代码
}catch(ExceptionName e1)
{
   //Catch 块
}

```

#### throws/throw 关键字

**throw** 关键字用于在代码中抛出异常，而 **throws** 关键字用于在方法声明中指定可能会抛出的异常类型。

#### finally关键字

finally 关键字用来创建在 try 代码块后面执行的代码块。

无论是否发生异常，finally 代码块中的代码总会被执行。

在 finally 代码块中，可以运行清理类型等收尾善后性质的语句。

finally 代码块出现在 catch 代码块最后，语法如下：

```java
try{
  // 程序代码
}catch(异常类型1 异常的变量名1){
  // 程序代码
}catch(异常类型2 异常的变量名2){
  // 程序代码
}finally{
  // 程序代码
}
```

```java
执行顺序
try{
   //待捕获代码    
}catch（Exception e）{
    System.out.println("catch is begin");//------(1)
    return 1 ；							//------(4)
}finally{
     System.out.println("finally is begin");//------(2)
     return 2 ;								//------(3)
}
```

就是执行了finally后已经return了，所以catch里面的return不会被执行到。也就是说finally永远都会在catch的return前被执行。

#### try-with-resources

JDK7 之后，Java 新增的 **try-with-resource** 语法糖来打开资源，并且可以在语句执行完毕后确保每个资源都被自动关闭 。

try-with-resources 是一种异常处理机制，它可以简化资源管理代码的编写。

JDK7 之前所有被打开的系统资源，比如流、文件或者 Socket 连接等，都需要被开发者手动关闭，否则将会造成资源泄露。

```java
try (resource declaration) {
  // 使用的资源
} catch (ExceptionType e1) {
  // 异常块
}
```

#### 自定义异常

在 Java 中你可以自定义异常。编写自己的异常类时需要记住下面的几点。

- 所有异常都必须是 Throwable 的子类。
- 如果希望写一个检查性异常类，则需要继承 Exception 类。
- 如果你想写一个运行时异常类，那么需要继承 RuntimeException 类。

可以像下面这样定义自己的异常类：

```java
class MyException extends Exception{
}
```

 ### java 继承

需要注意的是 Java 不支持多继承，但支持多重继承。

### 继承的特性

- 子类拥有父类非 private 的属性、方法。
- 子类可以拥有自己的属性和方法，即子类可以对父类进行扩展。
- 子类可以用自己的方式实现父类的方法。
- Java 的继承是单继承，但是可以多重继承，单继承就是一个子类只能继承一个父类，多重继承就是，例如 B 类继承 A 类，C 类继承 B 类，所以按照关系就是 B 类是 C 类的父类，A 类是 B 类的父类，这是 Java 继承区别于 C++ 继承的一个特性。
- 提高了类之间的耦合性（继承的缺点，耦合度高就会造成代码之间的联系越紧密，代码独立性越差）。

---

继承可以使用 extends 和 implements 这两个关键字来实现继承，而且所有的类都是继承于 java.lang.**Object**，当一个类没有继承的两个关键字，则默认继承 Object（这个类在 **java.lang** 包中，所以不需要 **import**）祖先类。

#### implements关键字

使用 implements 关键字可以变相的使java具有多继承的特性，使用范围为类继承接口的情况，可以同时继承多个接口（接口跟接口之间采用逗号分隔）。

```java
public interface A {
    public void eat();
    public void sleep();
}
 
public interface B {
    public void show();
}
 
public class C implements A,B {
}
```

#### super 与 this 关键字

super关键字：我们可以通过super关键字来实现对父类成员的访问，用来引用当前对象的父类。

this关键字：指向自己的引用。

super

- 调用父类的构造方法；
- 调用父类的方法（子类覆盖了父类的方法时）；
- 访问父类的数据域（可以这样用但没有必要这样用）。

调用父类的构造方法语法：

```java
super();  

或   

super(参数列表);

```

注意：**super 语句必须是子类构造方法的第一条语句**。不能在子类中使用父类构造方法名来调用父类构造方法。 父类的构造方法不被子类继承。调用父类的构造方法的唯一途径是使用 super 关键字，如果子类中没显式调用，则编译器自动将 super(); 作为子类构造方法的第一条语句。这会形成一个构造方法链。

静态方法中不能使用 super 关键字。

调用父类的方法语法：

```java
super.方法名(参数列表);
```

如果是继承的方法，是没有必要使用 super 来调用，直接即可调用。但如果**子类覆盖或重写**了父类的方法，则只有使用 super 才能在子类中调用父类中的被重写的方法。

#### 构造器

子类是不继承父类的构造器（构造方法或者构造函数）的，**它只是调用（隐式或显式）**。如果父类的构造器带有参数，则必须在子类的构造器中显式地通过 `super` 关键字调用父类的构造器并配以适当的参数列表。

**如果父类构造器没有参数，则在子类的构造器中不需要使用 `super`关键字调用父类构造器，系统会自动调用父类的无参构造器。**

在执行子类的构造函数前，总是会先执行父类中的构造函数。

```java
class SuperClass {
  private int n;
  SuperClass(){
    System.out.println("SuperClass()");
  }
  SuperClass(int n) {
    System.out.println("SuperClass(int n)");
    this.n = n;
  }
}
// SubClass 类继承
class SubClass extends SuperClass{
  private int n;
  
  SubClass(){ // 自动调用父类的无参数构造器
    System.out.println("SubClass");
  }  
  
  public SubClass(int n){ 
    super(300);  // 调用父类中带有参数的构造器
    System.out.println("SubClass(int n):"+n);
    this.n = n;
  }
}
// SubClass2 类继承
class SubClass2 extends SuperClass{
  private int n;
  
  SubClass2(){
    super(300);  // 调用父类中带有参数的构造器
    System.out.println("SubClass2");
  }  
  
  public SubClass2(int n){ // 自动调用父类的无参数构造器
    System.out.println("SubClass2(int n):"+n);
    this.n = n;
  }
}
public class TestSuperSub{
  public static void main (String args[]){
    System.out.println("------SubClass 类继承------");
    SubClass sc1 = new SubClass();
    SubClass sc2 = new SubClass(100); 
    System.out.println("------SubClass2 类继承------");
    SubClass2 sc3 = new SubClass2();
    SubClass2 sc4 = new SubClass2(200); 
  }
}
```

```java
运行结果:
------SubClass 类继承------
SuperClass()
SubClass
SuperClass(int n)
SubClass(int n):100
------SubClass2 类继承------
SuperClass(int n)
SubClass2
SuperClass()
SubClass2(int n):200
```

---

```java
当你不清楚你需要的参数是什么类型的，可以用Object来代替，Object可以代替任何类
```

子类不能直接继承父类中的 private 属性和方法。

```java
public class Animal {
    private String name;
    private int id;
    /*由于name和id都是私有的，所以子类不能直接继承，
    需要通过有参构造函数进行继承*/
    public Animal(String myname,int myid) {
        name = myname;
        id = myid;
    }
}

public class Penguin extends Animal {
    public Penguin(String myname,int myid) {
        super(myname,myid); // 声明继承父类中的两个属性
    }
}
```

#### java 转型

**父类引用指向子类对象**。

```java
Father f1 = new Son();   // 这就叫 upcasting （向上转型)
// 现在 f1 引用指向一个Son对象

Son s1 = (Son)f1;   // 这就叫 downcasting (向下转型)
// 现在f1 还是指向 Son对象
```

```java
Father f2 = new Father();
Son s2 = (Son)f2;       // 出错，子类引用不能指向父类对象
```

1、父类引用指向子类对象，而子类引用不能指向父类对象。

2、把子类对象直接赋给父类引用叫upcasting向上转型，向上转型不用强制转换吗，如：

```java
Father f1 = new Son();
```

**向上转型**

```java
Animal b=new Bird(); //向上转型
b.eat();
```

此处将调用子类的 eat() 方法。原因：b 实际指向的是 Bird 子类，故调用时会调用子类本身的方法。

需要注意的是向上转型时 b 会遗失除与父类对象共有的其他方法。

```java
public class Human {
  public void sleep() {
    System.out.println("Human sleep..");
  }
}
class Male extends Human {
  @Override
  public void sleep() {
    System.out.println("Male sleep..");
  }
}
class Female extends Human {
  @Override
  public void sleep() {
    System.out.println("Female sleep..");
  }
}
```

向上转型好处:

```java
public static void dosleep(Human h) {
    h.sleep();
}
```

这里以父类为参数，调有时用子类作为参数，就是利用了向上转型。这样使代码变得简洁。不然的话，如果 dosleep 以子类对象为参数，则有多少个子类就需要写多少个函数。这也体现了 JAVA 的抽象编程思想。

**向下转型**

与向上转型相反，即是把父类对象转为子类对象。

---

### Java 重写(Override)与重载(Overload)

**重写规则**

- 参数列表与被重写方法的参数列表必须完全相同。
- 返回类型与被重写方法的返回类型可以不相同，但是必须是父类返回值的派生类（java5 及更早版本返回类型要一样，java7 及更高版本可以不同）。
- 访问权限不能比父类中被重写的方法的访问权限更低。例如：如果父类的一个方法被声明为 public，那么在子类中重写该方法就不能声明为 protected。
- 父类的成员方法只能被它的子类重写。
- 声明为 final 的方法不能被重写。
- 声明为 static 的方法不能被重写，但是能够被再次声明。
- 子类和父类在同一个包中，那么子类可以重写父类所有方法，除了声明为 private 和 final 的方法。
- 子类和父类不在同一个包中，那么子类只能够重写父类的声明为 public 和 protected 的非 final 方法。
- 重写的方法能够抛出任何非强制异常，无论被重写的方法是否抛出异常。但是，重写的方法不能抛出新的强制性异常，或者比被重写方法声明的更广泛的强制性异常，反之则可以。
- 构造方法不能被重写。
- 如果不能继承一个类，则不能重写该类的方法。

#### 重载（Overload）

重载(overloading) 是在一个类里面，方法名字相同，而参数不同。返回类型可以相同也可以不同。

每个重载的方法（或者构造函数）都必须有一个独一无二的参数类型列表。

最常用的地方就是构造器的重载。

- 被重载的方法必须改变参数列表(参数个数或类型不一样)；
- 被重载的方法可以改变返回类型；
- 被重载的方法可以改变访问修饰符；
- 被重载的方法可以声明新的或更广的检查异常；
- 方法能够在同一个类中或者在一个子类中被重载。
- **无法以返回值类型作为重载函数的区分标准。**

重写与重载之间的区别

| 区别点   | 重载方法 | 重写方法                                       |
| :------- | :------- | :--------------------------------------------- |
| 参数列表 | 必须修改 | 一定不能修改                                   |
| 返回类型 | 可以修改 | 一定不能修改                                   |
| 异常     | 可以修改 | 可以减少或删除，一定不能抛出新的或者更广的异常 |
| 访问     | 可以修改 | 一定不能做更严格的限制（可以降低限制）         |

---

重载就是同样的一个方法能够根据输入数据的不同，做出不同的处理

重写就是当子类继承自父类的相同方法，输入数据一样，但要做出有别于父类的响应时，你就要覆盖父类方法

---

### Java 多态

**多态存在的三个必要条件**

- 继承
- 重写
- 父类引用指向子类对象：**Parent p = new Child();**

```java
class Shape {
    void draw() {}
}
  
class Circle extends Shape {
    void draw() {
        System.out.println("Circle.draw()");
    }
}
  
class Square extends Shape {
    void draw() {
        System.out.println("Square.draw()");
    }
}
  
class Triangle extends Shape {
    void draw() {
        System.out.println("Triangle.draw()");
    }
}
```

当使用多态方式调用方法时，首先检查父类中**是否有该方法**，如果没有，则编译错误；如果有，再去调用子类的同名方法。

多态的好处：可以使程序有良好的扩展，并可以对所有类的对象进行通用处理。

**类的属性变量是能重写（覆盖）**

**静态方法**被子类重写，要看父类引用还是子类引用指向子类对象，如果是父类引用指向子类对象，那么调静态方法时，会调用父类的静态方法，如果是子类引用指向子类对象，那么调静态方法时，会调用子类的静态方法。

### java 抽象类

