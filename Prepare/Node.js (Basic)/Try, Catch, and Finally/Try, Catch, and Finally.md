# Try, Catch, and Finally

## Problem
![alt text](image.png)

## Solution
```
'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', inputStdin => {
    inputString += inputStdin;
});

process.stdin.on('end', _ => {
    inputString = inputString.trim().split('\n').map(string => {
        return string.trim();
    });
    
    main();    
});

function readLine() {
    return inputString[currentLine++];
}

/*
 * Complete the reverseString function
 * Use console.log() to print to stdout.
 */
function reverseString(s) {
    try {
        // Try reversing the string
        s = s.split("").reverse().join("");
    } catch (error) {
        // If an exception occurs, log the error message
        console.log(error.message);
    } finally {
        // Print the result (reversed or original string)
        console.log(s);
    }
}


function main() {
    const s = eval(readLine());
    
    reverseString(s);
}
```