# javascipt-bits

## Make an array with values from 1 to n

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
growingList(6); // return [1,2,3,4,5,6]
```

```javascript
//functional
function growingList(n) {
  return Array.from(Array(n).keys(), x => ++x);
  //return [...Array(n).keys()].map(x => ++x);
}
growingList(7); // return [1,2,3,4,5,6,7]
```

## Find the product of an array

* Input Array of numbers
* Ouput: The product of every numbers

```javascript
// loop method
function productOfArray(numbers) {
  var list = 1;
  for (var i = 0; i < numbers.length; i++) {
    list = list * numbers[i];
  }
  return list;
}
productOfArray([2, 3, 7, 10]); // return 420;
```

```javascript
//For in Loop
function productOfArray(numbers) {
  var total = 1;
  for (var i in numbers) {
    total = total * numbers[i];
  }
  return total;
}
productOfArray([2, 3, 7, 10]); // return 420;
```

```javascript
// Functional
function productOfArray(numbers) {
  return numbers.reduce((acc, cur) => acc * cur);
}
productOfArray([2, 3, 7, 10]); // return 420;
```

## Find the average length of strings in array

* Input: Array of strings
* Ouput: The average length

```javascript
// Loop method
function averageWordLength(array) {
  var list = 0;
  for (var i = 0; i < array.length; i++) {
    list += array[i].length;
  }
  return list / array.length;
}
averageWordLength(["Fish", "Chips"]); // return 4.5
```

```javascript
// For in Loop
function averageWordLength(array) {
  var total = 0;
  for (var i in array) {
    total += array[i].length;
  }
  return total / array.length;
}
averageWordLength(["Fish", "Chips"]); // return 4.5
```

```javascript
// Clever trick
function averageWordLength(array) {
  return array.join("").length / array.length;
}
averageWordLength(["Pie", "Mash"])); // returns 3.5
```

```javascript
// Functional
function averageWordLength(array) {
  return array.reduce((a, b) => a.length + b.length) / array.length;
}
averageWordLength(["Fish", "Chips"]); // returns 4.5
```

## Display a sentence describing a person

* Input: Object with two properties: name (string) and gender ('male' or 'female')
* Ouput: A string that is
  name:A gender:"male" ==> "His name is A"
  name:B gender:"female" ==> "Her name is B"

```javascript
// Helper function
function pronoun(person) {
  if (person.gender === "female") {
    return "Her";
  } else if (person.gender == "male") {
    return "His";
  } else {
    return "Their";
  }
}
```

```javascript
//es6 template string
function displaySentence(person) {
  return `${pronoun(person)} name is ${person.name}`;
}
displaySentence({ name: "Steve", gender: "male" }); // return 'His name is Steve'
```

```javascript
function displaySentence(person) {
  return person.male ? "His" : "Her" + " name is " + person.name;
}
displaySentence({ name: "Jane", gender: "female" }); // return 'Her name is Jane'
```

## Counting Repetion

* Input: An array of string and a string
* Output: The number of time the string is present in the array

```javascript
// loop method
function howManyTimes(words, word) {
  var wordCount = 0;
  for (var i = 0; i < words.length; i++) {
    if (words[i] === word) wordCount++;
  }
  return wordCount;
}
howManyTimes(words, "matter"); // returns 4

// functional
function howManyTimes(words, word) {
  return words.filter(item => item === word).length;
}
howManyTimes(words, "dog"); // returns 0
var words = [
  "machine",
  "matter",
  "subset",
  "trouble",
  "starting",
  "matter",
  "eating",
  "matter",
  "truth",
  "disobedience",
  "matter"
];
```
