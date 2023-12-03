# First gift repeated

### Description

In the toy factory of the North Pole, each toy has a unique identification number.

However, due to an error in the toy machine, some numbers have been assigned to more than one toy.

Find the first identification number that has been repeated, where the second occurrence has the smallest index!

In other words, if there is more than one repeated number, you must return the number whose second occurrence appears first in the list. If there are no repeated numbers, return -1.

### Solution

```js
function findFirstRepeated(gifts) {
  let arr = []; 

  for(let i = 0; i < gifts.length; i++) {
    if(arr.includes(gifts[i])) {
      return gifts[i];
    }

    arr.push(gifts[i]);
  }

  return -1;
}
```

### Results

```
3,219 ops/s (Higher is better)
Cognitive complexity: 3
```