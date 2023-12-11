# First gift repeated

### Description

In 🎅 Santa's workshop, some Christmas messages have been written in a peculiar way: the words within the brackets must be read backwards.

Santa needs these messages to be correctly formatted. Your task is to write a function that takes a string and reverses the characters within each pair of parentheses, removing the parentheses as well.

However, bear in mind that there may be nested parentheses, so you should reverse the characters in the correct order.

```js
const a = decode('hola (odnum)')
console.log(a) // hola mundo

const b = decode('(olleh) (dlrow)!')
console.log(b) // hello world!

const c = decode('sa(u(cla)atn)s')
console.log(c) // santaclaus

// Step by step:
// 1. Reverse the nested -> sa(ualcatn)s
// 2. Reverse the remaining one -> santaclaus
```

Notes:
- The input strings will always be well formed with parentheses that match correctly, you do not need to validate them.
- There should not be any parentheses left in the final message.
- The maximum nesting level is 2.

### Solution

```js
function decode(message) {
  const chars = message.split('');

  let isInOuter = false; 
  let isInInner = false;
  let outer = [];
  let inner = [];
  let decoded = [];

  for(let i = 0; i < chars.length; i++) {
      const char = chars[i];

      if(char === '(') { 
        if (!isInOuter && !isInInner) {
          isInOuter = true;
        } else if(isInOuter && !isInInner) {
          isInInner = true;
        }
      } else if (char === ')') {
        if (isInOuter && !isInInner) {
          decoded = decoded.concat(outer.reverse());
          outer = [];
          isInOuter = false;
        } else if(isInOuter && isInInner) {
          outer = outer.concat(inner.reverse());
          inner = [];
          isInInner = false;          
        }
      } else {
        if(!isInOuter && !isInInner) {
          decoded.push(char);
        } else if(isInOuter && !isInInner) {
          outer.push(char);
        } else if(isInOuter && isInInner) {
          inner.push(char);
        } 
      }
  }

  return decoded.join('');
}
```

### Results

```
2,572 ops/s (Higher is better)
Cognitive complexity: 18 (Lower is better)
```