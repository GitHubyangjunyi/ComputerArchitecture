# Servlet生命周期

    Servlet作为一种在容器中运行的组件,生命周期如下:
        1. 调用init()加载和实例化Servlet类
            对一个Servlet可能在容器启动时或第一次被访问时加载到容器中,容器使用Class.forName()加载并初始化,要求Servlet类带有一个不带参数的public构造方法
            通常不在Servlet类中定义任何构造方法,而让编译器添加默认构造方法
        1. 初始化Servlet
            容器创建Servlet实例后将调用init(ServletConfig)初始化Servlet,ServletConfig对象包含在Web应用程序的初始化参数
            然后调用无参数init()完成初始化,init()仅调用一次
            有时候不在容器启动时对Servlet初始化(预加载),而是当容器第一次收到对该Servlet的请求时初始化,成为延迟加载
            可以使用@WebServlet注解的loadOnStartup元素或web.xml的<load-on-startup>元素指定当容器加载并初始化Servlet
        2. 容器从收到请求就将调用它的service()
            用户通过单击超链接或提交表单向容器请求访问Servlet
            当容器接收到对Servlet的请求时,容器根据请求中的URL找到Servlet,首先创建两个对象,HttpServletRequest请求对象和HttpServletResponse响应对象
            然后创建一个新的线程,在该线程中调用service(),同时将请求对象和响应对象作为参数传递给该方法
            有多少个请求就将创建多少个线程,接下来service()将检查HTTP请求的类型(GET/POST等)来决定调用Servlet的doGet()或doPost()
            Servlet使用响应对象获得输出流对象,调用有关方法将响应发送给浏览器
            之后线程将被销毁或者返回到容器的线程池中,这时请求和响应对象已经离开作用域也将被销毁
            最后客户得到响应
        3. 调用destroy()进入销毁状态
            当容器不再需要Servlet实例时将在实例上调用destory()释放资源
            一旦destory()被调用,Servlet实例从该状态仅能进入卸载状态
            在调用调用destory()之前,容器会等待其他执行Servlet的service()的线程结束