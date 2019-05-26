# Servlet API

    Servlet是服务器端小程序,使用Servlet API以及相关的类编写出来的Java程序,运行在Web容器中,主要用来扩展Web'服务器的功能
    要编译Servlet需要将Servlet API添加到类路径中,在Tomcat中,Servlet API包含在其安装目录的/lib/servlet-api.jar文件中

## 最简单Servlet

```Java
package com.demo;

import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.*;

@WebServlet(name = "helloServlet", urlPatterns = { "/helloServlet.do" })
public class HelloServlet extends HttpServlet {
        private static final long serialVersionUID = 1L;
        //覆盖doGet方法:获得响应对象并输出
        protected void doGet(HttpServletRequest request,
                            HttpServletResponse response)throws ServletException, IOException{
            response.setContentType("text/html;charset=UTF-8");
            PrintWriter out = response.getWriter();//Servlet使用响应对象获得输出流对象,调用有关方法将响应发送给浏览器
            out.println("<html>");
            out.println("<body><title>Hello Servlet</title>");
            out.println("<h3 style='color:#00f'>Hello,World!</h3>");
            out.println("现在的时间是:"+new java.util.Date());
            out.println("</body>");
            out.println("</html>");
        }
}
```

## Servlet部署

    Servlet作为Web应用程序的组件需要部署到容器中才能运行,在Servlet3.0之前需要在部署描述文件web.xml中部署
    3.0之后可以使用注解部署Servlet
    @WebServlet(name = "helloServlet", urlPatterns = { "/helloServlet.do" })
    指定Servlet名称为helloServlet,URL映射模式/helloServlet.do
    在浏览器中可以使用http://localhost:8080/helloweb/helloServlet.do 进行访问