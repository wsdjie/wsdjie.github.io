---
layout:     post
title:      "SpringBoot调用外部接口的一个实例"
subtitle:   ""
date:       2019-08-08-01:17:00
author:     "Djie"
header-img: "img/bg3.jpg"
tags:
    - 后端
    - 开发
---

### SpringBoot调用外部接口的一个简单实例

### 第一步

在pom.xml文件中加入相应的配置

```
		<dependency>
            <groupId>org.apache.httpcomponents</groupId>
            <artifactId>httpclient</artifactId>
        </dependency>

​		<dependency>
​            <groupId>org.springframework.boot</groupId>
​            <artifactId>spring-boot-starter-web</artifactId>
​        </dependency>
```

<br>
### 第二步

在service层中，建立HttpClient类

	import org.springframework.http.HttpMethod;
	import org.springframework.http.ResponseEntity;
	import org.springframework.stereotype.Service;
	import org.springframework.util.MultiValueMap;
	import org.springframework.web.client.RestTemplate;
	
	@Service
	public class HttpClient {
	
		public String client(String url,HttpMethod method,MultiValueMap<String, String> params) {
			RestTemplate template =new RestTemplate();
			ResponseEntity<String> response1 = template.getForEntity(url, String.class);
			System.out.println(response1.getBody());
			return response1.getBody();
		}
		}

<br>
### 第三步

编写controller层

	@Autowired
		HttpClient httpClient;
		
		@RequestMapping(value="/djieTest")
		public String test() {
			String url ="http://v.juhe.cn/toutiao/index?key=XXXXX"; //以聚合数据的新闻头条接口为例
			HttpMethod method = HttpMethod.GET;
			MultiValueMap<String, String> params = new LinkedMultiValueMap<>();
			return httpClient.client(url, method, params);
		}

<br>
#### 调用成功
<img src="/img/in-post/1565197781086.png">