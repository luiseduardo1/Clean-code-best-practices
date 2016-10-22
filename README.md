# Clean Code Principles
Clean code principles taken mostly from book [Clean Code: A Handbook of Agile Software Craftsmanship by Robert C. Martin](http://www.amazon.co.uk/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882). These are just my notes that i want to keep in mind.

# Main Principles:
- **Meaningful Names**
   - Pick one word per concept
    - Use solution domain Names
    - Use problem Domain Names
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
- **Formatting**
- **Objects and Data Structures**
- **Error Handling**
- **TDD**
    - Must respect three laws
        - You may not write production code until you have a written a failing unit test
        - You may not write more of a unit test than is sufficient to fail, and not compilling is failing
        - You may not write more production code than is sufficient to pass the currently failing test

