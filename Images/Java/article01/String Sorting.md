
In Java, we often need to sort a string list, this article will show you how to sort a string list.

## principle

In Java, we use compareTo to compare two string. for example please look at the code fragment below,

```java
int result = o1.compareTo(o2);	
```
if o1 is greater than o2 then the result will be greater than 0. For example if o1 == "b", o2 == "a" then o1 is greater than o2. Conversely, if o2 is greater than o1 then the result will be less than 0 


we use such principle to sort a string list. please look at the code below 

```java
		Collections.sort(array,new Comparator<String>(){
			@Override
			public int compare(String o1, String o2) {				
				int result = o1.compareTo(o2);				
				return result;
			}				
		});
```

Let's assume that there are two string objects in this list ("a","b"), In the above example, will the order of the elements in this list be changed?  

The answer is no. In order to figure out the answer we need to figure out what is o1 and what is o2? Normally, people will naturally believe o1 is "a" and o2 is "b".

Actually the idea is not correct. o1 is "b" and o2 is "a" that is to say o1 is the next element of o2 in the list. of course the result is greater than 0.

when the result is greater than 0 these two element will not exchange positions with each other. 

  
## samples 

* normal order 

```java
		Collections.sort(array,new Comparator<String>(){
			@Override
			public int compare(String o1, String o2) {				
				int result = o1.compareTo(o2);				
				return result;
			}				
		});
```

* reverse order 
```java
		Collections.sort(array,new Comparator<String>(){
			@Override
			public int compare(String o1, String o2) {
				int result = -o1.compareTo(o2);
				return result;
			}				
		});
```

* normal order ignore case 
```java
		Collections.sort(array,new Comparator<String>(){
			@Override
			public int compare(String o1, String o2) {
				int result = o1.compareToIgnoreCase(o2);
				return result;
			}				
		});
```


* reverse order ignore case 
```java
		Collections.sort(array,new Comparator<String>(){
			@Override
			public int compare(String o1, String o2) {
				int result = o1.compareToIgnoreCase(o2);
				return result;
			}				
		});
```





