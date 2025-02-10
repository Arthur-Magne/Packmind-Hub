<!-- #title -->
# Avoid Using `continue` Statements in Loops

<!-- #severity -->
*Critical*

<!-- #categories -->
- maintainability
- intentionality - clear

<!-- #description -->
## What is it?
This practice is triggered by the use of the `continue` statement in loops, which abruptly skips to the next iteration and disrupts the natural flow of control.

## Why apply it?
Using `continue` can make your code less readable, harder to test, and more difficult to maintain by obscuring the intended logic.

## How to Fix it?
Replace the `continue` statement with a conditional structure that explicitly handles when code should execute, preserving clear and structured control flow.

<!-- #examples -->

## Example 1:
### Positive
<!-- The positive example uses an if statement to conditionally execute code instead of skipping an iteration with continue. -->
```js
for (let i = 0; i < 10; i++) {
  if (i !== 5) {  /* Compliant */
    alert("i = " + i);
  }
}
```
### Negative
```js
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    continue;  /* Noncompliant */
  }
  alert("i = " + i);
}
```
## Example 2:
### Positive
<!-- The positive example uses an if statement to conditionally execute code instead of skipping an iteration with continue. -->
```js
let i = 0;
while (i < 10) {
  if (i !== 5) {  /* Compliant */
    console.log(i);
  }
  i++;
}
```
### Negative
```js
let i = 0;
while (i < 10) {
  if (i === 5) {
    i++;
    continue;  /* Noncompliant */
  }
  console.log(i);
  i++;
}
```