# JavaScript: the hard parts



As soon as we start running our code, we create a *global execution context*:
- Parsing and executing the code
- Live memory of variables with data

With a single thread.

When a function is executed, a new *local execution context* is created:
- a thread: for executing the code in the function
- a new local memory: for everything inside that function (aka. available environment)

After the execution of the function that local execution context goes away.

## Call Stack
Data structure to track which execution context is currently running.
Whatever is on top, that is the current context.

# Functional programming

- Pure functions has no side effects (besides the returned value)
- Higher order functions

Functions have two phases: definition/declaration & execution

csbin.io/callbacks

Functions are first class citizen.
- can be assigned to variables and properties of other objects
- passed as arguments into functions
- returned as values from functions

The only difference between functions and objects, is functions can be invoked

*High order function* is a function that takes in a function or passes out a function


# Closure
When a function gets called, a live store of data (local memory/variable environment) 
is created for that function's execution context.

When the function finishes executing, its local memory is deleted (except the returned value).

When the function returns a function

csbin.io/closures

## Lexical scope reference
When a function is defined, it gets a [[scope]] property that references the *Local Memory/Variable Environment* in which it has been defined.

The variables that are available, are determined from where the function was defined, not from where it was called.

The **static/lexical scope** (the available live data when the function was *defined*) is what determines the available variables and prioritization at function execution, not where the function was called.

The persistent lexical scope reference = closed over variable environment = "closure"

# Asynchronous JavaScript
JavaScript is a single threaded and has a synchronous execution model.









