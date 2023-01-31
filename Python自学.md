# Python自学

> b站视频自学的
>
> 遗留问题：
>
> 1. ...

## 基本内容

### 字面量

> 在代码中写下来的固定的值

例如：

* 数字Number（整数int，浮点数float，复数complex，布尔bool）
* 字符串String（在python中被双引号包围起来的都是字符串）
* 列表List
* 元组Tuple
* 集合Set
* 字典Dictionary

```python
90

1.901

"你好，世界！"

print(1.901)
print(90)
print("你好，世界！")

print(1.901, 90, "你好，世界！")

print(520, 1314, "GG")

```

### 变量

> 在python中，不需要提前为变量声明类型，因为变量无类型，变量存储的数据有类型

```python
a = 100
b = "你好，马里奥"
```

* 我们可以用type()函数查看数据类型

```python
Variable_int = 100
Variable_float = 100.1
Variable_str = "你好"
# 存type()语句返回值的变量
Variable_type = type(a)

# 以上四个数据用type()函数求出比数据类型后，用变量接收的值如下
# <class 'int'>
# <class 'float'>
# <class 'str'>
# <class 'type'>
```

* 标识符命名规范
   1. 见名知意思
   2. 用下划线分隔开不同的含义
   3. 字母全小写

### 字符串

> 区别于数据容器中的字符串
```python
str_test = '这是一个字符串'
str_test = "这是一个字符串"
str_test = """这是一个字符串"""
```
* 如果想让字符串中出现 ' 或 " 或 """，我们需要用转译字符 '\'
```python
str_test = "\"你好\"\n你好"
```
* 在一个字符串中，如果我们还不知道某个位置应该是什么，那可以用占位符
* 有三个占位符 %s %d %f
```python
# %s 预留的位置是给字符串的
dd = "世界"
ff = "你好%s" % dd
# %d 预留的位置是给整数的
# %f 预留的位置是给浮点数的
```
* 快速格式化方式
* 取格式format的首字母f
* 快速格式化的特点是不限制数据类型，不做精度控制，原本是什么样就输出什么样
```python
i1 = 2002
i2 = 12.0
ss = f"今天是{i1}年的第{i2}天"
```
* input() 获取用键盘输入的值
* input() 获取的数据的数据类型一定是字符串类型
```python
 b = input()
```
* 字符串可以进行大小比较，比较的过程是运用ASCII表进行比较
* 是从左向右比，如果一样，就比下一个
```python
if 'a' > 'A':
    print('a')
else:
    print('A')
# a

if 'b' > 'Asd':
    print('b')
else:
    print('Asd')
# b
```

### 数据类型转换

* 三个基础的数据类型转换的语句
* 转整数int()
* 转浮点数float()
* 转字符串str()
```python
a = 100
print(type(a), a)
# 可以直接这样写，因为在python中变量没有类型，只有数据有类型
a = float(a)
print(type(a), a)

# float转int可以直接去掉小数
a = 100.1
print(int(a))
```

### 数据容器


### 运算符

* 加 '+'
```python
add1 = 100
add2 = 200
add = add1 + add2
print(add)

# 300
```
* 减 '-'
```python
sub1 = 100
sub2 = 200
sub = sub1 - sub2
print(sub)

# -100
```
* 乘 '*'
```python
mul1 = 100
mul2 = 200
mul = mul1 * mul2
print(mul)

# 20000
```
* 除 '/'
```python
div1_1 = 100
div2_1 = 200
div_1 = div1_1 / div2_1
print(div_1)

# 0.5
```
* 取整除 '//'
```python
div1_2 = 123
div2_2 = 122
div_2_1 = div1_2 / div2_2
div_2_2 = div1_2 // div2_2
print(div_2_1, div_2_2)

# 1.0081967
# 1
```
* 取余 '%'
```python
div1_3 = 123
div2_3 = 122
div_3 = div1_3 % div2_3
print(div_3)

# 1
```
* 指数 '**'
```python
index = 2**10
print(index)

# 1024
```
* 以上所有运算符都可以和'='结合
* 例如 'a += b' => 'a = a + b'
```python
index = 2
index **= 2
print(index)

# 4
```

### 循环

* for循环的格式
```python
for x in y:
    ...
```
* x为临时变量
* y为待处理数据集（序列类型：内容可以被一个个取出）（字符串、列表、元组）
* 注意：y如果为int会报错，int对象不可迭代  int object is not iterable，float同理

```python
# 打印九九乘法表
for x in range(1, 10):
    s = ""
    for y in range(1, x+1):
        s += f"{y}*{x}={x*y}\t"
    print(s)
```

* while循环

```python
a = 0
while a < 10:
    print(a)
    a += 1
```
* continue 中断本次循环，执行下一次
* break 结束循环

### 函数

> 先定义后使用

```
def function_name(parameter):
    """
    本函数在学习函数时使用
    :param parameter:
    :return:
    """
    print(f"这里是函数的主体")
    print(f"本函数有参数，参数为{parameter}")
    # 可以没有返回值
    return -1
```
* 函数可以没有参数，也可以没有返回值
* 但是后声明的函数会把先声明的同名函数覆盖掉，后面再调用这个名字的函数时，会调用后声明的，即便两个同名函数的参数不同
* 存在一个特殊的字面量None。对于没有返回值的函数，返回的值为None

* None在进行布尔判断是与False等价，也就是数 None == False =True

* 如果想在函数内部修改全局变量，需要用到global关键字

```python
num = 200


def function_keyword_global():
    global num
    num = 300
```

* 对于一个函数,如果参数有默认值,那么在调用时可以不给参数赋值
* 这种方式，在很多系统自带的函数还有软件包内的函数经常用到
* 例如在图形设计时，标题颜色等参数一般都有默认值，但是也可也用关键字传参的方式更改这些默认值，使其达到你想要的效果。

```python
def dd(a, i="word", j="hello"):
    """
    一个有默认值的参数
    :param a:
    :param j:
    :param i:
    :return: None
    """
    print(f"dd函数，用来测试参数传入的一个参数:{a}")
    print(f"{j},{i}")
```

* 在一个函数中我们可以有带默认值的参数，也可以有不带默认值的参数
* 但是如果有不带默认值的参数，在传参时一定要写在有默认值参数的前面，并且传参顺序严格按照传入的顺序
* 也可以用关键字传参的方法传入，就不用在意顺序

```python
# # 在传参时，我们可以这样写，可以让传参更加清晰
# dd(4, i="python")
# dd(5, i="python", j="study")
# # 如果用键值传参，还可以不按顺序
# dd(6, j="study", i="python")
# # 同时，用键值传参和直接传参可以混用，不用键值指向的参数就会按顺序传入，但如果这样写就要注意顺序，否则就会出错
# # 不用关键字传参，则参数会严格遵从顺序，就比如函数为f(x, y, z)，传参为f(1, 2, z=3)，会把1，2按照顺序传给x，y，然后在把z=3传给z
# # 如果传参这样写f(1, 2, x=3)就会报错，因为这样1会传给x，后面有会传给x一个值，报错如下
# # dd() got multiple values for argument 'i'
# dd(7, "study", j="python")
```

* 关键字传参和普通的传参方法可以混用，但是直接传参一定要写在前面，并且要注意顺序

* 一个函数可以有多个返回值

```python
def function_return_more():
    return 1, 2
```

* 可以用两个变量接受这个函数的返回值

```python
x, y = function_return_more()

# x, y存储数据的数据类型都是int
```

* 也可也用一个变量接受，那么函数返回的就是一个元组

```python
x = function_return_more()

# x存储数据的数据类型是tuple
```

* 不定长参数传参

```python
# 不定长参数：参数的数量可以是任意个
# 位置传递的不定长
def f_para_countless1(*para):
    """

    :param para:一个元组
    :return:
    """
    print(para)

    
f_para_countless1(1)
f_para_countless1(1, 'hello')
# 数据类型是元组
```

```python
# 键值传递的不定长
def f_para_countless2(**key_para):
    """

    :param key_para: 一个字典
    :return:
    """
    print(key_para)


# # f_para_countless2() takes 0 positional arguments but 2 were given
# f_para_countless2(1, 2)
f_para_countless2(name='ljr', age=20)
# 数据类型是字典
```

* 同时，函数也可以作为参数参与传参

```python
def f_add(x, y):
    return x+y


def f_sub(x, y):
    return x-y


def f_mul(x, y):
    return x*y


def f_div(x, y):
    return x/y


def f_operation(algorithm, x, y):
    print(algorithm(x, y))


# 用函数做参数
# 传入的是一个运算逻辑
f_operation(f_mul, 20, 60)
```

* 匿名函数
* lambda定义，仅在这次调用中使用
* 不用return，默认直接return的
* 只能写一行
```python
# lambda x, y: x+y 取代了上面传函数中的传加法逻辑
f_operation(lambda x, y: x+y, 20, 60)
```

