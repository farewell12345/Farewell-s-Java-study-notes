# 1.数组

数组变量声明：int [] counts或者int counts[]

**创建数组对象：**：int []counts=new int[30];//创建一个数组，存放30个int数据

**所有Java数组都有一个length属性，表示数组的长度**

```java
int []x=new int[4]
   int a= x.length
    System.out.println(a)//输出4
```

**注：数组的length属性为final类型，不能被更改**

**用符号“...”声明数目可变参数：**

Java中可以使用符号**“...”来声明数目可变参数**

例如：

```java
int max(int a,int b,int c)
```

上边的方法可以简化为：

```java
int max(int...a)//方法允许有n个参数a传入
```

**可变参数特点：**

1.只能出现在参数列表的最后，作为最后一个参数。

```java
void method(int p1,int p2,String...p3){.......}//合法
void method(int p1,String ...p2,int p3){.......}//非法
```

2.符号“…”位于参数类型和参数名之间，前后有无空格都可以。

3.Java虚拟机在运行时为可变参数隐含创建一个数组，因此在方法体允许以数组形式访问可变参数.

```java
public class Throw {
    public int max(int ...data){
        if(data.length==0){
            return -1;
        }
        int result=0;
        for (int a:data) {
            if (result<a)result=a;
        }
        return result;
    }
}
public class Main {

    public static void main(String[] args) {
        Throw th = new Throw();
        System.out.println(th.max(1,12,4,2,3,2,3));
    }
}//输出12
```

**数组小结：**

Java中数组也是一种对象，必须通过new语句来创建：

```java
int []a=new int[30];  
```

创建数组后，**数组中每个元素都会被自动赋予为其数据类型的默认值**。

**数组有一个length属性，表示数组中元素的数目，该属性可以被读取，但不能修改**

**数组中的每一个元素都有唯一的索引，它表示元素在数组中位置，第一个元素为0，最后一个元素索引为length-1**

# 集合：

​	Java的集合时通过类来实现的。Java集合不仅可以方便地存放数据，而且提供了对数据进行添加，读取和删除等方法。

​	**Java集合中不能存放基本类型地数据，而且只能存放引用类型的数据。**

Java集合主要分为三类：

| set（集）         | 集合中的对象不按特定方式排序，并且没有重复对象。它的有些实现类（TreeSet）能对集合中对象按特定方式排序号 |
| ----------------- | ------------------------------------------------------------ |
| **List（列表）**  | 集合中的对象按照索引位置排序，可以有重复的对象，允许按照对象在集合中的索引位置检索对象 |
| **Queue（队列）** | 集合中的对象按照先进先出的规则来排列。在队列的末尾添加元素，在队列的头部删除元素 |
| **Map（映射）**   | 和集合有点类似，但是特殊之处在于集合中每一个元素包含一对键（Key）对象和值（value）对象，**集合中没有重复的键对象，值对象可以重复**。就像函数中x和y之间的映射关系，它的有些实现类（TreeMap）能对集合中的键对象进行排序） |

