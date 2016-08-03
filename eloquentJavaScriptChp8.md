Normally, problems surface only when a program encounters a situation that the programmer didn’t originally consider.

JavaScript --> dynamic type --> error prone --> hard to debug

### Strict mode:

JavaScript can be made a little more strict by enabling strict mode. This is done by putting the string "use strict" at the top of a file or a function body.

function canYouSpotTheProblem() {
  "use strict";
  for (counter = 0; counter < 10; counter++)
    console.log("Happy happy");
}

canYouSpotTheProblem();
// → ReferenceError: counter is not defined

Also, in strict mode, this binding holds the valueundefined in functions that are not called as methods. When making such a call outside of strict mode, this refers to the global scope object.

For example, consider the following code, which calls a constructor without thenew keyword so that its this will not refer to a newly constructed object:

function Person(name) { this.name = name; }
var ferdinand = Person("Ferdinand"); // oops
console.log(name);
// → Ferdinand

So the bogus call to Person succeeded but returned an undefined value and created the global variable name. In strict mode, the result is different.

"use strict";
function Person(name) { this.name = name; }
// Oops, forgot 'new'
var ferdinand = Person("Ferdinand");
// → TypeError: Cannot set property 'name' of undefined

### Testing:
Software that help you build and run collections of tests (test suites) by providing a language (in the form of functions and methods) suited to expressing tests and by outputting informative information when a test fails. These are called testing frameworks.

### Debugging:
An alternative to using console.log is to use the debugger capabilities of your browser. Modern browsers come with the ability to set a breakpoint on a specific line of your code.

### Exceptions:
Exceptions are a mechanism that make it possible for code that runs into a problem to raise (or throw) an exception, which is simply a value.

function promptDirection(question) {
  var result = prompt(question, "");
  if (result.toLowerCase() == "left") return "L";
  if (result.toLowerCase() == "right") return "R";
  throw new Error("Invalid direction: " + result);
}

function look() {
  if (promptDirection("Which way?") == "L")
    return "a house";
  else
    return "two angry bears";
}

try {
  console.log("You see", look());
} catch (error) {
  console.log("Something went wrong: " + error);
}

The throw keyword is used to raise an exception.  The throw keyword is used to raise an exception. Catching one is done by wrapping a piece of code in a try block, followed by the keyword catch. When the code in the try block causes an exception to be raised, the catch block is evaluated. The variable name (in parentheses) after catch will be bound to the exception value. After the catch block finishes—or if the try block finishes without problems—control proceeds beneath the entire try/catch statement.
