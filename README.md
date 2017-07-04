# JavaScript interview questions

#### #1 What will the output for the below code and why?

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
