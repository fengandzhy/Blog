
In JavaScript, we often need to convert a string to an object or convert an object to a string. please look at the code below
```js
var a={"name":"tom","sex":"M","age":"24"};//这是一个对象
var b='{"name":"tom","sex":"M","age":"24"}';//这是一个字符串
```
we know a is an object b is a string. what is the difference between them? please look at the short cut below.
![image](https://github.com/fengandzhy/Blog/raw/master/Images/JavaScript(ES5)/article02/1.png)
Is is very clear? I think the picture above has alread shown the difference between a and b. How to convert them? please look at the code below 
```js
var aToStr=JSON.stringify(a);//将对象转换成一个字符串
var bToObj=JSON.parse(b);//将字符创转换成一个对象
```
above code convert a to an object and convert b to an object. Let me write more code to verify them please look at the code below 
```js
console.log(aToStr);
console.log(bToObj);
console.log(typeof(aToStr));//string
console.log(typeof(bToObj));//object
```
the below picture is the result of running the above code 
![image](https://github.com/fengandzhy/Blog/raw/master/Images/JavaScript(ES5)/article02/2.png)
The same thing also could be found between arrays and strings, please look at the code below 
```js
const myArr = ['bacon', 'letuce', 'tomatoes'];
const myArrStr = JSON.stringify(myArr);
console.log(myArrStr);
console.log(JSON.parse(myArrStr));
console.log(typeof(myArr));
console.log(typeof(myArrStr));
``` 
the result is 
![image](https://github.com/fengandzhy/Blog/raw/master/Images/JavaScript(ES5)/article02/3.png)
## conslusion

In JavaScript, JSON.stringify() is used to convert an object(normally is json or arry) to string. JSON.parse() is used to convert a tring to an object. 
```js
console.log(aToStr);
console.log(bToObj);
console.log(typeof(aToStr));//string
console.log(typeof(bToObj));//object
```



