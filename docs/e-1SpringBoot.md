# SpringBoot 笔记

> 因为SpringBoot其实是在Spring的基础上简化配置过程和加上了注解开发，所以就不做多全面的总结。以自身不太熟悉的内容总结为主。

## 框架层级

**Controller层：控制层 控制业务逻辑**

Controller层负责具体的业务模块流程的控制，controller层负责前后端交互，接受前端请求，调用service层，接收service层返回的数据，最后返回具体的页面和数据到客户端

Controller层像是一个==服务员==（==Controller层==），他把客人（前端）点的菜（数据、请求的类型等）进行汇总什么口味、咸淡、量的多少，交给==厨师长==（==Service层==），厨师长则告诉砧板厨师（Dao1）、汤料房（Dao2）、配菜厨师（Dao3）等（统称Dao层）我需要什么样的半成品，==副厨们==（==Dao层==）就负责完成（Service层）交代的任务

**Service层：业务层 控制业务**

Service层主要负责业务模块的逻辑应用设计。先设计接口的类，在创建实现的类，然后在配置文件中进行配置器实现的关联。service层调用dao层接口，接收dao层返回的数据，完成项目的基本功能设计

封装Service层的业务逻辑有利于业务逻辑的独立性和重复利用性

**DAO层：持久层 主要域数据库进行交互**

DAO层 = mapper层，现在用Mybatis逆向工程生成的mapper层，其实就是dao层。DAO层会调用entity层，DAO中会定义实际使用到的方法，比如CRUD。DAO层的数据源和数据库连接的参数都是在配置文件中进行配置的，配置文件一般在同层的XML文件夹中。数据持久化操作就是指，把数据放到持久化的介质中，同时提供CRUD操作

**Entity层：实体层 数据库在项目中的类**

Enity层是实体层，也就是所谓的model，也称为pojo层，是数据库在项目中的类，该文件包含实体类的属性和对应属性的set、get方法

![image-20210503201532422](https://gitee.com/xiaoyuan_students_oo/Typora-picture1/raw/master/2021/20210503201534.png)

![img](https://gitee.com/xiaoyuan_students_oo/Typora-picture1/raw/master/2021/20210503201428.png)

## 注解

### 注解列表

~~~java
@SpringBootApplication //包含了 @ComponentScan、@Configuration 和 @EnableAutoConfiguration 注解

@ComponentScan //让 springboot 扫描到 Configuration 类并把它加入到程序上下文

@Configuration //等同于 spring 的 XML 配置文件；使用Java代码可以把它加入到程序上下文

@EnableAutoConfiguration //自动配置

@ComponentScan //组件扫描，可自动发现和装配一些Bean

@Component //可配合 CommandLineRunner使用，在程序启动后执行一些基础任务

@RestController //注解是 @Controller 和 @ResponseBody的合集，表示这是个控制器bean，并且是将函数的返回值直接填入HTTP响应体中，是REST风格的控制器

@Autowired //自动导入

@PathVariable //获取参数

@JsonBackReference //解决嵌套外链问题

@RepositoryRestResourcepublic //配合spring-boot-starter-data-rest使用
~~~

### 注解详解

~~~java
@SpringBootApplication //申明让spring boot自动给程序进行必要的配置，这个配置等同于:@Configuration,@EnableAutoConfiguration 和 @ComponentScan 三个配置

@ResponseBody //表示该方法的返回结果直接写入HTTP response body中，一般在异步获取数据时使用，用于构建RESTful的api。在使用@RequestMapping后，返回值通常解析为跳转路径，加上@Responsebody后返回结果不会被解析为跳转路径，而是直接写入HTTP response body中。比如异步获取json数据，加上@Responsebody后，会直接返回json数据。该注解一般会配合@RequestMapping一起使用

@Controller //用于定义控制器类，在spring项目中由控制器负责将用户发来的URL请求转发到对应的服务接口（service层），一般这个注解在类中，通常方法需要配合注解@RequestMapping

@RestController //用于标注控制层组件(如struts中的action)，@ResponseBody和@Controller的合集

@RequestMapping //提供路由信息，负责URL到Controller中的具体函数的映射

@EnableAutoConfiguration //SpringBoot自动配置（auto-configuration）：尝试根据你添加的jar依赖自动配置你的Spring应用。例如，如果你的classpath下存在HSQLDB，并且你没有手动配置任何数据库连接beans，那么我们将自动配置一个内存型（in-memory）数据库”。你可以将@EnableAutoConfiguration或者@SpringBootApplication注解添加到一个@Configuration类上来选择自动配置。如果发现应用了你不想要的特定自动配置类，你可以使用@EnableAutoConfiguration注解的排除属性来禁用它们

@ComponentScan //表示将该类自动发现扫描组件。个人理解相当于，如果扫描到有@Component、@Controller、@Service等这些注解的类，并注册为Bean，可以自动收集所有的Spring组件，包括@Configuration类。我们经常使用@ComponentScan注解搜索beans，并结合@Autowired注解导入。可以自动收集所有的Spring组件，包括@Configuration类。我们经常使用@ComponentScan注解搜索beans，并结合@Autowired注解导入。如果没有配置的话，Spring Boot会扫描启动类所在包下以及子包下的使用了@Service,@Repository等注解的类

@Configuration //相当于传统的xml配置文件，如果有些第三方库需要用到xml文件，建议仍然通过@Configuration类作为项目的配置主类——可以使用@ImportResource注解加载xml配置文件

@Import //用来导入其他配置类

@ImportResource //用来加载xml配置文件

@Autowired //自动导入依赖的bean

@Service  //一般用于修饰service层的组件

@Repository //使用@Repository注解可以确保DAO或者repositories提供异常转译，这个注解修饰的DAO或者repositories类会被ComponetScan发现并配置，同时也不需要为它们提供XML配置项

@Bean //用@Bean标注方法等价于XML中配置的bean

@Value //注入Spring boot application.properties配置的属性的值

@Inject //等价于默认的@Autowired，只是没有required属性

@Component //泛指组件，当组件不好归类的时候，我们可以使用这个注解进行标注

@Qualifier //当有多个同一类型的Bean时，可以用@Qualifier(“name”)来指定。与@Autowired配合使用。@Qualifier限定描述符除了能根据名字进行注入，但能进行更细粒度的控制如何选择候选者

@Resource(name=”name”,type=”type”) //没有括号内内容的话，默认byName。与@Autowired干类似的事
~~~

### JPA注解

~~~java
@Entity //@Table(name=”“)：表明这是一个实体类。一般用于jpa这两个注解一般一块使用，但是如果表名和实体类名相同的话，@Table可以省略

@MappedSuperClass //用在确定是父类的entity上。父类的属性子类可以继承

@NoRepositoryBean //一般用作父类的repository，有这个注解，spring不会去实例化该repository

@Column //如果字段名与列名相同，则可以省略

@Id //表示该属性为主键

@GeneratedValue(strategy = GenerationType.SEQUENCE,generator = "repair_seq") //表示主键生成策略是sequence（可以为Auto、IDENTITY、native等，Auto表示可在多个数据库间切换），指定sequence的名字是repair_seq

@SequenceGeneretor(name = "repair_seq", sequenceName = "seq_repair", allocationSize = 1) //name为sequence的名称，以便使用，sequenceName为数据库的sequence名称，两个名称可以一致

@Transient //表示该属性并非一个到数据库表的字段的映射,ORM框架将忽略该属性。如果一个属性并非数据库表的字段映射,就务必将其标示为@Transient,否则,ORM框架默认其注解为@Basic。@Basic(fetch=FetchType.LAZY)：标记可以指定实体属性的加载方式

@JsonIgnore //作用是json序列化时将Java bean中的一些属性忽略掉,序列化和反序列化都受影响

@JoinColumn(name="loginId") //一对一：本表中指向另一个表的外键。一对多：另一个表指向本表的外键

@OneToOne、@OneToMany、@ManyToOne //对应hibernate配置文件中的一对一，一对多，多对一
~~~

### SpringMVC相关注解

~~~java
@RequestMapping //@RequestMapping(“/path”)表示该控制器处理所有“/path”的URL请求。RequestMapping是一个用来处理请求地址映射的注解，可用于类或方法上
~~~

用于类上，表示类中的所有响应请求的方法都是以该地址作为父路径。该注解有六个属性：

- params：指定request中必须包含某些参数值是，才让该方法处理。
- headers：指定request中必须包含某些指定的header值，才能让该方法处理请求。
- value：指定请求的实际地址，指定的地址可以是URI Template 模式
- method：指定请求的method类型， GET、POST、PUT、DELETE等
- consumes：指定处理请求的提交内容类型（Content-Type），如application/json,text/html;
- produces：指定返回的内容类型，仅当request请求头中的(Accept)类型中包含该指定类型才返回

~~~java
@RequestParam //用在方法的参数前面

@RequestParam
String a =request.getParameter(“a”)
    
@PathVariable //路径变量
~~~

### 全局异常处理

~~~java
@ControllerAdvice //包含@Component。可以被扫描到。统一处理异常。
@ExceptionHandler(Exception.class) //用在方法上面表示遇到这个异常就执行以下方法。
~~~

## 整合步骤（以Mybatis为例）

1. 导入依赖

   ~~~xml
   <!--引入mybatis,这是Mybatis官方提供的适配SpringBoot的，而不是SpringBoot自己的-->
   <dependency>
       <groupId>org.mybatis.spring.boot</groupId>
       <artifactId>mybatis-spring-boot-starter</artifactId>
       <version>2.1.1</version>
   </dependency>
   ~~~

2. 配置yml文件

   ~~~yml
   # 配置spring自带的数据源
   spring:
     datasource:
       username: root
       password: root
       url: jdbc:mysql://localhost:3306/mybatis?userSSL=true&useUnicode=true&characterEncoding=UTF-8&serverTimezone=UTC
       driver-class-name: com.mysql.cj.jdbc.Driver
   
   # 整合mybatis
   mybatis:
     # 别名
     type-aliases-package: com.kuang.pojo
     # mapper文件位置
     mapper-locations: classpath:mybatis/mapper/*.xml
   ~~~

3. mybatis配置

   1. User（pojo层）

      ~~~java
      @Data
      @AllArgsConstructor
      @NoArgsConstructor
      public class User {
          private int id;
          private String name;
          private String password;
      }
      ~~~

   2. UserMapper接口（dao层）

      ~~~java
      @Repository
      @Mapper
      public interface UserMapper {
          public User queryUserByName(String name);  
      }
      ~~~

   3. UserMapper.xml配置文件（dao层）

      ~~~xml
      <!--namespace=绑定一个指定的Dao/Mapper接口-->
      <mapper namespace="com.kuang.mapper.UserMapper">
          <select id="getUserList" resultType="com.kuang.pojo.User" parameterType="String">
          select * from USER where name = #{name}
        	</select>
      </mapper>
      ~~~

4. 编写sql

5. service层调用dao层

   1. UserService接口（Service层）

      ~~~java
      public interface UserService {
          public User queryUserByName(String name);
      }
      ~~~

   2. UserServiceImpl实现类（Service层）

      ~~~java
      @Service
      public class UserServiceImpl implements UserService{
          @Autowired
          UserMapper mapper;
          public User queryUserByName(String name) {
              User user = mapper.queryUserByName(name);
              return user;
          }
      }
      ~~~

6. controller调用service层

   ~~~java
   @Autowired
   UserServiceImpl userService;
   public void mian(String args[]){
       User user = userService.queryUserByName("dog");
   }
   ~~~