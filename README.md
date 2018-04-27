# javascipt-bits

##Make an array with values from 1 to n

* Input: a number "n"
* Ouput: An array that contains n elements: 1, 2, 3, ... n

```javascript
function growingList(n) {
  var list = [];
  for (var i = 1; i <= n; i++) {
    list.push(i);
  }
  return list;
}
growingList(6);
// Should display [1,2,3,4,5,6]
```

###functional

```javascript
function growingList(n) {
  return Array.from(Array(n).keys(), x => ++x);
  //return [...Array(n).keys()].map(x => ++x);
}
growingList(7);
// Should display [1,2,3,4,5,6,7]
```

Find the product of an array

* Input: Array of numbers
* Ouput: The product of every numbers

```javascript
function productOfArray(numbers) {
    loop method
  var list = 1;
  for (var i=0; i<numbers.length; i++) {
    list = list * numbers[i]
  }
  return list;
  }
productOfArray([2, 3, 7, 10]));
// Should return 420;
```

### For in Loop

```javascript
function productOfArray(numbers) {

  var total= 1;
  for(var i in numbers) {
    total = total * numbers[i] ;
  }
   return total;
   }
productOfArray([2, 3, 7, 10]));
// Should return 420;
```

### Functional

```javascript
function productOfArray(numbers) {
     return numbers.reduce((acc, cur) => acc * cur )
}
productOfArray([2, 3, 7, 10]));
// Should return 420;
```

### Loop method

```javascript
function averageWordLength(array) {
  var list = 0;
  for (var i = 0; i < array.length; i++) {
    list += array[i].length;
  }
  return list / array.length;
}
console.log(averageWordLength(["Fish", "Chips"]));
// returns 4.5
```

### For in Loop

```javascript
function averageWordLength(array) {
  var total = 0;
  for (var i in array) {
    total += array[i].length;
  }
  return total / array.length;
}
console.log(averageWordLength(["Fish", "Chips"]));
// returns 4.5
```

### Clever trick

```javascript
function averageWordLength(array) {
  return array.join("").length / array.length;
}
console.log(averageWordLength(["Fish", "Chips"]));
// returns 4.5
```

### Functional

```javascript
function averageWordLength(array) {
  return array.reduce((a, b) => a.length + b.length) / array.length;
}
console.log(averageWordLength(["Fish", "Chips"]));
// returns 4.5
```
