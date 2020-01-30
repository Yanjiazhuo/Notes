# Python

## Mac OS下安装Python并配置环境变量

MAC 系统一般都自带有 Python2.x版本的环境。从官网下载推荐的python3.8.1的版本。
- 环境变量配置：程序和可执行文件可以在许多目录，而这些路径很可能不在操作系统提供可执行文件的搜索路径中。
在Mac OS中，安装程序的过程中改变了python的安装路径。如果你需要在其他目录引用Python，必须在path中添加Python目录。

配置前：在终端输入
```python
python --version
```
会出现 Python2.x版本
```python
which python
```
出现 
```
自带版本存储路径 /usr/bin/python
```
当输入
```
python3 --version
```
出现
```
 /Library/这个路径下3.x版本的存储路径
 ```
此时我们需要配置路径，在终端输入
```
cd
sudo su
```
输入系统密码（加锁的不显示输入）

创建.bash_profile文件
```
touch.bash_profile
```
如果存在文件，直接打开（能打开也表示创建成功）
```
sh-3.2# open.bash_profile
sh-3.2#
```
在文件中输入Python安装的路径环境变量命令
```
# Setting PATH for Python 3.8.1
# The original version is saved in .bash_profile.pysave
PATH="/Library/Frameworks/Python.framework/Versions/3.8/bin:${PATH}"
export PATH

alias python="/Library/Frameworks/Python.framework/Versions/3.8/bin/python3.8"
```
保存并退出，然后重新打开终端，输入python --version ，此时版本显示为python 3.8.1；路径也发生了改变。
## Mac OS下安装Python pip安装及使用
**pip 是Python包管理工具**，提供了对Python包的查找、下载、安装、卸载的功能。

如果在 python.org 下载了最新版本的安装包，则已经自带了该工具。

Python 2.7.9 + 或 Python 3.4+ 以上版本都自带 pip 工具。
判断是否安装
```
pip --version
```
如果没有安装，则
```python
$ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py   
# 下载安装脚本
$ sudo python get-pip.py    
# 运行安装脚本
```
```python
#注意：用哪个版本的 Python 运行安装脚本，pip 就被关联到哪个版本，如果是 Python3 则执行以下命令
$ sudo python3 get-pip.py  
```
结果
```
Successfully installed pip-20.0.2 wheel-0.34.1
pip 20.0.2 from /Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages/pip (python 3.8)
```
- 使用：https://www.runoob.com/w3cnote/python-pip-install-usage.html

- Python是**强类型(Strongly typed)，动态(dynamically)，隐式(implicitly)类型化**的语言。

> 例如：不需要声明变量！

- 大小写敏感。
- 面向对象(object-oriented)

## 帮助

```python
help(<object>)
# 可以获得关于这个对象如何工作的信息。
dir(<object>)
# 可以看到这个对象的所有方法
```

## 语法

- Pythob没有强制的语句终止字符，代码块(blocks)是通过**缩进**指定的。
  - 在代码块开始、结束时都进行缩进(dedent)。
- 注释：

```python
# 单行注释
""" 多行注释
可以用多行字符串表示
可以有很多行
很多很多很多行 """
```

- 赋值`=`、判断相等`==`、加等`+=`等等和`Java`相同。

## 数据类型

Python中可用的数据结构有：

- `list` 列表：一维数组
- `tuple` 元组：不可变的一维数组
- `dictionary` 字典：关联数组（Hash Table）
- `set` 集合

> Python中的“数组”可以使任何类型的，所以在列表、字典、元组中，可以**混合**整数、字符串等
>
> - 也可以在数组中放数组。

```python
sample = [1, ["another", "list"], ("a", "tuple")]
# 这个数组中有一个int, 一个两个字符串组成的列表, 一个两个字符串组成的tuple
mylist = ["List item 1", 2, 3.14]
mylist[0] = "List item 1 again" 
# 改变一个元素 
mylist[-1] = 3.21 
# 索引-1是最后一个元素
mydict = {"Key 1": "Value 1", 2: 3, "pi": 3.14}
mydict["pi"] = 3.15 
# 这是改变dictionary的值的方式
mytuple = (1, 2, 3)
myfunction = len
print(mylist)
# 打印出整个List
```

- 可以使用冒号`:`**访问数组范围**

```python
>>> mylist = ["List item 1", 2, 3.14]
>>> print(mylist[:])
#'List item 1', 2, 3.1400000000000001
>>> print(mylist[0:2])
#'List item 1', 2
>>> print(mylist[-3:-1])
# 'List item 1', 2
"""负数是代表从后向前数的索引
-1代表最后一个元素，-3就是倒数第三个元素"""
>>> print(mylist[1:])
# 2, 3.14
>>> print(mylist[::2])
#'List item 1', 3.14
```

### 字符串

- 字符串可以使用**单引号**或者**双引号**。并且可以在使用一种引号的字符串中包含另一种引号。

  `"He said 'Hello' to you"`

- 多行字符串：三个引号(单双都可以)。
- Python字符串总是`Unicode`编码，但是还有一种字符串类型是纯字节的。称为`bytestring`字节串，用`b`前缀表示。`b"Hello \xce\xb1"`

- 值填充字符串：模块化操作符:`%`

```python
print("This %(verb)s a %(noun)s." % {"noun": "test", "verb": "is"})
# This is a test.
```

## 流量控制语句

(flow control statements)

- 也就是`if`，`for`，`while`。
- 在python中**没有**`switch`。用`if`代替!

- 用`for`来枚举(enumerate)`list`中的成员。
- 可以遍历的数字序列：`range(<number>)`:

```python
print(range(10))
# range(0, 10)
rangelist = list(range(10))
print(rangelist)
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
for number in range(10): # 枚举
    if number in (3, 4, 7, 9):
        break
        # "Break" 可以在else前结束for循环
    else:
        continue
        # "Continue"直接开始下一次迭代
else:
    # "else" 语句不是必须的，仅在没有break的时候执行
    pass # Do nothing

if rangelist[1] == 2:
    print("The second item (lists are 0-based) is 2")
elif rangelist[1] == 3:
    print("The second item (lists are 0-based) is 3")
else:
    print("Dunno")

while rangelist[1] == 1:
    print("We are trapped in an infinite loop!")
```

## 函数Function

- 函数由`def`关键词声明。
- **可选参数optional arguments**实在强制参数之后的函数声明中通过分配一个默认值设置。

- 函数可以返回一个元组，解压元组可以获得多个值，以达到**返回多个值**的目的。

### Lambda函数

Lambda函数是由<u>一条语句</u>组成的特殊函数。

- 参数通过reference传递，单数不可变类型不能在调用中改变。

> （不可变类型：元组、int、字符串等等。）
>
> 这是因为，被传递的仅仅是一个内存位置，而将另一个对象绑定到变量上，丢弃原有的对象。所以不可变类型会被替换。

```python
# 相当于 def funcvar(x): return x + 1
funcvar = lambda x: x + 1
>>> print(funcvar(1))
# 输出：2

# an_int 和 a_string 是可选的参数，如果没有传进参数的话，它们会有默认值。
def passing_example(a_list, an_int=2, a_string="A default string"):
    a_list.append("A new item")
    an_int = 4
    return a_list, an_int, a_string

my_list = [1, 2, 3]
my_int = 10
print(passing_example(my_list, my_int))
# ([1, 2, 3, 'A new item'], 4, "A default string")
```

## 类Classes

- Python支持在类中有限的多重继承(multiple inheritance)形式。
- 声明**Private**的变量和方法：加一个前导下划线，例如：`_spam`（惯例，不是强制的）
- 可以将任意名称绑定给类的实例对象：

```python
class MyClass(object):
    common = 10
    def __init__(self):
        self.myvariable = 3
    def myfunction(self, arg1, arg2):
        return self.myvariable
    
# 类的实例化

classinstance = MyClass()
classinstance.myfunction(1, 2)
# 结果：3
# Common是所有实例对象共享的变量
classinstance2 = MyClass()
classinstance.common
# 结果：10
# Note how we use the class name
# instead of the instance.
MyClass.common = 30
classinstance.common
# 30
classinstance2.common
# 30
# 这样不会更新类中的那个变量，但会给(这个对象的)原本的变量名绑定一个新对象。
classinstance.common = 10
classinstance.common
# 10
classinstance2.common
# 30
MyClass.common = 50
# classinstance的common不会改变的，因为common现在是实例变量了。
>>> classinstance.common
# 10
>>> classinstance2.common
# 50

# 这个类继承了MyClass。
# 多个继承：class OtherClass(MyClass1, MyClass2, MyclassN)
class OtherClass(MyClass):
    # "self"是自动传入的，代表这个类的实例(只在类中有效)
    def __init__(self, arg1):
        self.myvariable = 3
        print(arg1)

classinstance = OtherClass("hello")
# 输出：hello
classinstance.myfunction(1, 2)
# 调用父类方法，结果：3

# 这个类没有一个叫做.test的成员，但我们还是可以给它加这么一个实例！
# 并不会改变整个类或者其他实例，仅仅用于这个实例。
>>> classinstance.test = 10
>>> classinstance.test
# 10
```

### 下划线

变量:

1. 前带`_`的变量:  标明是一个私有变量(`_private_value`)（只用于标明, 外部类还是可以访问到这个变量）

2. 前带两个`_` ,后带两个`_` 的变量(`__name__`):  标明是内置变量

3. 大写加下划线的变量(`USER_CONSTANT`):  标明不会发生改变的全局变量

函数:

1. 前带_的变量: 标明是一个私有函数, 只用于标明,

2. 前带两个`_` ,后带两个`_` 的函数(`__add__`):  标明是特殊函数

> 前面加了两个下划线`__`的变量会在解释期间被更名，以避免和其他变量的冲突。
>
> （Python的名称改编特性）

## 异常Exception

Python中的异常使用`try-except [exceptionname]`块处理:

```python
def some_function():
    try:
        # 0做除数会造成exception
        10 / 0
    except ZeroDivisionError:
        print("Oops, invalid.")
    else:
        # 没有出现exception时执行
        print("Nothing wrong happened");
        pass
    finally:
        # 代码块都运行且异常已经被处理之后执行。
        # （即使在处理过程中有了新的异常，也还是会执行。）
        print("We're done with that.")

some_function()
""" Oops, invalid.
    We're done with that."""
```

## 导入import

- `import [libname]`关键字可以导入外部库。
- 还可以使用`from [libname] import [funcname]`导入外部库的单个函数。

```python
import random
from time import clock

# 生成随机数
randomint = random.randint(1, 100)
print(randomint)
```

## File I/O

Python内建了大量的库。

例如，下面是如何使用文件I/O序列化(使用`pickle`库将数据结构转换为字符串):

```python
import pickle
mylist = ["This", "is", 4, 13327]
# 打开 C:\\binary.dat
# 文件名前的"r"用于阻止反斜杠的转义.
myfile = open(r"C:\\binary.dat", "wb")
pickle.dump(mylist, myfile)
# dump方法：写入文件并序列化
myfile.close()

myfile = open(r"C:\\text.txt", "w")
myfile.write("This is a sample string")
myfile.close()

myfile = open(r"C:\\text.txt")
print(myfile.read())
'This is a sample string'
myfile.close()

# Open the file for reading.
myfile = open(r"C:\\binary.dat", "rb")
loadedlist = pickle.load(myfile)
# load方法：读取并反序列化，即将文件内容载入loadedlist对象
myfile.close()
print(loadedlist)
['This', 'is', 4, 13327]
```

> `rb`,`wb`二进制模式的读写，以`byte`类型读写。

## 全局变量

- 全局变量在**函数外**声明。不需要任何特殊的声明。

- 但是，如果想要写入(更新)这个变量，必须在函数的开头用`global`声明这个变量。
  - 否则，Python会将对象绑定到一个新的本地变量上。

```python
number = 5
# 这是一个全局变量

def myfunc():
    print(number)
	# 输出：5
    
def anotherfunc():
    print(number)
    number = 3
    # 会发生异常：变量被输出时还没有绑定。
    # Python知道之后它会被绑定一个对象(看的到下一行！)，于是不会访问全局变量。

def yetanotherfunc():
    global number
    # 这样就可以正确的改变全局变量了
    number = 3
```

## 其他

- 允许连接的条件判断：`1 < a < 3`
- 可以使用`del`来删除数组中的变量或者元素
- **List comprehension列表理解**提供了创建和操作`list`的方法：
  - 表达式 + 一个或多个`if`或`for`：

```python
lst1 = [1, 2, 3]
lst2 = [3, 4, 5]
print([x * y for x in lst1 for y in lst2])
# 输出：[3, 4, 5, 6, 8, 10, 9, 12, 15]
print([x for x in lst1 if 4 > x > 1])
# 输出：[2, 3]

# any：是否存在任意元素满足条件：
any([i % 3 for i in [3, 3, 4, 4, 3]])
# 结果：True
# 只要存在满足条件的元素就会返回true
# 4 % 3 = 1, and 1 is true

# sum：有多少元素满足条件：
sum(1 for i in [3, 3, 4, 4, 3] if i == 4)
# 输出：2
del lst1[0]
# 删除第一个元素
print(lst1)
[2, 3]
del lst1
```

