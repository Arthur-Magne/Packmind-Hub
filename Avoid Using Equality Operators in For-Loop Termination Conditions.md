<!-- #title -->
# Avoid Using Equality Operators in For-Loop Termination Conditions

<!-- #severity -->
*Critical*

<!-- #categories -->
- correctness
- maintainability

<!-- #description -->
## What is it?
This practice discourages the use of equality (==) operators as loop termination conditions, which may cause loops to behave unexpectedly or not execute at all.

## Why apply it?
Using an equality check instead of a relational operator can lead to off‐by‐one errors or infinite loops if the condition is never met as intended.

## How to Fix it?
Use relational operators (such as < or <=) to clearly define the loop’s boundaries and ensure predictable execution.

<!-- #examples -->

## Example 1: 
### Positive
<!-- This loop correctly iterates over an array using a less-than operator. -->
```java
for (int i = 0; i < array.length; i++) {
    // Process array[i]
}
```
### Negative
```java
for (int i = 0; i == array.length; i++) {
    // This loop will not execute as intended.
}
```
