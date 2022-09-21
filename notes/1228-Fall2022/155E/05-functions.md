
## 4 - 6PM: Schorr Center

* Meet with dozens of employers, casually
* Pizza


# CSCE 155E - Computer Science I
## Functions
### Fall 2022

Introduction to functions in C

* A *function* is a reusable ***unit*** of code that may take *input(s)* and *may* produce an *output*
* Similar
  $$f(x) = x^2 + 4$$
* Observe:
  * Name? $f$
  * Input? $x$
  * $f(x,y)$, $f(x,y,z)$
  * Output?  $y = f(x)$
* How many outputs can a "function" have?
* Some functions in C: `main()`, `sqrt()`, `printf()`
* Why use functions in C?
  * Functions facilitate *code reuse*: you don't copy-pasta pieces of code (cut and paste), instead, you can put that code into a reusable function and then simply "call" or "invoke" the function
  * Procedural Abstraction
    * How does `sqrt()` work?
    * Who cares?  It just works
    * The details are hidden away (abstracted) into the function and we don't have to to worry about it
    * The details are *encapsulated* inside the function
  * Standard and external libraries have a *lot* of functionality that is well-tested, optimized, correct, etc.
    * Don't reinvent the wheel
  * Feeds into an overall engineering strategy: when faced with a problem what is the first question you ask: Is it already solved?

## Functions in C

* As with variables, functions in C have to be *declared* before you can use them
* To declare a function you define a *prototype*
  * A prototype in C is a function's *signature*
  * The function's name
  * The function's inputs (types of variables it takes)
  * The function's output type (the type of variable it computes and *returns*)
* Observations:
  * The prototype is ended with a semicolon
  * For now: your prototypes go above the `main()` (fix this later)
  * You should always document using doc-style comments every function you write
* Once you have created a prototype, you need to provide a function *definition*: the actual code that the function consists of
* Observations:
  * The names of functions should be (generally) verbs: because functions *do things*
  * Good naming convention: `lowerCamelCasing()`
  * The inputs to a function are called *parameters*
  * When you call a function, the function that calls it is the "calling function" and the function called is the "called function"
  * The function executes the code in its body until it reaches the end at which point it `return`s to the calling function
  * IDE Tip: you can hold down command (mac) or control (windows) and click on a function to jump to its code
  * Any variables declared inside a function only exist *in that function*: they are *local* to that function and are not available outside of it (they die at the end of the function)

## Modularity

* Not all function should be in the same source file: bad organization
* Instead they are separated into different files:
  * The prototype + documentation goes into a *header* file with a `.h` extension
  * The definition/implementation goes into a *source* file with a `.c` extension with the same base name
* Demonstration:
  * Included the header file using `#include "finance.h"` anywhere we  needed to (loan.c and finance.c files)
  * We included other headers as needed (math.h)
  * Compiled the "finance" library using the `-c` flag:
  `gcc -c finance.c` which produce an object file containing the actual machine code of our library
  * Compiled everything together using:
  `gcc loan.c finance.o -lm`
* Pitfalls
  * YOU NEVER NEVER NEVER include a source file: `#include "finance.c"` only include header file
* Advanced solution: if you have many source files and a more complex program, it can get very inconvenient to have to recompile *every single time*
* Most languages have some sort of "build system": a second system that:
  * Manages dependencies
  * Track changes so that only changed files get recompiled
  * Provides multiple ways of compiling for different systems, etc.
* For C: the `make` utility or the modern `cmake` utilty are standard (read more about it on your own)

### How Do Functions Work?

* Programs have a *program stack*: its a LIFO = Last In First Out data structure
* In a stack you can add something to the "top" (pushing) or remove something from the "top" (popping), but not in between; you only interact with a stack at the "top"
* Every time a function is called, a new *stack frame* is created and placed on top of the "call stack"
  * All local variables inside a function as well as parameter variables exist only in their *stack frame*
  * When a function is done executing and control is returned back to the *calling function*, it is a simple matter of popping off the stack frame
  * All variables in the stack frame are "destroyed"
  * Consequence: you cannot make changes to variables in the calling function because variables are *passed by value*
  * Copies of the values of the variables are given to the function!

## Unit Testing

* A *unit* is a piece of code (usually a function) that can be tested
* In general: it is an indivisible piece of code so that you can test it in *isolation* of all other code
* A unit test is an input-output pair that is known to be correct
* We unit test by feeding the input into our unit (function) and comparing the result to the *known correct* output: actual vs the expected
  * If they match: PASSES!
  * If it doesn't: it FAILS!
* Grouping multiple unit test cases together gives you a *test suite*
* If a future bug is reported: we have a new test case!
* A future change to the code may cause unit tests that passed before to now fail: this is a *regression*
* Tests should be automated and repeatable
* The more tests you have the higher certainty you have that your code is correct
* No matter how many test you have you never have a *proof* that your code is correct
* The more test cases you have the better *code coverage* you have
  * We want to test corner cases
  * Edge cases, extremal cases
  * Randomized testing/fuzzing
* Problems:
  * a lack of code coverage
  * *false positives*: when a test case is wrong but the code is correct
  * A *false negative*: when there is a bug in your program but your test suite does not indicate it
* TDD = Test Driven Development
  * Generally: you write your tests before the code

* Demo:
  * *informal* unit testing in C
  * Later (Lab 6, Hack 6): you will use a more formal unit testing framework : cmocka



```text






```