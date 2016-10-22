# Clean Code Principles
Clean code principles taken mostly from book [Clean Code: A Handbook of Agile Software Craftsmanship by Robert C. Martin](http://www.amazon.co.uk/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882). These are just my notes that i want to keep in mind.

## Main Principles:
- **Meaningful Names**
    - Should use one word per concept
    - Should use solution Domain Names
    - Should use problem Domain Names

- **Functions**
    - Must be small
    - Should do only one thing
        - A way to know a function is doing more than one thing is if you can extract another function from it with a name that is not merely a restatement o its implementation
        - The statements within our function are all at the same level of abstraction 
        - Error handling is one thing, thus a function that does error handling shouldn't do anything else
            - Tip: If there is a "try" in a function it should be the first word in the function and there shoudln't be anything after the catch/finally blockls
    - Should have one level or two level of abstractions(indentations) 
    - Ideally should have zero argument, could have one or at most two
    - Should have no side effect
    - Shouldn't receive a boolean (flag arguments) as argument
    - Shouldn't abuse the use of switch statements
        - Switch statements can be tolerate if they appear only once, are used to create polymorphic objects, and are hidden behind an inheritance
    - Should respect Command Query Separation
        - Functions should either do something or answer something, but not boith. The function should change the state of an object, or it should return some information about the object, if it does both it leads to confusion
        - Bad:  ```
                   public boolean set(String attribute, String value);
                   ```
        - Good: ```
                  if (attributeExists("username")) {
                  setAttribute("username", "unclebob");
                  }
                  ...
                       ``` 
    - Return exceptions instead of error codes
    - Should extract try/catch block in a function that does only that

- **Comments**
    - The code should be understable without the use of comments
    - Sometimes comments could be necessary
        - Examples: legal comments, to explain a complex regex, to explain a particular intent, to translate the meaning of some obscure argument or return value into something that's readable, sometimes could be reasonable to keep a TODO comment
    - Should never make you look in another module to understand its content
    - Shouldn't be a noise comment (restate the obvious and provide no new informations)
    - Shouldn't keep code commented

- **Objects and Data Structures**
    - Should respect the difference (and opposition) between objects and data structures
        - Objects hide their data behind abstractions and expose function that operate on that data
        - Data structure expose their data and have no meaningful functions (it's easy to add to functions because data structure don't have particular behaviour)
        - This expose the fundamental dichotomy between objects and data structures
            - Procedural code (code using data structures) makes it easy to addnew functions without changing the existing data structures. OO code, makes it easy to add new classes without changing existing functions
            - Procedural code makes it hard to add new data structures because all the functions must change. OO code makes it hard to add new functions because all the classes must change
    - Should respect the Law of Demeter
        - An object should not expose its internal structure through accessors because to do so is to expose, rather than to hide, its internal structure
        - The law says that a method *f* of a class *C* should only call the methods of these:
            - *C*
            - An object created by *f*
            - An object passed as an argument to *f*
            - An object held in an instance variable of *C*
        - The law allows to avoid Train Wrecks

- **Error Handling**
- **TDD**
    - Must respect three laws:
        - You may not write production code until you have a written a failing unit test
        - You may not write more of a unit test than is sufficient to fail, and not compilling is failing
        - You may not write more production code than is sufficient to pass the currently failing test

