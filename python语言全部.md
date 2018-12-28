# python语言基础

# 数据存储

## 思考

```
思考：为什么使用计算机？
为了存储数据、处理数据

思考：数据存在哪里？
数据存储在内存中

思考：内存是怎么存储数据的？
首先要弄清楚怎么存储数字
```

## 内存

```
内存：是计算机存储数的介质
抽象内存：一个开关，有两种状态，开启和关闭，一种对应1，一种对应0。把8个开关放到一间房子里，可以称这间房子为“一个字节”，一个开关代表的是一位。每个房间都有门牌号，看做“地址”。把无数个房间罗列起来组成摩天大厦，可以把摩天大厦看成内存。
```

## 单位

```
1bit
8bit      ==    1字节
1024字节  ==    1k
1024k     ==    1M
1024M     ==    1G
1024G     ==    1T
```

## 进制

```
二进制：逢2进1
        0 1
        1 + 1 = 10
八进制：逢8进1
        0 1 2 3 4 5 6 7
        1 + 7 = 10
十进制：逢10进1
        0 1 2 3 4 5 6 7 8 9
        1 + 9 = 10
十六进制：逢16进1
        0 1 2 3 4 5 6 7 8 9 a b c d e f
        1 + f = 10
```

## 进制转换

```
十进制转二进制
    公式：倒除法，余数逆序
二进制转十进制
    公式：当前的数字(0、1)乘以2的位数次方，在相加
    1001 -> 1 x 2^3 + 0 x 2^2 + 0 x 2^1 + 1 x 2^0 
八进制转二进制
    公式：【一转三位】八进制的一位相当于二进制的三位，计算时按十进制转换，不足三位高位补0
二进制转八进制
    公式：【三位一取】从低位开始，每三位得到一个八进制数字，最后高位不足则补0
十六进制转二进制
    公式：【一转四位】十六进制的一位相当于二进制的四位，计算时按十进制转换，不足四位高位补0
二进制转十六进制
    公式：【四位一取】从低位开始，每四位得到一个十六进制数字，最后高位不足则补0
```

## 内存中存储的数据

```
存储数据：
    1、计算机先开辟空间，在存储数据，计算机开辟空间的最小单位是字节
    2、在数据存储时，用最高位标识符号位，0表示正数，1表示复数
```

## 原码、补码、反码

```
1    -1

原码：规定了字节数，写明了符号位，得到了数据的原码
    思考：内存是以数据原码的形式存储的吗？

     0000 0000  0000 0000  0000 0000  0000 0001
+    1000 0000  0000 0000  0000 0000  0000 0001
---------------------------------------------------
     1000 0000  0000 0000  0000 0000  0000 0010   -2

    结论：不以原码的形式存储数据

反码：正数的反码就是其原码，负数的反码事其原码的符号位不变其他位取反
    思考：内存是以数据反码的形式存储的吗？
     0000 0000  0000 0000  0000 0000  0000 0001
+    1111 1111  1111 1111  1111 1111  1111 1110
--------------------------------------------------- 
     1111 1111  1111 1111  1111 1111  1111 1111

    结论：不以反码的形式存储数据

补码：正数的补码是其原码(正数三码合一)，负数的补码是反码加1
 
     0000 0000  0000 0000  0000 0000  0000 0001
+    1111 1111  1111 1111  1111 1111  1111 1111
---------------------------------------------------  
  1  0000 0000  0000 0000  0000 0000  0000 0000

  加法最后得到的1溢出了，没有存储到内存中
  
    结论：以补码的形式存储数据
```

# 第一个python程序

```
# python程序的文件以.py结尾
# python程序的文件名以后最好不要有中文


# 交互模式
# 黑屏终端输入 python 进入交互模式
# 输入 exit() 退出交互模式


# 命令模式
# 输出  将引号内的字符串输出到黑屏终端上
print("sunck is a good man! phone is 13691511443")
# 执行 进入程序所在目录，执行 python 文件名
```

# 注释

```
# 单行注释，只能注释一行

# 多行注释
# 根据对象的引用计数器，对象创建会给对象一个引用计数器属性，如果该属性的值为0，那么该对象会被释放。创建了一个字符串对象，但是没有任何的引用，所以计数器为0.
'''
print("sunck is a good man")
print("sunck is a nice man")
'''

"""
print("sunck is a cool man")
print("sunck is a handsome man")
"""

print("sunck is a very good man")
```

# 输入与输出

## 输入

```
# 输入：从外部获取变量的值
# input：阻塞，等待输入
name = input()
print("---------------------")
print(name)
```

## 输出

```
# 输出：打印到屏幕上一些信息
# 可以接受多个字符串，用逗号分隔
# 在写python程序时切记不要使用中文字符
print("sunck is a good man", "sunck is a nice man", 18)
```

# python数据类型

```
1、Number（数字）
    整数
    浮点数
    复数

2、String（字符串）
    "sunck is a good man"
    'sunck is a nice man'

3、Boolean（布尔值）
    表示真假的值

4、None（空值）

5、list（列表）

6、tuple（元组）

7、dict（字典）

8、set（集合）
```

# 标识符

```
标识符的作用：给变量、函数等命名的

什么是标识符：是一串字符串(注意：字符串未必是标识符)

标识符的规则：
    1、只能由字母、数字、下划线组成
    2、开头不能是数字
    3、不能是python的关键字  
        ['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
    4、区分大小写
    5、见名知意

    注意：在python3中，非ASCII标识符也是允许的了(但是慎用)
'''
```

# 变量与常量

```
'''
变量：
    概述：
        1、程序可操作的存储区名称
        2、程序运行过程期间能改变的数据
        3、每个变量都有特定的类型

    作用：
        将不同类型的数据存储到内存

    定义变量：
        变量名 = 数据值
        注意：变量在使用前必须先定义，否则会出现错误

    删除变量：
        del 变量名
        注意：删除后变量无法引用
'''
# print("num =", num)
age = 18
print("age =", age)
del age
# print("age =", age)

'''
常量：程序运行期间不能改变的数据
'''
```

# 运算符与表达式

## 概念

```
表达式：由变量、常量和运算符组成的式子称为表达式

阅读表达式：
    1、阅读表达式的功能
    2、阅读表达式的值
```

## 算数运算符与算数运算表达式

```
'''
算术运算符：
    +  -  *  /  %    **   //
    加 减 乘 除 取模 求幂 取整
'''
'''
算术运算表达式
    功能：进行符号对应的算术运算，不会修改变量的值
    值：相关算术运算的结果
'''
num1 = 10
num2 = 3
print(num1 + num2)
print(num1 - num2)
print(num1 * num2)
print(num1 / num2)
print(num1 % num2)
print(num1 ** num2)
print(num1 // num2)
```

## 赋值运算符和赋值运算表达式

```
'''
赋值运算符  =
'''
'''
赋值运算表达式
    格式：变量 = 表达式
    功能：计算右侧表达式的值，并赋值给等号左侧的变量
    值：赋值结束后变量的值
'''
num3 = 10
num4 = num3 + 2
```

## 复合运算符

```
'''
复合运算符：
    +=   -=    *=   /=    %=    **=    //=
    a += b  -->  a = a + b 
    a -= b  -->  a = a - b
    a *= b  -->  a = a * b
    a /= b  -->  a = a / b
    a %= b  -->  a = a % b
    a **= b  -->  a = a ** b
    a //= b  -->  a = a // b   
'''
```

## 位运算符



```
'''
位运算符：
    &  按位与运算符：参与运算的两个值，如果两个相应位都为1，则该位结果为1，否则为0

    |  按位或运算符：参与运算的两个值，如果两个相应位有一个为1时，则该位结果为1，否则为0

    ^  按位异或运算符：参与运算的两个值，如果两个相应不同时，则该位结果为1，否则为0

    ~  按位取反运算符：对数据的每个二进制位进行取反操作，把1变为0，把0变为1

    << 左移运算符：运算数的各二进制全部左移若干位，由<<右侧数字指定移动位数，高位丢弃，低位补0
    >> 右移运算符：运算数的各二进制全部右移若干位，由>>右侧数字指定移动位数
'''
print(5 & 7)
print(5 | 7)
print(5 ^ 7)
print(~5)
print(2 << 2)
print(11 >> 2)
```

## 关系运算符与关系运算表达式

```
'''
关系运算符
    ==     !=      >    <    >=       <=
    等于   不等于  大于 小于 大于等于 小于等于
'''
'''
关系运算表达式
格式：表达式1 关系运算符 表达式2
功能：计算表达式1和表达式2的值
值：
    如果关系成立，则整个关系运算表达式的值为真，如果关系不成立，则整个关系运算表达式的值为假
'''
if 1==1:
    print("sunck is a handsome man!")
```

## 逻辑运算符与逻辑运算表达式

### 与

```
'''
逻辑运算符
    逻辑与    逻辑或   逻辑非
'''

'''
逻辑与运算符         and

逻辑与运算表达式   
    格式：表达式1 and 表达式2
    功能：首先计算“表达式1”的值，若表达式1的值为真则计算“表达式2”的值
    值：
        1、如果表达式1的值为真，表达式2的值为真，则逻辑与运算表达式的值为真
        2、如果表达式1的值为真，表达式2的值为假，则逻辑与运算表达式的值为假
        3、如果表达式1的值为假，表达式2的值为真，则逻辑与运算表达式的值为假
        4、如果表达式1的值为假，表达式2的值为假，则逻辑与运算表达式的值为假
        总结：有一个为假就为假
'''
a = 2
b = 1
if a - 1 and b + 1:
    print("sunck is a good man!")
else:
    print("sunck is a nice man!")
```

### 或

```
'''
逻辑或       or
逻辑或运算表达式  
    格式：表达式1 or 表达式2
    功能：首先计算“表达式1”的值，如果表达式1的值为假，则继续计算“表达式2”的值
    值：
        1、如果表达式1的值为真，表达式2的值为真，则逻辑或运算表达式的值为真
        2、如果表达式1的值为真，表达式2的值为假，则逻辑或运算表达式的值为真
        3、如果表达式1的值为假，表达式2的值为真，则逻辑或运算表达式的值为真
        4、如果表达式1的值为假，表达式2的值为假，则逻辑或运算表达式的值为假
        总结：有一个为真就为真
'''
c = 2
d = 1
if c - 1 or print("123"):
    print("sunck is a very good man!")
else:
    print("sunck is a very nice man!")
```

### 逻辑与、逻辑或的特性

```
短路原则：
    表达式1 and 表达式2 and 表达式3 and …… and 表达式n
        从左至右依次计算表达式的值，直到遇到某个表达式的值为假就停止计算
    表达式1 or 表达式2 or 表达式3 or …… or 表达式n
        从左至右依次计算表达式的值，直到遇到某个表达式的值为真就停止计算
```

### 非

```
'''
逻辑非   not

逻辑非运算表达式
    格式：not 表达式
    值：
        1、如果“表达式”的值为真，则逻辑非运算表达式的值为假
        2、如果“表达式”的值为假，则逻辑非运算表达式的值为真
        总结：颠倒黑白
'''
e = 1
if not e:
    print("sunck is a very very good man!")
else:
    print("sunck is a very very nice man!")
```

## 成员运算符

```
'''
成员运算符
    格式： x in seq        x not in seq
in：如果在指定的序列中找到值则返回真，否则返回假
not in：如果在指定的序列中没有找打值则返回真，否则返回假
'''
```

## 身份运算符

```
'''
身份运算符
    格式： obj1 is obj2      obj1 is not obj2
is：判断两个标识符是否引用同一个对象，相同返回真，否则返回假
is not：判断两个标识符是否引用不同对象，不同返回真，否则返回假
'''
```

## 运算符优先级

```
'''
运算符的优先级：
**              指数
~ + -           按位取反和一元加减号
*  /  %  // 
+ -             加法减法
<<  >>
&
| ^
<  >  <=  >=
==  !=   <>
=  *=  /=  %=  //%  +=  -=  **=
is       is not
in       not in
and or not
'''
```

# 条件控制语句

```
'''
if语句
'''

'''
if-else 语句
'''

'''
if-elif-else语句

格式：
if 表达式1:
    语句1
elif 表达式2:
    语句2
……
elif 表达式n:
    语句n
else:
    语句e


逻辑：当程序执行到if-elif-else语句时，首先计算“表达式1”的值，如果“表达式1”的值为真，则执行“语句1”，执行完“语句1”则结束整个if-elif-else语句继续向下执行。如果“表达式1”的值为假，则计算“表达式2”的值，如果“表达式2”的值为真，则执行“语句2”，执行完“语句2”则结束整个if-elif-else语句继续向下执行。如果“表达式2”的值为假，则计算“表达式3”的值。如此进行下去，直到某个表达式的值为真为止。如果所有的表达式都为假，且有else语句则执行“语句e”

深刻理解（精髓）：每一个(else if)else都是对它上面所有表达式的否定
'''
'''
从该控制台输入一个年龄
小于0    输入有误
0~1      婴儿
2~6      幼儿
7~14     儿童
15~18    少年
19~30    青年
31~40    壮年
41~50    中年
51~150   老年
151~     妖精
'''

age = int(input("输入一个年龄:"))
# if age <= 0:
#     print("输入错误")
# if  age > 0 and age <= 1:
#     print("婴儿")
# if  age >= 2 and age <= 6:
#     print("幼儿")
# if  age >= 7 and age <= 14:
#     print("儿童")
# if  age >= 15 and age <= 18:
#     print("少年")
# if  age >= 19 and age <= 30:
#     print("青年")
# if  age >= 31 and age <= 40:
#     print("壮年")
# if  age >= 41 and age <= 50:
#     print("中年")
# if  age >= 51 and age <= 150:
#     print("老年")
# if  age > 150:
#     print("妖怪")


# if age <= 0:
#     print("输入错误")
# elif  age > 0 and age <= 1:
#     print("婴儿")
# elif  age >= 2 and age <= 6:
#     print("幼儿")
# elif  age >= 7 and age <= 14:
#     print("儿童")
# elif  age >= 15 and age <= 18:
#     print("少年")
# elif  age >= 19 and age <= 30:
#     print("青年")
# elif  age >= 31 and age <= 40:
#     print("壮年")
# elif  age >= 41 and age <= 50:
#     print("中年")
# elif  age >= 51 and age <= 150:
#     print("老年")
# else:
#     print("妖怪")




if age <= 0:
    print("输入错误")
elif  age <= 1:
    print("婴儿")
elif  age <= 6:
    print("幼儿")
elif  age <= 14:
    print("儿童")
elif  age <= 18:
    print("少年")
elif  age <= 30:
    print("青年")
elif  age <= 40:
    print("壮年")
elif  age <= 50:
    print("中年")
elif  age <= 150:
    print("老年")
else:
    print("妖怪")
```

# 循环语句（while）

## 格式与逻辑

```
'''
格式：
while 表达式:
    语句

逻辑：当程序执行到while语句时，首先计算表达式的值，如果表达式的值为假，则跳过整个while语句继续向下执行。如果表达式的值为真，则执行语句，执行完语句再计算表达式的值。如果表达式的值为假，则跳过整个while语句继续向下执行。如果表达式的值为真，则执行语句，执行完语句在计算表达式的值，如此循环往复直到表达式的值为假才停止。
'''
```

## 使用else语句



```
'''使用else语句 
格式：
while 表达式:
    语句1
else:
    语句2    

逻辑：在表达式的值为False时执行else语句中的语句2，如果是break结束的循环不走else语句
'''
a = 1
while a < 5:
    print("sunck is a nice man")
    a += 1
else:
    print("sunck is a good man")
```

# 循环语句（for）

## 格式与逻辑

```
'''
格式：
for 变量 in 集合:
    语句

逻辑：当程序执行到for语句时，按顺序取“集合”中的每个元素赋值给“变量”，在执行“语句”。如此循环往复，直到取完集合中的元素为止。
'''
```

## range函数

```
# range([startNum,]endNum[, step])
# 列表生成器
# startNum：开始的数字，默认为0
# endNum：结束的数字，不包含在内
# step: 步长，默认为1
# [1,2,3,4,5]
for x in range(1, 6):
    print("x = %d"%x)
```

## 同时遍历下标和元素

```
# 同时遍历下标和元素
for index, x in enumerate([1,2,3,4,5]):
    print(index, x)
```

# pass语句、continue语句、break语句

## pass语句

```
'''pass语句
作用：当语句要求不希望任何命令或代码来执行
说明：pass语句时一个空操作，在执行时没有任何响应。pass也是代码最终会用的，但是暂时写不出来
使用在 if语句、while语句、for语句、函数、类等位置
'''
if 1:
    pass
for x in [1,2,3]:
    pass
```

## continue语句

```
'''continue
作用：跳过本次循环快中的剩余语句，然后继续下一次循环
注意：只能跳过距离最近的for或者while
'''
for x in [1,2,3,4,5]:
    if x == 3:
        continue
    print("x = %d"%x)
print("-------------------")

# 代码嵌套，层级要明确，嵌套最多在6、7层左右，最好3层
for m in [1,2,3,4,5]:
    print("m = %d"%m)
    for n in [1,2,3,4,5]:
        if n == 3:
            continue
        print("n = %d"%n)
```

## break语句

```
'''break
作用：跳出循环
注意：只能跳出距离最近的for或者while
'''
for x in [1,2,3,4,5]:
    if x == 3:
        break
    print("x = %d"%x)
# print("-------------------")
# for m in [1,2,3,4,5]:
#     print("m = %d"%m)
#     for n in [1,2,3,4,5]:
#         if n == 3:
#             break
#         print("n = %d"%n)


# 循环语句可以有else子句，表达式错误导致循环终止时被执行，但循环被break终止时else语句不执行
index = 0
while index < 3:
    print("index = %d"%index)
    index += 1
    if index == 1:
        break
else:
    print("循环结束了")


print("---------------------------------")
```

# 深拷贝与浅拷贝

```
from copy import copy, deepcopy
'''
==：判断的是值
is：判断的是内存地址
'''
# num1 = 300
# num2 = 300
# print(id(num1), id(num2))
# print(num1 == num2)
# print(num1 is num2)

'''
小整数对象：[-5, 256]
最好在python环境中演示，pycharm进行了其他的优化
'''


# a = [1,2,3,4,5,[7,8,9]]
# b = a
# print(b == a)
# print(b is a)
# a[5][1] = 100
# print(a, b)
# print(id(a), id(b))
# print(id(a[5]), id(b[5]))

a = [1,2,3,[4,5,6]]
#深浅拷贝的区分的前提是列表中要有其他列表
#浅拷贝：只拷贝表层元素
# copy
b = copy(a)


#深拷贝：在内存中重新创建所有子元素
# deepcopy
c = deepcopy(a)

a[0] = 100
print(a, b, c)

# print(b == a)
# print(b is a)
# print(c == a)
# print(c is a)
# print(id(a[1]), id(b[1]), id(c[1]))
# print(id(a), id(b), id(c))
# print(id(a[3]), id(b[3]), id(c[3]))
# print(id(a[3][1]), id(b[3][1]), id(c[3][1]))
```

# turtle绘图模块

## 操作

```
'''
是一个简单的绘图工具
提供了一个小海龟，类似一个机器人，能听懂一些简单的命令
绘图窗口的原点(0,0)在正中间，默认海龟向右侧移动
'''



'''操作命令
1、运动命令
    forward(a)     向前移动,a代表距离
    backward(a)    向后移动,a代表距离
    right(degree)  向右转动degree度
    left(degree)   向左转动degree度
    goto(x, y)     将笔画(小海龟)移动到坐标(x,y)的位置
    speed([speed]) 笔画绘制的速度，范围在[0,10]之间的整数 
    
2、笔画控制命令
    up()                笔画抬起，移动时不绘制图形
    down()              笔画落下，移动时绘制图形
    setheading(degree)  海龟的朝向，degree代表角度
    reset()             恢复设置，清空窗口，重置turtle为起始状态
    clear()             清空窗口
    pensize(width)      笔画的宽度
    begin_fill()        开始填充
    fillcolor(color)    绘制图形的填充颜色
    end_fill()          结束填充
    dot(radius, color)  画点
    circle(redius, extent, steps) 绘制一个圆形，redius为半径，extent为次数，如果是画圆就不必写第二个参数

3、其他命令
    undo()    撤销turtle上一个动作
    hideturtle()   隐藏箭头
    showturtle()   显示箭头
    write(str, font=(font-name, font-size, font-type))
    screensize(x,y)   设置屏幕的宽高
    

'''
```

# Number(数字)

## 整数

```
'''
整数：
    python可以处理任意大小的整数，包含负数
'''
num1 = 10
print(id(num1))
print(type(num1))
# 连续定义
num3 = num4 = num5 = 1
# 交互对称定义
num6, num7 = 1, 2
print(num6, num7)

# 查看数据在内存中的地址
# 小整数对象
num1 = 12
num2 = 13
print(id(num1), id(num2))
num8 = -6
num9 = -6
print(id(num8), id(num9))
```

## 浮点数

```
'''
浮点：由整数部分和小数部分组成的
    注意：运算可能有四舍五入的误差
'''
num10 = 0.1
num11 = 0.2
print(num10 + num11)
```

## 复数

```
'''
复数：实数部分和虚数部分构成，一般不使用。
'''
```

## 数学函数

```
# 求绝对值
num1 = -18
num2 = abs(num1)
print(num2)

# 求多个数中的最大值
print(max(5,3,2,8,6,9,11,3,7))

# 求多个数中的最小值
print(min(5,3,2,8,6,9,11,3,7))

# 求x的n次方
print(pow(2, 4))

# 四舍五入  
# round(x[, n])将浮点数进行四舍五入，如果给出n的值，则代表舍入到小数点的后四位
print(round(3.1415926, 4))
```

## math模块

```
import math
# 向上取整  18.9
print(math.ceil(18.1))
# 向下取整
print(math.floor(18.9))
# 得到浮点数的小数部分和整数部分
print(math.modf(18.5))
# 开平方，数字不能是负数
print(math.sqrt(5))
```

## 随机数

```
# 导入随机数模块
import random
```

```
# 1、choice(seq)  从序列(集合)中随机获取一个元素
print(random.choice([2,4,6,8,10]))
```

```
# 2、randrange([start, ]stop[, step])
# 作用：从指定范围内，按照指定基数递增的集合中获取一个随机数，基数默认为1
# start-指定范围的开始值，包含在范围内，默认从0开始
# stop-指定范围的结束值，不包含在范围内
# step-指定的基数
print(random.randrange(3)) #[1,2,3,4]
```

```
# 3、random()
# 随机生成一个实数，范围在[0, 1)之间，得到浮点数
print(random.random())
```

```
# 4、uniform(x, y)
# 随机生成一个实数，范围在[x, y]之间，得到浮点数，x为随机数的最小值，y为随时的最大值
print(random.uniform(3, 8))
```

```
# 5、shuffle(list)
# 将序列的元素随机排列
arr = [1,2,3,4,5]
random.shuffle(arr)
print(arr)
```

```
# 6、randint(start, stop)
# 在指定的范围获得一个整数[start, stop]
print(random.randint(1,5))
```

## 三角函数

```
三角函数

#反正弦弧度值
asin(x)
#反正切弧度值
atan(x)
#反余弦弧度值
acos(x)
#x的弧度的余弦值
cos(x)
#x的弧度的正弦值
sin(x)
#x的弧度的正切值
tan(x)
#角度转为弧度
radians(x)
```

## 数字类型转换

```
# int(x)  将x转为一个整数
print(int(10.1))
print(int("123"))
```

```
# float(x)
print(float(10))
print(float("123.34"))
```



# 字符串

## 什么是字符串

```
'''
什么是字符串？
    字符串是以单引号或者双引号括起来的任意文本，比如'sunck is a good man'或者"sunck is a nice man"。但是要注意引号本身是一种表现形式，不属于字符串的一部分。
    注意：如果字符串本身带双引号    'sunck is a "very" good man'
'''
```

## 创建字符串

```
#创建字符串
str1 = 'sunck is a good man'
str2 = "sunck is a nice man"
```

## 字符串运算

```
'''字符串运算'''
# 字符串拼接
str3 = 'sunck is a good man'
str4 = "sunck is a nice man"
print(str3 + str4)
#重复输出字符串
print(str3 * 3)
# 通过索引下标获取字符串中的字符，索引从0开始(程序员放羊)   str[index]
print(str3[1])
# 截取字符串中的一部分  切片编程
print("*"+str3[11:15]+"*")
print("*"+str3[11:]+"*")
print("*"+str3[:15]+"*")
# 判断字符串中是否存在某些内容
print("kaige" in str3)
```

## 格式化输出字符串

```
'''
格式化输出（占位符）
%s  格式化字符串  
%d  格式化整数
%f  格式化浮点数，可以指定小数点后的精度，默认保留小数点后6位
'''
name = "sunck"
age = 18
height = 173.5
#    sunck is a good man, he is 18 years old, his height is 173.5cm.
print(name, "is a good man, he is", age, "years old, his height is", height, "cm.")
#如果只有一个替换，可以不写%后面的小括号，但是建议还是不要省略
print("%s is a good man, he is %d years old, his height is %.2fcm."%(name, age, height))
weight=75
print("*%d*"%(weight))
print("*%5d*"%(weight))
print("*%-5d*"%(weight))
print("*%.5d*"%(weight))
```

## 常用转义字符

```
'''
常用转义字符    
反斜杠     \\
单引号      \'
双引号     \"
换行       \n
横向制表符  \t
'''
str5 = '\\'
print(str5)
str6 = "sunck is a \"very\" good man"
print(str6)
print("sunck is\na good man")
# 如果字符串内部有过个换行，用\n写在一行里非常利于阅读
print("sunck\nis\na\ngood\nman")
print('''
line1
line2
line3
line4
''')
print("sunck\tgood")
# 如果字符串里面有很多字符需要转义，就需要加入很多\，为了简化，python允许使用r''表示''内部的字符串默认不转义
print('\\\t\\')
print(r'\\\t\\')
```

## String内置函数

```
# eval()
'''
原型：eval(*args, **kwargs)
功能：将字符串当成有效的表达式来求值并返回计算结果
参数:
'''
num1 = eval("123")
print(num1)
print(type(num1))
print(eval("+123"))
print(eval("-123"))
print(eval("12+3"))
print(eval("12-3"))
# print(eval("a123"))
# print(eval("12a3"))
abc = "123"
print(eval("abc"))
```

```
# len(string)
'''
原型：
功能：返回字符串的长度(按字符个数计算)
参数:
'''
print(len("sunck is a good man"))
print(len("sunck is a good man凯"))
```

```
# lower()
'''
原型：
功能：转换字符串中所有的大写字母为小写
参数:
'''
str1 = "Sunck Is A Good maN"
str2 = str1.lower()
print(str1, str2)
```

```
# upper()
'''
原型：
功能：转换字符串中所有的小写字母为大写
参数:
'''
```

```
# swapcase()
'''
原型：
功能：将字符串中大写转为小写，小写转为大写
参数:
'''
str3 = "Sunck Is A Good maN"
str4 = str3.swapcase()
print(str3, str4)
```

```
# capitalize()
'''
原型：
功能：将字符串中第一个字符转为大写，其余转为小写,用于每句话中开始字母大写
参数:
'''
str5 = "sunck Is A Good maN"
str6 = str5.capitalize()
print(str5, str6)
```

```
# title()
'''
原型：
功能：得到“标题化”的字符串，每个单词的首字符大写，其余小写
参数:
'''
str7 = "sunck Is A Good maN"
str8 = str7.title()
print(str7, str8)
```

```
# center(width[, fillchar])
'''
原型：
功能：返回一个指定宽度width的居中字符串,fillchar为填充字符，默认为空格
参数:
'''
str9 = "good"
str10 = str9.center(20, "#")
print("*"+str10+"*")
```

```
# ljust(width[, fillchar])
'''
原型：
功能：返回一个指定宽度width的左对齐字符串，fillchar为填充字符，默认为空格
参数:
'''
str11 = "good"
str12 = str11.ljust(20, "#")
print("*"+str12+"*")
```

```
# rjust(width,[, fillchar])
'''
原型：
功能：返回一个指定宽度width的右对齐字符串，fillchar为填充字符，默认为空格
参数:
'''
```

```
# zfill (width)
'''
原型：
功能：返回指定宽度width的右对齐字符串，填充0
参数:
'''
str13 = "good"
str14 = str13.zfill(20)
print("*"+str14+"*")

```

```
# count(str[, beg= 0,end=len(string)])
'''
原型：
功能：返回str在string里面出现的次数，如果beg或者end指定则返回指定范围内str出现的次数
参数:
'''
str15 = "sunck"
str16 = "sunck is a good man! sunck is a nice man"
print(str16.count(str15,0,20))

```

```
# find(str[, beg=0 end=len(string)])
'''
原型：
功能：检测str是否包含在string中，如果指定beg和end，则检测指定范围内是否包含。如果包含返回第一个开始的索引值，否则返回-1
参数:
'''
str17 = "sunck"
str18 = "cool"
str19 = "aaasunck is a good man! sunck is a nice man"
res = str19.find(str18)
print(res)

```

```
# index(str[, beg=0, end=len(string)])
'''
原型：
功能：跟find()一样，区别在于如果str不存在会报异常
参数:
'''
str20 = "sunck"
str21 = "cool"
str22 = "aaasunck is a good man! sunck is a nice man"
res = str22.index(str20)
print(res)

```

```
# rfind(str[, beg=0,end=len(string)])
'''
原型：
功能：类似于find(),只不过从右边开始查找
参数:
'''

```

```
# rindex(str[, beg=0, end=len(string)])
'''
原型：
功能：类似于index(),只不过从右边开始查找
参数:
'''

```

```
# lstrip()
'''
原型：
功能：截掉字符串左边指定的字符，默认为空格
参数:
'''
str23 = "    sunck is a good man"
str24 = str23.lstrip()
print(str23)
print(str24)
str25 = "*****sunck is a good man"
str26 = str25.lstrip("*")
print(str25)
print(str26)

```

```
# rstrip()
'''
原型：
功能：截掉字符串右边指定的字符，默认为空格
参数:
'''

```

```
# strip([chars])
'''
原型：
功能：在字符串上执行lstrip和rstrip
参数:
'''
str27 = "*****sunck is a good man**"
str28 = str27.strip("*")
print(str27)
print(str28)

```

```
# split(str="", num=string.count(str))
'''
原型：
功能：
参数:
'''
str29 = "sunck#is#a#good#man"
wordList = str29.split("#")
print(wordList)
print(type(wordList))

```

```
# splitlines([keepends])
'''
原型：
功能：按照行('\r','\r\n','\n')，如果keepends为False，不包含换行符，否则保留换行符
参数:
'''
str30 = '''good
nice
cool
handsome
'''
wordList2 = str30.splitlines()
print(wordList2)

```

```
# join(seq)
str31 = " ".join(wordList)
print(str31)
'''
原型：
功能：
参数:
'''

```

```
# max(str)
'''
原型：
功能：返回字符串中最大的字母
参数:
'''
str32 = "sunck is a good man"
print(max(str32))

```

```
# min(str)
'''
原型：
功能：返回字符串中最小的字母
参数:
'''

```

```
# replace(old, new [, max])
'''
原型：
功能：将字符串中的old替换成new，如果max指定，则替换不超过max次
参数:
'''
str33 = "sunck is a good man, sunck is a nice man, sunck is a cool man"
str34 = str33.replace("sunck", "kaige")
print(str34)

```

```
# maketrans()
'''
原型：
功能：创建字符映射的转换表，对于接受两个参数的,第一个是字符串，表示要转换的字符，第二个也是字符串表示转换的目标
参数:
'''
t = str.maketrans("ag", "12")


```

```
# translate(table)
'''
原型：
功能：根据str给出的表转换字符串
参数:
'''
str35 = "sunck is a good manag"
print(str35.translate(t))


```

```
# isalpha()
'''
原型：
功能：如果字符串至少有一个字符并且所有的字符都是字母返回True，否则返回假
参数:
'''
print("".isalpha())
print("abc".isalpha())
print("abc12".isalpha())


```

```
# isalnum()
'''
原型：
功能：如果字符串至少有一个字符并且所有的字符都是字母或数字返回True，否则返回假
参数:
'''
print("".isalnum())
print("abc".isalnum())
print("abc12".isalnum())


```

```
# isupper()
'''
原型：
功能：如果字符串至少有一个字符并且所有的字母都是大写字母返回True，否则返回假
参数:
'''
print("sunck".isupper())
print("SUNCK".isupper())
print("SUNCK#$%".isupper())
print("SUNCK123".isupper())
print("".isupper())


```

```
# islower()
'''
原型：
功能：如果字符串至少有一个字符并且所有的字母都是小写字母返回True，否则返回假
参数:
'''


```

```
# istitle()
'''
原型：
功能：如果字符串是标题化的返回True，否则返回False
参数:
'''


```

```
# isdigit()
'''
原型：
功能：如果字符串只包含数字返回True，否则返回False
参数:
'''
print("".isdigit())
print("123".isdigit())
print("abc123".isdigit())


```

```
# isnumeric()
'''
原型：
功能：如果字符串只包含数字返回True，否则返回False
参数:
'''


```

```
# isdecimal()
'''
原型：
功能：检测字符串是否只包含十进制数字
参数:
'''


```

```
# isspace()
'''
原型：
功能：如果字符串中只含有空格则返回True,否则返回False
参数:
'''
print("".isspace())
print("   ".isspace())
print(" a".isspace())
print("\t".isspace())
print("\n".isspace())

print("--------------------")


```

```
# startswith(str[, beg=0,end=len(string)])
'''
原型：
功能：检查字符串是否以str开头，是则返回True， 否则返回False。如果指定了beg和gend,则在指定范围内检查
参数:
'''
str40 = "sunck is a good man"
print(str40.startswith("good"))


```

```
# endswith(suffix[, beg=0, end=len(string)])
'''
原型：
功能：检查字符串是否以suffix结尾，是则返回True， 否则返回False。如果指定了beg和gend,则在指定范围内检查
参数:
'''


```

```
# encode(encoding='UTF-8',errors='strict')
'''
原型：
功能：以encoding指定的编码格式进行编码，如果出错默认报一个ValueError异常，除非errors指定的是igonre或者replace
参数:
'''
str41 = "凯哥是一个好男人"
str42 = str41.encode()
str43 = str41.encode("GBK") #gb2312
print(str41)
print(str42)
print(str43)


```

```
# bytes.decode(encoding="utf-8", errors="strict")
'''
原型：
功能：解码
参数:
'''
print(str42.decode("utf-8"))
print(str43.decode("GBK"))


```

```
# ord()
'''
原型：
功能：获取字符的整数表示
参数:
'''
print(ord("A"))
print(ord("凯"))


```

```
# chr()
'''
原型：
功能：把数字编码转为对应的字符
参数:
'''
print(chr(65))
print(chr(20975))


```

```
# str()
'''
原型：
功能：转成字符串
参数:
'''
print(str(123))
print(str(123.1))
print(type(str(True)))


```

# 布尔值和None

```
作用：作为真假的判断
'''
b = True
c = False
print(b, c)
print(type(b), type(c))


```

```
'''
空值：是python里一个特殊的值，用None表示。None不能理解为0，因为0是有意义的，而None是一个特殊的控制，没有实际意义。
作用：定义个变量时，不知道初始值要赋值成什么，那么就赋值为None，当有确定值在进行赋值操作。
'''
d = None
print(d)
print(type(d))

```

# list列表

## 概述

```
'''
问题：存储5个人的年龄，求他们的平均年龄
'''
age1 = 18
age2 = 19
age3 = 20
age4 = 21
age5 = 22
print((age1+age2+age3+age4+age5)/5)

'''
问题：存储100个人的年龄，求他们的平均年龄
解决：使用列表
列表本质：是一种有序的集合
'''

```

## 创建列表

```
'''创建列表
格式： 列表名 = [列表选项1, 列表选项2, ……, 列表选项n]
'''
# 创建空列表
list1 = []

# 创建带有元素的列表
# 列表中的元素的数据类型可以不同
list2 = [18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, "good", True, None]

```

## 列表元素访问

```
'''
列表元素的访问
'''
list3 = [18, 19, 20, 21, 22]
# 取值：列表名[下标]
print(list3[2])
# 替换：列表名[下标] = 新值
list3[2] = 200
print(list3)
# 注意：下标不要越界
# print(list3[5])
# list3[5] = 23
# print(list3)

```

## 列表操作

```
'''
列表操作
'''
# 列表组合
list4 = [1,2,3]
list5 = [4,5,6]
print(list4, list5)
print(list4 + list5)
# 列表重复
list6 = [7,8,9]
print(list6 * 3)
# in        not in
print(1 in [1,2,3])
# 列表截取(切片)
list7 = [1,2,3,4,5,6,7,8,9,0]
print(list7[2])
print(list7[1:4])
# -1表示的是最后一个元素的下标， -2倒数第二个元素的下标
print(list7[1:-1])
print(list7[4:])
print(list7[:4])

```

## 二维列表

```
'''
二维列表:列表中元素是一维列表
本质：一维列表
'''
list8 = [[1,2,3],
         [4,5,6],
         [7,8,9]]
print(list8)
print(list8[1][1])

```

## 列表方法

```
# append(obj)
# 在列表的末尾添加一个新的元素
list1 = [1,2,3,4,5]
list1.append([9,8,7])
print(list1)

```

```
# extend(seq)
# 在列表末尾一次性追加多个元素
list2 = [1,2,3,4,5]
list2.extend([9,8,7])
print(list2)

```

```
# insert(index, obj)
# 将元素出入列表，不会覆盖原元素，原元素按顺序后移
list3 = [1,2,3,4,5]
list3.insert(2, 100)
print(list3)

```

```
# pop(obj=list[-1])
# 移除列表中指定下标处的元素，默认删除最后一个元素
list4 = [1,2,3,4,5]
list4.pop()
# list4.pop()
print(list4)

```

```
# remove(obj)
# 移除列表中的某个值的第一个匹配项
list5 = [1,2,3,4,5,3]
list5.remove(3)
print(list5)

```

```
# clear()
# 清空列表
list6 = [1,2,3,4,5,3]
list6.clear()
print(list6)

```

```
# index(obj)
# 从列表中找出某个值第一个匹配项的下标
list6 = [1,2,3,4,5,3]
print(list6.index(3))

```

```
# len(list)
# 返回列表中元素的个数
list7 = [1,2,3,4,5,3]
print(len(list7))

```

```
# count(obj)
# 统计某个元素在列表中出现的次数
list7 = [1,2,3,4,5,3]
print(list7.count(3))

```

```
# max(list)
# 返回列表中元素的最大值

```

```
# min(list)
# 返回列表中元素的最小值

```

```
# reverse()
# 倒序列表中元素
list8 = [1,2,3,4,5,3]
list8.reverse()
print(list8)

```

```
# sort([func])
list9 = [4,7,1,3,9,5]
list9.sort()
list9.reverse()
print(list9)

```

```
# list(seq)
# 转为列表  字符串、元组、集合
print(list("sunck"))

```

# tuple（元组）

## 概述

```
'''
元组
本质：是一种有序集合

特性：
    1、与列表非常类似
    2、一旦初始化就不能修改
    3、使用小括号
'''

```

## 创建元组

```
#创建元组： 元组名 = (元组选项1, 元组选项2, ……, 元组选项n)
#创建空元组
t1 = ()
print(t1)
# 定义带元素的元组
# 元素类型可以不同
t2 = (1,2,3,4,5,"good")
print(t2)
# 定义含有一个元素的元组
# 注意：加个逗号
t3 = (1,)
print(t3)

```

## 元组的访问

```
'''
元组元素的访问
'''
#取值  元组名[下标]
t4 = (1,2,3,4,5)
print(t4[1])
# print(t4[5]) #下标越界
print(t4[-1])
print(t4[-5])
# print(t4[-6])  # 下标越界
#修改元组,元组的元素不能修改，但是元素如果是个列表那么可以修改这个列表
t5 = (1,2,3,4,5,[6,7,8])
# t5[5] = [8,7,6]
t5[5][1] = 100
print(t5)

```

## 元组的操作

```
'''元组的操作'''
#元祖的组合
t6 = (1,2,3)
t7 = (4,5,6)
print(t6 + t7)
#元组重复
print(t6 * 3)
# 元组截取（切片）
# 与列表、字符串向类似
t8 = (1,2,3,4,5,6,7,8,9)
print(t8[2:7])

```

## 元组方法

```
'''元组的方法'''
# len(tuple)
# 返回元组的元素个数
t9 = (1,2,3)
print(len(t9))

# max(tuple)
# min(tuple)

# tuple(seq)
# 将集合转为元组
l = [1,2,3,4,5,6]
t10 = tuple(l)
print(t10)

```

# dict（字典）

## 概述

```
'''
使用键-值对(key-value)的形式存储数据，具有极快的查找速度

可以的特性：
    1、字典中的key必须唯一
    2、key必须是不可变对象
        a、字符串、整数等都是不可变的，可以作为key
        b、列表时可变的，不能作为key
    3、key一般为字符串


思考：保存一个学生的基本信息(姓名、性别、年龄、升高、体重)
stu1 = ["sunck", "男", 18, 173.5, 75]
stu2 = ["男", "liudehua", 72, 55, 173]


解决：使用字典
注意：字典中的键值对是无序的
'''

```

## 创建字典

```
# 创建字典存储一个学生的基本信息
# {key1:value,key2:value2,……,keyn:valuen}
stu1 = {"name": "sunck", "age": 18, "sex": "男", "height": 173.5, "weight": 75}
stu2 = {"name": "liudehua", "age": 55, "sex": "男", "height": 173, "weight": 72}
stus = [stu1, stu2]
print(stu1)

```

## 访问字典

```
#元素的访问
stu3 = {"name": "sunck", "age": 18, "sex": "男", "height": 173.5, "weight": 75}
#获取    字典名[key]    字典.get(key)
print(stu3["name"])
# print(stu3["score"]) #获取的键不存在会报错
score = stu3.get("score")
if score:
    print("分数为：%.2f"%score)
else:
    print("学生没有这个属性")

```

## 字典的添加、删除、遍历

```
#添加  如果键不存在则增加属性，否则覆盖原数据
stu3["socre"] = 99.99
stu3["height"] = 180
print(stu3)

```

```
#删除
stu3.pop("socre")
print(stu3)

```

```
#遍历
stu4 = {"name": "sunck", "age": 18, "sex": "男", "height": 173.5, "weight": 75}
for key in stu4:
    print(key)
print("--------")
for value in stu4.values():
    print(value)
print("--------")
for key, value in stu4.items():
    print(key+": "+str(value))
print("--------")
for index, key in enumerate(stu3):
    print(index, key)

```

## list和dict的比较

```
'''比较list和dict
dict
    优点：查找和插入的速度极快，不会随着key的增多而降低效率
    缺点：需要占用大量的内存，内存浪费过多
list
    优点：占用内存空间小，浪费内存很少
    缺点：查找和插入的时间会随着元素的增加而增加
'''

```

# set（集合）

## 概述

```
'''
与dict类似，是一组key的集合(不存储value)
本质：无序和无重复的集合
'''

```

## 创建

```
#创建:需要用一个list或者tuple作为输入集合
# 注意列表中的重复元素会被过滤掉
s1 = set([1,2,3,4,5,3,4])
print(s1)
# 列表去重
numList = [1,2,3,5,7,8,3,5,6,8,9]
numList = list(set(numList))
print(numList)

```

## 添加

```
#添加
s2 = set([1,2,3,4,5])
# 插入list、字符串、元组的每个元素
# iterable 可迭代对象
# s2.update("sunck")
# s2.update([6,7,8])
# s2.update((6,7,8))
# 不能直接插入数字
# s2.update(9)
print(s2)

```

## 删除

```
#删除
s3 = set([1,2,3,4,5])
# 从左侧开始删除
print(s3.pop())
# 删除对应的元素，如果元素不存在会报KeyError的异常
s3.remove(3)
print(s3)

```

## 遍历

```
#遍历
s4 = set([6,2,3,4,5])
for key in s4:
    print(key)
print("------")
for index, key in enumerate(s4):
    print(index, key)

```

## 交集与并集

```
#交集与并集
s5 = set([1,2,3])
s6 = set([2,4,3])
# 交集
print(s5 & s6)
# 并集
print(s5 | s6)

```

# 类型转换

```
'''

list和tuple中的元素不能存在可变对象
list、tuple、string-->set
set()

tuple、set、string-->list
list()

list、set、string-->tuple
tuple()
'''
```

# 函数

## 概述

```
'''认识函数：
在一个完整的项目中，某些代码会被反复使用。那么将某段代码封装成函数，当我们要使用功能的时候直接调用函数即可
本质：函数是对功能的封装
有点：简化代码结构，增加代码的复用度
'''
```

## 定义函数

```
'''定义函数
格式
def 函数名(参数列表)：
    语句
    return 表达式

说明：
    def：函数代码块以def关键字开头
    函数名：遵守标识符的规则
    ()：参数列表的开始和结束
    参数列表：是函数的调用者给函数的信息，多个信息之间用逗号分隔，如果没有信息，那么小括号中什么都不用写（注意此时小括号不能省略）(形参)
    冒号：函数的内容以冒号起始，并且锁紧
    语句：函数封装的功能
    return：一般用于结束函数，并返回给函数的调用者一些信息。“表达式”就是要返回的数据。如果没有显示的去写return语句，默认return回None
    
注意：
    定义函数时，程序是不会执行函数，当调用函数时才会执行
'''

# def gaolei(money):
#     pass
```

## 使用函数

```
'''使用函数
格式：
函数名(参数列表)

说明：
    函数名：要使用某个功能函数的名字
    ()：参数列表的开始和结束
    参数列表：调用者给函数的信息(实参)
    
函数调用的本质：实参给形参赋值的过程
'''
```

## 函数参数

```
# 编写函数，给函数一个名字，一个年龄，一些爱好，在函数中进行打印
#  sunck  18    pwoer、money、book

#形式参数(形参):变量
#参数的数量理论上是无限制的，但是实际中最好不要超过6、7个，参数是类型没有限制
def func(name, age, hobby):
    print("%s is a good man! he is %d years old! he like %s、%s and %s"%(name, age, hobby[0], hobby[1], hobby[2]))

#函数在调用时，需要给函数按顺序传递数据，数量要对应
# 实际参数(实参)：是值
func("sunck", 18, ["power", "money", "book"])
```

## 函数返回值

```
# 编写函数，实现计算两个数的和
# 注意：在定义的函数体中，尽量不要常出现print和input
def func(x, y):
    sum = x + y
    return sum #将结果返回到调用函数的位置，返回的数据可以是任意类型的数据

# res接收了func函数运算后的返回值
res = func(1, 2)
```

## 传递参数

```
# 值传递：传递不可变类型数据
def func(num):
    print(id(num))
    num = 10
    print(id(num))
a = 20
print(id(a))
func(a)
print(a)




print("-------------------")
# 引用传递：传递可变类型数据
# 本质还是值传递，传递的是地址
def func2(arr):
    print(id(arr))
    arr.pop()
    print(id(arr))
li = [1,2,3,4,5]
print(id(li))
func2(li)
print(id(li))
print(li)
```

## 关键字参数

```
# -*- coding:utf-8 -*-



#目前为止的要求：函数调用时参数的顺序要与定义时一致
#关键字参数：允许函数调用时参数的顺序与定义时不一致


def func(name, age):
    print("%s is a good man! he is %d years old!"%(name, age))

#使用关键字参数
func(age=18, name="sunck")
```

## 默认参数

```
# -*- coding:utf-8 -*-

# 使用默认参数
# 在定义函数时尽量将默认参数写在最后
def func(name, age=18):
    print("%s is a good man! he is %d years old!"%(name, age))

# 在调用函数时，如果没有传递参数，就使用默认参数的值
func("sunck", 20)
```

## 不定长参数

```
# -*- coding:utf-8 -*-


#不定长参数：能处理比当初定义时更多的参数

# 在变量前加了星号，变量会存放所有未命名的变量的参数，如果在函数调用时没有指定参数，他就是个空元组
# 不定长参数在默认参数后面
# def func(name, age, a = 10, *args):
#     print("%s is a good man! he is %d years old"%(name, age))
#     print(args, type(args))
#
# func("sunck", 18)


#  **kwargs
#  **代表着键值对字典，和*差不多
# def func(name, age, **kwargs):
#     print("%s is a good man! he is %d years old"%(name, age))
#     print(kwargs, type(kwargs))
#
# func("sunck", 18, x=1, y=2, z=3)


def func(*args, **kwargs):
    print(args)
    print(kwargs)

func(1,2,3,x=1,y=2,z=3)
```

## 多个返回值

```
# -*- coding:utf-8 -*-


# 返回值可以一次性返回多个值
# 游戏中返回任务的坐标
def func():
    return 1,2

x, y = func()
z = func()
print(x, y)
print(z)
# for index, value in enumerate([1,2,3,4,5]):
```

## 匿名函数

```
# -*- coding:utf-8 -*-





'''
概念：不在使用def语句这样标准的形式定义函数，使用lambda来创建匿名函数

特定：
    1、lambda只是一个表达式，函数体比def简单得多
    2、lambda主体是一个表达式而不是代码块，仅能在lambda表达式中封装有限的逻辑
    3、lambda函数拥有自己的命名空间，且不能访问自有参数序列之外或全局命名空间里的参数
    4、虽然lambda函数看起来只能写一行，去不同于c和c++的内联函数，后者的目的是调用小函数时不占用栈内存而增加运行效率

格式:
    lambda [arg1[, arg2[, arg3, ……]]]:expression


使用：作为参数传递，实现回调。简化代码
'''

f = lambda x, y: x + y
ret = f(5, 6)
print(ret)
```

# 特殊函数

## map函数

```
'''map(fn, lsd)
参数：
    fn：是一个函数
    lsd：集合
功能：将传输的函数fn依次作用到lsd集合中的每个元素，并把结果作为新的Iterator返回
'''
def chr2int(chr):
    return {"0": 0, "1": 1, "2": 2, "3": 3, "4": 4, "5": 5, "6": 6, "7": 7, "8": 8, "9": 9}[chr]
ret = map(chr2int, "13586")
print(ret)
print(list(ret))
```

## reduce函数

```
'''reduce(fn, lsd)
参数：
    fn：函数
    lsd：集合
功能：传入的fn函数作用在lsd集合中，这个fn函数必须接受两个参数，reduce把结果继续和序列的下一个元素作累计计算
    
    reduce(f, [a, b, c, d])==f(f(f(a,b),c),d)

'''
# 求一个序列的和
from functools import reduce
def func(x, y):
    return x + y
res = reduce(func, [1,2,3,4,5])
print(res)



#reduce配合map实现str2int
def str2int(s):
    def chrToint(chr):
        return {"0": 0, "1": 1, "2": 2, "3": 3, "4": 4, "5": 5, "6": 6, "7": 7, "8": 8, "9": 9}[chr]
    def f(x, y):
        return x * 10 + y
    return reduce(f, map(chrToint, s))

res = str2int("13543")
print(res)
print(type(res))
```

## filter函数

```
# -*- coding:utf-8 -*-



'''
filter(fn, lsd)

参数：
    fn：函数
    lsd：集合

功能：用于过滤序列，把传入的fn函数依次作用在lsd集合中的每个元素上，然后根据返回值是True还是False决定是否保留该元素

'''

li1 = [1,2,3,4,5,6,7,8,9]
# 去掉列表中的所有偶数

#过滤的过程
# for i in li1:
#     if i % 2 == 0:
#         li1.remove(i)
# print(li1)

#过滤的逻辑
def func(num):
    if num % 2 == 0:
        return False
    return True
res = filter(func, li1)
print(li1)
print(res)
print(list(res))





#  找所有的素数



# 需求：删除列表中是空字符串的元素
li2 = ["a", "", "", "c", "    ", "  bsg  "]
def f(item):
    return item and item.strip()
res = filter(f, li2)
print(list(res))
```

## sorted函数

```
# -*- coding:utf-8 -*-


'''

排序算符：冒泡排序、快速排序、      选择排序、计数器排序……

'''
li = [3,4,1,2,5]


# 对列表进行排序
li1 = [3,4,1,2,5]
li2 = sorted(li1)
print(li2)

# 按绝对值大小排序
li3 = [3,-4,1,-2,5]
# key接收函数来实现自定义的排序
li4 = sorted(li3, key=abs)
print(li4)


#降序排序
li5 = [3,-4,1,-2,5]
li6 = sorted(li5, reverse=True)
print(li6)


# 字符串大小问题
# 原理：获取两个字符的第一个字符进行比较，谁的ASCII值大那么谁就大，如果相同则获取下一位字符比较
# print("abc">"ab")
li7 = ["abc", "awg", "agaerger", "eherth"]
#自定义排序逻辑
def func(x):
    return len(x)
li8 = sorted(li7, key=func)
print(li8)
```

# 作用域

## 概述

```
# -*- coding:utf-8 -*-

'''
作用域：变量可以使用的范围，程序的变量并不是在哪个位置都可以访问的，访问的权限决定于这个变量实在哪里赋值的。


作用域的划分：
    1、局部作用域(L)
    2、闭包函数外到函数中(E)
    3、全局作用域(G)
    4、内建作用域(B)

变量查找规则：
    L->E->G->B，首先在自身作用域中查找，找不到的话依次向上级作用中查找，注意不会向低级作用域中查找

Python中只有模块，类以及函数才会引入新的作用域，其它的代码块(比如if、elif、else、for、while、try、except等)是不会引入新的作用域的。

'''
```

## 体现作用域

```
# -*- coding:utf-8 -*-
num = 5
#if不会引入新的作用域
if 1:
    index = 10
    print("num = %d"%num)

print("index = %d"%index)

def func(x, y):
    # 取值的使用
    print("在func中使用num：%d"%num)
    # 定义局部变量
    tmp = 100
    return x + y
print(func(1,2))
#在全局中使用局部变量，找不到的
# print("tmp = %d"%tmp)
```

## 修改全局变量

```
# -*- coding:utf-8 -*-



num = 10
def func():
    # 在函数的内部可以直接获取全局变量的值，但是不能直接修改全局变量的值。直接修改相当于定义一个新的局部变量，没有修改到全局变量本身
    # 需要将定义的变量声明成全局变量
    global num
    num = 2
    print("1-----num = %d" % num)

func()
print("2-----num = %d" % num)
```

## 修改嵌套作用域中的变量

```
# -*- coding:utf-8 -*-
a = 30
def func():
    # 有global会在nonlocal那里报错，申明为全局的后就没有嵌套的了
    # global a
    # a = 10
    def f():
        #想修改嵌套作用域中的变量，需要将它声明
        # nonlocal a
        # a = 20
        print("1----a = %d"%a)
    f()
    print("2----a = %d"%a)

func()
print("3----a = %d"%a)
```

## 变量的作用域

```
# -*- coding:utf-8 -*-

a = 10
def func1():
    b = 20
    def func2():
        c = 30
        return a + b + c
    return func2()


print(func1())
```

## 利用闭包突破作用域链

```
# -*- coding:utf-8 -*-


'''闭包
概念：在函数体重定义内部函数，并且使用了外部函数的变量，然后把内部函数给，那么这个内部函数就是闭包

优点：避免污染全局环境，这样就可以在函数体外使用函数体中定义的变量

缺点：数据长期驻留在内存中，造成内存极大的浪费。


'''
a = 10
def func1():
    b = 20
    def func2():
        c = 30
        return a
    return func2


f2 = func1()
print(f2())





def func3():
    b = 40
    def func4():
        return b
    return func4
```

# 装饰器

## 概念

```
# -*- coding:utf-8 -*-

'''

是一个闭包，把一个函数作为参数然后返回一个替代版函数，本质上就是一个返回函数的函数

'''

#在不修改原函数的前提下增加函数的功能，最好的方式是使用装饰器
def func():
    print("sunck is a good man")


def f():
    print("***********")
    func()
```

## 简单装饰器

```
# -*- coding:utf-8 -*-

def func():
    print("sunck is a good man")

def wrapper(f):
    def inner():
        print("***********")
        f()
    return inner

# d = wrapper(func)
# d()
func = wrapper(func)
func()
```

## 复杂装饰器

```
# -*- coding:utf-8 -*-

# 下不修改say原函数代码的情况下增加say的功能，判断age是否符合常理
def say(name, age):
    return "%s is a good man! he is %d years old"%(name, age)



def wrapper(f):
    def inner(name, age):
        #增加功能
        if age <= 0:
            age = 0
        return f(name, age)
    return inner


say = wrapper(say)

print(say("sunck", -18))
```

## 使用@符号装饰

```
# -*- coding:utf-8 -*-
'''
python2.4支持使用@将装饰器应用在函数上，只需要再函数定义前加上@装饰器的名称即可

'''
def wrapper(f):
    def inner(name, age):
        #增加功能
        if age <= 0:
            age = 0
        return f(name, age)
    return inner

@wrapper
def say(name, age):
    return "%s is a good man! he is %d years old"%(name, age)

# 相当于  say = wrapper(say)

print(say("sunck", -18))
```

## 通用装饰器

```
# -*- coding:utf-8 -*-

def wrapper(f):
    def inner(*args, **kwargs):
        #在这增加功能
        print("no zuo no die")
        res = f(*args, **kwargs)
        #如果要修改原函数的返回值，在这修改
        return res
    return inner



@wrapper
def func(name, age):
    print(name, age)
    return "sunck is a good man"

print(func("kaige", 17))

@wrapper
def func2(height):
    print(height)
    print("**********")
func2(111)
```

## 参数装饰器

```
# -*- coding:utf-8 -*-

def wrapper(count=3):
    def deco(f):
        def inner(*args, **kwargs):
            for i in range(count):
                f(*args, **kwargs)
        return inner
    return deco

@wrapper()
def func():
    print("sunck is a good man")

func()
```

## 多个装饰器

```
# -*- coding:utf-8 -*-
def wrapper1(f):
    print("enter wrapper1")
    def inner1(*args, **kwargs):
        print("enter inner1")
        res = f(*args, **kwargs)
        print("exit inner1")
        return res
    print("exit wrapper1")
    return inner1

def wrapper2(f):
    print("enter wrapper2")
    def inner2(*args, **kwargs):
        print("enter inner2")
        res = f(*args, **kwargs)
        print("exit inner2")
        return res
    print("exit wrapper2")
    return inner2

def wrapper3(f):
    print("enter wrapper3")
    def inner3(*args, **kwargs):
        print("enter inner3")
        res = f(*args, **kwargs)
        print("exit inner3")
        return res
    print("exit wrapper3")
    return inner3

'''
装饰时：从距离近的装饰器开始装饰
执行时：从距离远的装饰器内部函数开始执行
'''
@wrapper1
@wrapper2
@wrapper3
def func(x, y):
    return x + y

print("----------------")
func(1, 2)



'''
inner3 = wrapper3(func)
inner2 = wrapper2(inner3)
inner1 = wrapper1(inner2)
func = inner1
'''
```

## 装饰器使用场景

```
# -*- coding:utf-8 -*-


'''
1、参数、结果检查
2、缓存
3、计数
4、日志
5、统计
6、权限管理
7、重试
'''

#=====================================================================
'''
1、参数检查是否合格
需求：计算年龄平均值，年龄不能为负数
'''
# def warpper(f):
#     def inner(*args,**kwargs):
#         for i in args:
#             if i <= 0:
#                 print("输入年龄有误")
#                 return
#         res = f(*args,**kwargs)
#         return res
#     return inner
#
# @warpper
# def avgYears(*args):
#     sum = 0
#     for i in args:
#         sum += i
#     av = sum/len(args)
#     return av
#
# print(avgYears(10,12,-2))

'''
结果检查
题目：计算两个数的和，结果超过100则给出警告，否则输出两个数的和
'''
# def wrapper(f):
#     def inner(a,b):
#         res = f(a,b)
#         if res > 100:
#             print("警告")
#         else:
#             return res
#     return inner
# @wrapper
# def sum(a,b):
#     return a+b
# print(sum(100,2))

'''
计数
题目：对函数调用次数统计
'''
# def wrapper(f):
#     count = 0
#     def inner(*args,**kwargs):
#         res = f(*args,**kwargs)
#         nonlocal count
#         count += 1
#         print("函数第%d次调用"%(count))
#         return res
#     return inner
#
# @wrapper
# def sum(a,b):
#     return a+b
#
# @wrapper
# def f():
#     print("fanding is a good man")
#
# print(sum(1,2))
# print(sum(4,5))
# f()
# f()

'''
重试
题目：数据库连接重试
'''
# import time
# def retry(count=3,wait=0,exceptions=(Exception,)):
#     def deco(f):
#         def inner(*args,**kwargs):
#             for i in range(count):
#                 try:
#                     res = f(*args,**kwargs)
#                 except:
#                     time.sleep(wait)
#                     continue
#                 else:
#                     return res
#         return inner
#     return deco
#
# import random
# @retry(3)
# def conn(ip, port, dbName, passwd):
#     num = random.choice([1, 2, 3, 4])
#     print("**************", num)
#     if num <= 2:
#         10 / 0
#
# conn("","","","")
```

# 可迭代对象

```
# -*- coding:utf-8 -*-

'''
概念：可以直接作用于for循环的对象统称可迭代对象(Iterable)


可以直接作用于for循环的数据类型：
    1、集合数据类型，如list、tuple、dict、set、string等
    2、generator，包含生成器和带yield的generator function

注意：可以使用isinstance()函数判断一个对象是否是Iterable对象
'''

from collections import Iterable

print(isinstance([], Iterable))
print(isinstance({}, Iterable))
print(isinstance((), Iterable))
print(isinstance("sunck", Iterable))
print(isinstance((x for x in range(10)), Iterable))
print(isinstance(100, Iterable))
```

# 列表生成式

```
# -*- coding:utf-8 -*-

'''
作用：python内置的非常简单并且强大的可以用来生成list的生成式
'''

# 生成列表
# 缺点：只能生成简单的列表
print(list(range(1, 11)))


# 需求：[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

# 循环生成列表
# 缺点：循环比较繁琐
li = []
for i in range(1, 11):
    li.append(i * i)
print(li)

# 列表生成式生成列表
li2 = [x * x for x in range(1, 11)]
print(li2)


# 列表生成式的for循环后可以加判断
li3 = [x * x for x in range(1, 11) if x % 2 == 0]
print(li3)


# 排列    组合    排列组合
# 使用双层循环，生成全排列
li4 = [m + n for m in "ABC" for n in "123"]
print(li4)





#六位密码全排列
# import string
# cc = 0
# print(type(string.digits))
# password = (a+b+c+d+e+f for a in string.digits for b in string.digits for c in string.digits for d in string.digits for e in string.digits for f in string.digits)
```

# 生成器

```
# -*- coding:utf-8 -*-

'''
概念：
    通过列表生成式，可以直接创建一个列表。所有的数据都会存到内存中，受内存的限制，列表的容量是有限制的。如果列表中有10000个数据，如果我们只需访问前几个元素，后面的基本不会访问，那么造成内存极大的浪费。
    如果列表中的元素可以按照某种算法推导出来，那么我们在循环遍历列表时不断推导后面的元素，从而节省大量内存。在python中，这种一边循环一边推导的机制称为生成器(generator)
'''


#创建生成器
# 1、修改列表生成式：将列表生成式的[]改为()即可
g = (x  for x in range(1, 6))
print(g)
print(type(g))
#生成器特点：可以通过next()函数获得generator的下一个值
# print(next(g))
# print(next(g))
# print(next(g))
# print(next(g))
# print(next(g))
# # 当所有元素都拿出来后在执行next会得到StopIteration异常
# print(next(g))

#遍历
#原理：generator保存的是算法，每次调用next()就计算生成器下一个元素的值，直到抛出StopIteration错误为止
# while 1:
#     print(next(g))
# print("sunck is a goo dman")
# 以后一般都是使用for循环来迭代生成器，不需要关心StopIteration异常
for i in g:
    print(i)
```

## 函数实现生成器

```
# -*- coding:utf-8 -*-

'''
推导的算法比较复杂，用列表生成式for循环无法实现的时候可以选择使用函数生成生成器
'''

# 函数是按顺序执行，遇到return语句或者最后一行函数语句就返回。
# 如果想让一个函数变为生成器函数，只需将函数的return改为yield
# 变成generator函数，在每次调用next()的时候，遇到yield语句返回，如果再次执行next(),会从上次返回的yield语句处继续执行
def func():
    yield 0
    print("sunck is a good man")
    yield 1
    print("sunck is a nice man")
    yield 2
    print("sunck is a cool man")
    yield 3

res = func()
# print(res)
# print(type(res))
print(next(res))
print(next(res))
print(next(res))
print(next(res))
# 遇到yield中断，再继续执行没有yield会报错
# print(next(res))
```

## 斐波那契数列练习

```
# -*- coding:utf-8 -*-

'''
0,     1,1,2,3,5,8,13,
'''

#编写函数实现斐波那契数列
# def fib(count):
#     index = 0
#     x, y = 0, 1
#     while index < count:
#         print(y)
#         x, y = y, x + y
#         index += 1
# fib(5)



# 生成器实现
# def fib(count):
#     index = 0
#     x, y = 0, 1
#     while index < count:
#         yield y
#         x, y = y, x + y
#         index += 1
#
# g = fib(6)
# for i in g:
#     print(i)





def fib(count):
    index = 0
    x, y = 0, 1
    while index < count:
        yield y
        x, y = y, x + y
        index += 1
    return "sunck is a good man"

g = fib(6)
# for循环遍历generator时，拿不到generator的return与的返回值
# 如果想拿返回值，必须捕获StopIteration错误，返回值包含在错误对象的value属性中
while 1:
    try:
        ret = next(g)
        print(ret)
    except StopIteration as e:
        print("返回值：", e.value)
        break
```

# 迭代器

```
# -*- coding:utf-8 -*-

'''
概述：
    1、可以被next()函数调用并返回一个值的对象称为迭代器对象(Iterator)
    2、迭代器不但可以作用于for循环，还可以被next()调用
'''

from collections import Iterator
print(isinstance([], Iterator))
print(isinstance({}, Iterator))
print(isinstance("sunck", Iterator))
print(isinstance((x for x in range(1, 5)), Iterator))


#转成Iterator对象
li = [1,2,3,4,5]
# 将可迭代对象转为迭代器
li = iter(li)
print(next(li))
print(next(li))
print(next(li))
print(next(li))
print(next(li))



# 为什么list、dict、str、set等数据类型不是Iterator
# Iterator对象表示的是一个数据流，Iterator对象能被一个next()函数调用并返回一个数据 ，直到抛出StopIteration错误。可以把数据流看成是一个有序的序列，但是不确定这个序列的长度，只能通过next()函数不断计算下一个数据，所以说Iterator的设计是惰性求值的。Iterator可以表示一个无限大的数据流，而list永远不可能存储无限的数据
```

# import语句

```
格式：import module1[, module2[, module3[, module4], ……]]
注意：一个模块只会被导入一次，不管你执行了多少次import，有效的防止导入模块被一次次的执行

使用模块中的内容：
    module.方法/变量/类
```

# from...import语句

```
作用：从模块中导入一个指定的部分
格式：from modulename import name1[, name2[, name3], ……]
```

# from...import*语句

```
作用：把一个模块的所有内容全部导入当前命名空间
格式：from modulename import *
注意：不应该过多的使用，很可能造成变量的冲突
```

# __name__属性

```
每个模块都一个__name__属性，当其值为"__main__"时，表明该模块自身在运行，否则是被当做模块引入，此时值为模块的名字

作用:模块就是一个可执行的python文件，一个模块被另一个模块引入，向让模块中的某一程序不执行，我们可以用__name__属性来使程序隐藏该块代码，当自身执行时在执行该块代码
```

# 模块概述

```
在计算机程序的开发过程中，随着程序代码越写越多，在一个文件里代码就会越来越长，越来越难以维护
为了编写可维护性的代码，我们会把很多函数进行分组，分别放到不同的文件里，这样，每个文件包含的代码就相对较少，大多数编程语言都是采用这种组织代码的方式。在python中，一个.py文件就称之为一个模块(module)



优点：
    1、提高了代码的可维护性
    2、提高了代码的复用度，编写代码不必从零开始，当一个模块编写完成，就可以被其他地方引用
    3、引用其他模块，包含python内置模块和第三方模块
    4、避免函数名和变量名等命名的冲突
```

# time模块

## 名词



```
UTC（世界协调时间）：格林尼治时间，世界标准时间。在中国UTC+8
DST（夏令时）：是一种为了节约能源而认为规定地方时间的制度，一般在天亮早的夏季将时间提前一小时
```

## 时间表示形式

```
1、时间戳
    以整型或者浮点型表示的是一个以秒为单位的时间间隔，这个时间的基础值是1970年1月1日零时开始算
2、元组形式
    一种python的数据结构表示，这个元组有9个整型元素，分别表示不同的时间含义
   year
   month(1-12)
   day(1-31)
   hours(0-23)
   minutes(0-59)
   seconds(0-59) 
   weekday(0-6,星期一为0)
   Julian day(1-366)：表示当前日期在本年是第几天，day in the year
   DST flag(-1 or 0 or 1)：夏令时格式，0表示正常格式，1表示为夏令时格式，-1表示根据当前的日期时间格式来判定
3、格式化字符串
    %a    本地简化星期名称
    %A    本地完整星期名称
    %b    本地简化月份名称
    %B    本地完整月份名称
    %c    本地相应的日期和时间表示
    %d    一个与中的第几天(01-31)
    %H    一天中的第几个小时(24时制，00-23)
    %I    一天中的第几个小时(12时制，01-12)    
    %j    一年中的第几天(001-366)
    %m    月份（01-12）
    %M    分钟数（00-59）
    %p    本地am或者pm的相应符号
    %S    秒（00-59）
    %U    一年中的星期数，以星期天为一个星期
    %w    一个星期中的第几天(0-6, 0表示星期日)
    %W    和%U基本相同，以星期一为一个星期
    %x    本地相应日期
    %X    本地相应时间
    %y    去掉世纪的年份(00-99)
    %Y    完整的年份
    %Z    时区的名字，如果不存在为空字符串
```

## 方法

```
# time()
#返回当前的时间戳，浮点数形式，无需传参
t1 = time.time()
print(t1)
```

```
# gmtime()
# 将时间戳转换为UTC时间元组格式，接收一个浮点型时间戳为参数，如果不传默认值为当前时间的时间戳
t2 = time.gmtime()
print(t2)
```

```
# localtime()
# 将时间戳转换为本地时间元组格式，接收一个浮点型时间戳为参数，如果不传默认值为当前时间的时间戳
t3 = time.localtime()
print(t3)
```

```
# mktime()
# 将本地时间元组转为时间戳，接受一个时间元组
t4 = time.mktime(t3)
print(t4)
```

```
# asctime()
# 将时间元组格式转为字符串形式，接受一个时间元组，默认值为localtime时间的时间元组
t5 = time.asctime(t3)
print(t5)
print(type(t5))
```

```
# ctime()
# 将时间戳转为字符串，接受一个时间戳，默认值为当前时间戳
t6 = time.ctime()
print(t6)
print(time.asctime(time.localtime()))
```

```
# strftime()
# 将时间元组以指定的格式转换为字符串形式，接受一个字符串格式化串、时间元组(默认为localtime())
t7 = time.strftime("%Y-%m-%d %X", t3)
print(t7)
```

```
# strptime()
# 将指定格式的时间字符串解析为时间元组，是strftime逆过程，
t8 = time.strptime("1999-10-01 08:08:08", "%Y-%m-%d %X")
print(t8)
```

```
# sleep()
# 延迟一个时间段，接收整型或者浮点型
```

```
# clock()
# 返回当前程序执行时间，Unix系统始终返回全部运行时间，而windows从第二次开始都是以第一次调用此函数的时间戳为基准，而不是以程序开始时间为基准
```

![](C:/Users/fanfan/Desktop/课堂笔记/课堂笔记pdf版/图片/%E6%97%B6%E9%97%B4%E7%B1%BB%E5%9E%8B%E8%BD%AC%E6%8D%A2%E5%9B%BE.png)

# datetime模块

## 概述

```
datetime 比 time 高级了不少，可以理解为 datetime 基于time进行了封装，提供了更使用的函数接口，datetime模块的接口更直观、更容易调用
```

## 模块中的类

```
模块中的类：
    time      只关注时间
    date      只关注日期
    datetime  同时有时间和日期   
    timedelta 主要用于计算时间跨度
    tzinfo    时区相关
```

## 方法

```
# 获取当前时间
t1 = datetime.datetime.now()
print(t1)
print(type(t1))
```

```
# 获取指定时间
t2 = datetime.datetime(1999, 10, 1, 8, 8, 8, 0)
print(t2)
```

```
# 将时间转为字符串
t3 = t1.strftime("%Y-%m-%d %X")
print(t3)
print(type(t3))
```

```
#将格式化字符串转为datetime对象
t4 = datetime.datetime.strptime(t3, "%Y-%m-%d %X")
print(t4)
print(type(t4))
```

```
# 时间相减，返回一个时间间隔
t5 = datetime.datetime(1999, 10, 1, 8, 8, 8, 0)
t6 = datetime.datetime(1999, 10, 2, 9, 8, 8, 0)
t7 = t6 - t5
print(t7)
print(type(t7))
#间隔天数
print(t7.days)
#除去间隔天数以外的间隔秒数
print(t7.seconds)
```

# calendar模块

```
import calendar
```

```
#返回指定年的某月
# print(calendar.month(2018, 8))
```

```
# 返回指定年的日历
# print(calendar.calendar(2018))
```

```
# 判断某一年是否是闰年
# print(calendar.isleap(2000))
```

```
#返回某个月的weekday的第一天和这个月的所有天数
# print(calendar.monthrange(2017, 8))
```

```
#返回某个月以一周为周期的元素序列
print(calendar.monthcalendar(2018, 12))
```

# collections模块

## namedtuple

```
概述：
# namedtuple
# 命名元组，本质是一个函数，用它来创建一个自定义的tuple对象
# 规定tuple元素的个数，并可以用属性而不是索来引用tuple中的元素
# 用namedtuple定义一个新的数据类型

```

```
# 假如这是一个点的坐标，但是没有写注释，过了好久就不知道了
p = (1, 2)
#定义了一个新的数据类型，属于tuple类型的子类型
Point = namedtuple("Point", ["x", "y"])
point = Point(1, 2)
print(isinstance(point, tuple))
print(isinstance(point, Point))
print(point)
print(point[0], point[1])
# 根据属性获取值
print(point.x, point.y)

```

## deque

```
# deque
# 使用list存储数据，按索引访问元素，但是插入和删除元素会根据元素的个数增多而效率降低。因为list是线性存储，数据量大插入和删除效率会低
# deque 就是为了高效实现插入和删除操作的双向列表，适用于队列和栈

```

```
q = deque([1,2,3,4,5])

q.append(6)
q.appendleft(0)
q.pop()
q.popleft()
print(q)

```

## defaultdict

```
from collections import defaultdict

# 使用dict时，如果引用的key不存在，会抛出KeyError异常。如果希望key不存在时，能得到一个默认的值，就使用defaultdict

d1 = {"a":1, "b":2, "c":3}
# print(d1["d"])
print(d1.get("d"))


d2 = defaultdict(lambda :"good")
d2["a"] = 1
print(d2)
print(d2["a"])
print(d2["d"])
print(d2.get("d"))

```

## OrderedDict

```
from collections import OrderedDict

#使用dict时，key是无序的。对dict做迭代时无法保证key的顺序。如果需要key有顺序，就可以使用OrderdDict
d1 = {"a":1, "b":2, "c":3}
print(d1)

# 顺序是按照键值对插入的顺序
d2 = OrderedDict([("a",[11, 111]),("c",33),("b",22)])
print(d2)
print(d2["a"])
print(d2.get("a"))

```

## Counter

```
from collections import Counter

# 一个简单的计数器，本质上是dict的一个子类

# 计算集合中每个元素出现的次数
a = "sunck is a good man"
c = Counter()
print(c)
for ch in a:
    c[ch] = c[ch] + 1
print(c)
结果：
Counter({' ': 4, 's': 2, 'n': 2, 'a': 2, 'o': 2, 'u': 1, 'c': 1, 'k': 1, 'i': 1, 'g': 1, 'd': 1, 'm': 1})

```

# uuid模块

## 概述

```
概述：
    是128位的全局唯一标识符，通常由32字节的字母串表示，它可以保证时间和空间的唯一性，也称为GUID

```

## 原理

```
原理：
    通过MAC地址、时间戳、命名空间、随机数、伪随机数来保证生产的ID的唯一性

```

## 作用

```
作用：
    随机生成字符串，当成token使用，当成用户账号使用，当成订单号使用等(要求不相同字符串)

```

## 算法

```
算法：
    1、uuid1()基于时间戳
        有MAC地址，当前时间错，随机数字，可以保证全球范围内的唯一性。但是由于MAC地址的使用时带来安全问题，局域网中可以使用IP来代替MAC
    2、uuid2()基于分布式计算环境DCE
        算法和uuid1相同，不同的是把时间戳的前四位换位POSIX的UID，实际当中很少使用，注意，Python中没有这个函数
    3、uuid3()基于名字和MD5散列值
        通过计算名字和命名空间的MD5散列值得到的，保证了同一命名空间中不同名字的唯一性，和不同命名空间的唯一性，但同一命名空间的相同名字生成相同的uuid
    4、uuid4()基于随机数
        有伪随机数得到的，有一定重复概率的，这个概率并且是可以计算出来的
    5、uuid5()基于名字和SAH1散列值
        算法和uuid3()相同，不同的是使用SHA1算法
        

```

## 使用经验

```
使用经验：
    1、python中没有基于DCE的，所以uuid2()可以忽略
    2、uuid4()存在概率性重复，由于无映射性，最好不用
    3、如果在全局的分布式环境下，最好使用uuid1()
    4、若名字的唯一性要求，最好使用uuid3()或uuid5()

```

## 用法

```
print(uuid.uuid1())
print(uuid.uuid4())
print(uuid.uuid3(uuid.NAMESPACE_DNS, "sunck"))
print(uuid.uuid3(uuid.NAMESPACE_DNS, "sunck"))
print(uuid.uuid3(uuid.NAMESPACE_DNS, "kaige"))
print(uuid.uuid5(uuid.NAMESPACE_DNS, "sunck"))

```

# base64模块

## 概述

```
概述：用记事本打开图片等文件，看到一坨乱码，因为二进制文件包含很多无法显示的内容。所以想让记事本能处理二进制数据，就需要将二进制字符串转换。base64是一种比较常见的二进制编码方法

```

## 编码原理

```
编码原理：
    一个包含64个字符的数组
    ['A', 'B', ……, 'a', 'b', ……, '0', '1', ……, '+', '/']
    
    对二进制数据进行处理，每个三个字节一组，一组就是3x8=24bit，划为4组，每组正好6bit

    得到4个数字作为索引，然后查表，获得相应的4个字符，就是编码后的字符串
    

```

## 作用

```
作用：
    适用于小段内容的编码，比如数字证书签名，cookie，网页中传输的少量二进制数据
    

```

## 注意

```
注意：base64是一种通过查表的编码方法，不能用于加密，即使修改了字符对照表页不行。

```

## 使用

```
#编码
s1 = b"sunck is a good ma"
print(base64.b64encode(s1))
#解码
s2 = b"c3VuY2sgaXMgYSBnb29kIG1h"
print(base64.b64decode(s2))

```

## 特例

```
#如果要编码的二进制不是3的倍数，怎么办？
#答：base用\x00字节在末尾补足，在编码的末尾加上1个或2个等号表示补了多少个字节,解码时会自动去掉
s3 = b"sunck is a good man"
print(base64.b64encode(s3))

```

```
# 由于标准base64编码后可能出现字符+和/，在URL中就不能直接作为参数
# 提供urlsafe_b64encode编码，保证url的安全，将+和/替换成-和_，提供urlsafe_b64decode进行url安全解码
s4 = b"sunck is a good m~"
print(base64.b64encode(s4))
print(base64.urlsafe_b64encode(s4))

s5 = b"c3VuY2sgaXMgYSBnb29kIG1-"
print(base64.urlsafe_b64decode(s5))

```

```
#由于=字符也可能出现在base64编码中，但是=在url、cookie里面会造成歧义，所以很多base64编码后会把=去掉
s6 = b"abcd"
s8 = base64.b64encode(s6)
print(s8)
#  b"abcd"  -->  b'YWJjZA=='
#  b"abcd"  -->  b'YWJjZA'
s7 = b'YWJjZA=='
print(base64.b64decode(s7))

```

```
#可以自定义编码对照表列表中64个字符的排序，这样可以自定义编码，但是通常情况下没有任何必要

```

# hashlib模块

## 概述

```
hashlib 模块提供了常见的摘要算法，如MD5，SHA1

摘要算法（又称哈希算法、散列算法）：
    原理：它通过一个函数，把任意长度的数据转为一个长度固定的数据串(通常用16进制的字符串表示)

```

## MD5

```
# 最常见的摘要算法，速度快，通常用32位16进制字符串表示
s1 = b"sunck is a good man"
m5 = hashlib.md5()
m5.update(s1)
print(m5.hexdigest())

#如果数据量比较大， 可以分多次调用update，最后的结果是一样的
m6 = hashlib.md5()
m6.update(b'sunck is ')
m6.update(b"a good man")
print(m6.hexdigest())

```

## SHA1

```
#SHA1
# 调用SHA1与调用MD5完全一样，通常用40位16进制字符串表示
s2 = b"sunck is a nice man"
sh1 = hashlib.sha1()
sh1.update(s2)
print(sh1.hexdigest())

```

## 更安全的

```
#更安全的
# SHA256
# SHA512
# 越安全的算法不仅越慢，而且摘要会越长



#有没有两个不同的数据通过hash算法后得到了相同的摘要呢？
#有这种可能性，因为摘要算法是将无限多的数据映射到有限的集合中，如果两个数据的摘要相同，称之为碰撞。可能出现，但是非常渺茫

```

## 总结

```
应用：
    任何允许用户登陆的网站都会存储用户登录的用户名和密码，那么密码一般存储的是原密码的摘要值。
    
    sunck--good明文存到数据中，如果数据库泄露，所有用户信息会暴露
    
    正确的保存口令方式不是存储明文内容，而是存储口令的摘要，当用户登录时，首先会计算用户输入的明文口令的摘要，和数据库中的对比，如果一直说明口令正确，否则一定错误。

```

# hmac模块

```
import  hmac

'''
实现HMAC算法，是用一个key对数据进行“杂凑”后在记性的hash,使用hmac比hash算法更安全，不同的key会产生不同的hash

'''
#对于同一条数据，key不同会得到不同的摘要值
s = b"sunck is a good man"
key = b"secret"
h = hmac.new(key, s, digestmod="MD5")
print(h.hexdigest())

```

# itertools模块

## 无限迭代

```
import itertools
import time
# 无限迭代
# count(start=0, step=1)
# c = itertools.count()
# for i in c:
#     print(i)
#     time.sleep(1)



# cycle(iterable)
# 把传入的一个序列无限重复下去
# cy = itertools.cycle("sunck")
# for i in cy:
#     print(i)
#     time.sleep(1)

# repeat(object[, times])
# 把一个元素无限重复下去，如果提供了第二个参数，就可以指定重复次数
# r = itertools.repeat("sunck", 3)
# for i in r:
#     print(i)
#     time.sleep(1)

```

## 有限迭代

```
# 有限迭代
# 把一组迭代对象串联起来，形成一个更大的迭代器
# chain(*iterables)
# cha = itertools.chain("ABC", "abc")
# for i in cha:
#     print(i)
#     time.sleep(1)
# 把迭代器中相邻的重复元素跳出来放在一起
# g = itertools.groupby("AABBBBccdedFFF")
# for key, value in g:
#     print(key, list(value))
#     time.sleep(1)

```

## 排列组合

```
#全排列
# 从n个不同元素中取出m(m<=n)个元素，按照一定的顺序排成一列，叫做从n个元素中获取m个元素的一个排列。当m==n时，这个排列称为全排列
# itertools.permutations(iterable, length)
# p = list(itertools.permutations([1,2,3,4], 4))
# print(p)
# print(len(p))
'''
5! = 1 * 2 * 3 * 4 * 5
0! = 1
1! = 1
从n个中选m个    n! / (n - m)!
4   1   4!/3!
4   2   4!/2!
4   3   4!/1!
4   4   4!/0!
'''


#组合
# 从n个不同的元素中，任意m(m<=n)个元素为一组，叫做从n个不同元素中取出m个元素的组合
# itertools.combinations(iterable, length)
# c = list(itertools.combinations([1,2,3,4], 3))
# print(c)
# print(len(c))

'''
4   4    1
4   3    4
4   2    6
4   1    4
n!/m!(n-m)!
'''

#排列组合(笛卡尔积)
# itertools.product(*iterable, repeat=1)
# passwds = list(["".join(x) for x in itertools.product("0123456789", repeat=6)])
# print(passwds)
# print(len(passwds))



# passwds = ("".join(x) for x in itertools.product("0123456789QWERTYUIOPASDFGHJKLZXCVBNMqwertyuiopasdfghjklzxcvbnm", repeat=8))
# for i in passwds:
#     print(i)
#     time.sleep(1)
# 暴力破解
# 枚举破解

```

# 安装三方模块

```
'''
Windows
pip  install  模块名
pip  install  模块名==版本号

Linux(超级root用户)  超级用户根本就不可能给你用
pip  install  模块名
pip  install  模块名==版本号

Linux(普通用户)
sudo  pip  install  模块名
sudo  pip  install  模块名==版本号
'''

```

# Pillow模块



```
from PIL import Image

# pip  install  Pillow
# 处理图形图像

im = Image.open("1.jpg")
# 打印图片的信息
# print(im.format, im.size, im.mode)
# 设置图片大小
im.thumbnail((100, 80))
#生成新图片
im.save("2.jpg", "JPEG")

```

# 面向对象

## 什么是面向对象

```
自上而下顺序执行，逐步求精；其程序结构是按功能划分为若干个基本模块，这些模块形成一个树状结构；各模块之间的关系尽可能简单，在功能上相对独立；每一模块内部均是由顺序、选择和循环三种基本结构组成；其模块化实现的具体方法是使用子程序。程序流程在写程序时就已决定。


把数据及对数据的操作方法放在一起，作为一个相互依存的整体——对象。
对同类对象抽象出其共性，形成类。
类中的大多数数据，只能用本类的方法进行处理。
类通过一个简单的外部接口与外界发生关系，对象与对象之间通过消息进行通信。
程序流程由用户在使用中决定。


```

## 理解面向对象

```
面向对象是相对面向过程而言
面向对象和面向过程都是一种思想
面向过程
强调的是功能行为
关注的是解决问题需要哪些步骤 
面向对象
将功能封装进对象，强调具备了功能的对象
关注的是解决问题需要哪些对象 
面向对象是基于面向过程的。
```

## 面向对象特点

```
是一种符合人们思考习惯的思想
可以将复杂的事情简单化
将程序员从执行者转换成了指挥者

完成需求时：
先要去找具有所需的功能的对象来用。
如果该对象不存在，那么创建一个具有所需功能的对象。
```

## 类的定义

```
生活中描述事物无非就是描述事物的名称/属性和行为。如：人有身高，体重等属性，有说话，打架等行为。Python中用类来描述事物也是如此属性：对应类中的成员变量。行为：对应类中的成员方法。定义类其实在定义类中的成员(成员变量和成员方法) 拥有相同（或者类似）属性和行为的对象都可以抽像出一个类
```

## 类的设计

```
只关心3样东西	事物名称（类名）：人（Person）	属性：身高（height）、年龄（age）	行为（功能）：跑（run）、打架（fight）
```

## 访问对象方法

```
# -*- coding:utf-8 -*-

'''
对象方法
    通过实例调用时（无法用类名调用），可以引用类内部的任何属性和方法
    格式：对象名.方法名(参数列表)
    注意：对象方法的第一个参数必须是self，其余参数按顺序排列，调用传参是忽略self
    self：代表一个对象，哪个对象调用的对象方法，那么在方法中self就代表哪个对象


类方法
    无需实例化，用类名调用（可以用对象调用），可以调用类的属性和方法，无法取到普通的对象属性和方法，使用@classmethod定义类方法
    cls：表示类名


静态方法：
    无论用类调用还是用实例调用，都无法获取到类内部的属性和方法，完全独立的一个方法，使用@staticmethod定义


总结：
    类方法效率要比对象方法高，因为类方法无需实例化对象，并且节省内存，当方法中不涉及对象属性和方法时使用
    静态方法一般用作工具方法
'''

class Person(object):
    # 对象方法
    def eat(self, x, y):
        print(self)
        print(self.eat2("a", "b"))
        return "吃%s和%s"%(x, y)
    def eat2(self, x, y):
        return "2吃%s和%s"%(x, y)
    #类方法
    @classmethod
    def run(cls, m):
        print(cls.run2(80))
        return ("跑%d米"%m)
    @classmethod
    def run2(cls, m):
        return ("2跑%d米" % m)
    #静态方法
    @staticmethod
    def play(x):
        return "玩%s"%x
per1 = Person()
per = Person()
print(per, per1)

#调用对象方法
print(per1.eat("苹果", "香蕉"))
#调用类方法
# print(Person.run(200))
#调用静态方法
# print(per.play("球"))
# print(Person.play("麻将"))





class Gongju():
    @staticmethod
    def a():
        pass
    @staticmethod
    def b():
        pass

Gongju.a()
Gongju.b()
```

## 类属性

```
# -*- coding:utf-8 -*-

class Person(object):
    #类属性：可以通过类调用，也可以通过对象调用
    # 当类的对象的属性值都一样时就使用类属性
    name = "lilei"
    age  = 20
    height = 170
    weight = 80

#在初始化对象时，每一个对象的属性值多相同了
per1 = Person()
per2 = Person()
#通过对象访问属性   对象名.属性名
print(per1.name)
print(per2.name)

#每个对象拥有自己的属性
per1.name = "hanmeimei"
print(per1.name)
print(per2.name)

print("-------------------")
print(Person.name)


#问题：使用类创建的所有的对象的属性初始值都一样
```

## 对象的初始状态

```
# -*- coding:utf-8 -*-

# 需求：在创建对象时给每个对象直接赋值属性的初始值

#  __init__()
# 构造方法，在使用类创建实例对象时自动调用，目的是初始化对象内容。

class Person(object):
    # 后期除非定义单例类，否则基本不用写
    def __new__(cls, *args, **kwargs):
        # 调用父类中的__new__方法开辟内存空间
        return super(Person, cls).__new__(cls)

    #类属性
    def __init__(self, name, age, height, weight):
        # 对象属性，只能对象调用
        self.name = name
        self.age = age
        self.height = height
        self.weight = weight
    def say(self):
        # 对象方法中可以调用对象属性
        return "my name is %s, I am %d years old"%(self.name, self.age)

#创建对象时给每个对象的属性赋值
per1 = Person("lilei", 20, 170, 80)
per2 = Person("hanmeimei", 18, 165, 50)

print(per1.name)
print(per2.name)

# print(Person.name) #类中没有name属性，且类名无法调用对象属性


print(per1.say())
print(per2.say())



# 延伸
# __new__()方法：是一个类方法，返回一个对象的实例，在使用类实例化对象时自动调用，目的是在堆区开辟一片内存空间，会在__init__之前调用
# 使用：创建单例类
```

## 析构函数

```
# -*- coding:utf-8 -*-

class Person(object):
    def __init__(self, name, age, height, weight):
        self.name = name
        self.age = age
        self.height = height
        self.weight = weight

    # 析构方法，在释放对象时自动调用
    # 作用：释放一些不必要的内存
    def __del__(self):
        print("object delete")

    def say(self):
        return "my name is %s, I am %d years old"%(self.name, self.age)

per = Person("lilei", 20, 170, 80)
del per
```

## 访问限制

```
# -*- coding:utf-8 -*-

class Person(object):
    # 在python中，变量名类似__xxxx__的，属于特殊变量，特殊变量时可以直接访问的，不是私有变量
    def __init__(self, name, age, height, weight, money):
        self.name = name
        self.age = age
        self.height = height
        self.weight = weight
        # 在python中_xxx变量，这样的实例变量我不是可以直接访问的。但是，按照约定俗成的规定，当看到这样的变量时，意思是虽然我可以被外部直接访问，但是请把我视为私有变量，不要在外部随意访问
        self._temp = 2
        # 特殊变量
        self.__test__ = 1
        #如果要让内部属性不被外部访问，可以把属性的名称前加上两个下划线
        #python中，示例的变量以__开头，就变成了一个私有属性(private)，只能在内部访问，外部无法访问
        #不能再外部直接访问__money的原因是python解释器对外把__money属性改成了_Person__money。所以任然可以用_Person__money来直接访问，但是强烈建议不要这么做，因为不同版本的python解释器可能会把__money改成不同的属性名
        self.__money = money



    #定义公有方法间接访问私有属性
    def getMoney(self):
        return self.__money
    def setMoney(self, money):
        if money >= 0:
            self.__money = money

    def say(self):
        return "my name is %s, I am %d years old"%(self.name, self.age)

per = Person("lilei", 20, 170, 80, 100)
per.age = 18
print(per.age)

# print(per.__money)
#间接访问私有属性
per.setMoney(10)
print(per.getMoney())
# print(per._Person__money) #不建议使用
print(per.__test__)
print(per._temp)
```

## @property

```
# -*- coding:utf-8 -*-

class Person(object):
    def __init__(self, name, age, height, weight, money):
        self.name = name
        self.age = age
        self.height = height
        self.weight = weight
        self.__money = money
    @property
    def money(self):
        return self.__money
    @money.setter
    def money(self, value):
        if value < 0:
            self.__money = 0
        else:
            self.__money = value
    #定义公有方法间接访问私有属性
    # def getMoney(self):
    #     return self.__money
    # def setMoney(self, money):
    #     if money < 0:
    #         self.__money = 0
    #     else:
    #         self.__money = money
    def say(self):
        return "my name is %s, I am %d years old"%(self.name, self.age)

per = Person("lilei", 20, 170, 80, 100)

# print(per.getMoney())
# per.setMoney(10)
# print(per.getMoney())

per.age = 15
print(per.age)

print("-------------")
#向让访问私有属性的方式类似访问普通属性，需要使用@property
#让私有属性可以使用点语法
print(per.money)  #相当于执行money()方法
per.money = -10
print(per.money)
```

## 动态给实例添加属性和方法、__slots__槽

```
# -*- coding:utf-8 -*-
class Person(object):
    __slots__ = ("name", "age", "height", "weight", "money", "run")
    def __init__(self, name, age, height, weight):
        self.name = name
        self.age = age
        self.height = height
        self.weight = weight
    def say(self):
        return "my name is %s, I am %d years old"%(self.name, self.age)

per1 = Person("lilei", 20, 170, 80)
per2 = Person("hanmeimei", 18, 165, 50)
print(per1.say())

#实例化一个对象后，可以给对象绑定任何的属性和方法，这就是动态语言的灵活性
#如果属性不存在，则变为增加属性
per1.money = 100
print(per1.money)
#增加方法
def run(self):
    print("run")
from types import MethodType
per1.run = MethodType(run, per1)
per1.run()
#注意：给一个实例对象绑定的属性和方法对另一个实例对象没有影响
# print(per2.money)


#需求：给所有的实例都绑定属性和方法
#解决：给类绑定就可以了
#注意：不仅仅给已存在的对象会绑定，未创建的对象也绑定了
Person.faceValue = 100
def play(self):
    print("play")
Person.play = play
print(per1.faceValue, per2.faceValue)
per1.play()
per2.play()
per3 = Person("laowang", 50, 167, 60)
print(per3.faceValue)



#思考：想限制实例的属性，不让对象随意添加属性，只能添加我们规定一些属性
#解决：在定义类时，顶一个特殊属性__slots__，限制该类实例能添加的属性
# per1.score = 100
```

## 单例

### 概述

```
# -*- coding:utf-8 -*-

'''
单例：是一种软件设计模式，该模式的主要目的是确保一个类只有一个实例存在

实现单例的方式：
    1、使用模块
    2、使用__new__
    3、使用装饰器
    4、使用元类

'''
```

### 使用--__new__--()实现单例

```
# -*- coding:utf-8 -*-

class Card(object):
    def __new__(cls, *args, **kwargs):
        # 每一次实例化的时候，我么都只返回instance同一个对象
        if not hasattr(cls, "instance"):
            cls.instance = super(Card, cls).__new__(cls)
        return cls.instance


card1 = Card()
card1.passwd = "666666"
card2 = Card()
print(card2.passwd)
print(card1 is card2)
```

### 使用装饰器实现单例

```
# -*- coding:utf-8 -*-

def singleton(cls):
    instances = {}
    def getinstance(*args, **kwargs):
        if cls not in instances:
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]
    return getinstance


@singleton
class Card(object):
    pass
@singleton
class Person(object):
    pass


c1 = Card()
c2 = Card()
print(c1 is c2)

p1 = Person()
p2 = Person()
print(p1 is p2)
```

## 重写--repr--和--str--方法

```
# -*- coding:utf-8 -*-


class Person(object):
    #重写：将继承的方法重写写一遍，在原有的功能基础上添加一些新的功能
    def __init__(self, name, age, height, weight):
        self.name = name
        self.age = age
        self.height = height
        self.weight = weight
    def say(self):
        return "my name is %s, I am %d years old"%(self.name, self.age)
    #需求：打印该类型的对象时，想打印出对象的各个属性值
    #解决：重写__str__方法
    #__str__()方法：在调用print打印对象时自动调用

    #是显示给用户的
    def __str__(self):
        return "name:%s\nage:%d\nheight:%.2f\nweight:%.2f"%(self.name, self.age, self.height, self.weight)
    #是给机器用的，在python解释器里直接敲对象后回车自动调用
    def __repr__(self):
        return "name:%s\nage:%d\nheight:%.2f\nweight:%.2f"%(self.name, self.age, self.height, self.weight)

per = Person("lilei", 20, 170, 80)
print(per)
```

# 异常处理、调试、测试

## 错误处理

```
# -*- coding:utf-8 -*-



'''概述

在程序运行过程中，总会遇到各种各样的错误，有的错误时编程代码有问题造成的，这种错误通常称为BUG，BUG是必须修复的。有的错误是用户输入造成的，这种错误的可以通过检查用户的输入来做响应处理。还有一种错误时完全无法在程序运行过程中预测的，比如写文件的时候，磁盘满了，写不进去了，再比如从网络中抓取数据，突然断网了，通常这种情况称为异常，在程序中必须要处理的，否则程序会因各种问题而退出
'''



# 遇到错误，最原始的方式解决方法是事先约定一个错误代码，这样就知道是否有错，在操作系统提供的调用中非常常用
'''
缺陷：
    1、函数本身返回的数据与错误码会混在一起，需要大量的判断是否出错
    2、一旦出错，要一级一级上报，直到某个函数可以处理
'''

#错误代码
# print(10 / 0)


#需求：当程序遇到错误时，不让程序结束，而是越过错误继续向下执行
'''try……except……else语句
格式：
    try:
        语句t
    except 错误表示码 as e:
        语句1
    except 错误表示码 as e:
        语句2
    ……
    except 错误表示码 as e:
        语句n
    else:
        语句e
        
        
作用：用来检测try语句块中的错误，从而让except语句捕获异常并处理
逻辑：
    1、如果try后的“语句t”执行时发生异常，就调回到执行try并执行一个匹配该异常的except子句，异常处理结束，就结束整个try语句(除非处理异常时又引发新的异常)
    2、果try后的“语句t”执行时发生异常，但是却没有匹配的except子句，异常提交到上一层try，或者到程序的最上层
    3、如果try后的“语句t”执行时没有发生异常，就不会匹配except，如果有else语句，则执行语句e，最后结束整个try语句
'''
# try:
#     try:
#         print(10 / 1)
#     except AttributeError as e:
#         print(str(e))
#     else:
#         print("没有异常")
# except ZeroDivisionError as e:
#     print("-----------")
# print("sunck is a good man")

# 特殊使用
#1、使用except而不带任何错误类型，捕获任何异常
# try:
#     print(10 / 1)
# except:
#     print("有问题")
# else:
#     print("没有异常")

#2、使用except而带有多种异常类型，同时匹配多种异常
# try:
#     print(10 / 1)
# except (AttributeError, ZeroDivisionError) as e:
#     print(str(e))
# else:
#     print("没有异常")


#使用注意项
#1、python中的错误实际上是类，所有的错误类型都继承自BaseException，所以在使用时注意父类会将子类异常一网打尽
# try:
#     print(10 / 0)
# except BaseException as e:
#     print("----------1")
# except ZeroDivisionError as e:
#     print("----------2")

#2、跨越多层调用，main里调用f2，f2里调用f1，在f1里出错，只要在main里捕获就可以处理了
# def f1(s):
#     return 10 / s
# def f2(s):
#     return f1(s) + 1
# def main():
#     try:
#         f2(0)
#     except ZeroDivisionError as e:
#         print(str(e))
# main()
# print("sunck is a good man")


'''try……except……finally语句
作用：无论try语句块是否发生异常，都将执行finally子句
格式：
    try:
        语句t
    except 错误表示码 as e:
        语句1
    except 错误表示码 as e:
        语句2
    ……
    except 错误表示码 as e:
        语句n
    finally:
        语句f

'''
try:
    print(10 / 1)
except ZeroDivisionError as e:
    print("----------2")
finally:
    print("**********")
```

## 调试（print）

```
# -*- coding:utf-8 -*-

# 写好的代码能直接运行的概率非常小，总会在不经意间出现更重各样的BUG，有的BUG很简单，看看错误提示就能修改，但是有的BUG分复杂，需要一些调试手段来发现并解决

def func(x):
    print("x = %d"%x)
    return 10 / x

func(0)


# 缺点：将来得删除调试的print，运行结果也会包含一些垃圾信息
```

## 调试（断言）

```
# -*- coding:utf-8 -*-

# 使用：凡是用print来辅助调试的 地方，都可以换成断言(assert)语句

#逻辑：当程序执行到assert语句时，首先计算第一个表达式的值，如果表达式的值为真则继续向下执行，否则断言失败，assert语句会抛出AssertionError异常，异常的信息为第二个表达式的值

#缺点：如果将所有的print换成assert也好不到哪里去

#优点：在启动程序时可以通过命令添加-O参数可以关闭assert

def func(x):
    assert x != 0, "x is zero"
    return 10 / x

func(0)
```

## 调试（logging）

```
# -*- coding:utf-8 -*-
import logging
#配置输出级别
logging.basicConfig(level=logging.INFO)
'''
CRITICAL = 50
FATAL = CRITICAL
ERROR = 40
WARNING = 30
WARN = WARNING
INFO = 20
DEBUG = 10
NOTSET = 0

'''

#使用：把print替换为logging也可以，和assert相比logging不会抛出错误，并且可以输出到文件


def func(x):
    logging.info("x = %d"%x)
    return 10 / x

func(0)
```

## 调试（pdb）

```
# -*- coding:utf-8 -*-

#使用：python的调试器，让程序已单步方式允许(一句一句的运行)，可以随时查看运行动态

#以pdb方式调试代码，需要黑屏启动  python  -m  pdb  文件名


'''调试命令
n：单步执行代码
p 变量名：查看变量
q：退出调试
'''

#缺点：麻烦，如果有10000代码，认为错误可能出现在9000行，需要运行到9000行才行

print("-------------1")
a = 1
print("-------------2")
print("-------------3")
b = 2
print("-------------4")
print("-------------5")
print("-------------6")
print("-------------7")
c = 3
n = 0
print(10 / n)
print("-------------8")
print("-------------9")
```

## 调试（pdb的自定义开始断点）

```
# -*- coding:utf-8 -*-

#使用：python的调试器，让程序已单步方式允许(一句一句的运行)，可以随时查看运行动态

#以pdb方式调试代码，需要黑屏启动  python  -m  pdb  文件名


'''调试命令
n：单步执行代码
p 变量名：查看变量
q：退出调试
'''

#缺点：麻烦，如果有10000代码，认为错误可能出现在9000行，需要运行到9000行才行

print("-------------1")
a = 1
print("-------------2")
print("-------------3")
b = 2
print("-------------4")
print("-------------5")
print("-------------6")
print("-------------7")
c = 3
n = 0
print(10 / n)
print("-------------8")
print("-------------9")
```

调试（IDE断点）

```
# -*- coding:utf-8 -*-

print("-------------1")
a = 1
print("-------------2")
print("-------------3")
b = 2
print("-------------4")
print("-------------5")
print("-------------6")
print("-------------7")
c = 3
n = "0"
n = int(n)
print(10 / n)
print("-------------8")
print("-------------9")
```

## 文档测试

```
# -*- coding:utf-8 -*-
import doctest
#该模块可以直接提取注释中的代码并执行测试


def mySum(x, y):
    #doctest严格按照python交互式命令的输入和输出来判断测试结果是否正确
    '''
    >>> print(mySum(1, 2))
    3
    '''
    return x + y
print("sunck good")
doctest.testmod()
```

# 对文件的操作

## 读文件

```
# -*- coding:utf-8 -*-
'''
过程：
    1、找到文件
    2、打开文件
    3、读取文件内容
    4、关闭文件
'''


#找到文件、打开文件
filePath = r"C:\Users\xlg\Desktop\gp01\day12\code\sunck.txt"
'''
原型：
    def open(file, mode='r', buffering=None, encoding=None, errors=None, newline=None, closefd=True)
参数：
    file：要打开文件的路径
    mode：打开方式
    encoding：编码方式
    errors：错误处理
返回值：
    文件描述符(本质就是一个引用)，通过文件描述符可以操作文件
'''
'''打开方式
r     以只读方式打开文件，文件的引用将会放在文件开头
rb    以二进制格式打开只读文件，文件的引用将会放在文件开头
r+    以读写方式打开文件，文件的引用将会放在文件开头
w     以只写方式打开文件，如果该文件已经存在，则将其内容覆盖，如果不存在则会创建文件
wb    以二进制格式打开只写文件，如果该文件已经存在，则将其内容覆盖，如果不存在则会创建文件
w+    以读写方式打开文件，如果该文件已经存在，则将其内容覆盖，如果不存在则会创建文件
a     打开一个文件用于追加，如果该文件已经存在，文件的引用将会放在文件的末尾，也就是说新的内容添加到已有内容之后。果不存在则会创建文件进行写入
a+    打开一个文件用于读写，如果该文件已经存在，文件的引用将会放在文件的末尾，也就是说新的内容添加到已有内容之后。果不存在则会创建文件进行写入
'''

#打开普通文件
fp = open(filePath, "r")
#打开二进制文件
# fp = open(filePath, "rb")
#打开指定编码格式的文件
# fp = open(filePath, "rb", encoding="GBK")
#错误处理：直接忽略
# fp = open(filePath, "rb", encoding="utf-8", errors="ignore")




#读取文件内容

#1、读取文件全部内容
# str1 = fp.read()
# print(str1)

#2、读取指定字节数
# str2 = fp.read(12)
# print("*"+str2+"*")

#3、读取整行，包括"\n"字符
# str3 = fp.readline()
# print(str3+"*")

#4、读取指定字节数
# str3 = fp.readline(12)
# print("*"+str3+"*")

#5、读取所有行并返回列表
# list4 = fp.readlines()
# print(list4)
# print(type(list4))

#读取文件的原理是从文件描述符的位置向后读取
print("-------------", fp.tell())
fp.read()
#查看文件描述符的位置
print("-------------", fp.tell())
#修改文件描述符的位置
fp.seek(1)
str5 = fp.read(12)
print("*"+str5+"*")
str6 = fp.read(2)
print("*"+str6+"*")


#关闭文件：文件使用完后必须关闭，因为文件对象会占用操作系统的资源，并且操作系统同一时间能打开的文件的数量是有限的
fp.close()
```

## 读文件的完整过程

```
# -*- coding:utf-8 -*-


try:
    fp = open("sunck.txt", "r")
    #操作文件
finally:
    if fp:
        fp.close()
```

## 读文件的简写方式



```
# -*- coding:utf-8 -*-


with open("sunck.txt", "r") as fp:
    print(fp.read())
```

## 写文件

```
# -*- coding:utf-8 -*-
import time

'''写文件过程
1、找到文件
2、打开文件
3、将内容写入缓冲区，此时内容没写写入文件
4、刷新缓冲区，直接把缓冲区的数据立刻写入文件
    刷新缓冲区的方式：
        a、程序结束
        b、关闭文件
        c、手动刷新
        d、遇到\n
        e、缓冲区满了
5、关闭文件
'''

filePath = "sunck.txt"
fp = open(filePath, "a")

# 将内容写入缓冲区
fp.write("sunck is a good man!")
# 刷新缓冲区
fp.flush()
# time.sleep(5)

fp.close()



#简单方式
# with open("sunck.txt", "w") as fp1:
#     fp1.write("asd")
```

## 编码与解码

```
# -*- coding:utf-8 -*-

# 编码
with open("sunck.txt", "wb") as f1:
    info = "sunck is a nice man!凯"
    info = info.encode("utf-8")
    print(info)
    f1.write(info)


# 解码
with open("sunck.txt", "rb") as f2:
    info = f2.read()
    print(info)
    print(type(info))
    info = info.decode("utf-8")
    print(info)
    print(type(info))
```

## StringIO和BytesIO

```
# -*- coding:utf-8 -*-
from io import StringIO
from io import BytesIO

#StringIO
#作用：数据的读写不一定都是文件，也可以在内存中读写，作用是在内存中读写字符串
#写
# fp = StringIO()
# fp.write("sunck")
# fp.write(" ")
# fp.write("is")
# fp.write(" ")
# fp.write("a")
# fp.write(" ")
# fp.write("good")
# fp.write(" ")
# fp.write("man!")
# #获取写入的内容
# info = fp.getvalue()
# print(info)


#读
# fp = StringIO("good\nnice\nhandsome\n")
# print(fp.read())
# print(fp.readline())



#BytesIO
#作用：StringIO只能操作字符串，BytesIO可以操作二进制数据，作用是在内存中读写bytes
#写
# fp = BytesIO()
# fp.write("凯哥".encode("utf-8"))
# print(fp.getvalue())

# 读
# fp = BytesIO(b'\xe5\x87\xaf\xe5\x93\xa5')
# print(fp.read().decode("utf-8"))
```

## os模块

```
# -*- coding:utf-8 -*-
import os

#作用：包含了普遍的操作系统功能，提供了非常丰富的方法来处理文件和目录


#使用


# 操作系统的类型
# nt       Windows
# posix    Linux、Unix
print(os.name)

# 获取详细的系统信息，linux、Unix下使用
# print(os.uname())

# 获取系统中的环境变量
print(os.environ)
# 获取指定环境变量的值
print(os.environ.get("ALLUSERSPROFILE"))

# 放回当前目录   .
print(os.curdir)

# 得到当前工作目录的绝对路径
print(os.getcwd())

# 返回指定目录下的所有文件和目录   listdir([path]),没有path返回当前工作目录下的
print(os.listdir(r"C:\Users\xlg\Desktop\gp01"))

#创建指定目录
# os.mkdir(r"C:\Users\xlg\Desktop\gp01\day14")

#删除目录
# os.rmdir(r"C:\Users\xlg\Desktop\gp01\day14")

#获取文件属性
# print(os.stat(r"C:\Users\xlg\Desktop\gp01\1、基础内容简介.txt"))

#重命名
# os.rename(r"C:\Users\xlg\Desktop\gp01\day13\code\sunck.txt",r"C:\Users\xlg\Desktop\gp01\day13\code\kaige.txt")

#删除普通文件
# os.remove(r"C:\Users\xlg\Desktop\gp01\day13\code\kaige.txt")

#运行shell命令
# os.system("notepad")
# os.system("shutdown -s -t 10")
# os.system("shutdown -a")




#操作文件和目录的函数一部分放在os模块中，还有一部分放在os.path中

#返回指定路径的绝对路径
print(os.path.abspath("."))
#拼接路径
print(os.path.join(r"C:\Users\xlg\Desktop\gp01\day13\abc", "kaige.txt"))
#拆分路径
print(os.path.split(r"C:\Users\xlg\Desktop\gp01\day13\abc\kaige.txt"))
#获取文件扩展名
print(os.path.splitext(r"C:\Users\xlg\Desktop\gp01\day13\abc\kaige.txt"))
#判断是否是目录（得存在），是返回True, 否则返回False,
print(os.path.isdir(r"C:\Users\xlg\Desktop\gp01\day13\code"))
#判断普通文件是否存在，存在返回True， 否则返回False
print(os.path.isfile(r"C:\Users\xlg\Desktop\gp01\day13\code\kaige.txt"))
#判断文件和目录是否存在
print(os.path.exists(r"C:\Users\xlg\Desktop\gp01\day13\abc"))
#判断是否是绝对路径,（不论是否存在）
print(os.path.isabs(r"C:\Users\xlg\Desktop\gp01\day13\abc"))


#获取文件大小
print(os.path.getsize(r"C:\Users\xlg\Desktop\gp01\day13\code\kaige.txt"))



#获取文件名
print(os.path.basename(r"C:\Users\xlg\Desktop\gp01\day13\code\kaige.txt"))
#得到文件路径
print(os.path.dirname(r"C:\Users\xlg\Desktop\gp01\day13\code\kaige.txt"))
```

## list、tuple、dict、set的文件操作

```
# -*- coding:utf-8 -*-

# 持久保存对象，将list、tuple、dict、set等数据进行序列化存储到文件
import pickle

# users = {"666666":{"name":"sunck","idCard":"666666","cards":{"1":{"cardId":"1","passwd":"1","money":"1"}}}}
# with open("users.txt", "wb") as fp:
#     pickle.dump(users, fp)


# with open("users.txt", "rb") as fp:
#     users = pickle.load(fp)
# print(users)
# print(type(users))
```

# 递归、深度遍历、广度遍历算法

## 递归

```
# -*- coding:utf-8 -*-

'''
递归：
    1、自身调用自身形成递归
    2、两个函数相互调用形成递归
递推：
'''


#递归调用：一个函数，调用自身，称为递归调用
#递归函数：一个会调用自身的函数称为递归函数
#注意：凡是循环能干的事，递归都能干

'''
递归三步走
1、写出临界条件
2、假设当前函数已经能用，调用自身计算上一次的结果，在求出本次结果
3、找这一次和上一次的关系
'''


#在以后的开发中尽量避免使用递归，容易造成内存泄露，效率也会偏低

#1 + 2 + 3 + 4 + 5
def func(num):
    if num == 1:
        return 1
    return func(num - 1) + num

print(func(5))

'''
func(5)  
func(4) + 5
func(3) + 4 + 5
func(2) + 3 + 4 + 5
func(1) + 2 + 3 + 4 + 5
1 + 2 + 3 + 4 + 5
'''
```

## 递归遍历目录

```
# -*- coding:utf-8 -*-

import os
def traverseDir(path, treeShow = ""):
    filesList = os.listdir(path)
    for filename in filesList:
        absPath = os.path.join(path, filename)
        if os.path.isdir(absPath):
            print(treeShow+"目录："+filename)
            traverseDir(absPath, treeShow + "    ")
        else:
            print(treeShow+"文件："+filename)
traverseDir(r"C:\Users\xlg\Desktop\gp01\day13\file")
```

## 栈模拟递归遍历目录（深度遍历）

```
# -*- coding:utf-8 -*-


def traverseDir(path):
    import os
    myStack = []

    myStack.append((path,0))

    while len(myStack) != 0:
        #出栈
        item = myStack.pop()
        filePath = item[0]
        num = item[1]
        treeShow = "    " * num
        filesList = os.listdir(filePath)
        for fileName in filesList:
            absPath = os.path.join(filePath, fileName)
            if os.path.isdir(absPath):
                #压栈
                print(treeShow + "目录：" + fileName)
                myStack.append((absPath, num+1))
            else:
                print(treeShow + "文件：" + fileName)

traverseDir(r"C:\Users\xlg\Desktop\gp01\day13\file")
```

## 队列模拟递归遍历目录（广度遍历）

```
# -*- coding:utf-8 -*-


def traverseDir(path):
    import os
    from collections import deque

    queue = deque([])

    #进队
    queue.append((path, 0))

    while len(queue) != 0:
        #出队
        item = queue.popleft()
        filePath = item[0]
        num = item[1]
        treeShow = "    " * num
        filesList = os.listdir(filePath)

        for fileName in filesList:
            absPath = os.path.join(filePath, fileName)
            if os.path.isdir(absPath):
                #进队
                print(treeShow + "目录：" + fileName)
                queue.append((absPath, num + 1))
            else:
                print(treeShow + "文件：" + fileName)



traverseDir(r"C:\Users\xlg\Desktop\gp01\day13\file")
```

# 正则

## 为什么使用正则

```
# -*- coding:utf-8 -*-

#输入一串字符串，判断是否是手机号码

def isPhone(phone):
    # 全都是数字字符
    # 长度为11
    # 以130、131等开头
    pass


# 使用正则会让这个问题简单化
```

## re模块概述

```
# -*- coding:utf-8 -*-


'''
python自1.5版本起增加了re模块，该模块提供了Perl风格的正则表达式模式

re模块使python语言拥有了全部的正则表达式功能


三个函数：
    match()
    search()
    findall()
'''
```

## match函数

```
# -*- coding:utf-8 -*-
import re

r'''
原型：match(pattern, string, flags=0)

功能：尝试从字符串string的起始位置匹配一个pattern模式，如果匹配成功，返回正则对象，否则返回None。
返回的正则对象中有：
start()：匹配到的开始索引、end()：匹配到的结束索引、string：匹配的字符串、groups（）：返回括号中匹配到的数据（单个）、span（）：返回匹配到的起始索引、group（）：返回匹配到的整体、endpos（）

参数：
    pattern：匹配的正则表达式
    string：要匹配的字符串
    flags：标志位，用于控制正则表达式的匹配方式(是否大小写、是否多行匹配等等)
        re.I：使匹配对大小写不敏感
        re.L：做本地化识别匹配
        re.M：多行匹配，影响^和$
        re.S：使.匹配包括换行符在内的所有字符
        re.U：根据Unicode字符集解析字符，影响\w、\W、\b、\B
        re.X：通过给予我们功能灵活的格式以便更好的理解正则表达式
'''

print(re.match("www", "www.sunck.wang"))
print(re.match("www", "sunck.wangwww"))
print(re.match("www", "Www.sunck.wang", re.I))
ret = re.match("www", "www.sunck.wang")
print(ret.span())
```

## search函数

```
# -*- coding:utf-8 -*-

import re

'''
原型：search(pattern, string, flags=0)

功能：扫描整个字符串string，并返回第一个成功的匹配

参数：

'''
print(re.search("www", "www.sunck.wang"))
print(re.search("www", "awww.sunck.wangwww"))
```

## findall函数

```
# -*- coding:utf-8 -*-
import re

'''
原型：findall(pattern, string, flags=0)
功能：扫描整个字符串string并返回结果的列表
'''
print(re.findall(r"ww[12345]","ww1.suwwwnck.wwwaaang"))

返回值：
如果成功，返回匹配到数据的列表（[('ww', 'w'), ('ww', 'w')]），如果不成功，返回空链表
# ww1  ww2  ww3   ww4  ww5
```

## 正则表达式元字符

```
# -*- coding:utf-8 -*-
import re

# 1、匹配单个字符与数字
'''
.    匹配除换行符以外的任意字符，当flags被指定为re.S时可以匹配包含换行符以内的所有字符，如果没有指定，那么不包含换行符[.\n]
[]   里面是字符的集合，匹配[]里面任意一个字符
[0123456789]   匹配任意一个数字字符
[0-9]    匹配任意一个数字字符
[a-z]    匹配任意一个小写英文字母字符
[A-Z]    匹配任意一个大写英文字母字符
[a-zA-Z] 匹配任意一个字母字符
[a-zA-Z0-9]  匹任意一个数字或字母字符
[^sunck]   []里的^称为脱字符，表示非，匹配不在[]里的任意一个字符。匹配除了 "s"  "u"  "n"  "c"  "k"以外任意一个字符
\d     匹配任意一个数字字符  [0-9]
\D     匹配任意一个非数字符  [^0-9]
\w     匹配字母、下划线、数字   [0-9a-zA-z_]
\W     匹配非字母、下划线、数字   [^0-9a-zA-z_]
\s     匹配空白符(空格、换页、换行、回车、制表等)  [ \f\n\r\t]
\S     匹配非空白符    [^ \f\n\r\t]
'''








# 2、锚字符
'''
^   行首匹配，和[]中的^不是一个意思

$   行尾匹配
'''
# print(re.search(r"^sunck$", "sunck"))


# 2、边界字符
r'''
\A   匹配字符串开始，和^的区别是\A只匹配整个字符的开头，即使在re.M模式下，也不会匹配其它的行首
\Z   匹配字符结尾，和$的区别是\Z只匹配整个字符的结尾，即使在re.M模式下，也不会匹配其它的结尾
\b   匹配一个单词的边界，指单词和空格的位置
\B   匹配非单词边界，
'''
s = '''sunck is a good man
sunck is a nice man
sunck is a cool man
'''
# print(re.findall(r"\Asunck", s, re.M))
# print(re.findall(r"ck\b", "sunck"))
# print(re.findall(r"ck\b", "suckn"))
# print(re.findall(r"ck\B", "sunck"))
# print(re.findall(r"ck\B", "suckn"))






# 4、匹配多个字符
'''以下使用的x、y、z均为假设的普通字符,n、m表示一个数字，不是正则表达是的元字符
(xyz)   匹配括号内的xyz(作为一个整体去匹配)
x?      匹配0个或1个x，非贪婪匹配
x*      匹配0个或任意多个x
x+      匹配至少一个x
x{n}    匹配确定n个x，n是非负整数
x{n,}   匹配至少n个x
x{n,m}  匹配至少n个，最多m个x
x|y     |表示或，匹配x或y
'''
print(re.findall(r"(sunck)", "sunck is a good man!sunck is a ncie man"))
print(re.findall(r"a?", "abbbaabbaaa"))
print(re.findall(r"a*", "aaa"))
print(re.findall(r"P|python", "pythonaaaPython"))
```

## 切分字符串

```
# -*- coding:utf-8 -*-
import re


str1 = "sunck  is a   good     man!"
# print(str1.split(" "))

print(re.split(r" +", str1))
```

## finditer函数

```
# -*- coding:utf-8 -*-
import re

'''
原型：finditer(pattern, string, flags=0)

作用：类似findall，返回一个迭代器

区别：findall返回所有匹配的字符，并存为一个列表，如果数据过多，占用内存。而finditer并不是直接返回找到的所有字符从，而是返回一个迭代器，可以通过next迭代

'''
str1 = "sunck is a good man! sunck is a good man"
res = re.finditer(r"(sunck)", str1)
print(res)
print(type(res))
for x in res:
    print(x)
```

## 字符串的替换和修改

```
# -*- coding:utf-8 -*-

import re

'''
sub(pattern, repl, string, count=0, flags=0)
subn(pattern, repl, string, count=0, flags=0)

作用：在目标字符串string中查找匹配的pattern模式字符，在把它们替换成指定的repl字符串，可以指定最多替换count次，否则替换所有

参数：
   pattern：正则表达式
   repl：指定用来替换的字符串
   string：目标字符串
   count：最多替换次数
   flags：

区别：sub返回一个被替换的字符串，subn返回一个元组，元组的第一个元素为被替换的字符串，第二个元素为发生了多少次替换

'''
str1 = "sunck is a good man!sunck is a nice man!sunck is a cool man"
print(re.sub(r"(sunck)", "kaige", str1))
print(re.subn(r"(sunck)", "kaige", str1))
```

## 分组

```
# -*- coding:utf-8 -*-
import re

'''
概念：除了简单的判断是否匹配之外，正则表达式还有提取子串的功能，用()表示的就是要提取的分组
'''

 
#组的排序：从外到内，从左到右
print(m)
# 使用组序号获取匹配的字符串，0表示原数据
print(m.group(0))
#根据名字获取组内容
print(m.group("quhao"))
print(m.group(1))
print(m.group("phone"))
print(m.group(2))
# 查看匹配的各组的数据
print(m.groups())
```

## 编译

```
# -*- coding:utf-8 -*-
import re

'''
概念：当在python中使用正则表达式时，re模块会做两件事情，一件是编译正则表达式，如果表达式的字符串本身不合法，会报错。一件是用编译后的正则表达式取匹配字符串


优点：如果一个正则表达式要使用几千遍，每一次都会编译，处于效率的考虑进行正则表达式的编译，这样就不用每次都编译，节省了编译时的时间，提升了效率

'''

#编译正则表达式，得到的是一个正则表达式对象
re_phone = re.compile(r"(?P<quhao>\d{3})-(?P<phone>\d{8})", re.I)



print(re_phone.findall("010-09876543aa010-98789098"))
'''
findall(self, string, pos=0, endpos=-1)
finditer(self, string, pos=0, endpos=-1)
match(self, string, pos=0, endpos=-1)
search(self, string, pos=0, endpos=-1)
'''

```

## 贪婪匹配

```
# -*- coding:utf-8 -*-
import re

'''
概念：匹配尽可能多的字符
'''


print(re.match(r"^(\d+?)(0*)$", "120345000").groups())


'''尽可能匹配少的字符串
*?
+?
??
'''


print(re.findall(r"//*.*/*/", r"/* part1 */ /* part2 */"))
res = re.findall(r"//*.*?/*/", r"/* part1 */ /* part2 */")
print(res)

```

# 多任务

## 多任务原理

```
# -*- coding:utf-8 -*-


'''
什么叫多任务：操作系统可以同时运行多个任务，现代的操作系统比如Windows、Mac OS X、Linux、Unix等都是支持多任务的系统
'''

#单核CPU实现多任务的原理：找图去看



#多核CPU实现多任务的原理：找图

# 为什么要实现多任务：想效率高，不卡顿


'''实现多任务的方式
    1、多进程模式：启动多个进程，每个进程虽然只有一个线程，但是多个进程可以一起执行多个任务
    2、多线程模式：启动一个进程，在一个进程的内部启动多个线程，这样多个线程也可以一起执行多个任务
    3、多进程+多线程：启动多个进程，每个进程再启动多个线程
    4、协程
    5、多进程+协程
'''

```

## 进程的概念

```
# -*- coding:utf-8 -*-

'''
什么是进程：进程（Process）是计算机中的程序关于某数据集合上的一次运行活动，是系统进行资源分配和调度的基本单位，是操作系统结构的基础。在早期面向进程设计的计算机结构中，进程是程序的基本执行实体；在当代面向线程设计的计算机结构中，进程是线程的容器。程序是指令、数据及其组织形式的描述，进程是程序的实体


对于操作系统来说，一个任务就是一个进程。比方说打开浏览器就是启动一个浏览器的进程，在打开一个记事本就启动一个记事本进程，如果打开两个记事本就启动两个记事本进程。
'''

```

## 单任务现象

```
# -*- coding:utf-8 -*-

from time import sleep


def run():
    while True:
        print("sunck is a good man!")
        sleep(1)

if __name__ == "__main__":
    while True:
        print("kaige is a nice man")
        sleep(1.2)
    # 不会执行到run方法，只有上面的while循环结束才行
    run()

```

## 启动进程实现多任务

```
# -*- coding:utf-8 -*-



from multiprocessing import Process
from time import sleep

'''
multiprocessing模块
1、跨平台的多进程模块
2、提供了一个Process类代表一个进程对象
'''

def run(name, description):
    while True:
        print("%s is a %s man!"%(name, description))
        sleep(1)

if __name__ == "__main__":
    #程序启动的进程称为主进程(父进程)

    #创建进程(子进程)
    p = Process(target=run, args=("sunck", "handsome"))
    #启动子进程
    p.start()

    while True:
        print("kaige is a nice man")
        sleep(1.2)

```

## 父子进程的先后顺序

```
# -*- coding:utf-8 -*-

from multiprocessing import Process
from time import sleep

def run():
    print("启动子进程")
    sleep(3)
    print("结束子进程")

def run2():
    print("启动子进程2")
    sleep(3)
    print("结束子进程2")

if __name__ == "__main__":
    print("启动主进程")

    p = Process(target=run)
    p.start()

    p2 = Process(target=run2)
    p2.start()

    #主进程的结束不能影响子进程，随意可以等待子进程结束在结束主进程
    #等待子进程结束，才能继续执行主进程
    #后期主进程主要做的是调度相关的工作，不具体负责业务逻辑
    p.join()
    p2.join()
    print("结束主进程")

```

## 全局变量在多个进程中不能共享

```
# -*- coding:utf-8 -*-

from multiprocessing import Process
from time import sleep

money = 10

def run1():
    print("启动子进程1")
    global money
    print("run1---1-", money)  #0
    sleep(3)
    print("run1---2-", money)  #20  真实为0
    money = 30
    print("run1---3-", money)  #30
    print("结束子进程2")

def run2():
    print("启动子进程2")
    global money
    print("run2---1-", money) #0
    sleep(1)
    money = 20
    print("run2---2-", money) #20
    print("结束子进程2")

if __name__ == "__main__":
    print("启动主进程")

    #在创建子进程时会将主进程的资源拷贝到子进程中，子进程单独有一份主进程中的数据。相互不影响
    p1 = Process(target=run1)
    p2 = Process(target=run2)
    p1.start()
    p2.start()

    p1.join()
    p2.join()
    print("money = %d"%money) #30  真实为0
    print("结束主进程")

```

## 启动大量子进程

```
# -*- coding:utf-8 -*-
import os
import time
import random

from multiprocessing import Process, Pool

def run(name):
    # os.getpid()获取当前进程的进程ID
    print("子进程%s启动--%s"%(name, os.getpid()))
    t1 = time.time()
    time.sleep(random.random()*5)
    t2 = time.time()
    print("子进程%s结束--%s--耗时%.2f" % (name, os.getpid(), t2-t1))

if __name__ == "__main__":
    print("启动父进程")

    #进程池
    #表示可以同时执行的进程数量
    #由于Pool的默认值为CPU的核心数量，如果有4个核心，则至少需要子进程才能看到等待的效果
    pool = Pool(4)
    for i in range(3):
        # 创建进程放入进程池中同意管理
        pool.apply_async(run, args=(i,))


    # 进程池对象调用join之前必须先调用close，调用close之后就不能向进程池中添加进程了
    pool.close()
    #Pool对象调用join方法，会等待所有子进程结束在执行主进程
    pool.join()

    print("结束父进程")

```

## 进程封装

```
class KaigeProcess(Process):
    def __init__(self, name):
        super().__init__()
        self.name = name
    #当对象调用start方法时，默认调用run方法
    def run(self):
        print("子进程(%s--%s)启动(父进程:%s)"%(self.name, os.getpid(),os.getppid()))
        print("kaige is a good man")
        time.sleep(2)
        print("子进程(%s--%s)结束(父进程:%s)" % (self.name, os.getpid(), os.getppid()))

```

## 多进程遍历目录

```
# -*- coding:utf-8 -*-
import os
import time
from multiprocessing import Pool

# path = r"C:\Users\xlg\Desktop\gp01\day14\file"
# filesList = os.listdir(path)
# t1 = time.time()
# for fileName in filesList:
#     absPath = os.path.join(path, fileName)
#     if os.path.isdir(absPath):
#         files = os.listdir(absPath)
#         for item in files:
#             print(os.path.join(absPath, item))
# t2 = time.time()
# print(t2-t1)


def run(path):
    files = os.listdir(path)
    for item in files:
        print(os.path.join(path, item))
if __name__ == "__main__":
    path = r"C:\Users\xlg\Desktop\gp01\day14\file"
    filesList = os.listdir(path)

    t1 = time.time()
    pool = Pool(5)
    for fileName in filesList:
        absPath = os.path.join(path, fileName)
        pool.apply_async(run, args=(absPath,))
    pool.close()
    pool.join()
    t2 = time.time()
    print(t2 - t1)

```

## 进程间通信

```
# -*- coding:utf-8 -*-

from multiprocessing import Process, Queue
import time
import random

'''进程间通信
有名管道
无名管道
队列
共享内存
信号
信号量
'''

#
def produce(q):
    print("启动produce子进程……")
    time.sleep(5)
    for value in ["good", "nice", "cool", "handsome"]:
        print("将%s放入队列"%value)
        q.put(value)
        time.sleep(random.random())
    print("结束produce子进程……")

#
def customer(q):
    print("启动customer子进程……")
    while True:
        print("消费者等待数据")
        value = q.get(True)
        print("消费者消费%s条数据"%value)
    print("结束customer子进程……")


if __name__ == "__main__":

    q = Queue()

    pro = Process(target=produce, args=(q,))
    cus = Process(target=customer, args=(q,))
    pro.start()
    cus.start()

    pro.join()
    #cus进程里是死循环，无法等待它的结束，只能强制结束该子进程
    cus.terminate()

    print("END")

```

## 什么是线程

```
# -*- coding:utf-8 -*-


'''
线程：
线程，有时被称为轻量进程(Lightweight Process，LWP），是程序执行流的最小单元。一个标准的线程由线程ID，当前指令指针(PC），寄存器集合和堆栈组成。另外，线程是进程中的一个实体，是被系统独立调度和分派的基本单位，线程自己不拥有系统资源，只拥有一点儿在运行中必不可少的资源，但它可与同属一个进程的其它线程共享进程所拥有的全部资源。一个线程可以创建和撤消另一个线程，同一进程中的多个线程之间可以并发执行。由于线程之间的相互制约，致使线程在运行中呈现出间断性。线程也有就绪、阻塞和运行三种基本状态。就绪状态是指线程具备运行的所有条件，逻辑上可以运行，在等待处理机；运行状态是指线程占有处理机正在运行；阻塞状态是指线程在等待一个事件（如某个信号量），逻辑上不可执行。每一个程序都至少有一个线程，若程序只有一个线程，那就是程序本身。

线程是程序中一个单一的顺序控制流程。进程内有一个相对独立的、可调度的执行单元，是系统独立调度和分派CPU的基本单位指令运行时的程序的调度单位。在单个程序中同时运行多个线程完成不同的工作，称为多线程



多线程：多线程（英语：multithreading），是指从软件或者硬件上实现多个线程并发执行的技术。具有多线程能力的计算机因有硬件支持而能够在同一时间执行多于一个线程，进而提升整体处理性能。具有这种能力的系统包括对称多处理机、多核心处理器以及芯片级多处理（Chip-level multithreading）或同时多线程（Simultaneous multithreading）处理器。 [1]  在一个程序中，这些独立运行的程序片段叫作“线程”（Thread），利用它编程的概念就叫作“多线程处理（Multithreading）”。具有多线程能力的计算机因有硬件支持而能够在同一时间执行多于一个线程（台湾译作“执行绪”），进而提升整体处理性能


'''

```

## 启动线程实现多任务

```
# -*- coding:utf-8 -*-

#模块
'''
_thread模块：低级模块
threading模块：高级模块，对_thread进行了封装
'''

import threading
import random
import time

def run1(num):
    print("启动%s子线程1-----%s"%(threading.current_thread().name, num))
    time.sleep(random.random()*5)
    print("结束%s子线程1-----%s" % (threading.current_thread().name, num))

def run2(num):
    print("启动%s子线程2-----%s" % (threading.current_thread().name, num))
    time.sleep(random.random() * 5)
    print("结束%s子线程2-----%s" % (threading.current_thread().name, num))


if __name__ == "__main__":
    # threading.current_thread()得到当前线程对象
    # 主线程的名字默认为MainThread
    print("主线程%s启动……" % threading.current_thread().name)

    #创建线程
    th1 = threading.Thread(target=run1, args=(1,), name="th1")
    th2 = threading.Thread(target=run2, args=(2,), name="th2")

    #启动
    th1.start()
    th2.start()

    #等待子线程结束
    th1.join()
    th2.join()

    print("主线程%s结束……" % threading.current_thread().name)

```

## 线程间共享数据

```
# -*- coding:utf-8 -*-

#多线程和多进程最大的不同在于，多进程中，同一个全局变量，每个子进程各自有一份拷贝，互不影响。而在多线程中，所有变量都由线程共享，所以任何一个变量都可以被任意线程所修改。因此，多个线程同时改变一个变量，容易把内容改乱了



import threading
import random
import time

money = 0
def changeMoney(n):
    global money
    money = money + n
    money = money - n

def run1(num):
    for i in range(1000000):
        changeMoney(num)

def run2(num):
    for i in range(1000000):
        changeMoney(num)


if __name__ == "__main__":
    #创建线程
    th1 = threading.Thread(target=run1, args=(5,), name="th1")
    th2 = threading.Thread(target=run2, args=(8,), name="th2")

    #启动
    th1.start()
    th2.start()

    #等待子线程结束
    th1.join()
    th2.join()

    print("money = %d"%money)

```

## 线程锁解决数据混乱

```
# -*- coding:utf-8 -*-


# 问题：两个线程同时一寸一取，可能造成变量值的不对，我们必须保证一个线程在修改money的时候，其他的线程一定不能修改


#后期在线程中对变量上锁，但是千万要注意释放锁(自己的锁自己放)，否则会造成死锁

import threading
import random
import time

lock = threading.Lock()

money = 0
def changeMoney(n):
    global money
    money = money + n
    money = money - n

def run1(num):
    for i in range(1000000):
        #获取线程锁，如果已上锁，则阻塞等待锁的释放
        lock.acquire()
        try:
            changeMoney(num)
        finally:
            #释放锁
            lock.release()

def run2(num):
    for i in range(1000000):
        with lock:
            changeMoney(num)


if __name__ == "__main__":
    #创建线程
    th1 = threading.Thread(target=run1, args=(5,), name="th1")
    th2 = threading.Thread(target=run2, args=(8,), name="th2")

    #启动
    th1.start()
    th2.start()

    #等待子线程结束
    th1.join()
    th2.join()

    print("money = %d"%money)

```

## ThreadLocal

```
# -*- coding:utf-8 -*-


import threading
import random
import time

# 创建全局ThreadLocal对象
# 每个线程独立的存储空间
# 每个Thread对它都可以读写属性操作，但是互不影响
local = threading.local()


def run1(num):
    time.sleep(1)
    local.money = 2
    print("1-------------", local.money,id(local.money))


def run2(num):
    time.sleep(3)
    local.money = 3
    print("3-------------", local.money,id(local.money))



if __name__ == "__main__":
    #创建线程
    th1 = threading.Thread(target=run1, args=(5,), name="th1")
    th2 = threading.Thread(target=run2, args=(8,), name="th2")

    #启动
    th1.start()
    th2.start()

    #等待子线程结束
    th1.join()
    th2.join()

    # print("money = %d"%money)
```

## 定时线程

```
# -*- coding:utf-8 -*-

import time
import threading


def run():
    print("sunck is a good man")


if __name__ == "__main__":
    # 经常启动5秒后在执行，不会阻塞主线程
    th = threading.Timer(5, run)

    th.start()

    th.join()
```

## 线程通信

```
# -*- coding:utf-8 -*-

import threading
import time


def func():
    event= threading.Event()
    def run():
        for i in range(10):
            #阻塞
            event.wait()
            #重置
            event.clear()
            print("--------------" + str(i))
    th = threading.Thread(target=run)
    th.start()
    return event

event = func()


for i in range(10):
    event.set()
    time.sleep(1)
print("END")
```

## 生产者与消费者

```
# -*- coding:utf-8 -*-


import threading
import queue
import random
import time

def produce(q, index):
    while True:
        num = random.randint(0, 1000000)
        q.put("生产者%s产生数据：%d"%(index, num))
        print("生产者%s产生数据：%d"%(index, num))
        time.sleep(1)
    # 完成任务
    q.task_done()


def customer(q, index):
    while True:
        item = q.get()
        if item is None:
            break
        print("消费者%s获取到：%s"%(index, item))
        time.sleep(4)
    # 完成任务
    q.task_done()


if __name__ == "__main__":
    q = queue.Queue(10)

    arr = []

    #创建三个生产者
    for i in range(3):
        th = threading.Thread(target=produce, args=(q, i))
        th.start()
        arr.append(th)

    # 创建5个消费者
    for j in range(5):
        th = threading.Thread(target=customer, args=(q, j))
        th.start()
        arr.append(th)

    for th in arr:
        th.join()
    print("END")
```

## 线程调度

```
# -*- coding:utf-8 -*-

# -*- coding:utf-8 -*-


import threading
import time

#线程条件变量
cond = threading.Condition()

def run1():
    with cond:
        for i in range(0, 10, 2):
            print(threading.current_thread().name+"---"+str(i))
            time.sleep(1)
            cond.wait()
            cond.notify()

def run2():
    with cond:
        for i in range(1, 10, 2):
            print(threading.current_thread().name+"---"+str(i))
            time.sleep(1)
            cond.notify()
            cond.wait()
if __name__ == "__main__":
    th1 = threading.Thread(target=run1, name="th1")
    th2 = threading.Thread(target=run2, name="th2")
    th1.start()
    th2.start()
    th1.join()
    th2.join()

    print("END")
```

## 进程、线程、协程深度理解

```
进程可在cpu间切换，线程跟着对应的进程走，协程跟着对应的线程走，线程实际上实现了计算机其他资源（除cpu）的并行使用
```



# 网络编程

## tcp

### client

```
# -*- coding:utf-8 -*-
import socket
import threading

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
#元组第一个元素为客户端要连接的服务器的IP地址，第二个参数为服务器的端口号
client.connect(("10.0.122.158", 8080))

# 创建接收线程
def run1(c):
    while True:
        data = c.recv(1024).decode("utf-8")
        print("服务器说：" + data)
th1 = threading.Thread(target=run1, args=(client,))
th1.start()
def run2(c):
    while True:
        #   456#你真坏
        data = input("请输入要发送给服务器的消息：")
        data = "talk#" + data
        c.send(data.encode("utf-8"))
th2 = threading.Thread(target=run2, args=(client,))
th2.start()


client.send("register#123#sunck".encode("utf-8"))


th1.join()
th2.join()
```

### server

```
# -*- coding:utf-8 -*-

import socket
import threading
from person import Person

usersDict = {}

# 1、创建socket
# AF_INET：表示使用IPv4
# SOCK_STREAM：表示TCP协议
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)


#2、绑定
# 参数为一个元组，元组第一个元素为本机ip，第二元素为端口号，使用8000以上的值，最大使用到65535
server.bind(("10.0.122.158", 8080))


#3、监听，设置最多连接数
server.listen(50)



def run(clientSocket, clientAddr):
    while True:
        #   register#123#sunck
        #   talk#456#sunck nice
        data = clientSocket.recv(1024).decode("utf-8")
        #解析数据
        arr = data.split("#")
        if arr[0] == "register":
            per = Person(clientSocket, arr[1], arr[2])
            usersDict[arr[1]] = per
        elif arr[0] == "talk":
            #找到当前用户的用户名
            name = None
            for account, per in usersDict.items():
                if per.clientSocket is clientSocket:
                    name = per.name
                    break
            #找到好友
            per = usersDict.get(arr[1])
            friendScoket = per.clientSocket
            # 给好友发送消息
            #  sunck说：你真帅
            friendScoket.send((name+"："+arr[2]).encode("utf-8"))


#4、等待客户端的链接
while True:
    print("等待链接……")
    #客户端连接成功返回客户端的socket和客户端的IP地址
    clientSocket, clientAddr = server.accept()
    print(clientAddr, "客户链接成功")
    #创建线程交互
    th = threading.Thread(target=run, args=(clientSocket, clientAddr))
    th.start()
```

## udp

### client

```
# -*- coding:utf-8 -*-

import socket


client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
while True:
    data = input("输入要发送的信息：")
    client.sendto(data.encode("utf-8"), ("10.0.122.158", 8080))





# 以下方式不建议使用
# client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
# client.connect(("10.0.122.158", 8081))
# while True:
#     data = input("输入要发送的信息：")
#     client.send(data.encode("utf-8"))
```

### server

```
# -*- coding:utf-8 -*-


# TCP是建立可靠连接，并且通信双方都可以以流的形式发送数据。相对TCP，UDP则是面向无连接的协议

# 使用UDP协议时，不需要建立连接，只需要知道对方的IP地址和端口号，就可以直接发送数据包，但是能不能到达就不知道了

# 虽然UDP传输数据不可靠，但是它的优点是和TCP相比较，速度快，对于不要求可靠到达的数据，可以使用UDP，广播类型的软件经常使用

import socket

server = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
server.bind(("10.0.122.158", 8081))

while True:
    data, addr = server.recvfrom(1024)
    print("来自", addr, "的消息：", data.decode("utf-8"))
```

## 使用udp冒充飞秋和轰炸



```
# -*- coding:utf-8 -*-


import socket

info = "1_lbt4_10#32499#002481627512#0#0#0:1289671407:a:b:288:sunck is a good man"

client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
client.sendto(info.encode("utf-8"), ("10.0.122.179", 2425))
```

```
# -*- coding:utf-8 -*-




import socket

info = "1_lbt4_10#32499#002481627512#0#0#0:1289671407:a:b:288:my name is a GP01 gaolei, you neng nai lai zhao wo!"

for i in range(256):
    ip = "10.%d.%d.%d"%(i,i,i)
    print(ip)
```

# 协程

## 协程概念

```
# -*- coding:utf-8 -*-

'''

协程：又称微线程，纤程，是一种用户态的轻量级线程

发展历程：
    1、最初的生成器变形yield/send
    2、引入@asyncio.coroutine和yield from
    3、在最近的python3.5版本中引入了async/await关键字

理解协程：
    1、普通理解：线程是系统级别的，他们是由操作系统调度。协程是程序级别的，由程序员根据需求自己调度。我们把一个线程中的一个个函数称为子程序，那么子程序在执行的过程中可以中断去执行别的子程序。别的子程序也可以中断回来继续执行之前的子程序，这就是协程。也就是说同一线程下的一段代码1执行执行着就可以中断，然后去执行另一段代码2，当再次回来执行代码块1的时候，接着从之前中断的地方开始执行
    2、专业理解：协程拥有自己的寄存器上下文和栈，协程在调度切换时，将寄存器上下文和栈保存到其他的地方，在切回来时，恢复先前保存的寄存器上下文和栈。因此，协程能保留上一次调用时的状态，每次过程重入时，就相当于进入上一次调用的状态。


子程序：在所有的语言中都是层级调用，比如A中调用B，B在执行过程中调用C，C执行完返回，B执行完返回，最后是A执行完毕。是通过栈实现的，一个线程就是执行一个子程序，子程序的调用总是有一个入口，一次返回，调用的顺序是明确的


优点：
    1、无需线程上下文切换的开销，协程避免了无意义的调度，由此提高了性能，但是，程序员必须自己承担调度的责任，同时协程也失去了标准线程使用多CPU的能力
    2、无需原子操作锁定及同步的开销
    3、方便切换控制流，简化编程模型
    4、高并发+高扩展性+低成本，一个CPU支持上万个协程不是问题


缺点：
    1、无法利用多核资源，协程的本质是单个线程，它不能同时将单个CPU的多个核使用上，协程需要和进程配合使用才能运行在多CPU上。但是一般不需要，除非是CPU密集型的应用
    2、进行阻塞操作(耗时IO)会阻塞整个程序
'''
# def A():
#     def B():
#         def C():
#             pass
#         C()
#     B()
# A()


def A():
    print(1)
    print(2)
    print(3)
def B():
    print("a")
    print("b")
    print("c")
'''
协程可能实现其他的打印效果
1
2
a
b
3
c
'''
```

## 协程的数据传递

```
# -*- coding:utf-8 -*-

def func():
    data = "#"
    # yield不但可以返回一个值，并且它还可以接收调用者发送的参数
    r = yield data
    print("-------------1", r, data)
    r = yield data
    print("-------------2", r, data)
    r = yield data
    print("-------------3", r, data)
    r = yield data

g = func()
print(g, type(g))
# print(next(g))
# print(next(g))
# print(next(g))
# print(next(g))
#启动g
print(g.send(None))
print(g.send("a"))
print(g.send("b"))
print(g.send("c"))
```

## 协程实现生产者消费者

```
# -*- coding:utf-8 -*-
import time
import threading

def produce(c):
    print(threading.current_thread().name)
    c.send(None)
    for i in range(5):
        print("[produce] 生成数据%d"%i)
        #发送给消费者
        res = c.send(str(i))
        print("[produce] 消费者反馈：%s"%res)
        time.sleep(2)
    #关闭消费者
    c.close()

def customer():
    print(threading.current_thread().name)
    res = ""
    while True:
        data = yield res
        if not data:
            return
        print("[customer] 消费数据%s"%data)
        res = "200 OK"


c = customer()
produce(c)
```

## 同步与异步

```
# -*- coding:utf-8 -*-

#前言：python由于GIL（全局锁）的存在，不能发挥多核的优势，其性能一直被人诟病。然而在IO密集型的网络编程里，异步处理比同步处理性能会提升成百上千倍


#同步：只完成事物的逻辑，先执行第一个事物，如果阻塞了，会一直等待，直到这个事物完成，在执行第二个事物，顺序执行


#异步：是和同步相对的，指在处理调用这个事物的之后，不会等待这个事物的处理结果，直接去处理第二个事物了，通过状态、通知、回调来通知调用者处理结果
```

## 同步代码

```
# -*- coding:utf-8 -*-
import time

def func():
    time.sleep(1)


for i in range(5):
    func()
    print("time:%s"%time.time())
```

## 异步代码

```
# -*- coding:utf-8 -*-
import time
import asyncio

#定义异步函数(定义一个协程)
async def func():
    #模拟一个耗时IO操作
    asyncio.sleep(1)
    print("time:%s"%time.time())

loop = asyncio.get_event_loop()
for i in range(5):
    loop.run_until_complete(func())
```

## asyncio模块概述

```
# -*- coding:utf-8 -*-

'''

asyncio模块使python3.4版本引入的标准库，直接内置了对异步IO的支持

编程模式：是有一个消息循环，我们从asyncio模块中直接获取一个EventLoop的引用，然后把需要执行的协程扔到EventLoop中执行，就实现了异步


说明：到目前为止实现协程的不仅只有asyncio，还有gevent和tornado都实现了类似的功能


关键字说明：
    1、evnet_loop 事件循环：程序开启一个无限循环，把一些函数注册到事件循环中，当满足条件发生时，调用相应的协程函数
    2、coroutine 协程：协程对象，指一个使用async关键字定义的函数，它的调用不会立即执行函数，而是会返回一个协程对象。协程对象需要注册到事件循环中，由事件循环调用
    3、task 任务：一个协程对象就是一个原生可以挂起的函数，任务则是对协程进一步的封装，其中包含了任务的各种状态
    4、future：代表将来执行或没有执行的任务的结果，它和task上没有本质上区别
    5、async/await：python3.5用于定义协程的关键字，async定义一个协程，await用于挂起阻塞异步调用接口






'''
```

## 定义一个协程

```
# -*- coding:utf-8 -*-

import time
import asyncio

# 通过async关键字定义了一个协程，协程不能直接运行，需要将协程加入到事件循环中
async def run(x):
    print("waiting：%d"%x)

start = time.time()

# 得到一个协程对象，这个时候run()函数没有执行
coroutine = run(2)
# print(coroutine)

# 创建一个事件循环（注意：真实情况是在asyncio模块中获取一个引用）
loop = asyncio.get_event_loop()
# 将协程对象加入到事件循环
loop.run_until_complete(coroutine)

end = time.time()
print("Time：", end - start)
```

## 创建一个task

```
# -*- coding:utf-8 -*-

import time
import asyncio

async def run(x):
    print("waiting：%d"%x)

start = time.time()





coroutine = run(2)

loop = asyncio.get_event_loop()
# 将协程对象加入到事件循环，协程对象不能直接运行，在注册事件循环的时候，其实是run_until_complete方法将协程对象包装成了一个任务对象，task对象是Future类的子类，保存了协程运行后的状态，用于未来获取协程的结果
# loop.run_until_complete(coroutine)

#创建任务
task = asyncio.ensure_future(coroutine)
# task = loop.create_task(coroutine)
print(task)
#将任务加入到事件循环
loop.run_until_complete(task)
print(task)



end = time.time()
print("Time：", end - start)
```

## 绑定回调

```
# -*- coding:utf-8 -*-

import time
import asyncio

async def run(x):
    print("waiting：%d"%x)
    return "done after %ds"%x

#定义一个回调函数，参数为future，任务对象
def callback(future):
    print("callback：", future.result())

start = time.time()





coroutine = run(2)
loop = asyncio.get_event_loop()
task = asyncio.ensure_future(coroutine)
#给任务添加回调，在任务结束后调用回调函数
task.add_done_callback(callback)
loop.run_until_complete(task)



end = time.time()
print("Time：", end - start)
```

## 阻塞和await

```
# -*- coding:utf-8 -*-

import time
import asyncio

#async可以定义协程对象，使用await可以针对耗时的操作进行挂起，就行生成器里的yield一样，函数交出控制权。协程遇到await，事件循环将会挂起该协程，执行别的协程，直到其他协程也挂起或者执行完毕，再进行下一个协程的执行
async def run(x):
    print("waiting：%d" % x)
    # 调用了一个耗时IO操作
    # asyncio.sleep(x)另一个协程对象
    await asyncio.sleep(x)
    return "done after %ds" % x
def callback(future):
    print("callback：", future.result())

start = time.time()

coroutine = run(2)
loop = asyncio.get_event_loop()
task = asyncio.ensure_future(coroutine)
task.add_done_callback(callback)
loop.run_until_complete(task)



end = time.time()
print("Time：", end - start)
```

## 并发和并行

```
# -*- coding:utf-8 -*-

'''
并发：指有多个任务需要同时进行

并行：同一时刻有多个任务执行

并发类似一个老师在同一时间段辅导不同的人功课，并行好几个老师分别同时辅导多个学生。

'''

import time
import asyncio

async def run(x):
    print("waiting：%d" % x)
    # 调用了一个耗时IO操作
    # asyncio.sleep(x)另一个协程对象
    await asyncio.sleep(x)
    return "done after %ds" % x

start = time.time()

coroutine1 = run(2)
coroutine2 = run(3)
coroutine3 = run(4)
coroutine4 = run(5)

tasks = [
    asyncio.ensure_future(coroutine1),
    asyncio.ensure_future(coroutine2),
    asyncio.ensure_future(coroutine3),
    asyncio.ensure_future(coroutine4)
]


loop = asyncio.get_event_loop()
#1、添加任务列表
# loop.run_until_complete(asyncio.wait(tasks))
#2、
loop.run_until_complete(asyncio.gather(*tasks))

for task in tasks:
    print("Task 返回值：", task.result())



end = time.time()
print("Time：", end - start)
```

## 协程嵌套

```
# -*- coding:utf-8 -*-


import time
import asyncio

async def run(x):
    print("waiting：%d" % x)
    await asyncio.sleep(x)
    return "done after %ds" % x

start = time.time()


async def main():
    coroutine1 = run(2)
    coroutine2 = run(3)
    coroutine3 = run(4)
    coroutine4 = run(5)
    tasks = [
        asyncio.ensure_future(coroutine1),
        asyncio.ensure_future(coroutine2),
        asyncio.ensure_future(coroutine3),
        asyncio.ensure_future(coroutine4)
    ]
    #1、
    # dones, pendings = await asyncio.wait(tasks)
    # for task in dones:
    #     print("Task 返回值：", task.result())

    #2、
    # results = await asyncio.gather(*tasks)
    # for result in results:
    #     print("task 返回值：", result)


    #3、
    # return await asyncio.wait(tasks)

    #4、
    # return await asyncio.gather(*tasks)

    #5、
    for task in asyncio.as_completed(tasks):
        result = await task
        print("task返回值：", result)

loop = asyncio.get_event_loop()
#1、
# loop.run_until_complete(main())
#2、
# loop.run_until_complete(main())
#3、
# dones, pending = loop.run_until_complete(main())
# for task in dones:
#     print("task返回值",task.result())
#4、
# results = loop.run_until_complete(main())
# for result in results:
#     print("task 返回值：", result)
#1、
loop.run_until_complete(main())


end = time.time()
print("Time：", end - start)
```

## 不同线程的事件循环

```
# -*- coding:utf-8 -*-

#一般情况我们的事件循环用于注册协程，有一些协程需要动态的添加到事件循环中。简单的方式就是使用多线程，当前线程创建一个事件循环，然后开启一个新线程，在新线程中启动事件循环，当前线程不会被block


import asyncio
import time
import threading

def start_loop(lp):
    #启动事件循环
    asyncio.set_event_loop(lp)
    lp.run_forever()

def run(x):
    print("waiting：%d" % x)
    time.sleep(x)
    print("finish after %ds" % x)

start = time.time()


loop = asyncio.get_event_loop()


#创建新线程，用于启动事件循环，此时不会阻塞主线程了
threading.Thread(target=start_loop, args=(loop,)).start()

end = time.time()
print("time:", end-start)

#给事件循环添加任务
loop.call_soon_threadsafe(run, 4)
loop.call_soon_threadsafe(run, 6)
```

## 新线程协程

```
# -*- coding:utf-8 -*-

#一般情况我们的事件循环用于注册协程，有一些协程需要动态的添加到事件循环中。简单的方式就是使用多线程，当前线程创建一个事件循环，然后开启一个新线程，在新线程中启动事件循环，当前线程不会被block


import asyncio
import time
import threading

def start_loop(lp):
    #启动事件循环
    asyncio.set_event_loop(lp)
    lp.run_forever()

async def run(x):
    print("waiting：%d" % x)
    await asyncio.sleep(x)
    print("finish after %ds" % x)

start = time.time()


loop = asyncio.get_event_loop()


#创建新线程，用于启动事件循环，此时不会阻塞主线程了
threading.Thread(target=start_loop, args=(loop,)).start()

end = time.time()
print("time:", end-start)

#给事件循环添加任务
asyncio.run_coroutine_threadsafe(run(4), loop)
asyncio.run_coroutine_threadsafe(run(6), loop)
```

## 获取网页信息

```
# -*- coding:utf-8 -*-

# www.163.com   www.baidu.com   www.sohu.com    www.sina.com.cn    www.google.com
#  3                5            2                  6

import asyncio
import time
import threading


def start_loop(lp):
    asyncio.set_event_loop(lp)
    lp.run_forever()

async def wget(urlStr):
    print("开始加载%s……"%urlStr)
    connet = asyncio.open_connection(urlStr, 80)
    print("***********************",connet)
    reader, writer = await connet
    #链接成功
    header = "GET / HTTP/1.0\r\nHost: %s\r\n\r\n"%urlStr
    writer.write(header.encode("utf-8"))
    await writer.drain()
    #接收到数据
    while True:
        line = await reader.readline()
        if line == b'\r\n':
            break
        print("%s header--->%s"%(urlStr, line.decode("utf-8").strip()))
    writer.close()


loop = asyncio.get_event_loop()
threading.Thread(target=start_loop, args=(loop,)).start()


#给时间循环添加任务
for url in ["www.163.com","www.sohu.com","www.sina.com.cn","www.baidu.com"]:
    asyncio.run_coroutine_threadsafe(wget(url), loop)
```

# json数据的序列化和反序列化

```
# 序列化：将Python对象转换成json字符串
dumps(obj, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, cls=None, indent=None, separators=None, default=None, sort_keys=False, **kw)

# 反序列化：将json字符串转换成Python对象
loads(s, encoding=None, cls=None, object_hook=None, parse_float=None, parse_int=None, parse_constant=None, object_pairs_hook=None, **kw)

# 序列化：将Python对象转换成json字符串并存储到文件中
dump(obj, fp, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, cls=None, indent=None, separators=None, default=None, sort_keys=False, **kw)

# 反序列化：读取指定文件中的json字符串并转换成Python对象
load(fp, cls=None, object_hook=None, parse_float=None, parse_int=None, parse_constant=None, object_pairs_hook=None, **kw)

参数说明：
	sort_keys参数： 表示序列化时是否对dict的key进行排序（dict默认是无序的）
	
	indent参数： 表示缩进的意思，它可以使得数据存储的格式变得更加优雅、可读性更强；如	果indent是一个非负整数或字符串，则JSON array元素和object成员将会被以相应的缩进级	   别进行打印输出；如果indent是0或负数或空字符串，则将只会插入换行，不会有缩进。
    
    separators参数： 尽管indent参数可以使得数据存储的格式变得更加优雅、可读性更强，但	是那是通过添加一些冗余的空白字符进行填充的。当json被用于网络数据通信时，应该尽可能	  的减少无用的数据传输，这样可以节省带宽并加快数据传输速度。json模块序列化Python对	    象后得到的json字符串中的','号和':'号分隔符后默认都会附加一个空白字符，我们可以通过	 separators参数重新指定分隔符，从而去除无用的空白字符；

    该参数的值应该是一个tuple(item_separator, key_separator)
    如果indent是None，其默认值为(', ', ': ')
    如果indent不为None，则默认值为(',', ': ')
    我们可以通过为separator赋值为(',', ':')来消除空白字符
    
    ensure_ascii参数： 当该参数的值为True（默认值）时，输出中的所有非ASCII字符（比如	   中文）都会被转义成'\uXXXX'组成的序列，得到的结果是一个完全由ASCII字符组成的str实	   例。如果我们想得到一个人类可读的输出结果，需要把ensure_ascii参数的值设置为			False。
```



# chardet

```
# -*- coding:utf-8 -*-



#作用：使用chardet检测编码，支持检测中文、日文、韩文等多种语言

# pip install chardet

import chardet

#数据量小，猜测的不太对
data = "凯".encode("gbk")
print(data)

s = chardet.detect(data)
print(s)
print(type(s))

info = data.decode(s["encoding"])
print(info)
```

# python2和python3的区别

```
# -*- coding:utf-8 -*-

# 1、性能
#python3.x起始比python2.x效率要低，但是python3.x有极大的优化空间，效率正在追赶，目前已经不差多少。


# 2、编码
#python3.x原码文件默认使用utf-8，使变量名更为广阔


# 3、语法
# 3.1、去除了<>，改用!=
'''3.2、
/
    python2.x整型触发返回整数
    python3.x整型触发返回浮点数，整除使用//

'''
# 3.3、加入了nonlocal语句
# 3.4、去除了print语句，加入了print()函数
# print("sunck", end=" ")
# print("kaige")
# 3.5、去除了raw_input语句，加入了input()函数
# 3.6、新的super(),可以不再给super()传递参数
# class A(object):
#     pass
# class B(A):
#     def __init__(self):
#         super().__int__()
# 3.7、改变了顺序操作符的行为，比如x<y，当x和y类型不匹配时抛出TypeError异常
# 3.8、新式的8进制数字变量



# 4、字符串和字节串
'''
python2.x  字符串以8bit字符串存储
python3.x  字符串以16bit Unicode字符串存储，现在字符串只有str一种类型
'''




# 5、数据类型
#python3.x去除了long类型，现在只有一种整数类型int，但是它的行为就像2.x中long
#新增了bytes类型，对应2.x版的八位串







# 6、面向对象
# 引入抽象基类




# 7、异常
#所有异常都从BaseException继承，并删除了StardardError
'''
python2
try:
    ……
except Exception e:
    ……



python3
try:
    ……
except Exception as e:
    ……
'''





# 8、其他
# python2.x中的xrange()在python3.x中名为range()
'''
file类被废弃
python2可以使用file(path)、open(path)

'''
```

# PEP8编码规范

```
# -*- coding:utf-8 -*-
#英文教程：https://legacy.python.org/dev/peps/pep-0008/#a-foolish-consistency-is-the-hobgoblin-of-little-minds

#中文教程：https://blog.csdn.net/ratsniper/article/details/78954852



'''
代码编排
    1、缩进4个空格，禁止空格与Tab混用
    2、行长79，防止单行的逻辑过于复杂

'''
if 1:
    pass



'''
命名
    1、除非在lamdba函数中，否则不要使用单字母的变量名，但是即使在lamdba函数中变量名也要尽可能有意义
    2、包名、模块名、函数名全部使用小写，单词使用下划线链接
    3、类名、异常名使用首字母大写的方法，异常名结尾加Error或者Warning
    4、全局变量尽量使用大写，同一类型的全局变量要加同一的前缀，单词用下划线链接
    5、自定义的变量、函数名等不要与标准库名冲突
    6、函数名必须有动词，最好是do_something的句式或者somebody_do_something句式
'''
COLOR_RED = 10
COLOR_BLUE = 11
f = lambda x: x+1
def func(x, y):
    pass
def get_money():
    pass





'''
注释
    1、忌讳没有注释和逐行注释
    2、行内注释
        当行逻辑过于复杂添加
    3、块注释
        一段逻辑开始时注释
    4、引入外来算法或者配置时必须在注释中添加源链接，标明出处
    5、函数和类尽量添加docstring
        
'''
def do_eat(x, y):
    print("------------")




'''
空格
    1、:,;后面要跟一个空格，前面没有空格，行尾分号无需空格
    2、二元操作符前后各一个空格
        数学运算符、比较运算符、逻辑运算符、位运算符
    3、=的注意事项：用于指示关键字参数或默认参数值时，不要添加空格
'''
a = 1
def f(x, y=1):
    pass


'''
换行
    1、适当添加换行
    2、函数间
        1、顶级函数空间空2行
        2、类的方法空1行
    3、文件结尾留空一行
'''



'''
import
    1、不要使用from xxx import *
    2、导入顺序(标准库、第三方、自定义)
        a、标准库
        b、第三方库
        c、自定义库
    3、单行不要导入多个库
    4、模块内用不到的不要去import
'''



'''
字符串拼接
    1、拼接方法
        a、字符串相加    （性能最差）
        b、字符串格式化
        c、python3.6支持f操作符
            >>> a = 111
            >>> b=222
            >>> c=333
            >>> s = f"{a}-{b}-{c}"
            >>> s
            '111-222-333'
        d、join
    2、尽量使用join方法，因为速度快，内存消耗小
'''




'''
语义
    1、要求明确、直白
    
    not x in y
    x not in y
    
    not x is y
    x is not y

'''


'''
测试工具：
pep8：即将失效，用pycodestyle替换
pylint：更加严格，引入的包没有使用都可以检测出来
flake8：

'''
```

