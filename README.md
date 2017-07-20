# JavaScript interview questions

#### #1 What will the output for the below code?

```javascript
(function(){
  var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```

most JavaScript developers would expect ```typeof a``` and ```typeof b``` to both be undefined in the above example.

However, that is not the case. The issue here is that most developers incorrectly understand the statement var a = b = 3; to be shorthand for:

``` var b = 3 ``` <br>
``` var a = b ```

But in fact, ```var a = b = 3;``` is actually shorthand for:

```b = 3``` <br>
```var a = b```

As a result (if you are not using strict mode), the output of the code snippet would be
```javascript
a defined? false
b defined? true
```

#### #2 What will the output for the below code?

```javascript
console.log(0.1 + 0.2);
console.log(0.1 + 0.2 == 0.3);
```

Answer to this question would be ```0.3``` and ```true``` correct? But your answer is wrong. In javscript all numbers will be treated with floating point precision. So may not yield the correct answer for this.

Surprisingly, it will print out:

```javascript
0.30000000000000004
false
```

to get a proper output we may need to do the following work around.

```javascript
console.log((0.1*10  +  0.2*10)/10);  // output 0.3
```


#### #3 What will the output for the below code?

```javascript
console.log(1 +  "2" + "2");		// 122
console.log(1 +  +"2" + "2");		// 32
console.log(1 +  -"1" + "2");		// 02
console.log(+"1" +  "1" + "2");		// 112
console.log( "A" - "B" + "2");		// NaN2
console.log( "A" - "B" + 2);		// NaN
console.log('1'+'C')			// "1C"
console.log('1'*'C')			// NaN
console.log('1'/'C')			// NaN
console.log('1'-'C')			// NaN
console.log('1'+0)			// "10"
console.log('1'*0)			// 0
console.log('1'/0)			// Infinity
console.log('1'-0)			// 1
console.log("1" - - "1");		// 2
```


#### #4 What will the output for the below code?

```javascript
console.log(false == '0')		// true
console.log(false === '0')		// false
```


#### #5 Write palindrome programe

```javascript
function isPalindrome(str) {
    str = str.replace(/\W/g, '').toLowerCase();
    return (str == str.split('').reverse().join(''));
}
```

```javascript
isPalindrome('MALAYALAM');	// true
isPalindrome('Anna');		// true
isPalindrome('Madam');		// true
isPalindrome('SURESH');		// false
```


#### #6 Write a mul function which will produce the following outputs when invoked:

```javascript
console.log(mul(2)(3)(4)); // output : 24 
console.log(mul(4)(3)(4)); // output : 48
```

```javascript
function mul (x) {
    return function (y) { // anonymous function 
        return function (z) { // anonymous function 
            return x * y * z; 
        };
    };
}
```



#### #7 How to empty an array in JavaScript

### Method-1

```javascript
A = [];
```

This is perfect if you ```don't have references``` to the original array A anywhere else, because this actually creates a brand new (empty) array. Only use this if you only reference the array by its original variable A.

This code sample shows the issue you can encounter when using this method:

```javascript
var arr1 = ['a','b','c','d','e','f'];
var arr2 = arr1;  // Reference arr1 by another variable 
arr1 = [];
console.log(arr2); // Output ['a','b','c','d','e','f']
```

### Method-2

```javascript
A.length = 0;
```


#### #8 What is the difference between the function declarations below?

```javascript
var first = function() { 
   // Some code
}; 

function second() { 
    // Some code
 }; 
```
The main difference is the function ```first``` is defined at run-time whereas function ```second``` is defined at parse time.




#### #9 What will be the output of the code below?

```javascript
var Employee = {
  company: 'xyz'
}
var emp1 = Object.create(Employee);
delete emp1.company
console.log(emp1.company);
```

The output would be ```xyz```. Here, ```emp1``` object has ```company``` as it is prototype property. The ```delete``` operator doesn’t delete prototype property.

```emp1``` object doesn’t have company as its own property.

 However, we can delete the ```company``` property directly from the ```Employee``` object using ```delete Employee.company```. 


 
#### #10 What is ‘this’ keyword in JavaScript?

```this``` keyword is used to point at the current object in the code.

For instance: If the code is presently at an object created by the help of the ‘new’ keyword, then ‘this’ keyword will point to the object being created.

 
#### #11 What is the difference between window.onload and onDocumentReady?

The ```window.onload``` event won’t trigger until every single element on the page has been fully loaded, including images and CSS. The downside to this is it might take a while before any code is actually executed. You can use ```onDocumentReady``` to execute code as soon as the DOM is loaded instead.


#### #12 How to convert a string to lowercase?

```javascript
var str='Suresh Alagarsamy';
str = str.toLowerCase();
console.log(str);
```


#### #13 How to convert JSON Object to String?

```javascript
var myobject=[{test:'Web'},'Technology','Experts','Notes']
JSON.stringify(myobject);

// "[{"test":"Web"},"Technology","Experts","Notes"]"
```

#### #14 How to convert JSON String to Object?

```javascript
var myJSONData = '[{"test":"Web"},"Technology","Experts","Notes"]';
JSON.parse(myJSONData);

// output
[{test:'Web'},'Technology','Experts','Notes']
```

#### #15 Can i declare a variable as CONSTANT in JavaScript?

ES2015 or ECMAScript 6, the latest version of JavaScript, has a notion of const:

```javascript
const MY_CONSTANT = "SURESH";
```

This will work in pretty much all browsers except IE 8, 9 and 10. Some may also need strict mode enabled.


#### #16 What is a Namespace in JavaScript?

Namespace is a container for set of identifiers, functions, methods and all that. It gives a level of direction to its contents so that it will be well distinguished and organized.

To achieve this, what we need to do is to create a namespace in application and use it.

<i>Unfortunately JavaScript doesn’t provide namespace by default. </i>So anything we create in JavaScript is global and we continue polluting that ```global``` namespace by adding more to that. As we know, in JavaScript everything is an object and creating an object is very simple. We can achieve namespace very easily with some minor tweaks.

```javascript
var myProduct = 'SONY';
function abc() {
    // code here
}

function xyz() {
	// code here
}
```

In the above code two functions ```abc()``` ```xyz()``` and variable ```myProduct``` are fall into global namespace.


* JavaScript Sample Namespace

```javascript
var MYAPPLICATION = {
	myProduct: 'SONY',
	abc:function() {
    	// code here
    },
	xyz:function() {
    	// code here
    }
}
```

To access any of the methods or variables, you need to fetch it through the MYAPPLICATION. Even we can create nested JavaScript Namespace as well.


#### #17 What Is Strict Mode In JavaScript?

 It provides following enhancements.
 
 * To use a variable, it has become mandatory to declare it.
 * It disallows duplicate property and parameter names.
 * It deprecates the “with” statement.
 * JavaScript will throw an error if we try to assign a value to a read-only property.
 * It decreases the global namespace pollution.

To enable strict mode, we have to add, “use strict” directive to the code. The physical location of the “strict” directive determines its scope. If used at the beginning of the js file, its scope is global. However, if we declare strict mode at the first line in the function block, its scope restricts to that function only.


#### #18 What Is EncodeURI() Function?

The encodeURI() function is used to encode a URI. This function encodes all special characters, except these < , / ? : @ & = + $ #>.

<i>Let’s See An Example.</i>

```javascript
var uri="http://www.suresh.com/how to make a website using javaScript";
var encodedURI = encodeURI(uri);
console.log(encodedURI);

// Output
// http://www.suresh.com/how%20to%20make%20a%20website%20using%20javaScript
```

We see that JavaScript encodes the space between the words in the <uri> variable as <%20>. Thus, the encodeURI function is used to encode special reserved characters and other non-ASCII characters in the URI.


#### #19 What Is Scope In JavaScript?

In JavaScript, the scope is of two types.

* Global Scope
* Local Scope

<b>Global Scope</b>

A variable defined outside a function comes under the Global scope. Variables defined inside the Global scope are accessible from any part of the code.

```javascript
var name = 'SURESH';
var myObject = {name:'SURESH',company:'xyz'};

function callMe() {
	alert(name);			 // Accessible here
    console.log(myObject);	 // Accessible here
}
```

<b>Local Scope</b>

Variables defined inside a function comes under the Local scope.

```javascript
function callMe() {
	var name = "SURESH";	// not accessible in other functions
}
```



#### #20 What Is Prototype Property In JavaScript?

Every JavaScript function has a prototype property (by default this property is null), that is mainly used for implementing inheritance. We add methods and properties to a function’s prototype so that it becomes available to that function.


```javascript
function callMe(a,b) {
	this.x = a;
	this.y = b;
}

callMe.prototype.addMe = function() {
	return 9 + this.x + this.y;
}

var callMeObj = new callMe(2,3);
console.log(callMeObj.addMe());
```

#### #21 Is JavaScript case sensitive?

All JavaScript identifiers are <b>case sensitive</b>. 

The variables ```lastName``` and ```lastname```, are two different variables.

Historically, programmers have used different ways of joining multiple words into one variable name. I would suggest the developers to use ```lower camel case``` letters like below.

``` myName ``` ``` firstName``` ```lastName```

#### upper camel case

![image](https://user-images.githubusercontent.com/6780840/27864704-47528b42-61ad-11e7-874a-5ca9bce63246.png)


#### #22 What is the difference between ViewState and SessionState?

* ```ViewState``` is specific to a page in a session.
* ```SessionState``` is specific to user specific data that can be accessed across all pages in the web application.

#### #23 What are the different types of errors in JavaScript?

There are three types of errors:

* ```Load time errors``` Errors which come up when loading a web page like improper syntax errors are known as Load time errors and it generates the errors dynamically.
* ```Run time errors``` Errors that come due to misuse of the command inside the HTML language.
* ```Logical Errors``` These are the errors that occur due to the bad logic performed on a function which is having different operation.


#### #24 What is ```undefined``` and ```not defined```?


<b>undefined</b>
```javascript
var x; 				// declaring x
console.log(x); 	// output: undefined 
```


<b>not defined</b>
```javascript
console.log(y); 	// output: Uncaught ReferenceError: y is not defined
```

#### #25 How do you check if a variable is an array in JavaScript?

There are many methods:

### method-1

<b>variable.constructor === Array</b>

```javascript
function checkVariable(param){
 	if(param.constructor === Array){ 
		console.log('Array');
 	} else {
 	  console.log('Not an array');
 	}
}
checkVariable({name:'SURESH'});		// Not an array
checkVariable(['A']);			// Array
```


### method-2

<b>Array.isArray(obj) == true</b>

```javascript
function checkVariable(param){
 	if(Array.isArray(param) == true){ 
		console.log('Array');
 	} else {
 	  console.log('Not an array');
 	}
}
checkVariable({name:'SURESH'});		// Not an array
```

#### #26 Find duplicate values in a array?

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Find duplicate values in a JavaScript array</title>
</head>
	<body>
		<script>
		function find_duplicate_in_array(myArray) {
			var i, result=[], obj={}; 
			for(i=0; i<myArray.length; i++)
			{
				obj[myArray[i]] = 0;	
			}
            
            		// output for the above for loop is 
            		// Object {1: 0, 2: 0, 3: 0, 4: 0, 5: 0, 6: 0, 7: 0, 8: 0, 71: 0, -2: 0}
            
			for(i in obj)	// loop for object method
			{
				result.push(i);
			}
			return result;
		}
		var arrayData = [1, 2, -2, 4, 5, 4, 7, 8, 7, 7, 71, 3, 6];

		console.log(find_duplicate_in_array(arrayData));
		</script>
	</body>
</html>
```

### Output

![image](https://user-images.githubusercontent.com/6780840/28199739-a2b4b954-6885-11e7-818f-f19d1852c552.png)

