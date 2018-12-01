一.jdbc怎么连接数据？
  1.通过反射加载驱动:
	Class.forName("com.mysql.jdbc.Driver");
  2.获得连接:
	String url="jdbc:mysql://localhost:3306/testDB";
	String userName="root";
	String password="root";
	Connection conn=DriverManager.getConnection(url,userName,password);
  3.声明sql语句:
	String sql="selcet * from test";
  4.防止sql注入，创建一个PreparedStatement对象
	PreparedStatement pstm=conn.prepareStatement(sql);
  5.执行sql
	ResultSet rs= pstm.executeQuery();
  6.处理结果
	while(rs.next){
		......
	}
  7.释放资源
	rs.close();
	pstm.close();
	conn.close();

二.抽象类和接口的区别？
  1.抽象类：
	被abstract修饰的类称为抽象类
	抽象类是一个模板，用来捕捉子类的通用特性的 。它不能被实例化，只能被用作子类的基类。
  2.接口：
	接口是抽象方法集合，
	所有的属性默认都是public static final
	所有的方法默认都是public abstract
  3.java中一个类只能继承的一个直接父类，但可以实现多个接口。
三.jsp常用标签
	<jsp:include>标签  
	<jsp:forward>标签  
	<jsp:param>标签
四.项目部署在哪里？
	.metadata/.plugins/org.eclipse.wst.server.core/tmp0/wtpwebapps
五.javabean怎么实现？
	JavaBean 只是定义了简单的编码规范：
	JavaBean 需要实现 java.io.Serializable 接口，为了保存对象的状态
	JavaBean 需要提供 public 修饰的无参构造方法，为了实例化对象
	为 private 修饰的字段提供 setter/getter，为了获取和设置字段的值
六.springMvc的流程？
	1、用户发起请求到前端控制器（DispatcherServlet），
	   该控制器会过滤出哪些请求可以访问Servlet、哪些不能访问。
	   就是url-pattern的作用，并且会加载springmvc.xml配置文件。
	2、前端控制器会找到处理器映射器（HandlerMapping），
	   通过HandlerMapping完成url到controller映射的组件，
	   简单来说，就是将在springmvc.xml中配置的或者注解的url与对应的处理类找到并进行存储，
	   用map<url,handler>这样的方式来存储。
	3、HandlerMapping有了映射关系，并且找到url对应的处理器，
	   HandlerMapping就会将其处理器（Handler）返回，在返回前，会加上很多拦截器。
	4、DispatcherServlet拿到Handler后，找到HandlerAdapter（处理器适配器），
	   通过它来访问处理器，并执行处理器。
	5、执行处理器
	6、处理器会返回一个ModelAndView对象给HandlerAdapter
	7、通过HandlerAdapter将ModelAndView对象返回给前端控制器(DispatcherServlet)
	8、前端控制器请求视图解析器(ViewResolver)去进行视图解析，
	   根据逻辑视图名解析成真正的视图(jsp)，
	   其实就是将ModelAndView对象中存放视图的名称进行查找，
	   找到对应的页面形成视图对象
	9、返回视图对象到前端控制器。
	10、视图渲染，就是将ModelAndView对象中的数据放到request域中，用来让页面加载数据的。
	11、通过第8步，通过名称找到了对应的页面，通过第10步，request域中有了所需要的数据，
	   那么就能够进行视图渲染了。最后将其返回即可。
七.重定向和转发：
	重定向：response.sendRedirect(url); 
	转发  ：request.getRequestDispatcher(url).forward(request, response);

	转发在服务器端完成的；重定向是在客户端完成的
	转发的速度快；重定向速度慢
	转发的是同一次请求；重定向是两次不同请求 
	转发不会执行转发后的代码；重定向会执行重定向之后的代码 
	转发地址栏没有变化；重定向地址栏有变化 
	转发必须是在同一台服务器下完成；重定向可以在不同的服务器下完成
八.控制了什么？反转了什么？
	1.IOC容器控制了对象，控制了外部资源的获取。
	  IOC是控制反转，是将代码中的操控权转到容器里去控制
	2.反转则是由容器来帮忙创建及注入对象，对象的获取被反转了。













