# JS Error Types

* Common Types of JavaScript Errors:

    1. SyntaxError:
        • Occours when code does not conform to JavaScript syntax rules
        • Example:

        ```js
        funtion broken() { // Uncaught SyntaxError: Unexpected identifier
            console.log("I'm broke");
        }
        ```

    2. ReferenceError:
        • Occurs when referencing a variable that does not exist or is not within the current scope
        • Example:

        ```js
        function callPuppy() {
            const puppy = "puppy";
            console.log(pupy); // ReferenceError: pupy is not defined
        }

        callPuppy();
        ```

    3. TypeError:
        • Occurs when an operation is performed on a value of the wrong type or an unchangeable value is modified
        • Example:

        ```js
        let dog;
        dog(); // TypeError: dog is not a function
        ```

* Additional Types of JavaScript Errors:

    • RangeError: When a numberic variable or parameter is outside its valid range
    • InternalError: Errors within the JavaScript engine
    • EvalError: Errors related to the global `eval` function
    • URIError: When `encodeURI()` or `decodeURI()` receive invalid parameters


* How to Handle Errors:

    1. Identify the Error Type:
        • SyntaxError: Check for syntax issues like missing or extra characters
        • ReferenceError: Verify that variables are declared and within scope
        • TypeError: Ensure operations are performed on the correct data types and modify only mutable values

    2. Look Up Errors:
        • Use resources to understand functions and error messages
        • Example:

        ```js
        let x = 123;
        let y = 123;
        x.toExponential(y); // check for `toExponential` usage and error message
        ```

    3. Example of Cross-Language Error Handling:
        • Understand error messages even in unfamiliar languages
        • Example (Python):

        ```py
        arr = [1, 2, 3]
        arr[3]
        # IndexError: list index out of range
        ```

* Summary:

    • Recognise common JavaScript errors (SyntaxError, ReferenceError, TypeError)
    • Use error messages and documentation to diagnose and fix issues
    • Apply these techniques to handle unfamiliar errors in any programming language


# Error Handling

* Overview:
    • JavaScript has built-in errors that are thrown when code violates certain conditions
    • You can create, throw and catch your own errors to handle unexpected conditions gracefully

* Creating JavaScript Errors:
    • Use the `error` constructor to create new error instances
    • Syntax: `new error([message[, fileName[, lineNumber]]])`
    • Example:

    ```js
    const first = Error("I am Error");
    const second = new Error("I, too, am Error");
    console.log(first); // Error: I am Error
    console.log(second); // Error: I, too, am Error
    ```

* Throwing your own Errors:
    • Use the `throw` keyword to throw custom errors and stop program execution
    • Example:

    ```js
    function giveNumber(num) {
        if (typeof num !== "number") {
            throw new Error("Give me a number!");
        }
        return "yay number!";
    }
    console.log(giveMeNumber(1)); // prints "yay number!"
    console.log(giveMeNumber("apple")); // Uncaught Error: Give me a number!
    ```

* Catching Errors with try...catch:
    • Use `try...catch` blocks to handle errors and continue program execution
    • Syntax:

    ```js
    try {
        // Attempt code execution
    } catch (error) {
        // Handle the error
    }
    ```
    • Example:
    ```js
    function safeDivide(a, b) {
        if (b === 0) {
            throw new Error("cannot divide by zero")
        }
        return a / b;
    }

    try {
        console.log(safeDivide(30, 5)); // prints 6
    } catch (error) {
        console.error(error.name + ": " + error.message);
    }
    console.log("hello"); // prints "hello"
    ```

* Catching Known Errors:
    • Use `instanceof` to catch specific error types
    • Example:

    ```js
    function callThatArg(arg) {
        arg(); // causes a TypeError
    }

    try {
        callThatArg(42);
    } catch (error) {
        if (error instanceof TypeError) {
            console.error(`Wrong Type: ${error.message}`) // prints Wrong Type: arg is not a function
        } else {
            console.error(error.message);
        }
    }
    console.log("done") // prints: done
    ```

* Handling Syntax Errors:
    • Syntax errors occur at compile time and cannot be caught using `try...catch`
    • Example:

    ```js
    try {
        if (true { // SyntaxError: Unexpected token '{'
            console.log("SyntaxErrors are the worst!")
        }
    } catch (e) {
        console.log(e);
    }
    ```

* Using the finally Block:
    • The `finally` block runs regardless of whether an error occurs
    • Example:

    ```js
    function trySafeDivide(n) {
        try {
            console.log(safeDivide(30, n));
        } catch (error) {
            console.error(error.name + ": " + error.message);
            return;
        } finally {
            console.log("This will always run");
        }
    }
    ```

* Best Practices:
    • Avoid wrapping all code in `try...catch` blocks as they slow down execution
    • Write defensive code to check for bad values before errors occur
    • Learn to read error messages to identify and fix code issues efficiently

* Summary:
    • Create, throw, and catch errors using `Error` objects and `try..catch` blocks
    • Use specific error handling techniques for better code management and debugging
