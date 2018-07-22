# JavaScript Guide

[Source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Introduction)

[Where did I left off?](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)

## What I've learned?!

1. You can experiment with JavaScript by creating snippets in your Chrome developers Tools.

   * Source > Snippets

2. Hoisted Variables

   * Variables that are hoisted return a value of undefined. So even if you declare and initialize after you use or refer to this variable, it still returns undefined. 
   ```javascript
   console.log(x === undefined); // true
   var x = 3;
   
   // The above wil be interpreted as:
   var x;
   console.log(x === undefined); // true
   x = 3;
   ```

3. The properties of objects and content of an array assigned to constants are not protected

4. Converting strings to numbers

   * An alternative method to `parseInt()` and `parseFloat()` for retrieving a Number from a String is with the + (unary plus) operator.
   ```javascript
   '1.1' + '1.1' // '1.11.1'
   (+'1.1') + (+'1.1') // 2.2   
   // Note: the parentheses are added for clarity, not required.
   ```
