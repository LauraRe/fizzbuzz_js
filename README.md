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

## Question 3

### Explain the difference between `===` and `==` in JS.

They both compare for equality but while `===` checks for both value and type identity, `==` will check the value identity after performing (if necessary) type conversion.

```javascript
3 === '3' // false   
3 == '3'  // true
```  

## Question 4

### Explain why we are moving `number % 5 === 0` to the top.

`number % 5 === 0` has to be moved to the top if we want that statement to be evaluated first.   
In fact, the `if` statement returns the value of the first statement that equals to `true`.   
For instance, if the value is divisible by both 5 and 3, the value returned will be the one associated with 5 ('Buzz'). 

## Question 5

### Explain the difference between feature and unit test.

A unit test is used to test small pieces of code (units) in an isolated environment.

A feature test is used to test the functionality of the entire application. It mimics the user behaviour as much as possible.

## Question 6 

### Explain what the following code does:
```javascript
describe('User can input a value and get FizzBuzz results', () => {
    before(async () => {
        await browser.init()
        await browser.visitPage('http://localhost:8080/')
    })

    beforeEach(async () => {
        await browser.page.reload();
    })

    after(async () => {
        await browser.close();
    })
})
```
* Before the tests execution wait for the browser to initialise and visit the server's root path (http://localhost:8080/).   
* Before each test reload the browser's page.  
* Close the browser when the test is finished.

## Question 7

### Explain what expectations in the context of testing are:

Expectations are used to compare an expected output (set in the test) with the actual output (given by your code).   
The test passes if expected output equals actual output, otherwise it fails.  

## Question 8

### Write a line to line explanation of what is happening in the following code:
```javascript
<script src="./js/fizz-buzz.js"></script>
        <script>
            document.addEventListener('DOMContentLoaded', () => {
                let button = document.getElementById('button')
                let displayDiv = document.getElementById('display_answer')
                button.addEventListener('click', () => {
                    let value = document.getElementById('value').value
                    let fizzBuzz = new FizzBuzz
                    let result = fizzBuzz.check(value)
                    displayDiv.innerHTML = result;
                })
            })
        </script>
```
* `src` stands for 'source' and it refers to the JS file that will be executed in the `script` tag when the page is loaded. It is possible to write code inside the `script` tag instead of loading a file.
* The `document.addEventListener` is a browser built-in method that is 'receptive' for a particular event/action. In this case, when the DOM content is loaded, the callback function will:
    * Store the element with id equal to 'button' in a variable called button;
    * Store the element with id equal to 'display_answer' in a variable called displayDiv.
    * When the button is clicked, the callback function will:
        * Store the element with id equal to 'value' in a variable called value;
        * Create a fizzBuzz instance;
        * Store the result of calling the `check` method with `value` in the variable result;
        * Display the result in the div section (id=display_answer) of the HTML page.