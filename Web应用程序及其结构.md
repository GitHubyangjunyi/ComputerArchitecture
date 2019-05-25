# Web应用程序及其结构 #

    Tomcat安装目录的webapps目录是所有Web应用程序的根目录,假设要建立一个名为xweb的应用程序,就应该在该目录下建立一个xweb目录
    xweb(应用程序文档根目录)
        |----css
        |----html
            |----*.html
        |----images
        |----js
        |----jsp
        |----index.html
        |----WEB-INF(存放供服务器访问的资源,不视为文档根目录的一部分,不为客户服务)
            |----classes(运行时容器将该目录添加到Web应用程序类路径中)
                |----com.demo.LoginServlet.class
            |----lib(运行时容器将该目录所有JAR文件添加到Web应用程序类路径中)
                |----*.jar
            |----web.xml(部署描述文件)

    假设服务器主机名为www.myserver.com,如果要访问xweb根目录下的index.html文件应该使用
    http://www.myserver.com/xweb/index.html

## Web归档文件 ##

    一个Web应用程序包含许多文件,可以将这些文件打包成一个扩展名为.war的Web归档文件
    WAR文件主要是为了方便Web'应用程序在不同系统之间的移植
    可以直接把WAR文件放到Tomcat服务器的webapps目录中,Tomcat会自动释放文件内容到webapps目录并创建一个同名的应用程序

### 创建WAR文件 ###

    cd xweb
    jar -cvf xweb.war *