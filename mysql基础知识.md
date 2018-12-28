# mysql基础知识

## 数据库简介





```

'''
数据库的诞生：
    人类在进化过程中，创造了数字、文字、符号等进行数据较多记录，但是随着认知能力和创造能力的提升，数据量越来越大，对于数据的记录和准确查找称为一个重大难题。计算机诞生后，数据开始在计算机中存储并计算，并设计出了数据库系统


数据库解决了的问题：
    1、持久化存储
    2、优化读写
    3、保证数据的有效性



为什么要使用数据库：
    因为数据量越来越大，有效存储对应的数据
    说明：
    ATM系统，用户和密码
    sunck#123456
    sunck#123456
    sunck#123456
    sunck#123456
    使用数据库存储用户的信息(账号和密码)


    类比(mysql充当文件管理的一个软件)：
        服务端：
            socket服务端
            解析指令（SQL语句）
            本地文件的操作

        客户端：
            socket客户端
            发送指令（SQL语句）




分类：
    文档型：例如SQLit，就是一个文件，通过对文件的复制完成数据库的复制

    服务型：例如mysql，数据存储在一个物理文件中，但是需要使用终端以tcp/ip协议链接，进行数据库的读写操作




三范式：
    概念：经过研究和对使用中问题的总结，对于设计数据库提出了一些规范，这些规范称为范式
    范式：
        第一范式：列不可拆分
        第二范式：唯一标识
        第三范式：引用主键

E-R模型：
    当前物理的数据库都是按照E-R模型进行设计的
    E：标识entry，实体
    R：标识relationship，关系
    一个实体对应转换为数据库中的一个表
    关系描述两个实体之间的对应规则：
        1、一对一
        2、一对多
        3、多对多
    关系转为数据库表中的一个列，在关系型数据库中一行就是一个对象

   
   '''
```

##  连接数据库

```

mysql安装后默认有一个root用户，可以先使用root用于登陆
    mysql -u 用户名 -p
    mysql -u root -p




简单使用：
    显示数据库
        show databases;
        自带数据库：
            information_schema    mysql本身架构相关数据
            mysql    用户权限相关数据

    创建数据库
        格式：
            utf-8：create  database  数据库名  default  charset  utf8  collate  utf8_general_ci;
            gbk：create  database  数据库名  default  charset  gbk  collate  gbk_chinese_ci;

    使用数据库
        格式：use 数据库名;

    查看当前正在使用的数据库
        select database();

    显示当前数据库中的所有表
        show tables;








用户管理：
    注意：需要使用root用户
    创建用户
        格式：create  user  '用户名'@'IP地址'  identified  by  '密码';
        示例：
            create  user  'sunck'@'10.0.122.158'  identified  by  'sunck1999';
                允许10.0.122.158使用sunck用户登录
            create  user  'sunck'@'10.0.122.%'  identified  by  'sunck1999';
                允许10.0.122.*网段使用sunck用户登录
            create  user  'sunck'@'%'  identified  by  'sunck1999';
        查看：
            use mysql;
            select user,host from user;

    删除用户：
        dorp  user  '用户名'@'IP地址';
    修改用户：
        rename  user  '用户名'@'IP地址'  to  '新用户名'@'IP地址';
    修改用户密码：
        set password for '用户名'@'IP地址' = password('新密码');





授权管理：需要root用户
    查看权限：
        show grants for '用户名'@'IP地址';
    授权：
        格式：
            grant 权限 on 数据库.表 to '用户名'@'IP地址';

        示例：
            只能对axf数据库下的t1表进行查看和插入操作
            grant select,insert on axf.t1 to 'sunck'@'%';
            只能对axf数据库下的所有表进行查看和插入操作
            grant select,insert on axf.* to 'sunck'@'%';
            添加对axf数据库下所有表，添加grant以外的所有权限
            grant all privileges on axf.* to 'sunck'@'%';

    权限说明：详情见《权限说明.txt》

    取消授权：
        revoke 权限 on 数据库.表 from '用户名'@'IP地址';


    将数据读取到内存，立即生效
        flush privileges



后期开发实际中的一些说明：
    后期开发基本不会使用root用户，进入公司后，公司的DB人员会体用一个用户名和密码并说明权限




配置阿里云的安全组协议

修改mysql的配置
    sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf

    bind-address = 127.0.0.1 --->bind-address = 0.0.0.0

远程终端连接数据库：
    mysql -h "ip地址" -u 用户名 -p

```



## 对库的操作

```
创建数据库
    # utf8_general_ci 排序
    utf-8:create database 数据库名 default charset utf8 collate utf8_general_ci;
    gbk:create database 数据库名 default charset gbk collate gbk_chinese_ci;

删除数据库
    drop database 数据库名

切换数据库
    ues 数据库名

查看当前选择的数据库
    select database();





```



##  对表的操作

```
一、查看当前数据库中的所有表
    show tables;

二、建表
    数据完整性：
        1、一个数据库就是一个完整的业务单元，可以包含多张表，数据被存储在表中
        2、在表中为了更加精准的存储数据，保证数据的正确有效性，可以在创建表的时候，为表添加一些强制性的验证，包括数据字段的类型、约束
    格式：
        create table 表名(列名 类型 [约束1[,约束2[,……]]]) engine=引擎 default charset=编码;
    表名：给数据集合起的名字
    列名：字段的名字
    编码：要与数据编码相同，可以解决存储编码错误的问题
    引擎：
        myisam：默认引擎，不支持事物
        innodb：支持事物，原子性操作
    类型：
        作用：明确字段存储的数据类型
        详情请见<MySQL字段类型.txt>

create table student(
    id int not null auto_increment primary key,
    sex bit,
    age int,
    name char(20),
    description varchar(100),
    birthday date,
    grade enum('python01','python02','python03'),
    hobby set('power','money','boy','girl')
) engine=innodb default charset=utf8;
create table student(
    id int not null auto_increment,
    sex bit,
    age int,
    name char(20),
    description varchar(100),
    birthday date,
    grade enum('python01','python02','python03'),
    hobby set('power','money','boy','girl'),
    primary key (id)
) engine=innodb default charset=utf8;

insert into student values(0,1,18,'tom','tom is a good man','1999-01-01','python01','power,money,boy');


    约束：
        1、primary key    主键
            作用：唯一约束标识数据库表中的每条记录
            注意：
                主键必须包含唯一的值
                主键列不能包含null值
                每个表都应该有一个主键，并且每个表只能拥有一个主键
        2、not null   非空
            作用：约束强制列不能接受null值
            注意：约束强制字段始终包含值，所以如过不想字段添加值，就无法插入和更新数据
        3、null     空
            作用：允许为空
        4、auto_increment   自增长
            作用：自增长
            注意：对于自增长列，必须是索引(含主键)
        5、default      默认值
            作用：用于向列中插入默认值
        6、unique       唯一值
            作用：约束唯一标识数据库中表的每条数据
            与primary key的区别：
                a、两者均为列或列集合提供了唯一性的保证
                b、pk拥有自动定义的unique约束
                c、每个表可以有多个unique约束，但是每个表只能有一个pk约束
            使用：unique 唯一索引名称 (列名1[,……])
        7、foreign key  外键
            说明：一个表中fK指向另一个表中的pk
            作用：
                a、用于用于预防破坏表之间的连接的动作
                b、也能防止非法数据插入外键列，因为它必须是它所指向的那个表中的值之一




create table student(
    id int not null auto_increment primary key,
    sex bit not null,
    age int default 20,
    name char(20),
    description varchar(100),
    birthday date,
    grade enum('python01','python02','python03'),
    hobby set('power','money','boy','girl')
) engine=innodb default charset=utf8;


insert into student values(0,null,18,'tom','tom is a good man','1999-01-01','python01','power,money,boy');
insert into student values(0,1,null,'tom','tom is a good man','1999-01-01','python01','power,money,boy');
insert into student values(0,1,null,'tom','tom is a good man','1999-01-01','python01','power,money,boy');

insert into student(sex, name) values(1, 'lilei');




create table student(
    id int not null auto_increment primary key,
    sex bit not null,
    age int default 20,
    sid char(20) unique,
    name char(20),
    description varchar(100),
    birthday date,
    grade enum('python01','python02','python03'),
    hobby set('power','money','boy','girl')
) engine=innodb default charset=utf8;
create table student(
    id int not null auto_increment primary key,
    sex bit not null,
    age int default 20,
    sid char(20),
    name char(20),
    description varchar(100),
    birthday date,
    grade enum('python01','python02','python03'),
    hobby set('power','money','boy','girl'),
    unique uq_sid (sid)
) engine=innodb default charset=utf8;
insert into student values(0,1,18,'123','tom','tom is a good man','1999-01-01','python01','power,money,boy');
insert into student values(0,1,19,'133','lilei','lilei is a good man','1999-01-01','python01','power,money,boy');


三、插入数据(增)
    1、全列插入
        insert into 表名 values(值1,值2,……);
        注意：主键是自增长，但是在全列插入式需要占位，插入成功后以实际值为准
        insert into student values(0, 18, 'sunck');
        insert into student values(0, 50, '刘德华');
        insert into student values(0, 40, '刀郎');

    2、缺省插入
        inset into 表名(列1,列2,……) values(值1,值2,……);
    3、同时插入多条数据
        insert into 表名 values(值1,值2,……),(值1,值2,……),……;
        insert into 表名(列1,列2,……) values(值1,值2,……),(值1,值2,……),……;

四、查看数据
    select * from 表名;
    说明：
        1、from关键字后面写的表名，表示数据来源于这张表
        2、select后面写表中的列名，如果是*，表示结果中显示表中所有的列
        3、如果要查询多个列，列之间使用逗号分隔


五、删除表
    drop table 表名;

六、查看表结构
    desc 表名

七、查看建表语句
    show create table 表名;     横着看
    show create table 表名 \G;  竖着看

八、重命名表名
    rename table 原表名 to 新表名;

九、清空表数据
    delete from 表名;
    truncate table 表名;


create table student(
    sex bit not null,
    age int default 20,
    sid char(20),
    name char(20),
    description varchar(100),
    birthday date,
    grade enum('python01','python02','python03'),
    hobby set('power','money','boy','girl'),
    unique uq_sid (sid)
) engine=innodb default charset=utf8;
十、修改表
    添加列
        alter table 表名 add 列名 类型;

    删除列
        alter table 表名 drop column 列名;

    修改列
        alter table 表名 modify column 列名 类型;--类型
        alter table 表名 change 原列名 新列名 类型;--列名,类型

    添加主键
        alter table 表名 add primary key(列名);

    删除主键
        alter table 表名 drop primary key;
        #列名后的类型会修改列名的类型
        alter table 表名 modify 列名 int,drop primary key;

    添加外键
        alter table 从表 add constraint 外键名称 foreign key 从表(外键字段) references 主表(主表字段);

        外键名称：fk_从表_主表
    删除外键
        alter table 表名 drop foreign key 外键名称
    修改默认值
        alter table 表名 alter 列名 set default 100;
    删除默认值
        alter table 表名 alter 列名 drop default;


```

##    数据类型

```
	数值
		bit[(M)]
			说明
				二进制位（101001），m表示二进制位的长度（1-64），默认m＝1
		tinyint[(m)]
			说明
				小整数
			数据类型用于保存一些范围的整数数值范围
				有符号
					-128 ～ 127
				无符号
					0 ～ 255


			数字1
			4字节 == 32位
	1000 0000  0000 0000  0000 0000  0000 0001  



			注意
				MySQL中无布尔值，使用tinyint(1)构造
		int[(m)]
			说明
				整数
			数据类型用于保存一些范围的整数数值范围
				有符号
					-2147483648 ～ 2147483647
				无符号
					0 ～ 4294967295
			注意
				整数类型中的m仅用于显示，对存储范围无限制。例如： int(5),当插入数据2时，select 时数据显示为： 00002
		bigint[(m)]
			说明
				大整数
			数据类型用于保存一些范围的整数数值范围
				有符号
					-9223372036854775808 ～ 9223372036854775807
				无符号
					0  ～  18446744073709551615
		decimal[(m[,d])]
			说明
				准确的小数值，m是数字总个数（负号不算），d是小数点后个数。 m最大值为65，d最大值为30
				decimal(5)  12345  1234.5  123.45
				decimal(5,2)  123.45
			注意
				对于精确数值计算时需要用此类型，decaimal能够存储精确值的原因在于其内部按照字符串存储
		FLOAT[(M,D)]
			说明
				单精度浮点数（非准确小数值），m是数字总个数，d是小数点后个数
			数据类型用于保存一些范围的整数数值范围
				有符号
					-3.402823466E+38 to -1.175494351E-38
					0
					1.175494351E-38 to 3.402823466E+38
				无符号
					0
					1.175494351E-38 to 3.402823466E+38
			注意
				数值越大，越不准确
		DOUBLE[(M,D)]
			说明
				双精度浮点数（非准确小数值），m是数字总个数，d是小数点后个数
			数据类型用于保存一些范围的整数数值范围
				有符号
					-1.7976931348623157E+308 to -2.2250738585072014E-308
					0
					2.2250738585072014E-308 to 1.7976931348623157E+308
				无符号
					0
					2.2250738585072014E-308 to 1.7976931348623157E+308
			说明
				数值越大，越不准确


		        单精度、双精度
		有效位：6~8位 、13~15位 
		3.1415926
		3.14150000000102302032043504
		3.14
		1.23



	字符串
		char(m)
			说明
				char数据类型用于表示固定长度的字符串，可以包含最多达255个字符。其中m代表字符串的长度
			注意
				即使数据小于m长度，也会占用m长度
			优点
				速度快
		varchar(m)
			说明
				varchar数据类型用于变长的字符串，可以包含最多达255个字符。其中m代表该数据类型所允许保存的字符串的最大长度，只要长度小于该最大值的字符串都可以被保存在该数据类型中
			注意
				虽然varchar使用起来较为灵活，但是从整个系统的性能角度来说，char数据类型的处理速度更快，有时甚至可以超出varchar处理速度的50%。因此，用户在设计数据库时应当综合考虑各方面的因素，以求达到最佳的平衡
				使用时将定长字段尽量写在前面，变长字段写在后面
			优点
				节省空间
		text
			说明
				text数据类型用于保存变长的大字符串，可以组多到65535 (2**16 − 1)个字符
			作用
				可用于文件上传，但是一般会将文件存磁盘，数据库存路径
		mediumtext
			说明
				A TEXT column with a maximum length of 16,777,215 (2**24 − 1) characters
		longtext
			说明
				A TEXT column with a maximum length of 4,294,967,295 or 4GB (2**32 − 1) characters
	时间
		DATE
			YYYY-MM-DD（1999-01-01）
		TIME
			HH:MM:SS（'24:59:59'）
		YEAR
			YYYY（1999）
		DATETIME
			YYYY-MM-DD HH:MM:SS（1999-01-01 00:00:00）
		TIMESTAMP
			YYYYMMDD HHMMSS（1970-01-01 00:00:00）
	其他
		enum
			枚举类型
		set
			集合类型
```



## auto_increment详解

```
作用：自增长
注意：对于自增长列，必须是索引(含主键)

原理：
    使用show create table 表名 \G 语句可以查看建表语句，第一次查看不到什么特殊情况，插入一条数据后在查看发现后面多了AUTO_INCREMENT=值，下次在插入数据时，表中的主键的值为刚才看到的AUTO_INCREMENT的值，并且AUTO_INCREMENT值按步长为1而递增。

    alter table 表名 AUTO_INCREMENT=值;
    alter table student AUTO_INCREMENT=5;



SQLit数据
基于表级别修改
create table student(
    id int not null auto_increment primary key,
    sex bit not null,
    age int default 20,
    sid char(20),
    name char(20),
    description varchar(100),
    birthday date,
    grade enum('python01','python02','python03'),
    hobby set('power','money','boy','girl'),
    unique uq_sid (sid)
) engine=innodb auto_increment=3 步长=值 default charset=utf8;



mysql
基于会话级别
1、自身会话
    show session variables like 'auto_inc%';
    修改步长
    set session auto_increment_increment=2;
    修改其实质，一般无需修改
    set session auto_increment_offset=1;  

2、全局会话
    show global variables like 'auto_inc%';
    set global auto_increment_increment=3;
    set global auto_increment_offset=1; 





```



## 主键（primary key）详解

```
作用：唯一约束标识数据库表中的每条记录
注意：
    主键必须包含唯一的值
    主键列不能包含null值
    每个表都应该有一个主键，并且每个表只能拥有一个主键
概念：一种特殊的唯一索引，不允许为空，如果主键使用单个列，则它的值必须唯一，如果是多个列，则其组合必须唯一


使用单个列
create table student(
    id int not null auto_increment primary key,
    name char(20)
) engine=innodb default charset=utf8;



使用多个列
create table student(
    nid int not null auto_increment,
    sid int not null,
    primary key(nid, sid),
    name char(20)
) engine=innodb default charset=utf8;
create table student(
    nid int not null,
    sid int not null,
    primary key(nid, sid),
    name char(20)
) engine=innodb default charset=utf8;
insert into student values(1,1,"tom");


```

## 唯一（unique）详解

```
作用：约束唯一标识数据库中表的每条数据
与primary key的区别：
    a、两者均为列或列集合提供了唯一性的保证
    b、pk拥有自动定义的unique约束
    c、每个表可以有多个unique约束，但是每个表只能有一个pk约束
使用：unique 唯一索引名称 (列名1[,……])
优点：
    1、加速查询
    2、唯一约束(可以为null)


基本使用：
create table student(
    id int not null auto_increment primary key,
    age int,
    sid char(20) unique,
    name char(20)
) engine=innodb default charset=utf8;
create table student(
    id int not null auto_increment primary key,
    age int,
    sid char(20),
    name char(20),
    unique uq_sid (sid)
) engine=innodb default charset=utf8;




思考：是否可以有多个唯一约束？
create table student(
    id int not null auto_increment primary key,
    age int,
    sid char(20) unique,
    pid char(20) unique,
    name char(20)
) engine=innodb default charset=utf8;
create table student(
    id int not null auto_increment primary key,
    age int,
    sid char(20),
    pid char(20),
    name char(20),
    unique uq_sid (sid),
    unique uq_pid (pid)
) engine=innodb default charset=utf8;
insert into student values(0, 18, 1, 1, 'tom1');
insert into student values(0, 18, 2, 2, 'tom2');
insert into student values(0, 18, 3, 4, 'tom3');
insert into student values(0, 18, 4, 3, 'tom4');
insert into student values(0, 18, 5, 5, 'tom5');
insert into student values(0, 18, 1, 6, 'tom5');


思考：unique 唯一标识名称 (列1[,列2[,……]])是否可以？？？
create table student2(
    id int not null auto_increment primary key,
    age int,
    sid char(20),
    pid char(20),
    name char(20),
    unique uq_sp (sid,pid)
) engine=innodb default charset=utf8;
insert into student2 values(0, 18, 1, 1, 'tom1');
insert into student2 values(0, 18, 2, 2, 'tom2');
insert into student2 values(0, 18, 3, 4, 'tom3');
insert into student2 values(0, 18, 4, 3, 'tom4');
insert into student2 values(0, 18, 5, 5, 'tom5');
insert into student2 values(0, 18, 1, 5, 'tom5');
注意：多条数据，只要sid和pid有一个不同即可(联合唯一)
```

## 外键（foreign key）详解

```
说明：一个表中fK指向另一个表中的pk
作用：
    a、用于用于预防破坏表之间的连接的动作
    b、也能防止非法数据插入外键列，因为它必须是它所指向的那个表中的值之一


为什么要使用外键？
    详情查看  1.png  2.png 3.png


基本代码：
create table grade(
    id int not null auto_increment primary key,
    title char(20)
) engine=innodb default charset=utf8;
create table student(
    id int not null auto_increment primary key,
    name char(20),
    grade_id int,
    constraint fk_student_grade foreign key (grade_id) references grade (id)
) engine=innodb default charset=utf8;

insert into grade values(0, "python01"),(0,"python02"),(0,"python03");
insert into student values(0, "tom1", 1);



外键约束两个字段：
create table grade(
    aid int not null,
    bid int not null,
    primary key(aid, bid),
    title char(20)
) engine=innodb default charset=utf8;
create table student(
    id int not null auto_increment primary key,
    name char(20),
    aaid int,
    bbid int,
    constraint fk_student_grade foreign key (aaid, bbid) references grade (aid, bid)
) engine=innodb default charset=utf8;




主表从表：声明关系的表示从表




一对多：外键在多的那一方
    学生表与班级表：
        学生：
            1   tom1   1
            2   tom2   1
            3   tom3   2
            4   tom4   3
        班级表：
            1   python01
            2   python02
            3   python03




一对一：外键在哪张表都行
    用户表和仓库表
    用户表：
        1   sunckgood
        2   suncknice
        3   sunckcool
        4   sunckhandsome
    仓库表：
                         外键+唯一
        1   sunckgood/    1
        2   suncknice/    2

    人与身份证
    人：
        1  tom1  
        2  tom2  
        3  tom3
        4  tom4
    身份证：
                外键+唯一
        1  100  1
        2  200  2
        3  300  3
        4  400  4
        5  500  4


    应用场景：表的字段太多，需要拆分

    id,name,height,weight,age,birthday,cardid,jiguan,sex

    用户表    身份证表


create table person(
    id int not null auto_increment primary key,
    name char(20)
) engine=innodb default charset=utf8;
create table card(
    id int not null auto_increment primary key,
    cardid char(20),
    person_id int,
    unique uq_per (person_id),
    constraint fk_card_person foreign key (person_id) references person (id)
) engine=innodb default charset=utf8;

insert into person values(0, 'tom1'),(0, 'tom2'),(0, 'tom3');
insert into card values(0, "100", 1);






多对多：
    原理：底层是通过两个外键实现，两个外键存在一张关系表中


user表
	id name
	1	fanding
	2	getong
	3	gaolei
host表
	id	ip
	1	100
	2	200	
	3	300
user2host表
	id user_id host_id
	1	1		1
	2	1		3
	3	2		1

user：
CREATE TABLE `user` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` char(20) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8


host：
CREATE TABLE `host` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `ip` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8


user2host：
CREATE TABLE `user2host` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `user_id` int(11) DEFAULT NULL,
  `host_id` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_uid_hid` (`user_id`,`host_id`),
  KEY `fk_user2host_host` (`host_id`),
  CONSTRAINT `fk_user2host_host` FOREIGN KEY (`host_id`) REFERENCES `host` (`id`),
  CONSTRAINT `fk_user2host_user` FOREIGN KEY (`user_id`) REFERENCES `user` (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8
```

## sql语句的增、删、改、查

### 增

```
1、全列插入
        insert into 表名 values(值1,值2,……);
        注意：主键是自增长，但是在全列插入式需要占位，插入成功后以实际值为准
        insert into student values(0, 18, 'sunck');
        insert into student values(0, 50, '刘德华');
        insert into student values(0, 40, '刀郎');
    2、缺省插入
        inset into 表名(列1,列2,……) values(值1,值2,……);
    3、同时插入多条数据
        insert into 表名 values(值1,值2,……),(值1,值2,……),……;
        insert into 表名(列1,列2,……) values(值1,值2,……),(值1,值2,……),……;

    将一张表的数据导入另一张表中
        t1(name, age)   t2(name, age)
        t2中有2条数据，t1中没有数，可以将t2表中的数据直接导入到t1表中
        insert into t1(name, age) select name,age from t2;

create table t1(
    id int not null auto_increment primary key,
    age int,
    name char(20)
) engine=innodb default charset=utf8;
create table t2(
    id int not null auto_increment primary key,
    age int,
    name char(20)
) engine=innodb default charset=utf8;
insert into t2(name, age) values("tom", 18),("lilei",20);

```

### 删

```
格式：
        根据条件删除某些数据：
            delete from 表名 where 条件;
        清空表：
            delete from 表名;
            truncate table 表名;

    示例：
        delete from t1 where id = 1;
        delete from t1 where id != 1;
        delete from t1 where id > 1;
        delete from t1 where id >= 1;
        delete from t1 where id >= 1 and id <= 5;
        delete from t1 where id < 4 or id > 5;

```

```
逻辑删除
    物理删除：将数数据从数据中删除。delete操作属于物理删除，物理删除的数据无法恢复，对于一些重要的数据，以后建议使用逻辑删除。
    逻辑删除：本质是修改(update)操作，对于重要数据表，增加一个isDelete字段，一般默认为0(没有被删除的的意思)，该字段逻辑上表示该条数据是否被删除，真实情况是在数据库中本条数据还存在
    create table student(
    id int not null auto_increment primary key,
    age int,
    name char(20),
    isDelete bit default 0
) engine=innodb default charset=utf8;

```

### 改

```
格式：
        根据条件具体修改某些数据：
            update 表名 set 列1=值1,…… where 条件;
        全部列修改：
            update 表名 set 列1=值1,……;



    示例：
        update t2 set age=18 where name='lilei';
```

### 查

```
1、查询全部
        select * from 表名;
        说明：
            a、from关键字后面写的表名，表示数据来源于这张表
            b、select后面写表中的列名，如果是*，表示结果中显示表中所有的列
            c、如果要查询多个列，列之间使用逗号分隔

2、条件查询
        select * from 表名 where 条件;
        a、比较运算符
            =    >    <    >=    <=    !=     <>
            select * from student where age > 30;
        b、逻辑运算符
            and    or    not
            select * from student where age > 20 and age < 30;
            select * from student where age < 20 or age > 30;
            select * from student where not age < 20;
        c、范围查询
            in：表示在一个非连续的范围内
            select * from student where id in(1,3,5);
            between...and...：表示在一个连续的范围内
            select * from student where id between 3 and 6;
        d、空判断
            is null：判空
            select * from student where sid is null;
            is not null：判非空
            select * from student where sid is not null;

            注意：null 与 ''(空字符)是不同的
        优先级：    
            小括号，not，比较运算符，逻辑运算符
            and比or优先运算，如果同时出现并希望先算or，需要结合小括号使用

  3、模糊查询
        使用 like
        %：表示任意多个字符
        _：表示一个任意字符
        select * from student where name like '高%';
        select * from student where name like '高_';

        select * from student where name like '高\%%';


  4、分页查询
        a、select * from 表名 limit [start,]count;
            start：从start开始获取，如果没有默认从0开始
            count：获取count条数据
        select * from student limit 0, 5;
        select * from student limit 5, 5;
        select * from student limit 10, 5;

        b、select * from 表名 limit count offset start;

        select * from student limit 5 offset 0;
        select * from student limit 5 offset 5;
        select * from student limit 5 offset 10;


 5、排序查询
        语法：select * from 表名 order by 列1 asc|desc[, 列2 asc|desc[,……]];
        说明：
            将行数据库按照列1进行排序，如果某些列1值相同时，则在按照列2进行排序，以此类推
            默认排序升序排序
            asc表示升序排序
            desc表示降序排序

        select * from student order by sid asc, age asc, id desc;

 6、聚合
        目的：为了快速得到统计数据
        count(*)：表示计算总行数，括号中写*与列名，结果相同
        max(列)：表示求此列的最大值
        min(列)：表示求此列的最小值
        sum(列)：表示此列的和
        avg(列)：表示求此列的平均值


        select count(*) from student where age = 34;
        select max(age) from student where name like'高%';
        select min(age) from student where name like'高%';
        select sum(age) from student where name like'高%';
        select avg(age) from student where name like'高%';
7、组合
        概述：
            a、按照字段分组，表示此字段相同的数据会被放到一个组中
            b、分组后，只能查询出相同的数据列，对于有差异的数据列无法出现在结果集中
            c、可以对分组后的数据进行统计，做聚合运算
        语法：
            select 列1,列2,……,聚合 from 表名 group by 列1,列2,……;

        示例：
            select * from student;
            select * from student group by grade_id;报错
            select grade_id from student group by grade_id;
            select grade_id,count(id) from student group by grade_id;


        分组后的数据筛选：
            需求：展示人数多于1的组信息

            #报错
            select grade_id,count(id) from student group by grade_id where count(id) > 1;

            使用having
                说明：如果对于聚合函数结果进行二次筛选时必须使用having
                语法：select 列1,列2,……,聚合 from 表名 group by 列1,列2,…… having 列1,……聚合……;
                示例：select grade_id,count(id) from student group by grade_id having count(id) > 1;

            having与where区别：
                a、where是对from后面指定的表进行数据筛选，对于原始数据的筛选
                b、having是对group by的结果进行筛选


 8、关联查询（连接查询）

        需求：显示所有学生，不仅显示班级id，也要把班级名称显示出来

        实现：
            select * from student,grade;#没有提供关系


            select * from student,grade where student.grade_id = grade.id;

            select grade_id,student.name,grade.name from student,grade where student.grade_id = grade.id;

   	关联分类：
         1、表A left join 表B
         表A与表B匹配的行会出现在结果集中，外加表A中独有的数据，未对应的数据使用null填充。(左边全部显示)
         2、表A right join 表B
                表A与表B匹配的行会出现在结果集中，外加表B中独有的数据，未对应的数据使用null填充。(右边全部显示)
         3、表A inner join 表B
                表A与表B匹配的行会出现在结果集中(将有null的行隐藏)


         select * from student left join grade on student.grade_id = grade.id;
         insert into student(name) values("sunck");
         insert into grade(name) values('python05');
         select * from student right join grade on student.grade_id = grade.id;
       #交换表位置模拟了右关联
        select * from grade left join student on student.grade_id = grade.id;
        select * from student inner join grade on student.grade_id = grade.id;
        说明：
            a、在查询或条件中推荐使用"表名.列名"的语法
            b、如果多个表中的列名不重复，可以省略"表名."的部分
            c、早起left与right存在性能上的差异，但是现在的mysql版本中已经没有差异了
        临时表：自己研究一下


```

## 备份表恢复表

```
转成SQL到文件

命令实现转成SQL到文件
    数据表结构+数据：
    mysqldump -u用户名 -p密码 数据库名 > 转储文件名
    数据表结构：
    mysqldump -u用户名 -p密码 -d 数据库名 > 转储文件名

    示例：
    mysqldump -usunck -psunck1999 axf > axf.sql
    mysqldump -usunck -psunck1999 -d axf > axf.sql

将转成文件导入数据库
    1、创建数据库
    2、导入
        mysql -u用户名 -p密码 数据库名 < 转储文件名

```

## 代码操作数据库

### 连接数据库

```
# -*- coding:utf-8 -*-

# 导入pymysql
import pymysql

# 连接数据库
# 参数1：mysql服务所在IP地址
# 参数2：用户名
# 参数3：用户密码
# 参数4：要连接的数据库
# 参数charset：显示汉字相关
db = pymysql.connect("www.sunck.wang", "sunck", "sunck1999", "axf", charset="utf8")

#创建cursor对象
cursor = db.cursor()

#待执行的SQL语句
sql = "select version();"

# 数据库的一些操作
# 执行SQL语句
cursor.execute(sql)

# 获取返回信息
data = cursor.fetchone()
print(data)

# 断开数据库连接
cursor.close()
db.close()

```

### 建表

```
# -*- coding:utf-8 -*-
import pymysql

db = pymysql.connect("www.sunck.wang", "sunck", "sunck1999", "axf", charset="utf8")
cursor = db.cursor()

# 建表之前首先判断表是否存在，存在则删除
sql1 = "drop table if exists student;"
sql2 = "create table student(id int not null auto_increment primary key,name char(20)) engine=innodb default charset=utf8;"


cursor.execute(sql1)
cursor.execute(sql2)



cursor.close()
db.close()
```

### 增

```
# -*- coding:utf-8 -*-
import pymysql

db = pymysql.connect("www.sunck.wang", "sunck", "sunck1999", "axf", charset="utf8")
cursor = db.cursor()

#待执行的SQL语句
sql = "insert into student values(0, 'lilei');"

try:
    cursor.execute(sql)
    # 提交事物，真正写入数据库
    db.commit()
except:
    # 如果提交失败，回滚到上次提交的数据
    db.rollback()

cursor.close()
db.close()
```

### 改

```
# -*- coding:utf-8 -*-
import pymysql

db = pymysql.connect("www.sunck.wang", "sunck", "sunck1999", "axf", charset="utf8")
cursor = db.cursor()

sql = "update student set name='hanmeimeaaai'"

try:
    cursor.execute(sql)
    db.commit()
    print("------------", cursor.rowcount)
except:
    db.rollback()



cursor.close()
db.close()
```

### 删

```
# -*- coding:utf-8 -*-
import pymysql

db = pymysql.connect("www.sunck.wang", "sunck", "sunck1999", "axf", charset="utf8")
cursor = db.cursor()

sql = "delete from student where id=1;"

try:
    cursor.execute(sql)
    db.commit()
except:
    pass

cursor.close()
db.close()
```

### 查

```
# -*- coding:utf-8 -*-
import pymysql


'''
fetchone()
功能：获取下一个查询结果集，结果集是一个对象

fetchall()
功能：接收全部的返回结果

rowcount
是一个只读属性，返回执行execute()方法后影响的行数
'''




db = pymysql.connect("www.sunck.wang", "sunck", "sunck1999", "axf", charset="utf8")
# cursor = db.cursor()
# 以字典形式显示
cursor = db.cursor(cursor=pymysql.cursors.DictCursor)

sql = "select * from student where id>=3;"

try:
    cursor.execute(sql)
    # 获取所有数据列表
    # reslist = cursor.fetchall()
    # print(reslist)
    # for row in reslist:
    #     print(row)



    # res = cursor.fetchone()
    # print(res)


    for i in range(cursor.rowcount):
        res = cursor.fetchone()
        print(res)

except:
    print("查询有误")


cursor.close()
db.close()
```

### sql注入

```
# -*- coding:utf-8 -*-
import pymysql

account = input("账号：")
passwd = input("密码：")


db = pymysql.connect("www.sunck.wang", "sunck", "sunck1999", "axf", charset="utf8")
cursor = db.cursor(cursor=pymysql.cursors.DictCursor)

# sql = "select * from user where account='%s' and passwd='%s';"%(account, passwd)
# select * from user where account='111' -- ' and passwd='';
# select * from user where account='aaa' or 1=1 -- ' and passwd='';

#防止SQL注入
# sql = "select * from user where account=%s and passwd=%s;"
sql = "select * from user where account=%(account)s and passwd=%(passwd)s;"

print(sql)

try:
    #execute为执行，格式化的数据在这里传值，以规避SQL注入
    # cursor.execute(sql, [account, passwd])
    cursor.execute(sql, {"account":account, "passwd":passwd})
    原理解释：
    	当参数传递进去后，传递的条件只是一个查询值，而没有任何语义，不会当做sql语句去执行。


    res = cursor.fetchall()
    if res:
        print("登陆成功", res)
    else:
        print("登陆失败")
except:
    print("查询有误")


cursor.close()
db.close()
```

### 增加多条数据

```
# -*- coding:utf-8 -*-
import pymysql

db = pymysql.connect("www.sunck.wang", "sunck", "sunck1999", "axf", charset="utf8")
cursor = db.cursor()

#待执行的SQL语句
sql = "insert into student(name) values(%s);"

try:
    cursor.executemany(sql, [("aaa",),("bbb",),("ccc",)])
    db.commit()
except:
    db.rollback()

cursor.close()
db.close()
```

### 新增数据的id获取

```
# -*- coding:utf-8 -*-
import pymysql

db = pymysql.connect("www.sunck.wang", "sunck", "sunck1999", "axf", charset="utf8")
cursor = db.cursor()

sql = "insert into article(title) values(%s);"

try:
    cursor.execute(sql, ["sunck"])

    # 插入对应的媒体，得直到刚才插入的文章的id号
    print("--------", cursor.lastrowid)

    db.commit()
except:
    db.rollback()

cursor.close()
db.close()
```

## 索引

```
一、作用：
    1、约束
    2、加速查找



二、分类：
    1、主键索引
        特点：最多有一个、不能为空、不能重复、加速查找
    2、普通索引
    3、唯一索引
        特点：可以有多个、不能重复、加速查找
    4、联合索引
        分类：联合主键索引、联合唯一索引、联合普通索引
    5、全文索引



三、为什么使用索引？
    快

    select * from student where name='tom40000';慢
    select * from student where id='10000';快

    小学时候使用字典
    
    无索引：从前到后依次遍历查找


四、原理：
    额外的文件保存特殊的数据结构

    注意：查询快，插入、更新、删除操作会变慢


五、索引算法种类
    1、btree索引
        名称：二叉树
        mysql默认使用的算法，效率高

    2、hash索引
        单值查询速度快，但是在文件中所以不是按照顺序排序的，所以范围查询时效率不会太高




六、创建索引
    1、主键索引
        不建议额外添加，在建表时已经创建
    2、全文索引
        作用：用于在一篇文章中，检索文本信息的
        说明：mysql从3.23.23版本开始支持全文索引，全文索引的类型为fulltext，可以创建在varchar或者text类型的字段身上。
        注意：一般不用mysql的，一般会基于其他框架实现
    3、普通索引
        格式：create index 索引名称 on 表名(列名);
        create index index_name on student(name);
        删除：drop index 索引名称 on 表名;

        索引合并：
            把多个单列索引合并使用
            假设：
                create index index_email on student(email);
                create index index_name on student(name);
            搜索：
                where name='';
                where email='';
                where name='' and email='';


    4、唯一索引
        格式：create unique index 索引名称 on 表名(列名);
        删除：drop unique index 索引名称 on 表名;

    5、联合索引
        a、联合唯一索引
            格式：create unique index 索引名称 on 表名(列名1,列名2,……);
            删除：drop unique index 索引名称 on 表名;
        b、联合普通索引
            格式：create index 索引名称 on 表名(列名1,列名2,……);
            删除：drop index 索引名称 on 表名;

        最左侧前缀匹配特性：
            假设：create index index_name_email_age on student(name, email, age);
            能使用到索引的情况：
                1、select * from student where name='tome40000';
                2、where name='tome40000' and email='11@qq.com';
                3、where name='tome40000' and age=5;
                4、where name='tome40000' and email='11@qq.com' and aeg=5;
            不走索引的情况：
                1、where email='11@qq.com';
                2、where age=5;
                3、where email='11@qq.com' and age=5;


    6、索引合并VS联合索引
        联合索引效率高于索引合并

    7、覆盖索引
        假设：create index index_name on student(name);

        使用：
            select * from student where name='tom42000';

            #直接在索引文件中获取信息，无需在去表中获取，这种行为就叫覆盖索引
            select name from student where name='tom42000';




七、索引的注意事项：
    1、频繁查找的列创建索引
    2、避免使用select *
    3、尽量使用count(1)或者count(列)替代count(*)，因为在有些数据中count(*)效率低，但是在现版本的mysql中不存在这个问题
    4、创建表是尽量使用char替换varchar
    5、表的字段顺序固定长度字段优先
    6、联合索引替代多个单列索引合并(经常使用多个条件查询时)
    7、尽量使用短索引
        1352345234@qq.com
        1352343333@qq.com
        1352555555@qq.com
        1352666666@qq.com
        1352777777@qq.com
        给字段类型为text类型添加索引必须使用端索引
        假设xxx字段为text类型
        create index index_xxx on table(xxx);报错
        create index index_xxx on table(xxx(5));xxx字段前五个字符为索引
    8、使用连接(join)替代子查询
    9、类型需要一致
    10、索引散列值重复少不适合建立索引
        性别不适合建立索引

 
八、命中索引
    给字段创建索引，并不是所有的情况都能使用到索引，索引要想生效需要命中索引。

    无法命中索引的请情况
        1、like 'xxx%'
            假设：create index index_name on student(name);
            select * from student where name like 'tom89%';
        2、使用函数
            select * from student where reverse(name)='tom12345';
        3、or
            or有时会导致无法命中索引
            假设：索引为id、name
            特别的：当or条件中有未建立索引的列才失效
            走索引：
                select * from student where id=444444;
                select * from student where sid=888888 or name='tom999998';
            不走索引：
                select * from student where sid=888888 or email='9753308846@qq.com';
            走索引：
                select * from student where sid=888888 or email='9753308846@qq.com' and name='tom880788';
        4、类型不一致
            如果列是字符串类型，传入条件必须使用''引起来
            假设：索引为id、name
            select * from student where name=999;
            注意：主键列不适用
        5、!=
            普通索引不走索引
                select * from student where name!='tom99999';
            注意：主键列不适用
        6、>
            普通索引不走索引
            注意：如果是主键或者索引类型是整数类型，还是会走索引
        7、order by
            当根据索引排序时，选择的映射如果不是索引，则不走索引
                不走：select email from student order by name desc;
                走：select name from student order by name desc;
            注意：如果对主键排序，还是会走索引的
                select * from student order by id desc;
        8、联合索引没有使用最左侧前缀
       
```

## 计划执行

### 介绍

```

作用：让mysql预估执行操作的时间(一般正确)

使用：explain SQL语句


字段：
    1、select_type
        查询类型
            simple   简单查询
            primary  最外层查询
            subquery 映射子查询
            derived  子查询
            union    联合查询
            union result  使用联合的结果
    2、table
        正在访问的表名

    3、type
        查询时的访问方式
        all
        index
        range
        index_range
        ref_or_null
        ref
        eq_ref
        const
        system

    4、 possible_keys
        可能使用的索引

    5、key
        真实使用的索引

    6、key_len
        mysql中使用索引字段的长度

    7、rows
        mysql估计为了找到所需要的行而读取的数据行数

    8、Extra
        包含mysql解决查询的详细信息
        Using index
        Using where
        Using temporary
        Using filesort
        Range checked for each recode

```

### extra字段

```
extra
	该列包含MySQL解决查询的详细信息
	Using index
		此值表示mysql将使用覆盖索引，以避免访问表。不要把覆盖索引和index访问类型弄混了
	Using where
		这意味着mysql服务器将在存储引擎检索行后再进行过滤，许多where条件里涉及索引中的列，当（并且如果）它读取索引时，就能被存储引擎检验，因此不是所有带where子句的查询都会显示“Using where”。有时“Using
	Using temporary
		这意味着mysql在对查询结果排序时会使用一个临时表
	Using filesort
		这意味着mysql会对结果使用一个外部索引排序，而不是按索引次序从表里读取行。mysql有两种文件排序算法，这两种排序方式都可以在内存或者磁盘上完成，explain不会告诉你mysql将使用哪一种文件排序，也不会告诉你排序会在内存里还是磁盘上完成
	Range checked for each record(index map: N)
		这个意味着没有好用的索引，新的索引将在联接的每一行上重新估算，N是显示在possible_keys列中索引的位图，并且是冗余的
```

### type字段

```
type
	查询时的访问方式
	all
		全表扫描，对于数据表从头到尾找一遍
		如果有limit限制，则找到之后就不在继续向下扫描
			select * from tb1 where email = 'seven@live.com'
			select * from tb1 where email = 'seven@live.com' limit 1;
				找到一个后就不再继续扫描
	index
		全索引扫描，对索引从头到尾找一遍
			select id from student;
	range
		对索引列进行范围查找
	index_merge
		合并索引，使用多个单列索引搜索
	ref_or_null
	ref
		根据索引查找一个或多个值
	eq_ref
		连接时使用primary key 或 unique类型
	const
		常量
		表最多有一个匹配行,因为仅有一行,在这行的列值可被优化器剩余部分认为是常数,const表很快,因为它们只读取一次
	system
		系统
		表仅有一行(=系统表)。这是const联接类型的一个特例
	性能
		all < index < range < index_merge < ref_or_null < ref < eq_ref < system/const
```



## 分页优化

```


select * from student limit 2000000,10;


解决方案：
    1、不让访问

    2、索引表中扫描
    select * from student where id in(select id from student limit 200000,10);

    3、记住当前页数据的最大id和最小id
        max_id  min_id
        a、只有上一页和下一页
            下一页：
                select * from student where id > max_id limit 10;
            上一页：
                select * from student where id < min_id order by id desc limit 10;


                       1010-1020     
        b、上一页  100  [101]  102  103  104  105  下一页
            目前在101，点击104
            select * from student where id in(select id from (select id from student where id > max_id limit 30) as T order by T.id desc limit 10);

            目前在104，点击101
```

## 视图

```


概念：给SQL起别名，方便以后使用，类似临时表


select * from student where id > 40000;

select * from (select * from student where id > 40000) where age > 4;
select * from (select * from student where id > 40000) where age > 20;
select * from (select * from student where id > 40000) where age > 50;


创建视图
    格式：create view 视图名称 as SQL;
    create view v1 as select * from student where id > 40000;

使用：
    select * from v1;


注意：视图虚拟存在

删除：drop view 视图名称;

修改：alter view 视图名称 as SQL;

注意：视图不常用，可读性不高
```

## 触发器

```

作用：当对某张表做增删改操作时，可以使用触发器自定义关联行为

注意：查询不会触发触发器

举例：在用户注册时，会在用户表中增加一条数据，同时也要在日志表中增加一条数据



解决例子中的问题
    1、程序级别解决，两条SQL语句顺序执行
    2、触发器解决，只需要再用户表中插入，而无需手动往日志表中添加数据


student grade

创建触发器：
    1、插入前
create trigger 触发器名 before insert on 表名 for each row
begin
    ……
end
    2、插入后
create trigger 触发器名 after insert on 表名 for each row
begin
    ……
end
    3、删除前
create trigger 触发器名 before delete on 表名 for each row
begin
    ……
end
    4、删除后
create trigger 触发器名 after delete on 表名 for each row
begin
    ……
end
    5、更新前
create trigger 触发器名 before update on 表名 for each row
begin
    ……
end
    6、更新后
create trigger 触发器名 after update on 表名 for each row
begin
    ……
end




create table grade(
    id int not null auto_increment primary key,
    name char(20)
) engine=innodb default charset=utf8;
create table teacher(
    id int not null auto_increment primary key,
    name char(20)
) engine=innodb default charset=utf8;



#如此创建会出现问题，结束字符问题
create trigger aaa after insert on grade for each row
begin
    insert into teacher(name) values("tom");
end



delimiter：修改结束字符
delimiter //
create trigger aaa after insert on grade for each row
begin
    insert into teacher(name) values("tom");
end //
delimiter ;



需求：插入一个班级后，插入的老师的名字与班级名相同
insert into grade(name) values("python03");

delimiter //
create trigger aaa after insert on grade for each row
begin
    insert into teacher(name) values(new.name);
end //
delimiter ;

注意：new表示新数据


需求：删除一个班级后，在插入一个老师，老师的名字为删除的班级的名字
delete from grade where id=1;

delimiter //
create trigger bbb after delete on grade for each row
begin
    insert into teacher(name) values(old.name);
end //
delimiter ;

注意：old表示老数据



```

## 函数

### 定义函数

```


内置函数：


自定义函数：

delimiter //
create function func3(
    a int,
    b int)
returns int
begin
    declare num int default 0;
    set num = a + b;
    return(num);
end //
delimiter ;

```

### 内置函数

```
https://dev.mysql.com/doc/refman/5.7/en/functions.html


内置函数
	select  curdate();
	CHAR_LENGTH(str)
		返回值为字符串str 的长度，长度的单位为字符。一个多字节字符算作一个单字符
		对于一个包含五个二字节字符集, LENGTH()返回值为 10, 而CHAR_LENGTH()的返回值为5
	CONCAT(str1,str2,...)
		字符串拼接
		如有任何一个参数为NULL ，则返回值为 NULL
	CONCAT_WS(separator,str1,str2,...)
		字符串拼接（自定义连接符）
		CONCAT_WS()不会忽略任何空字符串。 (然而会忽略所有的 NULL）
	CONV(N,from_base,to_base)
		进制转换
		例如
			SELECT CONV('a',16,2); 
			表示将 a 由16进制转换为2进制字符串表示
	FORMAT(X,D)
		将数字X 的格式写为'#,###,###.##',以四舍五入的方式保留小数点后 D 位， 并将结果以字符串的形式返回。若  D 为 0, 则返回结果不带有小数点，或不含小数部分
		例如
			SELECT FORMAT(12332.1,4);
			结果为： '12,332.1000'
	INSERT(str,pos,len,newstr)
		在str的指定位置插入字符串
		参数
			pos
				要替换位置其实位置
			len
				替换的长度
			newstr
				新字符串
		注意
			如果pos超过原字符串长度，则返回原字符串
			如果len超过原字符串长度，则由新字符串完全替换
	INSTR(str,substr)
		返回字符串 str 中子字符串的第一个出现位置
	LEFT(str,len)
		返回字符串str 从开始的len位置的子序列字符
	LOWER(str)
		变小写
	UPPER(str)
		变大写
	LTRIM(str)
		返回字符串 str ，其引导空格字符被删除
	RTRIM(str)
		返回字符串 str ，结尾空格字符被删去
	SUBSTRING(str,pos,len)
		获取字符串子序列
	LOCATE(substr,str,pos)
		获取子序列索引位置
	REPEAT(str,count)
		返回一个由重复的字符串str 组成的字符串，字符串str的数目等于count
		注意
			若 count <= 0,则返回一个空字符串
			若str 或 count 为 NULL，则返回 NULL
	REPLACE(str,from_str,to_str)
		返回字符串str 以及所有被字符串to_str替代的字符串from_str 
	REVERSE(str)
		返回字符串 str ，顺序和字符顺序相反
	RIGHT(str,len)
		从字符串str 开始，返回从后边开始len个字符组成的子序列
	SPACE(N)
		返回一个由N空格组成的字符串
	SUBSTRING(str,pos) SUBSTRING(str FROM pos) SUBSTRING(str,pos,len) SUBSTRING(str FROM pos FOR len)
		不带有len 参数的格式从字符串str返回一个子字符串，起始于位置 pos。带有len参数的格式从字符串str返回一个长度同len字符相同的子字符串，起始于位置 pos。 使用 FROM的格式为标准 SQL 语法。也可能对pos使用一个负值。假若这样，则子字符串的位置起始于字符串结尾的pos 字符，而不是字符串的开头位置。在以下格式的函数中可以对pos 使用一个负值
		示例
			SELECT SUBSTRING('Quadratically',5);
				'ratically'
			SELECT SUBSTRING('foobarbar' FROM 4);
				'barbar'
			SELECT SUBSTRING('Quadratically',5,6);
				'ratica'
			SELECT SUBSTRING('Sakila', -3);
				'ila'
			SELECT SUBSTRING('Sakila', -5, 3);
				'aki'
			SELECT SUBSTRING('Sakila' FROM -4 FOR 2);
				'ki'
	TRIM([{BOTH | LEADING | TRAILING} [remstr] FROM] str) TRIM(remstr FROM] str)
		返回字符串 str ， 其中所有remstr 前缀和/或后缀都已被删除。若分类符BOTH、LEADIN或TRAILING中没有一个是给定的,则假设为BOTH 。 remstr 为可选项，在未指定情况下，可删除空格
		示例
			SELECT TRIM('  bar   ');
				'bar'
			SELECT TRIM(LEADING 'x' FROM 'xxxbarxxx');
				'barxxx'
			SELECT TRIM(BOTH 'x' FROM 'xxxbarxxx');
				'bar'
			SELECT TRIM(TRAILING 'xyz' FROM 'barxxyz');
				'barx'
```



## 建表可扩展性（null字段的使用）

```


建议：以后在建表时额外增加几个无用(备用)的字段





create table student(
    id int not null auto_increment primary key,
    name char(20),
    grade_id int,
    constraint fk_student_grade foreign key(grade_id) references grade(id)
) engine=innodb default charset=utf8;
alter 增加一个money 字段



create table student(
    id int not null auto_increment primary key,
    name char(20),
    grade_id int,
    constraint fk_student_grade foreign key(grade_id) references grade(id),
    a int null, 
    b int null,
    c int null,
    d int null
) engine=innodb default charset=utf8; 
修改备用字段的名或类型，保证以前的数据该字段都有值


```

# NoSQL数据库

```
NoSQL简介
	概述
		NoSQL，全名为Not Only SQL，指的是非关系型的数据库
		随着访问量的上升，网站的数据库性能出现了问题，于是nosql被设计出来
	优点
		高可扩展性
		分布式计算   
		低成本   
		架构的灵活性，半结构化数据
		没有复杂的关系
	缺点
		没有标准化
		有限的查询功能（到目前为止）
		最终一致是不直观的程序
	分类
		列存储
			代表
				Hbase
				Cassandra
				Hypertable
			特点
				顾名思义，是按列存储数据的。最大的特点是方便存储结构化和半结构化数据，方便做数据压缩，对针对某一列或者某几列的查询有非常大的IO优势
		文档存储
			代表
				MongoDB
				CouchDB
			特点
				文档存储一般用类似json的格式存储，存储的内容是文档型的。这样也就有有机会对某些字段建立索引，实现关系数据库的某些功能
		key-value存储
			代表
				Tokyo Cabinet / Tyrant
				Berkeley DB
				MemcacheDB
				Redis
			特点
				可以通过key快速查询到其value。一般来说，存储不管value的格式，照单全收。（Redis包含了其他功能）
		图存储
			代表
				Neo4J
				FlockDB
			特点
				图形关系的最佳存储。使用传统关系数据库来解决的话性能低下，而且设计使用不方便
		对象存储
			代表
				db4o
				Versant
			特点
				通过类似面向对象语言的语法操作数据库，通过对象的方式存取数据
		xml数据库
			代表
				Berkeley DB XML
				BaseX
			特点
				高效的存储XML数据，并支持XML的内部查询语法，比如XQuery,Xpath
```



# MongoDB数据库

## MongoDB

```

一、什么是MongoDB？
    1、MongoDB是有C++语言编写的，是一个基于分布式文件存储的开源数据库系统，在高负载的情况下，添加更多节点，可以保证服务器的性能
    2、MongoDB为web应用提供了高性能的数据存储解决方案
    3、MongoDB将数据存储为一个文档，数据结构由(key->value)形式组层，MongoDB文档类似于json文件，字段值可以是其他文档，列表等

二、JSON文件
    存储数据的一种格式


    {}：代表字典
    []：列表
    ,：分隔两个部分
    :：键值对

{
    "code": 1,
    "totle": 3,
    "pers": [
        {
            "name":"tom1",
            "age":18
        },
        {
            "name":"tom2",
            "age":19            
        },
        {
            "name":"tom3",
            "age":17            
        }
    ]
}



三、特点
    1、MongoDB提供了一个面向文档存储，基本思路是将原来的“行”的概念换成了更加领过的“文档”模型，一条记录可以表示非常复杂的层次关系
    2、MongoDB支持丰富的查询表达式，查询指令是json形式的标记，可以轻易查询文档中嵌套的对象和列表
    3、非常容易扩展，扩展集群后还可以实现集群中的数据的负载均衡。
    4、MongoDB支持各种编程语言，比如python、Java、c++、c、php、c#、ruby、JavaScript等
    5、丰富的功能，包括索引、存储JavaScript、聚合、固定集合、文件存储等功能
    6、方便管理，处理启动数据库服务以外，记过没有其他什么必要的操作。管理集群只需要知道有哪个新增的节点即可，自动继承和配置新节点


```

## MongoDB的一些概念

```
一、与mysql术语的对比

二、与mysql数据结构的对比

三、数据库
    1、一个MongoDB中可以建立多个数据库
    2、MongoDB的单个示例可以容纳多个数据库，每一个都有自己的集合和权限，不同的数据库放在不同的文件中
    3、数据库通过名字来标识
        a、不能是空字符  
        b、不能含有   引号 空格 . $ / \ \0 
        c、全部小写
        d、最多64字节
    4、有一些数据库名是保留的，可以直接访问
        a、admin
            从权限的角度考虑，这是“root”数据库，要是将一个用户添加到这个数据库，这个用户自动继承所有数据库的权限，一些特定的数据库服务端的命令只有能从这个数据库运行，比如列出所有的数据库或者关闭服务
        b、local
            这个数据库永远不会被复制，用来存储仅限于本地单台服务器的一些集合
        c、config
            当MongoDB用于分片设置时，config数据库在内部使用，用于保存分片的相关数据

四、文档
    1、概念：
        文档是MongoDB中最核心的概念，是其核心单元，将文档类比成关系型数据库中的每一行数据
        多个键及其关联的值有序的放在一起就是文档，MongoDB使用了Bson数据结构来存储数据和网络数据交换
        BSON数据可以理解为在JSON的基础上添加了一些json没有的数据类型

    2、例子
        {"name":"tom","age":18,"hobby":["power","moey"]}

    3、文档的命名规范
        a、键不能还有\0
        b、键不能含有$
        c、以下划线开头的键都是保留的

    4、注意事项
        a、文档中的键值对是有序的
        b、文档中的值可以是列举的数据类型值，甚至是另一个文档
        c、MongoDB区分大小写和类型
        d、文档中的键不能重复
        e、文档中的键一般是字符串



        



五、集合
    类比mysql中的表，集合就是一组文档的组合
    在MongoDB中集合是无模式的，也就是说集合中存储的文档的结构可以不同
    {"name":"tom","age":18,"hobby":["power","moey"]}
    {"a":"tom","b":["power","moey"]}

    注意：当第一个文档插入式，集合就会被自动创建

    命名规则：
        1、集合名不能是字符串
        2、不能含有   引号 空格 . $ / \ \0 
        3、不能以“system.”开头，这是为系统集合保留的前缀
        4、集合的名字中不能含有保留字符
```

## MongoDB数据库操作

### 操作数据库

```
一、操作数据库：
    创建数据库：
        格式：use 数据库名
        注意：如果数据库不存在，则创建数据库，否则切断到指定数据库
    查看所有数据库：
        show dbs
        注意：如果刚刚创建的数据库不在列表内，并不代表没有创建，而是因为数据库中没有数据而不显示。如果要显示需要给数据库中插入一些数据

    查看当前使用的数据库：
        db 或者 db.getName()

    删除数据库：
        说明：当前正在使用哪个数据库则删除哪个数据库，db代表当前正在使用的数据库
        db.dropDatebase()

    断开链接：
        exit

    查看API：
        help
```

### 操作集合

```

二、操作集合
    查看当前数据库下的所有集合：
        show collections

    创建集合：
        1、db.createCollection("集合名称")
        2、db.集合名称.insert(文档)
        区别：第一种方法创建一个空集合，第二种方法创建一个空集合后并向集合中添加了一个文档

    删除集合：
        db.集合名称.dorp()

```

### 操作文档

#### 增

```
1、insert()
            db.集合名称.insert(文档)
                添加一个：db.student.insert({"name":"tom1","age":18})
                添加多个：db.student.insert([{"name":"tom2","age":22},{"name":"tom3","age":25}])
        2、save()
            db.集合名称.save(文档)
                db.student.save({"name":"tom5","age":30})
                注意：如果不指定_id字段save()方法类似于insert()方法，如果指定_id字段，则会更新该_id字段的数据库
                    db.student.save({"_id":ObjectId("5b864efc8ad03c4c28e530ea"),"name":"tom2","age":10})
```

#### 删

```
remove()
            db.集合名称.remove(
                <query>,
                {
                    justOne:<boolean>,
                    writeConcern:<document>
                }
            )
            参数说明：
                query：可选，删除的文档的条件
                justOne：可选，如果为ture，则只删除一个文档
                writeConcern：可选，抛出异常的级别

            示例： 
                db.student.remove({"_id":ObjectId("5b864efc8ad03c4c28e530ea")})
```

#### 改

```
1、update()：用于更新已经存在的文档
            db.集合名称.update(
                <query>,
                <update>,
                {
                    upset:<boolean>,
                    multi:<boolean>,
                    writeConcern:<document>
                }
            )


            参数说明：
                query：update的查询条件，类似mysql中update后面的where后面的条件语句
                update：一些跟新的操作，$set表示设置、$inc表示叠加
                upset：可选参数，如果不存在update的记录，是否插入该数据，true为插入，默认为false不插入
                multi：可选，默认为false，只更新找到的第一条数据，如果为true，则更新所有匹配的文档
                writeConcern：可选，抛出异常的级别
            
            

            示例：
            db.student.update({name:"tom3"},{$set:{age:8}})

            db.student.update({name:"tom3"},{$set:{age:7}},{multi:true})

            db.student.update({name:"tom1"},{$inc:{age:2}})



        2、save()：通过传入的文档替换已有的文档
            db.集合名称.save(
                <document>,
                {
                    writeConcern:<document>
                }
            )
            参数说明：
                document：文档数据
                writeConcern：可选，抛出异常的级别

```

#### 查

```
查询文档：
            find()
                db.集合名称.find()
                    查询集合中的所有文档数据
                    db.student.find()

                db.集合名称.find(
                    {
                        queryWhere
                    },
                    {
                        key1:1,
                        key2:1,
                        ……
                    }
                )
                    参数说明：
                        queryWhere：查询条件
                        key：要显示字段，1表示显示
                    示例：
                        db.student.find({name:"tom3"})
                        db.student.find({name:"tom3"},{age:1})

            pretty()
                以格式化的方式来显示所有文档
                db.student.find().pretty()

            findOne()
                匹配结构的第一条数据
                db.student.findOne({name:"tom3"})



        db.student.insert([{"name":"tom6","age":26},{"name":"tom7","age":35},{"name":"tom8","age":40},{"name":"tom9","age":44},{"name":"tom10","age":65},{"name":"tom11","age":15},{"name":"tom12","age":32},{"name":"tom13","age":46},{"name":"tom14","age":79},{"name":"tom15","age":66},{"name":"tom16","age":8}])
        查询条件操作符：
            
            >      $gt
            >=     $gte
            <      $lt
            <=     $lte
            db.集合名称.find({key:{操作符:值}})
            db.student.find({age:{$gt:30}})

            联合使用 >= 与 <=
            db.student.find({age:{$gte:30, $lte:50}})

            ==   
            db.集合名称.find({key:值})

            使用_id进行查询
            db.集合名称.find({"_id":ObjectId("id值")})

            查询某个结果集的数据条数
            db.student.find({age:{$gt:30}}).count()

            查询某个字段中是否包含另一个值
            db.集合名称.find({key:/value/})
            db.student.find({name:/aaa/})

            查询某个字段是否是以另一个值开头
            db.集合名称.find({key:/^value/})
            db.student.find({name:/^tom/})

        查询条件and和or：
            and：
                find()中出入多个键，每个键以逗号分隔
                db.student.find({name:"tom3",age:7})
            or：
                db.集合名称.find(
                    {
                        $or:[
                            {key1:value1},
                            {key2:value2},
                            ……
                        ]
                    }  
                )
                db.student.find({$or:[{age:20},{age:30}]})
                db.student.find({$or:[{age:{$lte:20}},{age:{$gte:30}}]})


            and与or联合使用：
                db.集合名称.find({
                    key1:value1,
                    key2:value,
                    $or:[
                        {key1:value1},
                        {key2:value2},
                    ]
                })

                需求：年龄小于等于20或者大于等于30且名字以tom开头
                db.student.find({name:/^tom/,$or:[{age:{$lte:20}},{age:{$gte:30}}]})

        limit和skip：
            limit()：读取指定数量的记录
                db.student.find().limit(5)

            skip()：跳过指定数量的数据
                db.student.find().skip(5)

            分页：
                db.student.find().skip(5).limit(5)

        排序：
            db.集合名称.find().sort({key:1})
            参数key：排序的字段，1表示升序排序，-1表示降序
            db.student.find().sort({age:1})

```

## pymongo模块的使用

### 增

```
# -*- coding:utf-8 -*-

from pymongo import MongoClient

#链接服务器
conn = MongoClient("www.sunck.wang", 27017)
#链接数据库
db = conn.axf
#获取集合
collection = db.student


collection.insert([{"name":"lilei","age":12},{"name":"hanmeimei","age":11}])


#断开链接
conn.close()
```

### 改

```
# -*- coding:utf-8 -*-

from pymongo import MongoClient

#链接服务器
conn = MongoClient("www.sunck.wang", 27017)
#链接数据库
db = conn.axf
#获取集合
collection = db.student


collection.update({"name":"lilei"},{"$set":{"age":20}})


#断开链接
conn.close()
```

### 删

```
# -*- coding:utf-8 -*-

from pymongo import MongoClient

#链接服务器
conn = MongoClient("www.sunck.wang", 27017)
#链接数据库
db = conn.axf
#获取集合
collection = db.student


collection.remove({"name":"lilei"})


#断开链接
conn.close()
```

### 查

```
# -*- coding:utf-8 -*-

from pymongo import MongoClient
import pymongo
from bson.objectid import ObjectId

#链接服务器
conn = MongoClient("www.sunck.wang", 27017)
#链接数据库
db = conn.axf
#获取集合
collection = db.student



# 查询所有
# res = collection.find()
# print(res)
# print(type(res))
# for stu in res:
#     print(stu, type(stu))


#查询部分
# res = collection.find({"age":{"$gt":40}})
# for stu in res:
#     print(stu)


#统计查询
# print(collection.find({"age":{"$gt":40}}).count())


#排序
# res = collection.find().sort("age", pymongo.DESCENDING)
# for stu in res:
#     print(stu)


# 分页相关
# res = collection.find().limit(5)
# for stu in res:
#     print(stu)



# _id查询
print(collection.find_one({"_id":ObjectId('5b865c3b8ad03c4c28e530ee')}))




#断开链接
conn.close()
```

# redis数据库

## 安装

```

```

## 使用

