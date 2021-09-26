### Spring IOC

#### 基础使用spring ioc

- gradle.gradle.kts

```kotlin 
dependencies {
    val lastVersion = "5.3.8"
    implementation("org.springframework:spring-core:${lastVersion}")
    implementation("org.springframework:spring-context:${lastVersion}")
    implementation("org.springframework:spring-beans:${lastVersion}")
}
```

- bean.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <!--    <bean id="info" class="com.looptry.model.UserInfo">-->
    <!--        <constructor-arg name="username" value="张三"/>-->
    <!--        <constructor-arg name="age" value="16"/>-->
    <!--    </bean>-->
</beans>
```

- Test.kt

```kotlin
@Test
fun test() {
    val context: ApplicationContext = ClassPathXmlApplicationContext("bean.xml")
    val userInfo = context.getBean("info", UserInfo::class)
    println("bean:$userInfo")
}
```

#### scope

- prototype
- singleton

#### lifecycle

Spring2.5 以后有三种方式控制bean的生命周期

- The InitializingBean and DisposableBean callback interfaces
- Custom init() and destroy() methods
- The @PostConstruct and @PreDestroy annotations. You can combine these mechanisms to control a given bean.