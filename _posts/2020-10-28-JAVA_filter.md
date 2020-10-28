---
layout:     post
title:      "JAVA过滤器"
subtitle:   ""
date:      	2020-10-28-21:00:00
author:     "Djie"
header-img: "img/ES.jpg"
tags:
  - 后端
  - 开发
---

## JAVA过滤器

### 过滤器应用场景

Web资源权限访问控制

请求字符集编码处理

内容敏感字符词汇过滤

响应信息压缩

### 过滤器工作流程

<img src="/img/in-post/1603857853322.png">

### 过滤器的生命周期

web应用程序**启动**时，web服务器**创建**filter的实例对象，以及对象的**初始化**。

当请求访问与过滤器**关联**的Web资源时，过滤器**拦截请求**，**完成指定功能**

Filter对象创建后会**驻留在内存**，在web应用移除或服务器**停止**时才**销毁**

过滤器的创建和销毁由**web服务器负责**

### 过滤器的实现步骤

1、编写java类实现Filter接口，并实现其doFilter方法

2、在web.xml文件中对filter类进行注册，并设置所拦截的资源

#### 过滤器链

在一个web应用中，多个过滤器组合起来称为一个过滤器链

过滤器的调用顺序取决于过滤器在web.xml文件中的注册顺序



### 举个栗子

**例**

java页面:

```java
public class test implements Filter{

	/**
	 * 销毁方法，做清理操作
	 */
	@Override
	public void destroy() {
		// TODO Auto-generated method stub
		System.out.println("拦截器销毁");
		
	}

	/**
	 *  主要方法，完成过滤器功能
	 *  FilterChain 过滤器链对象
	 */
	@Override
	public void doFilter(ServletRequest requert, ServletResponse response, FilterChain chain)
			throws IOException, ServletException {
		System.out.println("拦截处理");
		//方法内获取初始化蚕食
		String systemName = config.getInitParameter("systemName"); 
		//拦截完成后通知WEB服务器已完成，进行下一步操作或执行过滤器链的下一个过滤器若没有则执行请求，对请求资源进行处理
		chain.doFilter(requert,response);
	}

	@Override
	/**
	 * 初始化方法
	 */
	public void init(FilterConfig config) throws ServletException {
		// TODO Auto-generated method stub
		System.out.println("拦截器初始化");
		this.config = config;//获取初始化参数
	}
	
	private FilterConfig config;

}
```

web.xml页面

```xml
	<filter>
		<filter-name>characterEncodingFilter</filter-name><!-- 名称 -->
		<filter-class>test</filter-class><!-- 所在类 -->

		<init-param><!-- 初始化参数 -->
			<param-name>systemName</param-name>
			<param-value>key</param-value>
		</init-param>
	</filter>


	<filter-mapping>
		<filter-name>characterEncodingFilter</filter-name><!-- 映射的过滤器 -->
		<url-pattern>/*</url-pattern><!-- 对所有的请求都做拦截处理 -->
	</filter-mapping>
```

例2：解决中文乱码问题

```java
public class CharacterEncodingFilter implements Filter {

	private FilterConfig config;

	@Override
	public void destroy() {

	}

	@Override
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
			throws IOException, ServletException {

		request.setCharacterEncoding(config.getInitParameter("charset"));// 根据过滤器配置字符集，设置请求字符集编码

		// System.out.println("characterEncodingFilter 请求预处理");//测试过滤器（链）工作流程使用
		chain.doFilter(request, response);
		// System.out.println("characterEncodingFilter 响应后处理");//测试过滤器（链）工作流程使用

	}

	@Override
	public void init(FilterConfig config) throws ServletException {
		this.config = config;

	}
	}
```

xml

```xml
<!-- 字符集编码过滤器配置 -->
	<filter>
		<filter-name>characterEncodingFilter</filter-name><!-- 名称 -->
		<filter-class>filter.CharacterEncodingFilter</filter-class><!-- 所在类 -->

		<init-param><!-- 初始化参数 -->
			<param-name>charset</param-name>
			<param-value>UTF-8</param-value>
		</init-param>
	</filter>


	<filter-mapping>
		<filter-name>characterEncodingFilter</filter-name><!-- 映射的过滤器 -->
		<url-pattern>/*</url-pattern><!-- 对所有的请求都做拦截处理 -->

	</filter-mapping>
```

例3 登录安全控制过滤器

java:

```
public class SessionFilter implements Filter {

	@Override
	public void destroy() {

	}

	@Override
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
			throws IOException, ServletException {

		HttpServletRequest hrequest = (HttpServletRequest) request;// 涉及到HTTP请求处理，转型处理
		HttpServletResponse hresponse = (HttpServletResponse) response;// 涉及到HTTP请求处理，转型处理

		String loginUser = (String) hrequest.getSession().getAttribute("loginUser");// 判断用户是否完成了登录操作，session中是否存储用户名

		if (loginUser == null) {
			hresponse.sendRedirect(hrequest.getContextPath() + "/index.jsp?flag=1");// 未登录，系统强制重定向至登录页面
			return;
		} else {
			chain.doFilter(hrequest, hresponse);
			return;
		}

	}

	@Override
	public void init(FilterConfig config) throws ServletException {

	}

}
```

xml:

```xml
<!-- 用户登录安全控制过滤器配置 -->
	<filter>
		<filter-name>sessionFilter</filter-name>
		<filter-class>filter.SessionFilter</filter-class>
	</filter>

	<filter-mapping>
		<filter-name>sessionFilter</filter-name>
		<url-pattern>/message.jsp</url-pattern><!-- 对访问该页面的请求进行过滤 -->
        <dispatcher>REQUEST</dispatcher>
         <dispatcher>ERROR</dispatcher>
	</filter-mapping>
```

### 过滤器配置

 filter-mapping子元素dispatcher

REQUEST--直接访问页面（默认）

INCLUDE--通过include访问另外的页面

FORWARD--通过forward访问

ERROR--异常处理机制调用时