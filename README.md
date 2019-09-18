# mylearning
我的笔记
ServletContext的作用
1）获取WEB应用的初始化参数 ServletContext.getInitParameter(String name)
2）获取WEB应用中某个文件在服务器上的绝对路径 servletContext.getRealPath("/t.text");
3）获取WEB应用中某个文件对应的输入流  servletContext.getResourceAsStream("/WEB-INF/1.doc");
4）获取当前WEB应用的名称  .getContextPath
得到该Servlet运行其中的这个背景对象。从这个背景对象中你可以访问如下信息或资源：（注意该方法不是ServletContext的方法而是获取背景对象的方法由于HttpServlet继承Servlet的关系GenericServlet类和HttpServlet类同时具有该方法）：初始化参数 ServletContext.getInitParameter(String name)。存储在背境中的对象 context.getAttribute(String name) 与本背景关联的资源 ServletContext.getResource(String path) 日志 ServletContext.log(String msg) 以上所示方法均为ServletContext所提供，值得一提的是对于存储在背景中的对象访问方法常用的还有： context.setAttribute(String name， Object object)；将特定名字绑定的任意类型的对象上。将把object对象绑定到名字name，存放在Servlet背景中，可供同一背景中的其他Servlet共享。其他Servlet可以通过context.getAttribute(String name)，得到一个背景中的对象，或通过context.removeAttribute(String name)在背景中移除一个对象。
在Web应用范围内存取共享数据的方法:

注：web应用范围具有以下两层含义：
（1） 表示有web应用的生命周期构成的时间段.
（2） 表示在web应用的生命周期内所有web组件的集合。
setAttribute(String name,java.lang.Objectobject)：把一个java 对象和一个属性名绑定，并存放到ServletContext 中，参数name 指定属性名，参数Object 表示共享数据。
getAttribute(String name)：根据参数给定的属性名，返回一个Object类型的对象。
getAttributeNames()：返回一个Enumeration 对象，该对象包含了所有存放在ServletContext 中的属性名
removeAttribute(String name) ： 根 据 参 数 指 定 的 属 性 名 ， 从servletContext 对象中删除匹配的属性。
getRealPath（"/"）：得到绝对路径
访问web应用的静态资源

使用ServletContext接口可以直接访问web应用中的静态内容文档结构.包括HTML,GIF和JPEG文件。如以下方法:
.getResource
.getResourceAsStream
这两个方法的参数都是以"/"开头的字符串,表示资源相对于context根的相对路径.文档结构可以存在于服务器文件系统,或是war包中,或是在远程服务器上,抑或其他位置.不可以用来获得动态资源,比如,getResource("/index.jsp"),这个方法将返回该jsp文件的源码,而不是动态页面.可以用"Dispatching Requests"获得动态内容.
列出web应用中可被访问的资源,可以使用getResourcePaths（String path）方法。


 HTTP 是定义WEB浏览器与WEB服务器之间数据交换的过程与数据本身的格式
