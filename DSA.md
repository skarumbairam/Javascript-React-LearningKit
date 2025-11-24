# Data Structure & Algorithms (Thanks to Namaste JS Akshay Shaini)

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

```

