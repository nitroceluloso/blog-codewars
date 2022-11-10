---
title: Square sequence
date: 2022-11-08 09:31:03
tags:
- javascript
- 7kyu
---

Wellcome!
Let's start with todays kata:

>Complete the function that returns an array of length n, starting with the given number x and the squares of the previous number. If n is negative or zero, return an empty array/list.

When I first starting to write the code I understood that I had to return an array with the "detailed" square sequence, so if I receive 2^4, the returned array would be [2,4,8, 16], intead of the wanted result that is [2, 4, 16, 256].

```js First iteration
function squares(x, n) {
    if(n <=0) return [];
    const squaresArray = [x];
    for(let count = 1; count < n; count++){
        const square = squaresArray[squaresArray.length - 1] ** 2
        squaresArray.push(square)
    }
    return squaresArray;
}
```

This solution uses the for loop to add each previous element (to the square) into a new array. But as I try to use arrays and its methods (because I like the redability).
This would be "better" aproach:

```js Second iteration
function squares(x, n) {
  if(n <= 0) return []
  const factors = new Array(n -1).fill(0);
  return factors.reduce((prev, el) => {
    const prevEl = prev[prev.length-1];
    return prev.concat(prevEl**2);
  }, [x]);
}
```

In the line 3 I create an array of n-1 length (empty), and then filled with 0, so I can loop it after.
On line 6 I use the reduce method, and a initial value an array with the first number.

This second iteration was the answer that I sent, so now I will show you some interesting things that I found taking a look of the others solutions:

```js Founeded solution A (not exactly like this)
function squares(x, n) {
  if(n <= 0) return []
  const factors = new Array(n -1).fill(0);
  return factors.reduce((prev, el) => {
    const prevEl = prev[prev.length-1];
    const squareNumber = Math.pow(prevEl, 2);
    return prev.concat(squareNumber);
  }, [x]);
}

```
I wasn't aware of the method pow from Math, I was aware only of the ** operator.

*other consideration*

There is this [at](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/at) array method, which is cleaner that the array[array.length] way, so the previous code will look like this:

```js Using at method
function squares(x, n) {
  if(n <= 0) return []
  const factors = new Array(n -1).fill(0);
  return factors.reduce((prev, el) => {
    const prevEl = prev.at(-1);
    const squareNumber = Math.pow(prevEl, 2);
    return prev.concat(squareNumber);
  }, [x]);
}

```

I prefer this way *mainy* because is shorter and as easy to understand.

With nothing more to write, until the next post!