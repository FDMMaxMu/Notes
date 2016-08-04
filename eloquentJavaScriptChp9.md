# Regular Expression:

Regular expressions are a way to describe patterns in string data.

# Creating a regular expression:

Regular expression is an object in JavaScript
You can create one in two ways:
```JavaScript
var re1 = new RegExp("abc");
var re2 = /abc/;
```
When we do in the second way, we need to be cautious that we need to add backslash before the forwardslash that will appear in the pattern. Also, some characters like ? and + could have special meaning. If we want to use them as their mearning, we need to add a backslash before them. like var re2 = /\+Jesus/(match "+Jesus").

# Testing for matches:
```JavaScript
console.log(/abc/.text("abcde"));
/// -> true
console.log(/abc/.text("abxde"));
/// -> false
```
A regular expression consisting of only nonspecial characters simply represents that sequence of characters.

# Matching a set of characters:
In a regular expression, putting a set of characters between square brackets makes that part of the expression match any of the characters between the brackets.
```JavaScript
console.log(/[0-9]/.text("in 1992"));
// -> true
```
Shortcuts:
\d     digit
\w    alphanumeric character
\s     whitespace character
\D    a character that is not a digit
\W   a nonalphanumeric character
\S    a nonwhitespace character
.       any character except for a newline

To invert a set of characters, you can put (^) after the opening bracket.
```JavaScript
var notBinary = /[^01]/;
console.log(notBinary.("100101001010"));
// -> true
console.log(notBinary.("012001010101"));
// -> false
```

# Repeating parts of a pattern
If you want to match things repeated more than once, you should use "+", if you want to match 0 to more times of a character, you can use "*", "?" match zero or one time. If you want to match accurate number of times, user curly braces for example, {4}. Range: {2,4}. More than 5 times: {5, }
```JavaScript
console.log(/'\d+'/.test("'123'"));
// -> true
console.log(/'\d*'/.test("'123'"));
// -> true
console.log(/'\d*'/.text("'abxc'"));
// -> true
```

# Grouping subexpressions:
To use an operator on a group of characters, you can use parentheses.
```JavaScript
var cartoonCrying = /boo+(hoo+)+/i;
console.log(cartoonCrying.test("Boohoooohoohooo"));
// -> true
```

# Matches and groups:
If you want to get something back from regex matching, you can use "exec" of the regex object.
```JavaScript
var match = /\d+/.exec("one two 100");
console.log(match);
// -> ["100"]
console.log(match.index);
// -> 8
```
String values have a "match()" method.
```JavaScript
console.log("one two 100".match(/\d+/));
// -> ["100"]
```
When a group does not end up being matched at all, its position in the output array will hold undefined. Similarly, when a group is matched multiple times, only the last match ends up in the array:
```JavaScript
console.log(/bad(ly)?/.exec("bad"));
// -> ["bad", undefined]
console.log(/(\d)+/.exec("123"));
// -> ["123", "3"]
```

# The date type
JavaScript did a really strange thing: for month, it starts from 0. For days, it starts from 1.

```JavaScript
var today = new Date();
// -> Wed Aug 03 2016 17:14:30 GMT-0400 (Eastern Daylight Time)
```
