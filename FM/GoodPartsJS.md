
The Good Parts of JavaScript and the Web
https://frontendmasters.com/courses/good-parts-javascript-web

# Program Style
Automated tests do test for imperfection, there is no perfect program.

Confusion must be avoided. Because they produce bugs.
Write in a way that clearly communicates your intention.

Premature optimization is the root of all evil.

Good use of style can help reduce the occurrence of errors
programs must communicate clearly to people as well to computers


## Curly braces
Always putting curly braces at right.

The next code returns undefined
```
return 
{
    ok: false
}
```

Always put curly braces in every `if`, every `for`, `while`, etc.
```
if (a) b(); c();
```

In previous example, `c()` is always executed, not as an `else`.


## Semicolon
JS does an automatic semicolon insertion. But never miss semicolons


## IFFE
iffe should have the parentesis wraping the function call:
```
(function () {
  ....
}())
```

## Variables declaration
Big design error in JS: if you do no explicitly declare a variable in a function, JS assumes that you intended for it to be a global variable.

```
var a = b = 0;
```

In reality this turns to be
```
b = 0;
var a = 0;
```


# And then there was JavaScript

## Objects
An object in JS is a dynamic collection of properties. Every property has a key string that is unique within that object.

## Number
We are not guaranteed to get the right sum with binary floating point. `0.1 + 0.2  === 0.3` turns to be false

## Arrays
There are not out of bound errors in arrays, because they are in reality hash tables.

`length` in Arrays is one value larger than the highest integer subscript, which is not the same as number of elements in the array

Associative array in JS is the object

## RegExp
for regular expressions check www.jex.im/regulex

## Coercion
All values are boolish, they are true or false. They all return `true` except: - false 
- null 
- undefined
- empty string ""
- 0
- NaN

JS is **loosely typed**, any type can be stored in a variable or passed as a parameter to any function. BUT the language is not untyped!!

The benefit of JS vs typed languages is although the compiler prevents errors with types, the type of errors that a type checker can find, you find instantly anyway if you are doing the most trivial level of testing, but you safe much time.

The `===` operator compares object references, not values. So it is only true if both operands are the same object

## Sum operator
The `+` operator can be a sum or a concatenation. Every `+` expression that involves a string will result in a string: `42 + "0"` will produce string "420"

At the beginning of anything, the + operator returns a Number

The `-` operator can only be used in numeric operations.

## for loops
for in iterates through all of the members of an object, including the inheritated prototype functions

Both `for...in` and `for...of` statements iterate over something. The `for...in` statement iterates over the enumerable properties of an object. The `for...of` statement iterates over data that iterable object defines to be iterated over.

```
Object.prototype.objCustom = function() {}; 
Array.prototype.arrCustom = function() {};

let iterable = [3, 5, 7];
iterable.foo = 'hello';

for (let i in iterable) {
  console.log(i); // logs 0, 1, 2, "foo", "arrCustom", "objCustom"
}

for (let i in iterable) {
  if (iterable.hasOwnProperty(i)) {
    console.log(i); // logs 0, 1, 2, "foo"
  }
}

for (let i of iterable) {
  console.log(i); // logs 3, 5, 7
}
```


# Function
The functions run and add things to the environment as they are compiled.

## Function expression 
A function expression produces an instance of a function object.

Functions objects are first class, they may:
- be passed as arguments
- returned from a function
- assigned to a variable
- stored in an object or array 

Function objects inherit from Function.prototype 

There is no block scope, but function scope. Except `let` and `const`.

## Function statement 
The function statement is a short-hand for a `var` statement with a function value: `function foo() {}`.

Expression vs statement: if the first token in a statement is `function`, then it is a function statement. Otherwise is a function expression.

## arguments 
arguments contains all of the arguments from the invocation. It is an array-like object, it contains the `length` property but not all the other nice methods of arrays.

It has a weird interaction with parameters. If you change arguments value, the first parameter also changes. This makes one of the most hated features for people who make JS engines.

## this
This parameter conaines a reference to the object of invocation.
It allows a single function object to service many objects.
And `this` is key to protoypal inheritance. 

## Invocation
Four ways to call a function:
- function form: `functionObject(arguments)`
- method form: `thisObject.methodName(arguments)` 
- constructor form: `new FunctionObject(arguments)`
- apply form: `functionObject.apply(thisObject, [arguments])` or `functionObject.call(thisObject, arguments...)`

In Function form, `this` is set to the global object (fixed in "strict mode").

In mehtod form `this` is bound to `thisObject`. This happens at the moment of invocation.

In constructor form, a new object is created and assigned to `this`. If there is no return value, then `this` will be returned.

In apply form, the function's `apply` or `call` method allows for calling the function, explicitly speficying `thisObject`.

javascript.crockford.com/little.html

# Closure
Lexical scoping, or static scoping
It is a consecuence of functions can nest and functions are values.

Context of an inner function includes the scope of the outer function, an inner function enjoys that context even after the parent functions have returned.

- **Lisp[1958]** dynamic scope
- **Algol 60 [1960]** functions are not values
- **C [1972]** functions cannot be nested

The way to implement it was actually trivial: Don't allocate all of the activation records on a Stack, allocate them on a heap. Get a good garbage collector.

JavaScript was the first main language to bring Closure, then Python, Ruby, C# and finally Java adopted it.

# new
If `new` would have been implemented as a method it would do:
```
Function.prototype.new = function new() {
    var that = Object.create(this.prototype),
        result = this.apply(that, arguments);

    var isObject = (typeof result === 'object' && result != null);

    return (isObject) ? result : that;
}
```


# Browser
url -> FETCH -> cache -> PARSE -> tree -> FLOW -> display -> PAINT -> pixels

In a scripted browser they invented the event loop:
flow -> paint -> event -> script -> flow (again)

Script will not be stoped.  

# DOM

## DOM manipulation
This will create a DOM node: `document.createElement(tagName)`

but it will not be visible until it is attached to the DOM:
- `node.appendChild(new)`
- `node.insertBefore(new, sibling)`
- `node.replaceChild(new, old)`

Removing child from the DOM:
- `node.removeChild()`

Parsing HTML is normally faster than manipulating the DOM. Styling, touching a node, repaint, etc. have a big cost

## Event handlers
Adding an event to the DOM: `node.addEventListener(type, f, false)`

# ES5
## Function.prototype.bind
If bind should be implemented in JS, it would look like this:
```
Function.prototype.bind = function(object) {
    var slice = Array.prototype.slice,
        func = this,
        args = slice.call(arguments, 1);

    return function() {
        return func.apply(
            object,
            args.concat(slice.call(arguments, 0))
        );
    };
}
```

## Object.keys
```
Object.keys = function (object) {
    var name, result = [];
    for (name in object) {
        if(Object.prototype.hasOwnProperty.call(object, name)) {
            result.push(name);
        }
    }
    return result;
};
```

## Object.create
Is the primitive that makes an object that inherits from another object.
This gives us a direct way of doing prototype inheritance.
```
Object.create = function (object, properties) {
    var result;
    function F() {}
    F.prototype = object;
    result = new F();
    if (properties !== undefined) {
        Object.defineOwnProperties(object, properties);
    }
    return result;
}
```

## Attributes of properties
Meta Object API `Object.defineProperty(object, key, descriptor)`

Where the descriptor is:
- **value:** any JS value
- **writeable:** boolean
- **enumerable:** boolean
- **configurable:** boolean
- **get:** function() { ... return value;}
- **set:** function(value) { ... }


- `Object.preventExtensions(object)`
- `Object.seal(object)`
- `Object.freeze(object)`













