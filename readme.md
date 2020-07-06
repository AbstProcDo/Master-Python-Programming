# Python编程第一课：程序构成的7个基本元素

![Python编程第一课：程序构成的7个基本元素](readme.assets/3dd14ffb-0881-45ae-a4e0-ade66e5ed667)

我们学习编程最有效的方式，是从日常的应用出发，从已有的知识结构出发，逐层向上搭建。因此，我们本能的起点自然是如何进行数学运算，如何将Python作为计算器。

# 1.数学表达式

即使我们完全没有编程的概念和计算机基础，在python的interactive-shell中，也必然会执行加减乘除计算：

```
In [7]: 271828 + 828271   # 加法    
Out[7]: 1100099
In [8]: 828271 - 271828   # 减法   
Out[8]: 556443
In [9]: 17 * 3    # 乘法
Out[9]: 51
In [10]: 17 / 3   # 除法
Out[10]: 5.666666666666667
In [11]: 17 % 3   # 模除
Out[11]: 2
In [12]: 17 ** 3  # 乘方
Out[12]: 4913
```

Python编程就是这么简单。

再查看稍微复杂的数学表达式：

```
In [13]: (50 + 33*2) / (78*98 - 345)
Out[13]: 0.01589258802575695
```

是不是比我们手上的任何计算器都要方便呢。

观察上述的表达式｀271828 + 828271｀，可知其分为两个部分，一是数字（number）或者称为操作数（operand），二是作为操作符（operator）的运算符号加减乘除。

此处我们有一处洞见，数字是最原始最初级的数据，而加减乘除这些操作符则是最原始最初级的程序。

你看，一个简简单单的数学表达式，将编程的全部内容都囊括进来：数据与程序。

![Python编程第一课：程序构成的7个基本元素](readme.assets/6a6d7b09-cae4-4b03-b4b7-77cf72f90b74)



# 2.命名与变量

编程语言提供的核心服务之一是能将一长串的数字或者一段程序命名。这是重大的利好，简单想象一下每次都按数字电话拨号与用人名打电话的区别，我们能记得住千百个熟悉的名字，却往往记不住两个以上的电话号码。

命名的方式简单直接：

```
In [23]: radius = 9                 
In [24]: high = 21
In [25]: pi = 3.14159
```

接下来我们计算锥体的体积（公式为V=1/3Sh)

```
In [26]: S = pi * radius**2         
In [27]: V = 1/3 * S * high         
In [28]: V        
Out[28]: 1781.2815299999997
```

对变量命名是最简单的抽象方式，于是我们可以直接用抽象的名字进行数学运算。

![Python编程第一课：程序构成的7个基本元素](readme.assets/c84d7cfe-5d6d-46a4-a2a9-bb863f7d4e47)



# 3.函数

命名变量作为初级的抽象方式，其表达力十分有限。我们马上来认识更为强大的抽象工具--函数（Function）。我们可以将函数作为执行特定任务的黑匣子。函数Function又称为Subroutine就是程序本人。我们在第一节中已经接触到程序了，那些最初级的程序，加减乘除操作符。

我们先验证下操作符（operator）是最原始的程序这个观点。第一节中的运算又可以表达为：

```
In [36]: from operator import add, sub, mul, truediv, pow                
In [37]: add(271828, 828271)        
Out[37]: 1100099
In [38]: sub(828271, 271828)        
Out[38]: 556443
In [39]: mul(17, 3)                 
Out[39]: 51
In [40]: truediv(17, 3)             
Out[40]: 5.666666666666667
In [41]: pow(17, 3)                 
Out[41]: 4913
In [42]: truediv(add(50, mul(33,2)), sub(mul(78,98),345))                
Out[42]: 0.01589258802575695
```

将第一节的内容重新写了一遍，由此得证操作符operator是最初级的程序。 

自定义函数的语法也是简单直接：

```
def <name>(<formal parameters>): # def 是define的前三个字母
    return <return expression>
```

案例还是从我们现有的知识基础出发，以小学数学的求平方数为例：

```
In [43]: def square(x): 
    ...:     return x * x 
    ...:          

In [44]: square(11)                 
Out[44]: 121

In [45]: square(121)                
Out[45]: 14641
```

我们可以轻松的求两个数字的平方和，验证勾股定理。

```
In [2]: def sum_of_squares(x, y): 
   ...:     return square(x) + square(y) 
   ...:            

In [3]: sum_of_squares(3, 4)           
Out[3]: 25
```

由此，我们在函数square的基础上构建了sum_of_squares。此时，我们可以更进一步，以先定义的函数sum_of_squares为垫脚石，构建更为复杂的函数。

```
In [4]: def func(a): 
   ...:     return sum_of_squares(a+1, a+2) 
   ...:            

In [5]: func(2)    
Out[5]: 25
```

![Python编程第一课：程序构成的7个基本元素](readme.assets/76e4797f-802c-4eb9-ab83-aaa86168989d)

七巧板拼图勾股定理 

# 4.Lambda匿名函数

匿名函数是正式函数的快捷方式。很多时候，我们觉得不必要劳师动众给每段代码都命名，或者说给函数命名这件事实在太难了，甚至比编程本身难得多。因此，我们取捷径，只用函数之实体，而不给其命名。

lambda是强大而便捷的功能。在流行语言javascript以及全部的函数式编程语言中大规模普与应用。

语法如下：

```
square = lambda x: x ** 2
# 等价于：
def square(x):  return x * x     
```

然而，在Python语言中，lambda的全部只有这么多。因为Python之父不鼓励lambda的使用，曾经一度试图将lambda从其语言体系中连根除掉，而差点导致整个社区的大分裂。

因此，最终的妥协方案，python的lambda函数功能受限，社区更鼓励多使用正式命名函数。

![Python编程第一课：程序构成的7个基本元素](readme.assets/404d40f7-a1ed-4af5-8321-2a2d518f9722)



# 5.条件选择语句

前面三节中，我们的抽象能力逐步提高，从有限抽象的变量到似乎有着无限抽象能力的函数。问题也紧随而来，我们当前获得的表达力工具，没有途径做出种种测试，并根据测试的不同结果来决定下一步的操作。

由此，我们引入条件判断语句，其结构为：

```
if <expression>:
    <suite>
elif <expression>:
    <suite>
else:
    <suite>
```

马上尝试求绝对值的函数：

```
In [6]: def abs_val(x): 
   ...:     if x > 0: return x 
   ...:     elif x ==0: return 0 
   ...:     else: return -x 
   ...:            

In [8]: abs(-121)  
Out[8]: 121

In [9]: abs(0)     
Out[9]: 0

In [10]: abs(32)   
Out[10]: 32
```

![Python编程第一课：程序构成的7个基本元素](readme.assets/ec13b668-5468-4306-b484-846bb6153a65)

住房危机迹象开机自检 

# 6.迭代循环结构

编程的首要任务之一就是要协助我们从机械重复的活动中抽身而出，将其全部交由计算机完成。

先来看经典的for循环语句：

```
In [11]: words = ['seven', 'elements', 'in', 'python', 'programming']         

In [12]: for w in words: 
    ...:     print(w, len(w)) 
    ...:           
seven 5
elements 8
in 2
python 6
programming 11
```

以及while语句：

```
In [21]: i = 0
            while i < 10: 
    ...:     print(i) 
    ...:     i += 1
    ...:      
    ...:           
0
1
2
3
4
5
6
7
8
9
```

接下来，我们尝试应用循环结构求平方根，并且采用牛顿迭代算法：

牛顿求平方根法用的是‘连续逼近’的思路 "successive  approximations"。我们首先瞎猜一个y作为x的平方根，然后在这个瞎猜的基础上更好的瞎猜，不断地接近平方根的真实值。这个bette-guess为前面的瞎猜值与x/y的平均值，分布过程展示为：

![Python编程第一课：程序构成的7个基本元素](readme.assets/7d1a5b12343644d49014d2d6e823abd1)



具体实现为：

```
def sqrt(x):
    return sqrt_iter(1, x)

def sqrt_iter(guess, x):
    if x < 0: raise ValueError("n must not be negative.")
    while True:
        if good_enough_p(guess, x):
            return guess
        else:
            guess = improve(guess, x) 

def improve(guess, x):
    return average(guess, x/guess)

def good_enough_p(guess, x):
    return abs(guess**2 - x) < 0.00001

def average(x, y):
    return (x + y) / 2

In [23]: sqrt(121) 
Out[23]: 11.000000001611474
In [24]: sqrt(30)  
Out[24]: 5.47722557564769
```

牛顿迭代法的逻辑很清晰，当guess值足够好时，good-enough-p就返回当前的guess值；如果，guess值不能达到满意，则继续接着猜。

![Python编程第一课：程序构成的7个基本元素](readme.assets/5747de7e-f68f-4aae-8720-8b0cdb8e8e66)

英格兰,伦敦,大英图书馆,艾萨克·牛顿爵士铜像，爱德华多·帕洛齐

# 7.递归结构

Iteration循环结构乃是我们人类解决问题的一般思路，从眼前的局部出发，一步一步的往前挪，直至抵达目的地。与之相对的递归方案，则是上帝解决问题的策略。先从宏观大局入手，再分解到局部细节。随着年岁渐长，我们会将递归应用到生活与工作的方方面面，角角落落，并与之培养起来恒久的热爱。

我们还是沿用求平方根问题，这次使用Recursion的方案。

```
def sqrt2(x):
    return sqrt_iter(1, x)

def sqrt_iter2(guess, x):
    if x < 0: raise ValueError("n must not be negative.")
    if good_enough_p(guess, x):
        return guess
    else:
        return sqrt_iter2(improve(guesss), x)

In [26]: sqrt2(11) 
Out[26]: 3.3166248052315686
```

本例中，我们完全没有调用循环结构，而只单单使用函数本身就实现了与循环结构相同的效果。这是令人震惊的宣告，这是函数式编程的精髓之所在，这是初入了上帝思维思考问题的门径。

![Python编程第一课：程序构成的7个基本元素](readme.assets/4510f7a7-54fe-410f-9169-2c2d6efceed8)



# 8.收尾总结

本文我们探讨了 bash-script 的七项基本元素：

1. 数学表达式
2. 变量与命名
3. 函数
4. 匿名函数
5. 条件选择
6. 循环结构
7. 迭代结构

以上，第一课完结。

![Python编程第一课：程序构成的7个基本元素](readme.assets/d38de6cb-243e-4b82-910b-75c6ca8b8840)

