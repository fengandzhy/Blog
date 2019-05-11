## Overview
There are a lot of new features in Java 8. Lambda expression is one of them, other new features are mostly based on it. 
This article will show you some examples of Lambda expression so that you can understand the usage of lambda expression. 
Before we discuss the usage of lambda expressions, first let me create a java bean named 'Apple' 
```java
public class Apple {	
	private String color;
	private double weight;
	public String getColor() {
		return color;
	}
	public void setColor(String color) {
		this.color = color;
	}
	public double getWeight() {
		return weight;
	}
	public void setWeight(double weight) {
		this.weight = weight;
	}
	@Override
	public String toString() {
		return "Apple [color=" + color + ", weight=" + weight + "]";
	}
	public Apple(String color, double weight) {
		super();
		this.color = color;
		this.weight = weight;
	}	
}
```
## Compare
Now suppose we have a list of apple, then we need to sort the list according to the color of the apply. Before Java8 we need to write our code like that 
```java
Comparator<Apple> byColor1 = new Comparator<Apple>() {
	public int compare(Apple o1, Apple o2) {
		return o1.getColor().compareTo(o2.getColor());
	}           
};
apples.sort(byColor1);
```
It can be seen that there are 6 lines in the core code. How about Java8? we can write code like that.
```java
Comparator<Apple> byColor2 = (o1, o2) -> o1.getColor().compareTo(o2.getColor());
apples.sort(byColor2);
```
The core code only has two lines. greatly simplified? 
## Reason
The question is why we can do such things like that in Java8. Let's investigate the difference between Java8 and Java7 in source code. 
please look at the shortcuts below, they are souce code  of Comparator in Java8 and Java7
Java8
![image](https://github.com/fengandzhy/Blog/raw/master/Images/Java/article02/1.png) 
Java7
![image](https://github.com/fengandzhy/Blog/raw/master/Images/Java/article02/2.png) 
from above two pictures we can see that there are a more annotation in Java8 it is 
```java
@FunctionalInterface
```
it is because this annotation, we can simplified the code of Java8. 
## Another two exmples
Let's look at another two examples
example1
```java
Function<String, Integer> flambda = s -> s.length();
logger.info(flambda.apply("abc"));
```
In this example 'flambda' is an instance of the class which implements the interface of 'Function', the logic of 'flambda' is return the resutlt of running length()
therefore we can see the length of the string 'abc'. if the object transmitted into 'flambda' dose not have the method 'length()', a compile error will be output
 
example2
```java
Consumer<Apple> consumer = s -> {
logger.info(s.getColor());
logger.info(s.getWeight());
};
consumer.accept(new Apple("red", 100.00));
```
##Define the interface by ourselves 
```java
@FunctionalInterface
public interface Modifier<A,B,C> {
	C modify(A a, B b);
}
```
this is a custmer interface, we can use lambda expression like that 
```java
Modifier<Apple,Integer,String> modifier = (a,b)->{
	return a.getColor()+b;
};
String str = modifier.modify(new Apple("red", 100.00), 10);
logger.info(str);
``` 







 

