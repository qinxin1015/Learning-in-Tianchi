# python 高阶 task 03

2020.12.15

# 函数

## 函数的定义

还记得 Python 里面“万物皆对象”么？Python 把函数也当成对象，可以从另一个函数中返回出来而去构建高阶函数，比如：
参数是函数、返回值是函数。

我们首先来介绍函数的定义。

- 函数以`def`关键词开头，后接函数名和圆括号()。
- 函数执行的代码以冒号起始，并且缩进。
- return [表达式] 结束函数，选择性地返回一个值给调用方。不带表达式的return相当于返回`None`。


```python
def functionname (parameters):
	"函数_文档字符串"
	function_suite
	return [expression]
```

## 函数参数

Python 的函数具有非常灵活多样的参数形态，既可以实现简单的调用，又可以传入非常复杂的参数。从简到繁的参数形态如下：
- 位置参数 (positional argument)
- 默认参数 (default argument)
- 可变参数 (variable argument)
- 关键字参数 (keyword argument)
- 命名关键字参数 (name keyword argument)
- 参数组合

#### 位置参数

```python
def functionName(arg1,arg2):
	"函数文档字符串"
	function_suit
	return[expression]
```
- arg1,arg2:位置参数，Call function 时，arg1,arg2的位置要固定。
- 但是，如果调用时采用functionName(arg2 = value2, arg1 = value1)，则是可以允许的。因为python解释器可以通过参数名 匹配 参数值。

#### 默认参数
```python
def functionName(arg1, arg2 = value):
	"函数文档字符串"
	function_suit
	return[expression]
```
- arg1: 位置参数； arg2:默认参数。
- 当Call function 没有传入arg2时，arg2就采用默认值 value 调用函数。
- 默认参数 arg2 的定义必须放在位置参数arg1后面，否则，函数会报错。

#### 可变参数

```python
def functionName(arg1, *arg):
	"函数说明字符串"
	function_suit
	return[expression]
```
- \*arg: 可变参数, 参数可以是0，1，2，无数个；这些参数自动组成元组传入函数。
```python
def printinfo(arg1, *args):
    print(arg1)
    for var in args:
        print(var)


printinfo(10)  # 10
printinfo(70, 60, 50)
# 70
# 60
# 50
```
#### 关键字参数 （dict）
```python
def functionName(arg1,arg2 = value,*args,**kwargs):
	"函数说明字符串"
	function_suit
	return[expression]
```
- arg1:位置参数；arg2:默认参数；\*args:可变参数；\*\*kwargs: 关键字参数
- \*\*kw --- 关键字参数，可以是0~N个，自动组装成字典。

```python
def printinfo(arg1, *args, **kwargs):
    print(arg1)
    print(args)
    print(kwargs)

printinfo(70, 60, 50)
# 70
# (60, 50)
# {}
printinfo(70, 60, 50, a=1, b=2)
# 70
# (60, 50)
# {'a': 1, 'b': 2}
```

「可变参数」和「关键字参数」的同异总结如下：
- 可变参数允许传入零个到任意个参数，它们在函数调用时自动组装为一个元组 (tuple)。
- 关键字参数允许传入零个到任意个参数，它们在函数内部自动组装为一个字典 (dict)。

#### 命名关键字参数
```python
def functionName(arg1,*,nkw,**kwargs):
	"函数说明字符串"
	function_suit
	return[expression]
```
- \*,nkw : 为命名关键字参数，在调用时必须使用 nkw = value, 否则就会被当成位置参数，从而报错。
- `*, nkw` - 命名关键字参数，用户想要输入的关键字参数，定义方式是在nkw 前面加个分隔符 `*`。
```python
def printinfo(arg1, *, nkw, **kwargs):
    print(arg1)
    print(nkw)
    print(kwargs)

printinfo(70, nkw=10, a=1, b=2)
# 70
# 10
# {'a': 1, 'b': 2}

printinfo(70, 10, a=1, b=2)
# TypeError: printinfo() takes 1 positional argument but 2 were given
```
#### 参数组合

在 Python 中定义函数，可以用位置参数、默认参数、可变参数、命名关键字参数和关键字参数，这 5 种参数中的 4 个都可以一起使用，但是注意，参数定义的顺序必须是：
- 位置参数、默认参数、可变参数和关键字参数。
- 位置参数、默认参数、命名关键字参数和关键字参数。

要注意定义可变参数和关键字参数的语法：
- `*args` 是可变参数，`args` 接收的是一个 `tuple`
- `**kw` 是关键字参数，`kw` 接收的是一个 `dict`

命名关键字参数是为了限制调用者可以传入的参数名，同时可以提供默认值。定义命名关键字参数不要忘了写分隔符 `*`，否则定义的是位置参数。

警告：虽然可以组合多达 5 种参数，但不要同时使用太多的组合，否则函数很难懂。


## 变量作用域

- Python 中，程序的变量并不是在哪个位置都可以访问的，访问权限决定于这个变量是在哪里赋值的。
- 定义在函数内部的变量拥有局部作用域，该变量称为局部变量。
- 定义在函数外部的变量拥有全局作用域，该变量称为全局变量。
- 局部变量只能在其被声明的函数内部访问，而全局变量可以在整个程序范围内访问。

- 当内部作用域想修改外部作用域的变量时，就要用到`global`和`nonlocal`关键字了。

```python
num = 1

def fun1():
    global num  # 需要使用 global 关键字声明
    print(num)  # 1
    num = 123
    print(num)  # 123

fun1()
print(num)  # 123
```
#### 内嵌函数
```python
def outer():
    print('outer函数在这被调用')

    def inner():
        print('inner函数在这被调用')

    inner()  # 该函数只能在outer函数内部被调用

outer()
# outer函数在这被调用
# inner函数在这被调用
```
### 闭包 
- 是函数式编程的一个重要的语法结构，是一种特殊的**内嵌函数**。
- 如果在一个内部函数里对外层非全局作用域的变量进行引用，那么内部函数就被认为是闭包。
- 通过闭包可以访问外层非全局作用域的变量，这个作用域称为 <b>闭包作用域</b>。

- 闭包的返回值通常是函数
```python
def make_counter(init):
    counter = [init]

    def inc(): counter[0] += 1

    def dec(): counter[0] -= 1

    def get(): return counter[0]

    def reset(): counter[0] = init

    return inc, dec, get, reset


inc, dec, get, reset = make_counter(0)
inc()
inc()
inc()
print(get())  # 3
dec()
print(get())  # 2
reset()
print(get())  # 0
```
[]: https://zhuanlan.zhihu.com/p/26934085"什么是闭包"

[]:https://zhuanlan.zhihu.com/p/102462850

闭包，可以用于异步功能实现。
即，如果当前操作比较耗时，那么可以利用闭包先调用函数，后面继续执行其他操作，最后调用闭包函数执行结果。

？？？？？？？？？？？？？？？？？？？？？？？？？？？？？？？？？？？？

#### 递归

- 如果一个函数在内部调用自身本身，这个函数就是递归函数。

```python
def fattorial(n):
	"实现 n! "
	if n == 1：
		return 1
	return n * factorial(n-1)
	
print(factorial(5))  # 120
```
【例子】 斐波那契数列 f(n) = f(n-1) + f(n-2), f(0) = 0, f(1) = 1

```python
def recur_fibo(n):
	"斐波那契数列"
	if n < 2:
		return n
	return recur_fibo(n-1) + recur_fibo(n-2)
	
lst = list()
for k in range(11):
	lst.append(recur_fibo(k))
print(lst)
# [0,1,1,2,3,5,8,13,21,34,55]
```

# 匿名函数：Lambda 表达式

在python里 有两类函数：
- 第一类： 用 def 关键字 定义的正规函数
- 第二类： 用lambda 关键字定义的匿名函数

```python
lambda argument_list:expression
```

```python
sumary = lambda arg1,arg2: arg1+arg2
print(sumary(10,20))  # 30

func = lambda *args: sum(args)
print(func(1,2,3,4,5))  # 15
```
匿名函数 常用于 函数式编程的高阶函数
- 参数是函数 （filter, map）
- 返回值是函数 （closure）


如，在 `filter`和`map`函数中的应用：

- `filter(lamb_func, iterable)` 过滤序列，过滤掉不符合条件(lamb_func)的元素，返回一个迭代器对象，如果要转换为列表，可以使用 `list()` 来转换。

```python
odd_list = filter(lambda x: x % 2 == 1, range(10) )
print(list(odd_list))
# [1,3,5,7,9]
```
- `map(lamb_func, *iterables) ` 根据提供的函数，对指定序列做映射

```python
m1 = map(lambda x: x ** 2, range(1,6))
print(list(m1))
# [1,4,9,16,25]
```


[封装，继承，重写，多态]:https://www.zhihu.com/search?type=content&q=python%20%E5%A4%9A%E6%80%81


# 类与对象

### 对象 = 属性 + 方法

## self 
- Python  的self 相当于C++ 的 this 指针。

- python 魔法方法：
类有一个名为 __init__(self[,param1,param2...]) 的魔法方法，该方法在类实例化时会自动调用。

## 公有和私有
在python中定义私有变量，在 变量名 或 函数名 前面加 "_\_" (双下划线)，那么这个函数/变量 就变成私有了。

- 私有变量前面加双下划线 "_\_"
- 私有变量/函数不可以通过  类名.变量名/函数名  进行调用
- 私有变量也是可以通过其他方法调用，python对象私有化为伪私有化

```python
class Pig:
	# Pig 对象被调用时，会自动调用 __init__() 方法
	def __init__(self, color, age, weight):
		self.color = color
		self.age = age
		self.__weight = weight
		
	def How(self):
		print("This is a {} pig".format(self.color))

	def Quantity(self):
		if self.age > 30:
			print("The pig is too old!")
		else:
			print("haha,the pig is young")
	
	def __Price(self):
		price = self.__weight * 30 + self.age * (-1)
		print("The saleprice is ",price)
		return price
		
	def SalePrice(self):
		self.__Price()
		
pig = Pig("white", 30,100)
pig.How()
# This is a white pig

pig.Quantity()
# haha,the pig is young

pig.__Price()
# AttributeError: 'Pig' object has no attribute '__Price'

pig.SalePrice()
# The saleprice is  2970

pig._Pig__Price()
# The saleprice is  2970
```

# 继承

```python
class DerivedClassName(BaseClassName):
	statement-1
	.
	.
	.
	statement-N
```
- BaseClassName: 基类/父类； DerivedClassName：派生类/子类

- 如果 子类中定义与父类同名的方法或属性，则会自动覆盖父类对应的方法和属性

- 如果子类中定义了 __init__（）方法，则会自动覆盖父类的 __init__ 方法

- 如果同时需要初始化父类的__init__() 方法，可以通过两种方法：
1. 在DerivedClassName 的 __init__()函数中 添加 BaseClassName.__init__(self)
2. 利用 super函数，super().__init__()

```python
import random

class Fish:
	def __init__(self):
		self.x = random.randint(0,10)
		self.y = random.randint(0,10)
		
	def move(self):
		self.x -= 1
		print("我的位置",self.x, self.y)
		
class GoldFish(Fish):
	pass

class Shark(Fish):
	## Shark类 继承了Fish基类
	## Shark也重新定义了自己的 __init__ 类，则会自动覆盖基类的__init__类
	def __init__(self):
		self.hungry = True
		
	def eat(self):
		if self.hungry:
			print("I am hungry, i need something to eat")
			self.hungry = False
		else:
			print("I am eat up! I want to sleep now.")
			self.hungry = True


g = GoldFish()
g.move()

# 我的位置 9 0

s = Shark()
s.move()
# AttributeError: 'Shark' object has no attribute 'x'
# - 在这里，由于Shark对基类__init__进行了override，而在Shark中没有定义self.x 所以报错。
```

```python
## 对基类的__init__()方法进行调用，即可解决上述问题

import random

class Fish:
	def __init__(self):
		self.x = random.randint(0,10)
		self.y = random.randint(0,10)
		
	def move(self):
		self.x -= 1
		print("我的位置",self.x, self.y)

class Shark(Fish):
	## Shark类 继承了Fish基类
	## Shark也重新定义了自己的 __init__ 类，则会自动覆盖基类的__init__类
	def __init__(self):
        # 1. super()函数
# 		super().__init__()
        # 2. 调用未绑定的基类的__init__方法
		Fish.__init__(self)
		self.hungry = True
		
	def eat(self):
		if self.hungry:
			print("I am hungry, i need something to eat")
			self.hungry = False
		else:
			print("I am eat up! I want to sleep now.")
			self.hungry = True


s = Shark()
s.move()
# 我的位置 2 3
```
- python 虽然也支持多继承，但是一般不推荐使用。

# 魔法方法 __str__, __init__,__new__,等等


？？？？？？？？？？？？？？？？？？？？？？？？？？？？























