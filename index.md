##欢迎来到李世雄个人专栏

@@ -22,9 +22,9 @@ password = input('请输入口令: ')
# import getpass
# password = getpass.getpass('请输入口令: ')
if username == 'admin' and password == '123456':
	print('身份验证成功!')
    print('身份验证成功!')
else:
	print('身份验证失败!')
    print('身份验证失败!')
```

唯一需要说明的是和C/C++、Java等语言不同，Python中没有用花括号来构造代码块而是使用了缩进的方式来设置代码的层次结构，如果`if`条件成立的情况下需要执行多条语句，只要保持多条语句具有相同的缩进就可以了，换句话说连续的代码如果又保持了相同的缩进那么它们属于同一个代码块，相当于是一个执行的整体。
@@ -47,11 +47,11 @@ Author: 骆昊
x = float(input('x = '))
if x > 1:
	y = 3 * x - 5
    y = 3 * x - 5
elif x >= -1:
	y = x + 2
    y = x + 2
else:
	y = 5 * x + 3
    y = 5 * x + 3
print('f(%.2f) = %.2f' % (x, y))
```

@@ -70,12 +70,12 @@ Author: 骆昊
x = float(input('x = '))
if x > 1:
	y = 3 * x - 5
    y = 3 * x - 5
else:
	if x >= -1:
		y = x + 2
	else:
		y = 5 * x + 3
    if x >= -1:
        y = x + 2
    else:
        y = 5 * x + 3
print('f(%.2f) = %.2f' % (x, y))
```

@@ -96,11 +96,11 @@ Author: 骆昊
value = float(input('请输入长度: '))
unit = input('请输入单位: ')
if unit == 'in' or unit == '英寸':
	print('%f英寸 = %f厘米' % (value, value * 2.54))
    print('%f英寸 = %f厘米' % (value, value * 2.54))
elif unit == 'cm' or unit == '厘米':
	print('%f厘米 = %f英寸' % (value, value / 2.54))
    print('%f厘米 = %f英寸' % (value, value / 2.54))
else:
	print('请输入有效的单位')
    print('请输入有效的单位')
```

#### 练习2：掷骰子决定做什么
@@ -117,17 +117,17 @@ from random import randint
face = randint(1, 6)
if face == 1:
	result = '唱首歌'
    result = '唱首歌'
elif face == 2:
	result = '跳个舞'
    result = '跳个舞'
elif face == 3:
	result = '学狗叫'
    result = '学狗叫'
elif face == 4:
	result = '做俯卧撑'
    result = '做俯卧撑'
elif face == 5:
	result = '念绕口令'
    result = '念绕口令'
else:
	result = '讲冷笑话'
    result = '讲冷笑话'
print(result)
```
> **说明：**上面的代码中使用了random模块的randint函数生成指定范围的随机数来模拟掷骰子。
@@ -149,15 +149,15 @@ Author: 骆昊
score = float(input('请输入成绩: '))
if score >= 90:
	grade = 'A'
    grade = 'A'
elif score >= 80:
	grade = 'B'
    grade = 'B'
elif score >= 70:
	grade = 'C'
    grade = 'C'
elif score >= 60:
	grade = 'D'
    grade = 'D'
else:
	grade = 'E'
    grade = 'E'
print('对应的等级是:', grade)
```
#### 练习4：输入三条边长如果能构成三角形就计算周长和面积
@@ -177,12 +177,12 @@ a = float(input('a = '))
b = float(input('b = '))
c = float(input('c = '))
if a + b > c and a + c > b and b + c > a:
	print('周长: %f' % (a + b + c))
	p = (a + b + c) / 2
	area = math.sqrt(p * (p - a) * (p - b) * (p - c))
	print('面积: %f' % (area))
    print('周长: %f' % (a + b + c))
    p = (a + b + c) / 2
    area = math.sqrt(p * (p - a) * (p - b) * (p - c))
    print('面积: %f' % (area))
else:
	print('不能构成三角形')
    print('不能构成三角形')
```
> **说明：**上面的代码中使用了`math`模块的`sqrt`函数来计算平方根。用边长计算三角形面积的公式叫做[海伦公式](https://zh.wikipedia.org/zh-hans/海伦公式)。
@@ -200,32 +200,31 @@ salary = float(input('本月收入: '))
insurance = float(input('五险一金: '))
diff = salary - insurance - 3500
if diff <= 0:
	rate = 0
	deduction = 0
    rate = 0
    deduction = 0
elif diff < 1500:
	rate = 0.03
	deduction = 0
    rate = 0.03
    deduction = 0
elif diff < 4500:
	rate = 0.1
	deduction = 105
    rate = 0.1
    deduction = 105
elif diff < 9000:
	rate = 0.2
	deduction = 555
    rate = 0.2
    deduction = 555
elif diff < 35000:
	rate = 0.25
	deduction = 1005
    rate = 0.25
    deduction = 1005
elif diff < 55000:
	rate = 0.3
	deduction = 2755
    rate = 0.3
    deduction = 2755
elif diff < 80000:
	rate = 0.35
	deduction = 5505
    rate = 0.35
    deduction = 5505
else:
	rate = 0.45
	deduction = 13505
    rate = 0.45
    deduction = 13505
tax = abs(diff * rate - deduction)
print('个人所得税: ￥%.2f元' % tax)
print('实际到手收入: ￥%.2f元' % (diff + 3500 - tax))
```
>**说明：**上面的代码中使用了Python内置的`abs()`函数取绝对值来处理`-0`的问题。
  58  Day01-15/Day04/循环结构.md 
@@ -18,7 +18,7 @@ Author: 骆昊
sum = 0
for x in range(101):
	sum += x
    sum += x
print(sum)
```

@@ -40,7 +40,7 @@ Author: 骆昊
sum = 0
for x in range(2, 101, 2):
	sum += x
    sum += x
print(sum)
```

@@ -56,10 +56,9 @@ Author: 骆昊
sum = 0
for x in range(1, 101):
	if x % 2 == 0:
		sum += x
    if x % 2 == 0:
        sum += x
print(sum)
```

### while循环
@@ -81,18 +80,18 @@ import random
answer = random.randint(1, 100)
counter = 0
while True:
	counter += 1
	number = int(input('请输入: '))
	if number < answer:
		print('大一点')
	elif number > answer:
		print('小一点')
	else:
		print('恭喜你猜对了!')
		break
    counter += 1
    number = int(input('请输入: '))
    if number < answer:
        print('大一点')
    elif number > answer:
        print('小一点')
    else:
        print('恭喜你猜对了!')
        break
print('你总共猜了%d次' % counter)
if counter > 7:
	print('你的智商余额明显不足')
    print('你的智商余额明显不足')
```

> **说明：**上面的代码中使用了`break`关键字来提前终止循环，需要注意的是`break`只能终止它所在的那个循环，这一点在使用嵌套的循环结构（下面会讲到）需要引起注意。除了`break`之外，还有另一个关键字是`continue`，它可以用来放弃本次循环后续的代码直接让循环进入下一轮。
@@ -108,9 +107,9 @@ Author: 骆昊
"""
for i in range(1, 10):
	for j in range(1, i + 1):
		print('%d*%d=%d' % (i, j, i * j), end='\t')
	print()
    for j in range(1, i + 1):
        print('%d*%d=%d' % (i, j, i * j), end='\t')
    print()
```

### 练习
@@ -125,20 +124,19 @@ Version: 0.1
Author: 骆昊
Date: 2018-03-01
"""
from math import sqrt
num = int(input('请输入一个正整数: '))
end = int(sqrt(num))
is_prime = True
for x in range(2, end + 1):
	if num % x == 0:
		is_prime = False
		break
    if num % x == 0:
        is_prime = False
        break
if is_prime and num != 1:
	print('%d是素数' % num)
    print('%d是素数' % num)
else:
	print('%d不是素数' % num)
    print('%d不是素数' % num)
```

#### 练习2：输入两个正整数，计算最大公约数和最小公倍数。
@@ -155,13 +153,12 @@ Date: 2018-03-01
x = int(input('x = '))
y = int(input('y = '))
if x > y:
	(x, y) = (y, x)
    x, y = y, x
for factor in range(x, 0, -1):
	if x % factor == 0 and y % factor == 0:
		print('%d和%d的最大公约数是%d' % (x, y, factor))
		print('%d和%d的最小公倍数是%d' % (x, y, x * y // factor))
		break
    if x % factor == 0 and y % factor == 0:
        print('%d和%d的最大公约数是%d' % (x, y, factor))
        print('%d和%d的最小公倍数是%d' % (x, y, x * y // factor))
        break
```

#### 练习3：打印三角形图案。
@@ -214,4 +211,3 @@ for i in range(row):
        print('*', end='')
    print()
```

  186  Day01-15/Day07/字符串和常用数据结构.md 
@@ -103,28 +103,28 @@ if __name__ == '__main__':

```Python
def main():
	fruits = ['grape', 'apple', 'strawberry', 'waxberry']
    fruits = ['grape', 'apple', 'strawberry', 'waxberry']
	fruits += ['pitaya', 'pear', 'mango']
	# 循环遍历列表元素
	for fruit in fruits:
		print(fruit.title(), end=' ')
	print()
	# 列表切片
	fruits2 = fruits[1:4]
	print(fruits2)
	# fruit3 = fruits  # 没有复制列表只创建了新的引用
    for fruit in fruits:
        print(fruit.title(), end=' ')
    print()
    # 列表切片
    fruits2 = fruits[1:4]
    print(fruits2)
    # fruit3 = fruits  # 没有复制列表只创建了新的引用
    # 可以通过完整切片操作来复制列表
	fruits3 = fruits[:]
	print(fruits3)
	fruits4 = fruits[-3:-1]
	print(fruits4)
    fruits3 = fruits[:]
    print(fruits3)
    fruits4 = fruits[-3:-1]
    print(fruits4)
    # 可以通过反向切片操作来获得倒转后的列表的拷贝
	fruits5 = fruits[::-1]
	print(fruits5)
    fruits5 = fruits[::-1]
    print(fruits5)
if __name__ == '__main__':
	main()
    main()
```

下面的代码实现了对列表的排序操作。
@@ -200,12 +200,12 @@ def fib(n):
def main():
	for val in fib(20):
	    print(val)
    for val in fib(20):
        print(val)
if __name__ == '__main__':
	main()
    main()
```

### 使用元组
@@ -214,35 +214,35 @@ Python 的元组与列表类似，不同之处在于元组的元素不能修改

```Python
def main():
	# 定义元组
	t = ('骆昊', 38, True, '四川成都')
	print(t)
	# 获取元组中的元素
	print(t[0])
	print(t[3])
	# 遍历元组中的值
	for member in t:
		print(member)
	# 重新给元组赋值
	# t[0] = '王大锤'  # TypeError
	# 变量t重新引用了新的元组原来的元组将被垃圾回收
	t = ('王大锤', 20, True, '云南昆明')
	print(t)
	# 将元组转换成列表
	person = list(t)
	print(person)
    # 定义元组
    t = ('骆昊', 38, True, '四川成都')
    print(t)
    # 获取元组中的元素
    print(t[0])
    print(t[3])
    # 遍历元组中的值
    for member in t:
        print(member)
    # 重新给元组赋值
    # t[0] = '王大锤'  # TypeError
    # 变量t重新引用了新的元组原来的元组将被垃圾回收
    t = ('王大锤', 20, True, '云南昆明')
    print(t)
    # 将元组转换成列表
    person = list(t)
    print(person)
    # 列表是可以修改它的元素的
	person[0] = '李小龙'
	person[1] = 25
	print(person)
    person[0] = '李小龙'
    person[1] = 25
    print(person)
    # 将列表转换成元组
	fruits_list = ['apple', 'banana', 'orange']
	fruits_tuple = tuple(fruits_list)
	print(fruits_tuple)
    fruits_list = ['apple', 'banana', 'orange']
    fruits_tuple = tuple(fruits_list)
    print(fruits_tuple)
if __name__ == '__main__':
	main()
    main()
```

这里有一个非常值得探讨的问题，我们已经有了列表这种数据结构，为什么还需要元组这样的类型呢？
@@ -315,34 +315,34 @@ if __name__ == '__main__':

```Python
def main():
	scores = {'骆昊': 95, '白元芳': 78, '狄仁杰': 82}
    scores = {'骆昊': 95, '白元芳': 78, '狄仁杰': 82}
    # 通过键可以获取字典中对应的值
	print(scores['骆昊'])
	print(scores['狄仁杰'])
    print(scores['骆昊'])
    print(scores['狄仁杰'])
    # 对字典进行遍历(遍历的其实是键再通过键取对应的值)
	for elem in scores:
		print('%s\t--->\t%d' % (elem, scores[elem]))
    for elem in scores:
        print('%s\t--->\t%d' % (elem, scores[elem]))
    # 更新字典中的元素
	scores['白元芳'] = 65
	scores['诸葛王朗'] = 71
	scores.update(冷面=67, 方启鹤=85)
	print(scores)
	if '武则天' in scores:
		print(scores['武则天'])
	print(scores.get('武则天'))
    scores['白元芳'] = 65
    scores['诸葛王朗'] = 71
    scores.update(冷面=67, 方启鹤=85)
    print(scores)
    if '武则天' in scores:
        print(scores['武则天'])
    print(scores.get('武则天'))
    # get方法也是通过键获取对应的值但是可以设置默认值
	print(scores.get('武则天', 60))
    print(scores.get('武则天', 60))
    # 删除字典中的元素
	print(scores.popitem())
	print(scores.popitem())
	print(scores.pop('骆昊', 100)) 
    print(scores.popitem())
    print(scores.popitem())
    print(scores.pop('骆昊', 100))
    # 清空字典
	scores.clear()
	print(scores)
    scores.clear()
    print(scores)
if __name__ == '__main__':
	main()
    main()
```

### 练习
@@ -569,44 +569,44 @@ import os
def print_board(board):
	print(board['TL'] + '|' + board['TM'] + '|' + board['TR'])
	print('-+-+-')
	print(board['ML'] + '|' + board['MM'] + '|' + board['MR'])
	print('-+-+-')
	print(board['BL'] + '|' + board['BM'] + '|' + board['BR'])
    print(board['TL'] + '|' + board['TM'] + '|' + board['TR'])
    print('-+-+-')
    print(board['ML'] + '|' + board['MM'] + '|' + board['MR'])
    print('-+-+-')
    print(board['BL'] + '|' + board['BM'] + '|' + board['BR'])
def main():
	init_board = {
		'TL': ' ', 'TM': ' ', 'TR': ' ',
		'ML': ' ', 'MM': ' ', 'MR': ' ',
		'BL': ' ', 'BM': ' ', 'BR': ' '
	}
	begin = True
	while begin:
		curr_board = init_board.copy()
		begin = False
		turn = 'x'
		counter = 0
		os.system('clear')
		print_board(curr_board)
		while counter < 9:
			move = input('轮到%s走棋, 请输入位置: ' % turn)
			if curr_board[move] == ' ':
				counter += 1
				curr_board[move] = turn
				if turn == 'x':
					turn = 'o'
				else:
					turn = 'x'
			os.system('clear')
			print_board(curr_board)
		choice = input('再玩一局?(yes|no)')
		begin = choice == 'yes'
    init_board = {
        'TL': ' ', 'TM': ' ', 'TR': ' ',
        'ML': ' ', 'MM': ' ', 'MR': ' ',
        'BL': ' ', 'BM': ' ', 'BR': ' '
    }
    begin = True
    while begin:
        curr_board = init_board.copy()
        begin = False
        turn = 'x'
        counter = 0
        os.system('clear')
        print_board(curr_board)
        while counter < 9:
            move = input('轮到%s走棋, 请输入位置: ' % turn)
            if curr_board[move] == ' ':
                counter += 1
                curr_board[move] = turn
                if turn == 'x':
                    turn = 'o'
                else:
                    turn = 'x'
            os.system('clear')
            print_board(curr_board)
        choice = input('再玩一局?(yes|no)')
        begin = choice == 'yes'
if __name__ == '__main__':
	main()
    main()
```

>**说明**：最后这个案例来自[《Python编程快速上手:让繁琐工作自动化》](https://item.jd.com/11943853.html)一书（这本书对有编程基础想迅速使用Python将日常工作自动化的人来说还是不错的选择），对代码做了一点点的调整。
  2  Day01-15/Day08/code/rect.py 
@@ -11,7 +11,7 @@ class Rect(object):
    """矩形类"""

    def __init__(self, width=0, height=0):
        """构造器"""
        """初始化方法"""
        self.__width = width
        self.__height = height

  105  Day01-15/Day08/面向对象编程基础.md 
@@ -29,22 +29,22 @@
```Python
class Student(object):
	# __init__是一个特殊方法用于在创建对象时进行初始化操作
	# 通过这个方法我们可以为学生对象绑定name和age两个属性
	def __init__(self, name, age):
		self.name = name
		self.age = age
	def study(self, course_name):
		print('%s正在学习%s.' % (self.name, course_name))
	# PEP 8要求标识符的名字用全小写多个单词用下划线连接
	# 但是很多程序员和公司更倾向于使用驼峰命名法(驼峰标识)
	def watch_av(self):
		if self.age < 18:
			print('%s只能观看《熊出没》.' % self.name)
		else:
			print('%s正在观看岛国爱情动作片.' % self.name)
    # __init__是一个特殊方法用于在创建对象时进行初始化操作
    # 通过这个方法我们可以为学生对象绑定name和age两个属性
    def __init__(self, name, age):
        self.name = name
        self.age = age
    def study(self, course_name):
        print('%s正在学习%s.' % (self.name, course_name))
    # PEP 8要求标识符的名字用全小写多个单词用下划线连接
    # 但是很多程序员和公司更倾向于使用驼峰命名法(驼峰标识)
    def watch_av(self):
        if self.age < 18:
            print('%s只能观看《熊出没》.' % self.name)
        else:
            print('%s正在观看岛国爱情动作片.' % self.name
```
> **说明**：写在类中的函数，我们通常称之为（对象的）方法，这些方法就是对象可以接收的消息。
@@ -56,18 +56,18 @@ class Student(object):
```Python
def main():
    # 创建学生对象并指定姓名和年龄
	stu1 = Student('骆昊', 38)
    stu1 = Student('骆昊', 38)
    # 给对象发study消息
	stu1.study('Python程序设计')
    stu1.study('Python程序设计')
    # 给对象发watch_av消息
	stu1.watch_av()
	stu2 = Student('王大锤', 15)
	stu2.study('思想品德')
	stu2.watch_av()
    stu1.watch_av()
    stu2 = Student('王大锤', 15)
    stu2.study('思想品德')
    stu2.watch_av()
if __name__ == '__main__':
	main()
    main()
```
### 访问可见性问题
@@ -77,47 +77,47 @@ if __name__ == '__main__':
```Python
class Test:
	def __init__(self, foo):
		self.__foo = foo
    def __init__(self, foo):
        self.__foo = foo
	def __bar(self):
		print(self.__foo)
		print('__bar')
    def __bar(self):
        print(self.__foo)
        print('__bar')
def main():
	test = Test('hello')
	# AttributeError: 'Test' object has no attribute '__bar'
	test.__bar()
	# AttributeError: 'Test' object has no attribute '__foo'
	print(test.__foo)
    test = Test('hello')
    # AttributeError: 'Test' object has no attribute '__bar'
    test.__bar()
    # AttributeError: 'Test' object has no attribute '__foo'
    print(test.__foo)
if __name__ == "__main__":
	main()
    main()
```
但是，Python并没有从语法上严格保证私有属性或方法的私密性，它只是给私有的属性和方法换了一个名字来“妨碍”对它们的访问，事实上如果你知道更换名字的规则仍然可以访问到它们，下面的代码就可以验证这一点。之所以这样设定，可以用这样一句名言加以解释，就是“We are all consenting adults here”。因为绝大多数程序员都认为开放比封闭要好，而且程序员要自己为自己的行为负责。
```Python
class Test:
	def __init__(self, foo):
		self.__foo = foo
    def __init__(self, foo):
        self.__foo = foo
	def __bar(self):
		print(self.__foo)
		print('__bar')
    def __bar(self):
        print(self.__foo)
        print('__bar')
def main():
	test = Test('hello')
	test._Test__bar()
	print(test._Test__foo)
    test = Test('hello')
    test._Test__bar()
    print(test._Test__foo)
if __name__ == "__main__":
	main()
    main()
```
在实际开发中，我们并不建议将属性设置为私有的，因为这会导致子类无法访问（后面会讲到）。所以大多数Python程序员会遵循一种命名惯例就是让属性名以单下划线开头来表示属性是受保护的，本类之外的代码在访问这样的属性时应该要保持慎重。这种做法并不是语法上的规则，单下划线开头的属性和方法外界仍然是可以访问的，所以更多的时候它是一种暗示或隐喻，关于这一点可以看看我的[《Python - 那些年我们踩过的那些坑》](http://blog.csdn.net/jackfrued/article/details/79521404)文章中的讲解。
@@ -132,13 +132,10 @@ if __name__ == "__main__":
```Python
class Clock(object):
    """
    数字时钟
    """
    """数字时钟"""
    def __init__(self, hour=0, minute=0, second=0):
        """
        构造器
        """初始化方法
        :param hour: 时
        :param minute: 分
@@ -187,8 +184,7 @@ from math import sqrt
class Point(object):
    def __init__(self, x=0, y=0):
        """
        构造器
        """初始化方法
        
        :param x: 横坐标
        :param y: 纵坐标
@@ -197,8 +193,7 @@ class Point(object):
        self.y = y
    def move_to(self, x, y):
        """
        移动到指定位置
        """移动到指定位置
        
        :param x: 新的横坐标
        "param y: 新的纵坐标
@@ -207,8 +202,7 @@ class Point(object):
        self.y = y
    def move_by(self, dx, dy):
        """
        移动指定的增量
        """移动指定的增量
        
        :param dx: 横坐标的增量
        "param dy: 纵坐标的增量
@@ -217,8 +211,7 @@ class Point(object):
        self.y += dy
    def distance_to(self, other):
        """
        计算与另一个点的距离
        """计算与另一个点的距离
        
        :param other: 另一个点
        """
  15  Day01-15/Day09/面向对象进阶.md 
@@ -345,8 +345,7 @@ class Fighter(object, metaclass=ABCMeta):
    __slots__ = ('_name', '_hp')
    def __init__(self, name, hp):
        """
        初始化方法
        """初始化方法
        :param name: 名字
        :param hp: 生命值
@@ -372,8 +371,7 @@ class Fighter(object, metaclass=ABCMeta):
    @abstractmethod
    def attack(self, other):
        """
        攻击
        """攻击
        :param other: 被攻击的对象
        """
@@ -386,8 +384,7 @@ class Ultraman(Fighter):
    __slots__ = ('_name', '_hp', '_mp')
    def __init__(self, name, hp, mp):
        """
        初始化方法
        """初始化方法
        :param name: 名字
        :param hp: 生命值
@@ -400,8 +397,7 @@ class Ultraman(Fighter):
        other.hp -= randint(15, 25)
    def huge_attack(self, other):
        """
        究极必杀技(打掉对方至少50点或四分之三的血)
        """究极必杀技(打掉对方至少50点或四分之三的血)
        :param other: 被攻击的对象
@@ -418,8 +414,7 @@ class Ultraman(Fighter):
            return False
    def magic_attack(self, others):
        """
        魔法攻击
        """魔法攻击
        :param others: 被攻击的群体
  78  Day01-15/Day10/图形用户界面和游戏开发.md 
@@ -20,44 +20,44 @@ import tkinter.messagebox
def main():
	flag = True
	# 修改标签上的文字
	def change_label_text():
		nonlocal flag
		flag = not flag
		color, msg = ('red', 'Hello, world!')\
			if flag else ('blue', 'Goodbye, world!')
		label.config(text=msg, fg=color)
	# 确认退出
	def confirm_to_quit():
		if tkinter.messagebox.askokcancel('温馨提示', '确定要退出吗?'):
			top.quit()
	# 创建顶层窗口
	top = tkinter.Tk()
	# 设置窗口大小
	top.geometry('240x160')
	# 设置窗口标题
	top.title('小游戏')
	# 创建标签对象并添加到顶层窗口
	label = tkinter.Label(top, text='Hello, world!', font='Arial -32', fg='red')
	label.pack(expand=1)
	# 创建一个装按钮的容器
	panel = tkinter.Frame(top)
	# 创建按钮对象 指定添加到哪个容器中 通过command参数绑定事件回调函数
	button1 = tkinter.Button(panel, text='修改', command=change_label_text)
	button1.pack(side='left')
	button2 = tkinter.Button(panel, text='退出', command=confirm_to_quit)
	button2.pack(side='right')
	panel.pack(side='bottom')
	# 开启主事件循环
	tkinter.mainloop()
    flag = True
    # 修改标签上的文字
    def change_label_text():
        nonlocal flag
        flag = not flag
        color, msg = ('red', 'Hello, world!')\
            if flag else ('blue', 'Goodbye, world!')
        label.config(text=msg, fg=color)
    # 确认退出
    def confirm_to_quit():
        if tkinter.messagebox.askokcancel('温馨提示', '确定要退出吗?'):
            top.quit()
    # 创建顶层窗口
    top = tkinter.Tk()
    # 设置窗口大小
    top.geometry('240x160')
    # 设置窗口标题
    top.title('小游戏')
    # 创建标签对象并添加到顶层窗口
    label = tkinter.Label(top, text='Hello, world!', font='Arial -32', fg='red')
    label.pack(expand=1)
    # 创建一个装按钮的容器
    panel = tkinter.Frame(top)
    # 创建按钮对象 指定添加到哪个容器中 通过command参数绑定事件回调函数
    button1 = tkinter.Button(panel, text='修改', command=change_label_text)
    button1.pack(side='left')
    button2 = tkinter.Button(panel, text='退出', command=confirm_to_quit)
    button2.pack(side='right')
    panel.pack(side='bottom')
    # 开启主事件循环
    tkinter.mainloop()
if __name__ == '__main__':
	main()
    main()
```

需要说明的是，GUI应用通常是事件驱动式的，之所以要进入主事件循环就是要监听鼠标、键盘等各种事件的发生并执行对应的代码对事件进行处理，因为事件会持续的发生，所以需要这样的一个循环一直运行着等待下一个事件的发生。另一方面，Tk为控件的摆放提供了三种布局管理器，通过布局管理器可以对控件进行定位，这三种布局管理器分别是：Placer（开发者提供控件的大小和摆放位置）、Packer（自动将控件填充到合适的位置）和Grid（基于网格坐标来摆放控件），此处不进行赘述。
@@ -75,7 +75,7 @@ import pygame
def main():
	# 初始化导入的pygame中的模块
    # 初始化导入的pygame中的模块
    pygame.init()
    # 初始化用于显示的窗口并设置窗口尺寸
    screen = pygame.display.set_mode((800, 600))
@@ -84,7 +84,7 @@ def main():
    running = True
    # 开启一个事件循环处理发生的事件
    while running:
    	# 从消息队列中获取事件并对事件进行处理
        # 从消息队列中获取事件并对事件进行处理
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
@@ -103,7 +103,7 @@ import pygame
def main():
	# 初始化导入的pygame中的模块
    # 初始化导入的pygame中的模块
    pygame.init()
    # 初始化用于显示的窗口并设置窗口尺寸
    screen = pygame.display.set_mode((800, 600))
@@ -118,7 +118,7 @@ def main():
    running = True
    # 开启一个事件循环处理发生的事件
    while running:
    	# 从消息队列中获取事件并对事件进行处理
        # 从消息队列中获取事件并对事件进行处理
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
  58  Day01-15/Day11/文件和异常.md 
@@ -24,14 +24,13 @@

```Python
def main():
	f = open('致橡树.txt', 'r', encoding='utf-8')
	print(f.read())
	f.close()
    f = open('致橡树.txt', 'r', encoding='utf-8')
    print(f.read())
    f.close()
if __name__ == '__main__':
	main()
    main()
```

请注意上面的代码，如果`open`函数指定的文件并不存在或者无法打开，那么将引发异常状况导致程序崩溃。为了让代码有一定的健壮性和容错性，我们可以使用Python的异常机制对可能在运行时发生状况的代码进行适当的处理，如下所示。
@@ -55,7 +54,6 @@ def main():
if __name__ == '__main__':
    main()
```

在Python中，我们可以将那些在运行时可能会出现状况的代码放在`try`代码块中，在`try`代码块的后面可以跟上一个或多个`except`来捕获可能出现的异常状况。例如在上面读取文件的过程中，文件找不到会引发`FileNotFoundError`，指定了未知的编码会引发`LookupError`，而如果读取文件时无法按指定方式解码会引发`UnicodeDecodeError`，我们在`try`后面跟上了三个`except`分别处理这三种不同的异常状况。最后我们使用`finally`代码块来关闭打开的文件，释放掉程序中获取的外部资源，由于`finally`块的代码不论程序正常还是异常都会执行到（甚至是调用了`sys`模块的`exit`函数退出Python环境，`finally`块都会被执行，因为`exit`函数实质上是引发了`SystemExit`异常），因此我们通常把`finally`块称为“总是执行代码块”，它最适合用来做释放外部资源的操作。如果不愿意在`finally`代码块中关闭文件对象释放资源，也可以使用上下文语法，通过`with`关键字指定文件对象的上下文环境并在离开上下文环境时自动释放文件资源，代码如下所示。
@@ -75,7 +73,6 @@ def main():
if __name__ == '__main__':
    main()
```

除了使用文件对象的`read`方法读取文件之外，还可以使用`for-in`循环逐行读取或者用`readlines`方法将文件按行读取到一个列表容器中，代码如下所示。
@@ -85,26 +82,25 @@ import time
def main():
	# 一次性读取整个文件内容
	with open('致橡树.txt', 'r', encoding='utf-8') as f:
		print(f.read())
	# 通过for-in循环逐行读取
	with open('致橡树.txt', mode='r') as f:
		for line in f:
			print(line, end='')
			time.sleep(0.5)
	print()
	# 读取文件按行读取到列表中
	with open('致橡树.txt') as f:
		lines = f.readlines()
	print(lines)
	
    # 一次性读取整个文件内容
    with open('致橡树.txt', 'r', encoding='utf-8') as f:
        print(f.read())
if __name__ == '__main__':
	main()
    # 通过for-in循环逐行读取
    with open('致橡树.txt', mode='r') as f:
        for line in f:
            print(line, end='')
            time.sleep(0.5)
    print()
    # 读取文件按行读取到列表中
    with open('致橡树.txt') as f:
        lines = f.readlines()
    print(lines)
    
if __name__ == '__main__':
    main()
```

要将文本信息写入文件文件也非常简单，在使用`open`函数时指定好文件名并将文件模式设置为`'w'`即可。注意如果需要对文件内容进行追加式写入，应该将模式设置为`'a'`。如果要写入的文件不存在会自动创建文件而不是引发异常。下面的例子演示了如何将1~9999直接的素数分别写入三个文件中（1~99之间的素数保存在a.txt中，100~999之间的素数保存在b.txt中，1000~9999之间的素数保存在c.txt中）。
@@ -147,7 +143,6 @@ def main():
if __name__ == '__main__':
    main()
```

### 读写二进制文件
@@ -171,7 +166,6 @@ def main():
if __name__ == '__main__':
    main()
```

### 读写JSON文件
@@ -240,15 +234,14 @@ def main():
if __name__ == '__main__':
    main()
```

json模块主要有四个比较重要的函数，分别是：

- dump - 将Python对象按照JSON格式序列化到文件中
- dumps - 将Python对象处理成JSON格式的字符串
- load - 将文件中的JSON数据反序列化成对象
- loads - 将字符串的内容反序列化成Python对象
- `dump` - 将Python对象按照JSON格式序列化到文件中
- `dumps` - 将Python对象处理成JSON格式的字符串
- `load` - 将文件中的JSON数据反序列化成对象
- `loads` - 将字符串的内容反序列化成Python对象

这里出现了两个概念，一个叫序列化，一个叫反序列化。自由的百科全书[维基百科](https://zh.wikipedia.org/)上对这两个概念是这样解释的：“序列化（serialization）在计算机科学的数据处理中，是指将数据结构或对象状态转换为可以存储或传输的形式，这样在需要的时候能够恢复到原先的状态，而且通过序列化的数据重新获取字节时，可以利用这些字节来产生原始对象的副本（拷贝）。与这个过程相反的动作，即从一系列字节中提取数据结构的操作，就是反序列化（deserialization）”。

@@ -268,7 +261,6 @@ def main():
if __name__ == '__main__':
    main()
```

在Python中要实现序列化和反序列化除了使用json模块之外，还可以使用pickle和shelve模块，但是这两个模块是使用特有的序列化协议来序列化数据，因此序列化后的数据只能被Python识别。关于这两个模块的相关知识可以自己看看网络上的资料。另外，如果要了解更多的关于Python异常机制的知识，可以看看segmentfault上面的文章[《总结：Python中的异常处理》](https://segmentfault.com/a/1190000007736783)，这篇文章不仅介绍了Python中异常机制的使用，还总结了一系列的最佳实践，很值得一读。
  13  Day01-15/Day12/字符串和正则表达式.md 
@@ -72,15 +72,10 @@ Python提供了re模块来支持正则表达式相关操作，下面是re模块

```Python
"""
验证输入用户名和QQ号是否有效并给出对应的提示信息
要求：
用户名必须由字母、数字或下划线构成且长度在6~20个字符之间
QQ号是5~12的数字且首位不能为0
要求：用户名必须由字母、数字或下划线构成且长度在6~20个字符之间，QQ号是5~12的数字且首位不能为0
"""
import re
@@ -101,7 +96,6 @@ def main():
if __name__ == '__main__':
    main()
```

> **提示**：上面在书写正则表达式时使用了“原始字符串”的写法（在字符串前面加上了r），所谓“原始字符串”就是字符串中的每个字符都是它原始的意义，说得更直接一点就是字符串中没有所谓的转义字符啦。因为正则表达式中有很多元字符和需要进行转义的地方，如果不使用原始字符串就需要将反斜杠写作\\\\，例如表示数字的\\d得书写成\\\\d，这样不仅写起来不方便，阅读的时候也会很吃力。
@@ -140,7 +134,6 @@ def main():
if __name__ == '__main__':
    main()
```

> **说明**：上面匹配国内手机号的正则表达式并不够好，因为像14开头的号码只有145或147，而上面的正则表达式并没有考虑这种情况，要匹配国内手机号，更好的正则表达式的写法是：`(?<=\D)(1[38]\d{9}|14[57]\d{8}|15[0-35-9]\d{8}|17[678]\d{8})(?=\D)`，国内最近好像有19和16开头的手机号了，但是这个暂时不在我们考虑之列。
@@ -153,14 +146,13 @@ import re
def main():
    sentence = '你丫是傻叉吗? 我操你大爷的. Fuck you.'
    purified = re.sub('[操肏艹草曹]|fuck|shit|傻[比屄逼叉缺吊屌]|煞笔',
    purified = re.sub('[操肏艹]|fuck|shit|傻[比屄逼叉缺吊屌]|煞笔',
                      '*', sentence, flags=re.IGNORECASE)
    print(purified)  # 你丫是*吗? 我*你大爷的. * you.
if __name__ == '__main__':
    main()
```

> **说明**：re模块的正则表达式相关函数中都有一个flags参数，它代表了正则表达式的匹配标记，可以通过该标记来指定匹配时是否忽略大小写、是否进行多行匹配、是否显示调试信息等。如果需要为flags参数指定多个值，可以使用[按位或运算符](http://www.runoob.com/python/python-operators.html#ysf5)进行叠加，如`flags=re.I | re.M`。
@@ -181,7 +173,6 @@ def main():
if __name__ == '__main__':
    main()
```

### 后话
  36  Day01-15/Day13/进程和线程.md 
@@ -123,7 +123,6 @@ def main():
if __name__ == '__main__':
    main()
```

看起来没毛病，但是最后的结果是Ping和Pong各输出了10个，Why？当我们在程序中创建进程的时候，子进程复制了父进程及其所有的数据结构，每个子进程有自己独立的内存空间，这也就意味着两个子进程中各有一个`counter`变量，所以结果也就可想而知了。要解决这个问题比较简单的办法是使用multiprocessing模块中的`Queue`类，它是可以被多个进程共享的队列，底层是通过管道和[信号量（semaphore）]()机制来实现的，有兴趣的读者可以自己尝试一下。
@@ -140,27 +139,26 @@ from time import time, sleep
def download(filename):
	print('开始下载%s...' % filename)
	time_to_download = randint(5, 10)
	sleep(time_to_download)
	print('%s下载完成! 耗费了%d秒' % (filename, time_to_download))
    print('开始下载%s...' % filename)
    time_to_download = randint(5, 10)
    sleep(time_to_download)
    print('%s下载完成! 耗费了%d秒' % (filename, time_to_download))
def main():
	start = time()
	t1 = Thread(target=download, args=('Python从入门到住院.pdf',))
	t1.start()
	t2 = Thread(target=download, args=('Peking Hot.avi',))
	t2.start()
	t1.join()
	t2.join()
	end = time()
	print('总共耗费了%.3f秒' % (end - start))
    start = time()
    t1 = Thread(target=download, args=('Python从入门到住院.pdf',))
    t1.start()
    t2 = Thread(target=download, args=('Peking Hot.avi',))
    t2.start()
    t1.join()
    t2.join()
    end = time()
    print('总共耗费了%.3f秒' % (end - start))
if __name__ == '__main__':
	main()

    main()
```
我们可以直接使用threading模块的`Thread`类来创建线程，但是我们之前讲过一个非常重要的概念叫“继承”，我们可以从已有的类创建新类，因此也可以通过继承`Thread`类的方式来创建自定义的线程类，然后再创建线程对象并启动线程。代码如下所示。
@@ -198,7 +196,6 @@ def main():
if __name__ == '__main__':
    main()
```

因为多个线程可以共享进程的内存空间，因此要实现多个线程间的通信相对简单，大家能想到的最直接的办法就是设置一个全局变量，多个线程共享这个全局变量即可。但是当多个线程共享同一个变量（我们通常称之为“资源”）的时候，很有可能产生不可控的结果从而导致程序失效甚至崩溃。如果一个资源被多个线程竞争使用，那么我们通常称之为“临界资源”，对“临界资源”的访问需要加上保护，否则资源会处于“混乱”的状态。下面的例子演示了100个线程向同一个银行账户转账（转入1元钱）的场景，在这个例子中，银行账户就是一个临界资源，在没有保护的情况下我们很有可能会得到错误的结果。
@@ -253,7 +250,6 @@ def main():
if __name__ == '__main__':
    main()
```

运行上面的程序，结果让人大跌眼镜，100个线程分别向账户中转入1元钱，结果居然远远小于100元。之所以出现这种情况是因为我们没有对银行账户这个“临界资源”加以保护，多个线程同时向账户中存钱时，会一起执行到`new_balance = self._balance + money`这行代码，多个线程得到的账户余额都是初始状态下的`0`，所以都是`0`上面做了+1的操作，因此得到了错误的结果。在这种情况下，“锁”就可以派上用场了。我们可以通过“锁”来保护“临界资源”，只有获得“锁”的线程才能访问“临界资源”，而其他没有得到“锁”的线程只能被阻塞起来，直到获得“锁”的线程释放了“锁”，其他线程才有机会获得“锁”，进而访问被保护的“临界资源”。下面的代码演示了如何使用“锁”来保护对银行账户的操作，从而获得正确的结果。
@@ -310,7 +306,6 @@ def main():
if __name__ == '__main__':
    main()
```

比较遗憾的一件事情是Python的多线程并不能发挥CPU的多核特性，这一点只要启动几个执行死循环的线程就可以得到证实了。之所以如此，是因为Python的解释器有一个“全局解释器锁”（GIL）的东西，任何线程执行前必须先获得GIL锁，然后每执行100条字节码，解释器就自动释放GIL锁，让别的线程有机会执行，这是一个历史遗留问题，但是即便如此，就如我们之前举的例子，使用多线程在提升执行效率和改善用户体验方面仍然是有积极意义的。
@@ -490,4 +485,5 @@ if __name__ == '__main__':
    main()
```

比较两段代码的执行结果（在我目前使用的MacBook上，上面的代码需要大概6秒左右的时间，而下面的代码只需要不到1秒的时间，再强调一次我们只是比较了运算的时间，不考虑列表创建及切片操作花费的时间），使用多进程后由于获得了更多的CPU执行时间以及更好的利用了CPU的多核特性，明显的减少了程序的执行时间，而且计算量越大效果越明显。当然，如果愿意还可以将多个进程部署在不同的计算机上，做成分布式进程，具体的做法就是通过multiprocessing.managers模块中提供的管理器将`Queue`对象通过网络共享出来（注册到网络上让其他计算机可以访问），这部分内容也留到爬虫的专题再进行讲解。
比较两段代码的执行结果（在我目前使用的MacBook上，上面的代码需要大概6秒左右的时间，而下面的代码只需要不到1秒的时间，再强调一次我们只是比较了运算的时间，不考虑列表创建及切片操作花费的时间），使用多进程后由于获得了更多的CPU执行时间以及更好的利用了CPU的多核特性，明显的减少了程序的执行时间，而且计算量越大效果越明显。当然，如果愿意还可以将多个进程部署在不同的计算机上，做成分布式进程，具体的做法就是通过multiprocessing.managers模块中提供的管理器将`Queue`对象通过网络共享出来（注册到网络上让其他计算机可以访问），这部分内容也留到爬虫的专题再进行讲解。

  1  Day01-15/Day14-A/网络编程入门.md 
@@ -296,3 +296,4 @@ if __name__ == '__main__':
#### UDP套接字

传输层除了有可靠的传输协议TCP之外，还有一种非常轻便的传输协议叫做用户数据报协议，简称UDP。TCP和UDP都是提供端到端传输服务的协议，二者的差别就如同打电话和发短信的区别，后者不对传输的可靠性和可达性做出任何承诺从而避免了TCP中握手和重传的开销，所以在强调性能和而不是数据完整性的场景中（例如传输网络音视频数据），UDP可能是更好的选择。可能大家会注意到一个现象，就是在观看网络视频时，有时会出现卡顿，有时会出现花屏，这无非就是部分数据传丢或传错造成的。在Python中也可以使用UDP套接字来创建网络应用，对此我们不进行赘述，有兴趣的读者可以自行研究。

  24  Day01-15/Day14-B/网络应用开发.md 
@@ -16,21 +16,21 @@ from email.mime.text import MIMEText
def main():
    # 请自行修改下面的邮件发送者和接收者
	sender = 'abcdefg@126.com'
	receivers = ['uvwxyz@qq.com', 'uvwxyz@126.com']
	message = MIMEText('用Python发送邮件的示例代码.', 'plain', 'utf-8')
	message['From'] = Header('王大锤', 'utf-8')
	message['To'] = Header('骆昊', 'utf-8')
	message['Subject'] = Header('示例代码实验邮件', 'utf-8')
	smtper = SMTP('smtp.126.com')
    sender = 'abcdefg@126.com'
    receivers = ['uvwxyz@qq.com', 'uvwxyz@126.com']
    message = MIMEText('用Python发送邮件的示例代码.', 'plain', 'utf-8')
    message['From'] = Header('王大锤', 'utf-8')
    message['To'] = Header('骆昊', 'utf-8')
    message['Subject'] = Header('示例代码实验邮件', 'utf-8')
    smtper = SMTP('smtp.126.com')
    # 请自行修改下面的登录口令
	smtper.login(sender, 'secretpass')
	smtper.sendmail(sender, receivers, message.as_string())
	print('邮件发送完成!')
    smtper.login(sender, 'secretpass')
    smtper.sendmail(sender, receivers, message.as_string())
    print('邮件发送完成!')
if __name__ == '__main__':
	main()
    main()
```

如果要发送带有附件的邮件，那么可以按照下面的方式进行操作。
@@ -82,7 +82,7 @@ def main():
    smtper.sendmail(sender, receivers, message.as_string())
    # 与邮件服务器断开连接
    smtper.quit()
	print('发送完成!')
    print('发送完成!')
if __name__ == '__main__':
