## java程序设计基础

### 标识符

* 标识符由字母、下划线、美元符号和数字组成，长度不受限制

* 标识符的第一个字符不能为数字字符

* 标识符不能为关键字

* 标识符不能为true、false和null

### 命名规范

  * 见名知意
  * 包名：aaa.bbb.ccc
  * 类名：AaaBbbCcc（大驼峰式）
  * 变量名：aaaBbbCcc(小驼峰式)
    * 多为名词

  * 方法名：aaaBbbCcc（小驼峰式）

    * 多为动词

    * aaaBbbCcc （
  
  * 常量名：AAABBBCCC
        

### 关键字

| abstract                                              | assert             | boolean     | break                                                 | byte   |
| ----------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------- | ----------------------------------------------------- | --------------------------------------------- |
| case                                                  | catch               | char           | class           | const                                         |
| continue                                              | default           | do               | double         | else     |
| enum             | extends           | final         | finally       | float                                         |
| for               | goto                                                      | if               | implements | import |
| instanceof | int                   | interface | long                                                  | native                                        |
| new                                                   | package           | private     | protected   | public |
| return         | strictfp         | short         | static         | super   |
| switch         | synchronized | this           | throw           | throws                                        |
| transient   | try                                                       | void]           | volatile     | while   |

### 数据类型

#### 	基本数据类型

1. 数值型：整数型(byte, short, int, long)、浮点型(float, double)
2. 字符型 (char)
3. 布尔型 (boolean)  

   按精度排列：

​	byte short char int long float double

####  引用数据类型(类似指针)

1. 类 (class)
2. 接口(interface)
3. 数组

### 数据的输入输出

#### 可用 `Scanner` 类创建一个对象实现输入

  `Scanner reader = new Scanner(System.in);`

* reader对象调用下列方法来读取数据类型：

  `nextBoolean()`	`nextByte()`	......	`nextDouble()`

* 读取字符串的方法：

  `next()` “空格结束”	`nextLine()`“回车结束”	

* `Scanner` 在java.util包中，使用时要引入`importjava.util`

```java
import java.util.Scanner;
public class Test {
    public static void main(final String[] args) {
        Scanner reader = new Scanner(System.in);//键盘输入
        while (reader.hasNextInt()){//判断缓冲区数据类型
            int i = reader.nextInt();//从缓冲区接收数据
            System.out.println(i);
        }
        System.out.print("over");
    }   
}
```

#### 使用`System`类实现数据输出

* `System.out.println()` 或`System.out.print()` 输出串值，表达式的值，前者输出数据后换行，后者不换行。例如:`System.out.println(m+"个数的和为"+sum);`

* **“+” 两边都是 数值型 或 字符型 时做加法运算，有字符串时完成字符串的连接，例如：**

```java
System.out.println(12+8);
System.out.println(12+""+8);
```



### 数组

* 声明时形式为`int a[];`或者`int []a;`  **注意** ：声明后并不为其分配空间
* 分配元素空间的格式为`a = new int [n];`
* 数组创建后，系统自动给元素一个默认的值。
* 声明数组的同时也可以给数组的元素赋值，如：`float boy[]={21.3f,23.89f,2.0f};`
* 用`.length`输出数组长度。

**数组的引用**：有两数组 a 和 b，当 执行`a = b `时，a 数组就变成了 b 数组。

二维数组实现杨辉三角：

```java
public class Test {
    public static void main(final String[] args) {
      int [][] a = new int [6][6];
      for (int i = 0; i < a.length ; i++){
          for(int j = 0;j <= i ; j++){
                if (j==0 || j==i )
                    a[i][j]=1;
                else a[i][j]=a[i-1][j-1]+a[i-1][j];
          }
      }
      for (int i=0 ; i<a.length ; i++){
          for (int j=0 ;j<6-i-1;j++)
            System.out.print(" ");
          for (int j=0 ;j <= i ;j++)
            System.out.printf(" %2d",a[i][j]);
          System.out.println();          
      }
    }
}
```



### 运算符

* 算术运算符  + , - , * , / ,%
* 自增自减运算符  ++ , --
* 位移运算符 >> , << , >>>
* 关系运算符 < , > , <= , >= , == , !=
* 逻辑运算符 &&  ，|| ，！
* 赋值运算符 =
* 位运算符 & ，| ，~ ， ^
* instanceof  左边操作元为***对象***，右边为***类*** 。当左边的对象是右边类创建的对象时，输出true，否则输出false。















