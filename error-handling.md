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
