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
