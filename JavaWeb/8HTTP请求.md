# HTTP请求

    在客户端浏览器发送下面的事件,浏览器就像服务器发送一个HTTP请求
    1. 用户在浏览器地址栏输入URL并回车(GET)
    2. 用户单击了HTML页面中的超链接(GET)
    3. 用户在HTML页面中提交表单(GET/POST)
    默认情况下使用表单发送的请求也是GET请求,如果发送POST请求,需要将method属性值指定为post

```HTML
<form action="register.action" method="post">
<p>用户注册</p>
姓名：<input type="text" name="name" size="15">
年龄：<input type="text" name="age" size="5"><br>
性别：<input type="radio" name ="sex" value="male">男
      <input type="radio" name ="sex" value="female">女<br>
兴趣：<input type="checkbox" name="hobby" value="read">文学
      <input type="checkbox" name="hobby" value="sport">体育
      <input type="checkbox" name="hobby" value="computer">电脑<br>
学历：<select name="education">
      <option value="bachelor">学士</option>
      <option value="master">硕士</option> 
      <option value="doctor">博士</option> 
      </select>
邮件地址：<input type="text" name="email" size="20"><br>
<input type="submit" name="submit" value="提交">
<input type="reset" name="reset" value="重置">
</form>
</body>
</html>
```