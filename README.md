# Functional javascript comparisons

I am very aware there are many ways to solve a problems in programing and I think this can often be over looked. Personaly when writing code I like to use functional programing principles but when interacting with some developers they are more comfortable with alternative methods and I wanted to create this referance of problems sloved in a variety of ways to compare between them to help as a learning tool for people on both sides. I must confession I am not very comfortable with for loops as I haven't used them very often.

## Make an array with values from 1 to n

- Input: a number "n"
- Ouput: An array that contains n elements: 1, 2, 3, ... n

```javascript
// For loop method
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
// Functional method using Es6 `Array.from()` and `Array.keys()`
function growingList(n) {
  return Array.from(Array(n).keys(), x => ++x);
  //return [...Array(n).keys()].map(x => ++x);
}
growingList(7); // return [1,2,3,4,5,6,7]
```

## Find the product of an array

- Input: Array of numbers
- Ouput: The product of every numbers

```javascript
// For loop method
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
// For in Loop
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
// Functional using `Array.reduce()`
function productOfArray(numbers) {
  return numbers.reduce((acc, cur) => acc * cur);
}
productOfArray([2, 3, 7, 10]); // return 420;
```

## Find the average length of strings in array

- Input: Array of strings
- Ouput: The average length

```javascript
// For loop method
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
// Functional using `Array.reduce()`
function averageWordLength(array) {
  return array.reduce((a, b) => a.length + b.length) / array.length;
}
averageWordLength(["Fish", "Chips"]); // returns 4.5
```

## Display a sentence describing a person

- Input: Object with two properties: name (string) and gender ('male' or 'female')
- Ouput: A string that is
  name:A gender:"male" ==> "His name is A"
  name:B gender:"female" ==> "Her name is B"

```javascript
function displaySentence(person) {
  return person.gender === "male" ? "His" : "Her" + " name is " + person.name;
}
displaySentence({ name: "Jane", gender: "female" }); // return 'Her name is Jane'
```

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

// Es6 template string
function displaySentence(person) {
  return `${pronoun(person)} name is ${person.name}`;
}
displaySentence({ name: "Steve", gender: "male" }); // return 'His name is Steve'
```

## Convert values in an array to percentage

- Input: Array of numbers
- Ouput: The average of every number

```javascript
// For loop method
function percent(array) {
  var i,
    max = 0;
  var newarray = new Array();

  for (i = 0; i < array.length; i++) if (array[i] > max) max = array[i];

  for (i = 0; i < array.length; i++) newarray[i] = (array[i] * 100) / max;

  return newarray;
}
var store = [18, 200, 124, 98];
storePercentage = percent(store); //returns [9, 100, 64, 49]
```

```javascript
// Functional
const percent = arr => {
  const max = Math.max(...arr);
  return arr.map(int => {
    return int !== 0 ? Math.floor((int / max) * 100) : 0;
  });
};
var store = [18, 200, 124, 98];
storePercentage = percent(store); // returns [9, 100, 62, 49]
```

## Counting Repetion of a string in an array

- Input: An array of string and a string
- Output: The number of time the string is present in the array

```javascript
// For loop method
function howManyTimes(words, word) {
  var wordCount = 0;
  for (var i = 0; i < words.length; i++) {
    if (words[i] === word) wordCount++;
  }
  return wordCount;
}
howManyTimes(words, "matter"); // returns 4
```

```javascript
// Functional
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

## Longest fullname

- Input: An array of objects with each time a 'firstname' and 'lastname' property
- Output: The longuest fullname (with a space in between)

```javascript
// For loop method
function longuestFullname(persons) {
  longestName = "";
  for (var i = 0; i < persons.length; i++) {
    if (
      persons[i].firstname.length + persons[i].lastname.length >
      longestName.length
    ) {
      longestName = `${persons[i].firstname} ${persons[i].lastname}`;
    }
  }
  return longestName;
}
var persons = [
  { firstname: "Alice", lastname: "Smith" },
  { firstname: "Bob", lastname: "Lopez" },
  { firstname: "Charly", lastname: "Martin" }
];
console.log(longuestFullname(persons)); // return Charly Martin
```

```javascript
// Functional
function longestFullName(people) {
  return people.reduce((acc, { firstname, lastname }) => {
    return firstname.length + lastname.length > acc.length
      ? (acc = `${firstname} ${lastname}`)
      : acc;
  }, "");
}

var persons = [
  { firstname: "Alice", lastname: "Smith" },
  { firstname: "Bob", lastname: "Lopez" },
  { firstname: "Charly", lastname: "Martin" }
];
console.log(longuestFullname(persons)); // return Charly Martin
```

## Max of matrix

- Input: A two dimensional array of numbers
- Output: The maximum number of this matrix

```javascript
// For loop method - loop over arrays of array
function maxMatrix(matrix) {
  var highestNumber = 0;
  for (var i = 0; i < matrix.length; i++) {
    for (var a = 0; a < matrix[i].length; a++) {
      if (matrix[i][a] > highestNumber) {
        highestNumber = matrix[i][a];
      }
    }
  }
  return highestNumber;
}
var matrix1 = [[1, 6, 7], [7, 8, 4], [3, 5, 0]];
maxMatrix(matrix1); //return 8
```

```javascript
// Functional
function maxMatrix(matrix) {
  return Math.max(...[].concat.apply([], matrix));
}
var matrix1 = [[1, 6, 7], [7, 8, 4], [3, 5, 0]];
maxMatrix(matrix1); //return 8
```

## Traverse array elements diagonally

Source: https://www.codewars.com/kata/traverse-array-elements-diagonally/train/javascript
In this final exercise, you're given an n x n array and you're expected to traverse the elements diagonally from the bottom right to the top left.

- Input: An array of array
- Output: An array

```javascript
function diagonal(matrix) {}
var matrix2 = [[1, 6, 7], [7, 2, 4], [3, 5, 9]];
diagonal(matrix2); // return [9, 4, 5, 7, 2, 3, 6, 7, 1]
```
