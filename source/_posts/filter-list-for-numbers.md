---
title: Filter list for numbers
date: 2022-11-07 16:28:40
tags:
- javascript
- 7kyu
---


### Today's exercise:

> In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.
>> ###### Kata created by [cmgerber](https://www.codewars.com/users/cmgerber)


Anything out of the ordinary that you would probably do in a normal day at work, having that in mind you could thing in something like this.

```js First iteration
function filterList (list) {
  var numberList = [];
  for (let i = 0; i < list.length; i++) {
    const item = list[i];
    if(typeof item === 'number') numberList.push(item)
  }
  return numberList;
}

```

this would be the "traditional" aproach, but there is a couple of things that are expendable

- empty array that we will mutate over the iteration loop
- the implementation of a loop with his variables

a cleaner way to do the same (the inmutable way) would be:

```js Second iteration
function filterList (list) {
  return list.filter(el => typeof el === 'number');
}

```
Intead of using the old and confortable for, we use the filter method of the array, thus we don't need and mutate an empty array nor the variables required in the for loop.

I have to confess that while reading the kata for the first time, my mind was **watch out with the NaN*. What is the issue with NaN you may ask?

>typeof NaN === 'number'

So if hipotheticatly in the list that this function receives, there is a NaN, this is gonna be in the returned array aswell. Luckly with an extra validation we can fix it.

```js Third iteration
function filter_list(l) {
  return l.filter(el => !isNaN(el) && typeof el === 'number');
}
```

and yes, this was the solution that I submited for the kata.But then, reading the others solution I found a clever aproach.
```js It wasn't exaclty like this
function filter_list(l) {
  return l.filter(el => Number.isInteger(el));
}

```
Better and cleaner, only one function call was needed. The only thing that I can change about this aproach that you can implement it a little cleaner.

```js Final version
function filter_list(l) {
  return l.filter(Number.isInteger);
}

```

by the way, I deliberately keep the filter_list function the same way that was presented in the kata, so no arrow function for it.

Without any more to write, until tomorrow!