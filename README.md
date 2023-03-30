# Big O Notation
## Introduction
Big O notation is a way of describing the time complexity of an algorithm. It is used to describe how the execution time of an algorithm increases as the size of the input increases.

## Functions
**Constant function**: A function that always returns the same value, regardless of the input.

_f(x) = 5. No matter what value of x you plug in, the output will always be 5._

**Linear function**: A function that has a constant rate of change. In other words, the output changes by a fixed amount for every unit increase in the input. 

_f(x) = 2x + 1. If you plug in x = 0, the output will be 1. If you plug in x = 1, the output will be 3. If you plug in x = 2, the output will be 5. And so on._

**Logarithmic function**: A function that has a logarithm in it.

_f(x) = log(x). If you plug in x = 1, the output will be 0. If you plug in x = 10, the output will be approximately 1. If you plug in x = 100, the output will be approximately 2. And so on._

**Log-linear function**: A function that is the product of a logarithmic and a linear function.

_f(x) = x log(x). If you plug in x = 1, the output will be 0. If you plug in x = 10, the output will be approximately 23. If you plug in x = 100, the output will be approximately 460. And so on._

**Quadratic function**: A function that has a squared term in it.

_f(x) = x^2 + 2x + 1. If you plug in x = -1, the output will be 0. If you plug in x = 0, the output will be 1. If you plug in x = 1, the output will be 4. And so on._

**Factorial function**: A function that multiplies all positive integers up to a given number.

_For example, 5! (read “5 factorial”) = 5 x 4 x 3 x 2 x 1 = 120._

## Examples
Here are some examples of common time complexities and the algorithms that have those time complexities:

### O(1) - Constant Time
An algorithm with O(1) time complexity has a constant execution time, regardless of the size of the input. Here’s an example:
```javascript
//javascript
function getFirstElement(arr) {
  return arr[0];
}
```
```ruby
#ruby
def get_first_element(arr)
  return arr[0]
end
```
This function returns the first element of an array. It has a constant execution time because it only performs one operation, regardless of the size of the input array.

### O(n) - Linear Time
An algorithm with O(n) time complexity has an execution time that increases linearly with the size of the input. Here’s an example:
```javascript
//javascript
function sumArray(arr) {
  let sum = 0;

  for (let i = 0; i < arr.length; i++) {
    sum += arr[i];
  }

  return sum;
}
```
This function sums all the elements in an array. It has a linear execution time because it performs one operation for each element in the input array.
```ruby
#ruby
def find_element(arr, target)
  arr.each do |element|
    if element == target
      return true
    end
  end

  return false
end
```
This function has a time complexity of O(n) because its execution time increases linearly with the size of the input array. In other words, it has linear time complexity.

### O(log n) - Logarithmic Time
And algorithm with O(log n) time complexity has an execution time that increases logarithmically with the size of the input. Here's an example:
```javaScript
//javascript
function binarySearch(arr, target) {
  let low = 0;
  let high = arr.length - 1;

  while (low <= high) {
    let mid = Math.floor((low + high) / 2);

    if (arr[mid] === target) {
      return true;
    } else if (arr[mid] < target) {
      low = mid + 1;
    } else {
      high = mid - 1;
    }
  }

  return false;
}
```
```ruby
#ruby
def binary_search(arr, target)
  low = 0
  high = arr.length - 1

  while low <= high
    mid = (low + high) / 2

    if arr[mid] == target
      return true
    elsif arr[mid] < target
      low = mid + 1
    else
      high = mid - 1
    end
  end

  return false
end
```
Both of these algorithms have a time complexity of O(log n) because their execution time increases logarithmically with the size of the input array. In other words, they have logarithmic time complexity.

### O(n log n) - Log-Linear Time
An algorithm with O(n log n) time complexity has an execution time that increases logarithmically with the size of the input. Here’s an example:
```javascript
//javascript
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
```ruby
#ruby
def merge_sort(arr)
  if arr.length <= 1
    return arr
  end

  mid = arr.length / 2
  left = arr[0...mid]
  right = arr[mid..-1]

  left = merge_sort(left)
  right = merge_sort(right)

  return merge(left, right)
end

def merge(left, right)
  result = []

  while left.length > 0 && right.length > 0
    if left[0] <= right[0]
      result << left.shift
    else
      result << right.shift
    end
  end

  while left.length > 0
    result << left.shift
  end

  while right.length > 0
    result << right.shift
  end

  return result
end
```
Both of these algorithms have a time complexity of O(n log n) because their execution time increases proportionally to the size of the input array multiplied by the logarithm of the size of the input array. In other words, they have n log n time complexity.

### O(n^2) - Quadratic Time
An algorithm with O(n^2) time complexity has an execution time that increases quadratically with the size of the input. Here’s an example:
```javascript
//javascript
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
```ruby
#ruby
def bubble_sort(arr)
  n = arr.length

  loop do
    swapped = false

    (n - 1).times do |i|
      if arr[i] > arr[i + 1]
        arr[i], arr[i + 1] = arr[i + 1], arr[i]
        swapped = true
      end
    end

    break unless swapped
  end

  return arr
end
```

This function sorts an array using the bubble sort algorithm. It has a quadratic execution time because it compares each element in the input array to every other element in the array.

### O(n!) - Factorial Time
An algorithm with O(n!) time complexity has an execution time that increases factorially with the size of the input. Here’s an example:
```javascript
//javascript
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
```ruby
#ruby
def permutation(str)
  if str.length == 1
    return [str]
  end

  result = []

  str.each_char.with_index do |char, index|
    sub_permutations = permutation(str[0...index] + str[index + 1..-1])

    sub_permutations.each do |sub_permutation|
      result << char + sub_permutation
    end
  end

  return result
end
```

This function generates all possible permutations of a given string. It has a factorial execution time because there are n! possible permutations of a string of length n.
