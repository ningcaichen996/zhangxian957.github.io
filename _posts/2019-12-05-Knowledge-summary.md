对知识点进行系统的总结，通俗易懂易记。

#### 							知识总结

#####1、网页中的字体图标，阿里字体图标三种用法。

~~~
	<第一种> 原始应用
	1、在阿里图标项目下载解压
    2、导入项目
    		(1)在 style里面 定义
				先@font-face{
					font-family: 自定义家族名'小张';
					src: url(字体文件地址)
				}
				再 定义标签 比如：
				p{
					font-family: 'xiaozhang'
					样式当字体设置
				}
~~~

		<第二种> 原始加强版 两步
	
		1、  第一步：引入项目下面生成的 fontclass 代码：
			<link rel="stylesheet" href="./iconfont.css">
	
		2、  第二步：挑选相应图标并获取类名，应用于页面：
			<span class="iconfont icon-xxx"></span>
		<第三种> 彩色版 也是现在网站通用的  三步
	
		1、	第一步：导入JS文件
			<script src="./iconfont.js"></script>
	
		2、第二步挑选图标	
			<svg class="icon" aria-hidden="true">
				<use xlink:href="#icon-xxx"></use>
			</svg>
		3、第三步可以改图标的样式
			<style>
				.icon {
				  width: 1em;
				  height: 1em;
				  vertical-align: -0.15em;
				  fill: currentColor;
				  overflow: hidden;
				}
			</style>


##### 2、form表单提交的属性设置

~~~
1. form
		action 	将表单提交给服务器  
				服务器以 name => value 形式接收
			
		method 	将表单以什么样的方式进行提交
			get
				明文传输, 默认 		值会显示在地址栏中
				安全性低
				速度快
				传输大小 http协议理论上无限制
							实际上, 受到浏览器的限制 < 2KB
				查询

			post
				密文传输
				安全性高
				速度慢
				传输大小 http协议理论上无限制
				实际上, 受到服务器性能限制
				增删改

2. 文件上传三要素		PHP文件接收时,用$_FILES接收
   1)file表单的name必须写		
   2)method="post"		
   3)enctype="multipart/form-data"
   
3. form表单input属性
	关于input的属性
	
	name 		给表单取个名, 必须写. 如果不写, 服务器接收不到
	value 		给表单一个默认值
				可手动输入  : value可写可不写
				不可手动输入: value 必须写
	type		
		不写 		默认文本域 	可随意输入
	text 		文本域
	password	密码
	file 		文件上传	   #见表单上传三要素
	email 		邮箱			简单验证
	date 		日期
	url 		网址 			 简单验证  协议+域名
	search 		搜索			 与text区别就是输入时后面有个x,可以清楚前面错误的。
	radio 		单选 			 需要保证name一致   
	checkbox 	多选  		 需要保证name[]一致，能多选					
	hidden 		隐藏域          通常用来传ID
	
	textarea 	文本域		   写name就好
	<textarea name="text" cols="30" rows="10"></textarea>
	
	select		文本域		   select写name="xiala",
							如果有multiple(多选下拉)则以数组形式name="xiala[]"
							option要写value
	<select name="xiala[]" multiple>
		<option value="China">中国</option>
		<option value="America">美国</option>
	</select>
			
	submit 		提交给form的action属性
~~~

##### 3、HTML页面初始化

~~~
1. 初始化目的：兼容各大浏览器，重新统一定义默认值。
   [初始化][https://blog.csdn.net/kiss377052/article/details/78742097]
   
各大主流网站css代码初始化
/* 腾讯 */

body,ol,ul,h1,h2,h3,h4,h5,h6,p,th,td,dl,dd,form,fieldset,legend,input,textarea,select{margin:0;padding:0} 
body{font:12px"宋体","Arial Narrow",HELVETICA;background:#fff;-webkit-text-size-adjust:100%;} 
a{color:#2d374b;text-decoration:none} 
a:hover{color:#cd0200;text-decoration:underline} 
em{font-style:normal} 
li{list-style:none} 
img{border:0;vertical-align:middle} 
table{border-collapse:collapse;border-spacing:0} 
p{word-wrap:break-word}

/* 新浪 */

body,ul,ol,li,p,h1,h2,h3,h4,h5,h6,form,fieldset,table,td,img,div{margin:0;padding:0;border:0;} 
body{background:#fff;color:#333;font-size:12px; margin-top:5px;font-family:"SimSun","宋体","Arial Narrow";} 
 
ul,ol{list-style-type:none;} 
select,input,img,select{vertical-align:middle;} 
 
a{text-decoration:none;} 
a:link{color:#009;} 
a:visited{color:#800080;} 
a:hover,a:active,a:focus{color:#c00;text-decoration:underline;}

/* 网易 */

html {overflow-y:scroll;} 
body {margin:0; padding:29px00; font:12px"\5B8B\4F53",sans-serif;background:#ffffff;} 
div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,form,fieldset,input,textarea,blockquote,p{padding:0; margin:0;} 
table,td,tr,th{font-size:12px;} 
li{list-style-type:none;} 
img{vertical-align:top;border:0;} 
ol,ul {list-style:none;} 
h1,h2,h3,h4,h5,h6{font-size:12px; font-weight:normal;} 
address,cite,code,em,th {font-weight:normal; font-style:normal;}

/* 淘宝 */

body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; } 
body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; } 
h1, h2, h3, h4, h5, h6{ font-size:100%; } 
address, cite, dfn, em, var { font-style:normal; } 
code, kbd, pre, samp { font-family:couriernew, courier, monospace; } 
small{ font-size:12px; } 
ul, ol { list-style:none; } 
a { text-decoration:none; } 
a:hover { text-decoration:underline; } 
sup { vertical-align:text-top; } 
sub{ vertical-align:text-bottom; } 
legend { color:#000; } 
fieldset, img { border:0; } 
button, input, select, textarea { font-size:100%; } 
table { border-collapse:collapse; border-spacing:0; }
~~~

4、sublime 快捷键使用以及设置

~~~
	1. **注释
		Ctrl + ?     注释单行。
		Ctrl+Shift+/ 注释多行。

	2. **排版键
	    Tab  			向后推 
		Shift + Tab		向前推 

	3. **上下移动
		Ctrl + Shift + 方向键

	4. 单词整体选中
		Ctrl + D

	5. 多选光标
		Ctrl + Alt + 方向键

	6. **全部替换
		6.1 搜索 Ctrl + F
		6.2 按住 Alt + Enter

	7. 重复一行
		Ctrl + Shift + D 

	8. 剪切   当删除用

	9. 撤销
		Ctrl + Z 

	10. 反撤销
		Ctrl + Y 

	11. 新建文件
		Ctrl + N

	12. 多窗口
		Alt + Shift + num数字
	
	13. **从光标处开始删除代码至行尾
		Ctrl+K+K 
	
	14. **将多行代码合并为一行 (常用作css的多行合并)
		Ctrl+J
~~~

##### 5、函数知识点的总结

~~~
1.什么是函数？
  函数是将一堆东西组合成一个完整的功能。
2.函数的分类和形式
  分类: 系统函数和自定义函数.
  	   系统函数有：时间、字符串、数组、文件、时间、数据库。。。
  	   自定义函 function  函数名()
  	   			{
                    
  	   			}
  	   		   调用：函数名();
3.1 函数特点
  1)函数不调用不执行
  2)函数在调用时，位置不影响
  3)函数可以互相调用，互不影响
  4)函数在未调用时，语法正常解析
  5)函数名不区分大小写
  
3.2 函数的命名规范
  1)函数以数字、字母、下划线命名或组成命名，但是不能以数字开头(需要函数有意义)
  2)函数名命名的几种方式
  	驼峰命名法：	 ningCaiChen
  	帕斯卡命名法： NingCaiChen
  	下划线隔开：   ning_cai_chen
4. return 函数的返回值
   返回值类型：任意的类型
   特点：return时函数立刻结束，并返回到调用函数的地方。
   场景：1、如果没有return返回，强行用变量接收，则接收的值为null
   		2、如何返回多个变量,放在数组中返回 return[$a,$b,$c];
5. 函数的形参、实参
   5.1
   形参(param)  定义函数时候的参数
   实参(arg)	  调用函数时候的参数
   function zhang($a,$b)
   {
       
   }
   zhang($x,$y);
   
   形参与实参个数比较
   形参个数 = 实参个数	完美
   形参个数 < 实参个数	多余的实参被抛弃
   形参个数 > 实参个数	多余的形参当成未定义的变量,也可以给默认值
   function zhang($a=10,$b=20)
   
   5.2 操作实参的函数
   func_get_args()	获取所有的实参，并以数组形式接收
   func_get_arg(n) 	获取下表为n的实参
   func_num_args()  获取实参的总个数

6. 变量的作用域
   全局变量不能在局部用调用，局部变量也不能在全局中调用
   如果非要,*都是在局部中定义
   1)全局在局部中调用,$GOLBALS 超全局数组，用于存储所有的全局变量
   $a = 10;
   function zhang()
   {
       echo $GLOBALS['a'];
   }
   zhang();
   
   2)局部变量在全局中使用,global
   function zhang()
   {
   	   global $b;
       $b = '小张';
   }
   zhang();
   echo $a
   
7.常量：值是恒定不变的const、define
  常量特点？
  1)不能从新赋值
  2)不能从新定义
  3)严格区分大小写，推荐大写*
  4)常量对函数没有作用域
  5)在函数内定义常量，用define,不用const
  const NAME = '小张';
  define('XING','zhang',true);  true不区分大小写  false区分

8.静态变量 static 特殊的**局部**变量
  1)普通函数在结束时都会摧毁变量，而静态变量在结束时不会被摧毁。
  2)不同函数的同名静态变量互不影响。
  function sta()
  {
      static $a = 10;
  }
  sta();
  
  function sta2()
  {
      static $a = 20;
  }
  sta2();
  
~~~

##### 6、魔术方法: 当触发某些条件时, 就会自动调用

~~~
(1)构造方法：construct 
	// 1. 当实例化一个类时，会自动调用；用于初始化
	// 2. 实例化类时给的参数，由构造方接收
	// 3. 一个类中只能有一个构造方法
	// 4. 写在类的属性最后面方法最前面.

(2)方法名与类名相同时，实例化时自动调用.(前提是没有构造)
~~~

##### 7、3种连接数据库的方法

​      ![数据库连接](assets/conMS.png)

      ##### 	**推荐使用mysqli(面向对象)和PDO，1. 两者都是面向对象，且都支持预处理语句防sql注入。

##### 	**MySQLi ：MySQLi 只针对 MySQL 数据库，MySQLi 还提供了 API 接口。**

		##### 	**PDO (PHP Data Objects)：PDO 应用在 12 种不同数据库中。**

​	

 	##### 		**(1) 第一种**最简单的方式-mysql（面向过程） 

~~~

 	 注意：原来是从PHP5.0开始就不推荐使用mysql_connect()函数，到了php7.0则直接废弃了该函数，替代的函数		是：$con=mysqli_connect("localhost","my_user","my_password","my_db");也就是mysqli
<?php
    $con = mysql_connect("数据库连接地址","数据库用户名","数据库管理密码");
    $select_db = mysql_select_db('数据库名称');
    if (!$select_db) {
        die("could not connect to the db:\n" .  mysql_error());
    }
    //查询代码
    $sql = "select * from table";
    $res = mysql_query($sql);
    if (!$res) {
        die("could get the res:\n" . mysql_error());
    }
    while ($row = mysql_fetch_assoc($res)) {
        print_r($row);
    }
    //关闭MySQL数据库连接
    mysql_close($con);
?>
 
~~~

	##### 	**(2-1) 第二种**新的方式-mysqli（面向过程） 

~~~
	$my_server = '127.0.0.1';
		$my_datas = 'lo';
		$my_name = 'root';
		$my_pwd = '123456';

	// 连接数据库
		$conn = mysqli_connect($my_server, $my_name, $my_pwd, $my_datas);

	// 连接错误提示
		if ( !$conn ){
			die("数据库连接失败：".mysqli_connect_errno());
		}else {
			echo '数据库连接成功！<br>';
		}

	// 数据库编码格式
		mysqli_query($conn, "set names utf8");
	   或mysqli_set_charset($conn,'UTF-8');

	// 查询代码
	    $sql = "SELECT * FROM `user` WHERE `id` = 10";

	// 执行sql代码
	    $result = mysqli_query($conn, $sql);

	 // 解析数据(查询数据时候需要用到解析)
	 	$row = mysqli_fetch_array($result, MYSQLI_ASSOC);
		// 默认两种数字、关联都有
		// 数字数组 MYSQLI_NUM
		// 关联数组 MYSQLI_ASSOC
		// $row = mysqli_fetch_array($query, MYSQLI_ASSOC);
	    // mysqli_fetch_row() 相当于 数字数组
		
		**这里是查询的判断
		if ( $result  ){
			 // 一行行获取
    		while ( $row=mysqli_fetch_array($result, MYSQLI_ASSOC) )
    		{
        		var_dump($row);
    		}
  	
		    // 释放结果集
		    mysqli_free_result($result);
		}
		
		**这里是增删改的判断
		   	// 	if ($result) {
		   	// 		echo '数据修改成功喽';
		   	// 	} else {
		   	// 		echo '对不起，失败！';
		   	// 	}
		
		// 关闭数据库连接
  		mysqli_close($conn);
~~~

##### 		**(2-2) 第二种新的方式-mysqli（面向对象)**

~~~
	// 1. 连接数据库
	$conn = new mysqli('localhost', 'root', '123456', 'lo');
    
    // 2. 判断是否连接成功
	if ($conn->connect_errno) {
		var_dump("数据库连接失败：<br>".$conn->connect_error);
		exit();
	} else {
		echo "数据库连接成功啦！<br>";
	}
	
	$conn->set_charset('utf8'); // 设置数据库字符集

	// 3. 查询数据库
	$sql = " SELECT * FROM `user`";
	$result = $conn->query($sql);
	
	*****
	// 数据库增删改
	$sql = " INSERT INTO `user` (`nickname`, `pwd`) VALUES ('张贤', '666')" ;
	$result = $conn->query($sql);

	if ($result) {
		echo '添加成功';
	} else {
		echo '添加失败';
	}
	*****
	
	// 数字数组 MYSQLI_NUM
	// 关联数组 MYSQLI_ASSOC
	// 4. 打印所有数据
	// while($row = $result->fetch_array(MYSQLI_NUM)){
 	//        var_dump($row);
 	//    }
~~~

##### 	**(3)数据库抽象层PDO**

~~~
	// 数据库抽象层 PDO

	// 1. 链接数据库 
		$pdo = new PDO( 'mysql:host=localhost;dbname=s81;charset=utf8', 'root', '');

	
	// 2. 查询所有的用户
		$sql = 'select * from `user` ';
		
		// query() 	执行一条sql, 返回 成功:PDOStatement对象, 适合查
		// 							 失败:false 
		// 
		// exec()   执行一条sql, 返回 成功:受影响的行数, 适合增删改
		// 							 失败:false
		// 	
		// 
		// 
		$pdoStatement = $pdo->query($sql);

		

		// PDOStatement的方法
		// fetch() 		解析出一条数据, 以一维数组形式返回
		// fetchAll() 	解析出全部数据, 以二维数组形式返回
		// 			PDO::FETCH_ASSOC 	关联数组
		// 			PDO::FETCH_NUM	 	索引数组
		// 			PDO::FETCH_BOTH	 	混合数组, 默认

		// $res = $pdoStatement->fetch();
		// $res = $pdoStatement->fetch();
		// $res = $pdoStatement->fetch();
		// $res = $pdoStatement->fetch();
		// $res = $pdoStatement->fetch();
		// $res = $pdoStatement->fetch();
		// $res = $pdoStatement->fetch();
		// $res = $pdoStatement->fetch();
		// $res = $pdoStatement->fetch(); 	# 返回结果为 false时, 已经没有数据了
		// $res = $pdoStatement->fetchAll();
		$res = $pdoStatement->fetchAll(PDO::FETCH_ASSOC);
		// $res = $pdoStatement->fetchAll(PDO::FETCH_NUM);
		// $res = $pdoStatement->fetchAll(PDO::FETCH_BOTH);

		// var_dump($res);


	// 新增一个用户
	// 在MySQL中, 能不用函数, 尽量不要用函数
		// $pwd = MD5('123456');
		// $name = '小范';
		// $tel = '15000000000';
		// $sex = 1;
		// $address = '东厂';
		// $sql = "insert into  `user`(`name`,`pwd`,`tel`,`sex`,`address`)  values('{$name}','{$pwd}','{$tel}','{$sex}','{$address}') ";


	// 执行sql
		// $res = $pdo->exec($sql);
		// var_dump($res);
~~~



##### **8、MYSQL数据库的操作**

#####**8.1 模糊查询**

~~~
PDO连接方法：

(1) 连接数据库(带异常处理)
   try{
          // 1.连接数据库
          $pdo = new PDO('mysql:host=localhost;dbname=tp5;charset=utf8', 'root', '123456');
          echo '数据库连接成功！';
      }catch(PDOException $e){
          die('操作失败 '.$e->getMessage());
          # getMessage() 获取错误信息
          # getFile() 获取错误文件路径
          # getLine() 获取错误行号
          # getCode() 获取错误码
      }
      
 (2) 模糊sql语句  
 	$sql = "SELECT `id`,`name`,`hobby` FROM `user` WHERE `hobby` LIKE '%$content%'";
 
 (3) 执行sql语句 query() exec()
 	$pdoStatement = $pdo->query($sql);
 	
 (4) 解析数据
 	#解析出一条数据, 以一维数组形式返回
 	 $res = $pdoStatement->fetch();
	#解析出全部数据, 以二维数组形式返回
    //	PDO::FETCH_ASSOC 	关联数组
	//	PDO::FETCH_NUM	 	索引数组
	//	PDO::FETCH_BOTH	 	混合数组, 默认	
	$res = $pdoStatement->fetchAll(PDO::FETCH_ASSOC);
    
~~~

##### **9.Ajax**

​	(1) 客户端： 浏览器、软件、终端工具(命令行)、Ajax(一段代码脚本)都属于客户端。

​	(2) Ajax是什么？Ajax是用JavaScript写在HTML里面的一段脚本。

​	(3) 之前要访问另外一个页面，都是生成UR`L地址跳转；Ajax是将URL地址交给Ajax脚本，由Ajax代

​	     替地址。

​	(4)	 客户端访问服务器，静态资源则交给WEB服务器可以发送文字、图片、音频、视频、HTML文		

​		 件等等。若访问的是PHP文件，则WEB服务器提交给PHP解释器，涉及到数据库还将经过数据

​		库服务器。	 

​		 web服务器返回的是HTML文件。

​		![客户端和服务器交互](./AJAX/1.png)

​	(5) 同步和异步概念

​		同步：客户端向服务器发出请求，一直等到等待服务器的响应才能进行下一次请求。

​		异步：客户端向服务器发出请求，不用等到服务器的响应就可以发出下一次请求，并且监听

​		上次的请求。

​	(6) XMLHttpRequest(XML)对象

​						语法								功能

​		方法： 	open('请求类型', '请求URL', '交互方式')		设置请求参数

​				![open](./AJAX/open.png)

​				send('请求数据')							发送URL请求

![](./AJAX/send.png)

​				setRequestHeader('请求头信息')			设置请求头，适用于POST请求

​		属性：	onreadystatechange						接受事件回调用

![](./AJAX/on.png)

​				readyState								请求状态码

![](./AJAX/status.png	)

​				status									响应状态码

​				responseText							响应返回的纯文本

​				responseXML							响应返回的XML/HTML对象



​	(7) Ajax脚本的结构

​		1、创建Ajax对象；

​		2、设置onreadystatechange事件回调，狐狸响应返回的数据；

​		3、初始化一个请求：执行xhr的open()方法;

​		4、设置请求头信息(可选);

​		5、发送请求：send(null);

​	(8)ajax的json_encode解决json返回中文乱码问题

​		echo json_encode("小张" , JSON_UNESCAPED_UNICODE);

​	(9)ajax输出后来返回数据到指定位置页面老是刷新，和控制台输出没有数据

​		原因：form表单提交的用的是<input id="" name ="" type="submit" value="提交"

​		关键点就是那么type,将type改成button

​	(10) Ajaxget请求：两个，get无无参数，get有参数

​	(11)Ajaxpost请求：

​		1.post请求在第3和4步之间需要加个请求头信息

​		xhr.setRequestHeader('content-type', 'application/x-www-form-urlencoded');

​		2.将url地址放open里，不带参数，参数在send()方法里面传过去。

##### **10. json转中文**

​	json_encode($arr, JSON_UNESCAPED_UNICODE);

##### **11. die exit continue break return用法**

​	die 和 exit结束其后面所以程序, 且终止结束时还可以致命一击(说一句话)

​	die('程序结束');	exit('我也结束');

​	return 结束其后面的程序，放函数里面结束函数运行还有返回值;但是不会结束函数后面的程序

​	continue 结束当前一轮循环(仅是当前一轮)

​	break 结束当前循环或者分支(当前循环里面的全部结束)



####**PDO、预处理(防SQL注入)、mysql事物、命名空间namespace、trait多继承、smarty模板引擎**

$sql = "SELECT * FROM `user` WHERE `name`='$name' AND `password`='$password'";

##### **12. PDO**

​	<1> 设置PDO连接属性  setAttribute()

​			(1)  SQL错误处理方式

​				属性	

​					PDO::ATTR_ERRMODE

​				值

​					PDO::ERRMODE_SILENT	无提示(默认模式)

​					PDO::ERRMODE_WARNING  报错WARNING

​					PDO::ERRMODE_EXCEPTION  抛出异常

​			(2) 设置返回结果集的形式

​				属性

​					PDO::ATTR_DEFAULT_FETCH_MODE

​				值

​					PDO::FETCH_ASSOC	关联

​					PDO::FETCH_NUM	索引

​					PDO::FETCH_OBJ		对象

​					PDO::FETCH_BOTH	混合

​			(3) 是否自动提交（mysql事物的时候用到）	

​				属性

​					PDO::ATTR_AUTOCOMMIT

​				值

​					0-关闭 / 1-开启(默认)

​	<2> PDO对象

​			setAttrbute()		设置连接属性

​			getAttrbute()		得到连接属性

​			exec()			返回受影响行数

​			query()			返回查询结果集对象

​			lastInsertId()		返回自增ID

​			

​			prepare() 预处理

​	<3> PDOStatement对象

​			fetch()			单条数据

​			fetchAll()		所有数据

​			rowCount()		受影响行数	

​			

​			预处理里面的PDOStatement

​			bindValue()

​			bindParam()	要先用变量接收参数

​				$stmt->bindParam('n', $n);

​			execute()	预处理完真正执行

##### **13. 预处理(防sql注入)**

​	<1> 预处理优点

​		-- 对用户的数据 进行过滤 提高安全性

​		-- 对结果集进行处理，提高批量操作的性能

​		典型用法，预处理防SQL注入

​	<2> SQL的占位符

​		？

​		：

​	<3> 绑定参数

​		bindValue()

​		bindParam()

​		execute()

​	<4> 结果集的预处理

​		bindColumn()

​	<5> 例：6种绑定方法

​		推荐-- 1. bindValue() 	? 占位符,直接绑定

​			$sql = "INSERT INTO user (name, age, province) VALUES (?, ?, ?)";

​			// 预处理sql,返回pdostatement对象

​			$stmt = $pdo->prepare($sql);

​			// 绑定参数

​			$stmt->bindValue(1, '猪');

​			$stmt->bindValue(2, '3');

​			$stmt->bindValue(3, '荷兰');

​			// 真正执行

​			$stmt->execute();

​		推荐-- 2. bindValue() 	: 占位符,直接绑定

​			$sql = "INSERT INTO user (name, age, province) VALUES (:n, :a, :p)";

​			$stmt->bindValue(':n', '张贤');

​		-- 3. bindParam()	: 占位符,先用变量定义,再绑定变量到参数

​			$sql = "INSERT INTO user (name, password, sex, age, province) VALUES (?, ?, ?, ?, ?)";

​			$stmt = $pdo->prepare($sql);

​			// 变量准备参数

​			$n = '盖伦';
​			$p = '10086';
​			$s = '1';
​			$a = '28';
​			$p2 = '德玛西亚';
​			$stmt->bindParam(1, $n);
​			$stmt->bindParam(2, $p);
​			$stmt->bindParam(3, $s);
​			$stmt->bindParam(4, $a);
​			$stmt->bindParam(5, $p2);
​			$stmt->execute();

​		-- 4. bindParam() : 占位符,先用变量定义,再绑定变量到参数	

​			$sql = "INSERT INTO user (name, password, sex, age, province) VALUES (:n, :p, :s, :a, :p2)";

​			$stmt = $pdo->prepare($sql);

​			$n = '诺克萨斯';
​			$p = '10010';
​			$s = '1';
​			$a = '32';
​			$p2 = '诺克萨斯族';
​			$stmt->bindParam('n', $n);
​			$stmt->bindParam('p', $p);
​			$stmt->bindParam('s', $s);
​			$stmt->bindParam('a', $a);
​			$stmt->bindParam('p2', $p2);
​			$stmt->execute();

​	推荐-- 5. execute() ? 占位符,在执行时候绑定参数(普通数组形式)

​			$sql = "INSERT INTO user (name, password, sex, age, province) VALUES (?, ?, ?, ?, ?)";	

​			$stmt = $pdo->prepare($sql);

​			$stmt->execute(['皮城女警', '159630', '0', '18', '德玛西亚']);

​		-- 6. execute() : 占位符,在执行时候绑定参数(数组键值对形式绑定)

​			$sql = "INSERT INTO user (name, password, sex, age, province) VALUES (:n, :p, :s, :a, :p2)";

​			$stmt = $pdo->prepare($sql);

​			$stmt->execute(['n'=>'卡特琳娜', 'p'=>'147852', 's'=>'0', 'a'=>'20', 'p2'=>'诺克萨斯族']);

​	<6>  对结果集进行处理，提高批量操作的性能

​		bindColumn()	结果集的预处理

​		rowCount()	返回受影响行数

​		例子：

​			try {

​				$sql = "SELECT * FROM user";
​				$stmt = $pdo->prepare($sql);
​				$stmt->execute();

​				echo "公有{$stmt->rowCount()}条数据";

​				var_dump($stmt);die;

​				// bindColumn 批量操作
​				$stmt->bindColumn('name', $name);
​				$stmt->bindColumn('sex', $sex); 	
​				$stmt->bindColumn('province', $pro);

​					foreach ($stmt as $k => $v) {

​						// var_dump($k);

​						// var_dump($v);echo $name . '|'.$pro.'<hr>';

​					}

​				} catch (PDOException $e) {

​					$e->getMessage();

​					exit;

​				}

##### **15. 事物处理**

​	<1> 什么是mysql事物?

​		执行多条sql语句组成的单元，要么全成功则成功，有一条失败则失败。

​	<2> 关键字解析

​		是否自动提交	

​		$pdo->setAttribute()

​		属性：	PDO::ATTR_AUTOCOMMIT		值：	0-关闭 / 1-开启(默认开启) 	

​					

​		beginTransaction()	开启一个事物的回滚点

​		rollback()			混滚一个事物,回滚到begin之前的状态

​		commit()			提交一个事物,只有提交的事物才真正写入数据库

​	<3> 事物处理的步骤

​		(1) 开启事物的回滚点，并且关闭自动提交

​			$pdo->beginTransaction();

​			$pdo->setAttribute(PDO::ATTR_AUTOCOMMIT, 0);

​		(2) try {

​				....多条sql语句

​				$pdo->commit();

​		      }  catch {

​				echo $e->getMessage();

​				$pdo->rollBack();

​				exit();

​		      }

​	<4> 例如：代码

​		<?php

// 加载dbconfig文件
require './login/dbCongif.php';

// 连接数据库
try {
	$pdo = new PDO(DNS, root, password);
	// var_dump($pdo);
	
	// 设置连接属性
	$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);	#mysql错误抛出异常
	$pdo->setAttribute(PDO::ATTR_DEFAULT_FETCH_MODE, PDO::FETCH_ASSOC);	#设置结果集的返回形式
} catch (PDOException $e) {
	echo $e->getMessage();
	exit;
}

// 插入多条数据
try {
	// 准备一套数据
	$data = [
		['疾风剑豪', '123456', '1', '22', '西部牛仔'],
		['火影劫', '123456', '1', '22', '东部火影'],
		['男刀', '123456', '1', '22', '南部刀族']
	];
	// var_dump($data);
	
	$sql = "INSERT INTO `user` (`name`, `password`, `sex`, `age`, `province`) VALUES (?, ?, ?, ?, ?)";
	$stmt = $pdo->prepare($sql);
	
	$count = 0;
	$ids = [];
	foreach ($data as $v) {
		$stmt->execute($v);
		$count += $stmt->rowCount(); #统计添加成功的行数
		$ids = $pdo->lastInsertId(); #返回成功id
	}
	echo "共插入{$count}条数据,id为{$ids}";
	
	var_dump($ids);
} catch (PDOException $e) {
	echo $e->getMessage();
	exit;
}



##### **16. namespace命名空间**

​	<1> 什么是命名空间?

​		重新划定一个局部的区域，这个区域可以减少命名的冲突。

​		为了防止用户编写的代码与PHP内部的类、函数、常量或者第三方的类、函数、常量之间的名字冲突。

​		(系统级别，用户级别的命名重复)

​	<2> 命名空间的特点

​		特点：

​			(1) PHP 5.3及以后才有命名空间

​			(2) namespace前面不能有任何输出流

​			(3) 命名空间只对本脚本起作用

​			(4) 文件如果没有命名空间，则默认在全局之中 

​			(5) 命名空间建议小写, 类名大写



​	<4> 命名空间的形式

​		(1) namespace 命名空间名; 

​			var_dump() #加命名空间后是局部空间

​			\dds\var_dump()	#绝对路径的调用命名空间

​			\var_dump() #前面加\是全局空间

​		(2) 使用全局的类

​			$pdo = new \PDO();	#全面加\用全局的PDO

​			var_dump($pdo);	

​		(3) 使用其他文件的局部的类

​			require './fun1.php';  # fun1里面的namespace one, class ff{};

​			$p = new \one\ff();    #只能写指定的  命名空间

​			var_dump($p);

​		(4) 子命名空间

​			namespace dds\gif;

​			function demo(){}

​			调用：\dds\gif\demo();

​		(5) 定义多个命名空间	

​			-1 不推荐,一般一个文件只给一个命名空间

​			-2 如果非要定义多个命名空间,用大括号包起来

​				namespace dds{}			\dds\demo();

​				namespace ssg{}			\ssg\demo();

​		(6) 命名空间的3种形式

​			demo();          // 非限定名称
​			nb\demo();       // 限定名称
​			\dds\nb\demo();  // 完全限定名称

​			本文件有dds命名空间,加载的文件有dds\nb的命名空间,用的时候可以用限定名称nb\demo() 

​																		= dds\nb\demo();

​		(7) 命名空间和动态语言	

​			-1 动态调用,用个变量接收函数名,然后在变量后面加()调用函数 function demo(){} $a = 'demo'; $ a();

​			-2 命名空间的动态调用: 用一个变量接收命名空间和函数名，再在最后加上(),则可以调用此函数

​				写命名空间字串时 必须使用单引号

​			namespace dds;
​			function demo () {

​				echo 'demo..';

​			}

​				$de = '\dds\demo';
​				$de();

​			const DD = '得到';
​			$c = '\nb\DD';
​			// echo $c;
​			echo constant($c);

​		(8) namespace关键字 和 __NAMESPACE__常量

​			-1 namespace关键字

​				声明命名空间

​				简化调用

​				namespace A\B\C\D\E;
​				function demo(){

​					echo '好长的demo啊。。。';

​				}

​				// \A\B\C\D\E\demo(); #完整调用
​				namespace\demo();	# 关键字代替调用

​			-2 __NAMESPACE__常量

​				获取本命名空间的名字

​				echo __NAMESPACE__;

​			-3 	类名::class 

​				自 PHP 5.5 起，使用类名::class可以获取 命名空间 + 类的名字

​				echo spa::class;  得到A\B\C\D\E\spa

​		(9) 使用命名空间：别名/导入

​			我们真正在使用命名空间时候，不能给命名空间随意起名字，应该按照当前文件路径来命名

​			也方便以后寻找文件。

​			-1 别名

​				取别名 use ... as ... 或者 直接用use，重新命名为最好一个空间名 

​				namespace A\B\C\D\E;

​				use \ A\B\C\D\E as  A;

​				use \ A\B\C\D\e;  #此时别名就为e,这个别名得小写

​			-2  导入

​				use \www\s81\oop\User;	#导入User类，类名是大写

​				use \www\s81\oop\User as heheda; #还可以导入类，再给类起别名







​	<5> 命名空间的综合应用	



##### **17. Traint **

 1.  Trait的概述

     ~~~
     Trait 是 PHP5.4 中的新特性，是 PHP 多重继承的一种解决方案。
     例如，需要同时继承两个类或抽象类，
     这将会是件很麻烦的事情，Trait 就是为了解决这个问题。
     ~~~

     2. Trait的简单使用

       格式：trait 名字{成员属性 方法 }

    特点：

       	  1. 不能有常量
    	  2. 不能被实例化
    	  3. 在类中 使用use关键字 混入一个trait
    
    3. 多个Trait的使用(多继承)
    
    use A,B;
    
    4. Trait之间的嵌套
    
    一个trait可以由多个trait组成
    
    在trait中使用use引入其他trait
    
    后面的trait引入前面的trait,然后类中再引入后面的trait
    
    5. Trait的属性
    
    在trait中可以使用各类修饰符,并且按照原规则去限制使用
    
    在使用了use的class中,不能重复定义与trait重名的属性
    
    6. Trait的方法优先级(指trait和class中方法属性优先级)
    
    class中 如果有方法和trait同名,class覆盖trait
    
    继承时 trait的方法会覆盖重写父类的方法
    
    7. Trait的修饰符
    
    静态属性不能动态调用,但是静态方法可以动态调用
    
    如果trait 存在抽象方法,则必须实现才能使用(普通的方法实现抽象内容)
    
    8. Trait的冲突
    
    1. 代替
    
        insteadof  指定替代的方法
    
    2. 起别名
    
       ![](trait.png)

##### 18.正则表达式**

​	. 定界符

​	. 原子

​	. 元字符

​	. 模式修正符	

​	<1>  定界符

​		/ /   

​	<2> 原子

​		可见原子：数字、字母、标点、语言、其他可见原子

 		不可见原子：换行符\n  回车\r  制表符\t  空格 其他

​	<3> 元字符：

​		原子的筛选方式

​			| 匹配两个或者多个分支

​			[ ] 匹配方括号中的任意一个原子

​			[ ^ ]匹配除了方括号中的原子之外的任意字符

​		原子的集合

​			.  匹配除换行符之外的任意字符

​			\d 匹配任意一个十进制数字,[0-9]

​			\D 

​			\s 匹配一个不可见原子，[\n\t\r]

​			\S

​			\w 匹配任意一个数字、字母或下划线[ _0-9,a-z,A-Z ]

​			\W

​		量词，原子连续出现多少次

​			{n} 恰好出现n次

​			{n,} 至少出现n次

​			{n,m}出现n-m次

​			*  至少出现0次{0, }

​			+ 至少出现1次{1, }

​			? 出现0或1次 {0,1}

​		边界控制和模式单元

​			^ 字符开始 $字符结尾

​			() 匹配其中的整体为一个原子

​			( | ) 匹配其中的两个或更多的选择

​		模式修正符

​			.* 贪婪匹配 , 匹配结果存在歧义取其长(默认模式)

​			U  懒惰匹配，匹配结果存在歧义取其短 

​			X   忽略空白，忽略空白

​			i    大小写匹配，不区分大小写

​	<4>  正则[ ] 和 ( )区别

​			-1 [ ] 匹配其中的任意一个原子

​			     ( ) 匹配其整体为一个原子

 			-2 (1234|12){1} 表示两组选择只能选择一组，要么1234要么12才成立

​			     [1234|12]{1} 表示两组选择中，仅是任意的一个原子 1234任意一个都可以

​	<5> 正则函数

​		单次匹配

​		preg_match(正则，字符串，[匹配的结果]);

​		全部匹配

​		$res = preg_match_all(正则，字符串，[匹配的结果);

​		$preg = '/./';   	# 理解为 获取该字符串的长度	

​		$res为长度

​		

​		str_repeat('*',2);将字符串重复多少次

​		// 正则替换

​		$str = '123ad';

​		$str = preg_replace(正则，新值，旧值); #再返回给人家

##### **19. unset() isset() empty() is_null()**

~~~
 unset()	删除变量内存
 
 empty()	判断一个变量是否为空, 变量是否与false等价.
			返回值：空 => true, 非空 => false
			
 isset()	判断一个变量是否设置，变量的内存中是否有东西
			返回值： 设置 => true, 未设置 => false
			两种情况为false：$a=null , 未定义变量 a	
			
 is_null()  恰好与isset()相反, 空就是true,非空就是false
 
 例如： echo empty($_GET['a']); //如果变量a的值是空
 	   echo !isset($_GET['a']); //如果得不到变量a的值
~~~

##### **20. 运算符**

~~~
	// 算术运算符
	// + - * / %
	// var_dump(2 / 0);
	// var_dump(0 / 2);
	// var_dump(06 / 2);
	// var_dump(012 / 2);
	// var_dump(-5 % -2);
	
	// 自增，自减运算符
	// 自增
	// 		++a  a++
	// 自减 
	//      --a  a--
	
	// 赋值运算符
	// =
	// +=
	// -=
	// *=
	// /=
	// %=
	// .=
	
	// 比较运算符
	// 		>
	// 		>=
	// 		<
	// 		<=
	// 		==
	// 		===
	// 		!=
	// 		!==
	
	// 逻辑运算符
	// 结果：true/false
	// 与	&&	and
	// 或 	||	or
	// 非	!
~~~

##### **21. 一元运算符、二元运算符、三元运算符**

~~~
// 一元运算符	++	--	!
// 二元运算符	+	-	*	/
// 三元运算符	?  true : false
~~~

##### **22. 流程控制**

#####if分支

~~~
// 流程控制
// 1. 顺序结构：通常代码是从上往下依次执行的
// 2. 分支结构：通过if/switch来进行分支选择
// 3. 循环结构：while / dowhile / for循环

// if 支持范围型，定值型
// 条件表达式：最终结果只有true / false
// 分支1： 
// if(条件表达式)  只能影响紧跟在if后面的一句话

// 分支2：
// if () {}		  影响{ }里面的代码

// 分支3：
// if () {
//  true环境  
// } else {
// flase环境
// }

// 分支4： 巢状分支
// if () {
// 		if () {
//  
//		} else {
//  
//		} 
// } else {
//  	if () {
// 
//		 } else {
//  
// 		 }
// } 

// 分支5：
if () {
  
} elseif () {
  
} elseif () {
  
} elseif () {
  
} else {
  
}



~~~

##### **switch分支**

~~~
// 定值分支
// switch 只支持定值型

分支1：匹配到某一个标识, 则执行该标识的代码, 且依次向下执行
$name = '张贤';
switch(标识)
{
  case '' : 代码code;
  case '' : 代码code;
  case '' : 代码code;
  case '' : 代码code;
}

分支2：一旦执行到break, 会立马跳出分支
$name = '张贤';
switch(标识)
{
  case '' : 代码code; break;
  case '' : 代码code; break;
  case '' : 代码code; break;
  case '' : 代码code; break;
}

分支3：如果匹配不到case, 则执行default
$name = '张贤';
switch(标识)
{
  case '' : 代码code; break;
  case '' : 代码code; break;
  case '' : 代码code; break;
  case '' : 代码code; break;
  default: 代码code;
}

~~~



##### **23. 循环结构**

~~~
while 循环
dowhile 循环
for 循环
~~~

#####while 循环

~~~
while ( 1.条件表达式 ) {
	2. 循环体
}
3. 循环外的代码
// 执行顺序：1 2 1 2...，当1为false时，循环结束
循环三要素:
		初始值
		循环条件 		条件表达式
		循环增量 		目的: 为了改变条件值
		
特殊：while(1){} 不知道表达式时候用1
~~~

##### doWhile循环

~~~
do{
  2. 循环体
} while (1. 条件表达式);

执行顺序：2 1 2 1...
当1为false时候，结束循环;但是不管是否满足条件都会do一次

与while区别：
while: 先判断，再执行循环体
doWhile: 先执行循环体，再判断
~~~

##### for循环

~~~
for (1.初始值; 2.循环条件; 3.增量) {
  	4. 循环体
}
执行顺序：1 2 4 3 2 4 3...,当2循环条件为false时候结束循环
~~~

##### 24. 查询字段分类

~~~
-- 查询
-- select 	 * | 字段名
-- from      表名
-- where 	 条件
-- group by  字段名			分组查询
-- having 	 筛选条件 		   写在group by 后面，用来过滤group by查询结果
-- order by  字段名             (order by `id` desc)排序 asc升序 desc降序
-- limit     下标, 行数			从下表几开始，连续拿多少条数据	


-as	别名 适用于表名，字段名
-distinct 取消重复,写在查询的字段名后面

注意:
where 后面要跟的是数据表里的存在的字段，如果我把ag换成avg(price)也是错误的！因为表里没有该字段。
而having只是根据前面查询出来的是什么就可以后面接什么（比如一些聚合函数这样的“伪字段”）。
~~~

![](wh.png)

**24.trait的使用**

~~~
 1.trait 实现代码的复用和解决php只能单继承的问题
 2.trait 优先级的问题
   (1)当前类中的方法与trait类、父类中的方法重名，其解决方法.
       本类 > trait类 > 父类
   (2)当多个trait类中有同名方法时候，其解决方法.
       <1> insteadof 替换
           use Demo1,Demo2 {
                Demo1::hello insteadof Demo2;
          }
       <2> Demo2的方法hello起别名，D2hello

~~~

**25.PHP设计模式**

~~~
/**
 * PHP常用3个设计模式
 *  1.单例模式
 *  2.工厂模式
 *  3.注册树模式
 */

// 单例模式
class Site
{
    //属性
    public $sitename;
    //本类的静态属性
    protected static $instance = null;
    //禁用掉构造方法
    private function __construct($sitename)
    {
        $this->sitename = $sitename;
    }
    //获取本类的唯一实例
    public static function getInstance($sitename='PHP中文网')
    {
        if (!self::$instance instanceof self) {
            self::$instance = new self($sitename);
        }
        return self::$instance;
    }

}

// 用工厂模式来生成本类的单一实例
// 用create方法生成一个对象，然后把对象挂在一颗树上
class Factory
{
    public static function create()
    {
        return Site::getInstance('二狗子牛逼');
    }
}

// 对象注册树
/**
 * class Register,以下方法名是自定义
 * 1.注册：set(),把对象挂树上
 * 2.获取：get(),把树上对象取下来
 * 3.注销：_unset(),把树上对象注销掉
 */

class Register
{
    //创建对象池: 数组
    protected static $objects = [];
    //生成对象并上树
    public static function set($alias, $object)
    {
        self::$objects[$alias] = $object;
    }
    //从树上去下对象
    public static function get($alias)
    {
        return self::$objects[$alias];
    }
    //把树上对象注销掉
    public static function _unset()
    {
        unset(self::$objects[$alias]);
    }
}

// 单例和工厂是在创建,注册树是重在用
// 将Site类的实例上树,放入对象池
Register::set('site', Factory::create());
$obj = Register::get('site');
// 查看对象
var_dump($obj);
echo '<br>';
echo $obj->sitename;
~~~



















