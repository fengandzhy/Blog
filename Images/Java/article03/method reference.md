## Overview
In the article of [Lambda Expression](https://github.com/fengandzhy/Blog/issues/7) I show you there are only 2 lines in the core code of sort the list of 'Apple'
Is there any more simplified method? this is another topic we will discuss in this sector, the method reference. 
please look at the below two fragment code 
```java
List<Apple> list = Arrays.asList(new Apple("abc", 123), new Apple("Green", 110), new Apple("red", 123));
Comparator<Apple> byColor2 = (o1, o2) -> o1.getColor().compareTo(o2.getColor());
apples.sort(byColor2);
```
```java
List<Apple> list = Arrays.asList(new Apple("abc", 123), new Apple("Green", 110), new Apple("red", 123));
Comparator<Apple> byColor = Comparator.comparing(Apple::getColor);
apples.sort(byColor);
```
The above two fragment code are used to sort the list of apple by their color. However, we can find something new in the second code fragment it is 
```java
Apple::getColor
```
This is the method reference, it indicates the 'getColor' method in 'Apple' 

## More examples of method reference
example1
```java
Function<String, Integer> f = Integer::parseInt;
Integer a = f.apply("123");
logger.info(a);
```
'Integer::parseInt' means the static method in 'Integer'
```java
public static int parseInt(String s) throws NumberFormatException {
	return parseInt(s,10);
}
``` 
example2
```java
String str = new String("Hello");
Function<Integer, Character> fun = str::charAt;
logger.info(fun.apply(3));
```
'str::charAt' means the method of 'charAt' in 'String'
```java
public char charAt(int index) {
	if ((index < 0) || (index >= value.length)) {
		throw new StringIndexOutOfBoundsException(index);
	}
	return value[index];
}
``` 
example3
```java
StringSupplier<String> supplier = String::new;
String s = supplier.get("abc");
logger.info(s);
```
'String::new' means create a new String instance
## conslusion
When we define an instance of class which implements an interface with an annotation of  '@FunctionalInterface', method reference is a sign which is responsible for telling the java programe that we will call this method here. 
for example in the above exmaples 
```java
Function<Integer, Character> fun = str::charAt;
``` 



 

