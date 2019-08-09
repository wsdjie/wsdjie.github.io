---
layout:     post
title:      "SpringBoot学习笔记（一）"
subtitle:   ""
date:       2019-08-10-02:00:00
author:     "Djie"
header-img: "img/bg3.jpg"
tags:
  - 后端
  - 开发
---

> springBoot学习笔记（一）

**Spring Boot的分层结构**

<br>Keynote: MVC模型；三层架构； 
<br>Controller对应控制层、Service业务层、Repository数据层、model模型层 

**JUnit**：

JUnit是一个Java语言的单元测试框架。它由Kent Beck和Erich Gamma建立，逐渐成为源于KentBeck的sUnit的xUnit家族中最为成功的一个。 JUnit有它自己的JUnit扩展生态圈。多数Java的开发环境都已经集成了JUnit作为单元测试的工具。 
<br>[学习地址](https://www.w3cschool.cn/junit/) 

#### Spring Data JPA

JPA全称Java Persistence API，是一组用于将数据存入数据库的类和方法的集合。JPA通过JDK 5.0注解或
XML描述对象－关系表的映射关系，并将运行期的实体对象持久化到数据库中。 
JPA是开源API，各企业经营商Oracle, Redhat, Eclipse等，提供各种有特色的JPA产品，其中包括: Hiberate, 
Eclipselink, Toplink, Spring Data JPA等等。 
<br>[参考地址](https://docs.spring.io/spring-data/jpa/docs/2.1.0.M3/reference/html/ )

**在SpringBoot中使用JPA 操作MySQL数据库**

1.pom.xml中添加jpa依赖

```
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
```

2.添加配置

```
######################################################## 
###datasource 
######################################################## 
spring.datasource.url = jdbc:mysql://192.168.142.128/Djie?useUnicode=true&characterEncoding=utf8&useSSL=false 
spring.datasource.username = root 
spring.datasource.password = 123456 
spring.datasource.driverClassName = com.mysql.jdbc.Driver
spring.datasource.initial-size= 1 
spring.datasource.min-idle= 3 
spring.datasource.max-idle= 20 
spring.datasource.max-active= 20 
spring.datasource.time-between-eviction-runs-millis: 60000 
spring.datasource.min-evictable-idle-time-millis: 30000 
spring.datasource.validation-query: select 1 
spring.datasource.test-while-idle: true 
spring.datasource.test-on-borrow: false 
spring.datasource.test-on-return: false ######################################################## 
###jpa 
######################################################## 
spring.jpa.database= MYSQL spring.jpa.show-sql= true 
spring.jpa.hibernate.ddl-auto= update spring.jpa.open-in-view= true spring.jpa.properties.hibernate.enable_lazy_load_no_trans= true
```

3.模型设计

```
@Entity
@Table(name = "user")//数据库的表名
public class User implements Serializable{

	@Column(name = "username") //列名
	private String username;
	}
	@Column(name = "password") 
	private String username;
	}
	@Column(name = "Djid") 
	private String Djid;
	}
	
	public String getUsername() {
		return username;
	}
	public void setUsername(String username) {
		this.username = username;
	}
	省略........
```

4.编写JPA- UserRepository

```
package com.dayup.seckil.repository;

import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

import com.dayup.seckil.model.User;

@Repository 
//第一个对应的是实体映射，第二个对应的是主键类型
public interface UserRpository extends JpaRepository<User, String>{
	public User findByUsername(String password);
}

```

编写Service-UserService 

```
public interface UserService {
	public User regist(User user);
}

```

```
@Service
@Transactional
public class UserServiceImpl implements UserService{

	@Autowired
	public UserRpository userRpository;
	
	@Override
	public User regist(User user) {
		return userRpository.saveAndFlush(user);
	}

```

最后在src/test/java中创建一个UserRepositoryTests测试类使用JUnit Test测试

```
public class UserRepositoryTests {

	@Autowired
	private UserService userService;
	
	@Test
	public void test() {
		User user = new User("Djie","12345",20190810);
		Assert.assertNotNull(userService.regist(user));
	}
}
```