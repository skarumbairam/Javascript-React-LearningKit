# Data Structure & Algorithms (Thanks to Namaste JS Akshay Shaini)

1. Given an array [10,40,20,54,100], find the index of the specific element; if the number is not found, return -1.\
2. Get the number of repetitions of negative integers in the array [-10,40,-20,54,100]
3.  Find the greatest number in the given array [-10,40,-20,54,100]
4.  Find the smallest number in the given array [-10,-40,-20, -54, -100]
5.  Find the second largest number in the given array [10,40,20,54,100]
6.  Given an integer num, return the number of digits in num , let num=3457756, output = 7
7.  Reverse the number
8.  Check if the given number is a palindrome, true or false: 7447 - true, 84523 - false
9.  Remove duplicates from the given sorted array (Non Decreasing Order - which means array can contain duplicate values) ( Increasing order : a[i+1] > a[i], decreasing order : a[i+1] < a[i])
10.  

## Some Problems with Using Loops and Arrays

1. Question: Given an array [10,40,20,54,100], find the index of the specific element; if the number is not found, return -1.
    ```
     function getNumberIndex (array, number) {
      for(let i=0; i<array.length ; i++){
        if(array[i] === number){
          return i;
        }
      }
      return -1;
    }
    
    const arr =  [10,40,20,54,100];
    const result = getNumberIndex(arr, 54);
    // Output 3
    ```

2. Question: Get the number of repetitions of negative integers in the array [-10,40,-20,54,100];

   ```
    function getNegativeIntCount (array) {
      let count = 0;
       for(let i = 0 ;i< array.length ; i++){
          if(array[i] < 0 ){
              count ++;
          }
       }
     return count;
   }
   const arr = [-10,40,-20,54,100];
   const result = getNegativeIntCount(arr)
   console.log(result) // 2
   ```
   

4. Question: Find the greatest number in the given array [-10,40,-20,54,100];

    ```
     function getLargestNumber (array) {
     let largestNumber = -Infinity;
        for(let i=0; i< array.length ; i++) {
           if(array[i] > largestNumber) {
             largestNumber = array[i];
           }
       }
       return largestNumber;
     }
    const arr = [-10,-40,-20, -54, -100];
    const result = getLargestNumber(arr);
    console.log(result) // -10
    ```
5. Question: Find the smallest number in the given array [-10,-40,-20, -54, -100];

   ```
    function getSmallestNumber (array) {
     let smallNumber = +Infinity;
        for(let i=0; i< array.length ; i++) {
           if(array[i] < smallNumber) {
             smallNumber = array[i];
           }
       }
       return smallNumber;
     }
    const arr = [-10,-40,-20, -54, -100];
    const result = getSmallestNumber(arr);
    console.log(result) // -100
    ```

6. Question: Find the second largest number in the given array [10,40,20,54,100].

   ```
    function secondLargestNumber (array) {
      let firstLargest = -Infinity;
      let secondLargest = -Infinity;

      for(let i = 0; i<array.length ; i++) {

        if(array[i]>firstLargest){
          secondLargest = firstLargest;
          firstLargest = array[i];
        } else if(array[i] > secondLargest){
             secondLargest = array[i];
        }
      }

      return secondLargest;
    }

    const arr = [-10,-40,-20, -54, -100];
    const result = secondLargestNumber(arr);
    console.log(result) // -20
   ```

   Edge Cases :
   - What happens if the array is empty
   - The array has duplicates
   - The array has a negative number
  
  ```
    function secondLargestNumber (array) {

      if(array.length <0) return "Invalid array";

      let firstLargest = -Infinity;
      let secondLargest = -Infinity;

      for(let i = 0; i<array.length ; i++) {

        if(array[i]>firstLargest){
          secondLargest = firstLargest;
          firstLargest = array[i];
        } else if(array[i] > secondLargest && array[i] !== firstLargest){
             secondLargest = array[i];
        }
      }

      return secondLargest;
    }

    const arr = [-10,-40,-20, -54, -100, -18, -10 ];
    const result = secondLargestNumber(arr);
    console.log(result) // -18
   ```

## Some Star & Pattern Problems with Using double loops (Nested Loop)

1. Pattern (nxn):
   
```
*  *  *  *  
*  *  *  *  
*  *  *  *  
*  *  *  * 

**OR **

1 2 3 4
1 2 3 4
1 2 3 4
1 2 3 4
(to print number substitute * = j);

const n = 4;
for (let i=0; i<n; i++){
    let row = "";
    for(let j=0; j<n; j++){
        row = row + "*";
        // row = row + (j+1);
    }
 console.log(row);
}
```

2. Pattern Triangle with * and number:
   
```
* 
*  * 
*  *  * 
*  *  *  * 
*  *  *  *  *

**OR **

1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
(to print number substitute * = j);

const n = 5;

for (let i=0; i<n; i++){
    let row = "";
    for(let j=0; j<i+1; j++){
        row = row + "*";
    }
 console.log(row);
}
```

3. Pattern Triangle (same row values)
   
```
1
2 2
3 3 3
4 4 4 4
5 5 5 5 5

const n = 5;
for (let i = 0; i < n; i++) {
    let row = "";
    for (let j = 0; j < i + 1; j++) {
        row = row + (i+1);
    }
    console.log(row);
}

```
4. Pattern (Reverse Triangle)
   
```
1 2 3 4 5
1 2 3 4
1 2 3
1 2
1

for (let i = 0; i < n; i++) {
    let row = "";
    for (let j = 0; j < n - i; j++) {
        row = row + (j + 1)
    }
    console.log(row);
}

```

5. Pattern (Flip Triangle)
   
```

         *
       * *
     * * *
   * * * *
 * * * * *

const n = 5;
for (let i = 0; i < n; i++) {
    let row = "";

    { /* Create Empty Space */ }
    
    for (let j = 0; j < n-(i+1); j++) {
        row = row + ' ';
    }

    { /* Create Star */ }
    for (let k = 0; k < (i + 1); k++){
        row = row + '*';
    }

    console.log(row);
}

```

5. Pattern (Triangle number switch)

```
1
1 0
1 0 1
1 0 1 0
1 0 1 0 1

const n = 6;
for (let i = 0; i < n; i++) {
    let row = "";
    let toggle = 1;
    for (let j = 0; j < i + 1; j++) {
        row = row + toggle;
        if (toggle === 1) {
            toggle = 0;
        } else {
            toggle = 1;
        }
    }
    console.log(row);
}
```
## Count Digit pattern Problems & things to note

Note: 
- Math.floor → Rounds down to the nearest integer Math.floor(4.9) => 4
- Math.ceil → Rounds up to the nearest integer Math.ceil(4.1) => 5
- Math.round → Round to nearest (4.5 → 5), (4.4 → 4)
- Math.abs → Returns the absolute value (negative becomes positive, positive stays positive)
  
1.  Given an integer num, return the number of digits in num.
   
```
Input: num = 7, Output: 1
Input: num = 100, Output = 3
Input: num = -2030, output = 4

function countDigit(num) {
    // Handle 0 case
    if (num === 0) return 1;

    // Handle negative, this converts to a positive number
    num = Math.abs(num);

    let count = 0;

    while (num > 0) {
        num = Math.floor(num / 10); // Math.floor will round off Down 
        count++;
    }

    return count;
}

const getDigitCount = countDigit(23050);
console.log(getDigitCount);
```

2.  Check if the given number is a palindrome.
   
```
    Important Note:
       - Remove last digit from the number -> number/10
       - Get the last digit from the number  -> number % 10
     
    function palindrome(num) {
        // Handle 0 case
        if (num === 0) return 1;
    
        const numCopy = num;
        console.log('num ' + numCopy);
        num = Math.abs(num);
        let reverse = 0;
        while (num > 0) {
           
            let remainder = num % 10;
            num = Math.floor(num / 10);
            reverse = (10 * reverse) + remainder;
            console.log(reverse);
        }
    
        console.log('reverse ' + reverse);
        return numCopy === reverse;
    }
    
    const isPolindrome = palindrome(-2002);
    console.log(isPolindrome);
```

3. Reverse the number

```
- Input 24563: output 36542
- Input -345: output -543
 
    function revenseNumber(num) {
        // Handle 0 case
        if (num === 0) return 1;
    
        const numCopy = num;
        console.log('num ' + numCopy);
    
        num = Math.abs(num);
        let reverse = 0;
    
        while (num > 0) {
            let remainder = num % 10;
            num = Math.floor(num / 10);
            reverse = (10 * reverse) + remainder;
        }
    
        return numCopy < 0 ? -reverse : reverse;
    }
    
    const getReverseNumber = revenseNumber(-234763);
    console.log(getReverseNumber);
```

## Some Array Problems

1. Remove duplicates from a sorted array (Leetcode 26), Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

```
Example 1:
    Input: nums = [1,1,2]
    Output: 2, nums = [1,2,_]
    Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
    It does not matter what you leave beyond the returned k (hence they are underscores).
Example 2:
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).

    function removeDuplicates(arr) {
    
            let x = 0;
           // const uniqueArry = [];
            for (let i = 0; i < arr.length; i++) {
                // uniqueArry[0] = arr[0];
                if (arr[i] > arr[x]) {
                    x = x + 1;
                    arr[x] = arr[i];
                  // uniqueArry[x] = arr[i];
                }
            }
        
            console.log(arr);
          //  console.log(uniqueArry);
            return x+1;
     }
    
    const array = [0,0,1,1,2,2,3,3];
    const getUniqueArray = removeDuplicates(array);
    console.log(getUniqueArray);
```
2. Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val. (Leet Code 27)

```
function removeDuplicates(arr, val) {

  let x = 0;
  let modified = [];
  for (let i = 0; i < arr.length; i++) {

    if (arr[i] !== val) {
      modified[x] = arr[i];
      x = x + 1;
    } 
  }

  console.log(modified)
  return x;
}

const array = [3,2,1,5,3];

const getUniqueArray = removeDuplicates(array, 3);
console.log(getUniqueArray);
```
   
