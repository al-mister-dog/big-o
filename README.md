# Big O Notation
## Introduction
Big O notation is a way of describing the time complexity of an algorithm. It is used to describe how the execution time of an algorithm increases as the size of the input increases.

## Examples
Here are some examples of common time complexities and the algorithms that have those time complexities:

### O(1) - Constant Time
An algorithm with O(1) time complexity has a constant execution time, regardless of the size of the input. Here’s an example:
```javascript
function getFirstElement(arr) {
  return arr[0];
}
```
This function returns the first element of an array. It has a constant execution time because it only performs one operation, regardless of the size of the input array.

### O(n) - Linear Time
An algorithm with O(n) time complexity has an execution time that increases linearly with the size of the input. Here’s an example:
```javascript
function sumArray(arr) {
  let sum = 0;

  for (let i = 0; i < arr.length; i++) {
    sum += arr[i];
  }

  return sum;
}
```
This function sums all the elements in an array. It has a linear execution time because it performs one operation for each element in the input array.

### O(n log n) - Log-Linear Time
An algorithm with O(n log n) time complexity has an execution time that increases logarithmically with the size of the input. Here’s an example:
```javascript
function mergeSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }

  const mid = Math.floor(arr.length / 2);
  const left = arr.slice(0, mid);
  const right = arr.slice(mid);

  return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
  const result = [];

  while (left.length && right.length) {
    if (left[0] < right[0]) {
      result.push(left.shift());
    } else {
      result.push(right.shift());
    }
  }

  return [...result, ...left, ...right];
}
```
This function sorts an array using the merge sort algorithm. It has a log-linear execution time because it divides the input array into smaller subarrays and then merges them back together. The number of operations required to merge two subarrays is proportional to their combined length, which is why this algorithm has a log-linear execution time.

### O(n^2) - Quadratic Time
An algorithm with O(n^2) time complexity has an execution time that increases quadratically with the size of the input. Here’s an example:
```javascript
function bubbleSort(arr) {
  const n = arr.length;

  for (let i = 0; i < n; i++) {
    for (let j = 0; j < n - i - 1; j++) {
      if (arr[j] > arr[j + 1]) {
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
      }
    }
  }

  return arr;
}
```
This function sorts an array using the bubble sort algorithm. It has a quadratic execution time because it compares each element in the input array to every other element in the array.

### O(n!) - Factorial Time
An algorithm with O(n!) time complexity has an execution time that increases factorially with the size of the input. Here’s an example:
```javascript
function permutation(str) {
  if (str.length === 1) {
    return [str];
  }

  const result = [];

  for (let i = 0; i < str.length; i++) {
    const char = str[i];
    const sub_permutations = permutation(str.slice(0, i) + str.slice(i + 1));

    for (let j = 0; j < sub_permutations.length; j++) {
      result.push(char + sub_permutations[j]);
    }
  }

  return result;
}
```
This function generates all possible permutations of a given string. It has a factorial execution time because there are n! possible permutations of a string of length n.