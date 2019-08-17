

# flask使用操作指南之模型2

>Auth: 王海飞
>
>Data：2018-05-16
>
>Email：779598160@qq.com
>
>github：https://github.com/coco369/knowledge 


### 1. 深入数据库增删改查

定义模型，并定义初始化的函数：

	class Student(db.Model):
	
	    s_id = db.Column(db.Integer, primary_key=True, autoincrement=True)
	    s_name = db.Column(db.String(16), unique=True)
	    s_age = db.Column(db.Integer, default=1)
	
	    __tablename__ = "student"
	
	    def __init__(self, name, age):
	        self.s_name = name
	        self.s_age = age


#### 1.1 增--批量增加

第一种方式：

	@blue.route('/createstus/')
	def create_users():
	    stus = []
	    for i in range(5):
			# 实例化Student的对象
	        s = Student()
			# 对象的属性赋值
	        s.s_name = '张三%s' % random.randrange(10000)
	        s.s_age = '%d' % random.randrange(100)
	        stus.append(s)
		# 添加需要创建的数据
	    db.session.add_all(stus)
		# 提交事务到数据库
	    db.session.commit()
	
	    return '创建成功'

注：在创建单条数据的时候使用db.session.add()，在创建多条数据的时候使用db.session.add_all()

第二种方式：

	@blue.route('/createstus/')
	def create_users():
	    stus = []
	    for i in range(5):
			# 使用类的初始化去创建Student对象
	        s = Student('张三%s' % random.randrange(10000),
	                    '%d' % random.randrange(100))
	        stus.append(s)
	
	    db.session.add_all(stus)
	    db.session.commit()
	
	    return '创建成功'

#### 1.2 查--使用运算符

获取查询集
	
	filter(类名.属性名.运算符(‘xxx’))

	filter(类名.属性 数学运算符  值)

运算符：

	contains： 包含
	startswith：以什么开始
	endswith：以什么结束
	in_：在范围内
	like：模糊
	__gt__: 大于
	__ge__：大于等于
	__lt__：小于
	__le__：小于等于

筛选：
	
	offset()
	
	limit()
	
	order_by()
	
	get()
	
	first()
	
	paginate()

逻辑运算：

	与
		and_
		filter(and_(条件),条件…)
	
	或
		or_
		filter(or_(条件),条件…)
	
	非
		not_
		filter(not_(条件),条件…)


例子1：

1. 查询学生的id为3，4，5，6，16的的学生信息，使用<b>in_逻辑运算</b>


		@blue.route('/getstubyids/')
		def get_stu_by_ids():
	
	    	students = Student.query.filter(Student.s_id.in_([3,4,5,6,16]))
	    	return render_template('StudentList.html', students=students)

2. 查询学生的年龄小于18岁的学生的信息
	
		Student.query.filter(Student.s_age < 18)

3. 查询学生的年龄小于18岁的学生的信息，<b>\_\_lt\_\_小于</b>
 
		students = Student.query.filter(Student.s_age.__lt__(15))

4. 查询学生的年龄小于等于18岁的学生的信息，<b>\_\_le\_\_小于等于</b>

		students = Student.query.filter(Student.s_age.__le__(15))

5. 查询学生的姓名以什么开始或者以什么结尾的学生的信息<b>startswith和endswith</b>

    	students = Student.query.filter(Student.s_name.startswith('张'))
    	students = Student.query.filter(Student.s_name.endswith('2'))

6. 查询id=4的学生的信息

		Student.query.get(4)
		获取的结果是学生的对象

7. 模糊搜索like
		
		%：代表一个或者多个
		_：代表一个
		
		Student.query.filter(Student.s_name.like('%张%')) 

8. 分页，查询第二页的数据4条
		
		第一个参数是那一页，第二个参数是一页的条数，第三个参数是是否输出错误信息
		students = Student.query.paginate(2, 4, False).items

例子2：
	
跳过offset几个信息，截取limit结果的几个值

    # 按照id降序排列
    stus = Student.query.order_by('-s_id')

	# 按照id升序排列
    stus = Student.query.order_by('s_id')
    stus = Student.query.order_by(asc('s_id'))
    stus = Student.query.order_by('s_id asc')

    # 按照id降序获取三个
    stus = Student.query.order_by('-s_id').limit(3)
	stus = Student.query.order_by('s_id desc').limit(3)

	from sqlalchemy import desc
	stus = Student.query.order_by(desc('s_id')).limit(3)

    # 获取年龄最大的一个
    stus = Student.query.order_by('-s_age').first()

    # 跳过3个数据，查询5个信息
    stus = Student.query.order_by('-s_age').offset(3).limit(5)

    # 跳过3个数据
    stus = Student.query.order_by('-s_age').offset(3)

    # 获取id等于24的学生
    stus = Student.query.filter(Student.s_id==24)
    stus = Student.query.get(24)

例子3：

1. 查询

	from sqlalchemy import and\_, or\_, not\_

	<b>查询多个条件</b>

    stus = Student.query.filter(Student.s_age==18, Student.s_name=='雅典娜')

    <b>and_ 并且条件</b>

    stus = Student.query.filter(and\_(Student.s_age==18, Student.s_name=='雅典娜'))

    <b>or_ 或者条件</b>

    stus = Student.query.filter(or\_(Student.s_age==18, Student.s_name=='火神'))

    <b>not_ 非</b>

    stus = Student.query.filter(not\_(Student.s_age==18), Student.s_name=='火神')

    查询姓名不包含'可爱‘，并且年龄不等于12的学生

    stus = Student.query.filter(not_(Student.s_name.contains('可爱')),
                                not_(Student.s_age == 12))

例子4：

<b>分页：</b>

![图](images/flask_sqlalchemy_paginate.png)
	
后端数据处理：

	# 方法一：手动实现分页，使用offset和limit
    page = int(request.args.get('page', 1))
    stus = Student.query.offset((page-1)*5).limit(5)

    # 方法二： 使用切片[:]
    s_page = (page - 1)*5
    e_page = page * 5
    stus = Student.query.all()[s_page: e_page]
	
	# 方法三：使用paginate
	# 查询第几页的数据	
	page = int(request.args.get('page', 1))
	
	# 每一页的条数多少，默认为10条
    per_page = int(request.args.get('per_page', 10))
	
	# 查询当前第几个的多少条数据
    paginate = Student.query.order_by('-s_id').paginate(page, per_page, error_out=False)

    stus = paginate.items
    
前端数据展示：

	<h2>学生信息</h2>
    {% for stu in stus %}
        id：{{ stu.s_id }}
        姓名：{{ stu.s_name }}
        年龄：{{ stu.s_age }}
        <br>
    {% endfor %}
    <br>
    总页数: {{ paginate.pages }}
    <br>
    一共{{ paginate.total }}条数据
    <br>
    当前页数：{{ paginate.page }}
    <br>
    {% if paginate.has_prev %}
        <a href="/stupage/?page={{ paginate.prev_num }}">上一页</a>：{{ paginate.prev_num }}
    {% endif %}

    {% if paginate.has_next %}
        <a href="/stupage/?page={{ paginate.next_num }}">下一页</a>：{{ paginate.next_num }}
    {% endif %}
    <br>

    <br>
    页码：{% for i in  paginate.iter_pages() %}
            <a href="/stupage/?page={{ i }}">{{ i }}</a>
        {% endfor %}
	
	
### 2. 关联关系

#### 2.1 一对多建立模型

学生模型：

	class Student(db.Model):
	
	    s_id = db.Column(db.Integer, primary_key=True, autoincrement=True)
	    s_name = db.Column(db.String(20), unique=True)
	    s_age = db.Column(db.Integer, default=18)
	    s_g = db.Column(db.Integer, db.ForeignKey('grade.g_id'), nullable=True)
	
	    __tablename__ = 'student'

班级模型：

	class Grade(db.Model):

	    g_id = db.Column(db.Integer, primary_key=True, autoincrement=True)
	    g_name = db.Column(db.String(10), unique=True)
	    g_desc = db.Column(db.String(100), nullable=True)
	    g_time = db.Column(db.Date, default=datetime.now)
	    students = db.relationship('Student', backref='stu', lazy=True)
	
	    __tablename__ = 'grade'


官网解释有如下几个lazy的参数：

lazy 决定了 SQLAlchemy 什么时候从数据库中加载数据:，有如下四个值:

<b>select</b>/True: (which is the default) means that SQLAlchemy will load the data as necessary in one go using a standard select statement.

<b>joined</b>/False: tells SQLAlchemy to load the relationship in the same query as the parent using a JOIN statement.

<b>subquery</b>: works like ‘joined’ but instead SQLAlchemy will use a subquery.

<b>dynamic</b>: is special and useful if you have many items. Instead of loading the items SQLAlchemy will return another query object which
you can further refine before loading the items. This is usually what you want if you expect more than a handful of items for this relationship

	select就是访问到属性的时候，就会全部加载该属性的数据。

	joined则是在对关联的两个表进行join操作，从而获取到所有相关的对象。

	dynamic则不一样，在访问属性的时候，并没有在内存中加载数据，而是返回一个query对象, 需要执行相应方法才可以获取对象，

<b style="color:red;">注意</b>: 当在Student模型中新增s_g字段后，在执行db.create_all()方法时，该Student模型映射到数据库中的表并不会新增s_g字段，因此字段的新增需要手动的执行SQL语句，并指定和Grade模型对应的表grade之间的主外键关系。


	alter table student add s_g int;
	
	ALTER TABLE student add FOREIGN KEY (s_g) references grade(g_id);


#### 2.2

1. 通过班级查询学生信息


		@grade.route('/selectstubygrade/<int:id>/')
		
		def select_stu_by_grade(id):
		    grade = Grade.query.get(id)
			# 通过班级对象.定义的relationship变量去获取学生的信息
		    stus = grade.students
		
		    return render_template('grade_student.html',
		                           stus=stus,
		                           grade=grade
		                           )

2. 通过学生信息查询班级信息


		@stu.route('/selectgradebystu/<int:id>/')

		def select_grade_by_stu(id):
	
		    stu = Student.query.get(id)
			# 通过学生对象.定义的backref参数去获取班级的信息
		    grade = stu.stu
		
		    return render_template('student_grade.html',
		                           grade=grade,
		                           stu=stu)

注意：表的外键由db.ForeignKey指定，传入的参数是表的字段。db.relations它声明的属性不作为表字段，第一个参数是关联类的名字，backref是一个反向身份的代理,相当于在Student类中添加了stu的属性。例如，有Grade实例dept和Student实例stu。dept.students.count()将会返回学院学生人数;stu.stu.first()将会返回学生的学院信息的Grade类实例。一般来讲db.relationship()会放在一这一边。


### 3. 数据库迁移

在django中继承了makemigrations，可以通过migrate操作去更新数据库，修改我们定义的models，然后在将模型映射到数据库中。

在flask中也有migrate操作，它能跟踪模型的变化，并将变化映射到数据库中

#### 2.1 安装migrate

	pip install flask-migrate

#### 2.2 配置使用migrate

##### 2.2.1 初始化，使用app和db进行migrate对象的初始化

	from flask_migrate import Migrate

	#绑定app和数据库
    Migrate(app=app, db=db)

##### 2.2.2 安装了flask-script的话，可以在Manager()对象上添加迁移指令

	from flask_migrate import Migrate, MigrateCommand

	app = Flask(__name__)

	manage = Manager(app=app)

	manage.add_command('db', MigrateCommand)

操作：

	python manage.py db init  初始化出migrations的文件，只调用一次

	python manage.py db migrate  生成迁移文件

	python manage.py db upgrade 执行迁移文件中的升级
	
	python manage.py db downgrade 执行迁移文件中的降级

	python manage.py db --help 帮助文档
