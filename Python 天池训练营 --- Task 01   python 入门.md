# Python 天池训练营 --- Task 01   python 入门
- 2020.12.12

## 1.变量，运算符，数据类型

### 1.运算符

#### 算术运算符
操作符 | 名称 | 示例
:---:|:---:|:---:
`+` | 加 | `1 + 1`
`-` | 减 | `2 - 1`
`*` | 乘 | `3 * 4`
`/` | 除 | `3 / 4`
`//`| 整除（地板除，取商）| `3 // 4`
`%` | 取余| `3 % 4`
`**`| 幂 | `2 ** 3`

#### 比较运算符

操作符 | 名称 | 示例
:---:|:---:|:---:
`>` |大于| `2 > 1`
`>=`|大于等于| `2 >= 4`
`<` |小于| `1 < 2`
`<=`|小于等于| `5 <= 2`
`==`|等于| `3 == 4`
`!=`|不等于| `3 != 5`

#### 逻辑运算符

操作符 | 名称 | 示例
:---:|:---:|:---:
`and`|与| `(3 > 2) and (3 < 5)`
`or` |或| `(1 > 3) or (9 < 2)`
`not`|非| `not (2 > 1)`


#### 位运算符

操作符 | 名称 | 示例
:---:|:---:|:---:
`~` |按位取反|`~4`
`&` |按位与  |`4 & 5`
`|` |按位或  |`4 | 5`
`^` |按位异或|`4 ^ 5`
`<<`|左移    |`4 << 2`
`>>`|右移    |`4 >> 2`

#### 其他运算符

操作符 | 名称 | 示例
:---:|:---:|:---:
`in`|存在| `'A' in ['A', 'B', 'C']`
`not in`|不存在|`'h' not in ['A', 'B', 'C']`
`is`|是| `"hello" is "hello"`
`not is`|不是|`"hello" is not "hello"`

```
a = "hello"
b = "hello"
print(a is b, a == b)  # True True
print(a is not b, a != b)  # False False
```
- a, b 都是str类型，是不可变类型，所以a,b的指针指向的是相同的地址。

```
a = ["hello"]
b = ["hello"]
print(a is b, a == b)  # False True
print(a is not b, a != b)  # True False
```
- a, b 是list类型，list 是可变类型，所以，a,b 各自指向自己的地址来保存各自的元素。


<b>运算符的优先级</b>

| 运算符 | 描述 |
|-----|-----|
| ** | 指数（最高优先级）   |
| ~+- | 按位翻转，一元加号和减号 |
| * / % // | 乘，除，取模和取整除）   |
| + - | 加法减法 |
| >> << | 右移，左移运算符 |
|&| 位‘AND’|
| ^\| | 位运算符  |
| <=<>>=| 比较运算符 |
| <>==!= | 等于运算符  |
| =%=/=//=-=+=*=**= | 赋值运算符 |
| is is not | 身份运算符   |
| in not in | 成员运算符 |
| not and or | 逻辑运算符   |


#### 2. 数据类型和转换

类型 | 名称 | 示例
:---:|:---:|:---:
int | 整型 `<class 'int'>`| `-876, 10`
float | 浮点型`<class 'float'>`| `3.149, 11.11`
bool | 布尔型`<class 'bool'>` | `True, False`

- **Python 里面万物皆对象（object）**，整型也不例外，只要是对象，就有相应的**属性** （attributes） 和**方法**（methods）。

```
b = dir(int)
print(b)

# ['__abs__', '__add__', '__and__', '__bool__', '__ceil__', '__class__',
# '__delattr__', '__dir__', '__divmod__', '__doc__', '__eq__',
# '__float__', '__floor__', '__floordiv__', '__format__', '__ge__',
# '__getattribute__', '__getnewargs__', '__gt__', '__hash__',
# '__index__', '__init__', '__init_subclass__', '__int__', '__invert__',
# '__le__', '__lshift__', '__lt__', '__mod__', '__mul__', '__ne__',
# '__neg__', '__new__', '__or__', '__pos__', '__pow__', '__radd__',
# '__rand__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__',
# '__rfloordiv__', '__rlshift__', '__rmod__', '__rmul__', '__ror__',
# '__round__', '__rpow__', '__rrshift__', '__rshift__', '__rsub__',
# '__rtruediv__', '__rxor__', '__setattr__', '__sizeof__', '__str__',
# '__sub__', '__subclasshook__', '__truediv__', '__trunc__', '__xor__',
# 'bit_length', 'conjugate', 'denominator', 'from_bytes', 'imag',
# 'numerator', 'real', 'to_bytes']
```

- **属性/方法 VS 函数：方法是可以直接调用的，函数是需要传参的 **

<b>布尔型</b>

布尔 (boolean) 型变量只能取两个值，`True` 和 `False`。当把布尔型变量用在数字运算中，用 `1` 和 `0` 代表 `True` 和 `False`。

- 有时候，我们可以用布尔类型来判断满足条件的样本，从而进行计数。如，在IMD 中，可以用bool类型判断是否超过cutoff值，并对此进行count()计数，得到超过cutoff值的样本数

```python
print(isinstance(1, int))  # True
print(isinstance(5.2, float))  # True
print(isinstance(True, bool))  # True
print(isinstance('5.2', str))  # True
```

- `type()` 不会认为子类是一种父类类型，不考虑继承关系。
- `isinstance()` 会认为子类是一种父类类型，考虑继承关系。

如果要判断两个类型是否相同推荐使用 `isinstance()`。

#### 3. 利用位运算实现快速计算

通过 `<<`，`>>` 快速计算2的倍数问题。

```python
n << 1 -> 计算 n*2
n >> 1 -> 计算 n/2，负奇数的运算不可用
n << m -> 计算 n*(2^m)，即乘以 2 的 m 次方
n >> m -> 计算 n/(2^m)，即除以 2 的 m 次方
1 << n -> 2^n
```

## 2.条件语句

#### 1. if 语句

```python
if expression:
    expr_true_suite
```
```python
if 2 > 1 and not 2 > 3:
    print('Correct Judgement!')

# Correct Judgement!
```
#### 2. if - else 语句
```python
if expression:
    expr_true_suite
else:
    expr_false_suite
```
```python
temp = input("猜一猜小姐姐想的是哪个数字？")  ## input() 函数 返回的是 str 类型。
guess = int(temp) # input 函数将接收的任何数据类型都默认为 str。

if guess > 8:
    print("大了，大了")
else:
    if guess == 8:
        print("你太了解小姐姐的心思了！")
        print("哼，猜对也没有奖励！")
    else:
        print("小了，小了")
print("游戏结束，不玩儿啦！")
```
#### 3. if - elif - else 语句

```python
if expression1:
    expr1_true_suite
elif expression2:
    expr2_true_suite
    .
    .
elif expressionN:
    exprN_true_suite
else:
    expr_false_suite
```
```python
temp = input('请输入成绩:')
source = int(temp)
if 100 >= source >= 90:
    print('A')
elif 90 > source >= 80:
    print('B')
elif 80 > source >= 60:
    
    print('C')
elif 60 > source >= 0:
    print('D')
else:
    print('输入错误！')
```

#### 4. assert 关键词

- `assert`这个关键词我们称之为“断言”，当这个关键词后边的条件为 False 时，程序自动崩溃并抛出`AssertionError`的异常。
- 在进行单元测试时，可以用来在程序中置入检查点，只有条件为 True 才能让程序正常工作。

## 循环语句 while; for;
#### 1. while 语句
```python
while 布尔表达式:
    代码块
```
#### 2.while - else 语句
```python
while 布尔表达式:
    代码块
else:
    代码块
```

当`while`循环正常执行完的情况下，执行`else`输出，如果`while`循环中执行了跳出循环的语句，比如 `break`，将不执行`else`代码块的内容。   
```python
## while-else 循环语句， 可以用于循环结束后的提醒，也可以用于检查循环跳出时的状态测试。
count = 0
while count < 5:
    print("%d is  less than 5" % count)
    count = count + 1
else:
    print("%d is not less than 5" % count)
    
# 0 is  less than 5
# 1 is  less than 5
# 2 is  less than 5
# 3 is  less than 5
# 4 is  less than 5
# 5 is not less than 5
```
```python
count = 0
while count < 5:
    print("%d is  less than 5" % count)
    count = 6
    break
else:
    print("%d is not less than 5" % count)

# 0 is  less than 5
```

#### 3. for 循环语句
```python
for 迭代变量 in 可迭代对象:
    代码块
```

#### 4. for - else 循环

```python
for 迭代变量 in 可迭代对象:
    代码块
else:
    代码块
```
- 与`while - else`语句类似。
当`for`循环正常执行完的情况下，执行`else`输出，如果`for`循环中执行了跳出循环的语句，比如 `break`，将不执行`else`代码块的内容

#### 5. enumerate()函数

```python
enumerate(sequence, [start=0])
```
- sequence：一个序列、迭代器或其他支持迭代对象。
- start：下标起始位置。
- 返回 enumerate(枚举) 对象


**`enumerate()`与 for 循环的结合使用。**

```python
for i, a in enumerate(A)
    do something with a  
```
用 `enumerate(A)` 不仅返回了 `A` 中的元素，还顺便给该元素一个索引值 (默认从 0 开始)。此外，用 `enumerate(A, j)` 还可以确定索引起始值为 `j`。

```python
languages = ['Python', 'R', 'Matlab', 'C++']
for language in languages:
    print('I love', language)
print('Done!')
# I love Python
# I love R
# I love Matlab
# I love C++
# Done!


for i, language in enumerate(languages, start=2):
    print(i, 'I love', language)
print('Done!')
# 2 I love Python
# 3 I love R
# 4 I love Matlab
# 5 I love C++
# Done!
```

#### 6. break 语句

`break`语句可以跳出当前所在层的循环。

```python
import random
secret = random.randint(1, 10) #[1,10]之间的随机数

while True:
    temp = input("猜一猜小姐姐想的是哪个数字？")
    guess = int(temp)
    if guess > secret:
        print("大了，大了")
    else:
        if guess == secret:
            print("你太了解小姐姐的心思了！")
            print("哼，猜对也没有奖励！")
            break
        else:
            print("小了，小了")
print("游戏结束，不玩儿啦！")
```

#### 7. pass 语句

`pass` 语句的意思是“不做任何事”，如果你在需要有语句的地方不写任何语句，那么解释器会提示出错，而 `pass` 语句就是用来解决这些问题的。

```python
def a_func():
    pass
```
`pass`是空语句，不做任何操作，只起到**占位**的作用，其作用是为了保持程序结构的完整性。尽管`pass`语句不做任何操作，但如果暂时不确定要在一个位置放上什么样的代码，可以先放置一个`pass`语句，让代码可以正常运行。


#### 8. 推导式

**列表推导式**

```python
[ expr for value in collection [if condition] ]
```
```python
x = [i ** 2 for i in range(1, 10)]
print(x)
# [1, 4, 9, 16, 25, 36, 49, 64, 81]
```

```python
x = [(i, i ** 2) for i in range(6)]
print(x)

# [(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
```

```python
x = [i for i in range(100) if (i % 2) != 0 and (i % 3) == 0]
print(x)

# [3, 9, 15, 21, 27, 33, 39, 45, 51, 57, 63, 69, 75, 81, 87, 93, 99]
```

```python
a = [(i, j) for i in range(0, 3) for j in range(0, 3)]
print(a)

# [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)]
```

```python
a = [(i, j) for i in range(0, 3) if i < 1 for j in range(0, 3) if j > 1]
print(a)

# [(0, 2)]
```

**元组推导式**

```python
( expr for value in collection [if condition] )
```

```python
a = (x for x in range(10))
print(a)

# <generator object <genexpr> at 0x0000025BE511CC48>

print(tuple(a))

# (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
```
**字典推导式**

```python
{ key_expr: value_expr for value in collection [if condition] }
```

```python
b = {i: i % 2 == 0 for i in range(10) if i % 3 == 0}
print(b)
# {0: True, 3: False, 6: True, 9: False}
```


**集合推导式**

```
{ expr for value in collection [if condition] }
```
```python
c = {i for i in [1, 2, 3, 4, 5, 5, 6, 4, 3, 2, 1]}
print(c)
# {1, 2, 3, 4, 5, 6}
```

## 异常处理

异常就是运行期检测到的错误。计算机语言针对可能出现的错误定义了异常类型，某种错误引发对应的异常时，异常处理程序将被启动，从而恢复程序的正常运行。

![Python异常体系中的部分关系](https://img-blog.csdnimg.cn/20200710131404548.png)

---
#### 1. try - except 语句
```python
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
```

try 语句按照如下方式工作：
- 首先，执行`try`子句（在关键字`try`和关键字`except`之间的语句）
- 如果没有异常发生，忽略`except`子句，`try`子句执行后结束。
- 如果在执行`try`子句的过程中发生了异常，那么`try`子句余下的部分将被忽略。如果异常的类型和`except`之后的名称相符，那么对应的`except`子句将被执行。最后执行`try - except`语句之后的代码。
- 如果一个异常没有与任何的`except`匹配，那么这个异常将会传递给上层的`try`中。

```python
try:
    f = open('test.txt')
    print(f.read())
    f.close()
except OSError:
    print('打开文件出错')

# 打开文件出错
```
处理多分支可能异常
```python
try:
    int("abc")
    s = 1 + '1'
    f = open('test.txt')
    print(f.read())
    f.close()
except OSError as error:
    print('打开文件出错\n原因是：' + str(error))
except TypeError as error:
    print('类型出错\n原因是：' + str(error))
except ValueError as error:
    print('数值出错\n原因是：' + str(error))

# 数值出错
# 原因是：invalid literal for int() with base 10: 'abc'
```
---
#### 2. try - except - finally 语句
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
finally:
    无论如何都会被执行的代码

不管`try`子句里面有没有发生异常，`finally`子句都会执行。

```python
def divide(x, y):
    try:
        result = x / y
        print("result is", result)
    except ZeroDivisionError:
        print("division by zero!")
    finally:
        print("executing finally clause")


divide(2, 1)
# result is 2.0
# executing finally clause
divide(2, 0)
# division by zero!
# executing finally clause
divide("2", "1")
# executing finally clause
# TypeError: unsupported operand type(s) for /: 'str' and 'str'
```
---
#### 3. try - except - else 语句

如果在`try`子句执行时没有发生异常，Python将执行`else`语句后的语句。
- 注意： 只有 try - except - else 语句，~~没有 try - else 语句~~

```python
try:
    检测范围
except:
    出现异常后的处理代码
else:
    如果没有异常执行这块代码
```

使用`except`而不带任何异常类型，这不是一个很好的方式，我们不能通过该程序识别出具体的异常信息，因为它捕获所有的异常。

try:
    检测范围
except(Exception1[, Exception2[,...ExceptionN]]]):
   发生以上多个异常中的一个，执行这块代码
else:
    如果没有异常执行这块代码

```python
try:
    fh = open("testfile.txt", "w")
    fh.write("这是一个测试文件，用于测试异常!!")
except IOError:
    print("Error: 没有找到文件或读取文件失败")
else:
    print("内容写入文件成功")
    fh.close()

# 内容写入文件成功
```

---
#### 3. raise语句

Python 使用`raise`语句抛出一个指定的异常。
```python
try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')
    
# An exception flew by!
```














































