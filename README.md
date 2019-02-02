## Question 1 

### Explain the following lines of code:
```javascript
let fizzBuzz = fs.readFileSync('./src/js/fizz-buzz.js');
eval( fizzBuzz + `\nexports.FizzBuzz = FizzBuzz;`)
```
'fs' stands for 'file system', methods and data structures that the OS uses to keep track of files on disk or partition.  
'readFileSync' is a Node file descriptor method. It returns the content of the specified path.  
'eval' is a js method that executes the code contained in fizz-buzz.js and exports it.

## Question 2

### Why are we placing `let fizzBuzz = new FizzBuzz` outside the `it` block?

So that we can use the newly created fizzBuzz instance for all the it statements inside the describe block.