# We start the factory

### Description

In Santa's workshop, the elves have a gift list they wish to make and a limited set of materials.

Gifts are strings of text and materials are characters. Your task is to write a function that, given a list of gifts and the available materials, returns a list of the gifts that can be made.

A gift can be made if we have all the necessary materials to make it.

```js
const gifts = ['tren', 'oso', 'pelota']
const materials = 'tronesa'

manufacture(gifts, materials) // ["tren", "oso"]

const gifts = ['juego', 'puzzle']
const materials = 'jlepuz'

manufacture(gifts, materials) // ["puzzle"]

const gifts = ['libro', 'ps5']
const materials = 'psli'

manufacture(gifts, materials) // []
```

### Solution

```js
function manufacture(gifts, materials) {
  let returnArr = [];
  const matChars = materials.split('');

  for(let i = 0; i < gifts.length; i++) {
    const giftChars = gifts[i].split('');

    const included = giftChars.every((giftChar) => matChars.includes(giftChar));

    if(included) {
      returnArr.push(gifts[i]);
    }
  }

  return returnArr;
}
```

### Results

```
2,487 ops/s (Higher is better)
Cognitive complexity: 4 (Lower is better)
```