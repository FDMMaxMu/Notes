A fragment of code that produces a value is called an expression. Like human sentences, a sentences can have sub-sentences and sub-sentences can have its own sub-sentences.

A statement corresponds to a full sentence in a human language.

### Variable
If you produce new values using old values, you can still not save the internal state.
Variable could help you with that.
Example:

var caught = 5 * 5;
Var is the keywork that could be used to declare the rest of the line is a variable declaration.
After that, the variable could be used in expressions.
"=" could be used to disconnect the variable with its old value and replace it with the new value;

caught = 1 * 1;

If you didn't assign a value to a variable, it will be undefined.
You could also do this:

var a = 1, b = 2;
console.log(a); // it will be 1
console.log(b); // it will be 2

### Keywords and reserved words:
Variables should not use keywords or reserved words like var. Or there will be chaos.

### The Environment
The collection of variables and their values that exist at a given time is called the environment.

### Functions
A function is a piece of program wrapped in a value. Such values can be appliedin order to run the wrapped program. Executing a function is called invoking, calling, or applying it. Values given to functions are called arguments.
Another example: console.log() / alert() -> actually it is retrieve log property out of the console variable.

### Return Values
Functions could produce side effects. Also, functions could produce values.
console.log(Math.max(2, 4)); // return 4
Invoking this function could produce a value of 4.

### Prompt and confirm
Instead of alert. We have other prompts:
confirm returns a boolean value by asking whether or not for one question.
prompt returns a string value by asking an open question.

### Control Flow
We can choose to use conditional execution where we could choose between two different routes.

var theNumber(Number(prompt("Pick up a number")));
if(isNaN(theNumber)){
     alert("Your number is the square root of" + theNumber * theNumber);
} // If your answer is "cheese", you won't have any output

###For loops

for(var number = 0; number < 12; number++){
     console.log(number);
}
There is a special statement called break that has the effect of immediately jumping out of the enclosing loop. continue basically go to the beginning of the next round.
Name convention:
     -variable: fizzNameShit
     -function:FizzNameShit()
