# Asynchronous Javascript Part 1

## Synchronous Programming
```
const name = "Miriam";
const greeting = `Hello, my name is ${name}!`;
console.log(greeting);
// "Hello, my name is Miriam!"
```
##### Synchronous because it executes top to bottom one line at a time.
### Issue
- If one block of code takes a long time to execute then all others are forced to wait. For example, if you have a text box as a user input mixed with the generate prime numbers function in 'synchronous.js' then the text box will not work until the generation of prime numbers is complete

## Asynchronous programming
Just like event listeners, asynchronous programming refers to the use of callback type sequences which react to certain events without interrupting the main thread. Essentially functions are able to be run simultaneously without having to wait on one another, unless dependent on each other.

### Example (callbacks)
- Notice the sequence...we got from doOperation to doStep1 and put its result into doStep2 and put its result into doStep3. 
- In the end we get: 6 (0 + 1 (step 1) = 1 + 2 (step 2) = 3 + 3 (step 3)).
```
function doStep1(init, callback) {
const result = init + 1;
callback(result);
}

function doStep2(init, callback) {
const result = init + 2;
callback(result);
}

function doStep3(init, callback) {
const result = init + 3;
callback(result);
}

function doOperation() {
doStep1(0, (result1) => {
    doStep2(result1, (result2) => {
    doStep3(result2, (result3) => {
        console.log(`result: ${result3}`);
    });
    });
});
}

doOperation();
```

