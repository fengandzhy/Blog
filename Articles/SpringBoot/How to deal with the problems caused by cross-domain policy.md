## Overview
Nowadays, more and more web project seperate front-end code from back-end code so that the development of front-end and back-end could be seperated. 
This article will not discuss why we need to seperate front-end code from back-end code, it will discuss in a spring boot project if the front-end code is seperated from the back-end code how dose spring boot deal with the problems casued by cross-domain.
Before we discuss the problem, let's briefy what is the Same origin policy? 
## Same origin policy
In the web area, the same origin policy means the same domain name, protocol and port. That is, if a web page don't have the same domain name and the same protocol and the same port with another website, then this page is cross-domain for this site.  
Therefore if we seperate the front-end code from the back-end code in a spring boot project, the interaction between the front-end code to back-end code will need to overcome issues caused by cross-domain.
## The configuration of CROS in a spring boot project
Before we discuss how to config the CROS in a sprong boot project, what happens when a spring boot project without CROS configuration is accessed by a cross-domain visit? 
please look at the below picture shows
![image](https://github.com/fengandzhy/Blog/raw/master/Images/SpringBoot/article02/2.png) 
Add the class below to your spring boot project then it will solve the problem above.
```java
@Configuration
public class MyConfiguration implements WebMvcConfigurer{

	@Override  
    public void addCorsMappings(CorsRegistry registry) {  
        registry.addMapping("/**")  
                .allowCredentials(true)  
                .allowedHeaders("*")  
                .allowedOrigins("*")  
                .allowedMethods("*");
	}
}
```
Let's analyze the code. 
**allowedOrigins** All the requested domain names which can be allowed to access our cross-domain resources, you can fix a single or multiple content, such as: "http://www.baidu.com", only Baidu can access our cross-domain resources.
**addMapping** The a paths that can be allowed to access cross-domain resources, it can be configured arbitrarily or be specific to the direct request path.
**allowedMethods** The request method that allows input parameters accesses the cross-domain resource server, such as: POST, GET, PUT, OPTIONS, DELETE, and so on.
**allowedHeaders** All request header which are allowed to access, you can customize any request header information
**allowCredentials** The response header indicates whether the response to the request can be exposed to the page. Return true, no other values.
## Other code for the project 
index.html
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.min.js"></script>
		<script type="application/javascript">
			function get_list(){
				var loginBean = new Object();
				loginBean.username="abc";
				loginBean.password="bcd";
				var json = JSON.stringify(loginBean);
				$.ajax({
					type:'post',
					url: "http://127.0.0.1:8088"+"/index/loginbypost2",
					dataType:'json',
					data:{"username":"yd","password":"123456"},
					success:function(res){
						console.log(res);						
					}
				});
			}
		</script>
	</head>
	<body>
		<input type="button" value="click" onclick="get_list()" />
	</body>
	
</html>
```
pom.xml
```xml
<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>

		<!-- 添加热部署 开发者模式 -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<optional>true</optional>
		</dependency>

		<!-- https://mvnrepository.com/artifact/com.googlecode.json-simple/json-simple -->
		<dependency>
		    <groupId>com.googlecode.json-simple</groupId>
		    <artifactId>json-simple</artifactId>
		    <version>1.1</version>
		</dependency>
``` 
controller
```java
@RestController
@RequestMapping(value = "/index", produces = MediaType.APPLICATION_JSON_UTF8_VALUE)
public class TestController {	
	@SuppressWarnings("unchecked")
	@RequestMapping(value = "/loginbypost2", method = {RequestMethod.POST, RequestMethod.GET })
	public String loginByPost2(RequestLoginBean loginBean) {
		JSONObject result = new JSONObject();
		result.put("username", loginBean.getUsername());
		result.put("password", loginBean.getPassword());
		return result.toJSONString();
	}
}
```
frombean
```java
public class RequestLoginBean {
	private String username;
	private String password;
	........
```
## The structure of the project 
![image](https://github.com/fengandzhy/Blog/raw/master/Images/SpringBoot/article02/1.PNG)  


