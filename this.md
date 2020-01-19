## this的使用：

## **基础作用：**

this表示对象本身。再一个方法的方法体或参数中，可能声明与成员变量同名的局部变量，此时的局部变量会隐藏成员变量。要使用成员变量就需要再前面加上this关键字。

```java
class Plan {
    String name;
    int n;
    public Plan (String name,int n){
        this.name = name;//将传入参数的值赋给类中的成员变量
        this.n = n;//允许成员变量与传入参数名相同
    }
}
```

还可以用this在方法中调用属于该类中的其它方法

```java
package com.company;


public class Main{
    public static void main(String[]args){
    Plan imp = new Plan("李涛",10);
    imp.Wolf("李涛","陈昊");
    }
}


class Plan {
    String name;
    int n;
    public Plan (String name,int n){
        this.name = name;
        this.n = n;
        this.Wolf(name,name);//用this调用方法
    }
    public Plan(String name,String master){
        System.out.printf("The %s is %s\n",name,master);
    }

    void Wolf(String str,String name){
        this.name = str;
        System.out.println(name);
        for(int i = 0;i<=5;i++){
            System.out.print("汪");
        }            
        System.out.println();
    }

}

```

综上所述，this关键字主要用在下面三种情况：

**1.解决局部变量和成员变量同名的问题**

**2.解决方法参数与成员变量同名的问题**

**3.用来调用该类的另一个构造方法**

#### 注意：

**Java规定，this只能同在非static方法中，不能用在static方法中。**

实际上在对象调用一个非static方法时，向方法传递了一个引用，这个引用就是对象本身，在方法体中用this表示

##  this 

this 是自身的一个对象，代表对象本身，可以理解为：**指向对象本身的一个指针。**
this 的用法在 Java 中大体可以分为3种：
1.普通的直接引用
这种就不用讲了，this 相当于是指向当前对象本身。
2.形参与成员名字重名，用 this 来区分：
实例

```java
class Person {
  private int age = 10;
  public Person(){
  System.out.println("初始化年龄："+age);
}
  public int GetAge(int age){
    this.age = age;
    return this.age;
  }
}

public class test1 {
  public static void main(String[] args) {
    Person Harry = new Person();
    System.out.println("Harry's age is "+Harry.GetAge(12));
  }
}
```



运行结果：
初始化年龄：10
Harry's age is 12
可以看到，这里 age 是 GetAge 成员方法的形参，this.age 是 Person 类的成员变量。