---
title: Filter list for numbers
date: 2022-10-27 16:28:40
tags: javascript
---


Today's exercise:
```
In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.
```

My solution:
```js filter_list
function filter_list(l) {
  // Return a new array with the strings filtered out
  return l.filter(el => !isNaN(el) && typeof el === 'number');
}
```
