# 请求URL组成与解析

      一个请求URL组成:
        http://www.myserver.com/helloweb/helloservlet/hello/abc.jsp?userName=xx
        |协议与主机名与可选端口号| 上下文 |    Servlet路径    |路径信息| 查询字符串|
                               |            请求URI                 |
        请求URI可以使用HttpServletRequest的getRequestURI()得到
        查询字符串使用HttpServletRequest的getQueryString()得到
        一个请求URI由三部分组成:
            1. 上下文路径:
               1. /helloweb为上下文路径,假设在容器中有一个名为helloweb的应用程序
            2. Servlet路径:
               1. /helloservlet/hello为Servlet路径,假设<url-pattern>/helloServlet/hello/*</url-pattern>
            3. 路径信息:
               1. /abc.jsp为额外的路径信息
        分别使用请求对象的getContextPath()/getServletPath()/getPathInfo()得到

## URL模式的三种形式

    1. 目录匹配
        以/开头,以/*结尾

```XML
    <servlet-mapping>
        <servlet-name>helloservlet</servlet-name>
        <url-pattern>/helloServlet/hello/*</url-pattern>
    </servlet-mapping>
```

    将任何在Servlet路径中以/helloServlet/hello/字符串开头的请求都发送给helloservlet
    2. 扩展名匹配
        以*.开始后接一个扩展名

```XML
    <servlet-mapping>
        <servlet-name>helloservlet</servlet-name>
        <url-pattern>*.pdf</url-pattern>
    </servlet-mapping>
```

    3. 精确匹配

```XML
    <servlet-mapping>
        <servlet-name>reportservlet</servlet-name>
        <url-pattern>/report</url-pattern>
    </servlet-mapping>
```

    容器将http://www.myserver.com/helloweb/report 发送给reportservlet
    但不把http://www.myserver.com/helloweb/report/sales 发送给reportservlet

## 容器如何解析URL

    当容器收到一个URL请求,先解析出URI,然后从中取出第一部分作为上下文路径,这里是/helloweb
    接下来在容器中查找有没有名为helloweb的应用程序
    如果没有则上下文路径为空,请求发送到默认的Web应用程序,路径名为ROOT
    如果有名为helloweb的应用程序则继续解析下一个部分,容器尝试将Servlet路径与Servlet映射相匹配
    如果找到一个匹配则完整的URI请求(上下文路径部分除外)就是Servlet路径,则路径信息为null
    容器沿着请求URI路径树向下,每次一层目录,使用/作为分隔符,反复尝试最长的路径,查看是否与一个Servlet匹配
    如果有一个匹配,请求URI的匹配部分就是Servlet路径,剩余部分是路径信息
    如果不能找到匹配的资源将返回404