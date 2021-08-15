## 1.1 Golang的学习方向

* 区块链研发工程师
* Go服务器端/游戏软件工程师
* Golang分布式/云计算软件工程师

## 1.2 Go程序开发注意事项

1. 后缀名为`.go`
2. 执行入口是`main`函数
3. 严格区分大小写
4. 语句后不需要加 `;` Go语言每行后自动加`;`
5. 编译器一行一行编译，一行只写一条语句
6. Go语言**声明的变量**或**import的包**必须被使用，否则代码不通过编译

## 1.3 Go语言转义字符(escape char)

1. `\t `	: 制表位，实现对齐的功能，排版用
2. `\n`    ：换行符 
3. `\\`    ：  \
4. `\"`    ： "
5. `\r`    ： 回车（不换行）

## 2.1 Golang变量

### 2.1.1 变量的声明，初始化和赋值

声明并初始化一个变量  'i' : `vat i (变量类型) = (值)`

1. 变量表示内存中的一个储存区域
2. 该区域有自己的名称和类型

<img src="https://i.loli.net/2020/03/26/DUg48smiTaKqRXc.png"  />

3. 变量的使用有三种方式

	* 指定变量类型，声明后若不赋值，使用默认值 `var i int //i = 0`
	* 根据值自行判定变量类型（类型推导）`var num = 10.11 //num为double`
	* 省略var，使用 `:=` 赋值  [ 注意`:=`左侧变量不应该是已经声明过的 ]  `name := "tom"`
4. 多变量声明   
   * `var n1, n2, n3 int`
   * `var a, b, c = 100 , "jk" , 10.22` 
   * `a,b,c := 100, "tom", 1.21`
5. 变量在同一个作用域（函数或代码块）内不能重名

### 2.1.2  ' + ' 的使用

* 两边是数值时做 **加法运算**
* 两边是字符串是做 **字符串的拼接**

<img src="https://i.loli.net/2020/03/27/LghQSFf6CDwW2Ii.png" style="zoom: 67%;" />

### 2.1.3 变量的数据类型

<img src="https://i.loli.net/2020/03/27/oU7ZvwcV6fI95zS.png" style="zoom: 50%;" />

## 2.2 整数类型

![](https://i.loli.net/2020/04/01/GWjQg62YFyvhwqa.png)

有符号int：

![](https://i.loli.net/2020/04/01/9j5dW26boDwKhv3.png)

无符号uint：

![](https://i.loli.net/2020/04/01/XljTfWpycN6vYnV.png)

使用细节：

1. 默认声明为int型
2. 查看数据类型和字节数 （`"%T  %d", n,unsafe.Sizeof(n)`）
![](https://i.loli.net/2020/04/01/1EcWs2TuvdBYFNO.png)
3. 使用过程中，遵守保小不保大原则(尽量使用较小的数据类型)



