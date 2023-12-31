---
title: "python基础知识复习"
subtitle: ""
date: 2023-12-29T22:53:14+08:00
lastmod: 2023-12-29T22:53:14+08:00
draft: true

tags: []
categories: ["python"]
---
python常用知识点复习

## 数字与序列

### 数据类型

数值类型： 整数 分数 浮点数 复数 布尔型 字符串

序列类型： 字符串 列表(list) 元组(tuple)

映射和集合类型： 字典(dict) 集合(set) 冻结集(frozenset)

#### 整数和分数

* 整数默认十进制，可以使用内建函数 `bin` `oct` `hex`将整数转换成二进制、八进制、十六进制的字符串

```python
>>> bin(5) #二进制 0-1
'0b101'
>>> oct(9) #八进制 0-7
'0o11'
>>> hex(23) #十六进制 0-9 a-f(A-F)
'0x17'
```

* 分数 fractions标准库中Fraction类提供分数计算

```python
>>> from fractions import Fraction
>>> x = Fraction(2,5)
>>> y = Fraction(3,7)
>>> x+y
Fraction(29, 35)
>>> x/y
Fraction(14, 15)
>>> x**2
Fraction(4, 25)
>>> y.numerator #分子
3
>>> y.denominator #分母
7
```

* 浮点数转换成分数

```python
>>> x = 2.3
>>> x.as_integer_ratio()
(2589569785738035, 1125899906842624)
```

* 整数型位运算

是对整数在二进制表示下的位进行的运算。主要有以下几种：

1. 按位与（&）：如果两个相应的二进制位都为1，则该位的结果值为1，否则为0。
2. 按位或（|）：两个相应的二进制位中只要有一个为1，该位的结果值为1。
3. 按位异或（^）：两个相应的二进制位值相同则为0，不同则为1。
4. 按位取反（~）：对数据的每个二进制位取反,即把1变为0,把0变为1。
5. 左移（<<）：把<<左边的数据的各二进制位全部左移若干位，右边空出的位用0填充。
6. 右移（>>）：把>>左边的数据的各二进制位全部右移若干位，左边空出位用0的填充或者用符号位填充，具体情况取决于语言规定。

* 码值转换

#### 布尔型

* `bool()` 求布尔值
* 非零数字与非空集合布尔值都是 `True`
* 成员操作符 `in` 返回布尔值
* 布尔类型对象的三个操作符：`and`  `or` `not`

#### 浮点数与复数

* 浮点数64位，52位表示底，11为表示指数，剩下一位表示符号正负
* 复数为两个浮点数组成的有序数对，实部和虚部都是浮点数
* 访问实部、虚部、共轭复数、模
  ```python
  >>> acomplex = 3+4j   
  >>> acomplex.real#实部
  3.0
  >>> acomplex.imag#虚部 
  4.0
  >>> acomplex.conjugate
  <built-in method conjugate of complex object at 0x0000025F75FFA250>
  >>> acomplex.conjugate()#共轭复数
  (3-4j)
  >>> abs(acomplex) #求模
  5.0
  ```
* 浮点数操作函数在math模块中，复数操作的函数在cmath模块中
  ```python
  >>> import math
  >>> import cmath
  >>> from cmath import *
  ```

#### 字符串

* 赋值

  ```python
  >>> str1 = 'dasf' 
  >>> str2 = '1564 s' 
  >>> x = str1[0] 
  >>> x
  'd'
  >>> str1 + str2 #拼接
  'dasf1564 s'
  >>> str1 * 3
  'dasfdasfdasf'
  >>> str1[0] = 'd' #error 字符串内容不可修改
  Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
  TypeError: 'str' object does not support item assignment
  ```
* 操作
  格式化输出字符串

  ```python
  >>> print('The total is %0.2f' %56.432141) 
  The total is 56.43
  ```

  常见的格式说明符有以下几种：

  * `%s`：字符串。使用str()将任何Python对象转换为字符串。
  * `%d`：整数。十进制整数。
  * `%f`：浮点数。默认保留6位小数，可以通过 `.2f`这样的形式控制小数位数。
  * `%x`：十六进制数。使用小写字母。
  * `%X`：十六进制数。使用大写字母。
  * `%e`：科学计数法表示的浮点数，使用小写的'e'。
  * `%E`：科学计数法表示的浮点数，使用大写的'E'。
  * `%g`：根据值的大小决定使用%f或%e。
  * `%G`：类似%g，但使用大写字母。

#### 列表

列表（list）是一种有序的集合，可以随时添加和删除其中的元素

1. 添加元素，`append()`末尾追加元素 `insert()`在指定位置插入元素

   ```python
   my_list.append('d')
   my_list.insert(1, 'inserted') #insert(插入索引位置， 插入元素)
   ```

   合并列表,会修改原列表

   ```python
   list1 = [1, 2, 3]
   list2 = [4, 5, 6]
   list1.extend(list2)
   print(list1)  # 输出：[1, 2, 3, 4, 5, 6]
   ```
2. 删除元素，`del` `pop()` 或者 `remove()`

   ```python
   del my_list[0]
   my_list.pop()
   my_list.remove('b')
   ```
3. 列表切片访问
4. 列表循环
5. 列表推导式：简洁的方法创建列表

   `squares = [x**2 for x in range(10)]`
6. 列表排序

   ```python
   my_list.sort()
   new_list = sorted(my_list)
   ```

#### 元组

元组（tuple）是一种有序的不可变序列，一旦创建就不能修改，是一种只读的数据结构

1. 创建元组：使用圆括号 `()`来创建元组，元素之间用逗号 `,`分隔

   1. 创建只包含一个元素的元组，你需要在元素后面添加一个逗号 `,`。这是因为括号 `()`可以用于定义元组，也可以用于改变运算的优先级
2. 访问元组元素：通过索引来访问元组中的元素，索引从0开始
3. 不可变性：元组是不可变的，这意味着你不能在元组中添加、删除或修改元素

   元组中的元素如果是可变的（如列表），那么你可以修改这个元素

   ```
   >>> h = (5, [1,5], ('saf', 45, 4))
   >>> h[1][1] = 6
   >>> h
   (5, [1, 6], ('saf', 45, 4))
   ```
4. 元组切片：可以使用切片来访问元组的一部分
5. 可以使用for循环来遍历元组中的每一个元素
6. 元组解包：如果你有一个包含多个元素的元组，你可以在一行中将这些元素赋值给多个变量

   ```python
   >>> x,y,z = (1, 3, 53)  
   >>> x
   1
   >>> y
   3
   >>> z
   53
   ```
7. 元组和函数：元组经常用于Python函数的返回值，因为函数可以返回一个元组，从而一次返回多个值

   ```python
   def min_max(items):
       return min(items), max(items)

   print(min_max([1, 2, 3, 4, 5]))  # 输出：(1, 5)
   ```
8. 可哈希，可以作为字典的键key

## 流程控制、字典与集合

### 流程控制

条件语句

* `if...else` `if...elif...`语句
* 布尔表达式 -- 逻辑操作符 `and` `or` `not`

循环语句

* `while` 循环
* `for` 循环，遍历序列元素

控制流程

* `continue` 跳过循环剩余语句，继续下一轮循环
* `break` 终止循环语句
* `pass` 什么都不做
* `match-case` (python 3.10,不做要求)

### 字典

### 集合
