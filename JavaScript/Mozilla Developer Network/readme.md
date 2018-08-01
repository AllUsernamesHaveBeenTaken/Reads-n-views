# JavaScript Guide

[Source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Introduction)

[Where did I left off?](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)

## What I've learned?!

1. You can experiment with JavaScript by creating snippets in your Chrome developers Tools.

   * Source > Snippets

1. Hoisted Variables and Functions

   * Variables that are hoisted return a value of undefined. So even if you declare and initialize after you use or refer to this variable, it still returns undefined. 
   
   ```javascript
   console.log(x === undefined); // true
   var x = 3;
   
   // The above wil be interpreted as:
   var x;
   console.log(x === undefined); // true
   x = 3;
   ```
   *  Function hoisting only works with function declaration and not with function expression.
   ```javascript
   // This will work
   console.log(square(5));
   function square(n) { return n * n; }
   
   // This will not work
   console.log(square); // square is hoisted with an initial value undefined.
   console.log(square(5)); // TypeError: square is not a function
   var square = function(n) { 
   return n * n; 
   }
   ```

1. The properties of objects and content of an array assigned to constants are not protected

1. Converting strings to numbers

   * An alternative method to `parseInt()` and `parseFloat()` for retrieving a Number from a String is with the + (unary plus) operator.
   
   ```javascript
   '1.1' + '1.1' // '1.11.1'
   (+'1.1') + (+'1.1') // 2.2   
   // Note: the parentheses are added for clarity, not required.
   ```
1. if...else statement

   * Do not confuse the primitive boolean values true and false with the true and false values of the Boolean object.

   ```javascript
   var b = new Boolean(false);
   if (b) // this condition evaluates to true
   if (b == true) // this condition evaluates to false
   ```
1. Closures

   * You can call the outer function and specify arguments for both the outer and inner function.
  
   ```javascript
   function outside(x) {
     function inside(y) {
       return x + y;
     }
     return inside;
   }
   fn_inside = outside(3); // Think of it like: give me a function that adds 3 to whatever you give it
   result = fn_inside(5); // returns 8
   result1 = outside(3)(5); // returns 8
   ```
1. Arguments object

   * Using the arguments object, you can call a function with more arguments than it is formally declared to accept. This is often useful if you don't know in advance how many arguments will be passed to the function. You can use arguments.length to determine the number of arguments actually passed to the function, and then access each argument using the arguments object.
   
   ```javascript
   function myConcat(separator) {
     var result = ''; // initialize list
     var i;
     // iterate through arguments
     for (i = 1; i < arguments.length; i++) {
       result += arguments[i] + separator;
     }
     return result;
   }
   myConcat(', ', 'red', 'orange', 'blue');
   ```
   * The arguments variable is "array-like", but not an array. It is array-like in that it has a numbered index and a length property. However, it does not possess all of the array-manipulation methods.
   
1. Rest parameters
   * The rest parameter syntax allows us to represent an indefinite number of arguments as an array. In the example, we use the rest parameters to collect arguments from the second one to the end. We then multiply them by the first one. This example is using an arrow function, which is introduced in the next section.
   
   ```javascript
   function multiply(multiplier, ...theArgs) {
      return theArgs.map(x => multiplier * x);
   }

   var arr = multiply(2, 1, 2, 3);
   console.log(arr); // [2, 4, 6]
   ```
1. Comma Operator

   * The comma operator (,) simply evaluates both of its operands and returns the value of the last operand. This operator is primarily used inside a for loop, to allow multiple variables to be updated each time through the loop.
   
   ```javascript
   var x = [0,1,2,3,4,5,6,7,8,9]
   var a = [x, x, x, x, x];

   for (var i = 0, j = 9; i <= j; i++, j--)
   console.log('a[' + i + '][' + j + ']= ' + a[i][j]);
   ```
   
1. Unary operators

   **delete**
   
   * The delete operator deletes an object, an object's property, or an element at a specified index in an array. You can use the delete operator to delete variables declared implicitly but not those declared with the var statement. If the delete operator succeeds, it sets the property or element to undefined. The delete operator returns true if the operation is possible; it returns false if the operation is not possible.
   
   ```javascript
   x = 42;
   var y = 43;
   myobj = new Number();
   myobj.h = 4;    // create property h
   delete x;       // returns true (can delete if declared implicitly)
   delete y;       // returns false (cannot delete if declared with var)
   delete Math.PI; // returns false (cannot delete predefined properties)
   delete myobj.h; // returns true (can delete user-defined properties)
   delete myobj;   // returns true (can delete if declared implicitly)
   ```
   * When you delete an array element, the array length is not affected. For example, if you delete a[3], a[4] is still a[4] and a[3] is undefined.
   * If you want an array element to exist but have an undefined value, use the undefined keyword instead of the delete operator.

1. Array object

   * If you wish to initialize an array with a single element, and the element happens to be a Number, you must use the bracket syntax. When a single Number value is passed to the Array() constructor or function, it is interpreted as an arrayLength, not as a single element.
   
   * In ES2015, you can use Array.of static method to create arrays with single element.
   
   ```javascript
   let array = Array.of(9.3);  // wisenArray contains only one element 9.3
   ```
1. Map object 

   * ECMAScript 2015 introduces a new data structure to map values to values. A Map object is a simple key/value map and can iterate its elements in insertion order.
   
   * These three tips can help you to decide whether to use a Map or an Object:
  
      * Use maps over objects when keys are unknown until run time, and when all keys are the same type and all values are the same type.
      * Use maps if there is a need to store primitive values as keys because object treats each key as a string whether it's a number value, boolean value or any other primitive value.
      * Use objects when there is logic that operates on individual elements.
   
1. Set object 

   * Set objects are collections of values. You can iterate its elements in insertion order. A value in a Set may only occur once; it is unique in the Set's collection.
   
   * You can create an Array from a Set using Array.from or the spread operator. Also, the Set constructor accepts an Array to convert in the other direction. Note again that Set objects store unique values, so any duplicate elements from an Array are deleted when converting.
   
   ```javascript
   Array.from(mySet);
   [...mySet2];

   mySet2 = new Set([1, 2, 3, 4]);
   ```
   
