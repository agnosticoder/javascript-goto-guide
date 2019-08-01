- [Object Spread Operator](#org69a1bc7)
- [Object and Array Destructuring](#org8a21a5c)
- [Array Built-in Methods](#org85d7788)
  - [Array.prototype.filter()](#orgfa09853)
  - [Array.prototype.map()](#org37a938c)
  - [Array.prototype.reduce()](#org05b4f8e)


<a id="org69a1bc7"></a>

# Object Spread Operator

```javascript
let user = {
    name: 'Satinder',
    age: 24
};

//Change the name and age when used before ...user and vice-versa
console.log({
    name: 'Andrew',
    age: 27,
    ...user,
    someId: '94343'
});

/* Output
{
 name: 'Satinder',
 age: 24,
 someId: '94343'
}
*/

console.log({
    age: 27,
    ...user,
    name: 'Stephen',
    someId: '94343'
});

/* Output
{
 name: 'Stephen',
 age: 24,
 someId: '94343'
}
*/
```


<a id="org8a21a5c"></a>

# Object and Array Destructuring

```javascript
//Object Destructuring
const person = {
    name: 'Andrew',
    age: 26,
    location: {
	city: 'Philadelphia',
	temperature: 92
    } 
};

const { name: hisName = 'yoyolo', age} =  person;

console.log(`${hisName} is ${age} yo buddy`);
//Andrew is 26 yo buddy

//Array Destructuring
const address = ['1299', 'Philadelphia', 'Pennsylvania', '1914'];

const [, city, state = 'Bathinda', ...yo] = address;

console.log(`You are in ${city} ${state} and ${yo}`);
//You are in Philadelphia Pennsylvania and 1914
```


<a id="org85d7788"></a>

# Array Built-in Methods


<a id="orgfa09853"></a>

## Array.prototype.filter()

The filter() method creates a new array with all elements that pass the test implemented by the provided function. It does not mutate the array on which it is called.

```javascript
var words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```


<a id="org37a938c"></a>

## Array.prototype.map()

-   The map() method creates a new array with the results of calling a provided function on every element in the calling array.
-   The callback function takes four arguments
    -   currentValue
    -   currentIndex
    -   sourceArray
    -   thisArg
-   map() does not mutate the array

```javascript
let officers = [
    { id: 20, name: 'Captain Piett'},
    { id: 24, name: 'General Veers'},
    { id: 56, name: 'Admiral Ozzel'},
    { id: 88, name: 'Commander Jerjerrod'}
];

//What I need is [20, 24, 56, 88]

let ids = officers.map((officer, index, array) => (officer.id));
console.log(ids); // [20, 24, 56, 88]
```


<a id="org05b4f8e"></a>

## Array.prototype.reduce()

-   The reduce() method executes a reducer function (that you provide) on each element of the array, resulting in a single output value.
-   reduce() takes the two arguments
    -   reducer function
    -   initialValue
        -   The first time the callback is called, accumulator and currentValue can be one of two values. If initialValue is provided in the call to reduce(), then accumulator will be equal to initialValue, and currentValue will be equal to the first value in the array. If no initialValue is provided, then accumulator will be equal to the first value in the array, and currentValue will be equal to the second.
        -   **Note: If initialValue is not provided, reduce() will execute the callback function starting at index 1, skipping the first index. If initialValue is provided, it will start at index 0.**
-   The reducer function takes the four arguments
    -   accumulator
    -   currentValue
    -   currentIndex
    -   sourceArray
-   Your **reducer** function's returned value is assigned to the accumulator, whose value is remembered across each iteration throughout the array and ultimately becomes the final, single resulting value.

```javascript
let val = [5, 4, 1, 2, 9];

//reducer function
const sum = (accumulator, currentValue) => {
    return accumulator + currentValue;
};

//If initialvalue is not used, the callback function will start at index 1
//by taking accumulator value equal to first element of array
//If initialvalue is used then accumulator will be equal to the initialvalue
const result = val.reduce(sum,0);
console.log(result);//21
```