The most obvious application of functions is defining new vocabulary.

### Defining a function:
A function definition is just a regular variable definition where the value given to the variable happens to be a function.

var square = function(x){
     return x * x;
}
console.log(square(x)); // 144

A return statement determines the value the function returns. A function without a return statement could return `undefined` value in the very end.

### Parameters and scopes
The parameters to a function behave like regular variables, but their initial values are given by the caller of the function, not the code in the function itself.

An important property of functions is that the variables created inside of them, including their parameters, are local to the function.

var x = "outside";

var f1 = function() {
  var x = "inside f1";
};
f1();
console.log(x);
// → outside

var f2 = function() {
  x = "inside f2";
};
f2();
console.log(x);
// → inside f2
### Nested Scope
Functions can be created inside other functions, producing several degrees of locality.

var landscape = function() {
  var result = "";
  var flat = function(size) {
      for (var count = 0; count < size; count++)
      result += "_";
  };
  var mountain = function(size) {
      result += "/";
      for (var count = 0; count < size; count++)
      result += "'";
      result += "\\";
  };

  flat(3);
  mountain(4);
  flat(6);
  mountain(1);
  flat(1);
  return result;
};

console.log(landscape());
// → ___/''''\______/'\_

flat function and mountain function could see `result` variable but they can't see each other's count variable. These two functions have two different scopes.

But in JavaScript, functions are the only things that create a new scope.

A let keyword has been introduced, which works like var but creates a variable that is local to the enclosing block, not the enclosing function.

### Functions as values
var launchMissiles = function(value) {
  missileSystem.launch("now");
};
if (safeMode)
  launchMissiles = function(value) {/* do nothing */};

### Declaration notation

function square(x) {
  return x * x;
}
function declarations are not part of the regular top-to-bottom flow of control:
console.log("The future says:", future());

function future() {
  return "We STILL have no flying cars.";
}

### The "call" stack
The place where the computer stores the context is the call stack. Every time a function is called, the current context is put on top of this “stack”. When the function returns, it removes the top context from the stack and uses it to continue execution.

### Optional arguments
If a function only accept one variable, and you passed in 5 variables, it will only accept the first variable and ignore the rest. If you pass in too few, the ones with no definition will be "undefined".
alert("Hello", "Jesus", "John");
// result: only "Hello".

function power(base, exponent) {
  if (exponent == undefined)
  exponent = 2;
  var result = 1;
  for (var count = 0; count < exponent; count++)
  result *= base;
  return result;
}
console.log(power(4));
// → 16
console.log(power(4, 3));
// → 64

### Closure:
What happens to local variables when the function call that created them is no longer active?
function wrapValue(n) {
  var localVariable = n;
  return function() { return localVariable; };
}

var wrap1 = wrapValue(1);
var wrap2 = wrapValue(2);
console.log(wrap1());
// → 1
console.log(wrap2());
// → 2
In fact, multiple instances of the variable can be alive at the same time, which is another good illustration of the concept that local variables really are re-created for every call—different calls can’t trample on one another’s local variables.

This feature—being able to reference a specific instance of local variables in an enclosing function—is called closure. A function that “closes over” some local variables is called a closure.

Thinking about programs like this takes some practice. A good mental model is to think of the function keyword as “freezing” the code in its body and wrapping it into a package (the function value). So when you read return function(...) {...}, think of it as returning a handle to a piece of computation, frozen for later use.

### Recursion:
It is perfectly okay for a function to call itself, as long as it takes care not to overflow the stack. A function that calls itself is called recursive.
function power(base, exponent) {
  if (exponent == 0)
  return 1;
  else
  return base * power(base, exponent - 1);
}

console.log(power(2, 3));
// → 8
But recursion is not always just a less-efficient alternative to looping. Some problems are much easier to solve with recursion than with loops. Most often these are problems that require exploring or processing several “branches”, each of which might branch out again into more branches.
