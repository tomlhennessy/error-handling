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



# Recap of `try...catch`

* What is Error Handling?
    • A way to manage errors or exceptions that might occur while your program is running
    • Instead of letting the program crash, you can handle the errors gracefully and decide what to do next

* The `try...catch` Structure
    1. try block: You write the code that might throw an error inside the `try` block
    2. catch block: If an error occurs in the `try` block, the control jumps to the `catch` block where you can handle the error

* Basic Syntax

    ```js
    try {
        // code that might throw an error
        let result = riskyOperation();
        console.log(result);
    } catch (error) {
        // code to handle the error
        console.error("An error occured:", error.message);
    }
    ```

* Explanation
    • try block: the code inside this block is executed first. If no error occurs, the `catch` block is skipped
    • catch block: If an error occurs in the `try` block, the code inside the `catch` block is executed. The `catch` block receives an `error` object that contains information about the error

* Real-world Example
    • Imagine trying to read data from a file
    • This operation might fail if the file doesn't exist
    • Using `try...catch`, you can handle this gracefully

    ```js
    try {
        let data = fs.readFileSync('file.txt', 'utf8');
        console.log(data);
    } catch (error) {
        console.error("Failed to read the file:", error.message);
    }
    ```
* In this example:
    • If the file `file.txt` exists and is read successfully, its content is printed
    • If the file doesn't exist, an error is thrown, and the `catch` block prints an error message


* Why Use `try...catch`?
    • Prevents crashes: Without error handling, an error would stop your program
    • Graceful degradation: You can show user-friendly messages or take corrective actions
    • Debugging: The `catch` block can help you log detailed error information, making it easier to debug

* Key Points
    • Always use `try...catch` when dealing with potentially error-prone code (like network requests, file operations, or user inputs)
    • Keep `try` blocks small and focused on the code that might fail
    • Handle specific errors: You can have multiple `catch` blocks for different types of errors

* Summary
`try...catch` is a fundamental concept in error handling that allows you to write code that can deal with unexpected situations gracefully, preventing crashes and improving user experience. By wrapping risky operations in a `try` block and handling erors in a `catch` block, you can control the flow of your program even when things go wrong.
