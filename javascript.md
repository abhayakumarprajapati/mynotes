1. push() & pop()
Add/remove elements at the end

js
Copy
Edit
let arr = [1, 2, 3];
arr.push(4); // [1, 2, 3, 4]
arr.pop();   // [1, 2, 3]


2. unshift() & shift()
Add/remove elements at the start

js
Copy
Edit
let arr = [1, 2, 3];
arr.unshift(0); // [0, 1, 2, 3]
arr.shift();    // [1, 2, 3]

3. map()
Transform each element and return a new array

js
Copy
Edit
const nums = [1, 2, 3];
const squared = nums.map(n => n * n); // [1, 4, 9]


4. filter()
Filter elements based on a condition

js
Copy
Edit
const nums = [1, 2, 3, 4];
const evens = nums.filter(n => n % 2 === 0); // [2, 4]

 5. reduce()
Reduce array to a single value

js
Copy
Edit
const nums = [1, 2, 3, 4];
const sum = nums.reduce((acc, n) => acc + n, 0); // 10

6. forEach()
Iterate over elements (no return)

js
Copy
Edit
[1, 2, 3].forEach(n => console.log(n));

7. find()
Returns the first element that matches a condition

js
Copy
Edit
const users = [{id: 1}, {id: 2}];
const user = users.find(u => u.id === 2); // {id: 2}


8. findIndex()
Returns index of the first matching element

js
Copy
Edit
const arr = [10, 20, 30];
const index = arr.findIndex(n => n === 20); // 1


9. some() & every()
Check conditions

js
Copy
Edit
[1, 2, 3].some(n => n > 2);  // true
[1, 2, 3].every(n => n > 0); // true


10. includes()
Check if value exists

js
Copy
Edit
[1, 2, 3].includes(2); // true

11. indexOf() & lastIndexOf()
Find position of value

js
Copy
Edit
const arr = [1, 2, 3, 2];
arr.indexOf(2);      // 1
arr.lastIndexOf(2);  // 3


12. slice()
Extract a part of array (non-destructive)

js
Copy
Edit
const arr = [1, 2, 3, 4];
const part = arr.slice(1, 3); // [2, 3]


 13. splice()
Add/remove elements (destructive)

js
Copy
Edit
const arr = [1, 2, 3];
arr.splice(1, 1); // removes 2 → [1, 3]
arr.splice(1, 0, 99); // insert 99 → [1, 99, 3]

14. concat()
Merge arrays

js
Copy
Edit
[1, 2].concat([3, 4]); // [1, 2, 3, 4]


15. flat() & flatMap()
Flatten nested arrays

js
Copy
Edit
[1, [2, [3]]].flat(2); // [1, 2, 3]
[1, 2, 3].flatMap(x => [x, x * 2]); // [1, 2, 2, 4, 3, 6]


16. sort()
Sort elements (be careful with numbers)

js
Copy
Edit
[3, 1, 2].sort(); // [1, 2, 3]
[10, 5, 1].sort((a, b) => a - b); // [1, 5, 10]


17. reverse()
Reverse the array

js
Copy
Edit
[1, 2, 3].reverse(); // [3, 2, 1]


 18. join()
Join array into string

js
Copy
Edit
['a', 'b', 'c'].join('-'); // 'a-b-c'


19. from() and Array.of()
Convert and create arrays

js
Copy
Edit
Array.from('abc'); // ['a', 'b', 'c']
Array.of(5);       // [5]



 20. at()
Get element by index (supports negative index)

js
Copy
Edit
const arr = [1, 2, 3];
arr.at(-1); // 3 (last element)


Bonus: 🔥 Object + String Must-Know Methods
✅ Object.keys(obj) / Object.values(obj) / Object.entries(obj)
js
Copy
Edit
const obj = { a: 1, b: 2 };
Object.keys(obj);   // ['a', 'b']
Object.values(obj); // [1, 2]
Object.entries(obj); // [['a', 1], ['b', 2]]




JSON.stringify() / JSON.parse()
js
Copy
Edit
const obj = { name: "Abhay" };
const json = JSON.stringify(obj); // '{"name":"Abhay"}'
JSON.parse(json); // { name: "Abhay" }



String.trim() / toLowerCase() / toUpperCase() / split() / replace()
js
Copy
Edit
' Hello '.trim(); // 'Hello'
'Hi-There'.split('-'); // ['Hi', 'There']


***"abhay" how to make first letter capital***


const name = "abhay";
const capitalized = name.charAt(0).toUpperCase() + name.slice(1);
console.log(capitalized); // "Abhay"

 Explanation:
name.charAt(0) → 'a'

.toUpperCase() → 'A'

name.slice(1) → 'bhay'

Combine → 'A' + 'bhay' → "Abhay"


***Bonus: Capitalize every word in a sentence***

const sentence = "abhay prajapati";
const capitalized = sentence
  .split(" ")
  .map(word => word.charAt(0).toUpperCase() + word.slice(1))
  .join(" ");

console.log(capitalized); // "Abhay Prajapati"

***new Map()***

 Create a Map

const map = new Map();

map.set('name', 'Abhay');
map.set(123, 'ID');
map.set(true, 'Boolean Key');

console.log(map.get('name')); // "Abhay"


console.log(map.has(123)); // true
map.delete(true);

console.log(map.size); // 2

for (const [key, value] of map) {
  console.log(`${key} = ${value}`);
}

map.forEach((value, key) => {
  console.log(`${key}: ${value}`);
});

 1. Store dynamic keys (e.g. DOM elements, objects)
js
Copy
Edit
const objKey = { id: 1 };
const map = new Map();
map.set(objKey, "data for object");


2. Count occurrences
js
Copy
Edit
const countMap = new Map();
const arr = ['a', 'b', 'a', 'c', 'a'];

arr.forEach(char => {
  countMap.set(char, (countMap.get(char) || 0) + 1);
});

console.log(countMap); // Map { 'a' => 3, 'b' => 1, 'c' => 1 }


***delete from Map ***

const map = new Map();

map.set('name', 'Abhay');
map.set('age', 27);

console.log(map.size); // 2

map.delete('age');  // Delete the 'age' key

console.log(map.has('age')); // false
console.log(map.size); // 1



