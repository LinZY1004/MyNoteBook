1、概述
----

### 1.1、简介

*   Spring：春天------>给软件行业带来了春天
*   2002，首次推出了Spring框架的雏形，interface21框架
*   Spring框架即以interface21框架为基础，重新设计，并不断丰富其内涵，于2004年3月24日，发布了1.0正式版
*   Rod Johnson，Spring Framework创始人，著名作者。很难想象Rod Johnson的学历，真的让好多人大吃一惊，他是悉尼大学的博士，然而他的专业不是计算机，而是音乐学。
*   Spring理念：使现有技术更加容易使用，本身是一个大杂烩，整合了现有的技术框架！
*   SSH: Struct2 + Spring +Hibernate
*   SSM SpringMVC + Spring + Mybatis

官网：https://spring.io/projects/spring-framework#learn

官方下载地址：https://repo.spring.io/release/org/springframework/spring/

GitHub ：https://github.com/spring-projects/spring-framework/

依赖

```xml

<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>5.2.7.RELEASE</version>
</dependency>


```

### 1.2、优点

*   Spring是一个开源的免费的框架（容器）
*   Spring是一个轻量级的、非入侵式的框架
*   **控制反转（IOC）,面向切面编程（AOP）**
*   支持事务的处理，对框架整合的支持

**总结：Spring就是一个轻量级的控制反转（IOC）和面向切面编程（AOP）的框架**

### 1.3、组成

Spring 框架是一个分层架构，由 7 个定义良好的模块组成。Spring 模块构建在核心容器之上，核心容器定义了创建、配置和管理 bean 的方式

![](https://img-blog.csdnimg.cn/20200702090321754.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

**核心容器（Spring Core）**

核心容器提供Spring框架的基本功能。Spring以bean的方式组织和管理Java应用中的各个组件及其关系。Spring使用BeanFactory来产生和管理Bean，它是工厂模式的实现。BeanFactory使用控制反转(IoC)模式将应用的配置和依赖性规范与实际的应用程序代码分开。

**应用上下文（Spring Context）**

Spring上下文是一个配置文件，向Spring框架提供上下文信息。Spring上下文包括企业服务，如JNDI、EJB、电子邮件、国际化、校验和调度功能。

**Spring面向切面编程（Spring AOP）**

通过配置管理特性，Spring AOP 模块直接将面向方面的编程功能集成到了 Spring框架中。所以，可以很容易地使 Spring框架管理的任何对象支持 AOP。Spring AOP 模块为基于 Spring 的应用程序中的对象提供了事务管理服务。通过使用 Spring AOP，不用依赖 EJB 组件，就可以将声明性事务管理集成到应用程序中。

**JDBC和DAO模块（Spring DAO）**

JDBC、DAO的抽象层提供了有意义的异常层次结构，可用该结构来管理异常处理，和不同数据库供应商所抛出的错误信息。异常层次结构简化了错误处理，并且极大的降低了需要编写的代码数量，比如打开和关闭链接。

**对象实体映射（Spring ORM）**

Spring框架插入了若干个ORM框架，从而提供了ORM对象的关系工具，其中包括了Hibernate、JDO和 IBatis SQL Map等，所有这些都遵从Spring的通用事物和DAO异常层次结构。

**Web模块（Spring Web）**

Web上下文模块建立在应用程序上下文模块之上，为基于web的应用程序提供了上下文。所以Spring框架支持与Struts集成，web模块还简化了处理多部分请求以及将请求参数绑定到域对象的工作。

**MVC模块（Spring Web MVC）**

MVC框架是一个全功能的构建Web应用程序的MVC实现。通过策略接口，MVC框架变成为高度可配置的。MVC容纳了大量视图技术，其中包括JSP、POI等，模型来有JavaBean来构成，存放于m当中，而视图是一个街口，负责实现模型，控制器表示逻辑代码，由c的事情。Spring框架的功能可以用在任何J2EE服务器当中，大多数功能也适用于不受管理的环境。Spring的核心要点就是支持不绑定到特定J2EE服务的可重用业务和数据的访问的对象，毫无疑问这样的对象可以在不同的J2EE环境，独立应用程序和测试环境之间重用。

### 1.4、拓展

Spring的官方介绍：现代化的Java开发，说白了就是基于Spring的开发

![](https://img-blog.csdnimg.cn/2020070209033015.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

*   Spring Boot
    *   一个快速开发的脚手架
    *   基于Spring Boot可以快速的开发单个微服务
    *   约定大于配置
*   Spring Cloud
    *   Spring Cloud是基于SpringBoot实现的

因为现在大多数公司都在使用Spring Boot进行快速开发，学习Spring Boot的前提，需要完全掌握Spring及SpringMVC！承上启下的作用

弊端：发展太久之后，违背了原来的理念，配置十分繁琐，人称：配置地狱

### 1.5、BeanFactory&ApplicationContext

![img](https://gitee.com/xiaoyuan_students_oo/Typora-picture1/raw/master/2021/20210511093756.jpeg)

ApplicationContext继承了HierarchicalBeanFactory和ListableBeanFactory，也就是说前面看到的接口特性都被ApplicationContext继承下来了，另外通过类图可以发现，ApplicationContext还继承了诸如Environment、Resource、Message、Event等相关的接口，也就是说**除了bean的管理配置相关的能力，ApplicationContext还拥有Environment（环境）、MessageSource（国际化）、ResourceLoader（资源）、ApplicationEventPublisher（应用事件**）等服务相关的接口，简单的说ApplicationContext是以bean管理为基础的综合能力扩展，用于满足业务对Spring综合能力的需要；

除了继承，它自身也提供了一些扩展的能力：

```java
public interface ApplicationContext extends EnvironmentCapable, ListableBeanFactory, HierarchicalBeanFactory,
        MessageSource, ApplicationEventPublisher, ResourcePatternResolver {

    //标识当前context实例的id，最终会通过native方法来生成：System.identityHashCode
    String getId();

    //返回该context所属的应用名称，默认为空字符串，在web应用中返回的是servlet的contextpath 
    String getApplicationName();

    //返回当前context的名称
    String getDisplayName();

    //返回context第一次被加载的时间
    long getStartupDate();

    //返回该context的parent
    ApplicationContext getParent();

    //返回具有自动装配能力的beanFactory，默认返回的就是初始化时实例化的beanFactory
    AutowireCapableBeanFactory getAutowireCapableBeanFactory() throws IllegalStateException;
}
```

小结：
1. BeanFactory是基础，BeanFactory和它的子接口定义的API满足了spring环境中对bean管理和配置的需求；
2. ApplicationContext是扩展，以BeanFactory为主线，通过继承的方式综合了环境、国际化、资源、事件等多条支线，自己又规定了一些扩展服务（如返回context的id，应用名称等），而所有支线都以bean服务为基础；

2、IOC理论推导
---------

### IOC基础

在我们之前的业务中

1、UserDao接口

```java
public interface UserDao {
    void getData();
}

```

2、UserDaoImpi实现类

```java
public class UserDaoImpl implements UserDao{
    public void getData() {
        System.out.println("dao数据");
    }
}

```

3、UserService业务接口

```java
public interface UserService {
    void getData();
}

```

4、UserServiceImpl业务实现类

```java
public class UserServiceImpl implements UserService{
    
    private UserDao userDao = new UserDaoImpl;
    public void getData() {
        userDao.getData();
    }
}

```

5、测试

```java
@Test
public void getDate(){
    UserServiceImpl userService = new UserServiceImpl();
    userService.getData();
}

```

如果现在出现别的需求，需要再加dao实现类

```java
public class UserDaoMySqlImpl implements UserDao{
    public void getData() {
        System.out.println("mysql数据");
    }
}

```

```java
public class UserDaoOracleImpl implements UserDao{
    public void getData() {
        System.out.println("oracle数据");
    }
}

```

```java
public class UserDaoSqlServerImpl implements UserDao{
    public void getData() {
        System.out.println("sqlServer数据");
    }
}

```

那要想实现用户的需求就需要我们修改UserServiceImpl业务实现类里源代码

```java
public class UserServiceImpl implements UserService{
    private UserDao userDao = new UserDaoMySqlImpl;
    public void getData() {
        userDao.getData();
    }
}

```

```java
public class UserServiceImpl implements UserService{
    private UserDao userDao = new UserDaoOracleImpl;
    public void getData() {
        userDao.getData();
    }
}

```

```java
public class UserServiceImpl implements UserService{
    private UserDao userDao = new UserDaoSqlServerImpl;
    public void getData() {
        userDao.getData();
    }
}

```

那么用户的每一次需求都需要我们去修改源代码，这显然是不现实的

总结:

用户的需求可能会影响我们原来的代码，我们需要根据用户的需求去修改源代码，如果程序代码量十分大，修改一次的成本代价十分昂贵

解决：

我们在UserServiceImpl使用一个Set接口实现，已经发生了革命性的变化！

```java
private UserDao userDao;

public void setUserDao(UserDao userDao) {
    this.userDao = userDao;
}

```

测试：

```java
@Test
public void getDate(){
    UserServiceImpl userService = new UserServiceImpl();
    
    
    userService.setUserDao(new UserDaoMySqlImpl());
    userService.getData();
    
    userService.setUserDao(new UserDaoOracleImpl());
    userService.getData();
    
    userService.setUserDao(new UserDaoSqlServerImpl());
    userService.getData();
}

```

*   之前，程序是主动创建对象！控制权在程序员手上

![](https://img-blog.csdnimg.cn/20200702105012653.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

*   使用了set注入后，程序不在具有主动性，而是变成了被动的接受对象

![](https://img-blog.csdnimg.cn/20200702105019416.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

这种思想，从本质上解决了问题，我们程序员不用再去管理对象的创建了。系统的耦合性大大降低，可以更加专注的在业务的实现上！这是IOC的原型

### IOC本质

![](https://img-blog.csdnimg.cn/20200702105041999.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

**控制反转IOC（inversion of Control）是一种设计思想，DI（依赖注入）是实现IOC的一种方法**，也有人认为DI知识IOC的另一种说法，没有IOC的程序中,我们将使用面向对象编程，对象的创建与对象间的依赖关系完全硬编码在程序中，对象的创建由程序自己控制，控制反转后将对象的创建转移给第三方，个人认为所谓控制反转就是：获得依赖对象的方式反转了

采用XML方式配置Bean的时候，Bean的定义信息是和现实分离的，而采用注解的方式可以把两者合为一体，Bean的定义信息直接以注解的形式定义在实现类中，从而达到了零配置的目的

**控制反转是一种通过描述（xml或注解）并通过第三方去生产或获取特定对象的方式，在Spring中实现控制反转的是IOC容器，其实现方法是依赖注入（Dependency Injection，DI）**

3、HelloSpring
-------------

新建一个子项目

新建一个实体类Hello

```java
public class Hello {
    private String str;

    public String getStr() {
        return str;
    }

    public void setStr(String str) {
        this.str = str;
    }

    @Override
    public String toString() {
        return "Hello{" +
                "str='" + str + ''' +
                '}';
    }
}

```

从Spring官网拷贝最新配置文件到resources目录下这里命名为beans.xml

使用Spring来创建对象，并为Hello中的str赋值

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    <!--使用Spring来创建对象，在Spring这些都称为Bean
        类型 变量名 = new 类型();
        Hello hello = new Hello();

        id = 变量名
        class = new的对象
        property相当于给对象中的属性设置一个值
        -->
    <bean id="hello" class="com.chenjlong.pojo.Hello">
        <property name="str" value="Spring"/>
    </bean>

</beans>

```

测试

```java
public class MyTest {
    @Test
    public void Hello(){
        
        ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
        
        Hello hello = (Hello) context.getBean("hello");
        System.out.println(hello);

    }
}

```

思考：

*   Hello 对象是谁创建的 ?
    *   Hello 对象是由Spring创建的
*   Hello 对象的属性是怎么设置的 ?
    *   Hello 对象的属性是由Spring容器设置的

这个过程就叫控制反转 :

*   控制 : 谁来控制对象的创建 , 传统应用程序的对象是由程序本身控制创建的 , 使用Spring后 , 对象是由Spring来创建的
*   反转 : 程序本身不创建对象 , 而变成被动的接收对象 .

依赖注入 : 就是利用set方法来进行注入的.

IOC是一种编程思想，由主动的编程变成被动的接收

可以通过newClassPathXmlApplicationContext去浏览一下底层源码 .

修改刚才的推导案例

从Spring官网拷贝最新配置文件到resources目录下这里命名为beans.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    
    <bean id="mySqlImpl" class="com.chenjlong.dao.UserDaoMySqlImpl"/>
    <bean id="oracleImpl" class="com.chenjlong.dao.UserDaoOracleImpl"/>
    <bean id="sqlServerImpl" class="com.chenjlong.dao.UserDaoSqlServerImpl"/>
    
    <bean id="userService" class="com.chenjlong.service.UserServiceImpl">
        <property name="userDao" ref="sqlServerImpl"/>
    </bean>



</beans>

```

测试

```java
public class UserDaoTest {
    @Test
    public void getDate(){
        ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
        UserServiceImpl userService= (UserServiceImpl) context.getBean("userService");
        userService.getData();
    }
}

```

到了现在 , 我们彻底不用再程序中去改动了 , 要实现不同的操作 , 只需要在xml配置文件中进行修改 , 所谓的IoC,一句话搞定 : 对象由Spring 来创建 , 管理 , 装配 !

4.IOC创建对象方式
-----------

### 4.1.通过无参构造方法来创建（默认）

实体类User

```java
public class User {
    private String name;

    public User() {
        System.out.println("user无参构造方法");
    }

    public void print(){
        System.out.println("name:"+name);
    }
    public void setName(String name) {
        this.name = name;
    }
}

```

配置文件beans.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    <bean id="user" class="com.chenjlong.pojo.User">
        <property name="name" value="小陈"/>
    </bean>

</beans>

```

测试

```java
@Test
public void userTest(){
    ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
    User user = (User) context.getBean("user");
    user.print();
}

```

结果可以发现，在调用print方法之前，User对象已经通过无参构造初始化了！

### 4.2.通过有参构造方法来创建

User实体类

```java
public class User {
    private String name;

    public User(String name) {
        this.name = name;
    }

    public void print(){
        System.out.println("name:"+name);
    }
    public void setName(String name) {
        this.name = name;
    }
}

```

1、下标赋值

```xml
<bean id="user" class="com.chenjlong.pojo.User">
    <constructor-arg index="0" value="小陈"/>
</bean>

```

2、类型（不建议使用）

```xml
<bean id="user" class="com.chenjlong.pojo.User">
    <constructor-arg type="java.lang.String" value="小陈"/>
</bean>

```

3、参数名

```xml
<bean id="user" class="com.chenjlong.pojo.User">
    <constructor-arg name="name" value="小陈"/>
</bean>

```

测试代码不用改动

总结：在配置文件加载的时候，容器中管理的就已经初始化了

5.Spring配置
----------

### 5.1.别名

alias 设置别名 , 为bean设置别名

```xml

<alias name="user" alias="userNew"/>

```

### 5.2.Bean的配置

==可以设置多个别名，可以逗号分隔，空格分割，所以一般用这个==

```xml


<bean id="user" name="user1,user2,user3"> class="com.kuang.pojo.Hello">
   <property name="name" value="小陈"/>
</bean>

```

### 5.3、import

这个import，一般用于团队开发使用，他可以将多个配置文件，导入合并为一个

假设，现在项目中有多个人开发，每个人负责不同的类的开发，不同的类需要注册在不同的bean中，我们可以利用import将所有人的xml配置文件合并为一个总的

例如：

*   applicationContext.xml
  
    ```xml
    <import resource="beans01.xml"/>
    <import resource="beans02.xml"/>
    <import resource="beans03.xml"/>
    <import resource="beans04.xml"/>
    ...
    
    ```

使用的时候直接使用总的配置就可以了

6、依赖注入
------

### 6.1、构造器注入

前面已经说过了

### 6.2、Set方式注入【重点】

*   依赖注入：Set注入！
    *   依赖：bean对象的创建依赖于容器！
    *   注入：bean对象中的所有属性，由容器来注入

【环境搭建】

1、复杂环境 Address.java

```java
public class Address {
    private String address;

    public String getAddress() {
        return address;
    }

    public void setAddress(String address) {
        this.address = address;
    }

    @Override
    public String toString() {
        return "Address{" +
                "address='" + address + ''' +
                '}';
    }
}

```

2、真实测试对象 Student.java

```java
public class Student {
    private String name;  
    private Address address;  
    private String[] books; 
    private List<String> hobbies; 
    private Map<String,String> card; 
    private Set<String> games; 
    private Properties info; 
    private String wife;  
}    


```

3、applicationContext.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    <bean id="address" class="com.chenjlong.pojo.Address">
        <property name="address" value="内蒙古"/>
    </bean>
    <bean id="student" class="com.chenjlong.pojo.Student">
        
        <property name="name" value="小陈"/>
        
        <property name="address" ref="address"/>
        
        <property name="books">
            <array>
                <value>水浒传</value>
                <value>红楼梦</value>
                <value>西游记</value>
            </array>
        </property>
        
        <property name="hobbies">
            <list>
                <value>健身</value>
                <value>敲代码</value>
                <value>听音乐</value>
            </list>
        </property>
        
        <property name="card">
            <map>
                <entry key="身份证" value="150123123412341234"/>
                <entry key="银行卡" value="12341234123456"/>
            </map>
        </property>
        
        <property name="games">
            <set>
                <value>英雄联盟</value>
                <value>绝地求生</value>
            </set>
        </property>
        
        <property name="info">
            <props>
                <prop key="学号">20200001</prop>
                <prop key="姓名">小陈</prop>
                <prop key="性别">男</prop>
                <prop key="班级">001班</prop>
            </props>
        </property>
        
        <property name="wife">
            <null/>
        </property>
    </bean>


</beans>

```

4、测试

```java
@Test
public void studentTest(){
    ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
    Student student = (Student) context.getBean("student");
    System.out.println(student);    
}

```

成功注入

### 6.3、拓展方式注入

我们可以使用p命名空间和c命名空间进行注入

官方解释：

![](https://img-blog.csdnimg.cn/20200703104951337.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

使用

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:p="http://www.springframework.org/schema/p"
       xmlns:c="http://www.springframework.org/schema/c"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    
    <bean id="pUser" class="com.chenjlong.pojo.User" p:name="小陈" p:age="18"/>
    
    <bean id="cUser" class="com.chenjlong.pojo.User" c:name="小龙" c:age="20"/>
    
</beans>

```

测试

```java
@Test
public void userTest(){
    ApplicationContext Context = new ClassPathXmlApplicationContext("userBean.xml");
    User user = Context.getBean("cUser", User.class);
    System.out.println(user);
}

```

注意点：p命名和c命名不能直接使用，需要导入xml约束

```xml
xmlns:p="http://www.springframework.org/schema/p"
xmlns:c="http://www.springframework.org/schema/c"

```

### 6.4、bean的作用域

![](https://img-blog.csdnimg.cn/20200703105002594.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

1、单例模式（Spring默认机制）：共同使用一个对象

![](https://img-blog.csdnimg.cn/20200703105012679.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

```xml
<bean id="accountService" class="com.something.DefaultAccountService" scope="singleton"/>

```

2、原型模式：每次从容器中get的时候，都会产生一个新对象

![](https://img-blog.csdnimg.cn/20200703105019215.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

```xml
<bean id="accountService" class="com.something.DefaultAccountService" scope="prototype"/>

```

3、其余的request、session、application这些只能在web开发中使用到

7、Bean的自动注入
-----------

*   自动装配是Spring满足bean依赖的一种方式！
*   Spring会在上下文中自动寻找，并自动给bean装配属性！

在Spring中有三种装配的方式

1、在xml中显示的配置

2、在java中显示配置

3、隐式的自动装配bean【重要】

### 7.1、环境搭建

一个人有两个宠物

```java
public class Person {
    private String name;
    private Cat cat;
    private Dog dog;

}

```

```java
public class Cat {
    public void shout(){
        System.out.println("喵~");
    }
}

```

```java
public class Dog {
    public void shout(){
        System.out.println("汪~");
    }
}

```

### 7.2、byName自动装配

```xml
<bean id="dog" class="com.chenjlong.pojo.Dog"/>
<bean id="cat" class="com.chenjlong.pojo.Cat"/>

<bean id="person" class="com.chenjlong.pojo.Person" autowire="byName">
    <property name="name" value="小陈"/>
</bean>

```

### 7.3、byType自动装配

```xml
<bean class="com.chenjlong.pojo.Dog"/>
<bean class="com.chenjlong.pojo.Cat"/>

<bean id="person" class="com.chenjlong.pojo.Person" autowire="byType">
    <property name="name" value="小陈"/>
</bean>

```

小结：

*   byName:需要保证所有的bean的**id唯一**，并且这个bean需要和自动注入的属性的Set方法后面值一致
*   byName:需要保证所有的bean的**class唯一**，并且这个bean需要和自动注入的属性类型一致

### 7.4、使用注解实现自动装配

jdk1.5支持的注解，Spring2.5就支持注解了

```xml
The introduction of annotation-based configuration raised the question of whether this approach is “better” than XML.    
```

要使用注解须知

1.  导入约束：context约束
  
2.  配置注解的支持：【重要】
  
    ```xml
    <context:annotation-config/>
    ```

完整配置：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        https://www.springframework.org/schema/context/spring-context.xsd">

    <context:annotation-config/>

</beans>

```

**@Autowired**

直接在属性上或者set方法上使用即可

```java
public class Person {

    private String name;
    @Autowired
    private Cat cat;
    @Autowired
    private Dog dog;
}    

```

使用@Autowired我们可以不用编写set方法了，前提是你这个自动装配的属性在IOC（Spring）容器中存在，且符合类型byType

科普：

```java
@Nullable 字段标记了这个注解，说明这个字段可以为null
```

@Autowired有一个默认的属性required，默认为true

```java
public @interface Autowired {
    boolean required() default true;
}

```

@Autowired(required=false)：表示忽略当前要注入的bean，如果有直接注入，没有跳过，不会报错。

```java
public class Person {

    private String name;
    
    @Autowired(required = false)
    private Cat cat;

    @Autowired
    private Dog dog;
}    

```

@Autowired是byType自动装配的，如果出现多个类型的时候，就需要配合另一个注解@Qualifier(value = “xxx”)，来指定name，实现唯一的bean对象注入！

```java
public class Person {

    private String name;
    
    @Autowired()
    @Qualifier(value = "xxx")
    private Cat cat;
    
    @Autowired
    @Qualifier(value = "xxx")
    private Dog dog;
}    

```

@Resource注解

```java
public class Person {

    private String name;

    @Resource(name="xxx")
    private Cat cat;
	
    @Resource(name="xxx")
    private Dog dog;
}    

```

小结：

@Resource和@Autowired的异同

*   都是用来自动装配的，都可以放在属性字段上
*   @Autowired默认通过bytype的方式实现，如果有多个类型，则通过byname实现，如果两个都找不到，就报错！
*   @Resource默认通过byname的方式实现，如果找不到名字，则通过bytype实现，如果两个都找不到，就报错！
*   执行顺序不同：
    *   @Autowired默认通过bytype的方式实现。先byType，后byName
    *   @Resource默认通过byname的方式实现。先byName，后byType
    *   类型重复的话，如果名字不是默认的（如cat11，cat111，而没有默认的cat）
        *   @Autowired配合@Qualifier(value = “cat11”)使用
        *   @Resource直接使用@Resource(name = “cat11”)

8、使用注解开发
--------

在Spring4之后要使用注解开发，必须要保证aop的包导入了

![](https://img-blog.csdnimg.cn/2020070319112926.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

使用注解需要导入conText约束，增加注解的支持

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        https://www.springframework.org/schema/context/spring-context.xsd">
	
	<context:component-scan base-package="com.chenjlong"/>
    <context:annotation-config/>

</beans>

```

1、bean

```xml
@Component
```



2、属性如何注入@Value(“xxx”)

```java
@Component
public class User {
    
    @Value("小陈")
    private String name;

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + ''' +
                '}';
    }
}

```

3、衍生的注解

@Component有几个衍生注解，我们在web开发中，会按照mvc三层架构分层

*   dao 【@Repository】
*   service 【@service】
*   controller 【@controller】
*   这四个注解的功能都是一样的，都是代表将某个类注册到Spring中，装配Bean

4、自动装配

- @Autowired : 自动装配先通过类型，后名字
    - @Autowired如果不能唯一自动装配上属性，则需要通过@Qualifier(value="xxx")
- Nullable 字段装配了这个注解，说明这个字段可以为null
- @Resource ： 自动装配先通过名字，后类型

5、作用域@Scope

```java
@Component
@Scope("singleton")
public class User {

    
    @Value("小明")
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name=name;
    }
}
```

6、小结

xml与注解：

*   xml更加万能，适用于任何场合，维护简单方便
*   注解不是自己的类用不了（ref引用无法实现），维护相对复杂
*   xml与注解的最佳实践：
    *   xml只用来管理bean
    *   注解只负责完成属性的注入
    *   我们在使用的过程中只需要注意一个问题：必须让注解生效，需要开启注解的支持

```xml

<context:component-scan base-package="com.chenjlong"/>
<context:annotation-config/>

```

9、使用Java的方式配置Spring
-------------------

我们现在要完全不使用Spring的xml配置了，全权交给Java来做

JavaConfig是Spring的一个子项目，在Spring4之后，它成为一个核心功能！

![](https://img-blog.csdnimg.cn/20200703191154882.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

实体类

```java
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;

@Component//这个实体类交给spring托管，注册到容器中

public class User {
    //属性注入值
    @Value("小龙") 
    private String name;

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + ''' +
                '}';
    }
}

```

自定义配置类（相当于配置文件）

```java
import com.chenjlong.pojo.User;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Import;


@Configuration//代表这是一个配置类，和我们之前看到的beans.xml，本质也是@component，也会被spring容器托管


@ComponentScan("com.chenjlong") //扫描该目录下的所有实体类，没有扫描也可以用
@Import(Config01.class) //导入多个配置类，相当于之前导入多个beans.xml
public class MyConfig {
    
    
    //注册一个bean，就相当于我们之前写的bean标签
    //这个方法的名称就相当于bean标签的id
    //这个方法的返回值，就相当于bean标签中的class属性
    @Bean
    	
    public User getUser(){
        return new User();
    }

}

```

测试

```java
public class MyTest {
    @Test
    public void UserTest(){
        
        
        ApplicationContext context = new AnnotationConfigApplicationContext(MyConfig.class);
        User user = context.getBean("getUser", User.class);//getUser方法名
        System.out.println(user);
    }
}

```

**这种纯Java的配置方式，在SpringBoot中随处可见**

10、代理模式
-------

为什么要学习代理模式？ 因为这就是Spring AOP的底层！

面试必问【Spring AOP和SpringMVC】

代理模式的分类：

*   静态代理
*   动态代理

![](https://img-blog.csdnimg.cn/20200704125841503.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

### 10.1、静态代理

角色分析：

*   抽象角色（这里的租房事件）：一般会使用接口或者抽象类来解决
*   真实角色（这里的房东）：被代理的角色
*   代理角色（中介）：代理真实角色，代理真实角色后，我们一般会做一些附属操作
*   客户（租房子的人）：访问代理对象的人

代码步骤：

1、接口

```java

public interface Rent {
    public void rent();
}

```

2、真实角色

```java

public class Landlord implements Rent{
    public void rent(){
        System.out.println("房子");
    }
}

```

3、代理角色

```java

public class Intermediary implements Rent {
    private Landlord landlord;

    public Intermediary() {
    }

    public Intermediary(La	ndlord landlord) {
        this.landlord = landlord;
    }
    public void seeHouse(){
        System.out.println("中介带你看房");
    }
    public void rent() {
        landlord.rent();
    }
    public void contract(){
        System.out.println("签订合同");
    }
    public void collectMoney(){
        System.out.println("中介收取房租");
    }

}

```

4、客户端访问代理角色

```java
public class Person {
    public static void main(String[] args) {
        Landlord landlord = new Landlord();
        Intermediary intermediary = new Intermediary(landlord);
        intermediary.rent();
    }
}

```

代理模式的好处：

*   可以是真实角色的操作更加纯粹，不用去关注一些公共的业务
*   公共业务就交给代理角色！实现业务的分工
*   公共业务发生拓展的时候，方便集中管理！

缺点

*   一个真实角色就会产生一个代理角色，代码量会翻倍开发效率会变低

### 10.2、加深理解

代码步骤：

1、接口

```java
public interface UserService {
    public void addUser();
    public void deleteUser();
    public void updateUser();
}

```

2、真实角色

```java
public class UserServiceImpl implements UserService{
    public void addUser() {
        System.out.println("增加了一个用户");
    }

    public void deleteUser() {
        System.out.println("删除了一个用户");
    }

    public void updateUser() {
        System.out.println("修改了一个用户");
    }
}

```

3、代理角色

```java
public class UserServiceProxy implements UserService{
    private UserServiceImpl userService;

    public void setUserService(UserServiceImpl userService) {
        this.userService = userService;
    }

    public void addUser() {
        log("addUser");
        userService.addUser();
    }

    public void deleteUser() {
        log("deleteUser");
        userService.deleteUser();
    }

    public void updateUser() {
        log("updateUser");
        userService.updateUser();
    }
    public void log(String msg){
        System.out.println("使用了"+msg+"方法");
    }
}

```

4、客户端访问代理角色

```java
public class Client {
    public static void main(String[] args) {
        UserServiceImpl userService = new UserServiceImpl();
        UserServiceProxy proxy = new UserServiceProxy();
        proxy.setUserService(userService);
        proxy.addUser();
    }
}

```

聊聊AOP  
![](https://img-blog.csdnimg.cn/20200704125939462.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

### 10.3、动态代理

*   动态代理的角色和静态代理的一样
  
*   动态代理的代理类是动态生成的 . 静态代理的代理类是我们提前写好的
  
*   动态代理分为两类 : 一类是基于接口动态代理 , 一类是基于类的动态代理
  
    *   基于接口的动态代理----JDK动态代理
    *   基于类的动态代理–cglib
    *   现在用的比较多的是 java字节码实现：javasist
    *   我们这里使用JDK的原生代码来实现，其余的道理都是一样的！、
    
    **JDK的动态代理需要了解两个类**
    
    核心 : InvocationHandler 和 Proxy ， 打开JDK帮助文档看看

**将租房实例变为动态代理**

接口

```java
public interface Rent {
    public void rent();
}

```

真实角色

```java
public class Landlord implements Rent{
    public void rent() {
        System.out.println("房屋");
    }
}

```

代理实例的处理程序，调用可生成代理类（代理角色）

```java
import org.springframework.cglib.proxy.InvocationHandler;
import org.springframework.cglib.proxy.Proxy;
import java.lang.reflect.Method;




public class ProxyInvocationHandler implements InvocationHandler {

    private Rent rent;

    public void setRent(Rent rent) {
        this.rent = rent;
    }
    
    public Object getProxy(){
        return Proxy.newProxyInstance(rent.getClass().getClassLoader(),rent.getClass().getInterfaces(),this);
    }

    
    
    
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        
        Object result = method.invoke(rent, args);
        return result;
    }
}

```

客户端访问

```java
public class Person {
    public static void main(String[] args) {
        Landlord landlord = new Landlord();
        
        ProxyInvocationHandler pih = new ProxyInvocationHandler();
        pih.setRent(landlord); 
        Rent proxy = (Rent) pih.getProxy(); 
        proxy.rent();
    }
}

```

### 10.4、加深理解

接口

```java
public interface UserService {
    public void addUser();
    public void deleteUser();
    public void updateUser();
}

```

真实角色

```java
public class UserServiceImpl implements UserService{
    public void addUser() {
        System.out.println("增加了一个用户");
    }

    public void deleteUser() {
        System.out.println("删除了一个用户");
    }

    public void updateUser() {
        System.out.println("修改了一个用户");
    }
}

```

代理实例的处理程序

```java
import org.springframework.cglib.proxy.InvocationHandler;
import org.springframework.cglib.proxy.Proxy;
import java.lang.reflect.Method;

public class ProxyInvocationHandler implements InvocationHandler {
    private Object target;

    public void setTarget(Object target) {
        this.target = target;
    }
    public Object getProxy(){
        return Proxy.newProxyInstance(target.getClass().getClassLoader(),target.getClass().getInterfaces(),this);
    }
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        log(method.getName());
        Object result = method.invoke(target, args);
        return result;
    }
    public void log(String msg){
        System.out.println("使用了"+msg+"方法");
    }

}

```

客户端访问

```java
import com.chenjlong.Demo02.UserService;
import com.chenjlong.Demo02.UserServiceImpl;

public class Client {
    public static void main(String[] args) {
        UserService userService = new UserServiceImpl();
        ProxyInvocationHandler pih = new ProxyInvocationHandler();
        pih.setTarget(userService);
        UserService proxy = (UserService) pih.getProxy();
        proxy.addUser();
    }
}

```

动态代理的好处：

*   可以是真实角色的操作更加纯粹，不用去关注一些公共的业务
*   公共业务就交给代理角色！实现业务的分工
*   公共业务发生拓展的时候，方便集中管理！
*   一个动态代理类代理的是一个接口，一般就是对应的业务
*   一个动态代理类可以代理多个类

11.AOP
------

### 11.1.什么是AOP

AOP（Aspect Oriented Programming）意为：面向切面编程，通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术。AOP是OOP的延续，是软件开发中的一个热点，也是Spring框架中的一个重要内容，是函数式编程的一种衍生范型。利用AOP可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率。

![](https://img-blog.csdnimg.cn/20200704163747630.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

### 11.2.Aop在Spring中的作用

提供声明式事务；允许用户自定义切面

以下名词需要了解下：

*   横切关注点：跨越应用程序多个模块的方法或功能。即是，与我们业务逻辑无关的，但是我们需要关注的部分，就是横切关注点。如日志 , 安全 , 缓存 , 事务等等 …
*   切面（ASPECT）：横切关注点 被模块化 的特殊对象。即，它是一个类。
*   通知（Advice）：切面必须要完成的工作。即，它是类中的一个方法。
*   目标（Target）：被通知对象。
*   代理（Proxy）：向目标对象应用通知之后创建的对象。
*   切入点（PointCut）：切面通知 执行的 “地点”的定义。
*   连接点（JointPoint）：与切入点匹配的执行点。

![](https://img-blog.csdnimg.cn/20200704163800867.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

SpringAOP中，通过Advice定义横切逻辑，Spring中支持5种类型的Advice:

![](https://img-blog.csdnimg.cn/20200704163816307.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvbmcyNjMzNTQ5Nzk3,size_16,color_FFFFFF,t_70)

即 Aop 在 不改变原有代码的情况下 , 去增加新的功能 .

### 11.3、使用Spring实现AOP

【重点】 使用AOP织入，需要导入一个依赖包！

```xml

<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjweaver</artifactId>
    <version>1.9.5</version>
</dependency>


```

方式一：使用Spring的API接口**【主要SpringAPI接口实现】（切入前置类和后置类）**

1. 首先编写我们的业务接口和实现类

   ```java
   public interface UserService {
   
      public void add();
   
      public void delete();
   
      public void update();
   
      public void select();
   
   }
   
   ```

   ```java
   public class UserServiceImpl implements UserService{
   
      @Override
      public void add() {
          System.out.println("增加用户");
     }
   
      @Override
      public void delete() {
          System.out.println("删除用户");
     }
   
      @Override
      public void update() {
          System.out.println("更新用户");
     }
   
      @Override
      public void select() {
          System.out.println("查询用户");
     }
   }
   
   ```

2. 写我们的增强类 , 我们编写两个 , 一个前置增强 一个后置增强

   ```java
   //前置日志，构造前置切入类，继承MethodBeforeAdvice接口
   public class log implements MethodBeforeAdvice {
   
      @Override
      public void before(Method method, Object[] objects, Object o) throws Throwable {
          System.out.println( o.getClass().getName() + "的" + method.getName() + "方法被执行了");
     }
   }
   
   ```

   ```java
   //后置日志，构造后置切入类，继承AfterReturningAdvice接口
   public class AfterLog implements AfterReturningAdvice {
   
      @Override
      public void afterReturning(Object returnValue, Method method, Object[] args, Object target) throws Throwable {
          System.out.println("执行了" + target.getClass().getName()
          +"的"+method.getName()+"方法,"
          +"返回值："+returnValue);
     }
   }
   
   ```

3. 在spring的文件中注册 , 并实现aop切入实现 , 注意导入约束 .

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <beans xmlns="http://www.springframework.org/schema/beans"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xmlns:aop="http://www.springframework.org/schema/aop"
          xsi:schemaLocation="http://www.springframework.org/schema/beans
          http://www.springframework.org/schema/beans/spring-beans.xsd
          http://www.springframework.org/schema/aop
          http://www.springframework.org/schema/aop/spring-aop.xsd">
   
       
       <bean id="userService" class="Com.Sun.Service.UserServiceImpl"/>
       <bean id="log" class="Com.Sun.Log.log"/>
       <bean id="afterLog" class="Com.Sun.Log.AfterLog"/>
   
       <!--配置aop，需要导入aop约束-->
       <aop:config>
       <!--切入点：expression：表达式，固定写法execution(),*表示所有返回值类型，Com.Sun.Service.UserServiceImpl实现类的路径，.*(..)类的所有方法，任意参数-->
       <aop:pointcut id="pointcut" expression="execution(* Com.Sun.Service.UserServiceImpl.*(..))"/>
   	<!--执行环绕增强，advice-ref引用切入点的类，pointcut-ref切入的点-->
       <aop:advisor advice-ref="log" pointcut-ref="pointcut"/>
       <aop:advisor advice-ref="afterLog" pointcut-ref="pointcut"/>
       </aop:config>
   
   </beans>
   
   ```

4. 测试

   ```java
   public class MyTest {
      @Test
      public void test(){
          ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
          UserService userService = (UserService) context.getBean("userService");
          userService.select();
     }
   }
   
   ```

Aop的重要性 : 很重要 . 一定要理解其中的思路 , 主要是思想的理解这一块 .

**Spring的Aop就是将公共的业务 (日志 , 安全等) 和领域业务结合起来 , 当执行领域业务时 , 将会把公共业务加进来 . 实现公共业务的重复利用 . 领域业务更纯粹 , 程序猿专注领域业务 , 其本质还是动态代理 . **

方式二：自定义来实现**【主要是切面定义】（切入前置方法和后置方法）【推荐】切入点可以复用**

目标业务类不变依旧是userServiceImpl

1. 写我们自己的一个切入类

   ```java
   public class DiyPointCut {
       public void before() {//前置方法
           System.out.println("==========方法执行前============");
       }
   
       public void after() {//后置方法
           System.out.println("==========方法执行后============");
       }
   }
   
   ```

2. 去spring中配置

   ```xml
   
   <bean id="diy" class="Com.Sun.Diy.DiyPointCut"/>
   
   
   <aop:config>
       
       <aop:aspect ref="diy">
           
           <aop:pointcut id="point" expression="execution(* Com.Sun.Service.UserServiceImpl.*(..))"/>
           <aop:before method="before" pointcut-ref="point"/>
           <aop:after method="after" pointcut-ref="point"/>
           
       </aop:aspect>
   </aop:config>
   
   ```

3. 测试：

   ```java
   @Test
   public void test1() {
       ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
   
       UserService userService = (UserService)context.getBean("userService");
   
       userService.add();
   }
   
   ```

方式三：使用注解实现！

1. 编写一个注解实现的增强类

   ```java
   @Aspect
   public class AnnotationPointCut {
       @Before("execution(* Com.Sun.Service.UserServiceImpl.*(..))")
       public void before() {
           System.out.println("==========方法执行前============");
       }
   	
       @After("execution(* Com.Sun.Service.UserServiceImpl.*(..))")
       public void after() {
           System.out.println("==========方法执行后============");
       }
   	//环绕增强在方法执行前和后的前面
       @Around("execution(* Com.Sun.Service.UserServiceImpl.*(..))")
       public void around(ProceedingJoinPoint jp) throws Throwable {
           System.out.println("==========环绕前============");
           Object proceed = jp.proceed();
           System.out.println("==========环绕后============");
       }
   }
   
   ```
   
2. 在Spring配置文件中，注册bean，并增加支持注解的配置

   ```xml
   <!--方式三-->
   <bean id="annotationPointCut" class="Com.Sun.Annotation.AnnotationPointCut"/>
   <!--开启注解支持！	JDK（默认false）		cglib（true）-->
   <aop:aspectj-autoproxy proxy-target-class="false"/>
   
   ```

12、整合Mybatis
------------

步骤：

1、导入相关jar包

*   junit
*   mybatis
*   mysql数据库
*   spring-webmvc
*   spring-jdbc
*   aop织入
*   mybatis-spring

2、编写配置文件

3、测试

### 12.1、回忆mybatis

1、编写实体类

```java
import lombok.Data;

@Data
public class User {
    private int id;
    private String name;
    private String pwd;
}

```

2、编写核心配置文件

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">

<configuration>
    <!--给实体类取别名，默认是包下类首字母小写-->
    <typeAliases>
        <package name="com.chenjlong.pojo"/>
    </typeAliases>

    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL=true&amp;useUnicode=true&amp;characterEncoding=UTF-8"/>
                <property name="username" value="root"/>
                <property name="password" value="123456"/>
            </dataSource>
        </environment>
    </environments>
    <mappers>
        <package name="com.chenjlong.mapper"/>
    </mappers>

</configuration>

```

3、编写接口

```java
import com.chenjlong.pojo.User;

import java.util.List;

public interface UserMapper {
    public List<User> getUser();
}

```

4、编写Mapper.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.chenjlong.mapper.UserMapper">
    <select id="getUser" resultType="user">
        select * from user
    </select>
</mapper>

```

5、测试

```java
@Test
public void getUser() throws IOException {
    String resource = "mybatis-config.xml";
    InputStream in = Resources.getResourceAsStream(resource);
    SqlSessionFactory sessionFactory = new SqlSessionFactoryBuilder().build(in);
    SqlSession sqlSession = sessionFactory.openSession();
    UserMapper mapper = sqlSession.getMapper(UserMapper.class);
    List<User> userList = mapper.getUser();
    for (User user : userList) {
        System.out.println(user);
    }
    sqlSession.close();
}

```

### 12.2、Mybatis-Spring

引入Spring之前需要了解mybatis-spring包中的一些重要类；

[mybatis-spring官网](http://www.mybatis.org/spring/zh/index.html)

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-Whx1c1AE-1607333099025)(spring课堂笔记.assets/13.png)]

**什么是 MyBatis-Spring？**

MyBatis-Spring 会帮助你将 MyBatis 代码无缝地整合到 Spring 中。

**知识基础**

在开始使用 MyBatis-Spring 之前，你需要先熟悉 Spring 和 MyBatis 这两个框架和有关它们的术语。这很重要

MyBatis-Spring 需要以下版本：

| MyBatis-Spring | MyBatis | Spring 框架 | Spring Batch | Java    |
| -------------- | ------- | ----------- | ------------ | ------- |
| 2.0            | 3.5+    | 5.0+        | 4.0+         | Java 8+ |
| 1.3            | 3.4+    | 3.2.2+      | 2.1+         | Java 6+ |

如果使用 Maven 作为构建工具，仅需要在 pom.xml 中加入以下代码即可：

```xml
<dependency>
   <groupId>org.mybatis</groupId>
   <artifactId>mybatis-spring</artifactId>
   <version>2.0.2</version>
</dependency>

```

#### **整合方式一**

1. 引入配置文件

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.springframework.org/schema/beans
          http://www.springframework.org/schema/beans/spring-beans.xsd">
   </beans>
   
   ```

2. 编写数据源配置

   ```xml
   <bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
       <property name="driverClassName" value="com.mysql.cj.jdbc.Driver"/>
       <property name="url" value="jdbc:mysql://localhost:3306/mybatis?userSSL=ture&amp;useUnicode=true&amp;characterEncoding=UTF-8&amp;serverTimezone=Asia/Shanghai"/>
       <property name="username" value="root"/>
       <property name="password" value="cgj532416"/>
   </bean>
   
   ```

3. sqlSessionFactory

   ```xml
   <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
       <property name="dataSource" ref="dataSource"/>
       
       <property name="configLocation" value="classpath:mybatis-config.xml"/>
       <property name="mapperLocations" value="classpath:Com/Sun/Dao/UserMapper.xml"/>
   </bean>
   
   ```

4. sqlSessionTemplate

   ```xml
   <bean id="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
       
       <constructor-arg index="0" ref="sqlSessionFactory"/>
   </bean>
   
   ```

5. 需要给接口加实现类【新加的】

   ```java
   public class UserDaoImpl implements UserMapper {
       
       private SqlSessionTemplate sqlSession;
       public void setSqlSession(SqlSessionTemplate sqlSession) {
           this.sqlSession = sqlSession;
       }
       public List<User> getAllUser() {
           UserMapper mapper = sqlSession.getMapper(UserMapper.class);
           return mapper.getAllUser();
       }
   }
   
   ```

6. 将自己写的实现类，注入到Spring中

   ```xml
   <bean id="userDao" class="Com.Sun.Dao.UserDaoImpl">
       <property name="sqlSession" ref="sqlSession"/>
   </bean>
   
   ```

7. 测试使用即可

   ```java
   public static void main(String[] args) throws Exception{
       ApplicationContext context = new ClassPathXmlApplicationContext("ApplicationContext.xml");
       UserMapper userDao = (UserMapper) context.getBean("userDao");
       List<User> allUser = userDao.getAllUser();
       for (User user : allUser) {
           System.out.println(user.toString());
       }
   }
   
   ```

结果成功输出！现在我们的Mybatis配置文件的状态！发现都可以被Spring整合！

为了给mybatis-config.xml留点面子(使用方便)，在其中将别名和设置留下来

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
       PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
       "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
 <typeAliases>
     <package name="Com.Sun.pojo"/>
 </typeAliases>


</configuration>

```

#### **整合实现二**

mybatis-spring1.2.3版以上的才有这个 .

官方文档截图 :

dao继承Support类 , 直接利用 getSqlSession() 获得 , 然后直接注入SqlSessionFactory . 比起方式1 , 不需要管理SqlSessionTemplate , 而且对事务的支持更加友好 . 可跟踪源码查看

![](https://gitee.com/xiaoyuan_students_oo/Typora-picture1/raw/master/2021/20210427123944.png)

测试：

1. 将我们上面写的UserDaoImpl修改一下

   ```java
   public class UserDaoImpl2 extends SqlSessionDaoSupport implements UserMapper {
       @Override
       public List<User> getAllUser() {
           UserMapper mapper = getSqlSession().getMapper(UserMapper.class);
           List<User> allUser = mapper.getAllUser();
           return allUser;
       }
   }
   
   ```

2. 修改bean的配置

   ```xml
   <bean id="userDao" class="Com.Sun.Dao.UserDaoImpl2">
       <property name="sqlSessionFactory" ref="sqlSessionFactory"/>
   </bean>
   
   ```

3. 测试

   ```java
   @Test
   public void test(){
       ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
       UserMapper userDao = (UserMapper) context.getBean("userDao");
       for (User user : userDao.getAllUser()) {
           System.out.println(user);
       }
   }
   
   ```

**总结 : 整合到spring以后可以完全不要mybatis的配置文件，除了这些方式可以实现整合之外，我们还可以使用注解来实现，这个等我们后面学习SpringBoot的时候还会测试整合！**

## 13、声明式事务

### 13.1、回顾事务

*   把一组业务当成一个业务来做：要么都成功，要么都失败
*   事务在项目开发中，十分的重要，涉及到数据的一致性和完整性问题，不能马虎
*   确保完整性和一致性

事务ACID原则：

*   原子性
*   一致性
*   隔离性
    *   多个业务可能操纵同一个资源，防止数据损坏
*   持久性
    *   事务一旦提交，无论系统发生什么问题，结果都不会再被影响，被持久化到数据库中！

### 13.2、spring中的事务管理

*   声明式事务：AOP
*   编程式事务：需要在代码中，进行事务的管理

```xml

<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
    <property name="dataSource" ref="dataSource"/>
</bean>


<tx:advice id="interceptor" transaction-manager="transactionManager">
    <tx:attributes>
        
        
        <tx:method name="add" propagation="REQUIRED"/>
        <tx:method name="delete" propagation="REQUIRED"/>
        <tx:method name="update" propagation="REQUIRED"/>
        <tx:method name="query" read-only="true"/>
        <tx:method name="*" propagation="REQUIRED"/>
    </tx:attributes>
</tx:advice>

<aop:config>
    <aop:pointcut id="point" expression="execution(* com.chenjlong.mapper.*.*(..))"/>
    <aop:advisor advice-ref="interceptor" pointcut-ref="point"/>
</aop:config>

```

思考

为什么需要事务？

*   如果不配置事务，可能存在数据不一致的情况
*   如果我们不再spring中去配置声明式事务，我们需要在代码中手动配置事务
*   事务在项目开发中，十分的重要，涉及到数据的一致性和完整性问题，不能马虎