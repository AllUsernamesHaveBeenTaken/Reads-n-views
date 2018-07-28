# JavaScript Guide

[Source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Introduction)

[Where did I left off?](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)

## What I've learned?!

1. You can experiment with JavaScript by creating snippets in your Chrome developers Tools.

   * Source > Snippets

2. Hoisted Variables and Functions

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

3. The properties of objects and content of an array assigned to constants are not protected

4. Converting strings to numbers

   * An alternative method to `parseInt()` and `parseFloat()` for retrieving a Number from a String is with the + (unary plus) operator.
   
   ```javascript
   '1.1' + '1.1' // '1.11.1'
   (+'1.1') + (+'1.1') // 2.2   
   // Note: the parentheses are added for clarity, not required.
   ```
5. if...else statement

   * Do not confuse the primitive boolean values true and false with the true and false values of the Boolean object.

   ```javascript
   var b = new Boolean(false);
   if (b) // this condition evaluates to true
   if (b == true) // this condition evaluates to false
   ```
6. Closures

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
7. Arguments object

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
   
8. Rest parameters
   * The rest parameter syntax allows us to represent an indefinite number of arguments as an array. In the example, we use the rest parameters to collect arguments from the second one to the end. We then multiply them by the first one. This example is using an arrow function, which is introduced in the next section.
   
   ```javascript
   function multiply(multiplier, ...theArgs) {
      return theArgs.map(x => multiplier * x);
   }

   var arr = multiply(2, 1, 2, 3);
   console.log(arr); // [2, 4, 6]
   ```
   
