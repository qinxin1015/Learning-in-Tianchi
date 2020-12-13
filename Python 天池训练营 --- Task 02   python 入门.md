# python 天池训练营 task 02 - python基础

- 2020.12.13

简单数据类型
- 整型`<class 'int'>`
- 浮点型`<class 'float'>`
- 布尔型`<class 'bool'>`

容器数据类型
- 列表`<class 'list'>`
- 元组`<class 'tuple'>`
- 字典`<class 'dict'>`
- 集合`<class 'set'>`
- 字符串`<class 'str'>`

## 1. 列表
- 列表的定义
列表是有序集合，没有固定大小，能够保存任意数量任意类型的 Python 对象，语法为 `[元素1, 元素2, ..., 元素n]`。
- 列表的创建
```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(x, type(x))
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'] <class 'list'>

x = [2, 3, 4, 5, 6, 7]
print(x, type(x))
# [2, 3, 4, 5, 6, 7] <class 'list'>

x = list(range(1, 11, 2))
print(x, type(x))
# [1, 3, 5, 7, 9] <class 'list'>
```
- 利用推导式创建列表
```python
x = [i ** 2 for i in range(1, 10)]
print(x, type(x))
# [1, 4, 9, 16, 25, 36, 49, 64, 81] <class 'list'>

x = [i for i in range(100) if (i % 2) != 0 and (i % 3) == 0]
print(x, type(x))

# [3, 9, 15, 21, 27, 33, 39, 45, 51, 57, 63, 69, 75, 81, 87, 93, 99] <class 'list'>
```
注意：
由于list的元素可以是任何对象，因此**列表中所保存的是对象的指针**。即使保存一个简单的`[1,2,3]`，也有3个指针和3个整数对象。

列表不像元组，列表内容可更改 (mutable)，因此附加 (`append`, `extend`)、插入 (`insert`)、删除 (`remove`, `pop`) 这些操作都可以用在它身上。

#### 向列表中添加元素
- `list.append(obj)` 在列表末尾添加新的对象，只接受一个参数，参数可以是任何数据类型，被追加的元素在 list 中保持着原结构类型。
- `list.extend(seq)` 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）
- `list.insert(index, obj)` 在编号 `index` 位置插入 `obj`。

#### 删除列表中的元素
- `list.remove(obj)` 移除列表中某个值的第一个匹配项
- `list.pop([index=-1])` 移除列表中的一个元素（默认最后一个元素），并且**返回该元素的值**, pop有返回值，remove 没有。
- `del var1[, var2 ……]` 删除单个或多个对象。
- 如果你要从列表中删除一个元素，且不再以任何方式使用它，就使用`del`语句；如果你要在删除元素后还能继续使用它，就使用方法`pop()`。

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.remove('Monday')
print(x)  # ['Tuesday', 'Wednesday', 'Thursday', 'Friday']

x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
y = x.pop()
print(y)  # Friday
```
#### 获取列表中的元素
- 列表可以进行切片 （浅拷贝）

#### 列表的常用操作符
- 等号操作符：`==`  （只有成员、成员位置都相同时才返回True。）
- 连接操作符 `+`
- 重复操作符 `*`
- 成员关系操作符 `in`、`not in`
- 列表拼接有两种方式，用「加号 +」和「乘号 *」，前者首尾拼接，后者复制拼接。

```python
list1 = [123, 456]
list2 = [456, 123]
list3 = [123, 456]

print(list1 == list2)  # False
print(list1 == list3)  # True

list4 = list1 + list2  # extend()
print(list4)  # [123, 456, 456, 123]

list5 = list3 * 3
print(list5)  # [123, 456, 123, 456, 123, 456]

list3 *= 3
print(list3)  # [123, 456, 123, 456, 123, 456]

print(123 in list3)  # True
print(456 not in list3)  # False
```

#### 列表的其他方法
`list.count(obj)` 统计某个元素在列表中出现的次数
`list.index(x[, start[, end]])` 从列表中找出某个值第一个匹配项的索引位置
`list.reverse()` 反向列表中元素

`list.sort(key=None, reverse=False)` 对原列表进行排序。

- `key` -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
- `reverse` -- 排序规则，`reverse = True` 降序， `reverse = False` 升序（默认）。
- 该方法**没有返回值**，但是会对列表的对象进行排序。

## 2. 元组
- Python 的元组与列表类似，不同之处在于tuple被创建后就不能对其进行修改，类似字符串。
- 元组使用小括号，列表使用方括号。
- 元组与列表类似，也用整数来对它进行索引 (indexing) 和切片 (slicing)。

#### 元组相关的操作符
- Python 的元组与列表类似，不同之处在于tuple被创建后就不能对其进行修改，类似字符串。
- 元组使用小括号，列表使用方括号。
- 元组与列表类似，也用整数来对它进行索引 (indexing) 和切片 (slicing)。

#### 内置方法
元组大小和内容都不可更改，因此只有 `count` 和 `index` 两种方法。
#### 解压元组

```python
t = (1, 10.31, 'python')
(a, b, c) = t
print(a, b, c)
# 1 10.31 python

t = (1, 10.31, ('OK', 'python'))
(a, b, (c, d)) = t
print(a, b, c, d)
# 1 10.31 OK python
```
- 如果你只想要元组其中几个元素，用通配符「*」，英文叫 wildcard，在计算机语言中代表一个或多个元素。下例就是把多个元素丢给了 `rest` 变量。
```python
t = 1, 2, 3, 4, 5
a, b, *_ = t
print(a, b)  # 1 2
print(_)  # [3, 4, 5]
```

## 3. 字符串
#### 字符串的定义
Python 中字符串被定义为引号之间的字符集合。

- Python 的常用转义字符
转义字符 | 描述
:---:|---
`\\` | 反斜杠符号
`\'` | 单引号
`\"` | 双引号
`\n` | 换行
`\t` | 横向制表符(TAB)
`\r` | 回车

#### 字符串的常用内置方法
- `capitalize()` 将字符串的第一个字符转换为大写。
- `lower()` 转换字符串中所有大写字符为小写。
- `upper()` 转换字符串中的小写字母为大写。
- `swapcase()` 将字符串中大写转换为小写，小写转换为大写。
- `count(str, beg= 0,end=len(string))` 返回`str`在 string 里面出现的次数，如果`beg`或者`end`指定则返回指定范围内`str`出现的次数。
- `endswith(suffix, beg=0, end=len(string))` 检查字符串是否以指定子字符串 `suffix` 结束，如果是，返回 True，否则返回 False。如果 `beg` 和 `end` 指定值，则在指定范围内检查。
- `startswith(substr, beg=0,end=len(string))` 检查字符串是否以指定子字符串 `substr` 开头，如果是，返回 True，否则返回 False。如果 `beg` 和 `end` 指定值，则在指定范围内检查。
- `find(str, beg=0, end=len(string))` 检测 `str` 是否包含在字符串中，如果指定范围 `beg` 和 `end`，则检查是否包含在指定范围内，如果包含，**返回开始的索引值**，否则返回 -1。
- `rfind(str, beg=0,end=len(string))` 类似于 `find()` 函数，不过是从右边开始查找。
- `isnumeric()` 如果字符串中只包含数字字符，则返回 True，否则返回 False。
- `ljust(width[, fillchar])`返回一个原字符串左对齐，并使用`fillchar`（默认空格）填充至长度`width`的新字符串。
- `rjust(width[, fillchar])`返回一个原字符串右对齐，并使用`fillchar`（默认空格）填充至长度`width`的新字符串。
- `lstrip([chars])` 截掉字符串左边的空格或指定字符。
- `rstrip([chars])` 删除字符串末尾的空格或指定字符。
- `strip([chars])` 在字符串上执行`lstrip()`和`rstrip()`。
```python
str5 = ' I Love LsgoGroup '
print(str5.lstrip())  # 'I Love LsgoGroup '
print(str5.lstrip().strip('I'))  # ' Love LsgoGroup '
print(str5.rstrip())  # ' I Love LsgoGroup'
print(str5.strip())  # 'I Love LsgoGroup'
print(str5.strip().strip('p'))  # 'I Love LsgoGrou'
```
- `partition(sub)` 找到子字符串sub，把字符串分为一个三元组`(pre_sub,sub,fol_sub)`，如果字符串中不包含sub则返回`('原字符串','','')`。
- `rpartition(sub)`类似于`partition()`方法，不过是从右边开始查找。
- `replace(old, new [, max])` 把 将字符串中的`old`替换成`new`，如果`max`指定，则替换不超过`max`次。
```python
str5 = ' I Love LsgoGroup '
print(str5.strip().replace('I', 'We'))  # We Love LsgoGroup
```
- `split(str="", num)` 不带参数默认是以空格为分隔符切片字符串，如果`num`参数有设置，则仅分隔`num`个子字符串，返回切片后的子字符串拼接的列表。
```python
str5 = ' I Love LsgoGroup '
print(str5.strip().split())  # ['I', 'Love', 'LsgoGroup']
print(str5.strip().split('o'))  # ['I L', 've Lsg', 'Gr', 'up']

u = "www.baidu.com.cn"
# 使用默认分隔符
print(u.split())  # ['www.baidu.com.cn']

# 以"."为分隔符
print((u.split('.')))  # ['www', 'baidu', 'com', 'cn']

# 分割0次
print((u.split(".", 0)))  # ['www.baidu.com.cn']

# 分割一次
print((u.split(".", 1)))  # ['www', 'baidu.com.cn']

# 分割两次
print(u.split(".", 2))  # ['www', 'baidu', 'com.cn']

# 分割两次，并取序列为1的项
print((u.split(".", 2)[1]))  # baidu

# 分割两次，并把分割后的三个部分保存到三个变量
u1, u2, u3 = u.split(".", 2)
print(u1)  # www
print(u2)  # baidu
print(u3)  # com.cn

string = "hello boy<[www.baidu.com]>byebye"
print(string.split('[')[1].split(']')[0])  # www.baidu.com
print(string.split('[')[1].split(']')[0].split('.'))  # ['www', 'baidu', 'com']
```
- `splitlines([keepends])` 按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数`keepends`为 False，不包含换行符，如果为 True，则保留换行符。
```python
str6 = 'I \n Love \n LsgoGroup'
print(str6.splitlines())  # ['I ', ' Love ', ' LsgoGroup']
print(str6.splitlines(True))  # ['I \n', ' Love \n', ' LsgoGroup']
```
- `maketrans(intab, outtab)` 创建字符映射的转换表，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。
- `translate(table, deletechars="")` 根据参数`table`给出的表，转换字符串的字符，要过滤掉的字符放到`deletechars`参数中。
```python
str7 = 'this is string example....wow!!!'
intab = 'aeiou'
outtab = '12345'
trantab = str7.maketrans(intab, outtab)
print(str7.translate(trantab))  # th3s 3s str3ng 2x1mpl2....w4w!!!
print(trantab)  # {97: 49, 111: 52, 117: 53, 101: 50, 105: 51}
```
#### 字符串格式化
- **`format` 格式化函数**
```python
str8 = "{0} Love {1}".format('I', 'Lsgogroup')  # 位置参数
print(str8)  # I Love Lsgogroup

str8 = "{a} Love {b}".format(a='I', b='Lsgogroup')  # 关键字参数
print(str8)  # I Love Lsgogroup

str8 = '{0:.2f}GB'.format(27.658)  # 保留小数点后两位
print(str8)  # 27.66GB
```

## 4. 字典
- 字典是 Python 唯一的一个 <u>映射类型</u>，字符串、元组、列表属于<u>序列类型</u>。

#### 字典的内置方法
- `dict.fromkeys(seq[, value])` 用于创建一个新字典，以序列 `seq` 中元素做字典的键，`value` 为字典所有键对应的初始值。

```python
seq = ('name', 'age', 'sex')
dic1 = dict.fromkeys(seq)
print(dic1)
# {'name': None, 'age': None, 'sex': None}

dic2 = dict.fromkeys(seq, 10)
print(dic2)
# {'name': 10, 'age': 10, 'sex': 10}

dic3 = dict.fromkeys(seq, ('小马', '8', '男'))
print(dic3)
# {'name': ('小马', '8', '男'), 'age': ('小马', '8', '男'), 'sex': ('小马', '8', '男')}
```

- `dict.items()`以列表返回可遍历的 (键, 值) 元组数组。
- `dict.keys()`返回一个可迭代对象，可以使用 `list()` 来转换为列表，列表为字典中的所有键。
- `dict.values()`返回一个迭代器，可以使用 `list()` 来转换为列表，列表为字典中的所有值。

## 5. 集合
Python 中`set`与`dict`类似，也是一组`key`的集合，但不存储`value`。由于`key`不能重复，所以，在`set`中，没有重复的`key`。
- 集合的两个特点：无序 (unordered) 和唯一 (unique)。
注意，`key`为不可变类型，即可哈希的值。
```python
num = {}
print(type(num))  # <class 'dict'>
num = {1, 2, 3, 4}
print(type(num))  # <class 'set'>
```

#### 集合的内置方法
- `set.add(elmnt)`用于给集合添加元素，如果添加的元素在集合中已存在，则不执行任何操作。
```python
fruits = {"apple", "banana", "cherry"}
fruits.add("orange")
print(fruits)  
# {'orange', 'cherry', 'banana', 'apple'}

fruits.add("apple")
print(fruits)  
# {'orange', 'cherry', 'banana', 'apple'}
```
- `set.update(set)`用于修改当前集合，可以添加新的元素或集合到当前集合中，如果添加的元素在集合中已存在，则该元素只会出现一次，重复的会忽略。
```python
x = {"apple", "banana", "cherry"}
y = {"google", "baidu", "apple"}
x.update(y)
print(x)
# {'cherry', 'banana', 'apple', 'google', 'baidu'}

y.update(["lsgo", "dreamtech"])
print(y)
# {'lsgo', 'baidu', 'dreamtech', 'apple', 'google'}
```
- `set.remove(item)` 用于移除集合中的指定元素。如果元素不存在，则会发生错误。
- `set.discard(value)` 用于移除指定的集合元素。`remove()` 方法在移除一个不存在的元素时会发生错误，而 `discard()` 方法不会。
- `set.pop()` 用于随机移除一个元素。

## 6. 序列
#### 针对序列的内置函数
- `list(sub)` 把一个可迭代对象转换为列表。
- `tuple(sub)` 把一个可迭代对象转换为元组。
- `str(obj)` 把obj对象转换为字符串

- `len(s)` 返回对象（字符、列表、元组等）长度或元素个数。
- `max(sub)`返回序列或者参数集合中的最大值
- `min(sub)`返回序列或参数集合中的最小值
- `sum(iterable[, start=0])` 返回序列`iterable`与可选参数`start`的总和。

- `sorted(iterable, key=None, reverse=False) ` 对所有可迭代的对象进行排序操作。
    - `iterable` -- 可迭代对象。
    - `key` -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
    - `reverse` -- 排序规则，`reverse = True` 降序 ， `reverse = False` 升序（默认）。
    - 返回重新排序的列表。
```python
x = [-8, 99, 3, 7, 83]
print(sorted(x))  # [-8, 3, 7, 83, 99]
print(sorted(x, reverse=True))  # [99, 83, 7, 3, -8]

t = ({"age": 20, "name": "a"}, {"age": 25, "name": "b"}, {"age": 10, "name": "c"})
x = sorted(t, key=lambda a: a["age"])
print(x)
# [{'age': 10, 'name': 'c'}, {'age': 20, 'name': 'a'}, {'age': 25, 'name': 'b'}]
```

- `zip(iter1 [,iter2 [...]])`
    - 用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的对象，这样做的好处是节约了不少的内存。
    - 我们可以使用 `list()` 转换来输出列表。
    - 如果各个迭代器的元素个数不一致，则返回列表长度与最短的对象相同，利用 `*` 号操作符，可以将元组解压为列表。

```python
a = [1, 2, 3]
b = [4, 5, 6]
c = [4, 5, 6, 7, 8]

zipped = zip(a, b)
print(zipped)  # <zip object at 0x000000C5D89EDD88>
print(list(zipped))  # [(1, 4), (2, 5), (3, 6)]
zipped = zip(a, c)
print(list(zipped))  # [(1, 4), (2, 5), (3, 6)]

a1, a2 = zip(*zip(a, b))
print(list(a1))  # [1, 2, 3]
print(list(a2))  # [4, 5, 6]
```












