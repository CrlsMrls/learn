the value of array at **index** 'x' is ... `array[x]` also array-sub-x

the expression has been evaluated into ... `= x + array[x]`

the declaration of the function (the creation of a function):
```
function copyArray(array) {
    ...
}
...
```

the body of the function:

the function definition
```
function copyArray(array) {
    ...
}
```

declaration of labels (creation of a variable): `array = [1,2,3];`

executing/invoking a function: `copyArra(array);`

When a function is invoked we create a new execution context: `copyArra(array);`


Our parameter array takes the argument 1,2,3
```
const array = [1,2,3];
copyArray(array);
```

DRY principle: Don't Repeat Yourself

we parametrized or generalized our function


