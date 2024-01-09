# friendly-giggle
Info about let const and var and how does it work


Var:
Var is use to declare a variable in globally-scopped or locally scopped

Case :1

var x = 10;
if( x > 0){
  var x = 5
  console.log(x) //Output = 5
}

console.log(x) //Output = 5
The variable x is initially declared and assigned the value of 10 outside the if block. 
Inside the if block, another variable with the same name x is declared and assigned the value 5.
However, because var does not have block-level scoping in JavaScript, the second declaration of x 
inside the if block affects the variable declared outside the block. As a result, when you log the 
value of x both inside and outside the if block, the output is 5 in both cases.

It's important to note that this behavior is specific to the var keyword. Modern JavaScript introduces
let and const, which have block-level scoping and behave more intuitively in situations like the one 
you've shown. If you were to replace var with let in your code, you would get different results, and 
the inner x would be a separate variable with its own scope.

Case :2

In this code snippet:
  var x = 0;
  function f(){
  var x = y = 1;
  console.log(x, y); // Output: 1, 1
  }
  f();
  console.log(x, y); // Output: 0, 1

  Let's break down what happens:
  1. Inside the function `f`, there is a variable declaration `var x = y = 1;`. 
  This is equivalent to declaring two variables: `var x = 1;` and `y = 1;`.
  The variable `y` is assigned a value of `1` without using the `var` keyword, which means it becomes a global variable.

  2. When you log `x` and `y` inside the function using `console.log(x, y);`, 
  it prints `1, 1` because it refers to the local variable `x` and the global variable `y` (created due to the absence of the `var` keyword).

  3. After calling the function `f`, you log `x` and `y` outside the function using `console.log(x, y);`. 
  Here, `x` refers to the global variable declared at the beginning (`var x = 0;`), and `y` refers to the global variable created inside the function. 
  Hence, it prints `0, 1`.
  It's important to be cautious when using variables without explicitly declaring them with `var`, 
  `let`, or `const`, as they can lead to unexpected results due to variable hoisting and global scoping.

Case :3
Let's analyze the code step by step:
  var x = 1;
  function a(){
      var y = 2;
      console.log(x, y); // Output: 1 2

      function b(){
          x = 3;
          y = 4;
          z = 5;
      }

      b();

      console.log(x, y, z); // Output: 3 4 5
  }

  a();

  console.log(x, z); // Output: 3 5
  console.log("y", typeof(y)); // Output: undefined
  console.log("x", typeof(x)); // Output: number
  console.log("z", typeof(z)); // Output: number
```
Here's the breakdown:

  1. Initial global variables: `x` is assigned `1`.
  2. Inside function `a`:
  - Local variable `y` is assigned `2`.
  - Logging `x` and `y` within `a` outputs `1 2`.
  - Inside function `b`:
      - Global variable `x` is reassigned to `3`.
      - Local variable `y` is reassigned to `4`.
      - Variable `z` is assigned `5`. Note that `z` becomes a global variable since it is not declared with `var`, `let`, or `const`.
  - Logging `x`, `y`, and `z` within `a` after calling `b` outputs `3 4 5`.
  3. Logging `x` and `z` globally outputs `3 5`.
  4. Attempting to log `y` globally results in `undefined` since `y` was declared with `var` inside `a`, making it function-scoped and not accessible outside the function.
  5. Logging the types of `x`, `y`, and `z` globally shows that `x` and `z` are of type `number`, while `y` is `undefined` as it is not accessible globally.

*/

