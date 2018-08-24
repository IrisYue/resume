按照角色、权限、资源划分，实现相应的功能，前端利用easyui生成页面和实现前后端数据的交互
主要分为4大模块
业务大模块、管理大模块、维护大模块、系统大模块
一、系统大模块
角色管理、资源管理、IP管理（内网）、系统广播、系统监控、在线用户、活跃日志、系统状态、
计划任务、邮件日志
角色、权限、资源-照片1
用户维护界面-除了对用户的增删改查之外，还可以对用户的角色（46）种，对应的角色会有相对应的资源权限，什么角色的用户只能看到对应资源权限的页面，拿业务员来说，对应的业务员只能修改自己的客户和修改订单信息，所以另外也对客户进行了权限的划分，在新建用户之初会对影虎设置securityList
写对应方法的时候需要判断对应的model的客户部门是否相同，不相同的话会提示异常，无权限不能更改的。
Java实现缓存，类似于Redis的实现，可以缓存对象到内存中，提高访问效率。
定义CacheManager、cache
例子：类似于假如系统中有一个颜色类，固定的，后期变动小
存到一个自己定义的缓存中，后期直接调用
Forward/ Redirect
直接转发方式（Forward），客户端和浏览器只发出一次请求，Servlet、HTML、JSP或其它信息资源，由第二个信息资源响应该请求，在请求对象request中，保存的对象对于每个信息资源是共享的。
间接转发方式（Redirect）实际是两次HTTP请求，服务器端在响应第一次请求的时候，让浏览器再向另外一个URL发出请求，从而达到转发的目的
Redirect:一般用于避免用户的非正常访问
例如：用户在没有登录的情况下访问后台资源，Servlet可以将该HTTP请求重定向到登录页面，让用户登录以后再访问。在Servlet中，通过调用response对象的SendRedirect()方法，告诉浏览器重定向访问指定的URL ： response.sendRedirect
Forward:由控制器来控制请求应该转发给那个信息资源。然后由这些信息资源处理请求，处理完以后还可能转发给另外的信息资源来返回给用户，这个过程就是经典的MVC模式
requestDispatcher.forward(request,response);

问：直接转发和间接转发的原理及区别是什么？
答：Forward和Redirect代表了两种请求转发方式：直接转发和间接转发。对应到代码里，分别是RequestDispatcher类的forward()方法和HttpServletRequest类的sendRedirect()方法。
对于间接方式，服务器端在响应第一次请求的时候，让浏览器再向另外一个URL发出请求，从而达到转发的目的。它本质上是两次HTTP请求，对应两个request对象。
对于直接方式，客户端浏览器只发出一次请求，Servlet把请求转发给Servlet、HTML、JSP或其它信息资源，由第2个信息资源响应该请求，两个信息资源共享同一个request对象。
技巧：直接看地址栏变没变就可以了

活跃日志：通过ActivityInterceptor的preHanle方法进行收集
计划任务：在页面上实现任务是否运行
邮件日志：邮件基类，状态
系统状态：
使用servletContext注意事项 
因为存在servletContext中的数据会长时间的保存在服务器端，会占用内存，因此建议不要向servletContext中放过大的数据。

维护大模块
用户维护、部门维护、面料维护、。。。
管理大模块
审批和报表
业务大模块
java延迟加载
public class Singleton{        
    private Singleton(){        
        …        
    }        
    private static class SingletonContainer{        
        private static Singleton instance = new Singleton();        
    }        
    public static Singleton getInstance(){        
        return SingletonContainer.instance;        
    }        
}   

