# Spring Ioc容器原理
  IoC Inversion of Control
  IoC容器控制了对象，进行管理等操作。

  本module将用源码讲解IoC是怎么管理对象的，
  如何通过BeanDefinition生成bean对象的，以及Spring IoC容器中Bean的生命周期的

## Spring IoC实现方式
   1. XML方式实现
主要是在一个xml配置文件中声明bean节点
```xml
<bean id="user" class="com.gqzdev.ioc.bean.User"></bean>
```

   2. 通过注解方式实现
需要使用@Component、@Service、@Controller、@Repository
@Bean等注解
需要指定包扫描
1.@Configuration
    @ComponentScan
2.在xml文件中指定
```xml
    <!--spring管理的bean路径-->
    <context:component-scan bean="com.gqzdev.ioc.bean"></context>
```

### Spring IoC实现原理解析
BeanFactory最顶层接口

 

## Bean的生命周期
| Spring Bean生命周期各阶段 | 相关接口及方法    |
|:-- |:-- |
| 1. Bean自身方法    | Bean本身业务的方法<br />配置文件中init-method和destroy-method指定的方法 |
| 2. Bean生命周期接口方法   | InitiailizingBean接口 <br />DiposableBean接口 <br />BeanNameAware接口<br />ApplicationContextAware接口<br />BeanFactoryAware接口 <br />其他 |
| 3. 容器级别生命周期接口方法 <br />（一般称为“后处理器”） |  InstantiationAwareBeanPostProcessor接口实现 </br> BeanPostPorcessor 接口实现   |
| 4. 工厂后处理器接口方法 <br />（也可归纳为容器级别）  | AspectJWeavingEnable<br />ConfigurationClassPostProcessor<br /> CustomeAutowireConfigurer等 |