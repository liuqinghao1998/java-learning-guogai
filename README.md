![](https://i.imgur.com/T1EWK8l.jpg)
# Java面试通关要点汇总集（部分解答）

## 说明
如果你有幸能看到的话，

- 1、本文整体框架来自[@阿里.梁桂钊](https://juejin.im/post/5a94a8ca6fb9a0635c049e67)的博文，总结的非常不错。值得我们学习，它的[博客](http://blog.720ui.com)部分做了解答。
- 2、由于自己能力有限，没能实现心中那个想法，就是第一遍自己写，第二遍书本查询
- 3、文章会放到[GitHub](https://github.com/guoxiaoxu/java-learning-guogai),用Git控制。可能是一场持续站。
- 3、如有雷同，纯属意外。会放上你们的链接。如有拼写错误，还请谅解。
- 4、测试放到最后面，有兴趣的可以看下？这样的我能够入门吗？
- 5、苦逼-->傻逼-->二逼-->牛逼
- 6、自己动手，丰衣足食。

## 基础篇

### 基本功

**1、面向对象的特性**[参考](参考)

(1)封装：就是把客观事物封装成抽象的类，并且类可以把自己的数据和方法只让可信的对象操作，对不可信进行信息隐藏。简单来说，就是一个类封装了数据以及操作这些数据的代码逻辑实体。在一个类的内部，方法或数据可以是私有的，不能被外界访问。这样做的目的是对内部数据进行了不同级别的保护，防止错误的使用了对象的私有部分。

(2)继承：它可以使用现有类的所有功能，并在原来的基础上对这些功能进行扩展。通过继承创建新类被称为“子类”或“派生类”。被继承的类称为"基类"和“父类”或“超类”。要想实现继承可以通过“继承”和“组合(聚合)”：实现方式有：实现继承和接口继承。实现继承是指直接使用基类的属性和方法而无需额外的编码的能力；接口继承是指仅使用属性和方法的名称，但子类必须提供实现的能力。

(3)多态：是指一个类实例的相同方法在不同情形有不同的表现。多态机制使具有不同内部的结构的对象可以共享的外部接口。虽然针对不同对象的具体操作不同，但通过一个公共的类，他们可以通过相同的方法予以 调用。

最常见的多态就是将子类传入父类参数中，运行时调用父类方法时，通过传入的子类决定具体的内部结构或行为。

**2、面向对象五大原则：**

- (1)单一职责原则(Single-Resposiblity-Principle):一个类应该仅有一个引起它变化的原因
- (2)开放封闭原则(Open-Closed-Principle):对扩展开放，对更改时封闭的
- (3)里氏替换原则(Liskov-Substituion Principle):子类可以替换父类，并且出现在父类能够出现的任何地方。GOF倡导面向接口编程
- (4)接口隔离原则(Interface-Segregation Principle)：使用多个接口比使用单个接口要好的多。
- (5)依赖倒置原则(Dependecy-Invarsion Principle):让高层模块不要依赖低层模块。

**3、final, finally, finalize 的区别**[参考](https://www.jianshu.com/p/59b77edd3319)

1、final修饰符(关键字)

final用于控制成员、方法、或者是一个类是否可以被重写或者继承功能。

(1)、如果类被声明为final，意味着它不能被派生出新的子类，不能作为父类被继承。
(2)、将变量或方法声明为final，可以保证他们在使用中不会被改变，其初始化可以在两个地方：
- 在final定义时直接给赋值，
- 在构造函数中，二者只能选其一，在以后的引用中只能读取，不可修改

2、finally(用于异常处理)
一般是用于异常处理中，提供finally块来执行任何的清楚操作，try{}catch{}finally{}.finally结构使代码块总会执行，不管有无异常发生。使得finally可以维护对象的内部状态，并可以清理非内存资源。用于关闭文件的读写操作或者关闭数据库连接操作。

3、finalize(用于垃圾回收)

finalize这个是方法名。在Java中，允许使用finalize()方法在垃圾收集器将对象从内存中清理出去之前做必要的清理工作。这个方法是由垃圾收集器在确定这个对象没有被引用时对这个对象调用的。它是Object中定义的。因此，所有类都继承了它，finalize方法是在垃圾收集器删除对象之前对这个对象调用的。

**4、int 和 Integer 有什么区别**[参考](http://www.cnblogs.com/shenliang123/archive/2011/10/27/2226903.html)

两者最大的区别从大的方法来说就是基本类型与其包装类的区别

int是基本类型，直接存数值，而Integer是对象，用一个引用指向这个对象。

Java中的数据类型分为基本数据类型和复杂数据类型

int是前者，而Integer是后者(是一个类)，在进行初始化时，int的变量被初始化为0，而Interger的变量则被初始化null。

**5、重载和重写的区别**【[参考](https://www.cnblogs.com/bluestorm/archive/2012/03/01/2376236.html)

重载(OverLoad)

(1)、方法重载是让类以统一的方式处理同步类型数据的一种手段。在多个同名函数同时存在，具有不同的参数个数、类型。重载(Overload)是一个类中多态性的一种表现。

(2)、Java方法的重载，就是在类中可以创建多个方法，他们具有相同的名字，但是有不同的参数，以及定义。调用方法时通过传递给它们的不同参数个数和参数类型来决定具体使用那个方法，这就是多态。

(3)、重载的时候，方法名要一样，但是参数类型和个数不一样，返回值类型可以相同，也可以不相同。无法以返回值作为重载函数的区别标准

重写(Override)

(1)、父类和子类之间的多态性，对父类的函数进行重新定义。如果子类定义的方法和父类具有相同的方法名和参数一样，我们就说该方法被重写(Override).在Java中，子类可继承父类中的方法，而不需要重新编写相同的方法，但有时子类并不想原封不动地继承父类方法，而是想做一定的修改，这就需要方法重写，方法重写又被称为方法覆盖。

(2)、若子类中方法与父类的某个方法具有相同的名称、返回值、和参数列表，则新方法 将覆盖原有的方法。如需父类中的原有方法，可以使用super关键字，该关键字引用了当前类的父类。

(3)、子类函数的访问修饰权限不能少于父类 。


两者之间的区别在于：

重写多态性起作用，对调用被重载过的方法可以大大减少代码的输入量，同一个方法名只要往里面传递不同的参数就可以拥有不同的功能或返回值

**6、抽象类和接口有什么区别**[参考](http://www.importnew.com/12399.html)

抽象类是用来捕捉子类的通用特性的。它不能被实例化，只能被用作子类的超类。抽象类是被用来创建继承层级里的子类的模板。

接口是抽象方法的集合，如果一个类实现类某个接口，那么他就继承了这个接口的抽象方法。这就像契约模式。如果实现了这个接口，那么就必须确保使用这些方法。接口只是一种形式，接口自身不能做任何事情。

|参数 | 抽象类 | 接口|
|-----: | :-----:| :------:|
默认的方法实现 | 它可以有默认的方法实现 | 接口是完全抽象的，它根本不存在方法的实现|
|实现 |  子类使用extends关键字来继承抽象类 | 子类使用implements来实现接口 |
|构造器 |  抽象类可以有构造器| 接口不能有构造器|
|修饰访问符   | 抽象方法可以有public,protected,和default  | 接口方法默认 修饰符是public  |
| 多继承  | 抽象方法可以继承一个类或实现多个接口  | 接口只可以继承一个或多个其他接口  |

什么时候使用抽象类和接口

 - 1、如果你拥有一些方法想让他们中的一些默认实现，那么使用抽象类。
 - 2、如果你想实现多重继承，那么你必须使用接口。由于java不支多继承，子类不能够继承多个类，但可以实现多个接口
 - 3、如果基本功能在不断改变，那么就需要使用抽象类。如果不断改变基本功能并且使用接口 ，那么就需要改变所有实现了该接口的类。

JDK 8中的默认方法
向接口中引入了默认方法和静态方法，以此来减少抽象类和接口之间的差异。现在我们可以为接口提供默认实现的方法来，并且不用强制来实现它。

**7、说说反射的用途及实现**[推荐看](http://www.hello-code.com/blog/java/201703/6278.html)

Java反射机制是一个非常强大的功能，在很多的项目比如Spring，Mybatis都都可以看到反射的身影。通过反射机制，我们可以在运行期间获取对象的类型信息。利用这一点我们可以实现工厂模式和代理模式等设计模式，同时也可以解决java泛型擦除等令人苦恼的问题。

获取一个对象对应的反射类，在Java中有三种方法可以获取一个对象的反射类，
- 通过getClass()方法
- 通过Class.forName()方法；
- 使用类.class
- 通过类加载器实现，getClassLoader()

**8、说说自定义注解的场景及实现**[推荐，播客也推荐](http://linbinghe.com/2017/ac8515d0.html)

跟踪代码的依赖性，实现代替配置文件的功能。比较常见的是Spring等框架中的基于注解配置。

还可以生成文档常见的@See@param@return等。如@override放在方法签名，如果这个方法 并不是覆盖了超类方法，则编译时就能检查出。

使用@interface自定义注解时，自动继承了java.lang.annotation.Annotation接口，由编译程序自动完成其他细节，在定义注解时，不能继承其他注解或接口。


**9、HTTP 请求的 GET 与 POST 方式的区别**[参考](http://www.w3school.com.cn/tags/html_ref_httpmethods.asp)
在客户机和服务器之间进行请求-响应时，两种最常被用到的方法是：GET 和 POST。
- GET - 从指定的资源请求数据。
- POST - 向指定的资源提交要被处理的数据

GET方法

请注意，查询字符串（名称/值对）是在 GET 请求的 URL 中发送的：
```xml
/test/demo_form.asp?name1=value1&name2=value2
```
- 请求可被缓存
-  请求保留在浏览器历史记录中
-  请求可被收藏为书签
- 请求不应在处理敏感数据时使用
- 请求有长度限制
- 请求只应当用于取回数据


POST方法

请注意，查询字符串（名称/值对）是在 POST 请求的 HTTP 消息主体中发送的：
```xml
POST /test/demo_form.asp HTTP/1.1
Host: w3schools.com
name1=value1&name2=value2
```

比较 GET 与 POST

|方法 | GET | POST|
----- | :-----:| :------:|
 缓存  | 能被缓存  | 不能缓存  |
|编码类型   |  application/x-www-form-urlencoded | 	application/x-www-form-urlencoded 或 multipart/form-data。为二进制数据使用多重编码。  |
|对数据长度的限制   |  是的。当发送数据时，GET 方法向 URL 添加数据；URL 的长度是受限制的（URL 的最大长度是 2048 个字符） | 无限制。  |
|  对数据类型的限制 | 只允许 ASCII 字符  | 没有限制。也允许二进制数据。|
|安全性   | 与 POST 相比，GET 的安全性较差，因为所发送的数据是 URL 的一部分。在发送密码或其他敏感信息时绝不要使用 GET  | POST 比 GET 更安全，因为参数不会被保存在浏览器历史或 web 服务器日志中。  |
|可见性   | 数据在 URL 中对所有人都是可见的。  | 数据不会显示在 URL 中。  |

其他 HTTP 请求方法
- HEAD	与 GET 相同，但只返回 HTTP 报头，不返回文档主体。
- PUT	上传指定的 URI 表示。
- DELETE	删除指定资源。
- OPTIONS	返回服务器支持的 HTTP 方法
- CONNECT	把请求连接转换到透明的 TCP/IP 通道。


**10、session 与 cookie 区别**[参考，不错](https://showcc.github.io/2017/09/10/cookie%20and%20session/)

1. cookie数据存放在客户的浏览器上，session数据放在服务器上。
2. cookie不是很安全，别人可以分析存放在本地的COOKIE并进行COOKIE欺骗考虑到安全应当使用session。
3. session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能考虑到减轻服务器性能方面，应当使用COOKIE。
4. 单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。
5. 所以个人建议：
   将登陆信息等重要信息存放为SESSION
   其他信息如果需要保留，可以放在COOKIE中

**11、session 分布式处理**[参考，不错](https://my.oschina.net/u/1774673/blog/871912)

第一种：粘性session

粘性Session是指将用户锁定到某一个服务器上，比如上面说的例子，用户第一次请求时，负载均衡器将用户的请求转发到了A服务器上，如果负载均衡器设置了粘性Session的话，那么用户以后的每次请求都会转发到A服务器上，相当于把用户和A服务器粘到了一块，这就是粘性Session机制


第二种：服务器session复制

原理：任何一个服务器上的session发生改变（增删改），该节点会把这个 session的所有内容序列化，然后广播给所有其它节点，不管其他服务器需不需要session，以此来保证Session同步。


第三种：session共享机制

使用分布式缓存方案比如memcached、Redis，但是要求Memcached或Redis必须是集群。

原理：不同的 tomcat指定访问不同的主memcached。多个Memcached之间信息是同步的，能主从备份和高可用。用户访问时首先在tomcat中创建session，然后将session复制一份放到它对应的memcahed上

第四种：session持久化到数据库

原理：就不用多说了吧，拿出一个数据库，专门用来存储session信息。保证session的持久化。 优点：服务器出现问题，session不会丢失 缺点：如果网站的访问量很大，把session存储到数据库中，会对数据库造成很大压力，还需要增加额外的开销维护数据库。

第五种terracotta实现session复制

原理：就不用多说了吧，拿出一个数据库，专门用来存储session信息。保证session的持久化。 优点：服务器出现问题，session不会丢失 缺点：如果网站的访问量很大，把session存储到数据库中，会对数据库造成很大压力，还需要增加额外的开销维护数据库


**12、JDBC 流程**[](http://www.cnblogs.com/lazycoding/archive/2011/04/05/jdbc_process.html)

注意：在此之前应该先把所有用到的对象设为null

（1）向DriverManager类注册驱动数据库驱动程序，
```java
Class.forName( "com.somejdbcvendor.TheirJdbcDriver" );
```
（2）调用DriverManager.getConnection方法， 通过JDBC URL，用户名，密码取得数据库连接的Connection对象。

```java
Connection conn = DriverManager.getConnection(
      "jdbc:somejdbcvendor:other data needed by some jdbc vendor", //URL
       "myLogin", // 用户名
      "myPassword" ); // 密码
```
（3）获取Connection后， 便可以通过createStatement创建Statement用以执行SQL语句。下面是一个插入（INSERT）的例子：

```java
Statement stmt = conn.createStatement();
 stmt.executeUpdate( "INSERT INTO MyTable( name ) VALUES ( 'my name' ) " );
```
（4）有时候会得到查询结果，比如select，得到查询结果，查询（SELECT）的结果存放于结果集（ResultSet）中。
```java
ResultSet rs = stmt.executeQuery( "SELECT * FROM MyTable" );
```
（5）关闭数据库语句，关闭数据库连接。
```java
rs.close();
stmt.close();
```
**13、MVC 设计思想**

每当用户在Web浏览器中点击链接或提交表单的时候，请求就开始工作了。请求是一个十分繁忙的家伙，从离开浏览器开始到获取响应返回，它会经历很多站，在每站都会留下一些信息，同时也会带上一些信息。

![](https://i.imgur.com/5cHxVCF.png)

Spring工作流程描述[原文在这里](http://blog.csdn.net/zuoluoboy/article/details/19766131)

- 1. 用户向服务器发送请求，请求被Spring 前端控制Servelt DispatcherServlet捕获；

- 2. `DispatcherServlet`对请求URL进行解析，得到请求资源标识符（URI）。然后根据该URI，调用HandlerMapping获得该Handler配置的所有相关的对象（包括Handler对象以及Handler对象对应的拦截器），最后以`HandlerExecutionChain`对象的形式返回；

- 3. `DispatcherServlet` 根据获得的Handler，选择一个合适的HandlerAdapter。（附注：如果成功获得HandlerAdapter后，此时将开始执行拦截器的preHandler(...)方法）
-  4.  提取Request中的模型数据，填充Handler入参，开始执行Handler（Controller)。 在填充Handler的入参过程中，根据你的配置，Spring将帮你做一些额外的工作：
    - HttpMessageConveter： 将请求消息（如Json、xml等数据）转换成一个对象，将对象转换为指定的响应信息
    -  数据转换：对请求消息进行数据转换。如String转换成Integer、Double等
    -  数据根式化：对请求消息进行数据格式化。 如将字符串转换成格式化数字或格式化日期等
    -  数据验证： 验证数据的有效性（长度、格式等），验证结果存储到BindingResult或Error中
- 5.  Handler执行完成后，向DispatcherServlet 返回一个ModelAndView对象；
- 6.  根据返回的ModelAndView，选择一个适合的ViewResolver（必须是已经注册到Spring容器中的ViewResolver)返回给DispatcherServlet ；
- 7. ViewResolver 结合Model和View，来渲染视图
- 8. 将渲染结果返回给客户端。

[图片参考这里](http://blog.csdn.net/zuoluoboy/article/details/19766131)

![](https://i.imgur.com/DaqEiyL.png)


Spring工作流程描述
- 为什么Spring只使用一个Servlet(DispatcherServlet)来处理所有请求？
- 详细见J2EE设计模式-前端控制模式
- Spring为什么要结合使用`HandlerMapping`以及`HandlerAdapter`来处理Handler?
- 符合面向对象中的单一职责原则，代码架构清晰，便于维护，最重要的是代码可复用性高。如`HandlerAdapter`可能会被用于处理多种Handler。

----
1、请求旅程的第一站是Spring的`DispatcherServlet`。与大多数基于Java的Web框架一样，Spring MVC所有的请求都会通过一个前端控制器(front contrller)Servlet.前端控制器是常用Web应用程序模式。在这里一个单实例的Servlet将请求委托给应用的其他组件来执行实际的处理。在Spring MVC中，DisPatcherServlet就是前端控制器。


2、DisPactcher的任务是将请求发送Spring MVC控制器(controller).控制器是一个用于处理请求的Spring组件。在典型的应用中可能会有多个控制器，`DispatcherServlet`需要知道应该将请求发送给那个哪个控制器。所以Dispactcher以会查询一个或 多个处理器映射(Handler mapping),来确定请求的下一站在哪里。处理映射器根据请求携带的 URL信息来进行决策。

3、一旦选择了合适的控制器，`DispatcherServlet`会将请求发送给选中的控制器。到了控制器，请求会卸下其负载(用户提交的信息)并耐心等待控制器处理这些信息。(实际上，设计良好的控制器 本身只是处理很少，甚至不处理工作，而是将业务逻辑委托给一个或多个服务器对象进行处理)

4、控制器在完成处理逻辑后，通常会产生一些信息。这些 信息需要返回给 用户，并在浏览器上显示。这些信息被称为模型(Model),不过仅仅给用户返回原始的信息是不够的----这些信息需要以用户友好的方式进行格式化，一般会是HTML。所以，信息需要发送一个视图(View),通常会是JSP。

5、 控制器做的最后一件事就是将模型打包，并且表示出用于渲染输出的视图名。它接下来会将请求连同模型和视图发送回DispatcherServlet。

6、这样，*控制器就不会与特定的视图相耦合**传递给控制器的视图名并不直接表示某个特定的jsp。实际上，它甚至并不能确定视图就是JSP。相反，它仅仅传递了一个逻辑名称，这个名字将会用来查找产生结果的真正视图。DispatcherServlet将会使用视图解析器(View resolver),来将逻辑视图名称匹配为一个特定的视图实现，他可能也可能不是JSP

7、虽然DispatcherServlet已经知道了哪个驶入渲染结果、那请求的任务基本上也就完成了，它的最后一站是试图的实现。在这里它交付给模型数据。请求的任务就结束了。视图将使用模型数据渲染输出。这个输出通过响应对象传递给客户端(不会像听上去那样硬编码)

可以看到，请求要经过很多步骤，最终才能形成返回给客户端的响应，大多数的 步骤都是在Spirng框架内部完成的。

**14、equals 与 == 的区别[参考](http://www.importnew.com/6804.html)

- 1、使用==比较原生类型如：boolean、int、char等等，使用equals()比较对象。
- 2、==返回true如果两个引用指向相同的对象，equals()的返回结果依赖于具体业务实现
- 3、字符串的对比使用equals()代替==操作符
其主要的不同是一个是操作符一个是方法，==用于对比原生类型而equals()方法比较对象的相等性。
-----

### 有兴趣可以看下我的解答，没有对比就没伤害。
##### 1、软实力

**1、说说你的亮点**

之前一个人徒搭川藏线、青藏线。当凌晨站在布达拉宫的广场时，哪种成就感无法比喻，只能经历过的人才能体会到。经历过底层的生活，去过边陲云南，也去过北上杭。体验了一回流浪汉给让铺位的经历。让我对这个世界有了全新的认识。(这里只想提示面试官我有坚毅、不怕吃苦、有善心的品质)

技术方面：目前不才，没有解决过重大问题的经历。有一颗持续学习的心(英语很重要，很重要，很重要)。以后会养成一个写播客的习惯，混迹于GitHub。

**2、说说你最近在看什么书**

《Spring 实战》，这本书写的非常不错,深入的阐述了Spring的IOC和AOP特性。讲解了Spring生态系统中常用的组件。结合作者的[GitHub](https://github.com/habuma)代码示例，学习起来效果很好。

下一本会是《Spring Boot实战》

下下一本会是《Netty 实战》看第一章就深深的迷上了。

**3、说说你觉得最有意义的技术书籍**

个人认为是 Xxx是怎么Xx的(日系)。Xxx实战系列。Xxx权威指南，国产深入Xxx也不错。还有一些是计算机底层的书籍。

**4、工作之余做什么事情**

目前没工作，除了学习还是学习。假设有了工作，会学习英语，为自己的三年计划做准备。时不时会跑回去看父母(飞机)。

**5、说说个人发展方向方面的思考**

最近"移民"关键字很火热。会在国内待三年，让自己能独当一面。会在国外发展自己的仕途，在技术的路上一道走到黑。

**6、说说你认为的服务端开发工程师应该具备哪些能力**

网络必备，高并发，JVM必会，各种分布式技术，看源码的能力。

**7、说说你认为的架构师是什么样的，架构师主要做什么**

技术大拿，在多个领域有深入的研究。协调各个技术专家可以很好的一起工作。特定领域的架构师职能不一样，网络，底层，数据库。在一个点上可以独当一面，解决各大重大问题。

**8、说说你所理解的技术专家**

混迹于战场最起码十年，而且是在特定领域有自己独特的理解。对细节问题的掌握，遇到的问题比别人多，解决的问题也比别人多。假设是Java技术专家，JKD源码，JVM，设计模式(不是记住，应用到项目中)。对特大项目重构。越厉害，越底层。当有一天你什么都不懂了，就成技术专家了。


##### 基本功

**1、面向对象的特征**

讲特征之前你得知道什么是面对对象吧，面向对象OO = 面向对象设计OOD + 面向对象分析OOA + 面向对象编程OOP。还有什么面相呢？面向过程编程、面向接口编程、面向切面编程AOP、面向资源编程。什么是对象？对象怎么产生的？new Class啊(内省反射机制，容器)。对象定义了什么？之间有什么联系？对象是对现实世界的抽象。对象是由类实例化产生的，描述了类的一些属性和行为。是强耦合，还是虚耦合？是继承关系还是组合关系(is-a,has-a)？

- 继承：子类(衍生类)继承父类(超类)用来延续父类功能，子类本身也可以增强。所有类都继承自Object。单继承局限，为啥所有类都要继承Object？如何实现多继承呢？是用继承好还是组合(聚合)好？委托？

- 封装：你可能听过给我封装一个工具类，为什么要封装？解耦。怎么封装？抽取。封装方法还是封装类？如何隐藏自己，改变的同时不影响到别人？4个关键字，public，private...
- 多态：一种事物所呈现出不同的状态，人会吃，会跑，会跳，会睡？根据大脑给它传递什么消息。这里涉及到转型，向上转安全吗？向下呢？(no,yes)。这样会丢失对象一些特性。

**2、final, finally, finalize 的区别**

- final:最终的，修饰常量，final static。用大写字母描述。静态的不变的。在哪里会用到全局变量？局部呢？修饰方法，子类不能被覆盖(重写)，修饰类(父类不能被继承) String类被final了。为什么要这样设计？性能，安全、池。
- finally：一般在try{}catch{}finally{}中释放资源，IO，线程。不管如何总是会执行？真的吗，未必。还需要判断，非空，在try一次。JDK 8可以直接放在try(...){}catch{}

finalize:是一个本地方法，由JVM full GC的时候调用清理不再存活的对象。什么时候执行？一次两次？

**3、int 和 Integer 有什么区别**
前者是基本数据类型，后置是引用数据类型，之间如何转换的？能放到集合中吗？JDK 1.5自动装箱、拆箱。还有一点到底是值传递还是引用传递啊？

**4、重载和重写的区别**

- 用在多态上。方法名相同，参数列表、属性不同的方法。根据传参不同选择合适的方法。构造函数也是
- 重写：用在继承。方法名相同，参数也一样。父类的方法不能满足需求时，加以增强补充。用的时候到底调用子类还是父类的啊？super，this。这里会涉及到类的加载过程？还有static代码块。


**5、抽象类和接口有什么区别**

- 抽象类：用abstract修饰的类叫抽象类，定义类的时候往上层抽象，子类继承的时候必须全部实现，如不，那也是一个抽象类。类和接口之间的桥梁？
- 接口：用interface修饰定义了一些标准方法，方法默认是public abstract修饰的，没有方法体。JDK 8可以包含默认方法，有什么作用？要么全部实现，要么都不实现。但默认方法来了。避免单继承局限，可以实现多个接口

两者都不能被实例化，一个用来被继承，一个用来被实现。到底用哪个好？取决于你的类的设计。面向接口编程。中间过渡抽象类。顶层接口项目一般会有一个抽象类。在往下才是实现类。

**6、说说反射的用途及实现**
 要是没反射+泛型这个世界会变的怎样？在运行时动态的创建对象，通过类的全限定名我们可以知道类的任何信息。字段，方法、构造方法、异常、注解。几乎每个框架都几乎反射+泛型实现的。还有动态代理。底层使用静态代码块实现，。实现方法是有四种：类.class,类.getClass()，Class.forName(),还有一种是类的加载器实现，getClassloader().(启动、扩展、系统(App)).再次强调反射+泛型+代理(JDK,CGlib)很重要。

**7、说说自定义注解的场景及实现**

非常非常非常的重要，在框架中可以帮我们省去很多不必要的代码。Java规定一个类上不能出现一样的注解，那么我们就可以自定义。

```java
public interface Annotation {
    boolean equals(Object obj);
    int hashCode();
    String toString();
}
```
```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
@Inherited
public @interface RunWith {
    Class<? extends Runner> value();
}
```

**8、HTTP 请求的 GET 与 POST 方式的区别**
用于提交获取表单、资源。主要区别在于地址栏，缓存、大小。网络知识也得好好了解。

- GET 提交的数据地址栏一般会出现键值对的形式，用“&”相连.大小也有限制(64k?)。能缓存。
- POSP 用于提交表单、上传图片。数据一般放到请求体中。大小没限制。不能被缓存。

其他的呢？put？delete，trance？ 这里又扯到TESTful风格。

**9、session 与 cookie 区别**

最大的区别在于存放的位置不同，前者在服务端，后者在本地。但是本例浏览器要是限制cookie呢？题外话：我一般会经常用[Click&Clean](https://chrome.google.com/webstore/detail/clickclean/ghgabhipcejejjmhhchfonmamedcbeod)清除cookie的。有些网站也会禁用。别问我为什么,其实并无卵用，但是cookie里保存着大量重要信息。
![](https://i.imgur.com/LCaCAkf.jpg)

- cookie ：一般存放密码，令牌之类的信息。大小有限制，在第一次请求的时候，服务端创建，返回给客户端，第二次请求浏览器带着cookie去找服务器。这里有个跨域问题？ 可以设置过期失效。浏览器对cookie的限制。大量的cookie导致传输性能。通常会采用Gzip压缩。
- Session，存放于服务端。一般用于购物车也涉及到跨域问题，可以存放到redis中，还有一种办法复制的每个tomcat实例中，现实吗？Jsession什么东东？有什么作用？

这块只是得好好补补。

**10、session 分布式处理**
哈哈，抢先回答了。大家面试的时候不要一问一答。让面试官在你的问题中选择一个解答继续深入。直到问道你不会。也可以说些自己有把握话题，引导他继续深入。

**11、JDBC 流程**
准备 private static final URL、、、 也可以用properties从文件中读取。load()、

1、首先注册驱动啊？怎么注册？反射啊，Class.forName("xx.xx.xx.Driver");底层怎么实现的？静态代码，DriverManager.registerDriver?启动的时候，会自动调用静态代码块的内容。

2、接下来就是获取连接啊，怎么连接？远程连接(三次握手操作)，连接放哪里？作为资源必须放池子里。这样能提高性能。常见的连接池有DBCP，C3P0，传说中最安全，性能最好的Druid(国产)，而且还能监控。

3、你总的有SQL语句吧，之后就是Statement编译那。这里会出现SQL注入的安全问题。在语句后面加"1=1"成立。所以我们采用预编译的方式，PreparedStatement。可以防止这种问题的出现。

4、查完之后获取结果集。rs.getString().

5、头疼的来了，释放资源。各种 if(xx != nu) {try{ xx.close();}catch{}} 不用担心JDK8 出来一个新特性，可以放在try-withresource中。还有各种异常可以采用通道的形式 XxxException | XxxException

6、各种异常需要你放到一个try{}catch{}中，出问题你也不知道问题在哪里？

麻烦吗？不用担心，我们可以封装成一个工具类，需要的时候调用工具类.getConnection();

还是麻烦啊，可以用Spring框架为我们集成提供了jdbcTemplate，HibernaterTemplate。用模板代码消除了大量的样板代码。

为啥不早告诉我JDBC连接这么简单？同志们，我们需要知其然的同时，还要知其所以然。这样出现问题的时候才能找到更好的解决方法。

**12、MVC 设计思想**

什么是设计思想？前人踩过无数的坑，总结出来的真理。一般用来解决特定问题。需要好好学习设计模式，框架中大量采用.

那MVC又是什么东东？

回答之前我们先看看设计的原则。单一职责，开闭原则，面向接口编程，对象最少知道。一句话总结：“高内聚，低耦合”。六个字一个逗号。

- Model(模型层) ：一般存放处理逻辑，
- View (视图层)：存放html，jsp，文件
- Controller(控制层)：主要负责调度两者，实现解耦。

当我们像浏览器发送一个请求时，首先需要经过控制层(DispatcherServlet),其是它实际不做什么事情，委托给别人做。调用模型层(处理一些业务逻辑)，返回数据模型给控制器，接着在委托视图解析器解析视图。最后定位到视图的资源，返回给控制器，控制器在返回给客户端。(其实需要做的还有很多)

主要的目的是解耦，各司其职。做好你份内的事。对扩展性也好。增加需求不会影响到其他模块。

**13、equals 与 == 的区别**

- == 比较的是地址，具体来说就是存放在栈中的引用。
- equsls 比较的是内容。一般我们同时需要重写hashcode()方法，其底层是用“==”

这里分两种情况，基本类型和引用类型的比较。还会涉及到一个常量池(提高性能)。还有入池操作。还有四条原则，自反，传递，。。
