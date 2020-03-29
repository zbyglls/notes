# python
2019.12.9
## 变量
    命名规则：
    <1>变量命名可以包含数字，大小写字母，下划线或更多（可用中文），数字不可以开头
    <2>在python中，以下划线开头的内容具有特殊含义，不建议使用
    <3>变量名必须避开保留字和关键字
   
    变量声明：
```
var_name = var_value
var1 = var2 = var3 = var_value
var1,var2,var3 = v1,v2,v3
```
2019.12.12    
## 变量类型：
    标准数据类型6种。
    1.数字 Number
    <1>整数：无小数部分，表示个数的数字
        二进制，以0b开头的0，1代码
        八进制，以0o开头的包含0-7的数字
        十六进制，以0x开头
    <2>浮点数
        小数
        科学计数法，定义同数学；写法用e/E后面跟整数表示10的指数
    <3>复数complex，定义同数学定义一致；虚部用j/J表示
    <4>布尔值，表示真假True，False;布尔值若当数字使用，True=1，False=0；若数字当作布尔值使用，0=False，其余当作True
    2.字符串 str
        表达文字信息的内容，形式上是引号引起来的一段内容
        引号包括：单引号，双引号（单双引号含义一致），三引号（可以用来表示多行信息）
        None：表示没有，通常用来占位；如果函数没有返回值，可以返回None；用来解除变量绑定
    3.列表 list
    4.元组 tuple
    5.字典 dict
    6.集合 set
2019.12.16
## 表达式
    有一个或几个数字或变量或运算符合成的一行代码，通常返回一个结果
    
    1.运算符：用来操作运算的符号叫做运算符
    2.运算符分类：
    <1>算数运算符：+，-，*，/，**（指数）
        用来进行算数运算得符号，通常用来表示加减乘除；python没有自增自减运算符
        python除法分为普通除法（/），地板除（//，取整），取余（%）
    <2>比较或关系运算符：==，!=,<,>,<=,>=
        对两个内容进行比较的运算符，结果一定是布尔值，即True/False
    <3>逻辑运算符
        对布尔类型变量或值进行运算的符号，python里的逻辑运算没有异或
        and：逻辑与
        or ：逻辑或
        not：逻辑非
        运算规则：
            and看作乘法，or看作加法
            True看作1，False看作0
            最后结果是0则为False，否则为True
        逻辑运算的短路问题
            逻辑运算式，按照运算顺序计算，一旦能够确定整个式子未来的值，则不再进行计算，直接返回
```
#案例：
a = True
b = True
c = False
aa = a or b and (a and b) #转换成算数1+........
print(aa)
```
    <4>位运算
    <5>成员运算符：in，not in
        用来检测一个值或者变量是否在某个集合里面
    <6>身份运算符：is is not
        用来确定两个变量是否是同一变量
        对整数N in [-5,256],解释器对他们做了 单独的处理，放进了固定的内存中，不因每次运行而变化；内建的类也是这样处理的
    3.运算符的优先级问题
        小括号具有最高优先级
        **  指数 (最高优先级)
        ~ + -   按位翻转, 一元加号和减号 (最后两个的方法名为 +@ 和 -@)
        * / % //    乘，除，取模和取整除
        + - 加法减法
        >> <<   右移，左移运算符
        &   位 'AND'
        ^ | 位运算符
        <= < > >= == != 比较运算符
        = %= /= //= -= += *= **=    赋值运算符
        is is not   身份运算符
        in not in   成员运算符
        not or and  逻辑运算符
        
2019.12.18
## 程序结构
    1.程序三种结构
        顺序
        循环
        分支
    
    2.分支结构
    分支结构基本语法
```    
if 条件表达式：
    语句1
    语句2
    .....
```        
    双向分支语法结构
```
if 条件表达式：
    语句1
    语句2
    .....
else：
    语句1
    语句2
    .....
```
    多路分支
```
if 条件表达式：
    语句1
elif 条件表达式：
    语句1
    .....
elif 条件表达式：
    语句1
    .....    
else：
    语句1
    .....
```
    if 语句可以嵌套使用，不推荐
    python没有switch语句
    
2019.12.30
## 循环结构
    1.for循环语法
```
for 变量 in 序列：
    语句1
    语句2
    ...
```
    2.for-else语句
    for循环结束的时候，有时候需要执行一些收尾工作，此时需要使用esle语句；esle语句可选
    
    3.break,continue,pass
    break:无条件结束整个循环，简称循环猝死
    continue：继续
    pass：只是占位符号，代表这句话什么也不干，没有跳过功能
    
    4.range函数
    生成有序数列
    生成数字队列可定制
    一般在python中，表示范围的数字都是左包括右不包括，randint函数是个特例
    
    5.while循环
    表示当条件成立时，就循环，适应于不知道具体循环次数，但能确定在某个条件成立的情况下就循环
```
#while语法
while 条件表达式：
    语句块
        
#另一种
while 条件表达式：
    语句块1
else：
    语句块2
```
2019.12.31
## 函数
    函数是代码的一种组织形式
    函数应该能完成一项特定的工作，而且一般一个函数只完成一项工作
    有些语言，分函数和过程两个概念，通俗解释，有返回结果的叫函数，无返回结果的叫过程，python不区分
    1.函数的使用
        函数使用需要先定义
        使用函数，俗称调用
```        
def func():
    语句块
    ...
```    
    2.函数调用
        直接写出函数名字，后面小括号不能省略，括号内内容根据情况
        
    3.函数的参数和返回值
        参数：负责给函数传递一些必要的数据或信息
            形参（形式参数）：在函数定义的时候用到的参数，没有具体值，只是一个占位符号
            实参（实际参数）：在调用函数的时候输入的值
            
        返回值：调用函数的时候的一个执行结果
            使用return返回结果
            如果没有值需要返回，推荐使用return None 表示函数结束
            如果函数没有return关键字，函数默认返回None
            函数一旦执行return关键字，则函数立即结束
```          
#乘法表  
def jiujiu():
    for o in range(1,10):#外循环
        for i in range(1,o+1):#内循环
            print('{}*{}={}'.format(o,i,o*i),end='\t')
        print()
    return None
```               
    4.参数详解
        参数分类
            普通参数/位置参数
            默认参数
                形参带有默认值
                调用的时候，如果没有对相应形参赋值，则使用默认值
            关键字参数
                使用关键字参数，可以不考虑参数位置
            收集参数
                把没有位置，不能和定义时的参数位置相对应的参数，放入一个特定的数据结构中
                语法
                    def func(*args):
                        func_body
                        按照list使用访问args得到传入的参数
                    调用：
                    func(p1,p2,p3,....)
                参数名推荐直接用args
                参数名args前需要 * 
                收集参数可以和其他参数共存
```       
#普通参数案例
def normal_para(one,two,three):
    print(one+two)
    return None
        
narmal_para(1,2,3)  

#默认参数案例
def default_para(one,two,three=100):
    print(one+two)
    return None
        
default_para(1,2)
default——para(1,2,3)
        
#关键字参数
def key_para(one,two,three):
    print(one+two)
    print(three)
    return None
        
key_para(one=1,two=2,three=30)
key_para(three=30,two=2,one=1)

#收集参数案例
def stu(*args):
    print('hello,大家好，我自我介绍一下：')
    for item in args:
        print(item)

stu('lin san',16,'xx区')
stu('lin si')

#收集参数可以不带任何实参调用，此时收集参数为空tuple
stu()

```     
    5.收集参数之关键字收集参数
        把关键字参数按字典格式存入收集参数
        语法：
            def func( **kwargs):
                func_body
            
            调用：
            func(p1=v1,p2=v2,p3=v3,....)
        调用的时候，把多余的关键字参数放入kwargs
        访问kwargs需要按字典格式访问
```
#案例
#调用的时候需要使用关键字参数调用
def stu( **kwargs):
    print('hello,大家好，我自我介绍一下：')
    for k,v in kwargs.items():
        print(k,'---',v)
    
stu(name='lin san',age=16,addr='xx区')
    
```
    6.收集参数混合调用的顺序问题
        收集参数，关键字参数，普通参数可以混合使用
        使用规则就是，普通参数和关键字参数优先
        定义的时候一般找普通参数，关键字参数，收集参数tuple，收集参数dict
```
#收集参数混合调用案例
def stu(name,age,*args,hobby='没有',**kwargs):
    print('hello,大家好')
    print('我叫{0},我今年{1}了。'.format(name,age))
    if hobby == '没有':
        print('我没有爱好')
    else:
        print('我的爱好是{}'.format(hobby))
    print('*' * 20)
    for i in args:
        print(i)
    print('#' * 30)
    for k,v in kwargs.items():
        print(k,'---',v)

#调用
name = 'lin ci'
age = 18

stu(name,age,'我喜欢林三',hobby='游泳',hobby1='和女神聊天')       
```
    7.收集参数的解包问题
        把参数放入list或者字典中，直接把list/dict中的值放入收集参数中
        list类型用一个 * 
        dict类型用两个 *
```
def stu(*args):
    print('***********')
    for i in args:
        print(i)
        
li = ['d',1,2,3,'dj']
stu(*li)
```
    8.函数文档
        函数文档的作用是对当前函数提供使用相关的参考信息
        文档的写法：
            在函数内部开始的第一行使用三引号字符串定义符
            一般具有特定格式
            参看案例
        文档查看
            使用help函数，形如 help(func)
            使用__doc__, 参看案例
```
# 文档案例
def stu(name, age):
    '''
    这是文档的文字内容
    :param name: 表示学生的姓名
    :param age: 表示学生的年龄
    :return: 此函数没有返回值
    '''
    pass

print(help(stu))
print("*" * 20)

print(stu.__doc__)
```
    9.变量作用域
        分类：按作用范围分类
            全局（global）：在函数外部定义
            局部（local）：在函数内部定义
        变量的作用范围：
            全局变量：在整个全局范围都有效
            全局变量在局部可以使用（即函数内部可以访问函数外部定义的变量）
            局部变量在局部范围可以使用
            局部变量在全局范围无法使用
        LEGB原则
            L（Local）局部作用域
            E（Enclosing function locale）外部嵌套函数作用域
            G（Global module）函数定义所在模块作用域
            B（Buildin）： python内置模块的作用域
        
        提升局部变量为全局变量
            使用global
            
    #globals，locals函数
        可以通过globals和locals显示出局部变量和全局变量
        
    #eval()函数
        把一个字符串当成一个表达式类执行，返回表达式执行后的结果
        语法：
            eval(string_code,globals=None,locals=None)
            
    #exec()函数
        跟eval功能类似，但不返回结果
        语法：
            exec(string_code,globals=None,locals=None)
2020.1.1
## str模块
    1.字符串：表示文字信息；用单引号，双引号，三引号括起来
    
    2.转义字符：
    用一个特殊的方法表示出一系列不方便写出的内容，比如回车键，换行符，退格键
    借助反斜杠字符，一旦字符中出现反斜杠，则反斜杠后面一个或者几个字符表示已经不是原来的意思，进行了转义
    在字符串中，一旦出现反斜杠，可能有转义字符出现
    不同系统对换行操作有不同的表示
        Windows：\n
        linux：\r\n
```        
#使用单双引号嵌套
s = "let's go"
print(s)
        
#表示斜杠
# 比如 C:\User\Augsano
s = "C:\\User\\Augsano"
print(s)
        
#回车换行
s = "Ich\nlieb\nxxxxxx"
print(s)
```        
        #常见转义字符
        \(在行尾时)     续行符
        \\              反斜杠符号
        \'              单引号
        \"              双引号
        \a              响铃
        \b              退格（backspace）
        \e              转义
        \000            空
        \n              换行
        \v              纵向制表符
        \t              横向制表符
        \r              回车
        \f              换页
        \oyy            八进制，yy代表字符
        \xyy            十六进制
        \other          其他的字符以普通普通形式输出
        
    3.格式化
    把字符串按照一定格式进行打印或者填充
    格式化的分类：
        传统格式化
        format
```        
#字符串的传统格式化方法
使用%进行格式化；%也叫占位符
# %s表示简单的字符串
# 占位符可单独使用
s = "I love %s"
print(s%"xxx")
#占位符一般只能被同类型替换，或者替换类型能被转换成占位符的类型
print("i love %s"%100)

#如果需要格式化的信息多于一个，则用括号括起来就可以
s = "i am %.2fkg weight ,%.2fm height"
print(s%(60.0,1.69))

#format格式化
    使用函数格式化，代替以前的百分号
    #不要指定位置，按顺序读取
# 方式1
s = "{} {}!"
print(s.format("hello","world"))
# 方式2
s = "{} {}!".format("hello","world")
print(s)
            
    #设置指定位置
s = "{0} {1}!".format("hello","world")
print(s)
            
s = "{1} {0}!".format("hello","world")
print(s)
            
s = "i love {0} and {0} loves me".format("xxx")
print(s)
            
    #使用命名参数
s = "我们是{name}，我们的网址是{url}，{tea}最帅"
s = s.format(name="xxx",url="xxxxx",tea="xx")
print(s)
            
#通过字典设置参数，需要解包
    使用命名参数
s = "我们是{name}，我们的网址是{url}，{tea}最帅"
s_dict = {"name":"xxx","url":"xxxx","tea":"xx"}
s = s.format(**s_dict)      # **是解包操作
print(s)
            
#对数字的格式化需要用到
s = "i am {:.2f}kg weight ,{:.2f}m height"
print(s.format(60.0,1.69))
```
2020.1.2            
## str内置函数
    1.字符串查找类，find，index
    # find：查找字符串中是否包含一个子串
    # index：跟find的唯一区别是index如果找不到会引发异常
    # rfind，lfind：从左开始查找或者从右开始查找
```
s = "i love xxx and xxxx"
s1 = "xxx"
s.find(s1)  #返回第一次发现这个字符串的位置
s2 = "mlr"
s.find(s2)  #返回-1表示没有找到
```    
    # index：
    s.index(s2) #index会报错或引发异常
```    
#使用时还可以使用区间
s = "i love mlr and xxx"
s1 = "mlr"
s.find(s1,8)    #从下表8开始查找
```    
    2.判断类函数
    此类函数的特点是一般都用is开头，比如islower
    # isalpha：判断是否是字母，需要注意：
        此函数默认的前提是字符串至少包含一个字符，如果没有，同样返回False
        汉字被认为是alpha，此函数不能作为区分中英文的标识，区分中英文使用Unicode码
        
    # isdigit，isnumeric，isdecimal：三个判断数字的函数
        此类函数不建议使用，在爬虫中，判断是否是数字建议采用正则表达式
        isdigit：
          True：uicode数字，byte数字（单字节），全角数字（双字节），罗马数字
          False：汉字数字
          Error：无
        isdecimal：
          True：Unicode数字，全角数字（双字节）
          False：罗马数字，汉字数字
          Eror：byte数字（单字节）
        isnumeric：
          True：unicode数字，全角数字（双字节），罗马数字，汉字数字
          False：无
          Error：byte数字（单字节）
    
    3.内容判断类
    # starswith/endswith：是否以xxx开头或结尾
        检测某个字符串是否以某个字串开头，常用三个参数
         suffix：被检查的字符串，必须有
         start：检查范围的开始范围
         end：检查范围的结束
```        
linsan = "lin san"
xusi = "xu si"
s = "lin san really love xu si"
print(s.startswith(linsan))
print(s.endswith(xusi))
```        
    # islower/isupper：判断字符串是否是小/大写   
        空格不影响大小写判断
        汉字字符串无大小写概念
        
    4.操作类函数
    # format：格式化用
    # strip：此函数的主要作用是删除字符串两边的空格，此函数允许定义删除字符串两边的特定字符，不指定默认是空格。同样还有lstrip和rstrip。需要注意的是，删除的不是一个，是指从头开始符合条件的连续字符
    # join：此函数主要对字符串进行拼接。他需要一个可迭代的内容作为参数，功能是吧可迭代的字符串拼接在一起，中间使用调用字符串作为分隔符
```
s1 = "-"
ss = ["lin san","love","xu","si"]
print(s1.join(ss))
```    
## list列表
    一组由有序数据做成的序列
        数据有先后顺序
        数据可以不是一类数据
    1.list的创建
        直接创建，用中括号创建，内容直接用英文逗号隔开
        使用list()创建
        创建只包含一个字符串的列表用 
```
s = "lin san"
l = [s]
```            
    2.列表的常见操作
    #访问
        使用下标操作，也叫索引
        列表的元素索引是从0开始
    
    #切片操作
        对列表进行任意一段的截取
        截取之后创建了一个全新的队列
        #切片操作需要注意驱之范围，左包括右不包括
        #分片可以控制增长幅度，默认为1
        #下标可以超出范围，超出后不再考虑多余下标内容
        #下标值，增长幅度可以为负数
        #下标为负数，表明顺序从右往左
        #规定：数组最后一个数字的下标是-1
        
    #del：删除命令
```
#del原地删除，不生成新变量
a = [1,2,3,4,5,6]
del a[2]
#del一个变量后不能继续使用此变量
del a
print(a)

Traceback (most recent call last):
  File "<pyshell#2>", line 1, in <module>
    print(a)
NameError: name 'a' is not defined

#使用加号链接两个列表
a = [1,2,3,4,5]
b = [6,7,8,9]
c = b + c

#列表直接跟一个整数相乘
#相当于把n个列表接在一起
a = [1,2,3,4]
b = a * 3
```
    #列表遍历
        #for i in list
        #while循环访问list
```
#一般不用while遍历list
a = [1,2,3,4]
leng = len(a)
#indx表示的是list的下标
indx = 0
while indx < leng:
    print(a[indx])
    indx += 1
```
    列表内涵：list content
        通过简单方法创作列表
```
#for 创建
a = ['a','b','c']
#用list a创建一个list b
b = [i for i in a]      #对于a中所有元素，逐个放入新列表b中

#对a中所有元素乘以10，生成一个新list
a = [1,2,3,4,5]
b = [i*10 for i in a]

3还可以过滤原来list中的内容并放入新列表
a = [x for x in range(1,35)]    #生成1-34的一个列表
b = [m for m in a if m % 2 == 0]

#列表生成式可以嵌套
a = [i for i range(1,10)]
b = [i for i in range(100,1000) if i % 100 == 0]

c = [m+n for m in a for n in b]

```
    3.列表的函数
    #append：插入一个内容，在末尾追加
```
a = [i for i in range(1,5)]
print(a)
a.append(100)
print(a)
```
    #insert：指定位置插入
    #insert(index,data) 插入位置是index前面
```
a.insert(3,666)
print(a)
```
    #删除
    #del 删除
    #pop：把最后一个元素取出来
```
last_ele = a.pop()
print(last_ele)
print(a)
```
    #remove：在列表中删除指定的值的元素
    #如果被删除的值没在list中，则报错
    #即，删除list指定值的操作应该使用try。。。except语句，或者先行判断
    #if x in list:
    #   list.remove(x)    
```
print(id(a))
a.remove(666)
print(a)
print(id(a))
#输出两个id值一样，说明remove操作时在原list直接操作
```
    #clear：清空
```
print(id(a))
a.clear()
print(a)
print(id(a))

#如果不需要列表地址保持不变，则清空列表可以使用以下方式
a = list()
a = []
```
    #reverse：翻转,原地翻转
```
a = [1,2,3,4,5]
print(id(a))

a.reverse()

print(a)
print(id(a))
```
    # extend:扩展列表，两个列表，把一个直接拼接到后一个上
```
a = [ 1,2,3,4,5]
b = [6,7,8,9,10]
print(id(a))

a.extend(b)

print(a)
print(id(a))
```
    # count:查找列表中指定值或元素的个数
```
a.append(8)
a.insert(4, 8)
print(a)
a_len = a.count(8)
print(a_len)
```
    # copy: 拷贝，此函数是浅拷贝
```
#列表类型变量赋值示例
a = [1,2,3,4,5,666]

#list类型，简单赋值操作是传地址
b = a
b[3] = 777
print(a)
print(id(a))
print(b)
print(id(b))

#为解决以上问题，list赋值需要采用copy函数
b = a.copy()
print(a)
print(id(a))
print(b)
print(id(b))
```
    #
2020.1.3
## tuple（元组）
    可以理解为一个不允许更改的列表
    1.tuple的创建
```
#创建空元组
t = ()
#用小括号创建一个元素的tuple时
t = (xx,)
        
#直接用逗号
t = x,
t1 = x,xx,xxx
        
#使用tuple定义
t = tuple()
        
li = [1,2,3,"lin san"]
t = tuple(li)   #要求tuple参数必须可迭代
```     
    2.tuple其余特征跟list基本一致
        有序
        可以访问不可以被修改
        元素可以是任意类型
        #tuple加法
```
# 序列相加
t1 = (1,2,3)
t2 = (5,6,7)

# 传址操作
print(t1)
print(id(t1))
t1 = t1 + t2
print(t1)
print(id(t1))

# 以上操作，类似于
t1 = (1,2,3)
t1 = (2,3,4)

# tuple 的不可修改，指的是内容的不可修改
# 修改tuple内容会导致报错
t1[1] = 100
```
        #tuple乘法
```
# 元组相乘
t = (1,2,3)
t = t * 3
print(t)
```
        #tuple成员检测
```
t = 'lin san', 'love', 'lin ci'
if 'lin ci' in t:
    print('对的')
if 'love' not in t:
    print('不爱了')
```        
        #元组遍历
```
t = 'lin san', 'love', 'lin ci'
for i in t:
    print(i)
         
#嵌套元组
t = ((10,20,30),('lin san', 'love', 'lin ci'),(3,2,1))
#嵌套元组的访问
#双层循环访问
for i in t:
    print(i)
    for j in i:
        print(j)
        
#使用单层循环
for i,j,k in t:
    print(i,j,k)
#i,j,k要跟元组的元素个数对应
```           
    3.常用元组函数
        #len：长度
        #max：最大值
        #count：对某一元素计数
```
ta = 1,1,1,12,2,3
print(ta.count(1))
```        
        #index:某一元素所在位置
```
print(ta.index(3))
```        
        #tuple的特殊用法
```
a = 'lin san'
b = 'xu si'
a,b = b,a #对a，b值进行互换
```        
## set（集合）
    与数学中集合的概念一致
    内容无序 + 内容不重复
    
    1.集合的定义
```
#通过set关键字
sa = set()
        
#使用大括号
s = {1,2,2,3,5,32}
```        
    2.操作
```
#in操作
if 2 in s:
    print(222)
            
#遍历
for i in s:
    print(i)
            
s = {(10,20,30),('lin san', 'love', 'lin ci'),(3,2,1)}
for i,j,k in s:
    print(i,j,k)
```   
    3.集合的内涵
```
s = {1,2,3,4,5,6,7,8}
#利用s生成一个s1
#普通集合内涵
s1 = {i for i in s}

#带条件的集合内涵        
s2 = {i for i in s if i %2 ==0}
        
#多循环的集合内涵
s3 = {i**2 for i in s}
s4 = {m*n for m in s for n in s}
```        
    4.集合的内置函数
        #len：长度
        #max/min：最值
        #add：向集合中添加元素
```
s = {1,2}
s.add(223)
print(s)
```
        #clear：清空
```
s = {1,2,3,4,5}
print(id(s))
s.clear()
print(id(s))
# 结果表明clear函数是原地清空数据
```
        #remove和discard的区别
            remove删除的值如果不在集合中，报错
```
s = {1,2,3,4,5,100}
s.remove(4)
print(s)
s.discard(100)
print(s)

s.discard(5)
print(s)

s.remove(5)
print(s)

Traceback (most recent call last):
  File "<pyshell#42>", line 1, in <module>
    s.remove(5)
KeyError: 5
```
        #pop：弹出集合的一个内容
            删除的内容是随机的
```
s = {1,2,3,4,5,8}
d = s.pop()
print(d)
```
    5.集合的数学操作
    #intersection：交集
```
sa = {1,2,3,4,5,6,7}
sb = {4,5,6,7}
 #sa 和sb的交集
print(sa.intersection(sb))
```        
    #difference:差集
```
print(sa.difference(sb))
 #差集的另一种表示
print(sa - sb)
```        
    #union:并集
```
print(sa.union(sb))
```
    # issubset: 检查一个集合是否为另一个子集
    # issuperset: 检查一个集合是否为另一个超集
```
sa1 = sa.issubset(sb)
print(sa1)
```
    6.forzenset冰冻集合
        不允许修改的集合
```
sb = forzenset(sa)
```
## dict字典
    字典是一种组合数据，没有顺序色组合数组，数据以键值对形式出现
    1.字典的创建
```
# 创建空字典
d = {}
print(d)

# 创建空字典
d = dict()
print(d)

# 创建有值的字典， 每一组数据用冒号隔开， 每一对键值对用逗号隔开
d = {"one":1, "two":2, "three":3}
print(d)

# 用dict()创建有内容字典
d = dict({"one":1, "two":2, "three":3})
print(d)

# 用dict创建有内容字典
# 利用关键字参数
d = dict(one=1, two=2, three=3)
print(d)

#用元组创建
d = dict( [("one",1), ("two",2), ("three",3)])
print(d)
```
    2.字典的特征
        字典是序列类型，但是是无序序列，所以没有分片和索引
        字典中的数据每个都有键值对组成，即kv对
            key：必须是可哈希的值，比如int,string,float,tuple, 但是，list,set,dict 不行
            value: 任何值
    3.字典常见操作
    #访问数据
```
d = {"one":1, "two":2, "three":3}
# 注意访问格式
# 中括号内是键值
print(d["one"])

d["one"] = "eins"
print(d)

# 删除某个操作
# 使用del操作
del d["one"]
print(d)
```
    #成员检测
```
# 成员检测检测的是key内容
d = {"one":1, "two":2, "three":3}
if 2 in d:
    print("value")
    
if "two" in d:
    print("key")
    
if ("two",2) in d:
    print("kv")
```
    #遍历
```
# 按key来使用for循环
d = {"one":1, "two":2, "three":3}
# 使用for循环，直接按key值访问
for k in d:
    print(k,  d[k])
    
for k in d.keys():
    print(k,  d[k])
    
# 只访问字典的值
for v in d.values():
    print(v)
    
# 注意以下特殊用法
for k,v in d.items():
    print(k,'--',v)
```
    #字典生成式
```
d = {"one":1, "two":2, "three":3}

# 常规字典生成式
dd = {k:v for k,v in d.items()}
print(dd)

# 加限制条件的字典生成式
dd = {k:v for k,v in d.items() if v % 2 == 0}
print(dd)
```
    4.字典相关函数
    # 通用函数： len, max, min, dict
    # str(字典): 返回字典的字符串格式
```
d = {"one":1, "two":2, "three":3}
print(str(d))
```
    # clear: 清空字典
    # items: 返回字典的键值对组成的元组格式
```
d = {"one":1, "two":2, "three":3}
i = d.items()
print(type(i))
print(i)
```
    # keys:返回字典的键组成的一个结构
```
k = d.keys()
print(type(k))
print(k)
```
    # values: 同理，一个可迭代的结构
```
v = d.values()
print(type(v))
print(v)
```
    # get: 根据指定键返回相应的值， 好处是，可以设置默认值
```
d = {"one":1, "two":2, "three":3}
print(d.get("on333"))

# get默认值是None，可以设置
print(d.get("one", 100))
print(d.get("one333", 100))
```
    # fromkeys: 使用指定的序列作为键，使用一个值作为字典的所有的键的值
```
l = ["eins", "zwei", "drei"]
# 注意fromkeys两个参数的类型
# 注意fromkeys的调用主体
d = dict.fromkeys(l, "hahahahahah")
print(d)
```
2020.1.4
## 递归函数
    递归：函数间接或者直接调用自己
    优点：简洁，理解容易
    缺点：对递归深度有限制，消耗资源大
    python对递归深度有限制，超过限制报错
    递归分两个过程
        往下调用，分解过程
        往上回溯，综合过程
    递归一定要有结束条件
```    
#例：计算阶乘
def func(n):
    if n == 1:
        return 1
    return n * func(n-1)
    
#例：斐波那契数列
def fib(n):
    if n == 1 or n == 2:
        return 1
    return fib(n-1) + fib(n-2)
        
#例：汉诺塔
a = 'A'
b = 'B'
c = 'C'
def hano(a,b,c,n):
    if n == 1:
        print("{}->{}".format(a,c))
        return None
    if n == 2:
        print("{}->{}".format(a,c))
        print("{}->{}".format(a,b))
        print("{}->{}".format(b,c))
        return None
    hano(a,b,c,n-1)
    print("{}->{}".format(a,c))
    hano(b,a,c,n-1)
```        
2020.1.5
## OOP
    1.思想
        以模块化思想解决工程问题
        面向过程 vs 面向对象
        由面向过程转向面向对象
        
        OOA:面向对象的分析
        OOD:面向对象的设计
        OOI:xxx的实现
        OOA->OOD->OOI:面向对象的实现过程
    2.类 vs 对象
        类：抽象，描述的是一个集合，侧重于共性
        对象：具象，描述的是个体
        类跟对象的关系
            一个是具象，代表一类事物的某一个个体
            一个是抽象，代表的的是一大类事物
        
    3.类的内容：
        动作，函数
        属性，变量
        
    4.类命名：
        遵循大驼峰
        第一个字母大写
        尽量避开跟系统命名相似的命名
    5.定义类：class关键字
```        
#类的例子
class Student():
    name = "lin san"
    age = 18
        
    def sayHi(self):
        print("love you")
        return None
```
    6.类和对象的成员分析
        类和对象都可以存储成员，成员可以归类所有，也可以归对象所有
        类存储成员时使用的是与类关联的一个对象
        对象存储成员是是存储在当前对象中
        对象访问一个成员时，如果对象中没有该成员，尝试访问类中的同名成员， 
        如果对象中有此成员，一定使用对象中的成员
        创建对象的时候，类中的成员不会放入对象当中，而是得到一个空对象，没有成员
        通过对象对类中成员重新赋值或者通过对象添加成员时，对应成员会保存在对象中，而不会修改类成员
```
class A():
    name = "lin san"
    age = 18
    # 注意say的写法，参数由一个self
    def say(self):
        self.name = "aaaa"
        self.age = 200

# 此案例说明
# 类实例的属性和其对象的实例的属性在不对对象的实例属性赋值的前提下，指向同一个变量
        
# 此时，A称为类实例
print(A.name)
print(A.age)

print(id(A.name))
print(id(A.age))

a = A()

print(a.name)
print(a.age)
print(id(a.name))
print(id(a.age))
```
    7.关与self
        self在对象的方法中表示当前对象本身，如果通过对象调用一个方法，该对象会自动传入到当前方法的第一个参数中 
        self不是关键字，只是一个用于接受对象的普通参数，理论上可以用任何一个普通变量名代替
        方法中有self形参的方法称为非绑定类的方法，可以通过对象访问，没有self的是绑定类的方法，只能通过类访问
        使用类访问绑定类的方法时，如果类方法中需要访问当前类的成员，可以通过 __class__成员名来访问
```        
# 关于self的案例
class A():
    name = " liuying"
    age = 18
    def __init__(self):
        self.name = "aaaa"
        self.age = 200
    def say(self):
        print(self.name)
        print(self.age)
        
class B():
    name = "bbbb"
    age = 90
    
a = A()
# 此时，系统会默认把a作为第一个参数传入函数
a.say()
   
# 此时，self被a替换
A.say(a)
# 同样可以把A作为参数传入
A.say(A)

# 此时，传入的是类实例B，因为B具有name和age属性，所以不会报错
A.say(B)
# 以上代码，利用了鸭子模型
```
    #类的变量作用域的问题
        类变量：属于自己的变量
        实例变量：属于实例的变量
        访问实例的属性，如果实例没有定义属性，则自动访问类的属性，如果类也没有定义，报错
```
class Student():
    #name，age是类自己的变量
    name = "lin san"
    age = 18
        
    def sayHi(self,n,a):
        self.name = n
        self.age = a
        print("my name is {},i am {}years old".format(self.name,self.age))
        return None
    #以下案例说明，实例变量可以借用类的变量
    linsi = Student()
    #linsi.sayHi("linsan",16)   #观察有无此语句的区别
    print("my name is {},i am {}years old".format(Student.name,Student.age))
    print("my name is {},i am {}years old".format(linsi.name,linsi.age))
```        
    #访问类的属性
        在类里面如果强制访问类的属性，则需要使用__class__，（前后两个下划线）
        类方法：定义类的方法的时候，没有self参数
        类的方法中只允许使用类的内容
        两种用法：
            ClassName
            __class__
```
class Student():
    #name，age是类自己的变量
    name = "lin san"
    age = 18
        
    def sayHi(self):
        print("my name is {},i am {}years old".format(self.name,self.age))
        return None
        #sos是类的方法
        #如何访问类的变量
        #调用需要用到特殊的方法
    def sos():
        #类方法不允许访问实例的任何内容
        #如果访问类的内容，注意两种用法
        print("my name is {},i am {}years old".format(Student.name,__class__.age))
        return None
                
#体验类的方法
s = Student()
#调用类方法的例子
Student.sos()
```
    #面向对象的三大特征：继承、封装、多态
2020.1.31
## 封装
    封装就是对对象的成员
    封装的三个级别：
        公开，public
        受保护的，protected
        私有的，private
        public，private，protected不是关键字
    判别对象的位置
        对象内部
        对象外部
        子类中
    [python中下划线使用](http://blog.csdn.net/handsomekang/article/details/40303207) 
    私有
        私有成员是最高级别的封装，只能在当前类或对象中访问
        在成员前面添加两个两个下划线即可
            class Person():
                # name是共有的成员 
                name = "liuying"
                # __age就是私有成员
                __age = 18
        Python的私有不是真私有，是一种称为name mangling的改名策略
        可以使用对象._classname_attributename访问 
```
# 私有变量案例
class Person():
    # name是公有的成员 
    name = "linsan"
    # __age就是私有成员
    __age = 18
                
p = Person()
# name是公有变量
print(p.name)
# __age是私有变量
print(p.__age)

Traceback (most recent call last):
  File "<pyshell#6>", line 1, in <module>
    print(p.__age)
AttributeError: 'Person' object has no attribute '__age'

# name mangling技术
p._Person__age = 19
print(p._Person__age)
```
    受保护的封装  protected
        受保护的封装是将对象成员进行一定级别的封装，然后，在类中或者子类中都可以进行访问，但是在外部不可以
        封装方法： 在成员名称前添加一个下划线即可
    公开的，公共的 public
        公共的封装实际对成员没有任何操作，任何地方都可以访问  
2020.2.2
## 继承
    继承就是一个类可以获得另外一个类中的成员属性和成员方法
    作用： 减少代码，增加代码的复用功能， 同时可以设置类与类之间的关系
    1.继承与被继承的概念：
        被继承的类叫父类，也叫基类，也叫超类
        用于继承的类，叫子类，也叫派生类
        继承与被继承一定存在一个 is-a 关系
```
# 继承的语法
# 在python中，任何类都有一个共同的父类叫object

class Person():
    name = "NoName"
    age = 18
    __score = 0 # 考试成绩是秘密，只要自己知道
    _petname = "sec" #小名，是保护的，子类可以用，但不能公用
    def sleep(self):
        print("Sleeping ... ...")
        
#父类写在括号内
class Teacher(Person):
    teacher_id = "9527"
    def make_test(self):
        print("attention")
    
t = Teacher()
print(t.name)
# 受保护不能外部访问，为啥这里可以
print(t._petname)

# 私有访问问题
# 公开访问私有变量，报错
#print(t.__score)

t.sleep()
print(t.teacher_id)
t.make_test()
```
    2.继承的特征
        所有的类都继承自object类，即所有的类都是object类的子类
        子类一旦继承父类，则可以使用父类中除私有成员外的所有内容
        子类继承父类后并没有将父类成员完全赋值到子类中，而是通过引用关系访问调用
        子类中可以定义独有的成员属性和方法
        子类中定义的成员和父类成员如果相同，则优先使用子类成员
        子类如果想扩充父类的方法，可以在定义新方法的同时访问父类成员来进行代码重用，可以使用 [父类名.父类成员] 的格式来调用父类成员，也可以使用super().父类成员的格式来调用
```
# 子类和父类定义同一个名称变量，则优先使用子类本身
class Person():
    name = "NoName"
    age = 18
    __score = 0 # 考试成绩是秘密，只要自己知道
    _petname = "sec" #小名，是保护的，子类可以用，但不能公用
    def sleep(self):
        print("Sleeping ... ...")

class Teacher(Person):
    teacher_id = "9527"
    name = "linsan"
    def make_test(self):
        print("attention")
        
t = Teacher()
print(t.name)
```
```
# 子类扩充父类功能的案例
class Person():
    name = "NoName"
    age = 18
    __score = 0 # 考试成绩是秘密，只要自己知道
    _petname = "sec" #小名，是保护的，子类可以用，但不能公用
    def sleep(self):
        print("Sleeping ... ...")
    def work(self):
        print("make some money")

class Teacher(Person):
    teacher_id = "9527"
    name = "linsan"
    def make_test(self):
        print("attention")
        
    def work(self):
        # 扩充父类的功能只需要调用父类相应的函数
        #Person.work(self)
        # 扩充父类的另一种方法
        # super代表得到父类
        super().work()
        self.make_test()
        
t = Teacher()
t.work()
```
    3.继承变量函数的查找顺序问题
        优先查找自己的变量
        没有则查找父类
        构造函数如果本类中没有定义，则自动查找调用父类构造函数
        如果本类有定义，则不在继续向上查找
    4.构造函数
        是一类特殊的函数，在类进行实例化之前进行调用
        如果定义了构造函数，则实例化时使用构造函数，不查找父类构造函数
        如果没定义，则自动查找父类构造函数
        如果子类没定义，父类的构造函数带参数，则构造对象时的参数应该按父类参数构造
```
# 构造函数的概念
class Dog():
    # __init__就是构造函数
    # 每次实例化的时候，第一个被自动的调用
    # 因为主要工作是进行初始化，所以得名
    def __init__(self):
        print("I am init in dog")

# 实例化的时候，括号内的参数需要跟构造函数参数匹配
kaka = Dog()
```
```
#继承中的构造函数
class Animel():
    pass
class PaxingAni(Animel):
    pass
class Dog(PaxingAni):
    def __init__(self):
        print("I am init in dog")

kaka = Dog()
```
```
# 继承中的构造函数 - 2
class Animel():
    def __init__(self):
        print("Animel")
class PaxingAni(Animel):
    def __init__(self):
        print(" Paxing Dongwu")
class Dog(PaxingAni):
    def __init__(self):
        print("I am init in dog")
        
# 因为找到了构造函数，则不在查找父类的构造函数
kaka = Dog()

# 猫没有写构造函数
class Cat(PaxingAni):
    pass
# 此时应该自动调用构造函数，因为Cat没有构造函数，所以查找父类构造函数
# 在PaxingAni中查找到了构造函数，则停止向上查找
c = Cat()
```
```
# 继承中的构造函数 - 3
class Animel():
    def __init__(self):
        print("Animel")
class PaxingAni(Animel):
    def __init__(self, name):
        print(" Paxing Dongwu {0}".format(name))
class Dog(PaxingAni):
    def __init__(self):
        print("I am init in dog")
        
# 实例化Dog时，查找到Dog的构造函数，参数匹配，不报错      
d = Dog()

class Cat(PaxingAni):
    pass

# 此时，由于Cat没有构造函数，则向上查找
#  因为PaxingAni的构造函数需要两个参数，实例化的时候给了一个，报错
c = Cat()
```
    5.super
        super不是关键字， 而是一个类
        super的作用是获取MRO（MethodResolustionOrder）列表中的第一个类
        super于父类直接没任何实质性关系，但通过super可以调用到父类
        super使用两个方法,参见在构造函数中调用父类的构造函数
    6.单继承和多继承的优缺点
        单继承：
            传承有序逻辑清晰语法简单隐患少
            功能不能无限扩展，只能在当前唯一的继承链中扩展
        多继承：
            优点：类的功能扩展方便
            缺点：继承关系混乱
```
# 多继承的例子
# 子类可以直接拥有父类的属性和方法，私有属性和方法除外
class Fish():
    def __init__(self,name):
        self.name = name
    def swim(self):
        print("i am swimming......")
        
class Bird():
    def __init__(self, name):
        self.name = name
    def fly(self):
        print("I am flying.....")

class Person():
    def __init__(self, name):
        self.name = name
    def work(self):
        print("Working........")
        
# 单继承的例子      
class Student(Person):
    def __init__(self, name):
        self.name = name
stu = Student("yueyue")
stu.work()
        
        
# 多继承的例子  
class SuperMan(Person, Bird, Fish):
    def __init__(self, name):
        self.name = name


class SwimMan(Person, Fish):
    def __init__(self, name):
        self.name = name
        
s = SuperMan("yueyue")
s.fly()
s.swim()
```
    7.菱形继承/钻石继承问题
        多个子类继承自同一个父类，这些子类由被同一个类继承，于是继承关系图形成一个菱形图谱
        [MRO](https://www.cnblogs.com/whatisfantasy/p/6046991.html)
        关于多继承的MRO
            MRO就是多继承中，用于保存继承顺序的一个列表
            python本身采用C3算法来多多继承的菱形继承进行计算的结果
            MRO列表的计算原则：
                子类永远在父类前面
                如果多个父类，则根据继承语法中括号内类的书写顺序存放
                如果多个类继承了同一个父类，孙子类中只会选取继承语法括号中第一个父类的父类
    8.构造函数
        在对象进行实例化的时候，系统自动调用的一个函数叫构造函数，通常此函数用来对实例对象进行初始化
        构造函数一定要有，如果没有，则自动向上查找，按照MRO顺序，直到找到为止
```
class Person():
    def __init__(self):
        self.name = 'NoName'
        self.age = 18
        self.address = 'xxxx'
        print('in init func')

p = Person()

```
```
# # 构造函数的调用顺序
class A():
    def __init__(self):
        print("A")

class B(A):
    def __init__(self, name):
        print("B")
        print(name)
        
class C(B):
    pass

# 此时，首先查找C的构造函数
# 此时，会出现参数结构不对应错误
c = C()


Traceback (most recent call last):
  File "<pyshell#12>", line 1, in <module>
    c = C()
TypeError: __init__() missing 1 required positional argument: 'name'
```
```
# # 构造函数的调用顺序
class A():
    def __init__(self):
        print("A")
class B(A):
    def __init__(self, name):
        print("B")
        print(name)
class C(B):
    # c中想扩展B的构造函数
    # 由两种方法实现
    '''
    # 第一种是通过父类名调用
    def __init__(self, name):
        # 首先调用父类构造函数
        B.__init__(self, name)
        # 其次，再增加自己的功能
        print("这是C中附加的功能")
    '''  
    # 第二种，使用super调用
    def __init__(self, name):
        # 首先调用父类构造函数
        super(C, self).__init__(name)
        # 其次，再增加自己的功能
        print("这是C中附加的功能")
        
c = C("我是C")
```
2020.2.3
## 多态
    多态就是同一个对象在不同情况才有不同的状态出现
    多态不是语法，是一种设计思想
    多态性：一种调用方式，不同的执行效果
    多态：同一事物的多种形态
    [多态和多态性](https://www.cnblogs.com/luchuangao/p/6739557.html)
    
    1.Mixin设计模式    
        主要采用多继承方式对类的功能进行扩展
        [Mixin概念](https://www.zhihu.com/question/20778853)
        [MRO and Mixin](http://blog.csdn.net/robinjwong/article/details/48375833)
        [Mixin模式](https://www.cnblogs.com/xybaby/p/6484262.html)
        [Mixin MRO](http://runforever.github.io/2014-07-19/2014-07-19-python-mixin%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/)
        [MRO](http://xiaocong.github.io/blog/2012/06/13/python-mixin-and-mro/)
        
        使用多继承语法来实现Minxin
            他必须表示某一单一功能，而不是某个物品
            职责必须单一，如果有多个功能，则写多个Minxin
            Minxin不能依赖于子类的实现
            子类即使没有继承这个Minxin类，也能照样工作，稚时缺少了某个功能
    2.优点
        使用Minxin可以在不对类进行任何修改的情况下，扩充功能
        可以方便的组织和维护不同功能组合的划分
        可以根据需要任意调整功能类的组合
        可以避免创建很多新的类，导致类的继承混乱
```
#Minxin案例
class Person():
    name = "linsan"
    age = 18
    def eat(self):
        print("EAT.......")
    def drink(self):
        print("DRINK......")
    def sleep(self):
        print("SLEEP.....")
                
class Teacher(Person):
    def work(self):
        print("Work")

class Student(Person):
    def study(self):
        print("Study")

class Tutor(Teacher, Student):
    pass

t = Tutor()
             
print(Tutor.__mro__)
print(t.__dict__)
print(Tutor.__dict__)

class TeacherMixin():
    def work(self):
        print("Work")

class StudentMixin():
    def study(self):
        print("Study")
                    
class TutorM(Person, TeacherMixin, StudentMixin):
    pass

tt = TutorM()
print(TutorM.__mro__)
print(tt.__dict__)
print(TutorM.__dict__)
```
2020.2.5
## 类的相关函数
> issubclass:检测一个类是否是另一个类的子类
  isinstance:检测一个对象是否是一个类的实例
  hasattr:检测一个对象是否由成员xxx
  getattr: get attribute
  setattr: set attribute
  delattr: delete attribute
  dir: 获取对象的成员列表
```
#issubclass
class A():
    pass
class B(A):
    pass
class C():
    pass
print( issubclass(B, A))
print( issubclass(C, A))
print( issubclass(B, object))
```
```
#isinstance
class A():
    pass
a = A()
print(isinstance(a, A))
print(isinstance(A, A))
```
```
#hasattr
class A():
    name = "NoName"
a = A()
print(hasattr(a, "name" ))
print(hasattr(a, "age" ))
```
```
#dir 案例
class A():
    pass
#dir(A)
a = A()
dir(a)
```
## 类的成员描述符（属性）
    类的成员描述符是为了在类中对类的成员属性进行星官操作而创建的一种方式
        get：获取属性的操作
        set：修改或者添加属性操作
        delete：删除属性的操作
    使用类的成员描述符，有三种方法
        使用类的实现描述器
        使用属性修饰符
        使用property函数
            property函数简单
            property(fget, fset, fdel, doc)
```
#x = property(fget,fset,fdel,doc)
class Person():
    def fget(self):
        return self._name * 2
    def fset(self,name):
        self._name = name.upper()
    def fdel(self):
        self._name = 'NoName'
    name = property(fget,fset,fdel,'对name操作')
    
p = Person()
p.name = 'linsan'
print(p.name)
```
    无论哪种修饰符都是为了对成员属性进行相应的控制  
        类的方式： 适合多个类中的多个属性共用用一个描述符
        property：使用当前类中使用，可以控制一个类中多个属性
        属性修饰符： 使用于当前类中使用，控制一个类中的一个属性
## 类的内置属性
    __dict__:以字典的方式显示类的成员组成
    __doc__: 获取类的文档信息
    __name__:获取类的名称，如果在模块中使用，获取模块的名称
    __bases__: 获取某个类的所有父类，以元组的方式显示
## 类的常用魔术方法
    魔术方法就是不需要人为调用的方法，基本是在特定的时刻自动触发
    魔术方法的统一的特征，方法名被前后各两个下滑线包裹
    [魔术方法](http://pythonbase.baoshu.red/index.html)
    1.操作类
        __init__: 构造函数
        __new__: 对象实例化方法，此函数较特殊，一般不需要使用
        __call__: 对象当函数使用的时候触发
        __str__: 当对象被当做字符串使用的时候调用
        __repr__: 返回字符串，跟__str__具体区别请百度
```
#init 举例
class A():
    def __init__(self, name = 0):
        print("哈哈，我被调用了")
        
a = A()
```
```
#__call__举例
class A():
    def __init__(self, name = 0):
        print("哈哈，我被调用了")
        
    def __call__(self):
        print("我被调用了again")
        
a = A()
a()
```
```
#__str__举例
class A():
    def __init__(self, name = 0):
        print("哈哈，我被调用了")
        
    def __call__(self):
        print("我被调用了again")
       
    def __str__(self):
        return "图灵学院的例子"
a = A()
print(a)
```
    2.描述符相关
        __set__
        __get__
        __delete__
    3.属性操作相关
        __getattr__: 访问一个不存在的属性时触发
        __setattr__: 对成员属性进行设置的时候触发
            参数： 
                self用来获取当前对象
                被设置的属性名称，以字符串形式出现
                需要对属性名称设置的值
            作用：进行属性设置的时候进行验证或者修改
            注意：在该方法中不能对属性直接进行赋值操作，否则死循环
```
#__getattr__
class A():
    name = "NoName"
    age = 18
   
    def __getattr__(self, name):
        print("没找到呀没找到")
        print(name)
        
a = A()
print(a.name)
print(a.addr) 
```
```
#__setattr__案例
class Person():
    def __init__(self):
        pass
    def __setattr__(self, name, value):
        print("设置属性： {0}".format(name))
        # 下面语句会导致问题，死循环
        #self.name = value
        # 此种情况，为了避免死循环，规定统一调用父类魔法函数
        super().__setattr__(name, value)
        
p = Person()
print(p.__dict__)
p.age = 18
```
    4.运算分类相关魔术方法
        __gt__: 进行大于判断的时候触发的函数
            参数：
                - self
                - 第二个参数是第二个对象
                - 返回值可以是任意值，推荐返回布尔值
```
#__gt__
class Student():
    def __init__(self, name):
        self._name = name
    
    def __gt__(self, obj):
        print("哈哈， {0} 会比 {1} 大吗？".format(self, obj))
        return self._name > obj._name
    
stu1 = Student("one")
stu2 = Student("two")
print(stu1 > stu2)
```
## 类和对象的三种方法
    1.实例（对象）方法        需要实例化对象才能使用的方法，使用过程中可能需要借助对象的其他对象的方法完成
        特征：
            1.在类中定义的方法，含有self参数
            2.含有self的方法，只能使用对象进行调用
            3.该方法会把调用的对象传递进来
    2.静态方法
        不需要实例化，通过类直接访问
        特征：
            1.在类中定义的方法，使用了装饰器 @staticmethod 进行了装饰
            2.可以使用对象或者类进行调用
            3.不会传递对象或者类进来
    3.类方法
        不需要实例化
         特征：
            1.在类中定义的方法，使用装饰器 @classmethod 进行了装饰
            2.方法中有cls这个行参。不需要实例化对象，直接使用类进行调用
            3.会把调用这个方法的类传递进来
    4.绑定类方法
        特征：
            1.在类中定义的方法
            2.只能使用类进行调用
            3.不会传递对象或者类进来
```
#三种方法的案例
class Person:
    # 实例方法
    def eat(self):
        print(self)
        print("Eating.....")
    
    #类方法
    # 类方法的第一个参数，一般命名为cls，区别于self
    @classmethod
    def play(cls):
        print(cls)
        print("Playing.....")
        
    # 静态方法
    # 不需要用第一个参数表示自身或者类
    @staticmethod
    def say():
        print("Saying....")
        
yueyue = Person()

# 实例方法
yueyue.eat()
# 类方法
Person.play()
yueyue.play()
#静态方法
Person.say()
yueyue.say()
```
2020.2.6
```
#变量的三种用法
class A():
    def __init__(self):
        self.name = "haha"
        self.age =18
     
a = A()
#属性的三种用法
#1， 赋值
#2. 读取
#3. 删除
a.name = "linsan"
print(a.name)
del a.name
```
```
#类属性 property
#应用场景：
#对变量除了普通的三种操作，还想增加一些附加的操作，那么可以通过property完成
class A():
    def __init__(self):
        self.name = "haha"
        self.age =18
    # 此功能，是对类变量进行读取操作的时候应该执行的函数功能
    def fget(self):
        print("我被读取了")
        return self.name
    # 模拟的是对变量进行写操作的时候执行的功能
    def fset(self, name):
        print("我被写入了，但是还可以左好多事情")
        self.name = "图灵学院：" + name 
    # fdel模拟的是删除变量的时候进行的操作
    def fdel(self):
        pass
        
    # property的四个参数顺序是固定的
    # 第一个参数代表读取的时候需要调用的函数
    # 第二个参数代表写入的时候需要调用的函数
    # 第三个是删除
    name2 = property(fget, fset, fdel, "这是一个property的例子")
    
a = A()
print(a.name)
print(a.name2)
```
## 抽象类
    抽象方法： 没有具体实现内容的方法成为抽象方法
    抽象方法的主要意义是规范了子类的行为和接口
    抽象类的使用需要借助abc模块
            import abc
           
    抽象类：包含抽象方法的类叫抽象类，通常成为ABC类
    抽象类的使用
        抽象类可以包含抽象方法，也可以包含具体方法
        抽象类中可以有方法也可以有属性
        抽象类不允许直接实例化
        必须继承才可以使用，且继承的子类必须实现所有继承来的抽象方法
        假定子类没有是现实所有继承的抽象方法，则子类也不能实例化
        抽象类的主要作用是设定类的标准，以便于开发的时候具有统一的规范
```
#抽象类的实现
import abc
#声明一个类并且指定当前类的元类
class Human(metaclass=abc.ABCMeta):
    # 定义一个抽象的方法
    @abc.abstractmethod
    def smoking(self):
        pass
    
    # 定义类抽象方法
    @abc.abstractclassmethod
    def drink():
        pass
    
    # 定义静态抽象方法
    @abc.abstractstaticmethod
    def play():
        pass
```
## 自定义类
    类其实是一个类定义和各种方法的自由组合
    可以定义类和函数，然后自己通过类直接赋值
```
#函数名可以当变量使用
def sayHello(name):
    print("{0}你好，来一发吗？".format(name))
    
linsan = sayHello
linsan("yueyue")
```
```
#自己组装一个类
class A():
    pass

def say(self):
    print("Saying... ...")
    
A.say = say
a = A()
a.say()
```
    可以借助于MethodType实现
```
#自己组装一个类
from types import MethodType
class A():
    pass

def say(self):
    print("Saying... ...")
    
a = A()
a.say = MethodType(say, A)
a.say()
```
    借助于type实现
```
#利用type造一个类
#先定义类应该具有的成员函数
def say(self):
    print("Saying.....")
    
def talk(self):
    print("Talking .....")
    
#用type来创建一个类
A = type("AName", (object, ), {"class_say":say, "class_talk":talk})

#然后可以像正常访问一样使用类
a = A()

a.class_say()
a.class_talk()
```
    利用元类实现- MetaClass
        元类是类
        作用来创造别的类
```
#元类写法是固定的，必须继承自type
#元类一般命名以MetaClass结尾
class TulingMetaClass(type):
    # 注意以下写法
    def __new__(cls, name, bases, attrs):
        #自己的业务处理
        print("哈哈，我是元类呀")
        attrs['id'] = '000000'
        attrs['addr'] = "xxxxxxxxxxx"
        return type.__new__(cls, name, bases, attrs)
    
#元类定义完就可以使用，使用注意写法
class Teacher(object, metaclass=TulingMetaClass):
    pass

t = Teacher()
t.id
```
## python编码问题
    python文件默认utf-8编码，如果特殊需要，需要声明
        放在第一行，或者第二行
        ```# -*- coding: window-1252 -*-```
        读写文件默认utf-8，可以指定
        code point方式比较字符串，可能会带来问题
            重音符号的表示
            使用 unicidedata.normalize 函数
        python源码中出现了解码错误，那么会产生SytanxError异常
        其他情况下，如果发现编码解码错误，会产生UnicodeEncodeError，UnicodecodeError异常

## 传值和传地址的区别
    1.对于简单的数值，采用传值操作，即在函数内对参数的操作不影响外面的变量
    2.对于复杂的变量，采用传址操作，此时函数的参数和外部变量是同一份内容，任何地方对此内容的更改都影响另外的变量或参数的使用
```
def a(n):
    n[2] = 300
    print(n)
    return None

def b(n):
    n += 100
    print(n)
    return None


an = [1,2,3,4,5,6]
bn = 9

print(an)
a(an)
print(an)

print(bn)
b(bn)
print(bn)

#结果：
[1, 2, 3, 4, 5, 6]
[1, 2, 300, 4, 5, 6]
[1, 2, 300, 4, 5, 6]
9
109
9
```

## 深拷贝和浅拷贝的区别
### 浅拷贝
        浅拷贝只能拷贝列表中的一维元素，如果列表中存在二维元素或容器，则引用而不是拷贝
        使用cpoy函数或者copy模块中的copy函数拷贝的都是浅拷贝
```
#浅拷贝 只能拷贝当前列表，不能拷贝列表中的多维列表元素
varlist = [1,2,3]
#简单的拷贝 就可以把列表复制一份
newlist = varlist.copy()
# 对新拷贝的列表进行操作，也是独立的
del newlist[1]
#print(varlist,id(varlist))
#print(newlist,id(newlist))
'''
[1, 2, 3] 4332224992
[1, 3] 4332227552
'''

#多维列表
varlist = [1,2,3,['a','b','c']]

#使用copy函数 拷贝一个多维列表
newlist = varlist.copy()

'''
print(newlist,id(newlist))
print(varlist,id(varlist))
[1, 2, 3, ['a', 'b', 'c']] 4361085408
[1, 2, 3, ['a', 'b', 'c']] 4361898496
'''
#如果是一个被拷贝的列表，对它的多维列表元素进行操作时，会导致原列表中的多维列表也发生了变化
del newlist[3][1]

'''
通过id检测，发现列表中的多维列表是同一个元素（对象）
print(newlist[3],id(newlist[3]))
print(varlist[3],id(varlist[3]))
['a', 'c'] 4325397360
['a', 'c'] 4325397360
'''
```
### 深拷贝
        深拷贝就是不光拷贝了当前的列表，同时把列表中的多维元素或容器也拷贝了一份，而不是引用
        使用copy模块中的 deepcopy 函数可以完成深拷贝
```
#深拷贝 就是不光拷贝了当前的列表，同时把列表中的多维元素也拷贝了一份
import copy

varlist = [1,2,3,['a','b','c']]

#使用 copy模块中 深拷贝方法 deepcopy
newlist = copy.deepcopy(varlist)
del newlist[3][1]

print(varlist)
print(newlist)

'''
print(newlist[3],id(newlist[3]))
print(varlist[3],id(varlist[3]))
['a', 'c'] 4483351248
['a', 'b', 'c'] 4483003568
'''
```
2020.2.7
## 模块
    一个模块就是一个包含python代码的文件，模块就是个python文件
### 为什么用模块
        程序太大，编写维护非常不方便，需要拆分
        模块可以增加代码重复利用的方式
        当作命名空间使用，避免命名冲突
### 如何定义模块
        模块就是一个不同文件，所以代码可以直接书写
        根据模块规范，最好在模块中编写以下内容
            函数(单一功能)
            类（相似功能的组合，或者类似业务模块）
            测试代码
```
class Student():
    def __init__(self,name='NoName',age=18):
        self.name = name
        self.age = age
    def say(self):
        print("My name is {0}".format(self.name))

def sayHello():
    print("Hi！")
    
#此判断语句建议一直作为程序的入口
if __name__ == '__main__':
    print("我是模块p01呀")
```
### 如何使用模块
    模块直接导入
        假如模块名称直接以数字开头，需要借助importlib
        import importlib
        lin = importlib.import_module("01")
    语法：
        import module_name
        module_name.function_name
        moduel_name.class_name
    import 模块 as 别名
        导入的同时给模块起一个别名
        其余用法跟第一种相同 
    from module_name import func_name, class_name
        按上述方法有选择性的导入
        使用的时候可以直接使用导入的内容，不需要前缀
    from module_name import *
        导入模块所有内容
    if __name__ == "__main__ 的使用
        可以有效避免模块代码被导入的时候被动执行的问题
        建议所有程序的入口都以此代码为入口
    
## 模块的搜索路径和存储
    什么是模块的搜索路径：
        加载模块的时候，系统会在那些地方寻找此模块
    系统默认的模块搜索路径
            import sys
            sys.path 属性可以获取路径列表
    添加搜索路径
             sys.path.append(dir)
    模块的加载顺序
        1.搜索内存中已经加载好的模块
        2.搜索python的内置模块
        3.搜索sys.path路径 
## 包
    包是一种组织管理代码的方式，包里面存放的是模块
    用于将模块包含在一起的文件夹就是包
### 自定义包的结构
    
        |---包
        |---|--- __init__.py  包的标志文件
        |---|--- 模块1
        |---|--- 模块2
        |---|--- 子包(子文件夹)
        |---|---|--- __init__.py  包的标志文件
        |---|---|--- 子包模块1
        |---|---|--- 子包模块2
        
### 包的导入操作
        import package_name
            直接导入一个包，可以使用__init__.py中的内容
            使用方式：
                package_name.func_name
                package_name.class_naem.func_name()
        import package_name as p
            具体用法跟使用方式，跟上述简单导入一致
            注意的是此种方法是默认对__init__.py内容的导入
            
        import package.module
            导入保重某一个具体的模块
            使用方法
                package.module.func_name
                package.module.class.fun()
                package.module.class.var
        import package.module as pm
        
    from ... import 导入
        from package import module1, module2, module3, ..... 
        此种导入方式不执行__init__.py的内容
            from package import module
            module_name.func_name()
            module_name.class_name.func_name()
            module_name.class_name.var
        from package import *
            导入当前包 __init__.py文件中所有的函数和类
            使用方法
                    func_name()
                    class_name.func_name()
                    class_name.var
        
        from package.module import *
            导入包中指定的模块的所有内容    
            使用方法
                    func_name()
                    class_name.func_name()     
    在开发环境中经常会所以用其他模块，可以在当前包中直接导入其他模块中的内容
        import 完整的包或者模块的路径
    
    __all__ 的用法
        在使用from package import * 的时候， * 可以导入的内容  
        __init__.py中如果文件为空,或者没有 __all__，那么只可以把__init__中的内容导入
        __init__ 如果设置了__all__的值，那么则按照__all__ 指定的子包或者模块进行加载,如此则不会载入__init__中的内容
        __all__=['module1', 'module2', 'package1'.........]
## 命名空间
    用于区分不同位置不同功能但相同名称的函数或者变量的一个特定前缀
    作用是防止命名冲突
    
2020.2.8
## 异常
    广义上的错误分为错误和异常
    错误指的是可以人为避免
    异常是指在语法逻辑正确的前提下，出现的问题
    在python里，异常时一个类，可以处理和使用
    
### 异常的分类
    
        AssertError     断言语句（assert）失败
        AttributeError  尝试访问未知的对象属性
        EOFError    用户输入文件末尾标志EOF（Ctrl+d）
        FloatingPointError   浮点计算错误
        GeneratorExit   generator.close()方法被调用的时候
        ImportError     导入模块失败的时候
        IndexError  索引超出序列的范围
        KeyError    字典中查找一个不存在的关键字
        KeyboardInterrupt   用户输入中断键（Ctrl+c）
        MemoryError     内存溢出（可通过删除对象释放内存）
        NameError   尝试访问一个不存在的变量
        NotImplementedError     尚未实现的方法
        OSError     操作系统产生的异常（例如打开一个不存在的文件）
        OverflowError   数值运算超出最大限制
        ReferenceError  弱引用（weak reference）试图访问一个已经被垃圾回收机制回收了的对象
        RuntimeError    一般的运行时错误
        StopIteration   迭代器没有更多的值
        SyntaxError     Python的语法错误
        IndentationError    缩进错误
        TabError    Tab和空格混合使用
        SystemError     Python编译器系统错误
        SystemExit  Python编译器进程被关闭
        TypeError   不同类型间的无效操作
        UnboundLocalError   访问一个未初始化的本地变量（NameError的子类）
        UnicodeError    Unicode相关的错误（ValueError的子类）
        UnicodeEncodeError  Unicode编码时的错误（UnicodeError的子类）
        UnicodeDecodeError  Unicode解码时的错误（UnicodeError的子类）
        UnicodeTranslateError   Unicode转换时的错误（UnicodeError的子类）
        ValueError  传入无效的参数
        ZeroDivisionError   除数为零
        
### 异常处理
        不能保证成簇永远正确处理，但是必须保证程序在最坏的情况下得到的问题被妥善处理
        python的异常处理模块全部语法为：
            try:
                尝试实现某个操作，
                如果没出现异常，任务就可以完成
                如果出现异常，将异常从当前代码块扔出去尝试解决异常
        
            except 异常类型1:
                解决方案1：用于尝试在此处处理异常解决问题
        
            except 异常类型2：
                解决方案2：用于尝试在此处处理异常解决问题
        
            except (异常类型1,异常类型2...)
                解决方案：针对多个异常使用相同的处理方式
            
            excpet:
                解决方案：所有异常的解决方案
            
            else:
                如果没有出现任何异常，将会执行此处代码
            
            finally:
                管你有没有异常都要执行的代码
                
        流程
            1.执行try下面的语句
            2.如果出现异常，则在except语句里查找对应异常病进行处理
            3.如果没有出现异常，则执行else语句内容
            4.最后，不管是否出现异常，都要执行finally语句
            
            除except(最少一个)以外，else和finally可选
```
#简单异常案例
#给出提示信息
try:
    num = int(input("Plz input your number:"))
    rst = 100/num
    print("计算结果是： {0}".format(rst))
#捕获异常后，把异常实例化，出错信息会在实例里
#以下语句是捕获ZeroDivisionError异常并实例化实例e
except ZeroDivisionError as e:
    print(e)
    # exit是退出程序的意思
    exit()
```
```
# 简单异常案例
# 给出提示信息
try:
    num = int(input("Plz input your number:"))
    rst = 100/num
    print("计算结果是： {0}".format(rst))
#如果是多种error的情况
#需要把越具体的错误，越往前放
#在异常类继承关系中，越是子类的异常，越要往前放，
#越是父类的异常，越要往后放
#在处理异常的时候，一旦拦截到某一个异常，则不在继续往下查看，直接进行下一个
#代码，即有finally则执行finally语句块，否则就执行下一个大的语句
except ZeroDivisionError as e:
    print(e)
    exit()
except NameError as e:
    print("名字起错了")
    print(e)

except AttributeError as e:
    print("好像属性有问题")
    print(e)
    exit()
    
#所有异常都是继承自Exception
#如果写上下面这句话，任何异常都会拦截住
#而且，下面这句话一定是最后一个exception
except Exception as e:
    print("我也不知道就出错了")
    print(e)
```
### 用户手动引发异常
        当某些情况，用户希望自己引发一个异常的时候，可以使用
        raise 关键字来引发异常
```
#raise案例
#自己定义异常
#需要注意：自定义异常必须是系统异常的子类
class LinsanValueError(ValueError):
    pass
try:
    print("i love linsan")
    print(3.1415926)
    # 手动引发一个异常
    #注意语法：　raise　ＥｒｒｏｒＣｌａｓｓＮａｍｅ
    raise LinsanValueError
    print("还没完呀")
except NameError as e:
    print("NameError")
except ValueError as e:
    print("ValueError")
except Exception as e:
    print("有异常")
finally:
    print("我肯定会被执行的")
```
```
#else语句案例
try:
    num = int(input("Plz input your number:"))
    rst = 100/num
    print("计算结果是： {0}".format(rst))
except Exception as e:
    print("Exception")
    
else:
    print("No Exception")
finally:
    print("反正我会被执行")
```
### 关于自定义异常
        只要是raise异常，则推荐自定义异常
        在自定义异常的时候，一般包含以下内容：
            自定义发生异常的异常代码
            自定义发生异常后的问题提示
            自定义发生异常的行数
        最终的目的是，一旦发生异常，方便程序员快速定位错误现场

## 常用包
    calendar
    time
    datetime
    timeit
    os
    shutil
    zip
    math
    string
    上述所有模块使用理论上都应该先导入，string是特例
    calendar，time，datetime的区别参考中文意思
    
### calendar
        跟日历相关的模块
```
#calendar：　获取一年的日历字符串
#参数
#w = 每个日期之间的间隔字符数
#l = 每周所占用的行数
#c = 每个月之间的间隔字符数
cal = calendar.calendar(2020)
print(type(cal))
print(cal)
```
```
cal = calendar.calendar(2020, l=0, c=5)
print(cal)
```
    # isleap:判断某一年是否闰年
```
calendar.isleap(2020)
```
    # leapdays:获取指定年份之间的闰年的个数
```
calendar.leapdays(2000,2020)
```
    # month :获取某个月的日历字符串
        格式：calendar.month(年,月)
        返回值：月日历的字符串
```
m = calendar.month(2020,2)
print(m)
```
    # monthrange： 获取一个月的周几开始即和天数
        格式：calendar.monthrange(年,月)
        返回值：元组(周几开始,总天数)
        注意：周默认 0 -6 表示周一到周天       
```
w,t = calendar.monthrange(2020,2)
print(w)
print(t)
```
    # monthcalendar： 返回一个月每天的矩阵列表
        格式：calendar.monthcalendar(年，月)
        返回值：二级列表
        注意：矩阵中没有天数用0表示
```
m = calendar.monthcalendar(2020,2)
print(m)
```
    # prcal:直接打印日历
        calendar.prcal(2020)
    
    # prmonth：直接打印整个月的日历
        格式：calendar.prmonth(年，月)
        返回值：无
```
calendar.prmonth(2020,2)
```
    # weekday：获取周几
        格式:calendar.weekday(年，月，日)
        返回值:周几对应的数字
```
calendar.weekday(2020, 2, 8)
```
### time
    时间戳
        一个时间表示，根据不同语言，可以是整数或者浮点数
        是从1970年1月1日0时0分0秒到现在经历的秒数
        如果表示的时间是1970年以前或者太遥远的未来，可能出现异常
        32位操作系统能够支持到2038年
    UTC时间
        UTC又称为世界协调时间，以英国的格林尼治天文所在地区的时间作为参考的时间，也叫做世界标准时间。
        中国时间是 UTC+8 东八区
    夏令时
        夏令时就是在夏天的时候将时间调快一小时，本意是督促大家早睡早起节省蜡烛！ 每天变成25个小时，本质没变还是24小时
    时间元组
        一个包含时间内容的普通元组
        
            索引      内容    属性            值
        
            0       年       tm_year     2015
            1       月       tm_mon      1～12
            2       日       tm_mday     1～31
            3       时       tm_hour     0～23
            4       分       tm_min      0～59
            5       秒       tm_sec      0～61  60表示闰秒  61保留值
            6       周几     tm_wday     0～6
            7       第几天    tm_yday     1～366
            8       夏令时    tm_isdst    0，1，-1（表示夏令时）
            
```
#需要单独导入
import time

#时间模块的属性
#timezone: 当前时区和UTC时间相差的秒数，在没有夏令时的情况下的间隔,东八区的是 -28800
#altzone  获取当前时区与UTC时间相差的秒数，在有夏令时的情况下，
#daylight 测当前是否是夏令时时间状态, 0 表示是
print(time.daylight)
```
```
#得到时间戳
time.time()
```
    # localtime：得到当前时间色时间结构
```
# 可以通过点号操作符得到相应的属性元素的内容
t = time.localtime()
print(t.tm_hour)
```
    # asctime：返回元组的正常字符串之后的时间形式
        格式：time.asctime(时间元组)
        返回值：字符串
```
t = time.localtime()
tt = time.asctime(t)
print(tt)
```
    # ctime：获取字符串化的当前时间
```
t = time.ctime()
print(t)
```
    # mktime：使用时间元组获取对应的时间戳
        格式：time.mktime（时间元组）
        返回值：浮点数时间戳
```
lt = time.localtime()
ts = time.mktime(lt)
print(ts)
```
    # clock: 获取cpu时间， 3.0-3.3版本直接使用, 3.8将删除
    # sleep: 使程序进入睡眠，n秒后继续
```
for i in range(10):
    print(i)
    time.sleep(1)
```
    # strftime:将时间元组转化为自定义的字符串格式
```
'''
格式  含义  备注
%a  本地（locale）简化星期名称    
%A  本地完整星期名称    
%b  本地简化月份名称    
%B  本地完整月份名称    
%c  本地相应的日期和时间表示    
%d  一个月中的第几天（01 - 31）   
%H  一天中的第几个小时（24 小时制，00 - 23）   
%I  一天中的第几个小时（12 小时制，01 - 12）   
%j  一年中的第几天（001 - 366）  
%m  月份（01 - 12） 
%M  分钟数（00 - 59）    
%p  本地 am 或者 pm 的相应符    注1
%S  秒（01 - 61）  注2
%U  一年中的星期数（00 - 53 星期天是一个星期的开始）第一个星期天之前的所有天数都放在第 0 周   注3
%w  一个星期中的第几天（0 - 6，0 是星期天） 注3
%W  和 %U 基本相同，不同的是 %W 以星期一为一个星期的开始  
%x  本地相应日期  
%X  本地相应时间  
%y  去掉世纪的年份（00 - 99）    
%Y  完整的年份   
%z  用 +HHMM 或 -HHMM 表示距离格林威治的时区偏移（H 代表十进制的小时数，M 代表十进制的分钟数）      
%%  %号本身
'''
t = time.localtime()
ft = time.strftime("%Y年%m月%d日 %H:%M" , t)
print(ft)
```
### datetime
    datetinme提供日期和时间的运算和表示
    # datetime.date: 一个理想和的日期，提供year, month, day属性
```
dt = datetime.date(2020,2,8)
print(dt)
print(dt.day)
print(dt.year)
print(dt.month)
```
    # datetime.datetime: 提供日期跟时间的组合
```
from datetime import datetime
#常用类方法：
#today： 
#now
#utcnow
#fromtimestamp： 从时间戳中返回本地时间
dt = datetime(2018, 3, 26)
print(dt.today())
print(dt.now())

print(dt.fromtimestamp(time.time()))
```
    # datetime.timedelta: 提供一个时间差，时间长度
        表示一个时间间隔
```
from datetime import datetime, timedelta

t1 = datetime.now()
print( t1.strftime("%Y-%m-%d %H:%M:%S"))
#td表示以小时的时间长度
td = timedelta(hours=1)
#当前时间加上时间间隔后，把得到的一个小时后的时间格式化输出
print( (t1+td).strftime("%Y-%m-%d %H:%M:%S"))
```
### timeit  时间测量工具
    # 测量程序运行时间间隔实验
```
import timeit
#生成列表两种方法的比较
c = '''
sum = []
for i in range(1000):
    sum.append(i)
'''
 
#利用timeit调用代码，执行100000次，查看运行时间
t1= timeit.timeit(stmt="[i for i in range(1000)]", number=100000 )
#测量代码c执行100000次运行结果
t2 = timeit.timeit(stmt=c, number=100000)
print(t1)
print(t2)
```
    # timeit 可以执行一个函数，来测量一个函数的执行时间 
```
def doIt():
    num = 3
    for i in range(num):
        print("Repeat for {0}".format(i))
       
#执行函数，重复10次
t = timeit.timeit(stmt=doIt, number=10)
print(t)
```
```
s = '''
def doIt(num):
    for i in range(num):
        print("Repeat for {0}".format(i))

'''
#执行doIt(num)
#setup负责把环境变量准备好
#实际相当于给timeit创造了一个小环境
#在创作的小环境中， 代码执行的顺序大致是
'''
def doIt(num):
    .....
    
num = 3

doIt(num)
'''
t = timeit.timeit("doIt(num)", setup=s+"num=3", number=10)
print(t)
```
### os - 操作系统相关
    跟操作系统相关，主要是文件操作
    与系统相关的操作，主要包含在三个模块里
        os， 操作系统目录相关
        os.path, 系统路径相关操作
        shutil， 高级文件操作，目录树的操作，文件赋值，删除，移动
    路径：
        绝对路径： 总是从根目录上开始
        相对路径： 基本以当前环境为开始的一个相对的地方
#### os 模块
    # getcwd：获取当前的工作目录
        格式：os.getcwd()
        返回值：当前工作目录的字符串
        当前工作目录就是程序在进行文件相关操作，默认查找文件的目录
```
import os

mydir = os.getcwd()
print(mydir)
```
    # chdir：改变当前的工作目录
        格式：os.chdir（路径）
        返回值：无
```
os.chdir('/home')
mydir = os.getcwd()
print(mydir)
```
    # listdir：获取一个目录中所有子目录和文件的名称列表
        格式:os.listdir(路径)
        返回值：所有子目录和文件名称的列表
```
ld = os.listdir()
print(ld)
```
    # makedirs：递归创建文件夹
        格式：os.makedirs(递归路径)
        返回值：无
        递归路径：多个文件夹层层包含的路径就是递归路径 例如 a/b/c...
```
rst = os.makedirs("linsan")
print(rst)
```
    # system：运行系统shell命令
        格式：os.system(系统命令)
        返回值：打开一个shell或者终端界面
        一般推荐使用subprocess代替
```
rst = os.system("ls")
print(rst)

#在当前目录下创建一个linsan.txt 的文件
rst = os.system("touch linsan.txt")
print(rst)
```
    #getenv：获取指定的系统环境变量值
        相应的还有putenv
        格式：os.getenv('环境变量名')
        返回值：指定环境变量名对应的值
```
rst = os.getenv("PATH")
print(rst)
```
    # exit() 退出当前程序
        格式：exit()
        返回值:无
        
    # 值部分
        os.curdir: curretn dir,当前目录
        os.pardir: parent dir， 父亲目录
        os.sep: 当前系统的路径分隔符
            windows: "\"
            linux: "/"
        os.linesep: 当前系统的换行符号
            windows: "\r\n"
            unix,linux,macos: "\n"
        os.name： 当前系统名称
            windows： nt
            mac，unix，linux： posix
            
#### os.path
    # abspath() 将路径转化为绝对路径
        #  格式:os.path.abspath('路径')
        #  返回值：路径的绝对路径形式
```
#linux中
#. 点号，代表当前目录
#.. 双点，代表父目录
absp = op.abspath(".")
print(absp)
```
    # basename() 获取路径中的文件名部分
        格式:os.path.basename(路径)
        返回值：文件名字符串
```
bn = op.basename("/home/tlxy")
print(bn)
bn = op.basename("/home/tlxy")
print(bn)
```
    # join() 将多个路径拼合成一个路径
        格式：os.path.join(路径1，路径2....)
        返回值：组合之后的新路径字符串
```
bd = "/home/tlxy"
fn = "linsan.txt"

p = op.join(bd, fn)
print(p)
```
    # split() 将路径切割为文件夹部分和当前文件部分
        格式:os.path.split（路径）
        返回值：路径和文件名组成的元组
```
t = op.split("/home/tlxy/linsan.txt")
print(t)

d,p = op.split("/home/tlxy/linsan.txt")
print(d, p)
```
    # isdir（） 检测是否是目录
        格式：os.path.isdir(路径)
        返回值：布尔值
```
rst = op.isdir("/home/tlxy/linsan.txt")
```
    # exists() 检测文件或者目录是否存在
        格式：os.path.exists(路径)
        返回值:布尔值
```
e = op.exists("/home/tlxy/linsan")
```
#### shutil
    # copy() 复制文件
        格式：shutil.copy(来源路径，目标路径)
        返回值：返回目标路径
        拷贝的同时，可以给文件重命名
```
rst = shutil.copy("/home/tlxy/linsan.txt", "/home/tlxy/linsan.txt")
print(rst)
```
    # copy2() 复制文件，保留元数据（文件信息）
        格式：shutil.copy2(来源路径，目标路径)
        返回值：返回目标路径
        注意：copy和copy2的唯一区别在于copy2复制文件时尽量保留元数据
        
    # copyfile()将一个文件中的内容复制到另外一个文件当中
        格式：shutil.copyfile（'源路径','目标路径')
        返回值：无
```
rst = shutil.copyfile("linsan.txt", "linsan.linsan")
print(rst)
```
    # move() 移动文件/文件夹
        格式：shutil.move(源路径，目标路径)
        返回值：目标路径
```
rst  = shutil.move("/home/tlxy/linsan.txt", "/home/tlxy/linsan")
print(rst)
```
    # make_archive() 归档操作
        格式:shutil.make_archive('归档之后的目录和文件名','后缀','需要归档的文件夹')
        返回值：归档之后的地址
```
rst = shutil.make_archive("/home/tlxy/tuling", "zip", "/home/tlxy/linsan")
print(rst)
```
    # unpack_archive() 解包操作
        格式：shutil.unpack_archive('归档文件地址','解包之后的地址')
        返回值：解包之后的地址
        
#### zipfile
    # zipfile.ZipFile(file[, mode[, compression[, allowZip64]]])
        创建一个ZipFile对象，表示一个zip文件。
        参数:
            file：表示文件的路径或类文件对象(file-like object)
            mode：指定打开zip文件的模式，默认为’r’，表示读已经存在的zip文件，也可以为’w’或’a’，’w’表示新建一个zip文档或覆盖一个已经存在的zip文档，’a’表示将数据附加到一个现存的zip文档
            compression：表示在写zip文档时使用的压缩方法，它的值可以是zipfile. ZIP_STORED 或zipfile. ZIP_DEFLATED。
            如果要操作的zip文件大小超过2G，应该将allowZip64设置为True。
```
import zipfile
zf = zipfile.ZipFile("/home/tlxy/linsan.zip")
```
    # ZipFile.getinfo(name):
        获取zip文档内指定文件的信息。返回一个zipfile.ZipInfo对象，它包括文件的详细信息。
```
rst = zf.getinfo("linsan.txt")
print(rst)
```
    # ZipFile.namelist()
        获取zip文档内所有文件的名称列表。
```
nl = zf.namelist()
print(nl)
```
    # ZipFile.extractall([path[, members[, pwd]]])
        解压zip文档中的所有文件到当前目录。参数members的默认值为zip文档内的所有文件名称列表，也可以自己设置，选择要解压的文件名称。
```
rst = zf.extractall("/home/tlxy/linsan")
```
#### random
    随机数,所有的随机模块都是伪随机
    
    # random() 获取0-1之间的随机小数
        格式：random.random()
        返回值：随机0-1之间的小数
    # choice() 随机返回序列中的某个值
        格式：random.choice(序列)
        返回值：序列中的某个值
```
import random

l = [str(i)+"linsan" for i in range(10)]
print(l)
rst = random.choice(l)
print(rst)
```
    # shuffle() 随机打乱列表
        格式：random.shuffle(列表)
        返回值：打乱顺序之后的列表
```
l1 = [i for i in range(10)]
print(l1)

random.shuffle(l1)
print(l1)
```
    # randint(a,b): 返回一个a到b之间的随机整数，包含a和b
2020.2.9
## 函数式编程（FunctionalProgramming）
    基于lambda演算的一种编程方式
        程序中只有函数
        函数可以作为参数，同样可以作为返回值
    
### lambda表达式（匿名函数）
    一个表达式，函数体相对简单
    不是一个代码块，仅仅是一个表达式
    可以有参数，有多个参数也可以，用逗号隔开
    
     lambda表达式的用法
        1.以lambda开头
        2.紧跟一定的参数（如果有的话）
        3.参数后用冒号和表达式主题隔开
        4.只是一个表达式，所以，没有return
```
stm = lambda x: 100 * x
stm(10)
```
### 高阶函数
    把函数作为参数使用的函数，叫高阶函数
```
#函数名称就是一个变量
def funA():
    print("In funA")
    
funB = funA
funB()
```
    以上代码得出的结论：
        函数名称是变量
        funB 和 funA只是名称不一样而已
        既然函数名称是变量，则应该可以被当做参数传入另一个函数
```
#高阶函数举例
def funA(n):
    return n * 10

def funB(n):
    return funA(n) * 3

print(funB(6))
#写一个高阶函数
def funC(n, f):
    return f(n) * 3

print( funC(9, funA) )

#比较funC和funB, 显然funC的写法要优于funB
#例如：
def funD(n):
    return n*10

# 需求变更，需要把n放大三十倍，此时funB则无法实现
print(funC(7, funD))
```
### 系统高阶函数-map
    原意是映射，即把集合或者列表的元素，每一个元素都按照一定规则进行操作，生成一个新的列表或者集合
    map函数是系统提供的具有映射功能的函数，返回值是一个迭代对象
```
#map举例
#有一个列表，想对列表里的每一个元素乘以10， 并得到新的列表
l1 = [i for i in range(10)]
l2 = []
for i in l1:
    l2.append(i * 10)
print(l2)

#利用map实现
def mulTen(n):
    return n*10

l3 = map(mulTen, l1 )
#map类型是一个可迭代的结构，所以可以使用for遍历
for i in l3:
    print(i)
  
#以下列表生成式得到的结果为空， why？
l4 = [i for i in l3]
print(l4)
```
### reduce
    归并，缩减
    把一个可迭代对象最后归并成一个结果
    对于作为参数的函数要求： 必须有两个参数，必须有返回结果
    reduce([1,2,3,4,5]) == f( f(f(f(1,2),3), 4),5)
    reduce 需要导入functools包
```
from functools import reduce

#定义一个操作函数
#加入操作函数只是相加
def myAdd(x,y):
    return x + y
    
#对于列表[1,2,3,4,5,6]执行myAdd的reduce操作
rst = reduce( myAdd, [1,2,3,4,5,6] )
print(rst)
```
### filter 函数
    过滤函数： 对一组数据进行过滤，符合条件的数据会生成一个新的列表并返回
    跟map相比较：
        相同：都对列表的每一个元素逐一进行操作
        不同：
            map会生成一个跟原来数据想对应的新队列
            filter不一定，只要符合条件的才会进入新的数据集合
        filter函数怎么写：
            利用给定函数进行判断
            返回值一定是个布尔值
            调用格式： filter(f, data), f是过滤函数， data是数据
```
#filter举例

#需要定义过滤函数
def isEven(a):
    return a % 2 == 0
l = [3,4,5,6,9,78,87,54,56,65,22]
rst = filter(isEven,l)
#返回的filter内容是一个可迭代对象
print(rst)
 
```
### 高阶函数-排序
        把一个序列按照给定算法进行排序
        key: 在排序钱对每一个元素进行key函数运算，可以理解成按照key函数定义的逻辑进行排序
```
#排序案例
a = [2,3,5,6,9,88,9,45,55,1,22]
al = sorted(a,reverse=True)
print(al)
```
```
a = [-1,5,-9,-56,45,78,-78,23]
#abs是求绝对值的意思
al = sorted(a,key=abs,reverse=True)
print(al)
```
```
#sorted案例

astr = ['linsan', 'Linsan', 'linci', 'xusi', 'haha']
str1 = sorted(astr)
print(str1)

str2 = sorted(astr, key=str.lower)
print(str2)
```
### zip
    把两个可迭代内容生成一个可迭代的tuple元素类型组成的内容
```
# zip 案例
l1 = [ 1,2,3,4,5]
l2 = [11,22,33,44,55]

z = zip(l1, l2)
print(z)

for i in z:
    print(i)
```
### enumerate
    跟zip功能比较像
    对可迭代对象里的每一元素，配上一个索引，然后索引和内容构成tuple类型
```
#enumerate案例
l1 = [11,22,33,44,55]
em = enumerate(l1)

l2 = [i for i in em]
print(l2)

em = enumerate(l1, start=100)

l3 = [ i for i in em]
print(l3)
```
### collections模块
    namedtuple
        tuple类型
        是一个可命名的tuple
```
import collections

Point = collections.namedtuple("Point", ['x', 'y'])
p = Point(11, 22) 
print(p.x)
print(p[0])

Circle = collections.namedtuple("Circle", ['x', 'y', 'r'])
c = Circle(100, 150, 50)
print(c)
print(type(c))
```
    dequeue
        比较方便的解决了频繁删除插入带来的效率问题
```
from collections import deque

q = deque(['a', 'b', 'c'])
print(q)

q.append("d")
print(q)

q.appendleft('x')
print(q)
```
    defaultdict
        当直接读取dict不存在的属性时，直接返回默认值
```
from collections import defaultdict
#lambda表达式，直接返回字符串
func = lambda: "linsan"
d = defaultdict(func)

d["one"] = 1
d["two"] = 2

print(d['one'])
print(d['four'])
```
    Counter
        统计字符串个数
```
from collections import Counter

#需要括号里内容为可迭代
c = Counter("abcdefgabcdeabcdabcaba")
print(c)

s = ["linsan", "love", "love", "love", "love", "linci"]
c = Counter(s)

print(c)
```
### 返回函数
    函数可以返回具体的值，也可以返回一个函数作为结果
```
#函数作为返回值返回，被返回的函数在函数体内定义
def funA():
    def funB():
        print('in funB')
        return 'B'
    return funB
    
f = funA()
print(f)
f()
```
```
#args:参数列表
def funC(*args):
    def funD():
        rst = 0
        for n in args:
            rst += n
        return rst
    return funD
    
ff = funC(1,2,3,5,6,78,9)
ff()
```
### 闭包（closure）
    当一个函数在内部定义函数，并且内部的函数应用外部函数的参数或者局部变量，当内部函数被当做返回值的时候，相关参数和变量保存在返回的函数中，这种结果，叫闭包
```
#闭包常见坑
def count():
    # 定义列表，列表里存放的是定义的函数
    fs = []
    for i in range(1,4):
        def f():
            return i*i
        fs.append(f)
    return fs

f1,f2,f3 = count()
print(f1())
print(f2())
print(f3())
```
    出现的问题：
        造成上述状况的原因是,返回函数引用了变量i， i并非立即执行，而是等到三个函数都返回的时候才统一使用，此时i已经变成了3，最终调用的时候，都返回的是 3*3
        此问题描述成：返回闭包时，返回函数不能引用任何循环变量
        解决方案： 再创建一个函数，用该函数的参数绑定循环变量的当前值，无论该循环变量以后如何改变，已经绑定的函数参数值不再改变
```
#修改上述函数
def count():
    def f(j):
        def g():
            return j*j
        return g
    fs = []
    for i in range(1,4):
        fs.append(f(i))
    return fs

f1,f2,f3 = count()
print(f1())
print(f2())
print(f3())
```
### 装饰器（Decrator）
    在不改动函数代码的基础上无限制扩展函数功能的一种机制，本质上讲，装饰器是一个返回函数的高阶函数
    装饰器的使用： 使用@语法， 即在每次要扩展到函数定义前使用@+函数名
```
import time
 
def printTime(f):
    def wrapper(*args,**kwargs):
        print('Time:',time.ctime())
        return f(*args,**kwargs)
    return wrapper
#上面定义了装饰器，使用的时候需要用到@
@printTime
def hello():
    print('hello world')
    
hello()
#装饰器的好处是，一点定义，则可以装饰任意函数
#一旦被其装饰，则把装饰器的功能直接添加到定义函数的功能上
```
```
#手动执行装饰器
def hello():
    print('我是手动执行的')

hello = printTime(hello)
hello()
```
### 偏函数
    参数固定的函数，相当于一个由特定参数的函数体
    functools.partial的作用是，把一个函数某些函数固定，返回一个新函数
```
import functools

int16 = functools.partial(int,base=16)
int16('12345')
```
2020.2.10
## 调试
    调试流程：单元测试->集成测试->交测试部
    分类：
        静态调试
        动态调试
        
    pycharm调试
        run/debug模式 
        
    断点：程序的某一行，程序在debug模式下，遇到断点就会暂停
    
    单元测试
        推荐文档
            [官方测试文档集合](https://wiki.python.org/moin/PythonTestingToolsTaxonomy)
            [测试案例](http://blog.csdn.net/a542551042/article/details/46696635)
            [PyUnit](https://wiki.python.org/moin/PyUnit)
            [PyUnit详细讲解案例02](http://www.jb51.net/article/64119.htm)
            [测试案例](https://www.cnblogs.com/iamjqy/p/7155315.html) 
2020.2.11
## 文件
    长久保存信息的一种数据信息集合
    
    常用操作
        打开关闭（文件一旦打开，需要关闭操作）
        读写内容
        查找
### open函数
    open函数负责打开文件，带有很多参数
    第一个参数： 必须有，文件的路径和名称
    mode：表明文件用什么方式打开
        r:以只读方式打开
        w：写方式打开，会覆盖以前的内容
        x：创建方式打开，如文件已经存在，报错
        a：append方式，以追加的方式对文件内容进行写入
        b： binary方式，二进制方式写入
        t： 文本方式打开
        +： 可读写
```
#打开文件，用写的方式
#r表示后面字符串内容不需要转义
#f称之为文件句柄
f = open(r"test.txt", 'w')
#文件打开后必须关闭
f.close()

#此案例说明，以写方式打开文件，默认是如果没有文件，则创建
```
### with语句
    with语句使用的技术是一种称为上下文管理协议的技术(ContextManagementProtocal)
    自动判断文件的作用域，自动关闭不再使用的打开的文件句柄
```
#with案例

with open(r'test.txt', 'r') as f:
    # 按行读取内容
    strline = f.readline()
    # 此结构保证能够完整读取文件知道结束
    while strline:
        print(strline)
        strline = f.readline()
    #在本模块中不需要在使用close关闭文件f
```
```
#list能用打开的文件作为参数，把文件内每一行内容作为一个元素
with open(r'test.txt', 'r') as f:
    # 以打开的文件f作为参数，创建列表
    l = list(f)
    for line in l:
        print(line)
```
```
#read是按字符读取文件内容
#允许输入参数决定读取几个字符，如果没有制定，从当前位置读取到结尾
#否则，从当前位置读取指定个数字符
with open(r'test.txt', 'r') as f:
    strChar = f.read(1)
    print(strChar)
```
### seek(offset，from)
    移动文件的读取位置，也叫读取指针
    from的取值范围：
        0：从文件头开始偏移
        1：从文件当前位置开始偏移
        2：从文件末尾开始偏移
    移动的单位是字节(byte)
    一个汉子由若干个字节构成
    返回文件只针对 当前位置
```
# seek案例
# 打开文件后，从第5个字节出开始读取

# 打开读写指针在0处， 即文件的开头
with open(r'test.txt', 'r') as f:
    # seek移动单位是字节
    f.seek(6, 0)
    strChar = f.read()
    print(strChar)
```
### tell函数： 用来显示文件读写指针的当前位置
```
with open(r'test.txt', 'r') as f:
    strChar = f.read(3)
    pos = f.tell()
    while strChar:
        print(pos)
        print(strChar)
        strChar = f.read(3)
        pos = f.tell()
        
# tell的返回数字的单位是byte
# read是以字符为单位
```
### 文件的写操作-write
    write(str): 把字符串写入文件
    writelines(str): 把字符串按行写入文件
    区别：
        write函数参数只能是字符串
        writerlines参数可以是字符串，也可以是字符序列
```
#write案例
#a代表追加方式打开
with open(r'test.txt','a') as f:
    f.write('生活不仅有眼前的苟且，还有远方的苟且')
```
```
#writelines
#writelines表示写入很多行，参数可以是list格式
with open(r'test.txt', 'a') as f:
    f.writelines("生活不仅有眼前的苟且")
    f.writelines("还有远方的枸杞")
```
### pickle
    序列化（持久化，落地）：把程序运行中的信息保存再磁盘上
    反序列化：序列化的逆过程
    pickle： python提供的序列化模块
    pickle.dump:序列化
    pickle.load:反序列化
```
#序列化案例
import pickle

age = 19
with open(r'test.txt','wb') as f:
    pickle.dump(age,f)
    
#反序列化
with open(r'test.txt','rb') as f:
    age = pickle.load(f)
    print(age)
    
```
```
# 序列化案例
import pickle

a = [19, 'linsan', "i love linci", [185, 76]]
with open(r'test.txt', 'wb') as f:
    pickle.dump(a, f)
    
with open(r'test.txt', 'rb') as f:
    a  = pickle.load(f)
    print(a)
```
### shelve
    持久化工具
    类似字典，用kv对保存数据，存取方式跟字典也类似
```
#使用shelve创建文件并使用
import shelve

#shv相当于一个字典
shv = shelve.open(r'shv.db')

shv['one'] = 1
shv['two'] = 2
shv['three'] = 3
#shelve自动创建的不仅仅是一个shv.db文件，还包括其他格式文件
shv.close()

#shelve读取
shv = shelve.open(r'shv.db')
print(shv['one'])

shv.close
```
    shelve特性
    不支持多个应用并行写入
        为了解决这个问题，open的时候可以使用flag=r
    写回问题
        shelve不会等待持久化对象进行任何修改
        解决方法： 强制写回：writeback=True
```
# shelve 之只读打开
import shelve

shv = shelve.open(r'shv.db', flag='r')

try:
    k1 = shv['one']
    print(k1)
finally:
    shv.close()
```
```
# shelve忘记写回，需要使用强制写回
shv = shelve.open(r'shv.db', writeback=True)
try:
    k1 = shv['one']
    print(k1)
    # 此时，一旦shelve关闭，则内容还是存在于内存中，没有写回数据库
    k1["eins"] =100
finally:
    shv.close()
    
shv = shelve.open(r'shv.db')
try:
    k1 = shv['one']
    print(k1)
finally:
    shv.close()
```
```
#shelve 使用with管理上下文环境
with shelve.open(r'shv.db', writeback=True) as shv:
    k1 = shv['one']
    print(k1)
    k1["eins"] =1000

with shelve.open(r'shv.db') as shv:
    print(shv['one'])
```
2020.2.12
## log
- [参考资料](https://www.cnblogs.com/yyds/p/6901864.html)
- logging模块提供模块级别的函数记录日志
- 包括四大组件
### 日志相关概念
- 日志的级别（level）
    - DEBUG
    - INFO
    - NOTICE
    - WARNING
    - ERROR
    - CRITICAL
    - ALERT
    - EMERGENCY
- LOG的作用
    - 调试
    - 了解软件的运行情况
    - 分析定位问题
- 日志信息
    - time
    - 地点
    - level
    - 内容
- 成熟的第三方日志
    - log4j
    - log4php
    - logging
### Logging模块
- 日志级别
    - 级别可自定义
    - DEBUG
    - INFO
    - WARNING
    - ERROR
    - CRITICAL
- 初始化/写日志实例需要指定级别，只有当级别等于或高于指定级别才被记录
- 使用方式
    - 直接使用logging(封装了其他组件)
    - loging四大组件直接定制
### logging模块级别的日志
- 使用以下几个函数
     - logging.debug(msg, *args, **kwargs) 	创建一条严重级别为DEBUG的日志记录
     - logging.info(msg, *args, **kwargs) 	创建一条严重级别为INFO的日志记录
     - logging.warning(msg, *args, **kwargs) 	创建一条严重级别为WARNING的日志记录
     - logging.error(msg, *args, **kwargs) 	创建一条严重级别为ERROR的日志记录
     - logging.critical(msg, *args, **kwargs) 	创建一条严重级别为CRITICAL的日志记录
     - logging.log(level, *args, **kwargs) 	创建一条严重级别为level的日志记录
     - logging.basicConfig(**kwargs) 	对root logger进行一次性配置
- logging.basicConfig(**kwargs) 	对root logger进行一次性配置
    - 只在第一次调用的时候起作用
    - 不配置logger则使用默认值
        - 输出： sys.stderr
        - 级别： WARNING
        - 格式： level:log_name:content
```
#案例
import logging

LOG_FORMAT = "%(asctime)s=====%(levelname)s++++++%(message)s"

logging.basicConfig(filename="linsan.log", level=logging.DEBUG, format=LOG_FORMAT)

logging.debug("This is a debug log.")
logging.info("This is a info log.")
logging.warning("This is a warning log.")
logging.error("This is a error log.")
logging.critical("This is a critical log.")


# 另外一种写法
logging.log(logging.DEBUG, "This is a debug log.")
logging.log(logging.INFO, "This is a info log.")
logging.log(logging.WARNING, "This is a warning log.")
logging.log(logging.ERROR, "This is a error log.")
logging.log(logging.CRITICAL, "This is a critical log.")
```
- format参数
        asctime 	%(asctime)s 	日志事件发生的时间--人类可读时间，如：2003-07-08 16:49:45,896
        created 	%(created)f 	日志事件发生的时间--时间戳，就是当时调用time.time()函数返回的值
        relativeCreated 	%(relativeCreated)d 	日志事件发生的时间相对于logging模块加载时间的相对毫秒数（目前还不知道干嘛用的）
        msecs 	%(msecs)d 	日志事件发生事件的毫秒部分
        levelname 	%(levelname)s 	该日志记录的文字形式的日志级别（'DEBUG', 'INFO', 'WARNING', 'ERROR', 'CRITICAL'）
        levelno 	%(levelno)s 	该日志记录的数字形式的日志级别（10, 20, 30, 40, 50）
        name 	%(name)s 	所使用的日志器名称，默认是'root'，因为默认使用的是 rootLogger
        message 	%(message)s 	日志记录的文本内容，通过 msg % args计算得到的
        pathname 	%(pathname)s 	调用日志记录函数的源码文件的全路径
        filename 	%(filename)s 	pathname的文件名部分，包含文件后缀
        module 	%(module)s 	filename的名称部分，不包含后缀
        lineno 	%(lineno)d 	调用日志记录函数的源代码所在的行号
        funcName 	%(funcName)s 	调用日志记录函数的函数名
        process 	%(process)d 	进程ID
        processName 	%(processName)s 	进程名称，Python 3.1新增
        thread 	%(thread)d 	线程ID
        threadName 	%(thread)s 	线程名称 
### logging模块的处理流程
- 四大组件
    - 日志器(Logger): 产生日志的一个接口   
    - 处理器(Handler):把产生的日志发送到相应的目的地
    - 过滤器(Filter): 更精细的控制那些日志输出
    - 格式器(Formatter): 对输出信息进行格式化
- Logger
    - 产生一个日志
    - 操作
    

           Logger.setLevel() 	设置日志器将会处理的日志消息的最低严重级别
           Logger.addHandler() 和 Logger.removeHandler() 	为该logger对象添加 和 移除一个handler对象
           Logger.addFilter() 和 Logger.removeFilter() 	为该logger对象添加 和 移除一个filter对象
           Logger.debug: 产生一条debug级别的日志，同理，info，error，等
           Logger.exception(): 创建类似于Logger.error的日志消息
           Logger.log():获取一个明确的日志level参数类创建一个日志记录
    - 如何得到一个logger对象
        - 实例化
        - logging.getLogger()       
    
- Handler
    - 把log发送到制定位置
    - 方法
        - setLevel
        - setFormat
        - addFilter, removeFilter
    - 不需要直接使用，Handler是基类
    
            logging.StreamHandler 	将日志消息发送到输出到Stream，如std.out, std.err或任何file-like对象。
            logging.FileHandler 	将日志消息发送到磁盘文件，默认情况下文件大小会无限增长
            logging.handlers.RotatingFileHandler 	将日志消息发送到磁盘文件，并支持日志文件按大小切割
            logging.hanlders.TimedRotatingFileHandler 	将日志消息发送到磁盘文件，并支持日志文件按时间切割
            logging.handlers.HTTPHandler 	将日志消息以GET或POST的方式发送给一个HTTP服务器
            logging.handlers.SMTPHandler 	将日志消息发送给一个指定的email地址
            logging.NullHandler 	该Handler实例会忽略error messages，通常被想使用logging的library开发者使用来避免'No handlers could be found for logger XXX'信息的出现。
               
- Format类
    - 直接实例化
    - 可以继承Format添加特殊内容
    - 三个参数
        - fmt：指定消息格式化字符串，如果不指定该参数则默认使用message的原始值
        - datefmt：指定日期格式字符串，如果不指定该参数则默认使用"%Y-%m-%d %H:%M:%S"
        - style：Python 3.2新增的参数，可取值为 '%', '{'和 '$'，如果不指定该参数则默认使用'%'   
- Filter类
    - 可以被Handler和Logger使用
    - 控制传递过来的信息的具体内容
```
'''
1. 需求
    1）要求将所有级别的所有日志都写入磁盘文件中
    2）all.log文件中记录所有的日志信息，日志格式为：日期和时间 - 日志级别 - 日志信息
    3）error.log文件中单独记录error及以上级别的日志信息，日志格式为：日期和时间 - 日志级别 - 文件名[:行号] - 日志信息
    4）要求all.log在每天凌晨进行日志切割

2. 分析
    1）要记录所有级别的日志，因此日志器的有效level需要设置为最低级别--DEBUG;
    2）日志需要被发送到两个不同的目的地，因此需要为日志器设置两个handler；另外，两个目的地都是磁盘文件，因此这两个handler都是与FileHandler相关的；
    3）all.log要求按照时间进行日志切割，因此他需要用logging.handlers.TimedRotatingFileHandler; 而error.log没有要求日志切割，因此可以使用FileHandler;
    4）两个日志文件的格式不同，因此需要对这两个handler分别设置格式器；
'''
import logging
import logging.handlers
import datetime


# 定义logger
logger = logging.getLogger('mylogger')
logger.setLevel(logging.DEBUG)


#为两个不同的文件设置不同的handler
rf_handler = logging.handlers.TimedRotatingFileHandler('all.log', when='midnight', interval=1, backupCount=7, atTime=datetime.time(0, 0, 0, 0))
rf_handler.setFormatter(logging.Formatter("%(asctime)s - %(levelname)s - %(message)s"))



f_handler = logging.FileHandler('error.log')
f_handler.setLevel(logging.ERROR)
f_handler.setFormatter(logging.Formatter("%(asctime)s - %(levelname)s - %(filename)s[:%(lineno)d] - %(message)s"))

# 把相应的处理器组装到logger上
logger.addHandler(rf_handler)
logger.addHandler(f_handler)


logger.debug('debug message')
logger.info('info message')
logger.warning('warning message')
logger.error('error message')
logger.critical('critical message')
```
## 多线程
    1.进程：程序运行的一个状态，包含地址空间，内存，数据等。每个进程有自己完全独立的运行环境，多进程共享数据是一个问题
    2.线程：一个进程的独立运行片段，一个进程可以有多个线程；一个进程的多个线程共享数据和上下文运行环境；轻量化的进程
    
    3.全局解释器锁（GIL)
        Python代码的执行是由python虚拟机进行控制
        在主循环中只能有一个控制线程在执行
        https://www.cnblogs.com/jokerbj/p/7460260.html
        http://www.dabeaz.com/python/UnderstandingGIL.pdf
    4.threading包的使用
        1>.直接利用threading.Thread生成T和read实例
            t = threading.Thread(target=xxx, args=(xx,))
            t.start()   #启动多线程
            t.join()    #等待多线程执行完成
```
import time
import threading

def loop1(a):
    print('start loop 1 at :',time.ctime())
    print('我是参数{}'.format(a))
    time.sleep(4)
    print('end loop 1 at :',time.ctime())
    return None

def loop2(a, b):
    print('start loop 2 at :',time.ctime())
    print('我是参数{},和参数{}'.format(a, b))
    time.sleep(4)
    print('end loop 2 at :',time.ctime())
    return None

def main():
    print('starting at :',time.ctime())
    #生成threading.Thread实例
    t1 = threading.Thread(target=loop1, args=('linsan',))
    t1.start()
    t2 = threading.Thread(target=loop2, args=('linsan','linci'))
    t2.start()
    
    t1.join(
    t2.join())
    print('all done at :',time.ctime())
    
    return None

if __name__ == '__main__':
    main()
```
        守护线程daemon
            如果在程序中将子线程设置成守护线程，则子线程会在主线程结束的时候自动退出；一般认为，守护线程不重要或者不允许离开主线程独立运行；守护线程能否有效跟环境相关
```
import time
import threading

def func():
    print('start func')
    time.sleep(2)
    print('end func')
    return None
print('main thread')

t1 = threading.Thread(target=func, args=())
t1.setDaemon(True)
#t..daemon = True
t1.start()
time.sleep(1)
print('main thread end')
```
        线程常用属性
            threading.currentThread：返回当前线程变量
            threading.enumerate:返回一个包含正在运行的线程的list，正在运行的线程指的是线程启动后，结束前的状态
            threading.activeCount: 返回正在运行的线程数量，效果跟 len(threading.enumerate)相同
            thr.setName: 给线程设置名字
            thr.getName: 得到线程的名字
```
import time
import threading

def loop1():
    print('start loop 1 at :',time.ctime())
    time.sleep(4)
    print('end loop 1 at :',time.ctime())

def loop2():
    print('start loop 2 at :',time.ctime())
    time.sleep(2)
    print('end loop 2 at :',time.ctime())

def loop3():
    print('start loop 3 at :',time.ctime())
    time.sleep(5)
    print('end loop 3 at :',time.ctime())

def main():
    print('starting at:',time.ctime())
    t1 = threading.Thread(target=loop1, args=())
    t1.setName('TR1')
    t1.start()
    
    t2 = threading.Thread(target=loop2, args=())
    t2.setName('TR2')
    t2.start()
    
    t3 = threading.Thread(target=loop3, args=())
    t3.setName('TR3')
    t3.start()
    
    time.sleep(3)
    for thr in threading.enumerate():
        print('正在运行的线程名字是：{}'.format(thr.getName()))
    print('正在运行的子线程数量为：{}'.format(threading.activeCount()))
    print('all done at : ',time.ctime())

if __name__ == '__main__':
    main()
```
        2>.直接继承threading.Thread
            直接继承Thread
            重写run函数
            类实例可以直接运行
```
import time
import threading

class MyThread(threading.Thread):
    def __init__(self, arg):
        super(MyThread, self).__init__()
        self.arg = arg
    def run(self):
        time.sleep(2)
        print('the args for this class is {}'.format(self.arg))

for i in range(6):
    t = MyThread(i)
    t.start()
    t.join()
    
print('main thread is done!!!')
```
```
#高逼格写法
import threading
from time import sleep, ctime

loop = [4,2]

class ThreadFunc:
    def __init__(self, name):
        self.name = name

    def loop(self, nloop, nsec):
        '''
        :nloop: loop函数的名称
        :nsec: 系统休眠时间
        '''
        print('Start loop ', nloop, 'at ', ctime())
        sleep(nsec)
        print('Done loop ', nloop, ' at ', ctime())

def main():
    print("Starting at: ", ctime())

    # ThreadFunc("loop").loop 跟一下两个式子相等：
    # t = ThreadFunc("loop")
    # t.loop
    # 以下t1 和  t2的定义方式相等
    t = ThreadFunc("loop")
    t1 = threading.Thread( target = t.loop, args=("LOOP1", 4))
    # 下面这种写法更西方人，工业化一点
    t2 = threading.Thread( target = ThreadFunc('loop').loop, args=("LOOP2", 2))

    # 常见错误写法
    #t1 = threading.Thread(target=ThreadFunc('loop').loop(100,4))
    #t2 = threading.Thread(target=ThreadFunc('loop').loop(100,2))
    t1.start()
    t2.start()

    t1.join( )
    t2.join()


    print("ALL done at: ", ctime())


if __name__ == '__main__':
    main()
```
    5.共享变量
        共享变量：当多个线程同时访问一个变量的时候，会产生共享变量的问题
```
import threading

sum = 0
loopSum = 1000000
def myAdd():
    global sum,loopSum
    for i in range(1,loopSum):
        sum += 1
def myMinu():
    global sum,loopSum
    for i in range(1,loopSum):
        sum -= 1

if __name__ == '__main__':
    print('start....{}'.format(sum))
    t1 = threading.Thread(target=myAdd,args=())
    t2 = threading.Thread(target=myMinu,args=())
    
    t1.start()
    t2.start()
    
    t1.join()
    t2.join()
    print('done....{}'.format(sum))
```
        1>.锁（lock):是一个标志，表示一个线程占用一些资源
            使用方法
                上锁
                使用共享资源
                取消锁
```
import threading

sum = 0
loopSum = 1000000

lock = threading.Lock()

def myAdd():
    global sum,loopSum
    for i in range(1,loopSum):
        #上锁
        lock.acquire()
        sum += 1
        #释放
        lock.release()
def myMinu():
    global sum,loopSum
    for i in range(1,loopSum):
        lock.acquire()
        sum -= 1
        lock.release()
if __name__ == '__main__':
    print('start....{}'.format(sum))
    t1 = threading.Thread(target=myAdd,args=())
    t2 = threading.Thread(target=myMinu,args=())
    
    t1.start()
    t2.start()
    
    t1.join()
    t2.join()
    print('done....{}'.format(sum))
#锁谁： 哪个资源需要多个线程共享，锁哪个
#理解锁：锁不是锁住谁，而是一个令牌
```
        2>.线程安全问题：
            如果一个资源/变量，他对于多线程来讲，不用加锁也不会引起任何问题，则称为线程安全
            线程不安全变量类型： list, set, dict
            线程安全变量类型： queue
        3>.生产者消费者问题
            一个模型，可以用来搭建消息队列
            queue是一个用来存放变量的数据结构，特点是先进先出，内部元素排队，可以理解成一个特殊的list
```
import threading
import time
import queue

class Producer(threading.Thread):
    def run(self):
        global queue
        count = 0
        while True:
            # qsize返回queue内容长度
            if queue.qsize() < 1000:
                for i in range(100):
                    count = count +1
                    msg = '生成产品'+str(count)
                    # put是网queue中放入一个值
                    queue.put(msg)
                    print(msg)
            time.sleep(0.5)

class Consumer(threading.Thread):
    def run(self):
        global queue
        while True:
            if queue.qsize() > 100:
                for i in range(3):
                    # get是从queue中取出一个值
                    msg = self.name + '消费了 '+queue.get()
                    print(msg)
            time.sleep(1)

if __name__ == '__main__':
    queue = queue.Queue()

    for i in range(500):
        queue.put('初始产品'+str(i))
    for i in range(2):
        p = Producer()
        p.start()
    for i in range(5):
        c = Consumer()
        c.start()
```
        4>.死锁问题
        5>.锁的等待时间问题
        6>.semphore：允许一个资源最多由几个多线程同时使用
```
import threading
import time
#参数定义最多几个线程同时使用资源
semaphore = threading.Semaphore(3)

def func():
    if semaphore.acquire():
        for i in range(5):
            print(threading.currentThread().getName() + ' get semaphore')
        time.sleep(15)
        semaphore.release()
        print(threading.currentThread().getName() + ' release semaphore')

for i in range(8):
    t1 = threading.Thread(target=func)
    t1.start()
```
        7>.threading.Timer：Timer是利用多线程，在指定时间后启动一个功能
```
import threading
import time

def func():
    print("I am running.........")
    time.sleep(4)
    print("I am done......")

if __name__ == "__main__":
    t = threading.Timer(6, func)
    t.start()
    i = 0
    while True:
        print("{0}***************".format(i))
        time.sleep(3)
        i += 1
```
        8>.可重入锁
            一个锁，可以被一个线程多次申请
            主要解决递归调用的时候，需要申请锁的情况
```
import threading
import time

class MyThread(threading.Thread):
    def run(self):
        global num
        time.sleep(1)
        if mutex.acquire(1):
            num = num+1
            msg = self.name+' set num to '+str(num)
            print(msg)
            mutex.acquire()
            mutex.release()
            mutex.release()

num = 0
mutex = threading.RLock()

def testTh():
    for i in range(5):
        t = MyThread()
        t.start()

if __name__ == '__main__':
    testTh()
```
    6.线程替代方案
    1>.subprocess
        完全跳过线程，使用进程；是派生进程的主要替代方案
    2>.multiprocessing
        使用threadiing接口派生，使用子进程；允许为多核或者多cpu派生进程，接口跟threading非常相似
    3>.concurrent.futures
        新的异步执行模块；任务级别的操作
    
## 多进程
    1.进程间通讯（InterprocessCommunication，IPC）
    2.进程之间无任何共享状态
    3.进程的创建
        1>.直接生成Process实例对象
```
import multiprocessing
import time

def clock(interval):
    while True:
        print('the time is {}'.format(time.ctime()))
        time.sleep(interval)

if __name__ == '__main__':
    p = multiprocessing.Process(target=clock, args=(5,))
    p.start()
```
        2>.派生子类
```
import multiprocessing
import time

class ClockProcess(multiprocessing.Process):
    def __init__(self, interval):
        super().__init__()
        self.interval = interval
    def run(self):
        while True:
            print('the time is {}'.format(time.ctime()))
            time.sleep(self.interval)

if __name__ == '__main__':
    p = ClockProcess(5)
    p.start()
```
        3>.生产者消费者模型
            JoinableQueue
```
import multiprocessing
from time import ctime

def consumer(input_q):
    print ("Into consumer:", ctime())
    while True:
        item = input_q.get()
        if item is None:
            break
        print("pull", item, "out of q")
    print ("Out of consumer:", ctime())

def producer(sequence, output_q):
    for item in sequence:
        print ("Into procuder:", ctime())
        output_q.put(item)
        print ("Out of procuder:", ctime())

if __name__ == '__main__':
    q = multiprocessing.Queue()
    cons_p1 = multiprocessing.Process (target = consumer, args = (q,))
    cons_p1.start()

    cons_p2 = multiprocessing.Process (target = consumer, args = (q,))
    cons_p2.start()

    sequence = [1,2,3,4]
    producer(sequence, q)

    q.put(None)
    q.put(None)

    cons_p1.join()
    cons_p2.join()
```
## 迭代器
    可迭代（iterable）：直接作用于for循环的变量
    迭代器（iterator）：不但可以作用于for循环，还可以被next调用
```
#通过isinstance判断
#判断是否可迭代
from collections import Iterable
ll = [1,2,3,4,5]
print(isinstance(ll, Iterable))
#判断是否迭代器
from collections import Iterator
print(isinstance(ll, Iterator))
```
    iterable和iterator可以转换,通过iter函数
```
s = 'i love linsan'
print(isinstance(s, Iterable))
print(isinstance(s, Iterator))

s_iter = iter(s)
print(isinstance(s_iter, Iterable))
print(isinstance(s_iter, Iterator))
```
## 生成器
    1.generator: 一边循环一边计算下一个元素的机制/算法
    2.需要满足三个条件：
        每次调用都生产出for循环需要的下一个元素
        如果达到最后一个后，报出StopIteration异常
        可以被next函数调用
    3.如何生成一个生成器
        直接使用
```
L = [x*x for x in range(5)] # 放在中括号中是列表生成器
g = (x*x for x in range(5))#  放在小括号中就是生成器

print(type(L))
print(type(g))
```
        如果函数中包含yield，则这个函数就叫生成器
        next调用函数，遇到yield返回
```
#在函数odd中，yield负责返回
def odd():
    yield 1
    yield 2
    yield 3
#odd() 是调用生成器
g = odd()
one = next(g)
print(one)

two = next(g)
print(two)

three = next(g)
print(three)
```
```
# 斐波那契额数列的生成器写法
def fib(max):
    n, a, b = 0, 0, 1 
    while n < max:
        yield b
        a,b = b, a+b 
        n += 1
    #报出异常的返回值是return的返回值
    return 'Done'
g = fib(5)

for i in range(6):
    rst = next(g)
    print(rst)
    
ge = fib(10)
'''
生成器的典型用法是在for中使用
比较常用的典型生成器就是range
'''
#在for循环中使用生成器
for i in ge:
    print(i)
```
## 协程
    1.参考资料
    https://blog.csdn.net/andybegin/article/details/77884645
    http://python.jobbole.com/86481/
    http://python.jobbole.com/87310/
    https://segmentfault.com/a/1190000009781688
    
    2.定义：协程是为非抢占式多任务产生子程序的计算机程序组件，协程允许不同入口点在不同位置暂停或开始执行程序；从技术角度讲，协程就是一个你可以暂停执行的函数，或者干脆把协程理解成生成器
    
    3.协程的的实现
        yield返回
        send调用
    4.协程的四个状态
        inspect.getgeneratorstate(…) 函数确定，该函数会返回下述字符串中的一个：
        GEN_CREATED：等待开始执行
        GEN_RUNNING：解释器正在执行
        GEN_SUSPENED：在yield表达式处暂停
        GEN_CLOSED：执行结束
        next预激（prime)
```
def simple_coroutine(a):
    print('-> start')
    b = yield a
    print('-> recived', a, b)
    c = yield a + b
    print('-> recived', a, b, c)

sc = simple_coroutine(5)
#预激
aa = next(sc)
print(aa)
bb = sc.send(6) # 5, 6
print(bb)
cc = sc.send(7) # 5, 6, 7
print(cc)

执行结果
-> start
5
-> recived 5 6
11
-> recived 5 6 7
------------------------------------------------------------
StopIteration              Traceback (most recent call last)
<ipython-input-1-16dc5fdadbed> in <module>
     13 bb = sc.send(6) # 5, 6
     14 print(bb)
---> 15 cc = sc.send(7) # 5, 6, 7
     16 print(cc)
StopIteration: 
```
    5.协程终止
        协程中未处理的异常会向上冒泡，传给 next 函数或 send 方法的调用方（即触发协程的对象）
        终止协程的一种方式：发送某个哨符值，让协程退出。内置的 None 和Ellipsis 等常量经常用作哨符值
    6.yield from
        调用协程为了得到返回值，协程必须正常终止
        生成器正常终止会发出StopIteration异常，异常对象的vlaue属性保存返回值
        yield from从内部捕获StopIteration异常
    7.委派生成器
        包含yield from表达式的生成器函数
        委派生成器再yield from表达式处暂停，调用方可以直接把数据发给子生成器
        子生成器再把产出的值发给调用方
        子生成器再最后，解释器会抛出StopIteration，并且把返回值附加到异常对象上
```
#委派生成器案例
from collections import namedtuple
'''
解释：
1. 外层 for 循环每次迭代会新建一个 grouper 实例，赋值给 coroutine 变量； grouper 是委派生成器。
2. 调用 next(coroutine)，预激委派生成器 grouper，此时进入 while True 循环，调用子生成器 averager 后，在 yield from 表达式处暂停。
3. 内层 for 循环调用 coroutine.send(value)，直接把值传给子生成器 averager。同时，当前的 grouper 实例（coroutine）在 yield from 表达式处暂停。
4. 内层循环结束后， grouper 实例依旧在 yield from 表达式处暂停，因此， grouper函数定义体中为 results[key] 赋值的语句还没有执行。
5. coroutine.send(None) 终止 averager 子生成器，子生成器抛出 StopIteration 异常并将返回的数据包含在异常对象的value中，yield from 可以直接抓取 StopItration 异常并将异常对象的 value 赋值给 results[key]
'''
ResClass = namedtuple('Res', 'count average')
#子生成器
def averager():
    total = 0.0
    count = 0
    average = None

    while True:
        term = yield
        # None是哨兵值
        if term is None:
            break
        total += term
        count += 1
        average = total / count
    return ResClass(count, average)
#委派生成器
def grouper(storages, key):
    while True:
        # 获取averager()返回的值
        storages[key] = yield from averager()

#客户端代码
def client():
    process_data = {
        'boys_2': [39.0, 40.8, 43.2, 40.8, 43.1, 38.6, 41.4, 40.6, 36.3],
        'boys_1': [1.38, 1.5, 1.32, 1.25, 1.37, 1.48, 1.25, 1.49, 1.46]
    }
    storages = {}
    for k, v in process_data.items():
        #获得协程
        coroutine = grouper(storages, k)
        #预激协程
        next(coroutine)
        #发送数据到协程
        for dt in v:
            coroutine.send(dt)
        #终止协程
        coroutine.send(None)
    print(storages)

client()
```
    8.asynsio
        3.4开始引入的标准库,内置了对异步io的支持；asyncio本身是一个消息循环
        步骤
            创建消息循环
            把协程导入
            关闭
```
import asyncio

@asyncio.coroutine
def hello():
    print("Hello world!")
    # 异步调用asyncio.sleep(1):
    print("Start......")
    r = yield from asyncio.sleep(3)
    print("Done....")
    print("Hello again!")

# 获取EventLoop:
loop = asyncio.get_event_loop()
# 执行coroutine
loop.run_until_complete(hello())
loop.close()
```
    9.async and await
        为了更好的表示异步io
        python3.5 开始引入
        让coroutine代码更简洁
        使用上,可以简单进行替换
            可以把 @asyncio.coroutine 替换成async
            yield from 替换成await
```
import threading
import asyncio

#@asyncio.coroutine
async  def hello():
    print('Hello world! (%s)' % threading.currentThread())
    print('Start..... (%s)' % threading.currentThread())
    await asyncio.sleep(10)
    print('Done..... (%s)' % threading.currentThread())
    print('Hello again! (%s)' % threading.currentThread())

loop = asyncio.get_event_loop()
tasks = [hello(), hello()]
loop.run_until_complete(asyncio.wait(tasks))
loop.close()
```
    10.aiohttp
        asyncio实现单线程并发IO,在客户端用处不大
        在服务器端可以asyncio+coroutine配合,因为http是io操作
        asyncio实现了TCP,UIDP,SSL等协议
        aiohttp是给予asyncio实现的HTTP框架
        pip install aiohttp
```
#aiohttp案例

import asyncio
from aiohttp import web

async def index(request):
    await asyncio.sleep(0.5)
    return web.Response(body=b'<h1>Index</h1>')

async def hello(request):
    await asyncio.sleep(0.5)
    text = '<h1>helllo, %s!</h1>' % request.match_info['name']
    return web.Response(body=text.encode('utf-8'))

async def init(loop):
    app = web.Application(loop=loop)
    app.router.add_route('GET','/',index)
    app.router.add_route('GET','/hello/{name}',hello)
    srv = await loop.create_server(app.make_handler(), '127.0.0.1', 8000)
    print('server started at http://127.0.0.1:8000...')
    return srv

loop =asyncio.get_event_loop()
loop.run_until_complete(init(loop))
loop.run_forever()
```
    11.concurrent.futures
        类似其他语言的线程池的概念
        此模块利用multiprocessiong实现真正的平行计算
        核心原理是：concurrent.futures会以子进程的形式，平行的运行多个python解释器，从而令python程序可以利用多核CPU来提升执行速度
        由于子进程与主解释器相分离，所以他们的全局解释器锁也是相互独立的。每个子进程都能够完整的使用一个CPU内核
        
        concurrent.futures.Executor 
            ThreadPoolExecutor
            ProcessPoolExecutor
        submit(fn, args, kwargs)
            fn:异步执行的函数
            args,kwargs:参数
```
from concurrent.futures import ThreadPoolExecutor
import time
def return_future(msg):
    time.sleep(3)
    return msg

# 创建一个线程池
pool = ThreadPoolExecutor(max_workers=2)

# 往线程池加入2个task
f1 = pool.submit(return_future, 'hello')
f2 = pool.submit(return_future, 'world')

print(f1.done())
time.sleep(3)
print(f2.done())

print(f1.result())
print(f2.result())
```
```
# 官方死锁案例
from concurrent.futures import ThreadPoolExecutor
import time
def wait_on_b():
    time.sleep(5)
    print(b.result())  #b不会完成，他一直在等待a的return结果
    return 5

def wait_on_a():
    time.sleep(5)
    print(a.result())  #同理a也不会完成，他也是在等待b的结果
    return 6

executor = ThreadPoolExecutor(max_workers=2)
a = executor.submit(wait_on_b)
b = executor.submit(wait_on_a)
```
    concurrent中map函数
        map(fn, \*iterables, timeout=None)
        - 跟map函数类似
        - 函数需要异步执行
        - timeout: 超时时间
        - submit和map根据需要选一个即可
```
import time,re
import os,datetime
from concurrent import futures

data = ['1','2']

def wait_on(argument):
    print(argument)
    time.sleep(2)
    return "ok"

ex = futures.ThreadPoolExecutor(max_workers=2)
for i in ex.map(wait_on,data):
    print(i)
```
        Future
        - 未来需要完成的任务
        - future 实例由Excutor.submit创建
```
from concurrent.futures import ThreadPoolExecutor as Pool
from concurrent.futures import as_completed
import requests

URLS = ['http://qq.com', 'http://sina.com', 'http://www.baidu.com', ]


def task(url, timeout=10):
    return requests.get(url, timeout=timeout)


with Pool(max_workers=3) as executor:
    future_tasks = [executor.submit(task, url) for url in URLS]

    for f in future_tasks:
        if f.running():
            print('%s is running' % str(f))

    for f in as_completed(future_tasks):
        try:
            ret = f.done()
            if ret:
                f_ret = f.result()
                print('%s, done, result: %s, %s' % (str(f), f_ret.url, len(f_ret.content)))
        except Exception as e:
            f.cancel()
            print(str(e))
```
## XML
- 参考资料
    - https://docs.python.org/3/library/xml.etree.elementtree.html
    - http://www.runoob.com/python/python-xml.html
    - https://www.w3school.com.cn/xml/index.asp
    - https://blog.csdn.net/seetheworld518/article/details/49535285
### XML读取
    XML读取分两个主要技术,SAX， DOM
    1.SAX（Simple API for XML):
        基于事件驱动的API
        利用SAX解析文档设计到解析器和事件处理两部分
        特点:
            快
            流式读取
    2.DOM：是W3C规定的XML编程接口
        一个XML文件在缓存中以树形结构保存，读取
        用途
            定位浏览XML任何一个节点信息
            添加删除相应内容
        minidom
            minidom.parse(filename):加载读取的xml文件, filename也可以是xml代码
            doc.documentElement:获取xml文档对象，一个xml文件只有一个对于的文档对象
            node.getAttribute(attr_name):获取xml节点的属性值
            node.getElementByTagName(tage_name)：得到一个节点对象集合
            node.childNodes:得到所有孩子节点
            node.childNodes[index].nodeValue:获取单个节点值
            node.firstNode:得到第一个节点，等价于node.childNodes[0]
            node.attributes[tage_name]
```
#student.xml
<?xml version="1.0" encoding="utf-8" ?>
<School>
    <Teacher desc="PythonTeacher" score="good">
        <Name>Linxi</Name>
        <Age_1 Detail="Age for year 2010">18</Age_1>
        <Mobile>13260446055</Mobile>
    </Teacher>
    <Student>
        <Name Other="ta是班长">ZhangSan</Name>
        <Age Detail="The yongest boy in class">14</Age>
    </Student>
    <Student>
        <Name>LiSi</Name>
        <Age>19</Age>
        <Mobile>15578875040</Mobile>
    </Student>
</School>
```
```
import xml.dom.minidom
#负责解析xml文件
from xml.dom.minidom import parse

#使用minidom打开xml文件
DOMTree = xml.dom.minidom.parse("student.xml")
#得到文档对象
doc = DOMTree.documentElement

#显示子元素
for ele in doc.childNodes:
    if ele.nodeName == "Teacher":
        print("-------Node:{0}-----".format(ele.nodeName))
        childs = ele.childNodes
        for child in childs:
            if child.nodeName == "Name":
                #data是文本节点的一个属性，表示他的值
                print("Name: {0}".format(child.childNodes[0].data))
            if child.nodeName == "Mobile":
                #data是文本节点的一个属性，表示他的值
                print("Mobile: {0}".format(child.childNodes[0].data))
            if child.nodeName == "Age":
                #data是文本节点的一个属性，表示他的值
                print("Age: {0}".format(child.childNodes[0].data))
                if child.hasAttribute("detail"):
                    print("Age-detail: {0}".format(child.getAttribute("detail")))
```
    3.etree：以树形结构来表示xml
        root.getiterator:得到相应的可迭代的node集合
        root.iter
        find(node_name):查找指定node_name的节点,返回一个node
        root.findall(node_name):返回多个node_name的节点
        node.tag: node对应的tagename
        node.text:node的文本值
        node.attrib： 是node的属性的字典类型的内容
```
import xml.etree.ElementTree

root = xml.etree.ElementTree.parse("student.xml")
print("利用getiterator访问：")
nodes = root.getiterator()
for node in nodes:
    print("{0}--{1}".format(node.tag, node.text))

ele_teacher = root.find("Teacher")
print(type(ele_teacher))
print("{0}--{1}".format(ele_teacher.tag, ele_teacher.text))

ele_stus = root.findall("Student")
print(type(ele_stus))
for ele in ele_stus:
    print("{0}--{1}".format(ele.tag, ele.text))
    for sub in ele.getiterator():
        if sub.tag =="Name":
            if "Other" in sub.attrib.keys():
                print(sub.attrib['Other'])
```
### XML文件写入
    1.更改
        ele.set：修改属性
        ele.append：添加子元素
        ele.remove：删除元素
```
import xml.etree.ElementTree as et

tree = et.parse(r'to_edit.xml')
root = tree.getroot()
for e in root.iter('Name'):
    print(e.text)

for stu in root.iter('Student'):
    name = stu.find('Name')
    if name != None:
        name.set( 'test', name.text * 2)

stu = root.find('Student')

#生成一个新的 元素
e = et.Element('ADDer')
e.attrib = {'a':'b'}
e.text = '我加的'
stu.append(e)

#一定要把修改后的内容写回文件，否则修改无效
tree.write('to_edit.xml')
```
    2.生成创建
```
#SubElement

import xml.etree.ElementTree as et

stu = et.Element("Student1")
name = et.SubElement(stu, 'Name')
name.attrib = {'lang','en'}
name.text = 'maozedong'

age = et.SubElement(stu, 'Age')
age.text = 18

et.dump(stu)
```
```
#minidom 写入
import xml.dom.minidom

#在内存中创建一个空的文档
doc = xml.dom.minidom.Document()
#创建一个根节点Managers对象
root = doc.createElement('Managers')
#设置根节点的属性
root.setAttribute('company', 'xx科技')
root.setAttribute('address', '科技软件园')
#将根节点添加到文档对象中
doc.appendChild(root)

managerList = [{'name' : 'joy',  'age' : 27, 'sex' : '女'},
               {'name' : 'tom', 'age' : 30, 'sex' : '男'},
               {'name' : 'ruby', 'age' : 29, 'sex' : '女'}
]

for i in managerList :
    nodeManager = doc.createElement('Manager')
    nodeName = doc.createElement('name')
    #给叶子节点name设置一个文本节点，用于显示文本内容
    nodeName.appendChild(doc.createTextNode(str(i['name'])))

    nodeAge = doc.createElement("age")
    nodeAge.appendChild(doc.createTextNode(str(i["age"])))

    nodeSex = doc.createElement("sex")
    nodeSex.appendChild(doc.createTextNode(str(i["sex"])))

    #将各叶子节点添加到父节点Manager中，
    #最后将Manager添加到根节点Managers中
    nodeManager.appendChild(nodeName)
    nodeManager.appendChild(nodeAge)
    nodeManager.appendChild(nodeSex)
    root.appendChild(nodeManager)
#开始写xml文档
fp = open('Manager.xml', 'w')
doc.writexml(fp, indent='\t', addindent='\t', newl='\n', encoding="utf-8")
```
```
#etree创建
import xml.etree.ElementTree as et

#在内存中创建一个空的文档
etree = et.ElementTree()
e = et.Element('Student')
etree._setroot(e)
e_name = et.SubElement(e, 'Name')
e_name.text = "hahahah"
etree.write('xxx.xml')
```
## JSON
    1.在线工具
        https://www.sojson.com/
        http://www.w3school.com.cn/json/
        http://www.runoob.com/json/json-tutorial.html
    2.JSON(JavaScriptObjectNotation)：轻量级的数据交换格式，基于ECMAScript
        json格式是一个键值对形式的数据集    
            key: 字符串
            value:字符串，数字，列表，json
            json使用大括号包裹，键值对直接用都好隔开
            student={
                "name": "wangdapeng",
                "age": 18,
                "mobile":"13260446055"
                }
    3.json和python格式的对应
        字符串：字符串
        数字：数字
        队列：list
        对象：dict
        布尔值：布尔值
    4.python for json：json包
        json和python对象的转换
            json.dumps():对数据编码，把python格式表示成json格式
            json.loads(): 对数据解码，把json格式转换成python格式
        python读取json文件
            son.dump(): 把内容写入文件
            json.load(): 把json文件内容读入python
```
import json

# 此时student是一个dict格式内容，不是json
student={
    "name": "linxi",
    "age": 18,
    "mobile":"15578875040"
}

print(type(student))

stu_json = json.dumps(student)
print(type(stu_json))
print("JSON对象:{0}".format(stu_json))

stu_dict = json.loads(stu_json)
print(type(stu_dict))
print(stu_dict)
```
```
#读取文件
import json

data = {"name":"hahah", "age":12}

with open("t.json", 'w') as f:
    json.dump(data, f)

with open("t.json", 'r') as f:
    d = json.load( f)
    print(d)
```
## 正则表达式(RegularExpression, re)
    是一个计算机科学的概念；用于使用单个字符串来描述，匹配符合某个规则的字符；常常用来检索，替换某些模式的文本
    
正则的写法
>- .(点号):表示任意一个字符，除了\n, 比如查找所有的一个字符 \.
- []: 匹配中括号中列举的任意字符，比如[L,Y,0] , LLY, Y0, LIU
- \d: 任意一个数字
- \D:除了数字都可以
- \s:表示空格，tab键
- \S:除了空白符号
- \w: 单词字符， 就是a-z, A-Z, 0-9, _
- \W: 除了
- *： 表示前面内容重复零次或者多次， \w*
- +: 表示前面内容至少出现一次
- ？： 前面才出现的内容零次或者一次
- {m,n}:允许前面内容出现最少m次，最多n次
- ^:匹配字符串的开始
- $:匹配字符串的结尾
- \b:匹配单词的边界
- ():对正则表达式内容进行分组， 从第一个括号开始，编号逐渐增大

        验证一个数字： ^\d$
        必须有一个数字，最少一位：^\d+$
        只能出现数字，且位数为5-10位： ^\d{5,10}$
        注册者输入年龄，要求16岁以上，99岁以下： ^[16-99]$
        只能输入英文字符和数字： ^[A-Za-z0-9]$
        验证qq号码： [0-9]{5,12}
>- \A: 只匹配字符串开头， \Aabcd, 则abcd
- \Z: 仅匹配字符串末尾， abcd\Z, abcd
- |: 左右任意一个
- (?P<name>...): 分组，除了原来的编号再制定一个别名， (?P<id>12345){2}， 1234512345
- (?P=name): 引用分组，

## re
    1.使用大致步骤
    1>使用compile将表示正则的字符串编译为一个pattern对象
    2>通过pattern对象提供的一系列方法对文本进行查找匹配，获得匹配结果，一个match对象
    3>使用match对象提供的属性和方法获得信息，根据需要进行操作
    2.re常用函数
        group()：获得一个或者多个分组匹配的字符串，当要获得整个匹配的字符串的字串时，直接使用group或者group(0)
        start()：获得分组匹配的子串在整个字符串中的起始位置，参数默认为0
        end()：获得扽组匹配的子串字整个字符串中的结束位置，默认为0
        span()：返回的结构(start(group),end(group))
    3.查找  
        search(str[,pos[,endpos]])：在字符串中查找匹配，pos和endpos表示起始位置
        findall：查找所有
        finditer：查找，返回一个iter结果
    4.替换
        sub(rep1,str[,count])
    5.匹配中文
        大部分中文内容表示范围[u4e00-u9fa5],不包含全角标点
    6.贪婪和非贪婪
        贪婪：尽可能多的匹配，(*)表示贪婪匹配
        分贪婪：找到符合条件的最小内容即可，(?)表示非贪婪
        正则默认使用贪婪匹配
## XPath
- 在XML文件中查找信息的一套规则/语言，根据XML的元素或者属性进行遍历
- http://www.w3school.com.cn/xpath/index.asp

## 网络编程
- 网络模型：
    - 七层模型
        - 物理层
        - 数据链路层
        - 网络层
        - 传输层
        - 会话层
        - 表示层
        - 应用层
    - 四层模型-实际应用
        - 链路层
        - 网络
        - 传输层
        - 应用层
- 每一层都有相应的协议负责交换信息或者协同工作
- TCP/IP 协议族
- IP地址：负责在网络上唯一定位一个机器
    - IP地址分ABCDE类
    - 是由四个数字段组成，每个数字段的取值是0-255
    - 192.168.xxx.xxx:局域网ip
    - 127.0.0.1：本机
    - IPv4, IPv6
- 端口
    - 范围： 0-65535
        - 知名端口：0-1023
        - 非知名端口：1024-

## TCP/UDP协议
    1.UDP：非安全的不面向链接的传输
        安全性差；大小限制64kb；没有顺序；速度快
    2.TCP：基于链接的通信
    3.SOCKET编程
        socket（套接字）:是一个网络通信的端点，能实现不同主机的进程通信，网络大多基于Socket通信
        通过IP+端口定位对方并发送消息的通信机制
        分为UDP和TCP
        客户端Client： 发起访问的一方
        服务器端Server：接受访问的一方
    4.UDP 编程
        Server端流程
            1. 建立socket，socket是负责具体通信的一个实例
            2. 绑定，为创建的socket指派固定的端口和ip地址
            3. 接受对方发送内容
            4. 给对方发送反馈，此步骤为非必须步骤
        Client端流程
            1. 建立通信的socket
            2. 发送内容到指定服务器
            3. 接受服务器给定的反馈内容
```
#服务器端
import socket

def serverFunc():
    #建立socket
    #socket.AF_INET：使用ipv4协议族
    #socket.SOCKET_DGRAM：使用udp通信
    sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

    #绑定IP和port
    #地址是一个tuple类型，(ip, port)
    addr = ('127.0.0.1', 8000)
    sock.bind(addr)

    #接收对方消息
    #等待方式为死等，没有其他可能性
    #recvfrom接受的返回值是一个元组，前一项表示数据，后一项表示地址
    #参数的含义是缓冲区大小
    data, addr = sock.recvfrom(500)

    text = data.decode()
    print(text)

    #给对方返回的消息
    rsp = 'Ich hab keine Hunge'
    #发送的数据需要编码成bytes格式
    #默认是utf8
    data = rsp.encode()
    sock.sendto(data, addr)


if __name__ == "__main__":
    print('start')
    serverFunc()
    print('end')
    
#客户端
import socket

def clientFunc():
    sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    text = 'i love linsan'
    #发送的数据必须是bytes格式
    data = text.encode()
    #发送
    sock.sendto(data, ('127.0.0.1', 8000))
    data, addr = sock.recvfrom(200)
    data = data.decode()
    print(data)


if __name__ == "__main__":
    clientFunc()
```
```
#服务器程序要求永久运行，一般用死循环处理
#改造的服务器版本
import socket
import time

def serverFunc():
    #建立socket
    #socket.AF_INET：使用ipv4协议族
    #socket.SOCKET_DGRAM：使用udp通信
    sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

    #绑定IP和port
    #地址是一个tuple类型，(ip, port)
    addr = ('127.0.0.1', 8000)
    sock.bind(addr)

    #接收对方消息
    #等待方式为死等，没有其他可能性
    #recvfrom接受的返回值是一个元组，前一项表示数据，后一项表示地址
    #参数的含义是缓冲区大小
    data, addr = sock.recvfrom(500)

    text = data.decode()
    print(text)

    #给对方返回的消息
    rsp = 'Ich hab keine Hunge'
    #发送的数据需要编码成bytes格式
    #默认是utf8
    data = rsp.encode()
    sock.sendto(data, addr)

if __name__ == "__main__":
    while 1:
        try:
            serverFunc()
        except Exception as e:
            print(e)
        time.sleep(1)
```
    4.TCP编程
        面向链接的传输，即每次传输之前需要先建立一个链接
        Server端的编写流程
             1. 建立socket负责具体通信，这个socket其实只负责接受对方的请求，真正通信的是链接后从新建立的socket
             2. 绑定端口和地址
             3. 监听接入的访问socket
             4. 接受访问的socket，可以理解接受访问即建立了一个通讯的链接通路
             5. 接受对方的发送内容，利用接收到的socket接收内容
             6. 如果有必要，给对方发送反馈信息
             7. 关闭链接通路
        Client端流程
              1. 建立通信socket
              2. 链接对方，请求跟对方建立通路
              3. 发送内容到对方服务器
              4. 接受对方的反馈
              5. 关闭链接通路
```
#服务端
import socket

def  tcp_srv():
    #建立socket负责具体通信，这个socket其实只负责接受对方的请求，真正通信的是链接后从新建立的socket
    #需要用到两个参数
    #AF_INET: 含义同udp一致
    #SOCK_STREAM: 表明是使用的tcp进行通信
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    #绑定端口和地址
    #此地址信息是一个元祖类型内容，元祖分两部分，第一部分为字符串，代表ip，第二部分为端口，是一个整数，推荐大于10000
    addr = ("127.0.0.1", 8998)
    sock.bind(addr)
    #监听接入的访问socket
    sock.listen()

    while True:
        #接受访问的socket，可以理解接受访问即建立了一个通讯的链接通路
        #accept返回的元祖第一个元素赋值给skt，第二个赋值给addr
        skt,addr = sock.accept()
        #接受对方的发送内容，利用接收到的socket接收内容
        #500代表接收使用的buffersize
        #msg = skt.receive(500)
        msg = skt.recv(500)
        #接受到的是bytes格式内容
        #想得到str格式的，需要进行解码
        msg = msg.decode()

        rst = "Received msg: {0} from {1}".format(msg, addr)
        print(rst)
        #如果有必要，给对方发送反馈信息
        skt.send(rst.encode())

        #关闭链接通路
        skt.close()

if __name__ == "__main__":
    print("Starting tcp server.......")
    tcp_srv()
    print("Ending tcp server.......")
    
#客户端
import socket

def tcp_clt():
    #建立通信socket
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    #链接对方，请求跟对方建立通路
    addr = ("127.0.0.1", 8998)
    sock.connect(addr)
    #发送内容到对方服务器
    msg = "I love linsan"
    sock.send(msg.encode())
    #接受对方的反馈
    rst =  sock.recv(500)
    print(rst.decode())
    #关闭链接通路
    sock.close()
    
if __name__ == "__main__":
    tcp_clt()
```
## FTP编程
- FTP(FileTransferProtocal)文件传输协议
- 用途： 定制一些特殊的上传下载文件的服务
- 用户分类： 登陆FTP服务器必须有一个账号
    - Real账户: 注册账户
    - Guest账户： 可以临时对某一类人的行为进行授权
    - Anonymous账户： 匿名账户，允许任何人
- FTP工作流程
    1. 客户端链接远程主机上的FTP服务器
    2. 客户端输入用户名和密码（或者“anonymous”和电子邮件地址）
    3. 客户端和服务器进行各种文件传输和信息查询操作
    4. 客户端从远程FTP服务器退出，结束传输   
    
- FTP文件表示
    - 分三段表示FTP服务器上的文件
    - HOST: 主机地址，类似于 ftp.mozilla.org, 以ftp开头
    - DIR：目录， 表示文件所在本地的路径，例如 pub/android/focus/1.1-RC1/ 
    - File： 文件名称， 例如 Klar-1.1-RC1.apk
    - 如果想完整精确表示ftp上某一个文件，需要上述三部分组合在一起
```
import ftplib # 关于FTP的操作都在这个包里边
import os
import socket

#三部分精确表示在ftp服务器上的某一个文件
#好多公开ftp服务器访问会出错或者没有反应
HOST = "ftp.acc.umu.se"
DIR = 'Public/EFLIB/'
FILE = 'README'

#客户端链接远程主机上的FTP服务器
try:
    f = ftplib.FTP()
    #通过设置调试级别可以方便调试
    f.set_debuglevel(2)
    #链接主机地址
    f.connect(HOST)
except Exception as e:
    print(e)
    exit()
print("***Connected to host {0}".format(HOST))


#客户端输入用户名和密码（或者“anonymous”和电子邮件地址）
try:
    #登录如果没有输入用户信息，则默认使用匿名登录
    f.login()
except Exception as e:
    print(e)
    exit()
print("***Logged in as 'anonymous'")


#客户端和服务器进行各种文件传输和信息查询操作
try:
    #更改当前目录到指定目录
    f.cwd(DIR)
except Exception as e:
    print(e)
    exit()
print("*** Changed dir to {0}".format(DIR))

try:
    #从FTP服务器上下载文件
    #第一个参数是ftp命令
    #第二个参数是回调函数
    #此函数的意思是，执行RETR命令，下载文件到本地后，运行回调函数
    f.retrbinary('RETR {0}'.format(FILE), open(FILE, 'wb').write)
except Exception as e:
    print(e)
    exit()

#客户端从远程FTP服务器退出，结束传输
f.quit()
```

## Mail编程
- 参考资料
    - [官网](https://docs.python.org/3/library/email.mime.html)
    
