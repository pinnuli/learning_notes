
### servlet生命周期
1.初始化，调用`init()`方法，生成`Servlet`实例
2.响应客户请求，调用`service()`方法，由`service()`方法根据提交方式悬着执行`doGet()`或者`doPost()`方法
3.终止，调用`destroy()`方法
![servlet life cycle](/images/servlet_life_cycle.png)

### tomcat装载servlet的三种情况
1.Servlet容器启动时自动装载某些Servlet，需要在web.xml文件中的`<Servlet></Servlet>`之间添加`<loadon-startup>1<load-sartup>`
> 数字越小优先级越高
2.在Servlet容器启动后，客户首次向Servlet发送请求
3.Servlet类文件被修改时，重新装载Servlet

### 获取初始化参数
在web.xml中配置`Servle时可以配置初始化参数，通过`<init-param>`配置：
```XML
<init-param>
    <param-name>username</param-name>
    <param-value>pinnuli</param-value>
</init-param>
```
在Servlet类中可以通过`getInitParameter()`获取：
```java
String username = this.getInitParameter("username");
```

未完待续。。。