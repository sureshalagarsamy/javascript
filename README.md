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

As a result (if you are not using strict mode), the output of the code snippet would be:
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
