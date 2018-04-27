# javascipt-bits

##Make an array with values from 1 to n
// - Input: a number "n"
// - Ouput: An array that contains n elements: 1, 2, 3, ... n
///javascript
function growingList(n) {
var list = [];
for (var i=1; i<=n; i++) {
list.push(i)
}
return list;
}
///

###functional
///javascript
function growingList(n) {
return Array.from(Array(n).keys(), x => ++x);
//return [...Array(n).keys()].map(x => ++x);
}
///
console.log("\n> Exercise 2 --- Should display [1,2,3,4,5,6]");
console.log(growingList(6));
