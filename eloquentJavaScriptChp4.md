Data type specifically for storing sequences of values --> array
var listOfNumbers = [2,3,5,7,11];
console.log(listOfNumbers[1]);
// -> 3
console.log(listOfNumbers[1 - 1]);
// -> 2

The first index of an array is zero, not one.
### Properties:
These are expressions that access a property of some value: myString.length or Math.max

When using a dot, the part after the dot must be a valid variable name, and it directly names the property. When using square brackets, the expression between the brackets is evaluated to get the property name. Whereas value.x fetches the property of value named “x”, value[x] tries to evaluate the expression x and uses the result as the property name.

### Methods:

var doh = "Doh";
console.log(typeof doh.toUpperCase); // function
console.log(doh.toUpperCase()); // "DOH"

var mack = [];
mack.push("Mack");
mack.push("the knife");
console.log(mack); // ["Mack", "the", "knife"];
console.log(mack.join(" ")); // Mack the knife
console.log(mack.pop()); // knife
console.log(mack); // ["Mack", "the"]

### Objects:
Values of the type object are arbitrary collections of properties, and we can add or remove these properties as we please.

Reading a property that doesn’t exist will produce the value undefined

The delete operator is a unary operator that, when applied to a property access expression, will remove the named property from the object.

The binary in operator, when applied to a string and an object, returns a Boolean value that indicates whether that object has that property. The difference between setting a property to undefined and actually deleting it is that, in the first case, the object still has the property (it just doesn’t have a very interesting value), whereas in the second case the property is no longer present and in will return false.

### Mutability:

We’ve seen that object values can be modified. The types of values discussed in earlier chapters, such as numbers, strings, and Booleans, are all immutable—it is impossible to change an existing value of those types. You can combine them and derive new values from them, but when you take a specific string value, that value will always remain the same.

With objects, on the other hand, the content of a value can be modified by changing its properties.

With objects, there is a difference between having two references to the same object and having two different objects that contain the same properties.
var object1 = {value: 10};
var object2 = object1;
var object3 = {value: 10};

console.log(object1 == object2);
// → true
console.log(object1 == object3);
// → false

object1.value = 15;
console.log(object2.value);
// → 15
console.log(object3.value);
// → 10

JavaScript’s == operator, when comparing objects, will return true only if both objects are precisely the same value. Comparing different objects will return false, even if they have identical contents.

### Further Arrayology:

unshift()
shift()
add or remove from the beginning of the array.
var todoList = [];
function rememberTo(task) {
  todoList.push(task);
}
function whatIsNext() {
  return todoList.shift();
}
function urgentlyRememberTo(task) {
  todoList.unshift(task);
}

The previous program manages lists of tasks. You add tasks to the end of the list by calling rememberTo("eat"), and when you’re ready to do something, you call whatIsNext() to get (and remove) the front item from the list. TheurgentlyRememberTo function also adds a task but adds it to the front instead of the back of the list.

The indexOf method has a sibling called lastIndexOf, which starts searching for the given element at the end of the array instead of the front.

Another fundamental method is slice, which takes a start index and an end index and returns an array that has only the elements between those indices. The start index is inclusive, the end index exclusive.

### Strings and their properties:
Values of type string, number, and Boolean are not objects. The values are immutable and cannot be changed. These primitive values only have built-in properties and functions. Users could not stick new properties and functions to them.
indexOf()
trim() -> remove whitespace

### The arguments object
Whenever a function is called, a special variable named arguments is added to the environment in which the function body runs. This variable refers to an object that holds all of the arguments passed to the function. Remember that in JavaScript you are allowed to pass more (or fewer) arguments to a function than the number of parameters the function itself declares.

This arguments() object has a length property but it is actually not an array. (no slice() or indexOf() method.)
function argumentCounter() {
  console.log("You gave me", arguments.length, "arguments.");
}
argumentCounter("Straw man", "Tautology", "Ad hominem");
// → You gave me 3 arguments.

// Real world situation:
function addEntry(squirrel) {
  var entry = {events: [], squirrel: squirrel};
  for (var i = 1; i < arguments.length; i++)
    entry.events.push(arguments[i]);
  journal.push(entry);
}
addEntry(true, "work", "touched tree", "pizza",
        "running", "television");
