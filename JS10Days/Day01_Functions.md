# Day 1: Functions
## Objective

Today, we're discussing JavaScript functions. Check out the attached tutorial for more details.


## Task

Implement a function named factorial that has one parameter: an integer, **n**. It must return the value of **n!** (i.e., **n** factorial).

## Input Format

Locked stub code in the editor reads a single integer, **n**, from stdin and passes it to a function named factorial.


## Constraints
- **1 <= n <= 10**


## Output Format

The function must return the value of  **n!**.


## Sample Input 0

```
4
```


##Sample Output 0

```
24
```


## Explanation

We return the value of **4! = 4 X 3 X 2 X 1 = 24**.

<br/>
<br/>

---

## Solutions
### Solution 1

```javascript

const factorial = (n) => (n - 1) > 0 ? n * factorial(n - 1) : 1;

```
### Solution 2

```javascript

let memoization = [0, 1];

const factorial = (n) => {
    (typeof memoization[n] !== 'number') && (
        memoization[n] = (n - 1) > 0 ? n * factorial(n - 1) : 1 
    );

    return memoization[n];
}

```
### Solution 3
```javascript

function factorial(n){
    if(n === 0){
        return 1;
    } else{
        return n * factorial(n-1);
    }
}

//if we give n = 5
//factorial(5) = 5*factorial(4)

//factorial(4) ->  n = 4 verilir:
//factorial(4) = 4* factorial(3)

//for factorial(3) -> n = 3
//factorial(3) = 3* factorial(2)

//for factorial(2) -> n = 2
//factorial(2) = 2* factorial(1)

//for factorial(1) -> n = 1 and
//factorial(1) = 1* factorial(0)
//factorial(0) = 1
//
//factorial(5) =5*4*3*2*1

```
---