# Javascript Data Types

## Primitives

A primitive value is represented at the lowest level of implementation of a programming language. All primitives are immutable, meaning they can't be changed.

JavaScript has **6 primitive data types**:

  * **string:** words or phrases (in quotes)
  * **number:** integer, floating point number (decimal), `NaN`
  * **boolean:** `true` or `false`
  * **`null`:** non-existent object (used for blanking out variables)
  * **`undefined`:** empty variable
  * **symbol:** reusable identifier for object properties ([only in ES6](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol))


One of JavaScript's quirks is having both `null` and `undefined`. As a rule of thumb, you should let JavaScript decide when something is `undefined`.  You should use `null` wherever you want to "blank out" a variable so that it has no value.



<!-- | Type | Example(s) | Falsey Value(s) |
| :--- | :-----  | :-- |
| **string** | `'lightyear'`, `"867-5309"` | `''` or `"" ` |
| **number** | `3.1415`, `31` | `0`, `-0`, `NaN`<sup>+</sup> |
| **boolean** | only `true` or `false` | `false` |
| **null** | only `null` | `null` |
| **undefined** | only `undefined` | `undefined` |
| **symbol** | `Symbol("first")` | &nbsp; | -->

<sup>+</sup>`NaN` is a special global value meaning "Not A Number". `NaN` is the returned value when numerical evaluations fail, e.g. `8/"hello"`.


### Objects

Primitive data types are not enough for most programming purposes. Objects are **reference data types** that allow us to group primitives together.

Instead of storing a value, variables holding objects store a reference to a location in memory, and the computer looks it up when needed.


  ```js
  var shirt = { size: "L", color: 'green', clean: false };
  ```

Objects store information in key-value pairs. The key acts like a label, and the value is the data or behavior associated with that label.

`Object` is the most basic reference type in JavaScript. Every other non-primitive we'll use -- `Array`, `Function`, `Date` -- is actually built out from the basic `Object` type.


#### Object Manipulation

**Creating** an object literal:

```js
var person = { name: 'Bill', height: '5 feet, 9 inches', age: 34 };
```

**Getting** the value associated with a key:

```js
// this is called bracket notation:
person['age']; //=> 34
// this is called dot notation:
person.age;    //=> 34

// what if key doesn't exist?
person['hasGlasses']; //=> undefined
```

**Adding** a key-value pair:

```js
person['hairColor'] = 'blonde';
person.hairColor = 'blonde';
//=> { name: 'Bill', height: '5 feet, 9 inches', age: 34, hairColor: 'blonde' }
```

**Setting** the value for a key:

```js
person['hairColor'] = 'green';
person.hairColor = 'green';
//=> { name: 'Bill', height: '5 feet, 9 inches', age: 34, hairColor: 'green' }
```


**Semi-removing** a value:  

Use `null` as a marker for an empty value.

```js
person.hairColor = null;
```


**Fully removing** a key-value pair (rare):

```js
delete person.height;
//=> { name: 'Bill', age: 34, hairColor: 'green' }
```

Finding **keys** in the object (rare):

```js
var keys = Object.keys(person);
//=> ['name', 'age', 'hairColor']
```


**Looping** through Objects (rare):

One way to loop through objects in JavaScript is to use `for ... in` loops:

```js
for (key in person){
  // this next condition is required because of the prototype chain, which we haven't talked about quite yet
  if (person.hasOwnProperty(key)){  
    console.log(key, ": ", person[key]);
  }
}
// the order is not guaranteed, but this console logs:
//   'name': 'Bill'
//   'age': 34
//   'hairColor': null
```


### Arrays

```js
var friends = ["Moe", "Larry", "Curly"];
//=> ["Moe", "Larry", "Curly"]
```

Arrays are objects that store collections of data in **sequential** order.  Arrays are great for:

* Storing collections of one kind of data
* Ordered lists
* Enumerating data, i.e. using an index to find items
* Quickly reordering data


####Array Manipulation

**Creating** an array (literal):

```js
var fruits = ["Apple", "Banana", "Cherry", "Durian", "Elderberry",
"Fig", "Guava", "Huckleberry", "Ice plant", "Jackfruit"];
```

**Getting** an element by index:

```js
fruits[0]; //=> "Apple"
fruits[3]; //=> "Durian"
```

**Setting** the value at an index:

```js
fruits[3] = "Grape";
```

> Noticing a pattern? Arrays are a kind of object, and indices are just the keys.  Arrays don't allow dot notation, though.

**Looping** through Arrays:

```js
  for (var i=10; i>0; i--){
    console.log(i);
  }
  console.log('Blastoff!');
```

#### Array Properties and Methods

**Finding the number of elements**, in the **length** property:

```js
fruits.length; //=> 10
```

> Note that length is a property, NOT a method, for JavaScript arrays!

**Adding** an element to the **front**:

```js
fruits.unshift("Apricot"); //=> 11
```

**Adding** an element to the **end**:  

```js
fruits.push("Kiwi"); //=> 12
```

**Removing** an element from the **front**:

```js
fruits.shift(); //=> "Apricot"
```

**Removing** an element from the **end**:  

```js
fruits.pop(); //=> "Kiwi"
```

**Finding** the index of an element:  

```js
fruits.indexOf("Jackfruit"); // 9
fruits[9]; //=> "Jackfruit"
```

![img](http://www.frusion.com/media/1011/fruit-row.png)


Check out MDN's <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array" target="_blank">Array documentation</a> for more information on arrays. In particular, all of the methods listed in the <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Array_instances" target="_blank">Array instances</a> section are available to use with JavaScript arrays. Commonly used array methods include `join`, `sort`, and `reverse`.


### Other Object Types

#### `String`

JavaScript primitives can't have methods or attributes; they're just simple data.  For convenience, JavaScript includes specialized global objects to "wrap" most of its primitives, providing handy built-in methods and properties.

`String` is the most commonly used of these objects.

[MDN String Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

#### `Math`

In order to perform certain number operations, JavaScript has a `Math` object with some very useful methods.

```js
// 2^4
Math.pow(2, 4)
//=> 16

// returns a random decimal number between 0 and 1
Math.random();
//=> 0.229375290430

// rounds a floating point number to an integer
Math.round(2.5);
//=> 3
```


### `typeof`


Use JavaScript's <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof" target="_blank">`typeof`</a> method to check the type of a variable or value.

### Independent Practice

Practice with this [training](https://github.com/sf-wdi-34/js-data-types-training).  


### Closing Thoughts

For web developers, it's critically important to be able to work with JavaScript objects.  JavaScript's features are mostly built into objects like `Date`, `Math`, and `document`. We'll also see that JavaScript objects and arrays form the basis of JSON, a very popular format for transferring application data across the web.

The most important things to practice right now are:

- getting and setting values from within complex structures that include nested arrays and objects.
- learning to read documentation.

### Resources

* [JavaScript data types and data structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
