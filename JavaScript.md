# JavaScript

# Block Bindings

## Block-level declarations

ECMAScript 6 introduces block-level scoping. **Block scopes**, also called **lexical scopes**, are created in:
- inside a function
- insidea a {} block

### Hoisting
Variable declarations using var are treated at the top of the function (or in the global scope). This is called **hoisting**. The variable values is accessible and has a value of _undefined_.

### let declarations
Behaves more similarly to other C-based languages:
- limit variable's scope to only the current code block
- they are not hoisted
- they cannot be redeclared twice. It throws an error

```
if(condition) {
    let count = 0;
    ...
    count++; // ok
}
count++; // throws an error
```

### const declarations
Bindings declared using _const_ are considered as constants:
- values cannot be changed once set
- every const binding must be initialized on declaration

```
const age = 38;
const maxValue; // throws a missing initialization syntax error
```

Be aware, _const_ declaration prevents modification of the binding, not the of the value. In other words, they don't prevent modification of the content of objects.

### Temporal Dead Zone
_let_ and _const_ variables are not hoisted, so they are not accessible before their declaration. The JavaScript community called this _Temporal Dead Zone_



