# The naugthy elf 

### Description

In Santa's workshop, a mischievous elf has been playing around with the gift production line, adding or removing an unplanned step.

You have the original sequence of original manufacturing steps and the modified modified sequence that may include an extra step or be missing a step.

Your task is to write a function that identifies and returns the first extra step that was added or removed in the manufacturing chain. If there is no difference between the sequences, return an empty string.

```js
const original = 'abcd'
const modified = 'abcde'
findNaughtyStep(original, modified) // 'e'

const original = 'stepfor'
const modified = 'stepor'
findNaughtyStep(original, modified) // 'f'

const original = 'abcde'
const modified = 'abcde'
findNaughtyStep(original, modified) // ''
```

### Solution

```js
function findNaughtyStep(original, modified) {
    const len = original.length > modified.length ? original.length : modified.length;

    for (let i = 0; i < len; i++) {
        if (original[i] !== modified[i]) {
            return original.length > modified.length ? original[i] : modified[i];
        }
    }

    return '';
}
```

### Results

```
3,171 ops/s (Higher is better)
Cognitive complexity: 5 (Lower is better)
```


