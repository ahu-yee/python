# 0. 入门
 cmd powershell

``C:\>F:``

``F:\>cd .\code\``

``F:\code>ls``

```
F:\code>python
>>print('Hello,World.')
```

```
F:\code>python test.py
Hello,World.
```

```
print(120+120)
print('120+120')
print('120+120=',120+120)
```

```
Name=input('Please input your name\n' )
print('Hello,',Name)
```

F5 调试 断点

# 1. python 基础
- tab或者4个空格表示缩进
- 大小写敏感
## 1.1 数据类型和变量
**整数**
``0x``表示十六进制
``/``除法计算的结果是浮点数
```
>>>9/3
3.0
```
``//``地板除，两个整数的除法仍然是整数
```
>>>10//3
3
```
``%``余数运算
```
>>>10%3
1
```
**浮点数**
``1.2e-5``
**字符串**
``\``转义字符
``\n``换行
``\t``制表符
``\\``表示\
```
print('I\'m learning\nPython.')
print('\\\n\\')
```
``r''``表示``''``内部字符串默认不转义
```
print(r'\\\t\\\')
```
```
'''line1
...line2
...line3'''
```
**布尔值**
``True``
``False``
``and``
``or``
``not``
```
if age >= 18:
    print('adult')
else:
    print('teenager')
```
**空值**
``None``
**变量**
变量名必须是大小写英文、数字和_的组合，且不能用数字开头
动态语言
静态语言
```
x=10
x=x+2
```
```
a='ABC'
b=a
a='XYZ'
print(b)
```
**常量**
通常用全部大写的变量名表示常量

## 1.2 字符串和编码
``str`` ``bytes``
**ASCII编码**
**GB2312**
**Unicode**
**UTF-8**
```
>>> ord('A')
65
>>> ord('中')
20013
>>> chr(66)
'B'
```
```
>>>'\u4e2d\u6587'
'中文'
```
``'ABC'`` ``b'ABC'``
```
>>>'ABC'.encode('ascii')
b'ABC'
>>>'中文'.encode('utf-8')
b'\xe4\xb8\xad\xe6\x96\x87
>>>b'ABC'.decode('ascii')
'ABC'
>>>b'\xe4\xb8\xad\xe6\x96\x87.decode('utf-8')
'中文'
>>>b'\xe4\xb8\xad\xff'.decode('utf-8',error='ignore')
'中'
```
计算``str``包含多少字符,计算``bytes``包含多少字节
```
>>>len('ABC')
3
>>>len(b'ABC')
3
>>>len('中文'.encode('utf-8'))
6
```
应当始终坚持使用UTF-8编码对``str``和``bytes``进行转换
```
#!/usr/bin/env/ python3
# -*- codeing:utf-8 -*-
```
**格式化**
``%``格式化字符串
``%s``表示用字符串替换
``%d``表示用整数替换
``%f``表示用浮点数替换
``%x``表示用十六进制整数替换
``%%``表示%
格式化整数和浮点数还可以指定是否补0和整数与小数的位数
```
>>>'Hi,%s,you have $%d.'%('Mary',200000)
'Hi,Mary,you have $200000.'
>>>print('%2d-%02d'%(3,1))
 3-01
>>>print('%.2f'%3.1415926)
3.14
>>>'growth rate:%d %%' % 7
'growth rate:7 %'
```
``format()``

## 1.3 使用list和tuple
**list**
list是可变动的有序集合
``len()``获取list元素个数
索引是从0开始的
最后一个元素的索引是``len(classmaates)-1``
```
>>>classmates=['Bob','Mary','Leo']
>>>len(classmates)
3
>>>classmates[0]
'Bob'
>>>classmates[2]
'Leo'
```
取最后一个元素
```
>>>classmates[-1]
'Leo'
>>>classmates[-3]
'Bob'
```
往list中追加元素至末尾
```
>>>classmates.append('John')
classmates['Bob','Mary','Leo','John']
```
把元素插入指定位置
```
>>>classmates.inset(1,'Neo')
classmates['Bob','Neo','Leo','John']
```
删除list末尾元素
```
>>>classmates.pop()
'John'
>>>classmates
['Bob','Neo','Leo']
```
删除list指定元素``pop(i)``,其中i是索引位置
```
>>>classmates.pop(1)
'Neo'
>>>classmates
['Bob','Leo']
```
把某个元素替换成别的元素
```
>>>classmates[1]='Sarah'
>>>classmates
['Bob','Sarah']
```
list元素可以另一个list
```
>>>s=['aaa','bbb',['aba','cdc'],'ccc']
>>>s[2][1]
'cdc'
```
list没有元素，长度为0

**tuple**
元组，指向不变的有序集合，一旦初始化就不能修改
``append()`` ``inset()``都没有
但是可以``classmates[0]``来获取元素
```
>>>t=(2,3)
>>>t
(2,3)
>>>t=()
>>>t
()
>>>t=(1,)
>>>t
(1,)
```
"可变的"tuple
```
>>>t=('aaa','bbb',['ccc','ddd'])
>>>t[2][0]='eee'
>>>t[2][1]='fff'
>>>t
('aaa','bbb',['eee','fff'])
```

## 1.4 条件判断
```
age=20
if age < 6:
    print('kid')
elif age < 18:
    print('teenager')
else:
    print('adult')
```
简写，x是非零数值、非空字符串、非空list等，就判断为true，否则是false
```
if x:
    print('True')
```
```
x=[]
if len(x)==0:
    print('False')
else:
    print('True')
```
**input**
``input()``返回的数据类型是``str``，``str``不能直接和整数比较，先用``int()``函数将``str``转换成整数。``int()``发现一个字符串不是合法数字时会报错
```
s=input('brith:')
brith=int(s)
if birth < 2000:
    print('00前')
else:
    print('00后')
```

## 1.5 循环
**for...in循环**
```
>>>names=['Mary','Sarah','Bob']
>>>for name in names:
    print(name)
Mary
Sarah
Bob
```
```
sum=0
for x in [1,2,3,4]:
    sum=sum+1
print(sum)
```
``range()``生成整数序列
``range(5)``是从0开始小于5的整数序列
```
#1+2+3+...+100
sum=0
for x in range(101):
    sum=sum+x
print(sum)
```
```
L=['Bob','Lisa','Adam']
for name in L:
    print('Hello,%s!' % name)
```
**while循环**
计算100以内基数之和
```
sum=0
n=99
while n > 0:
    sum=sum+n
    n=n-2
print(sum)
```
**break**
提前退出循环
```
n=1
while n <= 100:
    if n > 10:
        break
    print(n)
    n=n+1
print('END')
```
**continue**
跳出当前的这次循环，直接开始下一次循环
```
#只打出1到10的基数
n=0
While n < 10:
    n=n+1
    if n % 2 == 0:
        continue
    print(n)
```
``break``和``continue``必须配合``if``使用
不要滥用``break``和``continue``
如果程序陷入死循环，可以用``ctrl+c``退出程序

## 1.6 使用dict和set
**dict**
使用key-value存储，无序的，具有极快查找速度
```
>>>d={'aaa':98,'bbb':80,'ccc':50}
>>>d['aaa']
98
```
将数据放入dict的方法,一个key对应一个value，多次对一个key放入value，后面的值会把前面的值冲掉
```
>>>d['ddd']=64
>>>d['ddd']
64
>>>d['aaa']=54
>>>d['aaa']
54
```
``in``或``get()``判断key是都存在
```
>>>'eee' in d
False
>>>d.get('fff')
#-1只是显示，并没有添加到dict
>>>d.get('fff',-1)
-1
```
删除一个key
```
>>>d.pop('aaa')
54
>>>d
{'bbb':80,'ccc':50,'ddd':64}
```
通过key计算位置的算法称为哈希算法（Hash）

**set**
一组key的集合，但不储存value，由于key不能重复，所以set中没有重复的key,无序的
```
>>>s=set([1,1,2,2,3,3])
>>>s
{1,2,3}
```
通过``add(key)``可以添加元素到set，重复添加不会有效果
``remove(key)``可以删除元素
set可以看成数学意义上的无序和无重复元素的集合
```
>>>s.add(4)
>>>s
{1,2,3,4}
>>>s.remove(4)
>>>s
{1,2,3}
>>>s1=set([1,2,3])
>>>s2=set([2,3,4])
#交集
>>>s1&s2
{2,3}
#并集
>>>s1|s2
{1,2,3,4}
```
dict和set的key必须是**不可变对象**
```
>>>a=['c','b','a']
>>>a.sort()
>>>a
['a','b','c']

>>>a='abc'
>>>a.replace('a','A')
'Abc'
>>>a
'abc'
```

    要理解dict的有关内容需要你理解哈希表（map）的相关基础知识，这个其实是《算法与数据结构》里面的内容。

    1.list和tuple其实是用链表顺序存储的，也就是前一个元素中存储了下一个元素的位置，这样只要找到第一个元素的位置就可以顺藤摸瓜找到所有元素的位置，所以list的名字其实就是个指针，指向list的第一个元素的位置。list的插入和删除等可以直接用链表的方式进行，比如我要在第1个元素和第2个元素中间插入一个元素，那么直接在链表的最后面（我们假设这个list只有两个元素，那么也就是在第3个元素的位置上）插入这个元素，然后把第一个元素指针指向这个元素（第3个位置），然后再把新插入的元素的指针指向原来的第2个元素，这样插入操作就完成了。读取这个list的时候，先用list的名字（就是个指针，指向第1个元素的位置）找到第一个元素，然后用第1一个元素的指针找到第2个元素（位置3），然后用第2个元素的指针找到第3个元素（位置2），以此类推。所以list的顺序和内存中的实际顺序其实不一定完全对应。这种存储方式不会浪费内存，但查找起来特别费时间，因为要按照链表一个一个找下去，如果你的list特别大的话，那么要等好久才会找到结果。

    2.dict则为了快速查找使用了一种特别的方法，哈希表。哈希表采用哈希函数从key计算得到一个数字（哈希函数有个特点：对于不同的key，有很大的概率得到的哈希值也不同），然后直接把value存储到这个数字所对应的地址上，比如key='ABC'，value=10，经过哈希函数得到key对应的哈希值为123，那么就申请一个有1000个地址（从0到999）的内存，然后把10存放在地址为123的地方。类似的，对于key='BCD'，value=20，得到key的哈希值为234，那么就把20存放在地址为234的地方。对于这样的表查找起来是非常方便的。只要给出key，计算得到哈希值，然后直接到对应的地址去找value就可以了。无论有几个元素，都可以直接找到value，无需遍历整个表。不过虽然dict查找速度快，但内存浪费严重，你看我们只存储了两个元素，都要申请一个长度为1000的内存。

    3.现在你知道为啥key要用不可变对象了吧？因为不可变对象是常量，每次的哈希值算出来都是固定的，这样就不会出错。比如key='ABC'，value=10，存储地址为123，假设我突发奇想，把key改成'BCD'，那么当查找'BCD'的value的时候就会去234的地址找，但那里啥也没有，这就乱套了。

    3.你看我们上面有一句话：对于不同的key，有很大的概率得到的哈希值也不同。那么有很小的概率不同的key可以得到相同的哈希值了？没错，比如对于我们的例子来说，哈希值只有3位，那么只要元素个数超过1000，就一定会有至少两个key的哈希值相同（鸽笼原理），这种情况叫“冲突”，设计哈希表的时候要采取办法减少冲突，实在冲突了也要想办法补救。不过这是编译器的事情，况且对于初学者的我们来说碰到的冲突的概率基本等于零，就不用操心了。
