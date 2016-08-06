#JSP
JSP(Java Server Pages),一种动态网页开发技术。

JSP是以Java语言作为脚本语言的，其开发的WEB应用可以跨平台使用，既可以运行在Linux上也能运行在Window上。

第一个Hello World 程序

	<html>
	    <head>
	           <title>第一个JSP程序</title>
	    </head>
	    <body>
	           <%
	                  out.println("Hello World！");
	           %>
	    </body>
	</html>

####JSP开发环境：
<ul>
<li>JDK</li>
<li>集成开发环境myeclipse、idea(我在用的)</li>
<li>服务器Tomcat</li>
</ul>

####JSP优势：
<ul>
 <li>性能更加优越，因为JSP可以直接在HTML网页中动态嵌入元素而不需要单独引用CGI文件。
<li>服务器调用的是已经编译好的JSP文件，而不像CGI/Perl那样必须先载入解释器和目标脚本。
<li>JSP基于Java Servlets API，因此，JSP拥有各种强大的企业级Java API，包括JDBC，JNDI，EJB，JAXP等等。
<li>JSP页面可以与处理业务逻辑的servlets一起使用，这种模式被Java servlet 模板引擎所支持
</ul>

####动态网页性能对比
<ul>
<li>JSP:适合开发大型的企业级web应用
<li>ASP.net:简单易学，但安全性和跨平台性差
<li>PHP:简单高效成本低，适合中小型企业开发
</ul>


####JSP页面元素构成
<ul>
<li>静态内容
<li>指令
<li>表达式
<li>小脚本
<li>声明
<li>注释
</ul>


#####JSP页面的生命周期
编译阶段：解析文件，转化为servlet，编译servlet</br> 
　　||</br>
初始化阶段：首先调用构造函数，jspInit（）方法只执行一次</br>
　　||</br>
执行阶段：_jspService(HttpServletRequest request,HttpServletResponse response)</br>
　　||</br>
销毁阶段：jspDestroy()



#####JSP指令
######page指令：定义网页依赖属性，比如脚本语言、error页面、缓存需求等等

``<%@ page ... %>``

属性：
<ul>
<li>language（默认JAVA）
<li>import：导入要使用的Java类
<li>contentType(常用：=text/html;charset="utf-8")
</ul>


######include指令：将一个外部文件嵌入到当前文件中，同时解析

``<%@ include file="文件相对 url 地址" %>``



######taglib指令：使用标签库定义新的自定义标签，启用定制行为

``<%@ taglib uri="uri" prefix="prefixOfTag" %>``


#####JSP声明

``<%！JAVA声明的变量或者方法%>``

#####JSP脚本元素
即JSP中可以执行的java代码

``<%JAVA代码%>``


#####JSP表达式

``<%=表达式%>`` 表达式不以分号结束；

#####JSP 九大内置对象
JSP容器为每个页面提供的Java对象，开发者可以直接使用它们而不用显式声明。
常用的：

<table>
<tbody>
<tr>
<td><em>对象</em></td>
<td><em>描述</em></td>
<td><em>备注</em></td>
</tr>
<tr>
<td>request</td>
<td>HttpServletRequest类的实例</td>
<td>request对象提供了一系列方法来获取HTTP头信息，cookies，HTTP方法等等</td>
</tr>
<tr>
<td>response</td>
<td>HttpServletResponse类的实例</td>
<td>定义了处理HTTP头模块的接口</td>
</tr>
<tr>
<td>out</td>
<td>PrintWriter类的实例，用于把结果输出至网页上</td>
<td>常用方法：printIn();clear();flush();clearBuffer();getBufferSize();getRemaining();isAutoFlush();close();</td>
</tr>
<tr>
<td>session</td>
<td>HttpSession类的实例</td>
<td></td>
</tr>
<tr>
<td>application</td>
<td>ServletContext类的实例，与应用上下文有关</td>
<td></td>
</tr>
<tr>
<td>config</td>
<td>ServletConfig类的实例</td>
<td></td>
</tr>
<tr>
<td>pageContext</td>
<td>PageContext类的实例，提供对JSP页面所有对象以及命名空间的访问</td>
<td>存储了request对象和response对象的引用</td>
</tr>
<tr>
<td>page</td>
<td>类似于Java类中的this关键字</td>
<td></td>
</tr>
<tr>
<td>Exception</td>
<td>Exception类的对象，代表发生错误的JSP页面中对应的异常对象</td>
<td>通常用来产生对出错条件的适当响应</td>
</tr>
</tbody>
</table>


#####JSP服务器相应
Response响应对象主要将JSP容器处理后的结果传回到客户端。可以通过response变量设置HTTP的状态和向客户端发送数据，如Cookie、HTTP文件头信息等。


#####JSP客户端相应
request对象提供了一系列方法来获取HTTP信息头，包括表单数据，cookies，HTTP方法等等。

#####JSP session
HTTP是无状态协议，这意味着每次客户端检索网页时，都要单独打开一个服务器连接，因此服务器不会记录下先前客户端请求的任何信息。

######维持客户端与服务器的会话的方法
* Cookies
* 隐藏表单域：
  `<input type="hidden" name="sessionid" value="12345">`
但点击A标签中的超链接时不会产生表单提交事件，因此隐藏表单域也不支持通用会话跟踪
* 重写URL
* session（保存在服务器的内存之中，每个用户对应一个不同的session）


######session的生命周期
创建
活动
销毁：调用session.incalidate()方法；session过期；重启服务器；













