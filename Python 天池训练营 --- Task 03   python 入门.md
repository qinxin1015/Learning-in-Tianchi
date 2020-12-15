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














































