## overview 

In this section, I suppose you have already installed JDK(1.8), Maven, STS. I will not discuss the usage of Maven in this article, I will discuss it in another article

STS is an IDE tool recommended by Spring organization, because it is very convenient for developers to develop spring applications. Actually, it is an Eclipse installed a spring plugin. 
## steps

1. New a maven project, please look at the shortcut below.
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/1.png)

2. Please choose these two items (create a simple project, Use default WorkSpace Location)
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/2.png)

3. Input the 'group Id', 'artifact id' and 'Version' and make sure you have chosen the 'war' in the 'packaging'
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/3.png)

4. click 'ok' then the web application has been created, however it is still problematic  
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/4.png)

5. The reason why there is an error in the pom.xml is that, you did not create a web.xml for this project, so we need to modify the project again. right click the project and choose 'proprites' then choose 'Project Factes'
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/5.png)

6. change the Java to 1.8 and 'Dynamic Web Modules' to 3.1. plese not when you change the 'Dynamic Web Modules' to 3.1, it cannot be changed directly
you need to give up choosing 'Dynamic Web Modules' then click 'Apply', then change 2.5 to 3.1 after that choose the 'Dynamic Web Modules' before you click the 'Apply' 
plese click 'Further configuration available' 
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/6.png)

7. input 'src/main/webapp' in Content Directory and click 'Generate web.xml ....' and then click 'OK'
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/7.png)

8. you can see the web.xml has already existed in the project and there is no longer indicate an error in the pom.xml 
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/8.png)

Actually, After the above eight steps, a web application has been preliminarily built. Now we need to add spring elements to it. 

Before we add spring elements to it, we need to show the modules in spring framework, please look at the picture below (the picture was downloaded from Internet by me)
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/9.png)

from this picture we can see that in the spring framework the core container is 'Beans','Core','Context','SpEL', that is to say, we at least need to import the relevant jar files to our project so that our project could use spring. 
how to import these jar files? The 'Maven' could help us. please add the below xml fragment to your pom.xml, then the maven will download and import jar files to our project automatically. 
```xml
<dependency>
	<groupId>org.springframework</groupId>
	<artifactId>spring-context</artifactId>
	<version>5.0.8.RELEASE</version>
</dependency>
```
Then you can see the basic jar files required by spirng are imported to your project 
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/10.png)

Then we need to create the 'bean configuration' xml file. In this project, we usually put the configuration files in the directory 'src/main/resource' 
right click the directory and choose the 'Spring Bean Configuration file', this option only can be seen in STS or the Eclipse which has been installed a spring plugin.
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/11.png)
![image](https://github.com/fengandzhy/Blog/raw/master/Images/spring/article01/12.png)



