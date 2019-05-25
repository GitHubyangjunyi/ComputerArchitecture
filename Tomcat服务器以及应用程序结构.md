# Tomcat服务器 #

## Tomcat目录结构及其用途 ##

    /bin        存放启动和关闭Tomcat的脚本文件
        |----tomcat7w.exe   管理Tomcat启动
    /conf       存放Tomcat服务器的各种配置文件,其中包括servler.xml/tomcat-users.xml/web.xml
    /lib        存放Tomcat服务器以及所有Web应用程序都可以访问的库文件
        |----servlet-api.jar
    /logs       日志文件
    /temp       临时文件
    /webpages   所有Web应用程序的根目录
        |----examples
        |----ROOT   默认的Web应用程序http://localhost:8080/
        |----hello  新建立的Web应用程序

    /work       存放JSP页面生成的Servlet源文件和字节码文件

### 配置Tomcat的服务器端口 ###

    Tomcat默认端口号是8080,要修改端口号需要编辑/conf/servler.xml文件并重新启动服务器
    <Connector port = "8080" protocol = "HTTP/1.1" connectionTimeout = "20000" redirectPort = "8443" />
    port属性改为80后访问Web应用时就无需指定端口号

## Web应用程序及其结构 ##

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

### Web归档文件 ###

    一个Web应用程序包含许多文件,可以将这些文件打包成一个扩展名为.war的Web归档文件
    WAR文件主要是为了方便Web'应用程序在不同系统之间的移植
    可以直接把WAR文件放到Tomcat服务器的webapps目录中,Tomcat会自动释放文件内容到webapps目录并创建一个同名的应用程序

#### 创建WAR文件 ####

    cd xweb
    jar -cvf xweb.war *
    生成WAR文件后可以将其部署到其他容器中

## 部署描述文件 ##

    Web应用程序包含多种组件,有些组件可以使用注解配置,有些需使用部署描述文件进行配置
    部署描述文件deployment descriptor可以用来初始化Web应用程序的组件
    DD文件是一个XML文件,第一行是声明
    下面所有内容元素都包含在<web-app>和</web-app>元素中