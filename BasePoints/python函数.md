
函数

函数的定义及基本结构

    def funcname(parameter_list):
        pass

1. 参数列表可省
2. 使用return返回value，如果没有return语句则认为返回Zone
3.     #递归函数，自己调用自己
       def print(code):
           print(code)
       print('1')#超出限制，maximum recursion depth exceeded，python可以设置递归最大长度

设置最大长度：

    import sys
    sys.setrecursionlimit(100)#递归次数限制

    def print_code(code):
        print(code)
        #非递归

1. 范例
       import sys
       sys.setrecursionlimit(100)#递归次数限制
       def add(a,b):
           return a+b
       
       def print_code(code):
           print(code)
       
       a=add(1,2)
       b=print_code("python")
       print(a,b)

结果：

python

3 None

a=add(1,2)，将add返回值存放在a中，接着调用print_code方法，因为print_code方法里面有print输出，所以先输出python,并把print_code的返回值存放在b中。接着print(a,b)，是在同一行打印输出a，b，得a为3，因为print_code没有返回值，所以默认b为Zone。

函数返回多个值

1. 函数没有指定返回值类型，所以可以返回各种类型，甚至可以返回函数
2.     def damage(one,two):
           damage1=one*2
           damege2=two*1
           return damage1,damege2
       
       print(damage(3,2))

结果：(6, 2)

默认以元组的形式返回

1.     def get(one,two):
           get1=one*3
           get2=two*2
           return [get1,get2]
       
       print(get(1,2))

结果：[3, 4]

也可以直接指明返回类型

    three=get(1,2)
    print(three[0],three[1])
    print(type(three))
    #获得值，但是这种方法不方便

    damage_1,damage_2=damage(3,2)
    print(damage_1,damage_2)
    #直接获取：序列解包，避免使用索引的方式

序列解包

1.     d=1,2,43
       print(type(d))
       #<class 'tuple'>，可得d是元组类型
2.     d=2,3,4
       a,b,c=d
       #也是python解包
3. 注意元素个数相等，接收发送相等
       a,b=[1,2,4]
       #ValueError: too many values to unpack (expected 2)

必须参数和关键字参数

1. 必须参数：参数必须传递
       def add(a,b):#第一个传入一定是a，第二个传入一定是b
           return a+b
2. 关键字参数：有了关键字可以灵活传入参数,明确指出给哪个参数传值
       c=add(b=3,a=1)
       print(c)
3. 定义多少个形参，就要传递多少个实参

默认参数

1. 当有太多参数时，可以设定默认参数，这样用户只需要输入少量参数
2.     #如果说只有姓名不一样，年龄性别都一样，设定默认参数
       def print_info(name,sex,age):
           print("name:"+name)
           print("sex:"+sex)
           print("age:"+age)
       
       print_info("ann","man","18"）

结果：

name:ann

sex:man

age:18

1.     def print_info(name,sex="man",age="18"):
           print("name:"+name)
           print("sex:"+sex)
           print("age:"+age)
           
           print_info("Mary")

结果：

name:Mary

sex:man

age:18

1. 使用默认参数，在调用时也可以改变参数
       print_info("ed","boy","20")

结果：

name:ed

sex:boy

age:20

1. 需要默认值则加上=并赋值，如果没有添加默认值，则一定要传入参数
2. 默认参数一定放后面，如果定义了默认参数，那么后面不能再有不是默认参数的参数
       def print_info(name,sex="man",age="18",school):
       #SyntaxError: non-default argument follows default argument
3.     def print_info(name,sex="man",age=8):
           print("name:"+name)
           print("sex:"+sex)
           print("age:"+str(age))
       
       print_info("ann","man",18)
       print_info("Mary")
       print_info("ed","boy",20)
       print_info("la",age=90)
       #print_info(age=23,"ann2",sex="woman")

注意age指定是int型，但是在输出的时候要转型，因为默认是str；在赋值的时候，默认参数和非默认参数的位置不能混，默认参数后面赋值；赋值的时候可以指定给哪个赋值，那么非默认参数和默认参数各自内部可以不按顺序
