## Day 3: Arrays
## Objective

In this challenge, we learn about Arrays. Check out the attached tutorial for more details.


## Task

Complete the getSecondLargest function in the editor below. It has one parameter: an array, **nums**, of **n** numbers. The function must find and return the second largest number in **nums**.

 
## Input Format

Locked stub code in the editor reads the following input from stdin and passes it to the function: <br/>
The first line contains an integer, **n**, denoting the size of the **nums** array. <br/>
The second line contains **n** space-separated numbers describing the elements in **nums**.

 
## Constraints
- **1 <= n <= 10**
- **0 <= nums <= 100**, where **nums** is the number at index **i**.
- The numbers in  are not distinct.


## Output Format

Return the value of the second largest number in the **nums** array.


## Sample Input 0

```
5
2 3 6 6 5
```


##Sample Output 0

```
5
```


## Explanation

Given the array **nums = [2,3,6,6,5]**, we see that the largest value in the array is **6** and the second largest value is **5**. Thus, we return **5** as our answer.

<br/>
<br/>

---

## Solution 1

```javascript
function getSecondLargest(nums) {
    // Complete the function
    const max = Math.max(...nums);

    nums = nums.filter(num => num !== max);

    return Math.max(...nums);
}


```

## Solution 2

```javascript
function getSecondLargest(nums) {
    // Complete the function
    let results = nums.sort((a, b) => a - b)
        .filter((el, index, array) => index === array.indexOf(el));

    return results[results.length - 2];
}

```

## Solution 3

```javascript
function getSecondLargest(nums) {
   
    const result = nums.reduce((target, num) => {
        num > target[1] && (
            num > target[0] ? (
                target[1] = target[0],
                target[0] = num
            ) : !(num === target[0]) && (target[1] = num)            
        );

        return target;
    }, [0, 0]);

    return result[1];
}

```
## Solution 4

```javascript

function getSecondLargest(nums) {
    let max = nums[0];
    let secondMax = nums[0];
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] > max) {
            secondMax = max;
            max = nums[i];
        }
        if (nums[i] > secondMax && nums[i] < max) {
            secondMax = nums[i];
        }
    }
    return secondMax;
}

/*num = [2, 3, 6, 6, 5];
nums[0] = 2;
nums[1] = 3;
nums[2] = 6;
nums[3] = 6;
nums[4] = 5;

i=0
i=0; 0<5; 0++  -> inew=1
if nums[0] > max -> 2>2 -> false
if nums[0] > secondMax && nums[0] < max -> 2>2 && 2<2 -> false

i=1
i=1; 1<5; 1++  -> inew=2
if nums[1] > max -> 3>2 -> true
secondMax = max -> secondMax = 2
max = nums[1] -> max = 3

i=2
i=2; 2<5; 2++  -> inew=3
if nums[2] > max -> 6>3 -> true
secondMax = max -> secondMax = 3
max = nums[2] -> max = 6

i=3
i=3; 3<5; 3++  -> inew=4
if nums[3] > max -> 6>6 -> false
if nums[3] > secondMax && nums[3] < max -> 6>3 && 6<6 -> false

i=4
i=4; 4<5; 4++  -> inew=5
if nums[4] > max -> 5>6 -> false
if nums[4] > secondMax && nums[4] < max -> 5>3 && 5<6 -> true
secondMax = nums[4] -> secondMax = 5

i=5
i=5; 5<5; 5++  -> inew=6
if nums[5] > max ->  -> false
if nums[5] > secondMax && nums[5] < max ->  -> false

*/

```
---

