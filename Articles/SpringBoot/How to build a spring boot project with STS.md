## Overview
Before we discuss the features of Spring Boot, I would like to show you how to build a Spring Boot project with STS here. 
1.create a spring starter project, the click next 
![image](https://github.com/fengandzhy/Blog/raw/master/Images/SpringBoot/article01/1.png) 
2.Input Name, GroupId, Artifact, package ect. please make sure that in the Packaging you choose the Jar and in the Language you choose Java the click next 
![image](https://github.com/fengandzhy/Blog/raw/master/Images/SpringBoot/article01/2.png) 
3.choose the version of spring boot, in this project we use 2.1.5, because at present this version is very stable, after you choose the version please choose the starters you want. if you are a starter, I suggest you just choose the web starter which like the below pictures shows.
![image](https://github.com/fengandzhy/Blog/raw/master/Images/SpringBoot/article01/3.png) 
4.click finish 
![image](https://github.com/fengandzhy/Blog/raw/master/Images/SpringBoot/article01/4.png)
5.after STS build the workspace automatically, you will find a strange mistake in you pom file just like below picture shows.
![image](https://github.com/fengandzhy/Blog/raw/master/Images/SpringBoot/article01/5.png) 
```xml
<maven-jar-plugin.version>3.1.1</maven-jar-plugin.version>
```
