---
title: Spring Boot核心注解
date: 2019-12-24 20:31:54
tags:
- Spring Boot
- Java
---

# Spring Boot核心注解

为了让自己不要每次看了就忘记，决定写下博客来尽力杜绝这样的事情发生orz

### @SpringBootApplication

这是 Spring Boot 最最最核心的注解，用在 Spring Boot 主类上，标识这是一个 Spring Boot 应用，用来开启 Spring Boot 的各项能力。

其实这个注解就是 `@SpringBootConfiguration`、`@EnableAutoConfiguration`、`@ComponentScan` 这三个注解的组合，也可以用这三个注解来代替 `@SpringBootApplication` 注解。

### @EnableAutoConfiguration

允许 Spring Boot 自动配置注解，开启这个注解之后，Spring Boot 就能根据当前类路径下的包或者类来配置 Spring Bean。

如：当前类路径下有 Mybatis 这个 JAR 包，`MybatisAutoConfiguration` 注解就能根据相关参数来配置 Mybatis 的各个 Spring Bean。

### @**Configuration**

这是 Spring 3.0 添加的一个注解，用来代替 applicationContext.xml 配置文件，所有这个配置文件里面能做到的事情都可以通过这个注解所在类来进行注册。

### @**SpringBootConfiguration**

这个注解就是 @Configuration 注解的变体，只是用来修饰是 Spring Boot 配置而已，或者可利于 Spring Boot 后续的扩展。

### @ComponentScan

自动扫描指定包下所有使用@Service,@Component,@Controller,@Repository的类并注册。

这是 Spring 3.1 添加的一个注解，用来代替配置文件中的 `component-scan` 配置，开启组件扫描，即自动扫描包路径下的 `@Component` 注解进行注册 bean 实例到 context 中。

另外，`@ComponentScans` 是可重复注解，即可以配置多个，用来配置注册不同的子包。

### @Conditional

这是 Spring 4.0 添加的新注解，用来标识一个 Spring Bean 或者 Configuration 配置文件，当满足指定的条件才开启配置。

### @Controller

组合注解（组合了@Component注解），应用在MVC层（控制层）,DispatcherServlet会自动扫描注解了此注解的类，然后将web请求映射到注解了@RequestMapping的方法上。

### @Service

组合注解（组合了@Component注解），应用在service层（业务逻辑层）

### @Repository

应用于DAO层

### @Compoent

表示一个带注释的类是一个“组件”，成为Spring管理的Bean。当使用基于注解的配置和类路径扫描时，这些类被视为自动检测的候选对象。同时@Component还是一个元注解。

### @Autowired

Spring提供的工具（由Spring的依赖注入工具（BeanPostProcessor、BeanFactoryPostProcessor）自动注入。）

### @Bean

注解在方法上，声明当前方法的返回值为一个Bean。返回的Bean对应的类中可以定义init()方法和destroy()方法，然后在@Bean(initMethod=“init”,destroyMethod=“destroy”)定义，在构造之后执行init，在销毁之前执行destroy。

### @Scope

1. singleton：单例模式，在整个Spring IoC容器中，使用singleton定义的Bean将只有一个实例
2. prototype：原型模式，每次通过容器的getBean方法获取prototype定义的Bean时，都将产生一个新的Bean实例
3. request：对于每次HTTP请求，使用request定义的Bean都将产生一个新实例，即每次HTTP请求将会产生不同的Bean实例。只有在Web应用中使用Spring时，该作用域才有效
4. session：对于每次HTTP Session，使用session定义的Bean都将产生一个新实例。同样在Web应用中使用Spring时，该作用域才有效

### @Qualifier

配合@Autowired使用，按照名称装配