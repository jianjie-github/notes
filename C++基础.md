# C++基础

## 1 认识C++

### 1.1 起源

贝尔实验室20实际80 年代初，本贾尼·斯特劳斯特鲁普

### 1.2 应用范围

* 文字处理程序以及电子表格

* 编译器

* 操作系统

* 大型游戏

### 1.3 从C到C++

* C语言是结构化和模块化的语言，面向过程。未完全实现解决软件设计危机的目标

* C++保留了C语言原有的所有优点，增加了面向对象的机制

* [C++为什么要面向对象？](https://www.cnblogs.com/zhuzhenwei918/p/9109917.html)

### 1.4 编写“hello world”

```C++
#include <iostream>
using namespace std;

int main()
{
 	cout << "hello world" << endl;
	system("pause");
	return 0;
}
```

### 1.5 注释

作用：在代码中加入一些说明和解释，方便自己或其他程序员阅读代码

两种格式：

单行注释：`//描述信息`

多行注释：`/*描述信息*/`

### 1.6 变量

作用：给一段指定的内容空间起名，方便操作这段内存，方便管理内存空间

语法：数据类型 变量名=初始值 ，如int  a  = 10

```C++
#include <iostream>
using namespace std;

int main()
{
	int a = 10;
	cout << "a =" << a <<endl;
	system("pause");
	return 0;
}
```

### 1.7 常量

作用：用于记录程序中不可更改的数据

两种方式：

1.\#define 宏常量：`#define 常量名 常量值`

* 通常在文件上方定义，表示一个常量

2.const修饰的变量:`const 数据类型 常量名=常量值`

* 通常在变量定义前加关键字，修饰该变量为常量，不可修改

```C++
#include <iostream>
using namespace std;
#define day 7 
int main()
{
	cout << "一周总共有" << day << "天"<< endl;
	system("pause");
	return 0;
}
#include <iostream>
using namespace std;
#define day 7 //宏常量
int main()
{
	cout << "一周总共有" << day << "天"<< endl;
	const int month = 12;//const修饰变量
	cout << "一年总共有" << month << "个月" << endl;
	system("pause");
	return 0;
}
```

### 1.8 关键字

定义：C++预先保留的单词（标识符）

* 在定义变量或者常量时，不要用关键字

C++关键字如下:

![](C:\Users\10755\Desktop\markdown文件\C++关键字.png)

### 1.9 标识符命名规则

C++规定给标识符（变量、常量）命名时，有一套自己的规则：

* 标识符不能是关键字

* 标识符只能有字母、数字、下划线组成

* 第一个字符必须为字母或者下划线 

* 标识符中区分大小写

建议：给标识符命名时，争取做到见名知意的效果

## 2 数据类型

C++规定在创建一个变量或者常量时，必须要指出相应的数据类型，否则无法给变量分配内存

### 2.1 整型

作用：整型变量表示的是<font color=red>整数类型</font>的数据

数据类型存在意义：给变量分配合适的内存空间

C++中能够表示整型的类型有以下几种方式，区别在于***所占用内存空间不同***：

![](C:\Users\10755\Desktop\markdown文件\整型类型.png)

Short：-32768~32767

如果输入`short num = 32768`，最终显示-32768

### 2.2  sizeof关键字

作用：利用sizeof关键字可以统计数据类型所占内存大小

语法：sizeof(数据类型 / 变量）

Short<int<=long<=long long 

```C++
#include <iostream>
using namespace std;

int main()
{
	short num = 10;
	cout << "short占用内存空间为：" << sizeof(short) <<  endl;//或者 sizeof(num)
	system("pause");
	return 0;
}
```

输出：short占用内存空间为：2

### 2.3 实型（浮点型）

作用：用于表示小数

浮点型变量分为两种：1.单精度float  2.双精度double

两者的区别在于表示的有效数字范围不同:

![](C:\Users\10755\Desktop\markdown文件\图片1.png)

默认情况下，输出一个小数，会显示出6位有效数字 如：3.14159

科学计数法：

float f2 = 3e2 表示3*10^2

float f3 = 3e-2 表示3*0.1^2

```C++
 #include <iostream>
using namespace std;

int main()
{
	float f1 = 3.14f;
	cout << "f1 =" << f1 <<  endl;
	cout << "float占用内存空间为：" << sizeof(float) << endl;
	
    double d1 = 3.14;
	cout << "d1 =" << d1 << endl;
	cout << "double占用内存空间为：" << sizeof(double) << endl;
	
    system("pause");
	return 0;
}
```

输出：

![](C:\Users\10755\Desktop\markdown文件\图片2.png)

### 2.4 字符型

作用：字符型变量用于显示单个字符

语法：`char ch =’a’;`

注意：

1.在显示字符型变量时，用**单引号**将字符括起来，不要用双引号

2.单引号内**只能有一个字符，不可以是字符串**

* C和C++中字符型变量只占用**1个字节**

* 字符型变量并不是把字符本身放到内存中存储，而是将**对应的ASCII编码**放入到存储单元

ASCII码大致由以下两部分组成：

* ASCII非打印控制字符：ASCII表上的数字0-31分配给了控制字符，用于控制像打印机等一些外围设备

* ASCII打印字符：数字32-126分配给了能在键盘上找到的字符，当查看或者打印文档时就会出现

```C++
#include <iostream>
using namespace std;

int main()
{
	//1.字符型变量创建方式
	char ch = 'a';
	char ch2 = 'A';
	cout << ch << endl;
	//2.字符型变量所占内存大小
	cout << "char字符型变量所占内存：" << sizeof(ch) << endl;
	//3.字符型变量常见错误
	//4.字符型变量对应SACII编码  A-65 a-97 b-98
	cout << (int)ch << endl;
	cout << (int)ch2 << endl;
	system("pause");
	return 0;
}
```

输出：

![](C:\Users\10755\Desktop\markdown文件\图片3.png)

### 2.5 转义字符

作用：用于表示一些不能显示出来的ASCII字符

现阶段我们常用的转义字符有：\n  \\   \t

![](C:\Users\10755\Desktop\markdown文件\图片4.png)

水平制表符：作用时整齐输出数据

```C++
#include <iostream>
using namespace std;

int main()
{
	cout << "hello\n" << endl;
	cout << "\\" << endl;
	cout << "hello\tworld!" << endl;
	system("pause");
	return 0;
}
```

输出：

![](C:\Users\10755\Desktop\markdown文件\图片5.png)

\\ 	输出一个\

\t 	hello\tworld：中间3个空格  hello\t总共8个字节，前面hello占用5个

### 2.6 字符串型

作用：用于表示一串字符

两种风格：

1.C风格字符串：`char 变量名[] =”字符串值”`

注意：C风格的字符串要用**双引号**括起来

2.C++风格字符串：`string 变量名 =”字符串值”`

注意：如果不行，则头文件加`#include<string>`

```C++
#include <iostream>
using namespace std;

int main()
{
	char str[] = "hello world";//1.C风格字符串  char 变量名[] =”字符串值”
	cout << str << endl;
	string str1 = "world hello";//2.C++风格字符串：string 变量名 = ”字符串值” 
	cout << str1 << endl;
	system("pause");
	return 0;
}
```

### 2.7 布尔类型bool

作用：布尔数据类型代表真或假的值

bool类型只有两个值：

* true ----真（本质是1）

* false----假（本质是0）

bool类型占**1个字节大小**

```C++
#include <iostream>
using namespace std;

int main()
{
	//1.创建bool数据类型
	bool flag = true;//true代表真
	cout << flag << endl;
	flag = false;
	cout << flag << endl;//false代表假
	//2.查看bool类型所占内存空间
	cout << "bool类型所占内存空间：" << sizeof(bool) << endl;
	system("pause");
	return 0;
}
```

输出：

![](C:\Users\10755\Desktop\markdown文件\图片6.png)

### 2.8 数据的输入

作用：用于从键盘获取数据

关键字：cin

语法：`cin >> 变量`

**bool类型 只要是非0 的值都代表为真**

```C++
#include <iostream>
using namespace std;

int main()
{
	//1.整型输入
	///*int a = 0;
	//cout << "请给整型变量a赋值：" << endl;
	//cin >> a;
	//cout << "整型变量a =" << a << endl;*/
	//2.浮点型输入
	/*float f = 3.14f;
	cout << "请给浮点型变量a赋值：" << endl;
	cin >> f;
	cout << "浮点型变量f =" << f << endl;*/
	//3.字符型输入
	/*char ch = 'a';
	cout << "请给字符型变量ch赋值：" << endl;
	cin >> ch;
	cout << "浮点型变量ch =" << ch << endl;*/
	//4.字符串输入
	/*string str = "hello";
	cout << "请给字符串型变量str赋值：" << endl;
	cin >> str;
	cout << "字符串型变量str =" << str << endl;*/
	//5.bool类型
	bool flag = false;
	cout << "请给布尔类型 flag 赋值" << endl;
	cin >> flag;//bool类型 只要是非0 的值都代表为真
	cout << "布尔类型flag=" << flag <<endl;

	system("pause");
	return 0;
}
```

***快捷键：ctrl+k+c 注释掉***

## 3 运算符

作用：用于执行代码的运算

本章主要讲解以下几类运算符：

![](C:\Users\10755\Desktop\markdown文件\图片7.png)

### 3.1 算术运算符

作用：用于处理四则运算

算术运算符包括以下符号：

![](C:\Users\10755\Desktop\markdown文件\图片8.png)

```C++
#include <iostream>
using namespace std;

int main()
{
	//加减乘除
	int a1 = 10;
	int b1 = 3;
	cout << a1 + b1 << endl;
	cout << a1 - b1 << endl;
	cout << a1 * b1 << endl;
	cout << a1 / b1 << endl;//两个正数相除，结果依然是整数，将小数部分去除
	
	int a2 = 10;
	int b2 = 20;
	cout << a2 / b2 << endl;
	
	/*int a3 = 10;
	int b3 = 0;
	cout << a3 / b3 << endl;*/ //两个数相除，除数不可以为0
	
	double d1 = 0.5;
	double d2 = 0.222;
	cout << d1 / d2 << endl;//两个小数相除,结果也可以是小数
	system("pause");
	return 0;
}
```

输出：

![](C:\Users\10755\Desktop\markdown文件\图片9.png)

***取模运算：两个小数是不可以做取模运算的，只有整型变量可以进行取模运算***

```C++
#include <iostream>
using namespace std;

int main()
{
	//取模运算本质就是取余数
	int a1 = 10;
	int b1 = 3;
	cout << a1 % b1 << endl;
	//两个小数是不可以做取模运算的
	/*double d1 = 3.14;
	double d2 = 1.1;
	cout << d1 % d2 << endl;*/
	
	system("pause");
	return 0;
}
```

***递增递减***

```C++
#include <iostream>
using namespace std;

int main()
{
	//1.前置递增
	int a = 10;
	++a;//让变量+1
	cout << "a= " << a << endl;
	//2.后置递增
	int b = 10;
	b++;//让变量+1
	cout << "b= " << b << endl;
	//3.前置和后置的区别
	//前置递增 先让变量(即a2)+1，后进行表达式运算
	int a2 = 10;
	int b2 = ++a2 * 10;
	cout << "a2 =" << a2 << endl;
	cout << "b2 =" << b2 << endl;

	//后置递增  先进行表达式运算，后让变量(即a3)+1
	int a3 = 10;
	int b3 = a3++ * 10;
	cout << "a3 =" << a3 << endl;
	cout << "b3 =" << b3 << endl;
	
	system("pause");
	return 0;
}
```

输出：

![](C:\Users\10755\Desktop\markdown文件\图片10.png)

### 3.2 赋值运算符

作用：用于将表达式的值赋给变量

赋值运算符包括以下几个符号：

![](C:\Users\10755\Desktop\markdown文件\图片11.png)

### 3.3 比较运算符

作用：用于表达式的比较，并返回一个真值或假值

比较运算符有以下符号：

![](C:\Users\10755\Desktop\markdown文件\图片12.png)

```C++
#include <iostream>
using namespace std;

int main()
{
	int a = 10;
	int b = 20;
	cout << (a == b )<< endl;//0
	cout << (a != b) << endl;//1
	cout << (a > b) << endl;//0
	cout << (a < b) << endl;//1
	cout << (a >= b) << endl;//0
	cout << (a <= b) << endl;//1
	system("pause");
	return 0;
}
```

### 3.4 逻辑运算符

作用：用于根据表达式的值返回真值或假值

有以下符号：

![](C:\Users\10755\Desktop\markdown文件\图片13.png)

```C++
#include <iostream>
using namespace std;

int main()
{
	int a = 10;
	//非
	cout << !a  << endl;//0       在C++中，除了0都是真
	cout << !!a << endl;//1
	//与
	int b = 10;
	int c = 10;
	cout << (b && c) << endl;//1        同真为真，其余为假
	//或
	int d = 0;
	int e = 0;
	cout << (d || e) << endl;//0          同假为假，其余为真
	system("pause");
	return 0;
}
```

## 4 程序流程结构

C/C++支持最基本的三种程序运行结构：顺序结构、选择结构、循环结构

* 顺序结构：程序按顺序执行，不发生跳转

* 选择结构：根据条件是否满足，有选择的执行相应功能

* 循环结构：根据条件是否满足，循环多次执行某段代码

### 4.1 选择结构

#### 4.1.1 if 语句

作用：执行满足条件的语句

If 语句的三种形式：

* 单行格式if语句

* 多行格式if语句

* 多条件的if语句

1.单行格式if语句： `if（条件）{条件满足执行的语句}`

![](C:\Users\10755\Desktop\markdown文件\图片14.png)

<font color=red>注意事项：if条件后面不要加分号</font>

```C++
#include <iostream>
using namespace std;

int main()
{
	//选择结构 单行if语句
	//用户输入分数，>600考上一本大学
	//1.用户输入分数
	int score = 0;
	cout << "请输入一个分数：" << endl;
	cin >> score;
	//2.打印用户输入的分数
	cout << "您输入的分数为：" << score << endl;
	//3.判断分数是否大于600，大于则输出
	if (score > 600) 
	{
		cout << "恭喜您考上了一本大学" << endl;
	}
	system("pause");
	return 0;
}
```

2.多行格式if语句：`if(条件）{条件满足执行的语句}else{条件不满足执行的语句}；`

![](C:\Users\10755\Desktop\markdown文件\图片15.png)

```C++
#include <iostream>
using namespace std;

int main()
{
	//选择结构 多行if语句
	//用户输入分数，>600考上一本大学，否则打印未考上一本大学
	//1.用户输入分数
	int score = 0;
	cout << "请输入一个分数：" << endl;
	cin >> score;
	//2.打印用户输入的分数
	cout << "您输入的分数为：" << score << endl;
	//3.判断分数是否大于600，大于则输出
	if (score > 600)
	{
		cout << "恭喜您考上了一本大学" << endl;
	}
	else 
	{
		cout << "未考上一本大学" << endl;

	}
	system("pause");
	return 0;
}
```

3.多条件的if语句：`If（条件1）{条件1 满足执行的语句}else if（条件2）{条件2满足执行的语句}......else {都不满足执行的语句}`

![](C:\Users\10755\Desktop\markdown文件\图片16.png)

```C++
#include <iostream>
using namespace std;

int main()
{
	//选择结构 多行if语句
	//用户输入分数，>600考上一本大学
	//大于500，二本大学
	//大于400，三本大学
	//小于等于400，未考上本科
	//1.用户输入分数
	int score = 0;
	cout << "请输入一个分数：" << endl;
	cin >> score;
	//2.打印用户输入的分数
	cout << "您输入的分数为：" << score << endl;
	//3.判断分数
	if (score > 600)
	{
		cout << "恭喜您考上了一本大学" << endl;
	}
	else if(score>500)
	{
		cout << "考上二本大学" << endl;
	}
	else if (score > 400)
	{
		cout << "考上三本大学" << endl;
	}
	else 
	{
		cout << "未考上本科" << endl;
	}

	system("pause");
	return 0;
}
```

<font color=red>**嵌套if语句：在if语句中，可以嵌套使用if语句，达到更精确的条件判断**</font>

案例需求：

1.提示用户输入一个高考分数，根据分数做出判断

2.分数>600，一本； >500 ，二本； >400 ，三本；其余未考上本科

3.在一本分数中，大于700， 北大 ；大于650 ，清华； 大于600， 人大

```C++
#include <iostream>
using namespace std;

int main()
{
	//选择结构 多行if语句
	//用户输入分数，>600考上一本大学
		//大于700 北大   大于650 清华    大于600 人大
	//大于500，二本大学
	//大于400，三本大学
	//小于等于400，未考上本科
	//1.用户输入分数
	int score = 0;
	cout << "请输入一个分数：" << endl;
	cin >> score;
	//2.打印用户输入的分数
	cout << "您输入的分数为：" << score << endl;
	//3.判断分数
	if (score > 600)
	{
		cout << "恭喜您考上了一本大学" << endl;
		if (score > 700)
		{
			cout << "恭喜你考上北大" << endl;
		}
		else if (score > 650)
		{
			cout << "恭喜你考上清华" << endl;
		}
		else
		{
			cout << "恭喜你考上人大" << endl;
		}
	}
		
	else if(score>500)
	{
		cout << "考上二本大学" << endl;
	}
	else if (score > 400)
	{
		cout << "考上三本大学" << endl;
	}
	else 
	{
		cout << "未考上本科" << endl;
	}

	system("pause");
	return 0;
}
```

案例：三只小猪称体重

先判断A与B谁重：

* A重		让A与C比较：
  * A重，结果是A最重
  * C重，结果是C最重

* B重		让A与C比较：
  * B重，结果是B最重
  * C重，结果是C最重

```C++
#include <iostream>
using namespace std;

int main()
{
	//1.创建三只小猪的体重变量
	int num1 = 0;
	int num2 = 0;
	int num3 = 0;
	//2.让用户输入三只小猪的重量
	cout << "请输入小猪A的重量：" << endl;
	cin >> num1;
	cout << "请输入小猪B的重量：" << endl;
	cin >> num2;
	cout << "请输入小猪C的重量：" << endl;
	cin >> num3;
	cout << "小猪A的重量：" << num1 << endl;
	cout << "小猪B的重量：" << num2 << endl;
	cout << "小猪B的重量：" << num3 << endl;
	//3.判断哪只最重
	//先判断A与B
	if (num1 > num2) //A重
	{
		if (num1 > num3) 
		{
			cout << "最重的是A" << endl;//A重
		}
		else 
		{
			cout << "最重的是C" << endl;//C重
		}
	}
	else
	{
		if (num2 > num3)//B重
		{
			cout << "最重的是B" << endl;//B重
		}
		else
		{
			cout << "最重的是C" << endl;//C重
		}

	}
	system("pause");
	return 0;
}
```

#### 4.1.2 三目运算符

作用：通过三目运算符实现简单的判断

语法：`表达式1？表达式2：表达式3`

**<font color=red>在C++中，三目运算符返回的是变量，可以继续赋值</font>**

解释：

如果表达式1的值为真，执行表达式2，并返回表达式2的结果

如果表达式1的值为假，执行表达式3，并返回表达式3的结果

```C++
#include<iostream>
using namespace std;

int main()
{
    //三目运算符
    //创建三个变量a b c 
    //将a与b比较，把变量大的赋值给变量c
    int a=10;
    int b=20;
    int c=0;
    c=(a>b?a:b);
    cout<<"c = "<<c<<endl;
    //在C++中，三目运算符返回的是变量，可以继续赋值
    (a>b?a:b)=100;
    cout<<"a = "<<a<<endl;
    cout<<"b = "<<b<<endl;
    system("pause");
    return 0;
}
```

#### 4.1.3 switch语句

作用：执行多条件分支语句

语法：

```C++
switch(表达式)
{
    case 结果1:执行语句;break;
    case 结果2:执行语句;break;
    ……
        
    default:执行语句;break;
}
```

**If语句和switch区别：**

Switch缺点：<font color=red>判断时只能是整型或字符型，不可以是区间</font>；如果没有break，程序会

一直向下执行。 优点：结构清晰，执行效率高。

```C++
#include <iostream>
using namespace std;

int main()
{
	//switch语句
	//给电影打分（10-9分，经典；8-7分，非常好；6-5分，一般；5分以下，烂片）
	//1.提示用户给电影评分
	cout << "请给电影打分：" << endl;
	int score = 0;
	//2.用户打分
	cin >> score;
	cout << "您打的分数是：" << score<<endl;
	//3.根据用户分数提示最后的结果
	switch (score) 
	{
	case 10:
		cout << "经典" << endl; break;
	case 9:
		cout << "经典" << endl; break;
	case 8:
		cout << "非常好" << endl; break;
	case 7:
		cout << "非常好" << endl; break;
	case 6:
		cout << "一般" << endl; break;
	case 5:
		cout << "一般" << endl; break;
	default:
		cout << "烂片" << endl; break;
	}
	system("pause");
	return 0;
}
```

### 4.2 循环语句

#### 4.2.1 while循环语句

作用：满足循环条件，执行循环语句

语法：`while(循环条件）{循环语句}`

解释：只要循环条件的结果为真，就执行循环语句

注意：在写循环一定要避免死循环的出现

![](C:\Users\10755\Desktop\markdown文件\图片17.png)

```C++
#include <iostream>
using namespace std;

int main()
{
    //while循环
    //打印0-9这10个数字
    int num =0;
    while(num<10)
    {
        cout<<num<<endl;
        num++;
	}
    system("pause");
    return 0;
}
```

案例：while循环 猜数字

描述：系统随机生成一个1-100之间的数字，玩家猜测，如果猜错，提示玩家数字过大或过小，如果猜对，恭喜玩家胜利，退出游戏。

```C++
#include <iostream>
using namespace std;
//time系统时间头文件包含
#include <ctime>

int main()
{
	//添加随机数种子 作用是利用当前系统时间生成随机数，防止每次随机数都一样
	srand ((unsigned int)time(NULL));

	//1.系统生成随机数
	int num=rand() % 100+1;//rand()%100+1生成0+1到99+1的随机数
	cout << num << endl;
	//2.玩家进行猜测
	int val = 0;
	cout << "请玩家输入数字：" << endl;
	//3.判断玩家的猜测
	while (1) 
	{
		cin >> val;
		if (val < num) 
		{
			cout << "猜小了" << endl;
		}
		else if(val > num)
		{
			cout << "猜大了" << endl;
		}
		else 
		{
			cout << "恭喜您猜对了！" << endl;
			break;//break在循环中，可以利用该关键字来退出当前循环
		}
	}
	system("pause");
	return 0;
}
```

<font color=green>**命令行积累:**</font>

time系统时间头文件包含：`#include <ctime>`

添加随机数种子 作用是利用当前系统时间生成随机数，防止每次随机数都一样:`srand ((unsigned int)time(NULL));`

系统生成随机数：`int num=rand() % 100+1;//rand()%100+1生成0+1到99+1的随机数`

`while (1) `:1 代表为真

#### 4.2.2 do......while循环语句

作用：满足循环条件，执行循环语句

语法：`do{循环语句}while（循环条件);`

注意：与while的区别在于**do.....while会先执行一次循环语句**，再判断循环条件

![](C:\Users\10755\Desktop\markdown文件\图片18.png)

与while比较：

![](C:\Users\10755\Desktop\markdown文件\图片17.png)

<font color=green>***案例：水仙花数***</font>

描述：水仙花数是指一个三位数，每个位置上的数的三次方相加和等于它本身

如：1^3+5^3+3^3=153

请用do……while语句，求出所有的水仙花数

1.将所有的三位数进行输出（100-999）

2.在所有的三位数中找到水仙花数

水仙花数    153

获得个位	153%10=3

获得十位	153/10%10=5  （整数相除结果为整，即153/10得15）

获得百位	153/100=1

判断：个位^3+十位^3+百位^3=本身

```C++
#include <iostream>
using namespace std;

int main()
{
	//1.先打印所有的三位数
	int num = 100;
	do
	{
		//2.从所有三位数中找到水仙花数
		int a = 0;//创建变量代表个位
		int b = 0;//十位
		int c = 0;//百位
		a = num % 10;//获取数字的个位
		b = num / 10 % 10;//获取数字的十位
		c = num / 100;//获取数字的百位
		if (num==a*a*a+b*b*b+c*c*c)//是水仙花数才打印
		{
			cout << num << endl;
		}
		num++;
	} while (num<1000);
	system("pause");
	return 0;
}
```

**整数相除结果为整，即153/10得15**

#### 4.2.3 for循环语句

作用：满足循环条件，执行循环语句

语法：`for(起始表达式；条件表达式；末尾循环体){循环语句；}`

判断顺序：

1.起始表达式，只执行一次

2.条件表达式

3.如果2成立，执行循环语句，接着末尾循环体；直到2不成立，退出循环

```C++
#include <iostream>
using namespace std;

int main()
{
	for (int i = 0; i < 10; i++) 
	{
		cout << i << endl;
	}
	system("pause");
	return 0;
}
也可以写为：
#include <iostream>
using namespace std;

int main()
{
	int i = 0;
	for (; ; i++) 
	{
		if(i>=10)
		{
			break;
		}
		cout << i << endl;
		i++;
	}
	system("pause");
	return 0;
}
```

案例：敲桌子

描述：1-100，如果数字个位、数字十位、或者是7的倍数，我们打印敲桌子，其余数字这届打印输出

1.先输出1-100这些数字

2.从这100个数字中找到特殊数字，改为“敲桌子”

特殊数字

7的倍数		num % 7=0

个位有7		num % 10=7

十位有7		num / 10 =7

```C++
#include <iostream>
using namespace std;

int main()
{
	//敲桌子
	//1.先输出1-100数字
	for (int i=1;i<=100;i++)
	{
		//2.从100个数字中找到特殊数字，打印“敲桌子”
		if(i%7==0||i%10==7||i/10==7)
		{
			cout << "敲桌子" << endl;//特殊数字，打印“敲桌子”
		}
		else
		{
			cout << i << endl;//不是特殊数字，打印数字
		}
		cout << i << endl;
	}
	system("pause");
	return 0;
}
```

#### 4.2.4 嵌套循环

作用：在循环中再嵌套一层循环，解决一些实际问题

案例：打印10*10 星图

```C++
#include <iostream>
using namespace std;
int main()
{
	//外层执行一次，内层执行一周
	//外层循环
	for (int i = 0; i < 10; i++)
	{
		//内层循环
		for (int j = 0; j < 10; j++)//打印一行星图
		{
			cout << "* ";
		}
		cout << endl;
	}
	system("pause");
	return 0;
}
```

输出：

![](C:\Users\10755\Desktop\markdown文件\图片19.png)

案例：乘法口诀表

相当于列数*行数，列数<=当前行数

![](C:\Users\10755\Desktop\markdown文件\图片20.png)

```C++
#include <iostream>
using namespace std;
int main()
{
	//打印行数
	for (int i =1;i<=9;i++)
	{
		//cout << i << endl;不需要打印行数
		for(int j=1;j<=i;j++)//列数<=行数
		{
			cout << j << " * " << i <<" = "<<j*i<<"  ";
		}
		cout << endl;
	}
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片21.png)

### 4.3 跳转语句

#### 4.3.1 break语句

作用：用于跳出选择结构或者循环结构

break使用的时机：

* 出现在switch条件语句中，作用是终止case并跳出switch

* 出现在循环语句中，作用是跳出当前的循环语句

* 出现在嵌套循环中，跳出最近的内层循环语句 

1.出现在switch语句中

```C++
cout<<"请选择副本难度："<<endl;
cout<<"1.普通"<<endl;
cout<<"2.中等"<<endl;
cout<<"3.困难"<<endl;
int select=0;
cin>>select;
switch(select)
{
    case 1:
        cout<<"您选择的是普通难度"<<endl;break;
    case 2:
        cout<<"您选择的是中等难度"<<endl;break;
    case 3:
        cout<<"您选择的是困难难度"<<endl;break;
    default：
        break;
}
```

2.出现在循环语句中

```C++
#include <iostream>
using namespace std;

int main()
{
	for(int i =0;i<10;i++)
	{
		if(i == 5)//打印到5退出循环
		{
			break;
		}
		cout << i << endl;
	}
	system("pause");
	return 0;
}
```

3.出现在嵌套循环

```C++
#include <iostream>
using namespace std;

int main()
{
    for (int i =0;i<10;i++)
    {
        for(int j=0;j<10;j++)
        {
            if(j==5)
            {
                break;//退出内层循环
            }
            cout<<"* ";
        }
        cout<<endl;
    }
    system("pause");
    return 0;
}    
```

输出：

![](C:\Users\10755\Desktop\markdown文件\图片22.png)

#### 4.3.2 continue语句

作用：在循环语句中，跳过本次循环中余下尚未执行的语句，继续执行下一次循环

注意：continue并不会使整个循环终止，而break会跳出循环

```C++
#include <iostream>
using namespace std;

int main()
{
    for(int i=0;i<101;i++)
    {
        if(i%2==0)//输出奇数
        {
            continue;
        }
        cout<<i<<endl;
    }
    system("pause");
    return 0;
}
```

案例中if和cout是一次循环，有continue，则跳过cout语句，执行下一次循环

#### 4.3.3 goto语句

作用：可以无条件跳转语句

语法：`goto标记;`

解释：如果标记的名称存在，执行到goto语句时，会跳转到标记的位置

注意：在程序中不建议使用goto语句，以免造成程序流程混乱

```C++
#include <iostream>
using namespace std;

int main()
{
    cout<<"1.xxxxx"<<endl;
    cout<<"2.xxxxx"<<endl;
    goto FLAG;
    cout<<"3.xxxxx"<<endl;
    cout<<"4.xxxxx"<<endl;
    FLAG:
    cout<<"5.xxxxx"<<endl;
    system("pause");
    return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片23.png)

## 5 数组

### 5.1 概述

数组 ：就是一个集合，里面存放了相同类型的数据元素

特点1：数组中每个元素都是相同的数据类型

特点2：数组是由连续的内存位置组成的

 ### 5.2 一维数组

#### 5.2.1 一维数组定义方式

一维数组定义的三种方式：

1.`数据类型 数组名[数组长度];`

2.`数据类型 数组名[数组长度]={值1，值2……};`

3.`数据类型 数组名[]={值1，值2……};`

```C++
//1.数据类型 数组名[数组长度];
int arr[5];
//给数组中的元素赋值
arr[0]=10;//数组元素的下标从0开始索引
arr[1]=20;
arr[2]=30;
arr[3]=40;
arr[4]=50;
cout<<arr[2]<<endl;

//2.数据类型 数组名[数组长度]={值1，值2……};
int arr2[5]={1,2,3,4,5};
cout<<arr2[2]<<ensl;
//利用循环输出数组中的元素
for (int i =0;i<5;i++)
{
    cout<<arr2[i]<<endl;
}

//3.数据类型 数组名[]={值1，值2……};
int arr3[]={90,80,70,60,50,40,30,20,10};
for (int i =0;i<9;i++)
{
    cout<<arr3[i]<<endl;
}
```

如果`int arr2[5] = { 1,2,3};`则输出1 2 3 0 0

即如果在初始化数据时，没有全部填写完，会用0来填补剩余的数据

总结：

* 数组名的命名规范与变量名命名规范一致，不要和变量重名

* 数组中下标从0 开始索引

#### 5.2.2 一维数组数组名

一维数组名称的用途：

1.可以统计整个数组在内存中的长度

2.可以获得数组在内存中的首地址

<font color=red>**注意：数组名是常量，不可以进行赋值操作**</font>

```C++
//一维数组名用途
//1.可以统计整个数组在内存中的长度
int arr[10]={1,2,3,4,5,6,7,8,9,10};
cout<<"整个数组占用的内存空间："<<sizeof(arr)<<endl;
cout<<"每个元素占用的内存空间："<<sizeof(arr[1])<<endl;
cout<<"数组中元素的个数为："<<sizeof(arr)/sizeof(arr[0])<<endl;
//2.可以获得数组在内存中的首地址
cout<<"数组的首地址为："<<arr<<endl;
cout<<"数组的首地址为："<<(int)arr<<endl;

cout<<"数组中第一个元素地址为："<<&arr[0]<<endl;//& 取址符
cout<<"数组中第一个元素地址为："<<(int)&arr[0]<<endl;
cout<<"数组中第二个元素地址为："<<(int)&arr[1]<<endl;//和第一个元素相差4个字节

```

![](C:\Users\10755\Desktop\markdown文件\图片24.png)

案例：五只小猪称体重

描述：在一个数组中记录五只小猪的体重

如:`int arr[5]={300,350,200,365,250};`

找出并打印最重的小猪体重

```C++
//1.创建五只小猪体重的数组
int arr[5]={300,350,200,365,250};
//2.从数组中找到最大值
int max=0;
for (int i=0;i<5;i++)
{
    if (arr[i]>max)//如果访问的数组中的元素比我认定的最大值大，则更新最大值
    {
        max=arr[i];
    }
}
//3.打印最大值
cout<<"最重的小猪体重是："<<max<<endl;
```

案例：数组元素逆置

```C++
#include <iostream>
using namespace std;

int main()
{
	//1、创建数组
	int arr[5] = { 1,2,3,4,5 };
	cout << "数组逆置前：" << endl;
	for(int i=0;i<5;i++)
	{
		cout << arr[i]<<" ";
	}
	cout << endl;
	/*2、实现逆置 2.1记录起始下标位置
			     2.2结束下标位置
				 2.3起始与结束的元素呼唤
			     2.4起始位置++   结束位置--
				 2.5循环执行，直到起始位置>=结束位置*/
	int start = 0;//起始下标
	int end = sizeof(arr) / sizeof(arr[0]) - 1;//结束下标
	while(start<end)
	{
		//实现元素互换
		int temp = arr[start];
		arr[start] = arr[end];
		arr[end] = temp;
		//下标更新
		start++;
		end--;
	}
	//3、打印逆置后的数组
	cout << "数组元素逆置后：" << endl;
	for (int i = 0; i < 5; i++)
	{
		cout << arr[i] << " ";
	}
	cout << endl;
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片25.png)

#### 5.2.3 冒泡排序

作用：最常用的排序算法，对数组内元素进行排序

1.比较相邻的元素。如果第一个比第二个大，就交换他们两个。

2.对每一对相邻元素做同样的工作，执行完毕后，找到第一个最大值。

3.重复以上的步骤，每次比较次数减1，直到不需要比较为止

![](C:\Users\10755\Desktop\markdown文件\图片26.png)

排序总轮数=元素个数-1

每轮对比次数=元素个数-1-排序轮数

```C++
#include <iostream>
using namespace std;
int main()
{
	//利用冒泡排序实现升序序列
	int arr[9] = { 4,2,8,0,5,7,1,3,9 };
	cout << "排序前：" << endl;
	for(int i =0;i<9;i++)
	{
		cout << arr[i] << " ";
	}
	cout << endl;
	//开始冒泡排序
	//总共排序轮数为元素个数-1
	for (int i = 0;i<9-1;i++)
	{
		//内层循环对比   次数=元素个数-当前轮数-1
		for(int j =0;j<9-i-1;j++)
		{
			//如果第一个数字比第二个数字大，交换两个数字
			if (arr[j] > arr[j + 1]) 
			{
				int temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
			}
		}
	}
	cout << "排序后：" << endl;
	for (int i = 0; i < 9; i++)
	{
		cout << arr[i] << " ";
	}
	cout << endl;
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片27.png)

### 5.3 二位数组

二位数组就是在一维数组上，多加一个维度

![](C:\Users\10755\Desktop\markdown文件\图片28.png)

#### 5.3.1 二维数组定义的四种方式：

1.`数据类型 数组名[行数][列数];`

2.`数据类型 数组名[行数][列数]={ {数据1，数据2}，{数据3，数据4} };`

3.`数据类型 数组名[行数][列数]={数据1，数据2，数据3，数据4};`

4.`数据类型 数组名[   ][列数]={数据1，数据2，数据3，数据4};`

建议：以上四种定义方式，<font color=green>**利用第二种更加直观，提高代码的可读性**</font>

```C++
#include <iostream>
using namespace std;

int main()
{
	//二维数组定义的四种方式：
	//1.数据类型 数组名[行数][列数]；
	int arr[2][3];
	arr[0][0] = 1;
	arr[0][1] = 2;
	arr[0][2] = 3;
	arr[1][0] = 4;
	arr[1][1] = 5;
	arr[1][2] = 6;
	/*cout << arr[0][0] << endl;*/
	//外层循环打印行数，内层循环打印列数
	for(int i =0;i<2;i++)
	{
		for (int j = 0; j < 3; j++)
		{
			cout << arr[i][j] << endl;
		}
	}
	//2.数据类型 数组名[行数][列数] = { {数据1，数据2}，{数据3，数据4} }；
	int arr2[2][3] =
	{
		{1,2,3},
		{4,5,6}
	};
	for (int i = 0; i < 2; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			cout << arr2[i][j] << " ";
		}
		cout << endl;
	}
	//3.数据类型 数组名[行数][列数] = { 数据1，数据2，数据3，数据4 }；
	int arr3[2][3] ={1,2,3,4,5,6};
	for (int i = 0; i < 2; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			cout << arr3[i][j];
		}
		cout << endl;
	}
	//4.数据类型 数组名[][列数] = { 数据1，数据2，数据3，数据4 }；
	int arr4[ ][3] = { 1,2,3,4,5,6 };
	for (int i = 0; i < 2; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			cout << arr4[i][j]<<"   ";
		}
		cout << endl;
	}
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片29.png)

#### 5.3.2 二维数组数组名

* 查看二维数组所占内存空间  利用`sizeof()`

* 获取二维数组首地址

```C++
//二维数组数组名
//1.查看二维数组所占内存空间
int arr[2][3]=
{
    {1,2,3},
    {4,5,6}
};
cout<<"二维数组占用的内存空间："<<sizeof(arr)<<endl;
cout<<"二维数组第一行占用的内存空间："<<sizeof(arr[0])<<endl;
cout<<"二维数组第一个元素占用的内存空间："<<sizeof(arr[0][0])<<endl;

cout<<"二维数组行数："<<sizeof(arr)/sizeof(arr[0])<<endl;
cout<<"二维数组列数："<<sizeof(arr[0])/sizeof(arr[0][0])<<endl;
//2.获取二维数组首地址
cout<<"二维数组的首地址为："<<arr<<endl;
cout<<"二维数组的首地址为："<<(int)arr<<endl;

cout<<"二维数组第一行首地址为："<<arr[0]<<endl;
cout<<"二维数组第二行首地址为："<<(int)arr[1]<<endl;
cout<<"二维数组第一个元素首地址为："<<(int)&arr[0][0]<<endl;
```

![](C:\Users\10755\Desktop\markdown文件\图片30.png)

#### 5.3.3 二维数组应用案例

考试成绩统计

描述：有三名同学的成绩，请分别输出三名同学的总成绩

![](C:\Users\10755\Desktop\markdown文件\图片31.png)

```C++
#include <iostream>
using namespace std;
#include<string>

int main()
{
	//二维数组案例-考试成绩统计
	//1.创建二维数组，3行3列
	int scores[3][3] =
	{
		{100,100,100},
		{90,50,100},
		{60,70,80}
	};
	string names[3] = { "张三","李四","王五" };
	//2.统计每个人的总和分数
	for (int i = 0; i < 3; i++)
	{
		int sum = 0;
		for (int j = 0; j < 3; j++)
		{
			sum += scores[i][j];
		}
		cout << names[i] << "人的总分是：" << sum << endl;
	}
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片32.png)

## 6 函数

### 6.1 概述

作用：将一段经常使用的代码封装起来，减少重复代码

一个较大的程序，一般分为若干个程序块，每个模块实现特定的功能

### 6.2 函数的定义

函数的定义一般有五个步骤：

1.返回值类型：一个函数可以返回一个值

2.函数名：给函数起名称

3.参数列表：使用该函数时，传入的数据

4.函数体语句：花括号内的代码，函数内需要执行的语句

5.return表达式：和返回值类型挂钩，函数执行完后，返回相应的数据

语法：

```C++
返回值类型 函数名 （参数列表）
{
    函数体语句
        
    return表达式
        
}
```

```C++
int add(int num1,int num2)
{
    int sum=num1+num2;
    return sum;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片33.png)

### 6.3 函数的调用

功能：使用定义好的函数

语法：`函数名（参数）`

```C++
#include <iostream>
using namespace std;

int add(int num1,int num2)
//函数定义的时候，num1和num2并没有真实参数，只是形式的上参数，简称形参
{
    int sum=num1+num2;
    return sum;
}
int main()
{
    int a=10;
    int b=20;
    int c=add(a,b);//函数调用语法：函数名称 （参数），a和b是实参
    //当调用函数时，实参的值会传递给形参
    cout<<"c = "<<c<<endl;
    system("pause");
    return 0;
}
```

### 6.4 值传递

* 就是函数调用时实参将数值传给形参

* 值传递时，<font color=green>如果形参发生改变，不会影响实参</font>

 ![](C:\Users\10755\Desktop\markdown文件\图片34.png)

```C++
#include <iostream>
using namespace std;

//值传递
//定义函数实现两个数进行交换
//如果函数不需要返回值，声明的时候可以写void
void swap(int num1,int num2)
{
    cout<<"交换前："<<endl;
    cout<<"num1 = "<<num1<<endl;
    cout<<"num2 = "<<num2<<endl;
    
    int temp=num1;
    num1=num2;
    num2=temp;
    
    cout<<"交换后："<<endl;
    cout<<"num1 = "<<num1<<endl;
    cout<<"num2 = "<<num2<<endl; 
}
int main()
{
    int a=10;
    int b=20;
    swap(a,b);
    system("pause");
    return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片35.png)

**如果函数不需要返回值，声明的时候可以写void**

### 6.5 函数的常见样式

常见的函数样式有四种：

无参无返；有参无返；无参有返；有参有返

```C++
#include <iostream>
using namespace std;

//常见的函数样式有四种：
//1.无参无返 
void test01()
{
	cout << "this is test01" << endl;
}
//2.有参无返 
void test02(int a)
{
	cout << "this is test02 a = " <<a<< endl;
}
//3.无参有返 
int test03()
{
	cout << "this is test03" << endl;
	return 1000;
}
//4.有参有返
int test04(int a)
{
	cout << "this is test04" << endl;
	return a;
}
int main()
{
	//无参无返函数调用
	test01();
	//有参无返函数调用
	test02(100);
	//无参有返函数调用
	int num1=test03();
	cout << "num1 = " << num1 << endl;
	//有参有返函数调用
	int num2 = test04(200);
	cout << "num2 = " << num2 << endl;
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片36.png)

### 6.6 函数的声明

作用：告诉编译器函数名称以及如何调用函数，函数的实际主体可以单独定义

* 函数的声明可以多次，但是函数的定义只能有一次

```C++
#include <iostream>
using namespace std;
//函数的声明
//比较函数，实现两个整型数字比较，返回较大值

//提前告诉编译器函数的存在，可以利用函数的声明
//函数的声明
//函数的声明可以多次，但是函数的定义只能有一次
int max(int a, int b);

int main()
{
	int a = 10;
	int b = 20;
	cout << max(a, b) << endl;
	system("pause");
	return 0;
}
//定义
int max(int a, int b)
{
	return a > b ? a : b;
}
```

### 6.7 函数的分文件编写

作用：让代码结构更加清晰

4个步骤：

1.创建后缀名为.h的头文件

2.创建后缀名为.cpp的源文件

3.在头文件中写函数的声明

4.在源文件中写函数的定义

在源文件中包含头文件 `#include"swap.h"`

```C++
#include <iostream>
using namespace std;
#include "swap.h"

int main()
{
    int a =10;
    int b =20;
    swap(a,b);
    system("pause");
    return 0;
}
```

```C++
//swap.cpp文件
#include "swap.h"

//函数的定义
void swap(int a,int b)
{
    int temp=a;
    a=b;
    b=temp;
    cout<<"a = "<<a<<endl;
    cout<<"b = "<<b<<endl;
}
```

```C++
//swap.h文件
#include <iostream>
using namespace std;

//实现两个数字交换的函数声明
void swap(int a,int b);
```

## 7 指针

### 7.1 指针的基本概念

<font color=green>**指针的作用：可以通过指针间接访问内存**</font>

* 内存编号是从0开始记录的，一般用**十六进制**数字表示

* 可以利用指针变量**保存地址**

### 7.2 指针变量的定义和使用

指针变量定义语法：`数据类型 * 变量名;`

可以通过解引用的方式来找到指针指向的内存，语法：指针前加*代表解引用

```C++
#include <iostream>
using namespace std;

int main()
{
	//1.定义指针
	int a = 10;
	//指针定义的语法：数据类型 * 指针变量名；
	int * p;
	//让指针记录变量a的地址
	p = &a;
	cout << "a的地址为：" << &a << endl;
	cout << "指针p为：" << p << endl;
	//2.使用指针
	//可以通过解引用的方式来找到指针指向的内存,语法：指针前加*代表解引用
	*p=1000;
	cout << "a = " << a << endl;
	cout << "*p = " << *p << endl;
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片37.png)

### 7.3 指针所占内存空间

* 在32位操作系统下，指针是占4个字节空间大小，不管是什么数据类型（VS中x86代表32位）

* 在64位操作系统下，指针是占8个字节空间大小，不管是什么数据类型

```C++
#include <iostream>
using namespace std;

int main()
{
	//定义指针
	int a = 10;
	int * p;
	p = &a;
	//可用int * p=&a;代替上面两式
	cout << "sizeof(int *) =  " << sizeof(int *) << endl;
	cout << "sizeof(int *) =  " << sizeof(p) << endl;
	cout << "sizeof(int *) =  " << sizeof(float*) << endl;
	cout << "sizeof(int *) =  " << sizeof(double*) << endl;
	cout << "sizeof(int *) =  " << sizeof(char*) << endl;
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片38.png)

### 7.4 空指针和野指针

空指针：指针变量指向内存中编号为0的空间

用途：**初始化指针变量**

注意：**空指针指向的内存是不可以访问的**

```C++
int main()
{
    //空指针
    //1.空指针用于给指针变量进行初始化
    int * p=NULL;
    //2.空指针是不可以进行访问的
    //0-255之间的内存编号是系统占用的，因此不可以访问
    //如*p=100;是错误的
    //cout<<*p<<endl;也是错误的
    system("pause");
    return 0;
}
```



野指针：指针变量指向非法的内存空间

```C++
int main()
{
    //野指针
    //在程序中，尽量避免出现野指针
    int * p =(int*)0x1100;
    cout<<*p<<endl;
    system("pause");
    return 0;
}
```

**空指针和野指针都不是我们申请的空间，因此不要访问**

### 7.5 const修饰指针

有三种情况：

1.const修饰指针-------常量指针

2.const修饰常量-------指针常量

3.const既修饰指针，又修饰常量

![](C:\Users\10755\Desktop\markdown文件\图片39.png)

![](C:\Users\10755\Desktop\markdown文件\图片40.png)

![](C:\Users\10755\Desktop\markdown文件\图片41.png)

const表示常量 

\* 表示指针

<font color=green>**技巧**</font>：看const右侧紧跟着的是指针还是常量，是指针就是常量指针，是常量就是指针常量

```C++
int main()
{
    //1.const修饰指针----常量指针
    int a =10;
    int b =10;
    const int * p=&a;//指向可以改，指针指向的值不可以改 *p=20;是错误的
    p=&b;
    //2.const修饰常量----指针常量
    int * const p2=&a;//指向不可以改，指针指向的值可以改 p2=&b;错误
    *p2=100;
    //3.const既修饰指针，又修饰常量
    const int * const p3=&a;//指向、指针指向的值都不可以改  *p3=100;p3=&b;都是错误的
    system("pause");
    return 0;
}
```

### 7.6 指针和数组

作用：利用指针访问数组中元素

p++表示**让指针向后偏移4个字节**

```C++
#include <iostream>
using namespace std;

int main()
{
	//指针和数组
	//利用指针访问数组中元素
	int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };
	cout << "第一个元素为：" << arr[0] << endl;
	int* p = arr;//arr就是数组的首地址
	cout << "利用指针访问第一个元素：" << *p << endl;
	p++;//让指针向后偏移4个字节
	cout << "利用指针访问第二个元素：" << *p << endl;
	cout << "利用指针遍历数组：" << endl;
	int* p2 = arr;
	for(int i =0;i<10;i++)
	{
		cout << *p2 << endl;
		p2++;
	}
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片42.png)

### 7.7 指针和函数

作用：利用指针做函数参数，可以修改实参的值

可以通过解引用的方式来找到指针指向的内存，<font color=red>**语法：指针前加*代表解引用**</font>

![](C:\Users\10755\Desktop\markdown文件\图片43.png)

```C++
#include <iostream>
using namespace std;
//实现两个数字进行交换
void swap01(int a,int b)
{
	int temp = a;
	a = b;
	b = temp;
	cout << "swap01 a = " << a << endl;
	cout << "swap01 b = " << b << endl;
}
void swap02(int *p1,int *p2)
{
	int temp = *p1;
	*p1 = *p2;
	*p2 = temp;
	cout << "swap02 *p1 = " << *p1 << endl;
	cout << "swap02 *p2 = " << *p2 << endl;
}
int main()
{
	//指针和函数
	//1.值传递
	int a = 10;
	int b = 20;
	swap01(a, b);
	cout << "a = " << a << endl;
	cout << "b = " << b << endl;
	//2.地址传递
	//如果地址传递，可以修饰实参
	swap02(&a, &b);
	cout << "a = " << a << endl;
	cout << "b = " << b << endl;
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片44.png)

<font color=red>**总结：**</font>

* 值传递不会改变实参

* 地址传递会改变实参

### 7.8 指针、数组、函数

案例描述：封装一个函数，利用冒泡排序，实现对整型数组的升序

如数组：int arr[10]={4,3,6,9,1,2,10,8,7,5}

注意：

1.数组怎么传递到函数中，首地址和长度

2.冒泡排序

3.传入数组长度

```C++
#include <iostream>
using namespace std;

//冒泡排序函数   参数1：数组首地址  参数2:数组长度
void bubblesort(int * arr,int len)
{
	for (int i = 0; i < len - 1; i++)
	{
		//内层循环对比   次数=元素个数-当前轮数-1
		for (int j = 0; j < len - i - 1; j++)
		{
			//如果第一个数字比第二个数字大，交换两个数字
			if (arr[j] > arr[j + 1])
			{
				int temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
			}
		}
	}
}
//打印数组
void printarray(int*arr,int len)
{
	for(int i=0;i<len;i++)
	{
		cout << arr[i] << endl;
	}
}
int main()
{
	//1.创建数组
	int arr[10] = { 4,3,6,9,1,2,10,8,7,5 };
	//数组长度
	int len = sizeof(arr) / sizeof(arr[0]);
	//2.创建函数，实现冒泡排序
	bubblesort(arr, len);//数组首地址，长度
	//3.打印排序后的数组
	printarray(arr, len);
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片45.png)

## 8 结构体

### 8.1 结构体基本概念

结构体属于用户**自定义的数据类型**，允许用户存储不同的数据类型

### 8.2 结构体定义和使用

语法：`struct 结构体名 {结构体成员列表};`

通过结构体创建变量的三种方式：

* `struct 结构体名 变量名`

* `struct 结构体名 变量名={成员1值，成员2值……}`

* 定义结构体时顺便创建变量

```C++
#include <iostream>
using namespace std;
#include <string>

//1.创建学生数据类型   学生：姓名，年龄，分数
//自定义数据类型，一些类型集合组成的一个类型 语法：struct 结构体名 {结构体成员列表}；
//结构体定义
struct student
{
	 //成员列表
	//姓名
	string name;
	//年龄
	int age;
	//分数
	int score;
}s3;//顺便创建结构体变量，结构体变量创建方式3

int main()
{
	//2.通过学生类型创建具体学生
    //2.1 struct 结构体名 变量名     struct关键字可以省略
	struct student s1;
	//给S1属性赋值，通过.访问结构体变量中的属性
	s1.name = "张三";
	s1.age = 18;
	s1.score = 100;
	cout << "姓名是：" << s1.name << "  年龄是：" << s1.age << "  分数是：" << s1.score << endl;

	//2.2 struct 结构体名 变量名 = { 成员1值，成员2值…… }
	struct student s2 = { "李四",19,80 };
	cout << "姓名是：" << s2.name << "  年龄是：" << s2.age << "  分数是：" << s2.score << endl;

	//2.3 定义结构体时顺便创建变量
	s3.name = "王五";
	s3.age = 20;
	s3.score = 60;
	cout << "姓名是：" << s3.name << "  年龄是：" << s3.age << "  分数是：" << s3.score << endl;

	system("pause");
	return 0;
}
```

总结：

1.定义结构体时的关键字是struct ，不可省略

2.创建结构体变量时，关键字struct 可以省略

3.**结构体变量利用操作符“.”访问成员**

### 8.3 结构体数组

作用：将自定义的结构体放入到数组中方便维护

语法：`struct 结构体名 数组名[元素个数]={ { }，{ }，……}`

```C++
#include <iostream>
using namespace std;
#include <string>
//结构体数组
//1.定义结构体
struct student
{
	string name;
	int age;
	int score;
};

int main()
{
	//2.创建结构体数组
	struct student stuarray[3] =
	{
		{"张三",18,100},
		{"李四",28,99},
		{"王五",38,90}
	};
    //3.给结构体数组中的元素赋值
	stuarray[2].name = "赵六";
	stuarray[2].age = 80;
	stuarray[2].score = 60;
	//4.遍历结构体数组
	for(int i =0;i<3;i++)
	{
		cout << "姓名：" << stuarray[i].name << "  年龄：" << stuarray[i].age << "  分数：" << stuarray[i].score << endl;
	}
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片46.png)

### 8.4 结构体指针

作用：通过指针访问结构体中的成员

* 利用操作符->可以通过结构体指针访问结构体属性

```C++
#include <iostream>
using namespace std;
#include <string>

//结构体指针
//定义学生结构体
struct student
{
	string name;
	int age;
	int score;
};
int main()
{
	//1.创建学生结构体变量
	struct student s = { "张三",18,100 };
	//2.通过指针指向结构体变量
	struct student* p = &s;
	//3.通过指针访问结构体变量中的数据
	//通过结构体指针，访问结构体中的属性，需要利用“->”
	cout<<"姓名："<<p->name<< "  年龄：" << p->age<< "  分数：" << p->score << endl;
	system("pause");
	return 0;
}
```

输出：姓名：张三   年龄：18   分数：100

通过指针指向结构体变量 `struct student* p = &s;`

### 8.5 结构体嵌套结构体

作用：**结构体中的成员可以是另一个结构体**

例如：每个老师辅导一个同学，一个老师的结构体中，记录一个学生的结构体

```C++
#include <iostream>
using namespace std;
#include <string>

//定义学生结构体
struct student
{
	string name;
	int age;
	int score;
};
//定义老师结构体
struct teacher
{
	int id;//教师编号
	string name;
	int age;
	struct student stu;
};
int main()
{
	//结构体嵌套结构体
	//创建老师
	teacher t;
	t.id = 10000;
	t.name = "老王";
	t.age = 50;
	t.stu.name = "小王";
	t.stu.age = 20;
	t.stu.score = 60;
	cout << "老师姓名：" << t.name << "  老师编号：" << t.id << "  老师年龄："
		<< t.age << "  老师辅导的学生姓名：" << t.stu.name << "  学生年龄:"
		<< t.stu.age << "  学生分数：" << t.stu.score << endl;
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片47.png)

### 8.6 结构体做函数参数

作用：将结构体作为参数向函数传递

传递方式有两种：

* 值传递：值传递时，如果形参发生改变，不会影响实参

* 地址传递：如果形参发生改变，会改变实参

```C++
#include <iostream>
using namespace std;
#include <string>

//定义学生结构体
struct student
{
	string name;
	int age;
	int score;
};
//打印学生信息函数
//1.值传递
void printstudent1(struct student s)
{
	s.age = 80;
	cout<<"子函数中 姓名："<< s.name << "  年龄：" << s.age << "  分数：" << s.score << endl;
}
//2.地址传递
void printstudent2(struct student *p)
{
	p->age = 100;
	cout << "子函数2中 姓名：" << p->name << "  年龄：" << p->age << "  分数：" << p->score << endl;
}
int main()
{
	//结构体做函数参数
	//将学生传入到一个参数中，打印学生身上的所有信息
	//创建结构体变量
	struct student s;
	s.name = "张三";
	s.age = 20;
	s.score = 85;
	printstudent1(s);
	//printstudent2(&s);
	cout << "main函数中打印 姓名：" << s.name << "年龄：" << s.age << "分数：" << s.score << endl;
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片48.png)

如果：

```C++
//printstudent1(s);
printstudent2(&s);
```

![](C:\Users\10755\Desktop\markdown文件\图片49.png)

<font color=red>**总结：**</font>如果不想修改主函数中的数据，用值传递；反之用地址传递

### 8.7 结构体中const 使用场景

作用：用const来防止误操作

```C++
#include <iostream>
using namespace std;
#include <string>

//const的使用场景
struct student
{
	string name;
	int age;
	int score;
};
//将函数中的形参改为指针，可以减少内存空间，而且不会复制新的副本出来
//void printstudents(student s)
//{
//	s.age = 40;
//	cout << "姓名：" << s.name << "年龄：" << s.age << "分数：" << s.score << endl;
//}
void printstudents(const student *s)//const防止被改写，只能读
{
	//s->age = 40;//加const之后一旦有修改的操作就会报错，可以防止我们的误操作
	cout << "姓名：" << s->name << "年龄：" << s->age << "分数：" << s->score << endl;
}
int main()
{
	//创建结构体变量
	struct student s = { "张三",15,70 };  //并且初始化赋值

	//通过函数打印结构体变量信息
	printstudents(&s);
	cout << "main中张三年龄：" << s.age << endl;
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片50.png)

### 8.8 结构体案例

#### 8.8.1 案例一

描述：学校正在做毕设项目，每名老师带领5个学生，总共有3名老师，需求如下：

* 设计老师和学生的结构体，其中在老师的结构体中，有老师姓名和一个存放5名学生的数组作为成员

* 学生的成员有姓名，考试分数，创建数组存放3名老师，通过函数给每个老师和学生赋值

* 最后打印出老师数据以及老师所带的学生数据

```C++
#include <iostream>
using namespace std;
#include <string>
#include<ctime>
struct student
{
	string sname;
	int score;
};
struct teacher
{
	string tname;//老师姓名
	struct student sarray[5];//学生数组
};
//给老师和学生赋值的函数
void allocatespace(struct teacher tarray[],int len)
{
	string nameseed = "ABCDE";
	//给老师开始赋值
	for (int i=0;i<len;i++)
	{
		tarray[i].tname = "teacher_";
		tarray[i].tname += nameseed[i];
		//通过循环给每名老师所带的学生赋值
		for(int j=0;j<5;j++)
		{
			tarray[i].sarray[j].sname = "student_";
			tarray[i].sarray[j].sname += nameseed[j];
			int random = rand() % 61 + 40;//40~100
			tarray[i].sarray[j].score = random;
		}
		
	}
}
//打印所有信息
void printinfo(struct teacher tarray[],int len)
{
	for (int i = 0; i < len; i++)
	{
		cout << "老师姓名：" << tarray[i].tname << endl;
		for (int j = 0; j < 5; j++)
		{
			cout << "学生姓名：" << tarray[i].sarray[j].sname <<
				"考试分数：" << tarray[i].sarray[j].score << endl;
		}
	}
}
int main()
{
	//随机数种子
	srand((unsigned int) time(NULL));
	//1.创建3名老师的数组
	struct teacher tarray[3];
	//2.通过函数给三名老师的信息赋值，并给老师带的学生信息赋值
	int len = sizeof(tarray) / sizeof(tarray[0]);
	allocatespace(tarray, len);
	//3.打印所有老师和所带的学生信息
	printinfo(tarray,len);
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片51.png)

#### 8.8.2 案例二

描述：

* 设计一个英雄的结构体，包括成员姓名、年龄、性别。创建结构体数组，数组中存放5名英雄

* 通过冒泡排序的算法，将数组中的英雄按照年龄进行排序，最终打印排序后的结果

五名英雄：

{“刘备”,23,”男”}

{“关羽”,22,”男”}

{“张飞”,20,”男”}

{“赵云”,21,”男”}

{“貂蝉”,19,”女”}

```C++
#include <iostream>
using namespace std;

//1.设计英雄结构体
struct Hero
{
	string name;
	int age;
	string sex;
};
//冒泡排序，实现年龄升序排列
void bubbleSort(struct Hero heroArray[], int len)
{
	for (int i=0;i<len-1;i++)
	{
		for (int j=0;j<len-i-1;j++)
		{
			//如果j下标的元素年龄大于j+1下标的元素的年龄，交换两个元素
			if (heroArray[j].age > heroArray[j+1].age)
			{
				struct Hero temp = heroArray[j];
				heroArray[j] = heroArray[j + 1];
				heroArray[j + 1] = temp;
			}
		}
	}
}
//打印排序后数组中的信息
void printHero(struct Hero heroArray[],int len)
{
	for (int i =0;i<len;i++)
	{
		cout << "姓名：" << heroArray[i].name << "年龄：" << heroArray[i].age
			<< "性别：" << heroArray[i].sex << endl;
	}
}
int main()
{
	//2.创建数组存放5名英雄
	struct Hero heroArray[5] =
	{
		{"刘备",23,"男"},
		{"关羽",22,"男"},
		{"张飞",20,"男"},
		{"赵云",21,"男"},
		{"貂蝉",19,"女"},
	};
	int len = sizeof(heroArray) / sizeof(heroArray[0]);
	cout << "排序前打印：" << endl;
	for (int i =0;i<len;i++)
	{
		cout << "姓名：" << heroArray[i].name << "年龄：" << heroArray[i].age 
			<< "性别：" << heroArray[i].sex << endl;
	}
	//3.对数组进行排序，按照年龄升序
	bubbleSort(heroArray, len);
	cout << "排序后打印：" << endl;
	//4.将排序后的结果打印输出
	printHero(heroArray, len);
	system("pause");
	return 0;
}
```

![](C:\Users\10755\Desktop\markdown文件\图片52.png)

