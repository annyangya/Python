## Python的基本类型

1. int float bool complex(复数)类型都是Number的子类
2. Python中浮点数只有float类型且为双精度类型，没有double类型
3. type()方法，判断给定内容的类型
```python
>>> type(int)
<class 'type'>
>>> type(1)
<class 'int'>
>>> type('string')
<class 'str'>
>>> type(2.2)
<class 'float'>
>>> type(True)
<class 'bool'>
```
4. 除法与地板除："/"的结果是float类型，“//”的结果是int类型（整除）
```python
>>> 1/2
0.5
>>> 1//2
0
>>> 4//3
1
>>> 4/3
1.3333333333333333
>>> 
>>> 2/2
1.0
>>> 2//2
1
```
5. python中的二进制，八进制，十进制，十六进制的表示
(1) 二进制：0，1，10，11……满二进一；0b开头表示这个数为二进制数，如0b10表示这个数是二进制中的2
(2) 八进制：0，1，2，……，7，10，……；0o开头表示这个数是八进制数，如0o10表示这个数是八进制中的2
(3) 十进制：就是平常的数，0，1，2，3，4，……，10，11……
(4) 十六进制：0，1，2，……，9，A，B，C，D，E，F；0x开头表示这个数是十六进制数，如0x10表示这个数是十六进制中的16
6. 进制转换
(1) 把其他类型的数转成二进制：bin()
```python
>>> bin(0b10)
'0b10'
>>> bin(0o10)
'0b1000'
>>> bin(0x10)
'0b10000'
>>> bin(10)
'0b1010'
```
(2) 把其他类型转成八进制，oct()
```python
>>> oct(0b10)
'0o2'
>>> oct(0o10)
'0o10'
>>> oct(10)
'0o12'
>>> oct(0x10)
'0o20'
```
(3) 把其他类型转成十进制,int()
```python
>>> int(0b10)
2
>>> int(0o10)
8
>>> int(0x10)
16
```
(4) 把其他类型转成十进制,hex()
```python
>>> hex(0b10)
'0x2'
>>> hex(0o10)
'0x8'
>>> hex(10)
'0xa'
```
7. bool类型：True,False,注意开头字母大写
```python
<class 'bool'>
>>> int(True)
1
>>> int(False)
0
>>> bool(1)
True
>>> bool(2)
True
>>> bool("heelo")
True
>>> bool(-1)
True
>>> bool(0)
False
>>> bool("");
False
>>> bool(" ")
True
>>> bool(None)
False
>>> 
>>> bool({})
False
```
由上可知，python中所有不为0即不为空的数字或字符串或序列等都表示布尔真，只有0，Zone，"",{},[]等空数值序列等表示布尔假
8. 单引号，双引号，三引号

(1) 单引号，双引号，三引号都可以用来表示字符串，如'hello',"hello",'''hello'''
(2) 引号必须成对存在才可以用来表示字符串,下面是表示let's go的写法
```python
>>> 'let's go'（错误）
SyntaxError: invalid syntax
>>> "let's go"
"let's go"
>>> 'let\'s go'
"let's go"
>>> 'let''s go'
'lets go'
```
如果字符串内容由单引号，最外面可用双引号，或是把单引号用转义字符表示出来
(3) 当内容需要表示多行时，可用三引号表示:'''或"""
```python
>>> ''' hello
hello
hello'''
' hello\nhello\nhello'
>>> """hello
hello"""
'hello\nhello'
```
内容的换行自动转变成\n，而如果在内容中有\n,则不会被当作换行符\n，直接把\n当作字符串内容
```python
>>> '''hello\nhello\n'''
'hello\nhello\n'
```
但是在print()中，内容有\n，则会被当作换行符，输出内容换行
```python
>>> print('''hello\nhello''')
hello
hello
>>> print('hello\nhello')
hello
hello
```
'''可实现换行的效果，单引号加 \ 也可以实现输入换行，但是结果不一样
```python
>>> 'hello\
hello'
'hellohello'
>>> '''hello
hello'''
'hello\nhello'
```
9. 转义字符：特殊的字符，可实现无法“看见”的字符，或是与语言本身语法有冲突的字符
(1) 在print中输出\n,而不将其当作换行符
```python
>>> print('hello\\nhello')
hello\nhello
```
(2) 输出路径，如C：\north\west
```python
>>> print('C:\\north\\west')
C:\north\west
>>> print(r'C:\north\west')
C:\north\west
```
由上可知，可以用转义字符或是在字符串前面加上r或R，加上r表示这个字符串为一个原始字符串，该字符串所见即为内容
```python
>>> print(r"let's go")
let's go
>>> print(r'let's go')(引号成对)
      
SyntaxError: invalid syntax
>>> print("let's go")
let's go
>>> 
```
10. 字符串的运算
(1). + 表示字符串的连接
```python
>>> 'hello'+'world'
'helloworld'
```
(2) * 表示内容复制加倍
```python
>>> 'hello'+'world'
'helloworld'
>>> 'hello'*3
'hellohellohello'
>>> 'hello'*-1
''
>>> 'hello'*(-1)
''
>>> "hello"*-1
''
>>> 'hello'*0
''
>>> 'hello'*1.2
Traceback (most recent call last):
  File "<pyshell#76>", line 1, in <module>
    'hello'*1.2
TypeError: can't multiply sequence by non-int of type 'float'
>>> 'hello'*'hello'
Traceback (most recent call last):
  File "<pyshell#77>", line 1, in <module>
    'hello'*'hello'
TypeError: can't multiply sequence by non-int of type 'str'
```
由上可知，字符串只能乘以int类型的整数，而不能乘以浮点数，字符串等。乘以int类型表示加倍，乘以负数或0表示字符串为空
(3) 获取字符串子内容
```python
>>> 'hello world'[0]
'h'
>>> 'hello world'[-1]
'd'
>>> 'hello world'[-2]
'l'
>>> 'hello world'[3:]
'lo world'
>>> 'hello world'[3:8]
'lo wo'
>>> 'hello world'[3:20]
'lo world'
>>> 'hello world'[:-3]
'hello wo'
>>> 'hello world'[0:-3]
'hello wo'
>>> 'hello world'[6:-1]
'worl'
>>> 
>>> 'hello world'[-5:]
'world'
>>> 'hello world'[:-5]
'hello '
```
由上可知：

(1). [下标]可获得某个子元素
(2). 切片操作[1:4]表示从下表1到下标3的子元素序列
(3). [-2]表示从序列末尾开始倒数第二个子元素
(4). [:-5]表示从倒数第六个元素开始前面所有的子元素组成的序列（包括倒数第六，不包括倒数第五）
(5). [-5:]表示从倒数第五个元素开始后面所有的子元素组成的序列，包括倒数第五
(6). [0:-1]表示从字符串最开始到倒数第二个元素，不包括最后一个
