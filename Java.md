# Java



**第一个Java程序：计算圆的面积**

```c
package com.company;//将源文件打包，在其它源文件里可以用import来引用本源文件的类

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
	double radius;
	double area;
	Scanner input = new Scanner(System.in);//scanner类是存放于java.util包中的，因此程序使用import语句导入该类（在使用时会自动补全导入）
	System.out.print("请输入半径： ");
	radius = input.nextDouble();//scanner类有nexInt（）方法或nextDouble()方法
	area = Math.PI *radius *radius;
	System.out.println("圆的面积为："+area);
	for (int i = 0;i<=9;i++)
	{
		for(int j = 0;j<=i;j++)
		{
			System.out.print("*");
		}
		System.out.print("\n");
	}
    }
}
```

**注意：在输入的数据与要获得得到数据不匹配时，会产生InputMismatchExecption的error**

**Scanner类**：

从键盘读取数据可以使用Scanner类的nextInt（）方法和nextDouble（）方法以及nextLine读取一行文本等。





**Java数据类型**

Java数据类型与c基本相同，但是需要注意的是，Java里面多了byte类型（占用空间极小的整数类型）和boolean类型，**另外char类型在Java中占两个字节而非一个字节**

![img](https://gss0.baidu.com/9fo3dSag_xI4khGko9WTAnF6hhy/zhidao/wh%3D600%2C800/sign=fa95881bcdfdfc03e52debbee40fabac/e4dde71190ef76c6958685ce9316fdfaae5167fa.jpg)

#### **字面值和常量**：

**字面值(literals)是某种类型值的表示形式**

比如100是int类型的字面值。

字面值分为：基本类型的字面值，字符串字面值以及null字面值。

**常量**

常量使用**final**修饰，一旦为其赋值，其值在程序中便不能被更改

比如

```c
final int SNO;
final int max_array_size = 22;
final double pi = 3.1415926;
```

### **为对象定义类**

#### **（1）类的修饰符：**

类的访问修饰符可以是public或缺省。若用public修饰，则称该类为公共类，公共类可被任何包中的类使用。如果不加public修饰符，则只能被同一个包中的其它类使用。

**没有用static修饰的方法称为实例方法，用static修饰的方法称为静态方法。**

**如果使用abstract修饰符，则该类为抽象类**。

若用final修饰符，则该类为最终类，是静态

**注意：父类的private成员方法是不能被子类方法覆盖的，因此private类型的方法默认是final类型的。**
 **1、final类**

final类不能被继承，因此final类的成员方法没有机会被覆盖，默认都是final的。在设计类时候，如果这个类不需要有子类，类的实现细节不允许改变，并且确信这个类不会载被扩展，那么就设计为final类。

**2、final方法**
 如果一个类不允许其子类覆盖某个方法，则可以把这个方法声明为final方法。使用final方法的原因有二：
 ①把方法锁定，防止任何继承类修改它的意义和实现。
 ②高效，编译器在遇到调用final方法时候会转入内嵌机制，大大提高执行效率。

#### （2）extends SuperClass

如果一个类要继承某个类需要使用extends指明该类的父类，SuperClass为父类名，即定义该类继承了哪个类。如果定义类的时候没有指明所继承的父类，那么它自动继承Object类。

#### （3）类体：

类声明结束后是一对大括号，大括号括起来的部分称为类体。类体中通常含三部分内容：构造方法，成员变量，成员方法。构造方法用于创建类实例，成员变量定义对象状态，成员方法定义对象行为。

**方法的访问修饰符**

private 方法只能在同一个类中被调用，

protected方法可以在同一个类，同一个包以及子类中调用，用public修饰的方法可以在任何类中调用。

public方法可以在任何类中调用。

### 堆与栈

内存空间从逻辑上分为栈(stack)和堆(heap)两种结构

**堆：**堆空间的内存一般是动态分配的，用于存放对象，需要手动释放内存。（比如malloc，new，realloc等）

**栈:**存放函数的参数值，局部变量，对象的地址等，由编译器自动分配和释放，通常在函数执行完就释放了。这些在系统层面已经限定住了，程序员只需要在这种约束下进行编程就好。

**从申请的大小方面讲：**

栈空间比较小；

 

堆空间比较大。

**从数据存储方面来说：**

栈空间中一般存储基本数据类型，对象的地址；

堆空间一般存放对象本身，block的copy等。

**创建对象时初始化顺序**：

1.**静态初始化器**

2.**初始化器**

3.**构造方法**

```java
public class Empty {
    private static String name;
    private static int age;
    private static int sex;
    public Empty(){
        //构造方法
    }
    public Empty(String name,int age,int sex){//构造重载
        this.name = name;
        this.age = age;
        this.sex = sex;
    }
    public  void print(){
        System.out.println(true);
    }
    {
        //初始化器，第二加载
    }
    static {
        //静态初始化器，最先加载
    }

    public static String getName() {
        return name;
    }

    public static void setName(String name) {
        Empty.name = name;
    }

    public static int getAge() {
        return age;
    }

    public static void setAge(int age) {
        Empty.age = age;
    }

    public static int getSex() {
        return sex;
    }

    public static void setSex(int sex) {
        Empty.sex = sex;
    }
}

```

**Java数组**：

1格式：

```java
int []array = new int []
  //初始化：int []array = {……}
```



对于引用类型数组（对象数组）还要为每个数组元素分配引用空间。例如：

```java
String []words = new String [7];
words[0] = new String("is"); 
```



java有一个lenth的成员变量，它表示数组元素的个数，访问该成员变量的方法为array.lenth

数组初始化器：(数组静态初始化)

本方法适合数组元素较少的情况

```java
int []marks = new int[]{1,2,4,5,67,9};
```

**增强的for循环：**

```c
for(int score : array)//自动遍历整个数组，从头遍历到尾为止
    等价于for(int i = 0;i<=array.lenth;i++)
    			score=array[i]
```

数组元素的复制。

在System类里的arraycopy方法可以实现数组的快速复制：

System.arraycopy.(源数组，复制源数组的起始位置，目标数组，目标数组的下标位置，要复制的长度)

```c
int []source = {10,20,30,40};
int target = new int[source.length];
System.arraycopy(source,0,target,0,4)//如果木匾数组不足以容纳源数组的元素，会抛出异常
```

**数组参数与返回值**

数组引用复制：

```java
int[] source = {10.30.230.40};
int target = source;//引用赋值
```

上述两条语句实现对象的引用赋值，两个数组引用指向同一个数组对象。

（类似指针）

可以将数组对象作为参数传递给方法。

```java
public static double sunArray(double array[])
```

一个方法还可以返回一个数组对象：

```java
    public static int[] sumArray(int array[]) {
        ……
            return array；
    }//对传入的数组进行加工后返回数组
```

**可变参数的方法**

在Java中，方法传入的参数数量可以改变

```java
public class sumArray {
    public static double average(double ...values) {//可以向方法中传入n个double类型的变量
        double sum = 0;
        for(double value:values)//这n个变量可以看作一个数组，遍历这个数组即可对传入的所有参数进行更改
        {
            sum+=value;
        }
        double average = sum/values.length;
        return average;//返回平均数
    }
}

```

实例：抽牌比大小游戏

```java
import java.math.*;
import java.util.Scanner;

public class Main{
    public static void main(String[]args) {
        int[] desk = new int[52];
        String[] word = {"方块", "梅花", "红桃", "黑桃"};
        String[] ranks = {"A", "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K"};
        for (int i = 0; i < desk.length; i++) {
            desk[i] = i;//初始化每一张牌；
        }
        for (int i = 0; i < desk.length; i++) {
            int temp = (int) (Math.random() * desk.length);//打乱顺序
            int index = desk[i];
            desk[i] = desk[temp];
            desk[temp] = index;//打乱
        }
        System.out.println("A方抽牌：");
        for (int i = 0; i < 3; i++) {
            String color = word[desk[i] / 13];
            String number = ranks[desk[i] / 4];
            System.out.println(color + " " + number);
        }
        System.out.println("B方抽牌：");
        for (int i = 3; i < 6; i++) {
            String color = word[desk[i] / 13];
            String number = ranks[desk[i] / 4];
            System.out.println(color + " " + number);
        }
    }
}

```



### Arrays类

Java.util.Arrays类定义了若干静态方法对数组操作，包括对数组排序（Array.sort(array_name))，

在已排序的数组中查找指定元素（Arrays.binarySearch(int []array_name,int key)//对整型数组查找，返回元素所在位置

（Arrays.binarySearch(Object []array_name,Object key）

**数组元素复制：**目标数组名=Arrays.copyOfRange(源数组，源数组起始下标，结束下标)

**调用Arrays类的fill方法可以将一个值填充到数组的每个元素中**

**数组比较：**Arrays.equals(array1,array2) **返回值为布尔型 **

#### **不规则二维数组**：

java的二维数组是数组的数组，对二维数组声明时可以只指定第一维的大小，第二维的每个元素都可以指定不同的大小。

```java
public class Stack {   
    public static void main(String[] args) {       
        String [][]cities = new String[2][];      
        cities[0][0] = new String("wocoa");      
        cities[0][2] = new String("guangzhou");
    }
}//这种方法使用于低维数组元素个数不同的情况，即每个数组的元素个数可以不同
```

**格式化输出：**

java格式化字符与c基本相同，新增了%b用于输出布尔型元素

**BigInteger和BigDecimal**

在计算中需要非常大的整数和非常高精度的浮点数，可以使用java.math包中定义的**BigInteger和BigDecimal**类。这两个类的实例都是不可变的，

```java
BigInteger abs()  //返回大整数的绝对值
BigInteger add(BigInteger val) //返回两个大整数的和
BigInteger and(BigInteger val)  //返回两个大整数的按位与的结果
BigInteger andNot(BigInteger val) //返回两个大整数与非的结果
BigInteger divide(BigInteger val)  //返回两个大整数的商
double doubleValue()   //返回大整数的double类型的值
float floatValue()   //返回大整数的float类型的值
BigInteger gcd(BigInteger val)  //返回大整数的最大公约数
int intValue() //返回大整数的整型值
long longValue() //返回大整数的long型值
BigInteger max(BigInteger val) //返回两个大整数的最大者
BigInteger min(BigInteger val) //返回两个大整数的最小者
BigInteger mod(BigInteger val) //用当前大整数对val求模
BigInteger multiply(BigInteger val) //返回两个大整数的积
BigInteger negate() //返回当前大整数的相反数
BigInteger not() //返回当前大整数的非
BigInteger or(BigInteger val) //返回两个大整数的按位或
BigInteger pow(int exponent) //返回当前大整数的exponent次方
BigInteger remainder(BigInteger val)                                                                                                                                                                                                                  //返回当前大整数除以val的余数
BigInteger leftShift(int n) //将当前大整数左移n位后返回
BigInteger rightShift(int n) //将当前大整数右移n位后返回
BigInteger subtract(BigInteger val)//返回两个大整数相减的结果
byte[] toByteArray(BigInteger val)//将大整数转换成二进制反码保存在byte数组中
String toString() //将当前大整数转换成十进制的字符串形式
BigInteger xor(BigInteger val) //返回两个大整数的异或
```

Character类：

Character类用于对单个字符进行基本操作。

Character类在对象中包装一个基本类型char的值

Character类的方法：

| 序号 | 方法与描述                                      |
| ---- | ----------------------------------------------- |
| 1    | isLetter()**是否是一个字母**                    |
| 2    | isDight()**是否是一个数字字符**                 |
| 3    | isWhitespace()**是否是一个空白字符**            |
| 4    | isUpperCase()**是否是大写字母**                 |
| 5    | isLowerCase()**是否是小写字母**                 |
| 6    | toUpperCase()**指定字母与大写形式**（大写转换） |
| 7    | toLowerCase()**指定字母小写形式**（小写转换）   |
| 8    | toString()                                      |

例子：

```java
public class Main {

    public static void main(String[] args) throws kid {
        Character ch = 'a';
        System.out.println(Character.toUpperCase('a'));//大写直接转换
    }
}                            
```

