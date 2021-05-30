### Hi there, I'm Saurav - 👋 
### This repository contains a list of most popular JavaScript interview questions. It also includes some tricky questions on Algorithms, DataStructures, React, Node and Express.


## I'm a full stack JavaScript Developer!!

- 🌱 I’m currently learning everything 🤣
- 👯 I’m looking to collaborate with other content creators
- 🥅 2021 Goals: Contribute more to Open Source projects
- ⚡ Fun fact: I love to draw and visit new places

### Languages and Tools:

<img align="left" alt="Visual Studio Code" width="26px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/visual-studio-code/visual-studio-code.png" />
<img align="left" alt="HTML5" width="26px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/html/html.png" />
<img align="left" alt="CSS3" width="26px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/css/css.png" />
<img align="left" alt="Sass" width="26px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/sass/sass.png" />
<img align="left" alt="JavaScript" width="26px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/javascript/javascript.png" />
<img align="left" alt="React" width="26px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/react/react.png" />
<img align="left" alt="Node.js" width="26px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/nodejs/nodejs.png" />
<img align="left" alt="MongoDB" width="26px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/mongodb/mongodb.png" />
<img align="left" alt="Git" width="26px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/git/git.png" />
<img align="left" alt="GitHub" width="26px" src="https://raw.githubusercontent.com/github/explore/78df643247d429f6cc873026c0622819ad797942/topics/github/github.png" />
<img align="left" alt="Terminal" width="26px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/terminal/terminal.png" />
<br />
<br />


# Importnant Interview Questions: 

#### 1.Predict the output of the below code

<pre>
<code>
  const user = {
  name: 'Raj',
  location: {
    city: 'NY',
    state: 'NY'
  }
};
const copy = Object.assign({}, user);
// OR
// const copy = { ...user };
copy.location.city = 'Albany';
console.log('original: ', user.location);
console.log('copy:', copy.location);
  </code>
  </pre>
  
The output of the above code is
<pre><code>
original:  {
  city: 'Albany',
  state: 'NY'
}
copy: {
  city: 'Albany',
  state: 'NY'
}
</code></pre>
</br>
The reason for the changed original object is because when we use Object.assign or spread operator, it only does shallow copy, which means while creating a copy of the object, properties of only the first level are copied and if there are nested properties then only their reference is copied which means the copied reference still refers to the original place where the object is stored.
</br>
So in our case, the location property will still refer to the original object which is a user object in our case.

#### 2.Predict the output of the below code
<pre><code>
const number = 1;
const result = (function (number) {
  delete number;
  return number;
})(10);
console.log(result);
</code></pre>
</br>
The output of the above code is 10.

In this code, we are passing the value 10 as the input to the function. But again inside the function number is just a local primitive type of variable so delete will not make any changes to the number and the value 10 passed to the function will be returned from the function.

#### 3.Predict the output of the below code
<pre><code>
function display() {
  var a = b = 10;
}
display();
console.log('b', typeof b === 'undefined');
console.log('a', typeof a === 'undefined');
</code></pre>
</br>

The output of the above code is
b false
a true

</br>
This is because the <b>assignment operator has right to left associativity in Javascript which means it will be evaluated from right to left so first, b will be assigned the value 10 and then it’s assigned to a</b>. Therefore
</br>
<pre><code>
function display() {
  var a = b = 10;
}
</code></pre>
is same as
<pre><code>
function display() {
  var a = (b = 10);
}
</code></pre>
which is same as
<pre><code>
function display() {
 b = 10; 
 var a = b;
}
</code></pre>
So b becomes a global variable because there is no var keyword before it and a becomes a local variable. Therefore, outside the function, only b is available so typeof a === 'undefined' comes as true and typeof b === 'undefined' comes as false.

Output
If we execute the above code in strict mode as shown below,

<pre><code>
'use strict';
function display() {
  var a = b = 10;
}
display();
console.log('b', typeof b === 'undefined');
console.log('a', typeof a === 'undefined');
</code></pre>

It will throw an error because b becomes a global variable and <b>strict mode does not allow creating global variables</b> so you will get an error when you execute this code.

## Array
<a name="array--product"></a><a name="1.1"></a>
- **[1.1](#array--product) Given an array of integers, find the largest product yielded from three of the integers**
  ```javascript
  var unsortedArray = [-10, 7, 29, 30, 5, -10, -70];

  computeProduct(unsortedArray); // 21000

  function sortIntegers(a, b) {
    return a - b;
  }

  // Greatest product is either (min1 * min2 * max1 || max1 * max2 * max3)
  function computeProduct(unsorted) {
    var sortedArray = unsorted.sort(sortIntegers),
      product1 = 1,
      product2 = 1,
      array_n_element = sortedArray.length - 1;

    // Get the product of three largest integers in sorted array
    for (var x = array_n_element; x > array_n_element - 3; x--) {
        product1 = product1 * sortedArray[x];
    }

    product2 = sortedArray[0] * sortedArray[1] * sortedArray[array_n_element];

    if (product1 > product2) return product1;

    return product2;
  }
  ```
  **View on Codepen:** https://codepen.io/kennymkchan/pen/LxoMvm?editors=0012

<a name="array--consecutive--sum"></a><a name="1.2"></a>
- **[1.2](#array--consecutive--sum) Being told that an unsorted array contains (n - 1) of n consecutive numbers (where the bounds are defined), find the missing number in `O(n)` time**
  ```javascript
  // The output of the function should be 8
  var arrayOfIntegers = [2, 5, 1, 4, 9, 6, 3, 7];
  var upperBound = 9;
  var lowerBound = 1;

  findMissingNumber(arrayOfIntegers, upperBound, lowerBound); // 8

  function findMissingNumber(arrayOfIntegers, upperBound, lowerBound) {
    // Iterate through array to find the sum of the numbers
    var sumOfIntegers = 0;
    for (var i = 0; i < arrayOfIntegers.length; i++) {
      sumOfIntegers += arrayOfIntegers[i];
    }

    // Find theoretical sum of the consecutive numbers using a variation of Gauss Sum.
    // Formula: [(N * (N + 1)) / 2] - [(M * (M - 1)) / 2];
    // N is the upper bound and M is the lower bound

    upperLimitSum = (upperBound * (upperBound + 1)) / 2;
    lowerLimitSum = (lowerBound * (lowerBound - 1)) / 2;

    theoreticalSum = upperLimitSum - lowerLimitSum;

    return theoreticalSum - sumOfIntegers;
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/rjgoXw?editors=0012

<a name="array--unique"></a><a name="1.3"></a>
- **[1.3](#array--unique) Removing duplicates of an array and returning an array of only unique elements**
  ```javascript
  // ES6 Implementation
  var array = [1, 2, 3, 5, 1, 5, 9, 1, 2, 8];

  Array.from(new Set(array)); // [1, 2, 3, 5, 9, 8]

  // ES5 Implementation
  var array = [1, 2, 3, 5, 1, 5, 9, 1, 2, 8];

  uniqueArray(array); // [1, 2, 3, 5, 9, 8]

  function uniqueArray(array) {
    var hashmap = {};
    var unique = [];

    for(var i = 0; i < array.length; i++) {
      // If key returns undefined (unique), it is evaluated as false.
      if(!hashmap.hasOwnProperty(array[i])) {
        hashmap[array[i]] = 1;
        unique.push(array[i]);
      }
    }

    return unique;
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/ZLNwze?editors=0012

<a name="array--largest-difference"></a><a name="1.4"></a>
- **[1.4](#array--largest-difference) Given an array of integers, find the largest difference between two elements such that the element of lesser value must come before the greater element**
  ```javascript
  var array = [7, 8, 4, 9, 9, 15, 3, 1, 10];
  // [7, 8, 4, 9, 9, 15, 3, 1, 10] would return `11` based on the difference between `4` and `15`
  // Notice: It is not `14` from the difference between `15` and `1` because 15 comes before 1.

  findLargestDifference(array);

  function findLargestDifference(array) {
    // If there is only one element, there is no difference
    if (array.length <= 1) return -1;

    // currentMin will keep track of the current lowest
    var currentMin = array[0];
    var currentMaxDifference = 0;

    // We will iterate through the array and keep track of the current max difference
    // If we find a greater max difference, we will set the current max difference to that variable
    // Keep track of the current min as we iterate through the array, since we know the greatest
    // difference is yield from `largest value in future` - `smallest value before it`

    for (var i = 1; i < array.length; i++) {
      if (array[i] > currentMin && (array[i] - currentMin > currentMaxDifference)) {
        currentMaxDifference = array[i] - currentMin;
      } else if (array[i] <= currentMin) {
        currentMin = array[i];
      }
    }

    // If negative or 0, there is no largest difference
    if (currentMaxDifference <= 0) return -1;

    return currentMaxDifference;
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/MJdLWJ?editors=0012

<a name="array--product-other-than-itself"></a><a name="1.5"></a>
- **[1.5](#array--product-other-than-itself) Given an array of integers, return an output array such that output[i] is equal to the product of all the elements in the array other than itself. (Solve this in O(n) without division)**
  ```javascript
  var firstArray = [2, 2, 4, 1];
  var secondArray = [0, 0, 0, 2];
  var thirdArray = [-2, -2, -3, 2];

  productExceptSelf(firstArray); // [8, 8, 4, 16]
  productExceptSelf(secondArray); // [0, 0, 0, 0]
  productExceptSelf(thirdArray); // [12, 12, 8, -12]

  function productExceptSelf(numArray) {
  	var product = 1;
  	var size = numArray.length;
  	var output = [];

    // From first array: [1, 2, 4, 16]
    // The last number in this case is already in the right spot (allows for us)
    // to just multiply by 1 in the next step.
    // This step essentially gets the product to the left of the index at index + 1
  	for (var x = 0; x < size; x++) {
  		output.push(product);
  		product = product * numArray[x];
  	}

    // From the back, we multiply the current output element (which represents the product
    // on the left of the index, and multiplies it by the product on the right of the element)
  	var product = 1;
  	for (var i = size - 1; i > -1; i--) {
  		output[i] = output[i] * product;
  		product = product * numArray[i];
  	}

    return output;
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/OWYdJK?editors=0012

<a name="array--intersection"></a><a name="1.6"></a>
- **[1.6](#array--intersection) Find the intersection of two arrays. An intersection would be the common elements that exists within both arrays. In this case, these elements should be unique!**
  ```javascript
  var firstArray = [2, 2, 4, 1];
  var secondArray = [1, 2, 0, 2];

  intersection(firstArray, secondArray); // [2, 1]

  function intersection(firstArray, secondArray) {
    // The logic here is to create a hashmap with the elements of the firstArray as the keys.
    // After that, you can use the hashmap's O(1) look up time to check if the element exists in the hash
    // If it does exist, add that element to the new array.

    var hashmap = {};
    var intersectionArray = [];

    firstArray.forEach(function(element) {
      hashmap[element] = 1;
    });

    // Since we only want to push unique elements in our case... we can implement a counter to keep track of what we already added
    secondArray.forEach(function(element) {
      if (hashmap[element] === 1) {
        intersectionArray.push(element);
        hashmap[element]++;
      }
    });

    return intersectionArray;

    // Time complexity O(n), Space complexity O(n)
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/vgwbEb?editors=0012

**[⬆ back to top](#table-of-contents)**

## Strings
<a name="string--reverse"></a><a name="2.1"></a>
- **[2.1](#string--reverse) Given a string, reverse each word in the sentence**
  `"Welcome to this Javascript Guide!"` should be become `"emocleW ot siht tpircsavaJ !ediuG"`
  ```javascript
  var string = "Welcome to this Javascript Guide!";

  // Output becomes !ediuG tpircsavaJ siht ot emocleW
  var reverseEntireSentence = reverseBySeparator(string, "");

  // Output becomes emocleW ot siht tpircsavaJ !ediuG
  var reverseEachWord = reverseBySeparator(reverseEntireSentence, " ");

  function reverseBySeparator(string, separator) {
    return string.split(separator).reverse().join(separator);
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/VPOONZ?editors=0012

<a name="string--anagram"></a><a name="2.2"></a>
- **[2.2](#string--anagram) Given two strings, return true if they are anagrams of one another**
  `"Mary" is an anagram of "Army"`
  ```javascript
  var firstWord = "Mary";
  var secondWord = "Army";

  isAnagram(firstWord, secondWord); // true

  function isAnagram(first, second) {
    // For case insensitivity, change both words to lowercase.
    var a = first.toLowerCase();
    var b = second.toLowerCase();

    // Sort the strings, and join the resulting array to a string. Compare the results
    a = a.split("").sort().join("");
    b = b.split("").sort().join("");

    return a === b;
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/NdVVVj?editors=0012

<a name="string--palindrome"></a><a name="2.3"></a>
- **[2.3](#string--palindrome) Check if a given string is a palindrome**
  `"racecar" is a palindrome. "race car" should also be considered a palindrome. Case sensitivity should be taken into account`
  ```javascript
  isPalindrome("racecar"); // true
  isPalindrome("race Car"); // true

  function isPalindrome(word) {
    // Replace all non-letter chars with "" and change to lowercase
    var lettersOnly = word.toLowerCase().replace(/\s/g, "");

    // Compare the string with the reversed version of the string
    return lettersOnly === lettersOnly.split("").reverse().join("");
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/xgNNNB?editors=0012

<a name="string--isIsomorphic"></a><a name="2.3"></a>
- **[2.3](#string--palindrome) Check if a given string is a isomorphic**

  ```
  For two strings to be isomorphic, all occurrences of a character in string A can be replaced with another character
  to get string B. The order of the characters must be preserved. There must be one-to-one mapping for ever char of
  string A to every char of string B.

  `paper` and `title` would return true.
  `egg` and `sad` would return false.
  `dgg` and `add` would return true.
  ```
  ```javascript
  isIsomorphic("egg", 'add'); // true
  isIsomorphic("paper", 'title'); // true
  isIsomorphic("kick", 'side'); // false

  function isIsomorphic(firstString, secondString) {

    // Check if the same lenght. If not, they cannot be isomorphic
    if (firstString.length !== secondString.length) return false

    var letterMap = {};

    for (var i = 0; i < firstString.length; i++) {
      var letterA = firstString[i],
          letterB = secondString[i];

      // If the letter does not exist, create a map and map it to the value
      // of the second letter
      if (letterMap[letterA] === undefined) {
        // If letterB has already been added to letterMap, then we can say: they are not isomorphic.
        if(secondString.indexOf(letterB) < i){
            return false;
        } else {
            letterMap[letterA] = letterB;            
        }
      } else if (letterMap[letterA] !== letterB) {
        // Eles if letterA already exists in the map, but it does not map to
        // letterB, that means that A is mapping to more than one letter.
        return false;
      }
    }
    // If after iterating through and conditions are satisfied, return true.
    // They are isomorphic
    return true;
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/mRZgaj?editors=0012

**[⬆ back to top](#table-of-contents)**

## Stacks and Queues

<a name="stack-queue--stack-as-queue"></a><a name="3.1"></a>
- **[3.1](#stack-queue--stack-as-queue) Implement enqueue and dequeue using only two stacks**
  ```javascript
  var inputStack = []; // First stack
  var outputStack = []; // Second stack

  // For enqueue, just push the item into the first stack
  function enqueue(stackInput, item) {
    return stackInput.push(item);
  }

  function dequeue(stackInput, stackOutput) {
    // Reverse the stack such that the first element of the output stack is the
    // last element of the input stack. After that, pop the top of the output to
    // get the first element that was ever pushed into the input stack
    if (stackOutput.length <= 0) {
      while(stackInput.length > 0) {
        var elementToOutput = stackInput.pop();
        stackOutput.push(elementToOutput);
      }
    }

    return stackOutput.pop();
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/mRYYZV?editors=0012

<a name="stack-queue--parentheses-balancing"></a><a name="3.2"></a>
- **[3.2](#stack-queue--parentheses-balancing) Create a function that will evaluate if a given expression has balanced parentheses -- Using stacks**
  In this example, we will only consider "{}" as valid parentheses
  `{}{}` would be considered balancing. `{{{}}` is not balanced
  ```javascript
  var expression = "{{}}{}{}"
  var expressionFalse = "{}{{}";

  isBalanced(expression); // true
  isBalanced(expressionFalse); // false
  isBalanced(""); // true

  function isBalanced(expression) {
    var checkString = expression;
    var stack = [];

    // If empty, parentheses are technically balanced
    if (checkString.length <= 0) return true;

    for (var i = 0; i < checkString.length; i++) {
      if(checkString[i] === '{') {
        stack.push(checkString[i]);
      } else if (checkString[i] === '}') {
        // Pop on an empty array is undefined
        if (stack.length > 0) {
          stack.pop();
        } else {
          return false;
        }
      }
    }

    // If the array is not empty, it is not balanced
    if (stack.pop()) return false;
    return true;
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/egaawj?editors=0012

**[⬆ back to top](#table-of-contents)**

## Recursion
<a name="recursion--decimal-to-binary"></a><a name="4.1"></a>
- **[4.1](#recursion--decimal-to-binary) Write a recursive function that returns the binary string of a given decimal number**
  Given `4` as the decimal input, the function should return `100`

  ```javascript
  decimalToBinary(3); // 11
  decimalToBinary(8); // 1000
  decimalToBinary(1000); // 1111101000

  function decimalToBinary(digit) {
    if(digit >= 1) {
      // If digit is not divisible by 2 then recursively return proceeding
      // binary of the digit minus 1, 1 is added for the leftover 1 digit
      if (digit % 2) {
        return decimalToBinary((digit - 1) / 2) + 1;
      } else {
        // Recursively return proceeding binary digits
        return decimalToBinary(digit / 2) + 0;
      }
    } else {
      // Exit condition
      return '';
    }
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/OWYYKb?editors=0012

<a name="recursion--binary-search"></a><a name="4.2"></a>
- **[4.2](#recursion--binary-search) Write a recursive function that performs a binary search**

  ```javascript
  function recursiveBinarySearch(array, value, leftPosition, rightPosition) {
    // Value DNE
    if (leftPosition > rightPosition) return -1;

    var middlePivot = Math.floor((leftPosition + rightPosition) / 2);
    if (array[middlePivot] === value) {
      return middlePivot;
    } else if (array[middlePivot] > value) {
      return recursiveBinarySearch(array, value, leftPosition, middlePivot - 1);
    } else {
      return recursiveBinarySearch(array, value, middlePivot + 1, rightPosition);
    }
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/ygWWmK?editors=0012

**[⬆ back to top](#table-of-contents)**

## Numbers
<a name="numbers--power-of-two"></a><a name="5.1"></a>
- **[5.1](#numbers--power-of-two) Given an integer, determine if it is a power of 2. If so,
  return that number, else return -1. (0 is not a power of two)**
  ```javascript
  isPowerOfTwo(4); // true
  isPowerOfTwo(64); // true
  isPowerOfTwo(1); // true
  isPowerOfTwo(0); // false
  isPowerOfTwo(-1); // false

  // For the non-zero case:
  function isPowerOfTwo(number) {
    // `&` uses the bitwise n.
    // In the case of number = 4; the expression would be identical to:
    // `return (4 & 3 === 0)`
    // In bitwise, 4 is 100, and 3 is 011. Using &, if two values at the same
    // spot is 1, then result is 1, else 0. In this case, it would return 000,
    // and thus, 4 satisfies are expression.
    // In turn, if the expression is `return (5 & 4 === 0)`, it would be false
    // since it returns 101 & 100 = 100 (NOT === 0)

    return number & (number - 1) === 0;
  }

  // For zero-case:
  function isPowerOfTwoZeroCase(number) {
    return (number !== 0) && ((number & (number - 1)) === 0);
  }
  ```
  **View on Codepen:** http://codepen.io/kennymkchan/pen/qRGGeG?editors=0012

**[⬆ back to top](#table-of-contents)**

## Javascript
<a name="javascript--hoisting"></a><a name="6.1"></a>
- **[6.1](#javascript--hosting) Explain what is hoisting in Javascript**

  ```
  Hoisting is the concept in which Javascript, by default, moves all declarations to the top
  of the current scope. As such, a variable can be used before it has been declared. Note that
  Javascript only hoists declarations and not initializations
  ```

<a name="javascript--use-strict"></a><a name="6.2"></a>
- **[6.2](#javascript--use-strict) Describe the functionality of the `use strict;` directive**
  ```
  the `use strict` directive defines that the Javascript should be executed in `strict mode`.
  One major benefit that strict mode provides is that it prevents developers from using
  undeclared variables. Older versions of javascript would ignore this directive declaration
  ```

  ```javascript
  // Example of strict mode
  "use strict";

  catchThemAll();
  function catchThemAll() {
    x = 3.14; // Error will be thrown
    return x * x;
  }
  ```
<a name="javascript--event-bubbling"></a><a name="6.3"></a>
- **[6.3](#javascript--event-bubbling) Explain `event bubbling` and how one may prevent it**
  ```
  Event bubbling is the concept in which an event triggers at the deepest possible element,
  and triggers on parent elements in nesting order. As a result, when clicking on a child element
  one may exhibit the handler of the parent activating.

  One way to prevent event bubbling is using `event.stopPropagation()` or `event.cancelBubble`
  on IE < 9
  ```
<a name="javascript--strict-operators"></a><a name="6.4"></a>
- **[6.4](#javascript--strict-operators) What is the difference between `==` and `===` in JS?**
  ```
  `===` is known as a strict operator. The key difference between `==` and `===` is that the
  strict operator matches for both value and type, as opposed to just the value.
  ```

  ```javascript
  // Example of comparators
  0 == false; // true
  0 === false; // false

  2 == '2'; // true
  2 === '2'; // false
  ```

<a name="javascript--null-undefined"></a><a name="6.5"></a>
- **[6.5](#javascript--null-undefined) What is the difference between `null` and `undefined`**

  ```
  In Javascript, null is an assignment value, and can be assigned to a variable representing that
  it has no value. Undefined, on the other hand, represents that a variable has been declared but
  there is no value associated with it
  ```

<a name="javascript--difference-inheritance"></a><a name="6.6"></a>
- **[6.6](#javascript--difference-inheritance) How does `prototypal inheritance` differ from `classical inheritance`**

  ```
  In classical inheritance, classes are immutable, may or may not support multiple
  inheritance, and may contain interfaces, final classes, and abstract classes. In contrast,
  prototypes are much more flexible in the sense that they may be mutable or immutable. The object
  may inherit from multiple prototypes, and only contains objects.
  ```

**[⬆ back to top](#table-of-contents)**

---
title: JavaScript Questions
---

Answers to [Front-end Job Interview Questions - JS Questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/src/questions/javascript-questions.md). Pull requests for suggestions and corrections are welcome!

## Table of Contents

- [Explain event delegation](#explain-event-delegation)
- [Explain how `this` works in JavaScript](#explain-how-this-works-in-javascript)
- [Explain how prototypal inheritance works](#explain-how-prototypal-inheritance-works)
- [What do you think of AMD vs CommonJS?](#what-do-you-think-of-amd-vs-commonjs)
- [Explain why the following doesn't work as an IIFE: `function foo(){ }();`. What needs to be changed to properly make it an IIFE?](#explain-why-the-following-doesnt-work-as-an-iife-function-foo--what-needs-to-be-changed-to-properly-make-it-an-iife)
- [What's the difference between a variable that is: `null`, `undefined` or undeclared? How would you go about checking for any of these states?](#whats-the-difference-between-a-variable-that-is-null-undefined-or-undeclared-how-would-you-go-about-checking-for-any-of-these-states)
- [What is a closure, and how/why would you use one?](#what-is-a-closure-and-howwhy-would-you-use-one)
- [Can you describe the main difference between a `.forEach` loop and a `.map()` loop and why you would pick one versus the other?](#can-you-describe-the-main-difference-between-a-foreach-loop-and-a-map-loop-and-why-you-would-pick-one-versus-the-other)
- [What's a typical use case for anonymous functions?](#whats-a-typical-use-case-for-anonymous-functions)
- [How do you organize your code? (module pattern, classical inheritance?)](#how-do-you-organize-your-code-module-pattern-classical-inheritance)
- [What's the difference between host objects and native objects?](#whats-the-difference-between-host-objects-and-native-objects)
- [Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?](#difference-between-function-person-var-person--person-and-var-person--new-person)
- [What's the difference between `.call` and `.apply`?](#whats-the-difference-between-call-and-apply)
- [Explain `Function.prototype.bind`.](#explain-functionprototypebind)
- [When would you use `document.write()`?](#when-would-you-use-documentwrite)
- [What's the difference between feature detection, feature inference, and using the UA string?](#whats-the-difference-between-feature-detection-feature-inference-and-using-the-ua-string)
- [Explain Ajax in as much detail as possible.](#explain-ajax-in-as-much-detail-as-possible)
- [What are the advantages and disadvantages of using Ajax?](#what-are-the-advantages-and-disadvantages-of-using-ajax)
- [Explain how JSONP works (and how it's not really Ajax).](#explain-how-jsonp-works-and-how-its-not-really-ajax)
- [Have you ever used JavaScript templating? If so, what libraries have you used?](#have-you-ever-used-javascript-templating-if-so-what-libraries-have-you-used)
- [Explain "hoisting".](#explain-hoisting)
- [Describe event bubbling.](#describe-event-bubbling)
- [What's the difference between an "attribute" and a "property"?](#whats-the-difference-between-an-attribute-and-a-property)
- [Why is extending built-in JavaScript objects not a good idea?](#why-is-extending-built-in-javascript-objects-not-a-good-idea)
- [Difference between document `load` event and document `DOMContentLoaded` event?](#difference-between-document-load-event-and-document-domcontentloaded-event)
- [What is the difference between `==` and `===`?](#what-is-the-difference-between--and-)
- [Explain the same-origin policy with regards to JavaScript.](#explain-the-same-origin-policy-with-regards-to-javascript)
- [Make this work: `duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]`](#make-this-work)
- [Why is it called a Ternary expression, what does the word "Ternary" indicate?](#why-is-it-called-a-ternary-expression-what-does-the-word-ternary-indicate)
- [What is "use strict";? what are the advantages and disadvantages to using it?](#what-is-use-strict-what-are-the-advantages-and-disadvantages-to-using-it)
- [Create a for loop that iterates up to 100 while outputting "fizz" at multiples of 3, "buzz" at multiples of 5 and "fizzbuzz" at multiples of 3 and 5](#create-a-for-loop-that-iterates-up-to-100-while-outputting-fizz-at-multiples-of-3-buzz-at-multiples-of-5-and-fizzbuzz-at-multiples-of-3-and-5)
- [Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?](#why-is-it-in-general-a-good-idea-to-leave-the-global-scope-of-a-website-as-is-and-never-touch-it)
- [Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?](#why-would-you-use-something-like-the-load-event-does-this-event-have-disadvantages-do-you-know-any-alternatives-and-why-would-you-use-those)
- [Explain what a single page app is and how to make one SEO-friendly.](#explain-what-a-single-page-app-is-and-how-to-make-one-seo-friendly)
- [What is the extent of your experience with Promises and/or their polyfills?](#what-is-the-extent-of-your-experience-with-promises-andor-their-polyfills)
- [What are the pros and cons of using Promises instead of callbacks?](#what-are-the-pros-and-cons-of-using-promises-instead-of-callbacks)
- [What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?](#what-are-some-of-the-advantagesdisadvantages-of-writing-javascript-code-in-a-language-that-compiles-to-javascript)
- [What tools and techniques do you use debugging JavaScript code?](#what-tools-and-techniques-do-you-use-for-debugging-javascript-code)
- [What language constructions do you use for iterating over object properties and array items?](#what-language-constructions-do-you-use-for-iterating-over-object-properties-and-array-items)
- [Explain the difference between mutable and immutable objects.](#explain-the-difference-between-mutable-and-immutable-objects)
- [Explain the difference between synchronous and asynchronous functions.](#explain-the-difference-between-synchronous-and-asynchronous-functions)
- [What is event loop? What is the difference between call stack and task queue?](#what-is-event-loop-what-is-the-difference-between-call-stack-and-task-queue)
- [Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`](#explain-the-differences-on-the-usage-of-foo-between-function-foo--and-var-foo--function-)
- [What are the differences between variables created using `let`, `var` or `const`?](#what-are-the-differences-between-variables-created-using-let-var-or-const)
- [What are the differences between ES6 class and ES5 function constructors?](#what-are-the-differences-between-es6-class-and-es5-function-constructors)
- [Can you offer a use case for the new arrow => function syntax? How does this new syntax differ from other functions?](#can-you-offer-a-use-case-for-the-new-arrow--function-syntax-how-does-this-new-syntax-differ-from-other-functions)
- [What advantage is there for using the arrow syntax for a method in a constructor?](#what-advantage-is-there-for-using-the-arrow-syntax-for-a-method-in-a-constructor)
- [What is the definition of a higher-order function?](#what-is-the-definition-of-a-higher-order-function)
- [Can you give an example for destructuring an object or an array?](#can-you-give-an-example-for-destructuring-an-object-or-an-array)
- [ES6 Template Literals offer a lot of flexibility in generating strings, can you give an example?](#es6-template-literals-offer-a-lot-of-flexibility-in-generating-strings-can-you-give-an-example)
- [Can you give an example of a curry function and why this syntax offers an advantage?](#can-you-give-an-example-of-a-curry-function-and-why-this-syntax-offers-an-advantage)
- [What are the benefits of using spread syntax and how is it different from rest syntax?](#what-are-the-benefits-of-using-spread-syntax-and-how-is-it-different-from-rest-syntax)
- [How can you share code between files?](#how-can-you-share-code-between-files)
- [Why you might want to create static class members?](#why-you-might-want-to-create-static-class-members)

### Explain event delegation

Event delegation is a technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant elements due to event bubbling up the DOM. The benefits of this technique are:

- Memory footprint goes down because only one single handler is needed on the parent element, rather than having to attach event handlers on each descendant.
- There is no need to unbind the handler from elements that are removed and to bind the event for new elements.

###### References

- https://davidwalsh.name/event-delegate
- https://stackoverflow.com/questions/1687296/what-is-dom-event-delegation

[[↑] Back to top](#table-of-contents)

### Explain how `this` works in JavaScript

There's no simple explanation for `this`; it is one of the most confusing concepts in JavaScript. A hand-wavey explanation is that the value of `this` depends on how the function is called. I have read many explanations on `this` online, and I found [Arnav Aggrawal](https://medium.com/@arnav_aggarwal)'s explanation to be the clearest. The following rules are applied:

1. If the `new` keyword is used when calling the function, `this` inside the function is a brand new object.
2. If `apply`, `call`, or `bind` are used to call/create a function, `this` inside the function is the object that is passed in as the argument.
3. If a function is called as a method, such as `obj.method()` — `this` is the object that the function is a property of.
4. If a function is invoked as a free function invocation, meaning it was invoked without any of the conditions present above, `this` is the global object. In a browser, it is the `window` object. If in strict mode (`'use strict'`), `this` will be `undefined` instead of the global object.
5. If multiple of the above rules apply, the rule that is higher wins and will set the `this` value.
6. If the function is an ES2015 arrow function, it ignores all the rules above and receives the `this` value of its surrounding scope at the time it is created.

For an in-depth explanation, do check out his [article on Medium](https://codeburst.io/the-simple-rules-to-this-in-javascript-35d97f31bde3).

#### Can you give an example of one of the ways that working with this has changed in ES6?

ES6 allows you to use [arrow functions](http://2ality.com/2017/12/alternate-this.html#arrow-functions) which uses the [enclosing lexical scope](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#No_separate_this). This is usually convenient, but does prevent the caller from controlling context via `.call` or `.apply`—the consequences being that a library such as `jQuery` will not properly bind `this` in your event handler functions. Thus, it's important to keep this in mind when refactoring large legacy applications.

###### References

- https://codeburst.io/the-simple-rules-to-this-in-javascript-35d97f31bde3
- https://stackoverflow.com/a/3127440/1751946

[[↑] Back to top](#table-of-contents)

### Explain how prototypal inheritance works

This is an extremely common JavaScript interview question. All JavaScript objects have a `__proto__` property, that is a reference to another object, which is called the object's "prototype". When a property is accessed on an object and if the property is not found on that object, the JavaScript engine looks at the object's `__proto__`, and the `__proto__`'s `__proto__` and so on, until it finds the property defined on one of the `__proto__`s or until it reaches the end of the prototype chain. This behavior simulates classical inheritance, but it is really more of [delegation than inheritance](https://davidwalsh.name/javascript-objects).

#### Example of Prototypal Inheritance

We already have a build-in `Object.create`, but if you were to provide a polyfill for it, that might look like:

```js
if (typeof Object.create !== 'function') {
  Object.create = function (parent) {
    function Tmp() {}
    Tmp.prototype = parent;
    return new Tmp();
  };
}

const Parent = function () {
  this.name = 'Parent';
};

Parent.prototype.greet = function () {
  console.log('hello from Parent');
};

const child = Object.create(Parent.prototype);

child.cry = function () {
  console.log('waaaaaahhhh!');
};

child.cry();
// Outputs: waaaaaahhhh!

child.greet();
// Outputs: hello from Parent
```

Things to note are:

- `.greet` is not defined on the _child_, so the engine goes up the prototype chain and finds `.greet` off the inherited from _Parent_.
- We need to call `Object.create` in one of following ways for the prototype methods to be inherited:
  - Object.create(Parent.prototype);
  - Object.create(new Parent(null));
  - Object.create(objLiteral);
  - Currently, `child.constructor` is pointing to the `Parent`:

```js
child.constructor
ƒ () {
  this.name = "Parent";
}
child.constructor.name
"Parent"
```

- If we'd like to correct this, one option would be to do:

```js
function Child() {
  Parent.call(this);
  this.name = 'child';
}

Child.prototype = Parent.prototype;
Child.prototype.constructor = Child;

const c = new Child();

c.cry();
// Outputs: waaaaaahhhh!

c.greet();
// Outputs: hello from Parent

c.constructor.name;
// Outputs: "Child"
```

###### References

- http://dmitrysoshnikov.com/ecmascript/javascript-the-core/
- https://www.quora.com/What-is-prototypal-inheritance/answer/Kyle-Simpson
- https://davidwalsh.name/javascript-objects
- https://crockford.com/javascript/prototypal.html
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain

[[↑] Back to top](#table-of-contents)

### What do you think of AMD vs CommonJS?

Both are ways to implement a module system, which was not natively present in JavaScript until ES2015 came along. CommonJS is synchronous while AMD (Asynchronous Module Definition) is obviously asynchronous. CommonJS is designed with server-side development in mind while AMD, with its support for asynchronous loading of modules, is more intended for browsers.

I find AMD syntax to be quite verbose and CommonJS is closer to the style you would write import statements in other languages. Most of the time, I find AMD unnecessary, because if you served all your JavaScript into one concatenated bundle file, you wouldn't benefit from the async loading properties. Also, CommonJS syntax is closer to Node style of writing modules and there is less context-switching overhead when switching between client side and server side JavaScript development.

I'm glad that with ES2015 modules, that has support for both synchronous and asynchronous loading, we can finally just stick to one approach. Although it hasn't been fully rolled out in browsers and in Node, we can always use transpilers to convert our code.

###### References

- https://auth0.com/blog/javascript-module-systems-showdown/
- https://stackoverflow.com/questions/16521471/relation-between-commonjs-amd-and-requirejs

[[↑] Back to top](#table-of-contents)

### Explain why the following doesn't work as an IIFE: `function foo(){ }();`. What needs to be changed to properly make it an IIFE?

IIFE stands for Immediately Invoked Function Expressions. The JavaScript parser reads `function foo(){ }();` as `function foo(){ }` and `();`, where the former is a _function declaration_ and the latter (a pair of parentheses) is an attempt at calling a function but there is no name specified, hence it throws `Uncaught SyntaxError: Unexpected token )`.

Here are two ways to fix it that involves adding more parentheses: `(function foo(){ })()` and `(function foo(){ }())`. Statements that begin with `function` are considered to be _function declarations_; by wrapping this function within `()`, it becomes a _function expression_ which can then be executed with the subsequent `()`. These functions are not exposed in the global scope and you can even omit its name if you do not need to reference itself within the body.

You might also use `void` operator: `void function foo(){ }();`. Unfortunately, there is one issue with such approach. The evaluation of given expression is always `undefined`, so if your IIFE function returns anything, you can't use it. An example:

```js
const foo = void (function bar() {
  return 'foo';
})();

console.log(foo); // undefined
```

###### References

- http://lucybain.com/blog/2014/immediately-invoked-function-expression/
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/void

[[↑] Back to top](#table-of-contents)

### What's the difference between a variable that is: `null`, `undefined` or undeclared? How would you go about checking for any of these states?

**Undeclared** variables are created when you assign a value to an identifier that is not previously created using `var`, `let` or `const`. Undeclared variables will be defined globally, outside of the current scope. In strict mode, a `ReferenceError` will be thrown when you try to assign to an undeclared variable. Undeclared variables are bad just like how global variables are bad. Avoid them at all cost! To check for them, wrap its usage in a `try`/`catch` block.

```js
function foo() {
  x = 1; // Throws a ReferenceError in strict mode
}

foo();
console.log(x); // 1
```

A variable that is `undefined` is a variable that has been declared, but not assigned a value. It is of type `undefined`. If a function does not return any value as the result of executing it is assigned to a variable, the variable also has the value of `undefined`. To check for it, compare using the strict equality (`===`) operator or `typeof` which will give the `'undefined'` string. Note that you should not be using the abstract equality operator to check, as it will also return `true` if the value is `null`.

```js
var foo;
console.log(foo); // undefined
console.log(foo === undefined); // true
console.log(typeof foo === 'undefined'); // true

console.log(foo == null); // true. Wrong, don't use this to check!

function bar() {}
var baz = bar();
console.log(baz); // undefined
```

A variable that is `null` will have been explicitly assigned to the `null` value. It represents no value and is different from `undefined` in the sense that it has been explicitly assigned. To check for `null,` simply compare using the strict equality operator. Note that like the above, you should not be using the abstract equality operator (`==`) to check, as it will also return `true` if the value is `undefined`.

```js
var foo = null;
console.log(foo === null); // true
console.log(typeof foo === 'object'); // true

console.log(foo == undefined); // true. Wrong, don't use this to check!
```

As a personal habit, I never leave my variables undeclared or unassigned. I will explicitly assign `null` to them after declaring if I don't intend to use it yet. If you use a linter in your workflow, it will usually also be able to check that you are not referencing undeclared variables.

###### References

- https://stackoverflow.com/questions/15985875/effect-of-declared-and-undeclared-variables
- https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/undefined

[[↑] Back to top](#table-of-contents)

### What is a closure, and how/why would you use one?

A closure is the combination of a function and the lexical environment within which that function was declared. The word "lexical" refers to the fact that lexical scoping uses the location where a variable is declared within the source code to determine where that variable is available. Closures are functions that have access to the outer (enclosing) function's variables—scope chain even after the outer function has returned.

**Why would you use one?**

- Data privacy / emulating private methods with closures. Commonly used in the [module pattern](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#modulepatternjavascript).
- [Partial applications or currying](https://medium.com/javascript-scene/curry-or-partial-application-8150044c78b8#.l4b6l1i3x).

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures
- https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36

[[↑] Back to top](#table-of-contents)

### Can you describe the main difference between a `.forEach` loop and a `.map()` loop and why you would pick one versus the other?

To understand the differences between the two, let's look at what each function does.

**`forEach`**

- Iterates through the elements in an array.
- Executes a callback for each element.
- Does not return a value.

```js
const a = [1, 2, 3];
const doubled = a.forEach((num, index) => {
  // Do something with num and/or index.
});

// doubled = undefined
```

**`map`**

- Iterates through the elements in an array.
- "Maps" each element to a new element by calling the function on each element, creating a new array as a result.

```js
const a = [1, 2, 3];
const doubled = a.map((num) => {
  return num * 2;
});

// doubled = [2, 4, 6]
```

The main difference between `.forEach` and `.map()` is that `.map()` returns a new array. If you need the result, but do not wish to mutate the original array, `.map()` is the clear choice. If you simply need to iterate over an array, `forEach` is a fine choice.

###### References

- https://codeburst.io/javascript-map-vs-foreach-f38111822c0f

[[↑] Back to top](#table-of-contents)

### What's a typical use case for anonymous functions?

They can be used in IIFEs to encapsulate some code within a local scope so that variables declared in it do not leak to the global scope.

```js
(function () {
  // Some code here.
})();
```

As a callback that is used once and does not need to be used anywhere else. The code will seem more self-contained and readable when handlers are defined right inside the code calling them, rather than having to search elsewhere to find the function body.

```js
setTimeout(function () {
  console.log('Hello world!');
}, 1000);
```

Arguments to functional programming constructs or Lodash (similar to callbacks).

```js
const arr = [1, 2, 3];
const double = arr.map(function (el) {
  return el * 2;
});
console.log(double); // [2, 4, 6]
```

###### References

- https://www.quora.com/What-is-a-typical-usecase-for-anonymous-functions
- https://stackoverflow.com/questions/10273185/what-are-the-benefits-to-using-anonymous-functions-instead-of-named-functions-fo

[[↑] Back to top](#table-of-contents)

### How do you organize your code? (module pattern, classical inheritance?)

In the past, I've used Backbone for my models which encourages a more OOP approach, creating Backbone models and attaching methods to them.

The module pattern is still great, but these days, I use React/Redux which utilize a single-directional data flow based on Flux architecture. I would represent my app's models using plain objects and write utility pure functions to manipulate these objects. State is manipulated using actions and reducers like in any other Redux application.

I avoid using classical inheritance where possible. When and if I do, I stick to [these rules](https://medium.com/@dan_abramov/how-to-use-classes-and-sleep-at-night-9af8de78ccb4).

[[↑] Back to top](#table-of-contents)

### What's the difference between host objects and native objects?

Native objects are objects that are part of the JavaScript language defined by the ECMAScript specification, such as `String`, `Math`, `RegExp`, `Object`, `Function`, etc.

Host objects are provided by the runtime environment (browser or Node), such as `window`, `XMLHTTPRequest`, etc.

###### References

- https://stackoverflow.com/questions/7614317/what-is-the-difference-between-native-objects-and-host-objects

[[↑] Back to top](#table-of-contents)

### Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?

This question is pretty vague. My best guess at its intention is that it is asking about constructors in JavaScript. Technically speaking, `function Person(){}` is just a normal function declaration. The convention is to use PascalCase for functions that are intended to be used as constructors.

`var person = Person()` invokes the `Person` as a function, and not as a constructor. Invoking as such is a common mistake if the function is intended to be used as a constructor. Typically, the constructor does not return anything, hence invoking the constructor like a normal function will return `undefined` and that gets assigned to the variable intended as the instance.

`var person = new Person()` creates an instance of the `Person` object using the `new` operator, which inherits from `Person.prototype`. An alternative would be to use `Object.create`, such as: `Object.create(Person.prototype)`.

```js
function Person(name) {
  this.name = name;
}

var person = Person('John');
console.log(person); // undefined
console.log(person.name); // Uncaught TypeError: Cannot read property 'name' of undefined

var person = new Person('John');
console.log(person); // Person { name: "John" }
console.log(person.name); // "john"
```

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new

[[↑] Back to top](#table-of-contents)

### What's the difference between `.call` and `.apply`?

Both `.call` and `.apply` are used to invoke functions and the first parameter will be used as the value of `this` within the function. However, `.call` takes in comma-separated arguments as the next arguments while `.apply` takes in an array of arguments as the next argument. An easy way to remember this is C for `call` and comma-separated and A for `apply` and an array of arguments.

```js
function add(a, b) {
  return a + b;
}

console.log(add.call(null, 1, 2)); // 3
console.log(add.apply(null, [1, 2])); // 3
```

[[↑] Back to top](#table-of-contents)

### Explain `Function.prototype.bind`.

Taken word-for-word from [MDN](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Function/bind):

> The `bind()` method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

In my experience, it is most useful for binding the value of `this` in methods of classes that you want to pass into other functions. This is frequently done in React components.

###### References

- https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Function/bind

[[↑] Back to top](#table-of-contents)

### When would you use `document.write()`?

`document.write()` writes a string of text to a document stream opened by `document.open()`. When `document.write()` is executed after the page has loaded, it will call `document.open` which clears the whole document (`<head>` and `<body>` removed!) and replaces the contents with the given parameter value. Hence it is usually considered dangerous and prone to misuse.

There are some answers online that explain `document.write()` is being used in analytics code or [when you want to include styles that should only work if JavaScript is enabled](https://www.quirksmode.org/blog/archives/2005/06/three_javascrip_1.html). It is even being used in HTML5 boilerplate to [load scripts in parallel and preserve execution order](https://github.com/paulirish/html5-boilerplate/wiki/Script-Loading-Techniques#documentwrite-script-tag)! However, I suspect those reasons might be outdated and in the modern day, they can be achieved without using `document.write()`. Please do correct me if I'm wrong about this.

###### References

- https://www.quirksmode.org/blog/archives/2005/06/three_javascrip_1.html
- https://github.com/h5bp/html5-boilerplate/wiki/Script-Loading-Techniques#documentwrite-script-tag

[[↑] Back to top](#table-of-contents)

### What's the difference between feature detection, feature inference, and using the UA string?

**Feature Detection**

Feature detection involves working out whether a browser supports a certain block of code, and running different code depending on whether it does (or doesn't), so that the browser can always provide a working experience rather crashing/erroring in some browsers. For example:

```js
if ('geolocation' in navigator) {
  // Can use navigator.geolocation
} else {
  // Handle lack of feature
}
```

[Modernizr](https://modernizr.com/) is a great library to handle feature detection.

**Feature Inference**

Feature inference checks for a feature just like feature detection, but uses another function because it assumes it will also exist, e.g.:

```js
if (document.getElementsByTagName) {
  element = document.getElementById(id);
}
```

This is not really recommended. Feature detection is more foolproof.

**UA String**

This is a browser-reported string that allows the network protocol peers to identify the application type, operating system, software vendor or software version of the requesting software user agent. It can be accessed via `navigator.userAgent`. However, the string is tricky to parse and can be spoofed. For example, Chrome reports both as Chrome and Safari. So to detect Safari you have to check for the Safari string and the absence of the Chrome string. Avoid this method.

###### References

- https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection
- https://stackoverflow.com/questions/20104930/whats-the-difference-between-feature-detection-feature-inference-and-using-th
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Browser_detection_using_the_user_agent

[[↑] Back to top](#table-of-contents)

### Explain Ajax in as much detail as possible.

Ajax (asynchronous JavaScript and XML) is a set of web development techniques using many web technologies on the client side to create asynchronous web applications. With Ajax, web applications can send data to and retrieve from a server asynchronously (in the background) without interfering with the display and behavior of the existing page. By decoupling the data interchange layer from the presentation layer, Ajax allows for web pages, and by extension web applications, to change content dynamically without the need to reload the entire page. In practice, modern implementations commonly use JSON instead of XML, due to the advantages of JSON being native to JavaScript.

The `XMLHttpRequest` API is frequently used for the asynchronous communication or these days, the `fetch` API.

###### References

- https://en.wikipedia.org/wiki/Ajax_(programming)
- https://developer.mozilla.org/en-US/docs/AJAX

[[↑] Back to top](#table-of-contents)

### What are the advantages and disadvantages of using Ajax?

**Advantages**

- Better interactivity. New content from the server can be changed dynamically without the need to reload the entire page.
- Reduce connections to the server since scripts and stylesheets only have to be requested once.
- State can be maintained on a page. JavaScript variables and DOM state will persist because the main container page was not reloaded.
- Basically most of the advantages of an SPA.

**Disadvantages**

- Dynamic webpages are harder to bookmark.
- Does not work if JavaScript has been disabled in the browser.
- Some webcrawlers do not execute JavaScript and would not see content that has been loaded by JavaScript.
- Webpages using Ajax to fetch data will likely have to combine the fetched remote data with client-side templates to update the DOM. For this to happen, JavaScript will have to be parsed and executed on the browser, and low-end mobile devices might struggle with this.
- Basically most of the disadvantages of an SPA.

[[↑] Back to top](#table-of-contents)

### Explain how JSONP works (and how it's not really Ajax).

JSONP (JSON with Padding) is a method commonly used to bypass the cross-domain policies in web browsers because Ajax requests from the current page to a cross-origin domain is not allowed.

JSONP works by making a request to a cross-origin domain via a `<script>` tag and usually with a `callback` query parameter, for example: `https://example.com?callback=printData`. The server will then wrap the data within a function called `printData` and return it to the client.

```html
<!-- https://mydomain.com -->
<script>
  function printData(data) {
    console.log(`My name is ${data.name}!`);
  }
</script>

<script src="https://example.com?callback=printData"></script>
```

```js
// File loaded from https://example.com?callback=printData
printData({name: 'Yang Shun'});
```

The client has to have the `printData` function in its global scope and the function will be executed by the client when the response from the cross-origin domain is received.

JSONP can be unsafe and has some security implications. As JSONP is really JavaScript, it can do everything else JavaScript can do, so you need to trust the provider of the JSONP data.

These days, [CORS](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing) is the recommended approach and JSONP is seen as a hack.

###### References

- https://stackoverflow.com/a/2067584/1751946

[[↑] Back to top](#table-of-contents)

### Have you ever used JavaScript templating? If so, what libraries have you used?

Yes. Handlebars, Underscore, Lodash, AngularJS, and JSX. I disliked templating in AngularJS because it made heavy use of strings in the directives and typos would go uncaught. JSX is my new favorite as it is closer to JavaScript and there is barely any syntax to learn. Nowadays, you can even use ES2015 template string literals as a quick way for creating templates without relying on third-party code.

```js
const template = `<div>My name is: ${name}</div>`;
```

However, do be aware of a potential XSS in the above approach as the contents are not escaped for you, unlike in templating libraries.

[[↑] Back to top](#table-of-contents)

### Explain "hoisting".

Hoisting is a term used to explain the behavior of variable declarations in your code. Variables declared or initialized with the `var` keyword will have their declaration "moved" up to the top of their module/function-level scope, which we refer to as hoisting. However, only the declaration is hoisted, the assignment (if there is one), will stay where it is.

Note that the declaration is not actually moved - the JavaScript engine parses the declarations during compilation and becomes aware of declarations and their scopes. It is just easier to understand this behavior by visualizing the declarations as being hoisted to the top of their scope. Let's explain with a few examples.

```js
console.log(foo); // undefined
var foo = 1;
console.log(foo); // 1
```

Function declarations have the body hoisted while the function expressions (written in the form of variable declarations) only has the variable declaration hoisted.

```js
// Function Declaration
console.log(foo); // [Function: foo]
foo(); // 'FOOOOO'
function foo() {
  console.log('FOOOOO');
}
console.log(foo); // [Function: foo]

// Function Expression
console.log(bar); // undefined
bar(); // Uncaught TypeError: bar is not a function
var bar = function () {
  console.log('BARRRR');
};
console.log(bar); // [Function: bar]
```

Variables declared via `let` and `const` are hoisted as well. However, unlike `var` and `function`, they are not initialized and accessing them before the declaration will result in a `ReferenceError` exception. The variable is in a "temporal dead zone" from the start of the block until the declaration is processed.

```js
x; // undefined
y; // Reference error: y is not defined

var x = 'local';
let y = 'local';
```

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_Types#Variable_hoisting
- https://stackoverflow.com/questions/31219420/are-variables-declared-with-let-or-const-not-hoisted-in-es6/31222689#31222689

[[↑] Back to top](#table-of-contents)

### Describe event bubbling.

When an event triggers on a DOM element, it will attempt to handle the event if there is a listener attached, then the event is bubbled up to its parent and the same thing happens. This bubbling occurs up the element's ancestors all the way to the `document`. Event bubbling is the mechanism behind event delegation.

[[↑] Back to top](#table-of-contents)

### What's the difference between an "attribute" and a "property"?

Attributes are defined on the HTML markup but properties are defined on the DOM. To illustrate the difference, imagine we have this text field in our HTML: `<input type="text" value="Hello">`.

```js
const input = document.querySelector('input');
console.log(input.getAttribute('value')); // Hello
console.log(input.value); // Hello
```

But after you change the value of the text field by adding "World!" to it, this becomes:

```js
console.log(input.getAttribute('value')); // Hello
console.log(input.value); // Hello World!
```

###### References

- https://stackoverflow.com/questions/6003819/properties-and-attributes-in-html

[[↑] Back to top](#table-of-contents)

### Why is extending built-in JavaScript objects not a good idea?

Extending a built-in/native JavaScript object means adding properties/functions to its `prototype`. While this may seem like a good idea at first, it is dangerous in practice. Imagine your code uses a few libraries that both extend the `Array.prototype` by adding the same `contains` method, the implementations will overwrite each other and your code will break if the behavior of these two methods is not the same.

The only time you may want to extend a native object is when you want to create a polyfill, essentially providing your own implementation for a method that is part of the JavaScript specification but might not exist in the user's browser due to it being an older browser.

###### References

- http://lucybain.com/blog/2014/js-extending-built-in-objects/

[[↑] Back to top](#table-of-contents)

### Difference between document `load` event and document `DOMContentLoaded` event?

The `DOMContentLoaded` event is fired when the initial HTML document has been completely loaded and parsed, without waiting for stylesheets, images, and subframes to finish loading.

`window`'s `load` event is only fired after the DOM and all dependent resources and assets have loaded.

###### References

- https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded
- https://developer.mozilla.org/en-US/docs/Web/Events/load

[[↑] Back to top](#table-of-contents)

### What is the difference between `==` and `===`?

`==` is the abstract equality operator while `===` is the strict equality operator. The `==` operator will compare for equality after doing any necessary type conversions. The `===` operator will not do type conversion, so if two values are not the same type `===` will simply return `false`. When using `==`, funky things can happen, such as:

```js
1 == '1'; // true
1 == [1]; // true
1 == true; // true
0 == ''; // true
0 == '0'; // true
0 == false; // true
```

My advice is never to use the `==` operator, except for convenience when comparing against `null` or `undefined`, where `a == null` will return `true` if `a` is `null` or `undefined`.

```js
var a = null;
console.log(a == null); // true
console.log(a == undefined); // true
```

###### References

- https://stackoverflow.com/questions/359494/which-equals-operator-vs-should-be-used-in-javascript-comparisons

[[↑] Back to top](#table-of-contents)

### Explain the same-origin policy with regards to JavaScript.

The same-origin policy prevents JavaScript from making requests across domain boundaries. An origin is defined as a combination of URI scheme, hostname, and port number. This policy prevents a malicious script on one page from obtaining access to sensitive data on another web page through that page's Document Object Model.

###### References

- https://en.wikipedia.org/wiki/Same-origin_policy

[[↑] Back to top](#table-of-contents)

### Make this work:

```js
duplicate([1, 2, 3, 4, 5]); // [1,2,3,4,5,1,2,3,4,5]
```

```js
function duplicate(arr) {
  return arr.concat(arr);
}

duplicate([1, 2, 3, 4, 5]); // [1,2,3,4,5,1,2,3,4,5]
```

Or with ES6:

```js
const duplicate = (arr) => [...arr, ...arr];

duplicate([1, 2, 3, 4, 5]); // [1,2,3,4,5,1,2,3,4,5]
```

[[↑] Back to top](#table-of-contents)

### Why is it called a Ternary expression, what does the word "Ternary" indicate?

"Ternary" indicates three, and a ternary expression accepts three operands, the test condition, the "then" expression and the "else" expression. Ternary expressions are not specific to JavaScript and I'm not sure why it is even in this list.

###### References

- https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Conditional_Operator

[[↑] Back to top](#table-of-contents)

### What is `"use strict";`? What are the advantages and disadvantages to using it?

'use strict' is a statement used to enable strict mode to entire scripts or individual functions. Strict mode is a way to opt into a restricted variant of JavaScript.

Advantages:

- Makes it impossible to accidentally create global variables.
- Makes assignments which would otherwise silently fail to throw an exception.
- Makes attempts to delete undeletable properties throw (where before the attempt would simply have no effect).
- Requires that function parameter names be unique.
- `this` is undefined in the global context.
- It catches some common coding bloopers, throwing exceptions.
- It disables features that are confusing or poorly thought out.

Disadvantages:

- Many missing features that some developers might be used to.
- No more access to `function.caller` and `function.arguments`.
- Concatenation of scripts written in different strict modes might cause issues.

Overall, I think the benefits outweigh the disadvantages, and I never had to rely on the features that strict mode blocks. I would recommend using strict mode.

###### References

- http://2ality.com/2011/10/strict-mode-hatred.html
- http://lucybain.com/blog/2014/js-use-strict/

[[↑] Back to top](#table-of-contents)

### Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`.

Check out this version of FizzBuzz by [Paul Irish](https://gist.github.com/jaysonrowe/1592432#gistcomment-790724).

```js
for (let i = 1; i <= 100; i++) {
  let f = i % 3 == 0,
    b = i % 5 == 0;
  console.log(f ? (b ? 'FizzBuzz' : 'Fizz') : b ? 'Buzz' : i);
}
```

I would not advise you to write the above during interviews though. Just stick with the long but clear approach. For more wacky versions of FizzBuzz, check out the reference link below.

###### References

- https://gist.github.com/jaysonrowe/1592432

[[↑] Back to top](#table-of-contents)

### Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?

Every script has access to the global scope, and if everyone uses the global namespace to define their variables, collisions will likely occur. Use the module pattern (IIFEs) to encapsulate your variables within a local namespace.

[[↑] Back to top](#table-of-contents)

### Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?

The `load` event fires at the end of the document loading process. At this point, all of the objects in the document are in the DOM, and all the images, scripts, links and sub-frames have finished loading.

The DOM event `DOMContentLoaded` will fire after the DOM for the page has been constructed, but do not wait for other resources to finish loading. This is preferred in certain cases when you do not need the full page to be loaded before initializing.

TODO.

###### References

- https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers/onload

[[↑] Back to top](#table-of-contents)

### Explain what a single page app is and how to make one SEO-friendly.

The below is taken from the awesome [Grab Front End Guide](https://github.com/grab/front-end-guide), which coincidentally, is written by me!

Web developers these days refer to the products they build as web apps, rather than websites. While there is no strict difference between the two terms, web apps tend to be highly interactive and dynamic, allowing the user to perform actions and receive a response to their action. Traditionally, the browser receives HTML from the server and renders it. When the user navigates to another URL, a full-page refresh is required and the server sends fresh new HTML to the new page. This is called server-side rendering.

However, in modern SPAs, client-side rendering is used instead. The browser loads the initial page from the server, along with the scripts (frameworks, libraries, app code) and stylesheets required for the whole app. When the user navigates to other pages, a page refresh is not triggered. The URL of the page is updated via the [HTML5 History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API). New data required for the new page, usually in JSON format, is retrieved by the browser via [AJAX](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started) requests to the server. The SPA then dynamically updates the page with the data via JavaScript, which it has already downloaded in the initial page load. This model is similar to how native mobile apps work.

The benefits:

- The app feels more responsive and users do not see the flash between page navigations due to full-page refreshes.
- Fewer HTTP requests are made to the server, as the same assets do not have to be downloaded again for each page load.
- Clear separation of the concerns between the client and the server; you can easily build new clients for different platforms (e.g. mobile, chatbots, smart watches) without having to modify the server code. You can also modify the technology stack on the client and server independently, as long as the API contract is not broken.

The downsides:

- Heavier initial page load due to the loading of framework, app code, and assets required for multiple pages.
- There's an additional step to be done on your server which is to configure it to route all requests to a single entry point and allow client-side routing to take over from there.
- SPAs are reliant on JavaScript to render content, but not all search engines execute JavaScript during crawling, and they may see empty content on your page. This inadvertently hurts the Search Engine Optimization (SEO) of your app. However, most of the time, when you are building apps, SEO is not the most important factor, as not all the content needs to be indexable by search engines. To overcome this, you can either server-side render your app or use services such as [Prerender](https://prerender.io/) to "render your javascript in a browser, save the static HTML, and return that to the crawlers".

###### References

- https://github.com/grab/front-end-guide#single-page-apps-spas
- http://stackoverflow.com/questions/21862054/single-page-app-advantages-and-disadvantages
- http://blog.isquaredsoftware.com/presentations/2016-10-revolution-of-web-dev/
- https://medium.freecodecamp.com/heres-why-client-side-rendering-won-46a349fadb52

[[↑] Back to top](#table-of-contents)

### What is the extent of your experience with Promises and/or their polyfills?

Possess working knowledge of it. A promise is an object that may produce a single value sometime in the future: either a resolved value or a reason that it's not resolved (e.g., a network error occurred). A promise may be in one of 3 possible states: fulfilled, rejected, or pending. Promise users can attach callbacks to handle the fulfilled value or the reason for rejection.

Some common polyfills are `$.deferred`, Q and Bluebird but not all of them comply with the specification. ES2015 supports Promises out of the box and polyfills are typically not needed these days.

###### References

- https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261

[[↑] Back to top](#table-of-contents)

### What are the pros and cons of using Promises instead of callbacks?

**Pros**

- Avoid callback hell which can be unreadable.
- Makes it easy to write sequential asynchronous code that is readable with `.then()`.
- Makes it easy to write parallel asynchronous code with `Promise.all()`.
- With promises, these scenarios which are present in callbacks-only coding, will not happen:
  - Call the callback too early
  - Call the callback too late (or never)
  - Call the callback too few or too many times
  - Fail to pass along any necessary environment/parameters
  - Swallow any errors/exceptions that may happen

**Cons**

- Slightly more complex code (debatable).
- In older browsers where ES2015 is not supported, you need to load a polyfill in order to use it.

###### References

- https://github.com/getify/You-Dont-Know-JS/blob/master/async%20%26%20performance/ch3.md

[[↑] Back to top](#table-of-contents)

### What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?

Some examples of languages that compile to JavaScript include CoffeeScript, Elm, ClojureScript, PureScript, and TypeScript.

Advantages:

- Fixes some of the longstanding problems in JavaScript and discourages JavaScript anti-patterns.
- Enables you to write shorter code, by providing some syntactic sugar on top of JavaScript, which I think ES5 lacks, but ES2015 is awesome.
- Static types are awesome (in the case of TypeScript) for large projects that need to be maintained over time.

Disadvantages:

- Require a build/compile process as browsers only run JavaScript and your code will need to be compiled into JavaScript before being served to browsers.
- Debugging can be a pain if your source maps do not map nicely to your pre-compiled source.
- Most developers are not familiar with these languages and will need to learn it. There's a ramp up cost involved for your team if you use it for your projects.
- Smaller community (depends on the language), which means resources, tutorials, libraries, and tooling would be harder to find.
- IDE/editor support might be lacking.
- These languages will always be behind the latest JavaScript standard.
- Developers should be cognizant of what their code is being compiled to — because that is what would actually be running, and that is what matters in the end.

Practically, ES2015 has vastly improved JavaScript and made it much nicer to write. I don't really see the need for CoffeeScript these days.

###### References

- https://softwareengineering.stackexchange.com/questions/72569/what-are-the-pros-and-cons-of-coffeescript

[[↑] Back to top](#table-of-contents)

### What tools and techniques do you use for debugging JavaScript code?

- React and Redux
  - [React Devtools](https://github.com/facebook/react-devtools)
  - [Redux Devtools](https://github.com/gaearon/redux-devtools)
- Vue
  - [Vue Devtools](https://github.com/vuejs/vue-devtools)
- JavaScript
  - [Chrome Devtools](https://hackernoon.com/twelve-fancy-chrome-devtools-tips-dc1e39d10d9d)
  - `debugger` statement
  - Good old `console.log` debugging

###### References

- https://hackernoon.com/twelve-fancy-chrome-devtools-tips-dc1e39d10d9d
- https://raygun.com/blog/javascript-debugging/

[[↑] Back to top](#table-of-contents)

### What language constructions do you use for iterating over object properties and array items?

For objects:

- `for-in` loops - `for (var property in obj) { console.log(property); }`. However, this will also iterate through its inherited properties, and you will add an `obj.hasOwnProperty(property)` check before using it.
- `Object.keys()` - `Object.keys(obj).forEach(function (property) { ... })`. `Object.keys()` is a static method that will lists all enumerable properties of the object that you pass it.
- `Object.getOwnPropertyNames()` - `Object.getOwnPropertyNames(obj).forEach(function (property) { ... })`. `Object.getOwnPropertyNames()` is a static method that will lists all enumerable and non-enumerable properties of the object that you pass it.

For arrays:

- `for` loops - `for (var i = 0; i < arr.length; i++)`. The common pitfall here is that `var` is in the function scope and not the block scope and most of the time you would want block scoped iterator variable. ES2015 introduces `let` which has block scope and it is recommended to use that instead. So this becomes: `for (let i = 0; i < arr.length; i++)`.
- `forEach` - `arr.forEach(function (el, index) { ... })`. This construct can be more convenient at times because you do not have to use the `index` if all you need is the array elements. There are also the `every` and `some` methods which will allow you to terminate the iteration early.
- `for-of` loops - `for (let elem of arr) { ... }`. ES6 introduces a new loop, the `for-of` loop, that allows you to loop over objects that conform to the [iterable protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterable_protocol) such as `String`, `Array`, `Map`, `Set`, etc. It combines the advantages of the `for` loop and the `forEach()` method. The advantage of the `for` loop is that you can break from it, and the advantage of `forEach()` is that it is more concise than the `for` loop because you don't need a counter variable. With the `for-of` loop, you get both the ability to break from a loop and a more concise syntax.

Most of the time, I would prefer the `.forEach` method, but it really depends on what you are trying to do. Before ES6, we used `for` loops when we needed to prematurely terminate the loop using `break`. But now with ES6, we can do that with `for-of` loops. I would use `for` loops when I need even more flexibility, such as incrementing the iterator more than once per loop.

Also, when using the `for-of` loop, if you need to access both the index and value of each array element, you can do so with the ES6 Array `entries()` method and destructuring:

```js
const arr = ['a', 'b', 'c'];

for (let [index, elem] of arr.entries()) {
  console.log(index, ': ', elem);
}
```

###### References

- http://2ality.com/2015/08/getting-started-es6.html#from-for-to-foreach-to-for-of
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/entries

[[↑] Back to top](#table-of-contents)

### Explain the difference between mutable and immutable objects.

Immutability is a core principle in functional programming, and has lots to offer to object-oriented programs as well. A mutable object is an object whose state can be modified after it is created. An immutable object is an object whose state cannot be modified after it is created.

#### What is an example of an immutable object in JavaScript?

In JavaScript, some built-in types (numbers, strings) are immutable, but custom objects are generally mutable.

Some built-in immutable JavaScript objects are `Math`, `Date`.

Here are a few ways to add/simulate immutability on plain JavaScript objects.

**Object Constant Properties**

By combining `writable: false` and `configurable: false`, you can essentially create a constant (cannot be changed, redefined or deleted) as an object property, like:

```js
let myObject = {};
Object.defineProperty(myObject, 'number', {
  value: 42,
  writable: false,
  configurable: false,
});
console.log(myObject.number); // 42
myObject.number = 43;
console.log(myObject.number); // 42
```

**Prevent Extensions**

If you want to prevent an object from having new properties added to it, but otherwise leave the rest of the object's properties alone, call `Object.preventExtensions(...)`:

```js
var myObject = {
  a: 2,
};

Object.preventExtensions(myObject);

myObject.b = 3;
myObject.b; // undefined
```

In non-strict mode, the creation of `b` fails silently. In strict mode, it throws a `TypeError`.

**Seal**

`Object.seal()` creates a "sealed" object, which means it takes an existing object and essentially calls `Object.preventExtensions()` on it, but also marks all its existing properties as `configurable: false`.

So, not only can you not add any more properties, but you also cannot reconfigure or delete any existing properties (though you can still modify their values).

**Freeze**

`Object.freeze()` creates a frozen object, which means it takes an existing object and essentially calls `Object.seal()` on it, but it also marks all "data accessor" properties as writable:false, so that their values cannot be changed.

This approach is the highest level of immutability that you can attain for an object itself, as it prevents any changes to the object or to any of its direct properties (though, as mentioned above, the contents of any referenced other objects are unaffected).

```js
var immutable = Object.freeze({});
```

Freezing an object does not allow new properties to be added to an object and prevents from removing or altering the existing properties. `Object.freeze()` preserves the enumerability, configurability, writability and the prototype of the object. It returns the passed object and does not create a frozen copy.

#### What are the pros and cons of immutability?

**Pros**

- Easier change detection - Object equality can be determined in a performant and easy manner through referential equality. This is useful for comparing object differences in React and Redux.
- Programs with immutable objects are less complicated to think about, since you don't need to worry about how an object may evolve over time.
- Defensive copies are no longer necessary when immutable objects are returning from or passed to functions, since there is no possibility an immutable object will be modified by it.
- Easy sharing via references - One copy of an object is just as good as another, so you can cache objects or reuse the same object multiple times.
- Thread-safe - Immutable objects can be safely used between threads in a multi-threaded environment since there is no risk of them being modified in other concurrently running threads.
- Using libraries like ImmmutableJS, objects are modified using structural sharing and less memory is needed for having multiple objects with similar structures.

**Cons**

- Naive implementations of immutable data structures and its operations can result in extremely poor performance because new objects are created each time. It is recommended to use libraries for efficient immutable data structures and operations that leverage on structural sharing.
- Allocation (and deallocation) of many small objects rather than modifying existing ones can cause a performance impact. The complexity of either the allocator or the garbage collector usually depends on the number of objects on the heap.
- Cyclic data structures such as graphs are difficult to build. If you have two objects which can't be modified after initialization, how can you get them to point to each other?

###### References

- https://stackoverflow.com/questions/1863515/pros-cons-of-immutability-vs-mutability

[[↑] Back to top](#table-of-contents)

#### How can you achieve immutability in your own code?

One way to achieve immutability is to use libraries like [immutable.js](http://facebook.github.io/immutable-js/), [mori](https://github.com/swannodette/mori) or [immer](https://github.com/immerjs/immer).

The alternative is to use `const` declarations combined with the techniques mentioned above for creation. For "mutating" objects, use the spread operator, `Object.assign`, `Array.concat()`, etc., to create new objects instead of mutate the original object.

Examples:

```js
// Array Example
const arr = [1, 2, 3];
const newArr = [...arr, 4]; // [1, 2, 3, 4]

// Object Example
const human = Object.freeze({race: 'human'});
const john = {...human, name: 'John'}; // {race: "human", name: "John"}
const alienJohn = {...john, race: 'alien'}; // {race: "alien", name: "John"}
```

###### References

- https://stackoverflow.com/questions/1863515/pros-cons-of-immutability-vs-mutability
- https://www.sitepoint.com/immutability-javascript/
- https://wecodetheweb.com/2016/02/12/immutable-javascript-using-es6-and-beyond/

[[↑] Back to top](#table-of-contents)

### Explain the difference between synchronous and asynchronous functions.

Synchronous functions are blocking while asynchronous functions are not. In synchronous functions, statements complete before the next statement is run. In this case, the program is evaluated exactly in order of the statements and execution of the program is paused if one of the statements take a very long time.

Asynchronous functions usually accept a callback as a parameter and execution continue on the next line immediately after the asynchronous function is invoked. The callback is only invoked when the asynchronous operation is complete and the call stack is empty. Heavy duty operations such as loading data from a web server or querying a database should be done asynchronously so that the main thread can continue executing other operations instead of blocking until that long operation to complete (in the case of browsers, the UI will freeze).

[[↑] Back to top](#table-of-contents)

### What is event loop? What is the difference between call stack and task queue?

The event loop is a single-threaded loop that monitors the call stack and checks if there is any work to be done in the task queue. If the call stack is empty and there are callback functions in the task queue, a function is dequeued and pushed onto the call stack to be executed.

If you haven't already checked out Philip Robert's [talk on the Event Loop](https://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html), you should. It is one of the most viewed videos on JavaScript.

###### References

- https://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html

[[↑] Back to top](#table-of-contents)

### Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`

The former is a function declaration while the latter is a function expression. The key difference is that function declarations have its body hoisted but the bodies of function expressions are not (they have the same hoisting behavior as variables). For more explanation on hoisting, refer to the question above [on hoisting](#explain-hoisting). If you try to invoke a function expression before it is defined, you will get an `Uncaught TypeError: XXX is not a function` error.

**Function Declaration**

```js
foo(); // 'FOOOOO'
function foo() {
  console.log('FOOOOO');
}
```

**Function Expression**

```js
foo(); // Uncaught TypeError: foo is not a function
var foo = function () {
  console.log('FOOOOO');
};
```

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function

[[↑] Back to top](#table-of-contents)

### What are the differences between variables created using `let`, `var` or `const`?

Variables declared using the `var` keyword are scoped to the function in which they are created, or if created outside of any function, to the global object. `let` and `const` are _block scoped_, meaning they are only accessible within the nearest set of curly braces (function, if-else block, or for-loop).

```js
function foo() {
  // All variables are accessible within functions.
  var bar = 'bar';
  let baz = 'baz';
  const qux = 'qux';

  console.log(bar); // bar
  console.log(baz); // baz
  console.log(qux); // qux
}

console.log(bar); // ReferenceError: bar is not defined
console.log(baz); // ReferenceError: baz is not defined
console.log(qux); // ReferenceError: qux is not defined
```

```js
if (true) {
  var bar = 'bar';
  let baz = 'baz';
  const qux = 'qux';
}

// var declared variables are accessible anywhere in the function scope.
console.log(bar); // bar
// let and const defined variables are not accessible outside of the block they were defined in.
console.log(baz); // ReferenceError: baz is not defined
console.log(qux); // ReferenceError: qux is not defined
```

`var` allows variables to be hoisted, meaning they can be referenced in code before they are declared. `let` and `const` will not allow this, instead throwing an error.

```js
console.log(foo); // undefined

var foo = 'foo';

console.log(baz); // ReferenceError: can't access lexical declaration 'baz' before initialization

let baz = 'baz';

console.log(bar); // ReferenceError: can't access lexical declaration 'bar' before initialization

const bar = 'bar';
```

Redeclaring a variable with `var` will not throw an error, but `let` and `const` will.

```js
var foo = 'foo';
var foo = 'bar';
console.log(foo); // "bar"

let baz = 'baz';
let baz = 'qux'; // Uncaught SyntaxError: Identifier 'baz' has already been declared
```

`let` and `const` differ in that `let` allows reassigning the variable's value while `const` does not.

```js
// This is fine.
let foo = 'foo';
foo = 'bar';

// This causes an exception.
const baz = 'baz';
baz = 'qux';
```

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const

[[↑] Back to top](#table-of-contents)

### What are the differences between ES6 class and ES5 function constructors?

Let's first look at example of each:

```js
// ES5 Function Constructor
function Person(name) {
  this.name = name;
}

// ES6 Class
class Person {
  constructor(name) {
    this.name = name;
  }
}
```

For simple constructors, they look pretty similar.

The main difference in the constructor comes when using inheritance. If we want to create a `Student` class that subclasses `Person` and add a `studentId` field, this is what we have to do in addition to the above.

```js
// ES5 Function Constructor
function Student(name, studentId) {
  // Call constructor of superclass to initialize superclass-derived members.
  Person.call(this, name);

  // Initialize subclass's own members.
  this.studentId = studentId;
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;

// ES6 Class
class Student extends Person {
  constructor(name, studentId) {
    super(name);
    this.studentId = studentId;
  }
}
```

It's much more verbose to use inheritance in ES5 and the ES6 version is easier to understand and remember.

###### References

- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance
- https://eli.thegreenplace.net/2013/10/22/classical-inheritance-in-javascript-es5

[[↑] Back to top](#table-of-contents)

### Can you offer a use case for the new arrow => function syntax? How does this new syntax differ from other functions?

One obvious benefit of arrow functions is to simplify the syntax needed to create functions, without a need for the `function` keyword. The `this` within arrow functions is also bound to the enclosing scope which is different compared to regular functions where the `this` is determined by the object calling it. Lexically-scoped `this` is useful when invoking callbacks especially in React components.

[[↑] Back to top](#table-of-contents)

### What advantage is there for using the arrow syntax for a method in a constructor?

The main advantage of using an arrow function as a method inside a constructor is that the value of `this` gets set at the time of the function creation and can't change after that. So, when the constructor is used to create a new object, `this` will always refer to that object. For example, let's say we have a `Person` constructor that takes a first name as an argument has two methods to `console.log` that name, one as a regular function and one as an arrow function:

```js
const Person = function (firstName) {
  this.firstName = firstName;
  this.sayName1 = function () {
    console.log(this.firstName);
  };
  this.sayName2 = () => {
    console.log(this.firstName);
  };
};

const john = new Person('John');
const dave = new Person('Dave');

john.sayName1(); // John
john.sayName2(); // John

// The regular function can have its 'this' value changed, but the arrow function cannot
john.sayName1.call(dave); // Dave (because "this" is now the dave object)
john.sayName2.call(dave); // John

john.sayName1.apply(dave); // Dave (because 'this' is now the dave object)
john.sayName2.apply(dave); // John

john.sayName1.bind(dave)(); // Dave (because 'this' is now the dave object)
john.sayName2.bind(dave)(); // John

var sayNameFromWindow1 = john.sayName1;
sayNameFromWindow1(); // undefined (because 'this' is now the window object)

var sayNameFromWindow2 = john.sayName2;
sayNameFromWindow2(); // John
```

The main takeaway here is that `this` can be changed for a normal function, but the context always stays the same for an arrow function. So even if you are passing around your arrow function to different parts of your application, you wouldn't have to worry about the context changing.

This can be particularly helpful in React class components. If you define a class method for something such as a click handler using a normal function, and then you pass that click handler down into a child component as a prop, you will need to also bind `this` in the constructor of the parent component. If you instead use an arrow function, there is no need to also bind "this", as the method will automatically get its "this" value from its enclosing lexical context. (See this article for an excellent demonstration and sample code: https://medium.com/@machnicki/handle-events-in-react-with-arrow-functions-ede88184bbb)

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions
- https://medium.com/@machnicki/handle-events-in-react-with-arrow-functions-ede88184bbb

[[↑] Back to top](#table-of-contents)

### What is the definition of a higher-order function?

A higher-order function is any function that takes one or more functions as arguments, which it uses to operate on some data, and/or returns a function as a result. Higher-order functions are meant to abstract some operation that is performed repeatedly. The classic example of this is `map`, which takes an array and a function as arguments. `map` then uses this function to transform each item in the array, returning a new array with the transformed data. Other popular examples in JavaScript are `forEach`, `filter`, and `reduce`. A higher-order function doesn't just need to be manipulating arrays as there are many use cases for returning a function from another function. `Function.prototype.bind` is one such example in JavaScript.

**Map**

Let say we have an array of names which we need to transform each string to uppercase.

```js
const names = ['irish', 'daisy', 'anna'];
```

The imperative way will be as such:

```js
const transformNamesToUppercase = function (names) {
  const results = [];
  for (let i = 0; i < names.length; i++) {
    results.push(names[i].toUpperCase());
  }
  return results;
};
transformNamesToUppercase(names); // ['IRISH', 'DAISY', 'ANNA']
```

Use `.map(transformerFn)` makes the code shorter and more declarative.

```js
const transformNamesToUppercase = function (names) {
  return names.map((name) => name.toUpperCase());
};
transformNamesToUppercase(names); // ['IRISH', 'DAISY', 'ANNA']
```

###### References

- https://medium.com/javascript-scene/higher-order-functions-composing-software-5365cf2cbe99
- https://hackernoon.com/effective-functional-javascript-first-class-and-higher-order-functions-713fde8df50a
- https://eloquentjavascript.net/05_higher_order.html

[[↑] Back to top](#table-of-contents)

### Can you give an example for destructuring an object or an array?

Destructuring is an expression available in ES6 which enables a succinct and convenient way to extract values of Objects or Arrays and place them into distinct variables.

**Array destructuring**

```js
// Variable assignment.
const foo = ['one', 'two', 'three'];

const [one, two, three] = foo;
console.log(one); // "one"
console.log(two); // "two"
console.log(three); // "three"
```

```js
// Swapping variables
let a = 1;
let b = 3;

[a, b] = [b, a];
console.log(a); // 3
console.log(b); // 1
```

**Object destructuring**

```js
// Variable assignment.
const o = {p: 42, q: true};
const {p, q} = o;

console.log(p); // 42
console.log(q); // true
```

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment
- https://ponyfoo.com/articles/es6-destructuring-in-depth

[[↑] Back to top](#table-of-contents)

### ES6 Template Literals offer a lot of flexibility in generating strings, can you give an example?

Template literals help make it simple to do string interpolation, or to include variables in a string. Before ES2015, it was common to do something like this:

```js
var person = {name: 'Tyler', age: 28};
console.log(
  'Hi, my name is ' + person.name + ' and I am ' + person.age + ' years old!',
);
// 'Hi, my name is Tyler and I am 28 years old!'
```

With template literals, you can now create that same output like this instead:

```js
const person = {name: 'Tyler', age: 28};
console.log(`Hi, my name is ${person.name} and I am ${person.age} years old!`);
// 'Hi, my name is Tyler and I am 28 years old!'
```

Note that you use backticks, not quotes, to indicate that you are using a template literal and that you can insert expressions inside the `${}` placeholders.

A second helpful use case is in creating multi-line strings. Before ES2015, you could create a multi-line string like this:

```js
console.log('This is line one.\nThis is line two.');
// This is line one.
// This is line two.
```

Or if you wanted to break it up into multiple lines in your code so you didn't have to scroll to the right in your text editor to read a long string, you could also write it like this:

```js
console.log('This is line one.\n' + 'This is line two.');
// This is line one.
// This is line two.
```

Template literals, however, preserve whatever spacing you add to them. For example, to create that same multi-line output that we created above, you can simply do:

```js
console.log(`This is line one.
This is line two.`);
// This is line one.
// This is line two.
```

Another use case of template literals would be to use as a substitute for templating libraries for simple variable interpolations:

```js
const person = {name: 'Tyler', age: 28};
document.body.innerHTML = `
  <div>
    <p>Name: ${person.name}</p>
    <p>Name: ${person.age}</p>
  </div>
`;
```

**Note that your code may be susceptible to XSS by using `.innerHTML`. Sanitize your data before displaying it if it came from a user!**

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals

[[↑] Back to top](#table-of-contents)

### Can you give an example of a curry function and why this syntax offers an advantage?

Currying is a pattern where a function with more than one parameter is broken into multiple functions that, when called in series, will accumulate all of the required parameters one at a time. This technique can be useful for making code written in a functional style easier to read and compose. It's important to note that for a function to be curried, it needs to start out as one function, then broken out into a sequence of functions that each accepts one parameter.

```js
function curry(fn) {
  if (fn.length === 0) {
    return fn;
  }

  function _curried(depth, args) {
    return function (newArgument) {
      if (depth - 1 === 0) {
        return fn(...args, newArgument);
      }
      return _curried(depth - 1, [...args, newArgument]);
    };
  }

  return _curried(fn.length, []);
}

function add(a, b) {
  return a + b;
}

var curriedAdd = curry(add);
var addFive = curriedAdd(5);

var result = [0, 1, 2, 3, 4, 5].map(addFive); // [5, 6, 7, 8, 9, 10]
```

###### References

- https://hackernoon.com/currying-in-js-d9ddc64f162e

[[↑] Back to top](#table-of-contents)

### What are the benefits of using spread syntax and how is it different from rest syntax?

ES6's spread syntax is very useful when coding in a functional paradigm as we can easily create copies of arrays or objects without resorting to `Object.create`, `slice`, or a library function. This language feature is used often in Redux and RxJS projects.

```js
function putDookieInAnyArray(arr) {
  return [...arr, 'dookie'];
}

const result = putDookieInAnyArray(['I', 'really', "don't", 'like']); // ["I", "really", "don't", "like", "dookie"]

const person = {
  name: 'Todd',
  age: 29,
};

const copyOfTodd = {...person};
```

ES6's rest syntax offers a shorthand for including an arbitrary number of arguments to be passed to a function. It is like an inverse of the spread syntax, taking data and stuffing it into an array rather than unpacking an array of data, and it works in function arguments, as well as in array and object destructuring assignments.

```js
function addFiveToABunchOfNumbers(...numbers) {
  return numbers.map((x) => x + 5);
}

const result = addFiveToABunchOfNumbers(4, 5, 6, 7, 8, 9, 10); // [9, 10, 11, 12, 13, 14, 15]

const [a, b, ...rest] = [1, 2, 3, 4]; // a: 1, b: 2, rest: [3, 4]

const {e, f, ...others} = {
  e: 1,
  f: 2,
  g: 3,
  h: 4,
}; // e: 1, f: 2, others: { g: 3, h: 4 }
```

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment

[[↑] Back to top](#table-of-contents)

### How can you share code between files?

This depends on the JavaScript environment.

On the client (browser environment), as long as the variables/functions are declared in the global scope (`window`), all scripts can refer to them. Alternatively, adopt the Asynchronous Module Definition (AMD) via RequireJS for a more modular approach.

On the server (Node.js), the common way has been to use CommonJS. Each file is treated as a module and it can export variables and functions by attaching them to the `module.exports` object.

ES2015 defines a module syntax which aims to replace both AMD and CommonJS. This will eventually be supported in both browser and Node environments.

[[↑] Back to top](#table-of-contents)

###### References

- http://requirejs.org/docs/whyamd.html
- https://nodejs.org/docs/latest/api/modules.html
- http://2ality.com/2014/09/es6-modules-final.html

### Why you might want to create static class members?

Static class members (properties/methods) are not tied to a specific instance of a class and have the same value regardless of which instance is referring to it. Static properties are typically configuration variables and static methods are usually pure utility functions which do not depend on the state of the instance.

###### References

- https://stackoverflow.com/questions/21155438/when-to-use-static-variables-methods-and-when-to-use-instance-variables-methods

[[↑] Back to top](#table-of-contents)

### Other Answers

- http://flowerszhong.github.io/2013/11/20/javascript-questions.html


### CSS

* [CSS interview questions and answers for freshers and experienced candidates Also there you can find CSS online practice tests to fight written tests and certification exams on CSS](http://www.careerride.com/Interview-Questions-CSS.aspx)
* [Development hiring managers and potential interviewees may find there sample CSS proficiency interview Q&As and code snippets useful](http://www.techrepublic.com/blog/software-engineer/css-interview-questions-and-answers/)
* [Interview Questions and Exercises About CSS](https://css-tricks.com/interview-questions-css/)
* [Top 50 CSS(Cascading Style Sheet) Interview Questions covering the most of tricky CSS moments](http://career.guru99.com/top-50-csscascading-style-sheet-interview-questions/)
* [CSS Questions and Answers](https://github.com/yangshun/front-end-interview-handbook/blob/master/questions/css-questions.md)

### Docker

* [Docker Interview Questions](https://mindmajix.com/docker-interview-questions)
* [Top Docker Interview Questions You Must Prepare In 2019](https://www.edureka.co/blog/interview-questions/docker-interview-questions/)
* [Top Docker Interview Questions And Answers](https://intellipaat.com/interview-question/docker-interview-questions/)
* [DOCKER (SOFTWARE) INTERVIEW QUESTIONS & ANSWERS](https://www.wisdomjobs.com/e-university/docker-software-interview-questions.html)
* [30 Docker Interview Questions and Answers in 2019](https://www.fullstack.cafe/blog/docker-interview-questions-and-answers)
* [Docker Interview Questions & Answers](https://www.interviewbit.com/docker-interview-questions/)


### HTML

* [10 Typical HTML Interview Exercises from SitePoint.com](http://www.sitepoint.com/10-typical-html-interview-exercises/)
* [16 Essential HTML5 Interview Questions from Toptal](http://www.toptal.com/html5/interview-questions)
* [40 important HTML 5 Interview questions with answers](http://www.codeproject.com/Articles/702051/important-HTML-Interview-questions-with-answe)
* [HTML interview questions and answers for freshers and experienced candidates Also find HTML online practice tests to fight written tests and certification exams on HTML](http://www.careerride.com/Interview-Questions-HTML.aspx)
* [Top 50 HTML Interview Questions for both freshers and experienced developers](http://career.guru99.com/top-50-html-interview-questions/)
* [Common HTML interview questions for freshers](http://www.javatpoint.com/html-interview-questions)
* [HTML Questions and Answers](https://github.com/yangshun/front-end-interview-handbook/blob/master/questions/html-questions.md)
* [30 HTML Interview Questions and Answers](https://www.techbeamers.com/latest-html-interview-questions/)
* [30+ HTML Interview Questions (2021)](https://www.interviewbit.com/html-interview-questions/)

### JavaScript

* [Practice common algorithms using JavaScript](https://github.com/ignacio-chiazzo/Algorithms-Leetcode-Javascript)
* [10 Interview Questions Every JavaScript Developer Should Know](https://medium.com/javascript-scene/10-interview-questions-every-javascript-developer-should-know-6fa6bdf5ad95)
* [21 Essential JavaScript Interview Questions from best mentors all over the world](https://www.codementor.io/javascript/tutorial/21-essential-javascript-tech-interview-practice-questions-answers)
* [20 Essential JavaScript Interview Questions from Adeva](https://adevait.com/javascript-developers/interview-questions)
* [37 Essential JavaScript Interview Questions from Toptal](http://www.toptal.com/javascript/interview-questions)
* [5 More JavaScript Interview Exercises](http://www.sitepoint.com/5-javascript-interview-exercises/)
* [5 Typical JavaScript Interview Exercises](http://www.sitepoint.com/5-typical-javascript-interview-exercises/)
* [Development hiring managers and potential interviewees may find these sample JavaScript proficiency interview Q&As and code snippets useful](http://www.techrepublic.com/blog/software-engineer/javascript-interview-questions-and-answers/)
* [123 Essential JavaScript Interview Question](https://github.com/nishant8BITS/123-Essential-JavaScript-Interview-Question)
* [JavaScript Interview Questions have been designed specially to get you acquainted with the nature of questions you may encounter during your interview for the subject of JavaScript](http://www.tutorialspoint.com/javascript/javascript_interview_questions.htm)
* [JS: Basics and Tricky Questions](http://www.thatjsdude.com/interview/js2.html)
* [JS: Interview Algorithm](http://thatjsdude.com/interview/js1.html)
* [Some basic javascript coding challenges and interview questions](https://github.com/kolodny/exercises)
* [Some JavaScript interview exercises](https://github.com/csvenja/javascript-exercises)
* [Ten Questions I've Been Asked, Most More Than Once, Over Six Technical JavaScript / Front-End Engineer Job Interviews.](https://www.reddit.com/r/javascript/comments/3rb88w/ten_questions_ive_been_asked_most_more_than_once)
* [Top 85 JavaScript Interview Questions](http://career.guru99.com/top-85-javascript-interview-questions/)
* [Interview Cake JavaScript Interview Questions](https://www.interviewcake.com/javascript-interview-questions)
* [The Best Frontend JavaScript Interview Questions (written by a Frontend Engineer)](https://performancejs.com/post/hde6d32/The-Best-Frontend-JavaScript-Interview-Questions-(written-by-a-Frontend-Engineer))
* [10 JavaScript Concepts You Need to Know for Interviews](https://dev.to/arnavaggarwal/10-javascript-concepts-you-need-to-know-for-interviews)
* [Front end interview handbook](https://github.com/yangshun/front-end-interview-handbook)
* [JavaScript Interview Questions - Quick Refresher](https://www.techbeamers.com/javascript-interview-questions-answers/)
* [The MEGA Interview Guide](https://github.com/danieldelcore/mega-interview-guide)
* [Javascript Interview Questions and Answers (2020)](https://www.interviewbit.com/javascript-interview-questions/)
* [JavaScript Modern Interview Code Challenges 2021](https://github.com/sadanandpai/javascript-code-challenges)
* [70 JavaScript Interview Questions](https://dev.to/macmacky/70-javascript-interview-questions-5gfi)

### Front-end build tools

* [Webpack interview questions & answers](https://github.com/styopdev/webpack-interview-questions)
* [Gulp js interview questions](https://www.codeproject.com/Articles/1065184/Latest-Gulp-js-interview-questions)
* [Grunt js interview questions for beginners](http://www.talkingdotnet.com/grunt-js-interview-questions/)
* [Grunt js interview questions](https://mindmajix.com/grunt-interview-questions)

### NodeJS

* [25 Essential Node.js Interview Questions from Adeva](https://adevait.com/nodejs/interview-questions) 
* [8 Essential Nodejs Interview Questions from Toptal](http://www.toptal.com/nodejs/interview-questions)
* [Node.JS Interview Questions have been designed specially to get you acquainted with the nature of questions you may encounter during your interview for the subject of Node.JS](http://www.tutorialspoint.com/nodejs/nodejs_interview_questions.htm)
* [Node.js Interview Questions and Answers](https://blog.risingstack.com/node-js-interview-questions/)
* [Top 25 Nodejs Interview Questions & Answers from Career Guru](http://career.guru99.com/top-25-interview-questions-on-node-js/)
* [Top 30 Node.Js Interview Questions With Answers](https://www.techbeamers.com/top-30-node-js-interview-questions-answers/)
* [Top Nodejs Interview Questions & Answers](https://www.interviewbit.com/node-js-interview-questions/)
* [Node.js Interview Questions in Chinese](https://github.com/haizlin/fe-interview/blob/master/category/nodejs.md)


### ReactJS

* [Reddit users share their expectations from ReactJS interview](https://www.reddit.com/r/reactjs/comments/3m5equ/react_what_interview_questions_to_expect/)
* [This is a first in the series of interview questions related to ReactJS](http://interview-questions-247.appspot.com/reactjs-interview-questions-set-1)
* [This quiz intends to test your understanding of ReactJS fundamentals (Set 3)](http://interview-questions-247.appspot.com/reactjs-interview-questions-set-3)
* [This quiz intends to test your understanding of ReactJS fundamentals](http://interview-questions-247.appspot.com/reactjs-interview-questions-set-2)
* [5 Essential React.js Interview Questions](https://www.codementor.io/reactjs/tutorial/5-essential-reactjs-interview-questions)
* [React Interview Questions](https://tylermcginnis.com/react-interview-questions/)
* [Toptal's 13 Essential React.js Interview Questions](https://www.toptal.com/react/interview-questions)
* [19 Essential ReactJs Interview Questions](https://www.educba.com/reactjs-interview-questions/)



### Sass

* [Top 17 Sass Interview Questions from Career Guru](http://career.guru99.com/top-17-sass-interview-questions/)
* [Top 10 Sass Interview Questions from educba](https://www.educba.com/sass-interview-questions/)


### TypeScript

* [Typescript Interview Questions](https://www.onlineinterviewquestions.com/typescript-interview-questions)
* [Top 10 TypeScript Interview Questions and Answers for Beginner Web Developers 2019](https://www.positronx.io/typescript-interview-questions-answers-2109/)

### MongoDB

* [28 MongoDB NoSQL Database Interview Questions and Answers](http://theprofessionalspoint.blogspot.com.by/2014/01/28-mongodb-nosql-database-interview.html)
* [MongoDB frequently Asked Questions by expert members with experience in MongoDB These questions and answers will help you strengthen your technical skills, prepare for the new job test and quickly revise the concepts](http://www.globalguideline.com/interview_questions/Questions.php?sc=MongoDB)

* [MongoDB Interview Questions from JavaTPointcom](http://www.javatpoint.com/mongodb-interview-questions)
* [MongoDB Interview Questions that have been designed specially to get you acquainted with the nature of questions you may encounter during your interview for the subject of MongoDB](http://www.tutorialspoint.com/mongodb/mongodb_interview_questions.htm)
* [Top 20 MongoDB interview questions from Career Guru](http://career.guru99.com/top-20-mongodb-interview-questions/)


### Linux

* [10 Job Interview Questions for Linux System Administrators from Linux.com](https://www.linuxfoundation.org/blog/2015/07/10-job-interview-questions-for-linux-system-administrators/)
* [10 Useful Random Linux Interview Questions and Answers](http://www.tecmint.com/useful-random-linux-interview-questions-and-answers/)
* [11 Basic Linux Interview Questions and Answers](http://www.tecmint.com/basic-linux-interview-questions-and-answers/)
* [11 Essential Linux Interview Questions from Toptal](http://www.toptal.com/linux/interview-questions)
* [Top 30 Linux System Admin Interview Questions & Answers](http://www.linuxtechi.com/experience-linux-admin-interview-questions/)
* [Top 50 Linux Interview Questions from Career Guru](http://career.guru99.com/top-50-linux-interview-questions/)
* [278 Test Questions and Answers for \*nix System Administrators](https://github.com/trimstray/test-your-sysadmin-skills)
* [Linux Interview Questions - Quick Refresher](https://www.techbeamers.com/essential-linux-questions-answers/)


## Algorithms
* [Comprehensive list of interview questions of top tech companies](https://github.com/rishabh115/Interview-Questions)
* [A great list of Java interview questions](http://java2novice.com/java-interview-programs/)
* [Algorithms playground for common interview questions written in Ruby](https://github.com/sagivo/algorithms)
* [EKAlgorithms contains some well known CS algorithms & data structures](https://github.com/EvgenyKarkan/EKAlgorithms)
* [Top 10 Algorithms for Coding Interview](http://www.programcreek.com/2012/11/top-10-algorithms-for-coding-interview/)
* [Top 15 Data Structures and Algorithm Interview Questions for Java programmer](http://javarevisited.blogspot.com.by/2013/03/top-15-data-structures-algorithm-interview-questions-answers-java-programming.html)
* [Top Algorithms Questions by Topics](https://github.com/yangshun/tech-interview-handbook/blob/master/algorithms/README.md)
* [Daily Coding Interview Practice](https://www.techseries.dev/daily)

## Coding exercises

* [Common interview questions and puzzles solved in several languages](https://github.com/mre/the-coding-interview)
* [Interactive, test-driven Python coding challenges (algorithms and data structures) typically found in coding interviews or coding competitions](https://github.com/donnemartin/interactive-coding-challenges)
* [Interview questions solved in python](https://github.com/roseperrone/interview-questions)
* [7 Swift Coding Challenges to Practice Your Skills](https://www.makeuseof.com/tag/swift-coding-challenges/)


## Comprehensive lists

* [A list of helpful front-end related questions you can use to interview potential candidates, test yourself or completely ignore](https://github.com/h5bp/Front-end-Developer-Interview-Questions)
* [Front End Developer Interview Questions](http://www.aperfectmix.com/free_web_design/front-end-interview-questions.html)
* [Answers to Front End Developer Interview Questions](https://github.com/yangshun/front-end-interview-handbook/blob/master/README.md)
* [Some simple questions to interview potential backend candidates](https://github.com/starandtina/backend-interview-questions)

## Design Patterns
* [Design Pattern Interview Questions that have been designed specially to get you acquainted with the nature of questions you may encounter during your interview for the subject of Design Pattern](http://www.tutorialspoint.com/design_pattern/design_pattern_interview_questions.htm)
* [Design Patterns for Humans™ - An ultra-simplified explanation](https://github.com/kamranahmedse/design-patterns-for-humans)
* [Design Patterns implemented in Java](https://github.com/iluwatar/java-design-patterns)
* [Design Patterns implemented in DotNet](https://www.dofactory.com/net/design-patterns)

## Data structures

* [Top 15 Data Structures and Algorithm Interview Questions for Java programmer](http://javarevisited.blogspot.com.by/2013/03/top-15-data-structures-algorithm-interview-questions-answers-java-programming.html)
* [Top 50 Data Structure Interview Questions from Career Guru](http://career.guru99.com/top-50-data-structure-interview-questions/)
* [What is Data Structure? | Top 40 Data Structure Interview Questions](https://www.interviewbit.com/data-structure-interview-questions/)

# JS interview questions

Repo with notes from/for interviews for js-developer positions.

- [Passing by value/reference](https://github.com/vvscode/js--interview-questions/blob/master/topics/passing-by-value-and-by-reference.md)
- [Closures](https://github.com/vvscode/js--interview-questions/blob/master/topics/closures.md)
- [Flow](https://github.com/vvscode/js--interview-questions/blob/master/topics/flow.md)
- [Hoisting and types](https://github.com/vvscode/js--interview-questions/blob/master/topics/hoisting-vs-types.md)
- [Inheritance and context](https://github.com/vvscode/js--interview-questions/blob/master/topics/inheritance-vs-context.md)
- [Complex](https://github.com/vvscode/js--interview-questions/blob/master/topics/complex.md)
- [Quirks](https://github.com/vvscode/js--interview-questions/blob/master/topics/quirks.md)
- [WTF](https://github.com/vvscode/js--interview-questions/blob/master/topics/wft.md)
- [Greate list of framework specific (not only js) questions](https://www.toptal.com/resources)
- [Unlocking the JavaScript Code Interview (an Interviewer Perspective)](https://medium.com/appsflyer/unlocking-the-javascript-code-interview-an-interviewer-perspective-f4fe06246b29)

---

Here I've noted only questions from my interviews.

## If you want to get more information/materials check next repos:

- https://github.com/h5bp/Front-end-Developer-Interview-Questions -- not only about js
- https://github.com/nishant8BITS/123-Essential-JavaScript-Interview-Question
- https://github.com/kolodny/exercises Some basic javascript coding challenges and interview questions
- https://github.com/malachaifrazier/JavaScript-Interview-Questions Common Questions that may be Asked on a Job Interview
- https://github.com/adam-s/js-interview-review What Do I Need to Know to Ace a JavaScript Interview?
- https://github.com/mi-lee/js-interview-questions/blob/master/interview-questions.md
- https://github.com/nathansmith/javascript-quiz
- https://github.com/ChiperSoft/InterviewThis An open source list of developer questions to ask prospective employers
- https://github.com/MaximAbramchuck/awesome-interview-questions Awesome Interviews ( multiple langs )
- https://github.com/apoterenko/javascript-interview-questions ( about 50 questions like "Explain ouput.."
- https://github.com/kensterz/interview-questions-in-javascript Interview Algorithm Questions in Javascript
- https://github.com/HIROSN/coding-interviews-es6 Coding Interview Questions (ECMAScript 2015)
- https://github.com/mkshen/code-problems-solutions Interview coding questions and answers in Javascript - ES6
- https://github.com/khan4019/front-end-Interview-Questions Interview Questions for front-end-Developer ( Only for JS developer when they have to answer some side questions to make interviewer comfortable. ) by [That JsDude](http://www.thatjsdude.com/interview/index.html)
- https://medium.com/javascript-scene/10-interview-questions-every-javascript-developer-should-know-6fa6bdf5ad95#.i5mgmc4m0 10 Interview Questions Every JavaScript Developer Should Know AKA: The Keys to JavaScript Mastery
- https://github.com/yangshun/tech-interview-handbook/blob/master/front-end/interview-questions.md - Front-end Job Interview Questions (and **Answers** - that might be most interesting for lazy persons who just want to know keys for interview )
- https://github.com/wwwebman/front-end-interview-questions Our front end interview questions and answers can help you to prepare for an interview better and faster
- https://github.com/kennymkchan/interview-questions-in-javascript A mostly reasonable collection of technical software development interview questions solved in Javascript
- https://github.com/fejes713/30-seconds-of-interviews A curated collection of common interview questions to help you prepare for your next interview.
- https://github.com/rakesh-sankar/awesome-interview-question A curated list of interview questions of various domain.
- https://github.com/ajzawawi/js-interview-prep A collection of JS interview questions ~~updated every day~~
- https://github.com/monkey3310/full-stack-interview Full Stack Interview Questions & Answers (inc. js-stack)
- https://github.com/sudheerj/reactjs-interview-questions List of top 222 ReactJS Interview Questions & Answers
- https://github.com/Pau1fitz/react-interview  List of common React interview questions.
- https://github.com/ElemeFE/node-interview How to pass the Node.js interview of ElemeFE
- https://www.adaface.com/blog/react-interview-questions/ 100+ React Interview Questions (2020)

## More specific questions:

- [Top 50 React Interview Questions You Must Prepare In 2019](https://www.edureka.co/blog/interview-questions/react-interview-questions/)
- [5 Essential React.js Interview Questions](https://www.codementor.io/reactjs/tutorial/5-essential-reactjs-interview-questions)
- [(one more time ) Awesome Interviews - not only languages, but libraries/frameworks too](https://github.com/MaximAbramchuck/awesome-interview-questions)
- JS Interview Algorithm [beginner](http://www.thatjsdude.com/interview/js1.html) / [intermediate](http://www.thatjsdude.com/interview/js2.html)
- [13 Essential React.js Interview Questions](https://www.toptal.com/react/interview-questions)
- [React Interview Questions and Answers](https://www.interviewbit.com/react-interview-questions/)

## Also it may be helpful to check next books:

- **"Javascript Technical Interview Questions"** by Xuanyi Chew https://leanpub.com/jsinterviewquestions
- **"Quick JavaScript Interview Questions"** by Sandeep Kumar Patel https://leanpub.com/quickjavascriptinterviewquestions
- **"JavaScript Interview Questions: Who Else Wants to Nail that Interview?"** by Volkan Özçelik https://o2js.com/assets/javascript-interview-questions.pdf
- https://www.frontendhandbook.com/practice/interview-q.html The part about interview at `Front-End Developer Handbook`
- http://www.w3resource.com/javascript-exercises/ JavaScript Exercises, Practice, Solution ( starter level, suppose. Most questions is about knowledge of basic API / lang construction )
- https://www.interviewcake.com/javascript-interview-questions ( JavaScript Interview Questions, like "Merging Meeting Times", "Two Egg Problem" -- the exersizes/questions can be solved no only via js - they are more algorithmic and give you mental pabulum ). Both - tasks/solutions are pretty cool
- https://github.com/yangshun/tech-interview-handbook **Tech Interview Handbook** (Algorithms, front end and behavioral content for rocking your coding interview)

## Some ideas can be found during online tests. Like next:

- https://tests4geeks.com/category/javascript
- http://perfectionkills.com/javascript-quiz-es6/ ( also check explains at https://gist.github.com/DmitrySoshnikov/3928607cb8fdba42e712 )
- http://dmitry.baranovskiy.com/post/91403200 - So, you think you know JavaScript? it's usefull to read https://www.nczonline.net/blog/2010/01/26/answering-baranovskiys-javascript-quiz/ )
- http://perfectionkills.com/javascript-quiz/
- https://www.adaface.com/assessment-test/javascript-online-test

## You can get more practice in interview questions at:

- https://codesignal.com/interview-practice
- https://www.pramp.com
- https://interviewbuddy.in
- http://www.gainlo.co


If you're ready to share your experience - you're welcome. Make PR to related file ( by topic ) or create issue with list of questions

**_P.S._** it worth to check **_*'Cracking the Coding Interview'*_** by Gayle Laakmann McDowell ( solutions can be founded at https://github.com/careercup/CtCI-6th-Edition , book (at least 5th edition can be googled )

<img src="office.jpg">

# Awesome JavaScript Interviews

A collection of super-popular Interview questions, along with explanations and implementation examples that I was putting together for myself while preparing for my first Full-Stack JavaScript job interviews.

## Table of Contents of this Readme file

1. [Most common Fundamental JavaScript Interview Topics & Questions](#most-common-fundamental-javascript-interview-topics--questions)

2. [Most common Tricky Javascript Interview Topics & Questions](#most-common-tricky-javascript-interview-topics--questions)

3. [Most common Async/Await and Promise related Interview Topics & Questions](#most-common-asyncawait-and-promise-related-interview-topics--questions)

4. [Most common Node Interview Topics & Questions](#most-common-node-interview-topics--questions)

5. [Most common Web-Development Architecture related Interview Topics & Questions](#most-common-web-development-architecture-related-interview-topics--questions)

6. [Most common React Interview Topics & Questions](#most-common-react-interview-topics--questions)

7. [Most common Redux Interview Topics & Questions](#most-common-redux-interview-topics--questions)

8. [Most common Angular Interview Topics & Questions](#most-common-angular-interview-topics--questions)

9. [Most common MongoDB Interview Topics & Questions](#most-common-mongodb-interview-topics--questions)

10. [Most common HTML Interview Topics & Questions](#most-common-html-interview-topics--questions)

11. [Most common CSS Interview Topics & Questions](#most-common-css-interview-topics--questions)

12. [Most common Git and Github related Interview Topics & Questions](#most-common-git-and-github-related-interview-topics--questions)

13. [Understanding the Theory and the fundamentals of some super-popular Algorithm questions](#understanding-the-theory-and-the-fundamentals-of-some-super-popular-algorithm-questions)

14. [Github Repositories with large collections of problems-and-solutions of them most popular Interview challenges](#github-repositories-with-large-collections-of-problems-and-solutions-of-them-most-popular-interview-challenges)

15. [Overall multi-factor approach for winning this huge challenge and a great journey of getting the first Developer Job](#overall-multi-factor-approach-for-winning-this-huge-challenge-and-a-great-journey-of-getting-the-first-developer-job)

16. [Other important resources](#other-important-resources)

17. [Coding Challenge Practice Platforms](#coding-challenge-practice-platforms)

18. [More curated list of general resources for JavaScript Interviews](#more-curated-list-of-general-resources-for-javascript-interviews)

19. [Most frequently asked concepts for Front End Engineering Interview](#most-frequently-asked-concepts-for-front-end-engineering-interview)

20. [List of sites where you can hunt for a developer job](#list-of-sites-where-you-can-hunt-for-a-developer-job)

21. [Want a startup job?](#want-a-startup-job)

22. [Best places to job hunt for remote jobs](#best-places-to-job-hunt-for-remote-jobs)

23. [Here are a few places to hunt for ios, react, vue and more](#here-are-a-few-places-to-hunt-for-ios-react-vue-and-more)

24. [Want a list of just JavaScript jobs?](#want-a-list-of-just-javascript-jobs)

25. [Are you looking for a junior dev job?](#are-you-looking-for-a-junior-dev-job)

26. [Women focused job boards!](#women-focused-job-boards)

27. [Want a job as a freelance dev? Here's a list](#want-a-job-as-a-freelance-dev-heres-a-list)

28. [Some useful websites for programmers](#some-useful-websites-for-programmers)

29. [When you get stuck](#when-you-get-stuck)

30. [For small project ideas](for-small-project-ideas)

31. [General Coding advice](general-coding-advice)

32. [Coding Style](#coding-style)

33. [General Good Articles](#general-good-articles)

34. [Collection of Leetcode Problem solution](#collection-of-leetcode-problem-solution)

35. [Collection of Cracking the Coding Interview Book Problem solution](#collection-of-cracking-the-coding-interview-book-problem-solution)

36. [Most common System-Design Interview Topics & Questions](#most-common-system-design-interview-topics--questions)

37. [System-Design related topics-Some very useful articles](#system-design-related-topics-some-very-useful-articles)

38. [System-Design-Company engineering blog](#system-design-company-engineering-blog)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common Fundamental JavaScript Interview Topics & Questions

(Below Links are all within this Repository)

- [Explain event delegation](Javascript/event-delegation-propagation-bubbling.md)
- [Explain how `this` works in JavaScript](Javascript/this-keyword/this-keyword-2nd-example-GREAT-Example.md)
  - [more-on `this` keyword](Javascript/this-keyword/this-example-custom-Array-Prototype-method.md)
  - [more on `this` keyword](Javascript/this-keyword/this-keyword-simplest-catagories.md)
  - [more-on-this-keyword](Javascript/this-keyword/this-keyword-1.js)
- [Explain how prototypal inheritance works](Javascript/OOP-Prototypal-Inheritence/README.md)
  - [how-to-get-prototype-of-an-object](Javascript/OOP-Prototypal-Inheritence/how-to-get-prototype-of-an-object.md)
  - [Inheritence-OOP-Class-vs-Prototypes-Example](Javascript/OOP-Prototypal-Inheritence/Inheritence-OOP-Class-vs-Prototypes-Example-BEST.md)
  - [Inheritence-OOP-Class-vs-Prototypes-Theory](Javascript/OOP-Prototypal-Inheritence/Inheritence-OOP-Class-vs-Prototypes-Theory.md)
  - [Inheritence-with-classes-super-keyword-Exhaustive-Explanation](Javascript/OOP-Prototypal-Inheritence/Inheritence-with-classes-super-keyword-SIMPLEST-EXHAUSTIVE.md)
  - [OOP-Basics-1](Javascript/OOP-Prototypal-Inheritence/OOP-Basics-1.md)
  - [OOP-basics-2](Javascript/OOP-Prototypal-Inheritence/OOP-basics-2.md)
  - [OOP-Encapsulation-example-1](Javascript/OOP-Prototypal-Inheritence/OOP-Encapsulation-example-1.md)
  - [OOP-Encapsulation-example-2](Javascript/OOP-Prototypal-Inheritence/OOP-Encapsulation-example-2.md)
  - [OOP-Encapsulation-Theory-GOOD-Explanations-Private-Methods](Javascript/OOP-Prototypal-Inheritence/OOP-Encapsulation-Theory-GOOD-Explanations-Private-Methods.md)
  - [print-All-Prototypes-of-Objects](Javascript/OOP-Prototypal-Inheritence/print-All-Prototypes-of-Objects.js)
  - [Prototype-Example-Really-GOOD-Explanations](Javascript/OOP-Prototypal-Inheritence/Prototype-Example-Really-GOOD-Explanations.js)
  - [Prototype-Example-1](Javascript/OOP-Prototypal-Inheritence/Prototype-Example-1.js)
  - [Prototype-Example-2](Javascript/OOP-Prototypal-Inheritence/Prototype-Example-2.js)
  - [prototype-func-print-array-elements](Javascript/OOP-Prototypal-Inheritence/prototype-func-print-array-elements.js)
  - [Prototype-func-String-dasherize](Javascript/OOP-Prototypal-Inheritence/Prototype-func-String-dasherize.js)
  - [Prototypes-Benefits-Handling-Memory-Leaks](Javascript/OOP-Prototypal-Inheritence/Prototypes-Benefits-Handling-Memory-Leaks.md)
  - [Prototypes-Prevents-Memory-Leaks-1-Good-Explanation](Javascript/OOP-Prototypal-Inheritence/Prototypes-Prevents-Memory-Leaks-1-Good-Explanation.md)
- [Explain the concepts around and the difference between Call, Apply and Bind](Javascript/call-apply-bind/call-function-basics-1.md)
  - [More on Call, Apply and Bind](Javascript/call-apply-bind/call-function-basics-2.md)
  - [More on Call, Apply and Bind](Javascript/call-apply-bind/call-function-basics-2.md)
  - [call-vs-apply-vs-bind](Javascript/call-apply-bind/call-vs-apply-vs-bind.md)
  - [Why bind function is needed](bind-why-its-needed)
- [arrow-vs-regular-functions](Javascript/arrow-function/arrow-vs-regular-functions.md)
- [when-not-to-use-arrow-function](Javascript/arrow-function/when-not-to-use-arrow-function.md)
- [arrow-function-and-this-keyword](arrow-function-and-this-keyword)
- [Destructuring - some examples](Javascript/ES6-Array-Helper-Methods/Destructuring_Geneal.md)
- [filter method implementation](Javascript/ES6-Array-Helper-Methods/filter-implement.js)
- [forEach-vs-map](Javascript/ES6-Array-Helper-Methods/forEach-vs-map.md)
- [Pure-functions-basics](Javascript/Functional-Programming_Pure-Function/Pure-functions-basics.md)
- [closure explanations](Javascript/js-basics/Closure/closure.md)
- [closure-MOST-POPULAR-Interview Question on setTimeout](Javascript/js-basics/Closure/closure-setTimeout-MOST-POPULAR.js)
  - [Basics closure concepts involving setTimeout](Javascript/js-basics/Closure/closure-setTimeout.js)
  - [closure-tricky and great Example](Javascript/js-basics/Closure/closure-tricky-GREAT-EXAMPLE.JS)
  - [closure-use-case-for-creating-private-variable](Javascript/js-basics/Closure/closure-use-case-create-private-variable.js)
  - [closure-why-its-needed at all](Javascript/js-basics/Closure/closure-why-its-needed.js)
  - [More on Closure](Javascript/js-basics/Closure/closures-retains-values-of-outer-function-after-outer-returns.md)
- [Custom Callback Function-1](Javascript/js-basics/custom_Callback-1.js)
- [Custom Callback Function-2](Javascript/js-basics/custom_Callback-2.js)
- [IIFE function in 10 different ways](Javascript/js-basics/IIFE-10-ways.js)
- [IIFE](Javascript/IIFE.md)
- [scope in JS - A basic-understanding](Javascript/js-basics/scope-basic-understanding.md)
- [Data Types in JS](Javascript/js-data-types/data-types.md)
  - [BigInt-data-type](Javascript/js-data-types/BigInt-data-type.md)
  - [check-data-type-with-typeof](Javascript/js-data-types/check-data-type-with-typeof.js)
  - [data-type-mutability](Javascript/js-data-types/data-type-mutability.md)
  - [data-types of Number-A very popular Interview Question](Javascript/js-data-types/data-types-Number-Famous-Question.md)
  - [More on data-types of Number](Javascript/js-data-types/data-types-Number.md)
  - [data-types-symbol](Javascript/js-data-types/data-types-symbol.md)
  - [what-is-type-coercion](Javascript/js-data-types/what-is-type-coercion.md)
  - [More on coercion](Javascript/coercion.md)
- [spread-operator-vs-rest-parameters](Javascript/rest-spread-destructuring/spread-operator-vs-rest-parameters.md)
- [rest-spread-basic-techniques](Javascript/rest-spread-destructuring/rest-spread-basic-techniques.js)
- [More on rest and spread operator](Javascript/rest-spread-destructuring/rest-spread-2.js)
- [Example of Call Stack](Javascript/call-stack-good-example.md)
- [const-var-let](Javascript/const-var-let.md)
- [curried-function](Javascript/curried-function.md)
- [execution-context-call-stack.md](Javascript/execution-context-call-stack.md)
- [hashing-vs-encrypting.md](Javascript/hashing-vs-encrypting.md)
- [Hoisting - The supre important concept](Javascript/hoisting.md)
- [is-javascript-static-or-dynamically-typed](Javascript/is-javascript-static-or-dynamically-typed.md)
- [is-JS-block-scoped-or-function-scoped](Javascript/is-JS-block-scoped-or-function-scoped.md)
- [map-set-get](Javascript/map-set-get.js)
- [Null-Coalescing-operator](Javascript/Null-Coalescing-operator.md)
- [truthy-falsy-1](Javascript/truthy-falsy-1.js)
- [truthy-falsy-2](Javascript/truthy-falsy-2.md)
- [truthy-falsy-pass-by-value-vs-reference-strict-equality-use-case](Javascript/truthy-falsy-pass-by-value-vs-reference-strict-equality-use-case.js)
- [passing-by-value-and-by-reference](Javascript/passing-by-value-and-by-reference.md)
- [undefined-vs-not_defined](Javascript/undefined-vs-not_defined.md)
- [Why-eval-function-considered-dangerous](Javascript/Why-eval-function-considered-dangerous.md)
- [use-strict-describe](Javascript/use-strict-describe.md)
- [How would you compare two objects in JavaScript?](Large-Collection-of-Popular-Problems-with-Solutions/Objects-Master-List-of-Problems-Super-Useful-Daily-Techniques/compare-two-objects.md)
- [Memoize a function](Large-Collection-of-Popular-Problems-with-Solutions/Objects-Master-List-of-Problems-Super-Useful-Daily-Techniques/Memoize-a-function.md)
- [repaint-reflow](Javascript/repaint-reflow.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common Tricky Javascript Interview Topics & Questions

(Below Links are all within this Repository)

- [Collection-of-Tricky-JS-Questlions](Javascript/Tricky-JS-Problems/Collection-of-Tricky-JS-Questlions.md)
- [closure-tricky and great Example](Javascript/js-basics/Closure/closure-tricky-GREAT-EXAMPLE.js)
- [logical-and-operator-Tricky Question](Javascript/Tricky-JS-Problems/logical-and-operator.js)
- [Value of Null](Javascript/Tricky-JS-Problems/value-of-null.js)
- [pitfall-of-using-typeof](Javascript/Tricky-JS-Problems/pitfall-of-using-typeof.md)
- [What-is-the-value-of-Math.max([2,3,4,5])](<Javascript/Tricky-JS-Problems/What-is-the-value-of-Math.max([2,3,4,5]).md>)
- [not-not-operator-in-javascript](Javascript/Tricky-JS-Problems/not-not-operator-in-javascript.md)
- [why-does-adding-two-decimals-in-javascript-produce-a-wrong-result](Javascript/Tricky-JS-Problems/why-does-adding-two-decimals-in-javascript-produce-a-wrong-result.md)
- [typeof-NaN](Javascript/Tricky-JS-Problems/typeof-NaN.md)
- [If null is a primitive, why does typeof(null) return "object"?](Javascript/Tricky-JS-Problems/typeof-null-why-its-object.md)
- [null-vs-undefined](Javascript/Tricky-JS-Problems/null-vs-undefined.md)
- [Closures-Inside-Loops](Javascript/Tricky-JS-Problems/Closures-Inside-Loops.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common Async/Await and Promise related Interview Topics & Questions

(Below Links are all within this Repository)

- [Async/Await - Understanding the fundamentals](Promise-Async-Await-Sequential-Execution/async-await-master-notes/README.md)
- [asyn-await-how-its-called-asynchronous-when-it-makes-possible-to-execute-in-synchrounous-manner](Promise-Async-Await-Sequential-Execution/async-await-master-notes/asyn-await-how-its-called-asynchronous-when-it-makes-possible-to-execute-in-synchrounous-manner.md)
- [Example async-await-1](Promise-Async-Await-Sequential-Execution/async-await-master-notes/async-await-1.js)
- [Example async-await-2](Promise-Async-Await-Sequential-Execution/async-await-master-notes/async-await-2.js)
- [Example async-await-3](Promise-Async-Await-Sequential-Execution/async-await-master-notes/async-await-3.js)
- [async-await-absolute-basics](async-await-absolute-basics.js)
- [async-await-example-when-Promise-is-preferred](Promise-Async-Await-Sequential-Execution/async-await-master-notes/async-await-example-when-Promise-is-preferred.js)
- [converting-callback-to-Promise-and-async-await-1](Promise-Async-Await-Sequential-Execution/async-await-master-notes/converting-callback-to-Promise-and-async-await-1.md)
- [converting-callback-to-Promise-and-async-await-2](Promise-Async-Await-Sequential-Execution/async-await-master-notes/converting-callback-to-Promise-and-async-await-2.md)
- [setTimeout-rate-limiting-api-calls-IMP-with-async-await-looping-over-apis-1](Promise-Async-Await-Sequential-Execution/async-await-master-notes/setTimeout-rate-limiting-api-calls-IMP-with-async-await-looping-over-apis-1.js)
- [setTimeout-rate-limiting-api-calls-IMP-with-async-await-looping-over-apis-2](Promise-Async-Await-Sequential-Execution/async-await-master-notes/setTimeout-rate-limiting-api-calls-IMP-with-async-await-looping-over-apis-2.js)
- [Promise - Fundamental Understanding](Promise-Async-Await-Sequential-Execution/Promise-async-await-master-notes/README.md)
- [calback-hell-resolved-with-promise](Promise-Async-Await-Sequential-Execution/Promise-async-await-master-notes/calback-hell-resolved-with-promise.js)
- [More callback-hell-examples](Promise-Async-Await-Sequential-Execution/Promise-async-await-master-notes/callback-hell-examples.js)
- [How-Promise-makes-code-Asynchronous-non-blocking](Promise-Async-Await-Sequential-Execution/Promise-async-await-master-notes/How-Promise-makes-code-Asynchronous-non-blocking.md)
- [Promise Super simple-Examples](Promise-Async-Await-Sequential-Execution/Promise-async-await-master-notes/Promise-simple-Example.js)
- [More Promise Super simple Examples](Promise-Async-Await-Sequential-Execution/Promise-Super-Basic/absolute-super-basic-Promise-creation.md)
- [More Promise Super simple Examples](Promise-Async-Await-Sequential-Execution/Promise-Super-Basic/Promise-super-basic-implementation-Absolute-Basics.js)
- [Understanding then in Promise](Promise-Async-Await-Sequential-Execution/Promise-async-await-master-notes/then-in-Promise-GOOD-Explanations.md)
- [Promise-super-basic-example-transform-values-with-Promise](Promise-Async-Await-Sequential-Execution/Promise-Super-Basic/Promise-super-basic-example-transform-values-with-Promise.md)
- [Promise-Absolute basic-syntax](Promise-Async-Await-Sequential-Execution/Promise-Super-Basic/Promise-super-basic-syntax-GOOD.md)
- [Async-await-API-call-Simple-Example-synchronous-Fetch](Promise-Async-Await-Sequential-Execution/sequential-execution-of-codes-React-Node-Context-Master-Notes/Async-await-API-call-Simple-Example-synchronous-Fetchl-Simple-Good-Example.md)
- [Async-Event-Handler-both-async-await-and-with-Promise-1](Promise-Async-Await-Sequential-Execution/sequential-execution-of-codes-React-Node-Context-Master-Notes/Async-Event-Handler-both-async-await-and-with-Promise-1.md)
- [multiple-API-calls-before-executing-next-function-in-React-Promise-2](Promise-Async-Await-Sequential-Execution/sequential-execution-of-codes-React-Node-Context-Master-Notes/multiple-API-calls-before-executing-next-function-in-React-Promise-2.md)
- [multiple-API-fetch-before-executing-next-function-in-React-Promise-1](Promise-Async-Await-Sequential-Execution/sequential-execution-of-codes-React-Node-Context-Master-Notes/multiple-API-fetch-before-executing-next-function-in-React-Promise-1.md)
- [multiple-sequential-axios-request](Promise-Async-Await-Sequential-Execution/sequential-execution-of-codes-React-Node-Context-Master-Notes/multiple-sequential-axios-request.md)
- [sequential-execution-async-await-in-Express-routes](Promise-Async-Await-Sequential-Execution/sequential-execution-of-codes-React-Node-Context-Master-Notes/sequential-execution-async-await-in-Express-routes.md)
- [sequential-execution-fundamental_working-THEORY](Promise-Async-Await-Sequential-Execution/sequential-execution-of-codes-React-Node-Context-Master-Notes/sequential-execution-fundamental_working-THEORY.md)
- [sequential-execution-plain-callback-in-Express-routes](Promise-Async-Await-Sequential-Execution/sequential-execution-of-codes-React-Node-Context-Master-Notes/sequential-execution-plain-callback-in-Express-routes.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common Node Interview Topics & Questions

(Below Links are all within this Repository)

- [why-nodejs-required-at-all-and-difference-vs-plain-js](Node-Express/why-nodejs-required-at-all-and-difference-vs-plain-js.md)
- [How-nodejs-works](Node-Express/How-nodejs-works.md)
- [What-is-an-error-first-callback](Node-Express/What-is-an-error-first-callback.md)
- [Authentication vs Authorization](Node-Express/Authentication-vs-Authorization.md)
- [What is Middleware-1](Node-Express/app.use-Middleware-1.md)
- [What is Middleware-2](Node-Express/app.use-Middleware-2.md)
- [app.use-vs-app.get](Node-Express/app.use-vs-app.get.md)
- [bcrypt-How-it-works-de-hashing](Node-Express/bcrypt-How-it-works-de-hashing.md)
- [bcrypt-manually-generate-a-salted-and-encrypted-password](Node-Express/bcrypt-manually-generate-a-salted-and-encrypted-password.md)
- [bodyParser_what-does-it-do](Node-Express/bodyParser_what-does-it-do.md)
- [buffer-class-what-is-it](Node-Express/buffer-class-what-is-it.md)
- [busboy-why-its-needed](Node-Express/busboy-why-its-needed.md)
  - [busboy-why-I-use-stream-to-upload-file](Node-Express/busboy-why-I-use-stream-to-upload-file.md)
- [cookie-parser-what-does-it-do](Node-Express/cookie-parser-what-does-it-do.md)
- [cors_Why_its_needed](Node-Express/cors_Why_its_needed.md)
- [error-handling-in-node-Theory](Node-Express/error-handling-in-node-Theory.md)
- [More on error-handling-in-node](Node-Express/error-handling-in-node.md)
- [express-js-why-do-i-need-it](Node-Express/express-js-why-do-i-need-it.md)
- [gracefully-shut-down-node-app](Node-Express/gracefully-shut-down-node-app.md)
- [jwt-how-it-works](Node-Express/jwt-how-it-works.md)
- [jwt-where-to-save-localStorage-vs-sessionStorage-vs-cookie](Node-Express/jwt-where-to-save-localStorage-vs-sessionStorage-vs-cookie.md)
- [session-cookies-vs-JWT-Tokens-2-ways-to-authenticate](Node-Express/session-cookies-vs-JWT-Tokens-2-ways-to-authenticate.md)
- [sesstionStorage-vs-localStorage-vs-Cookie](Node-Express/sesstionStorage-vs-localStorage-vs-Cookie.md)
- [localForage-what-does-it-do](Node-Express/localForage-what-does-it-do.md)
- [How would you do node-debugging](Node-Express/node-debugging.md)
- [passport-authentication-middleware-BASIC-FLOW](Node-Express/passport-authentication-middleware-BASIC-FLOW.md)
- [passport-express-session-Fundamentals-and-params](Node-Express/passport-express-session-Fundamentals-and-params.md)
- [passport-express-session-how-it-works](Node-Express/passport-express-session-how-it-works.md)
- [passport-workflow-with-passport-local-strategy](Node-Express/passport-workflow-with-passport-local-strategy.md)
- [pipe concepts in node](Node-Express/pipe-in-node.md)
- [REST-architectural-concepts](Node-Express/REST-architectural-concepts.md)
- [significance-of-file-bin-www](Node-Express/significance-of-file-bin-www.md)
- [Streams Concepts in Node](Node-Express/Streams.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common Web-Development Architecture related Interview Topics & Questions

(Below Links are all within this Repository)

- [critical-render-path](Web-Development-In-General/critical-render-path.md)
- [How-to-Check-HTTP-Request-Response-on-Chrome](Web-Development-In-General/How-to-Check-HTTP-Request-Response-on-Chrome.md)
- [HTTP-and-TCP-Difference](Web-Development-In-General/HTTP-and-TCP-Difference.md)
- [HTTP-methods-put-vs-post](Web-Development-In-General/HTTP-methods-put-vs-post.md)
- [HTTP-Protocol](Web-Development-In-General/HTTP-Protocol.md)
- [HTTP-Status-Codes-Understanding-Express-res.status](Web-Development-In-General/HTTP-Status-Codes-Understanding-Express-res.status.md)
- [More on HTTP-Status-Codes](Web-Development-In-General/HTTP-Status-Codes.md)
- [http-vs-https](Web-Development-In-General/http-vs-https.md)
- [minimmize-page-load-time](Web-Development-In-General/minimmize-page-load-time.md)
- [Postman-checking-protected-routes-from-backend](Web-Development-In-General/Postman-checking-protected-routes-from-backend.md)
- [websocket-basics](Web-Development-In-General/websocket-basics.md
- [What-happens-when-you-navigate-to-an-URL](Web-Development-In-General/What-happens-when-you-navigate-to-an-URL.md)
- [What-happens-when-you-navigate-to-google](Web-Development-In-General/What-happens-when-you-navigate-to-google.md)
- [what-is-AJAX](Web-Development-In-General/what-is-AJAX.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common React Interview Topics & Questions

(Below Links are all within this Repository)

- [Element-vs-Component-in-React](React/Element-vs-Component-in-React.md)
- [What is a Prop - props-Absolute-Basics](React/props-Absolute-Basics.md)
- [Life-Cycle-Fundamentals](React/Component-Life-Cycle/README.md)
- [Life Cycle Methods - getDerivedStateFromProps](React/Component-Life-Cycle/getDerivedStateFromProps.md)
- [Life Cycle Methods - shouldComponentUpdate-what-does-it-do](React/Component-Life-Cycle/shouldComponentUpdate-what-does-it-do.md)
- [Life Cycle Methods - constructor-vs-componentwillmount](React/Component-Life-Cycle/constructor-vs-componentwillmount.md)
- [React-Hooks-convert-ClassBasedForm-to-HooksBasedForm](React/Hooks/convert-ClassBasedForm-to-HooksBasedForm.md)
  - [hooks-updateState-with-callback](React/Hooks/updateState-with-callback.md)
  - [lifeCycle-methods-for-various-hooks](React/Hooks/lifeCycle-methods-for-various-hooks.md)
  - [Shallow-comparison-React-useEffect-compare-array-in-second-argument](React/Hooks/Shallow-comparison-React-useEffect-compare-array-in-second-argument.md)
  - [useEffect-basics-1](React/Hooks/useEffect-basics-1.md)
  - [useEffect-api-call-with-async-inside-useEffect](React/Hooks/useEffect-api-call-with-async-inside-useEffect.md)
  - [More on useEffect-async-call-inside](React/Hooks/useEffect-async-call-inside.md)
  - [useEffect-compare-array-in-second-argument-replace-ComonentDidMount-with-useRef](React/Hooks/useEffect-compare-array-in-second-argument-replace-ComonentDidMount-with-useRef.md)
  - [useEffect-compare-array-in-second-argument-shallow](React/Hooks/useEffect-compare-array-in-second-argument-shallow.md)
  - [useEffect-replace-componentDidMount-and-Update](React/Hooks/useEffect-replace-componentDidMount-and-Update.md)
  - [useEffect-replace-componentWillUnmount](React/Hooks/useEffect-replace-componentWillUnmount.md)
  - [useEffect-running-callback-after-setState-IMPORTANT](React/Hooks/useEffect-running-callback-after-setState-IMPORTANT.md)
  - [useEffect-with-Redux-actions](React/Hooks/useEffect-with-Redux-actions-GOOD.md)
  - [useReducer-basics-1](React/Hooks/useReducer-basics-1.md)
  - [userReducer-vs-redux-reducer](React/Hooks/userReducer-vs-redux-reducer.md)
  - [useState-replace-componentWillReceiveProps-getDerivedStateFromProps](React/Hooks/useState-replace-componentWillReceiveProps-getDerivedStateFromProps.md)
- [styled-component-basics](React/React-Styled-Component/styled-component-basics.md)
- [styled-component-a-clean-example](React/React-Styled-Component/styled-component-a-clean-example.md)
- [Testing-react-shallow-renderer-basics](React/React-Testing-Jest/Testing-react-shallow-renderer-basics.md)
- [snapshot-testing](React/React-Testing-Jest/snapshot-testing.md)
- [React Testing - where-should-enzyme-setup-file-be-written](React/React-Testing-Jest/where-should-enzyme-setup-file-be-written.md)
- [refs-in-React](React/refs-in-react/refs-in-React.md)
  - [refs-Call-child-method-from-parent](React/refs-in-react/refs-Call-child-method-from-parent.md)
  - [execute-child-function-from-parent](React/refs-in-react/execute-child-function-from-parent.md)
  - [refs-vs-keys-when-to-use-ref](React/refs-in-react/refs-vs-keys-when-to-use-ref.md)
  - [useRef-basics](React/refs-in-react/useRef-basics.md)
- [context-api-basics](React/context-api-basics.md)
- [controlled-unContolled-Component](React/controlled-unContolled-Component.md)
- [Create-Class-avoiding-binding-in-constructor](React/Create-Class-avoiding-binding-in-constructor.md)
- [destructuring_basics-js](React/destructuring_basics-js.md)
- [More destructuring_example](React/destructuring_example.md)
- [More Destructuring explanations and examples](React/Destructuring_General.md)
- [destructuring_in_react-1](React/destructuring_in_react-1.md)
- [More destructuring_in_react](React/destructuring_in_react-2.md)
- [What is e.target.value](React/e.target.value.md)
- [Explain-whats-wrong-with-this-React-code](React/Explain-whats-wrong-with-this-React-code.md)
- [functional-component-declaration-syntax](React/functional-component-declaration-syntax.md)
- [More examples on functional-component-declaration-syntax](React/functional-component-declaration-syntax-1.md)
- [HOC - Higher Order Component](React/HOC.md)
- [how-react-decide-to-re-render-a-component](React/how-react-decide-to-re-render-a-component.md)
- [Unique keys-for-li-elements-why-its-needed](React/keys-for-li-elements-why-its-needed.md)
- [onChange-updating-state-from-child](React/onChange-updating-state-from-child.md)
- [pass-props-from-Parent-To-Child-Component-communication](React/pass-props-from-Parent-To-Child-Component-communication.md)
  - [pass-prop-to-component-rendered-by-React-Router](React/pass-prop-to-component-rendered-by-React-Router.md)
  - [More on pass-props-from-Child-to-parent-Component-communication](React/pass-props-from-Child-to-parent-Component-communication.md)
  - [More on pass-props-from-Child-to-parent-Component-communication-2](React/pass-props-from-Child-to-parent-Component-communication-2.md)
- [preventDefault-in-React](React/preventDefault-in-React.md)
- [pureComponent - What they are](React/pureComponent.md)
- [pureComponent-Performance-benefit](React/pureComponent-Performance-benefit.md)
- [react-hot-loader](React/react-hot-loader.md)
- [React.Fragment](React/React.Fragment.md)
- [Redirect-from-react-router-dom](React/Redirect-from-react-router-dom.md)
- [server-side-rendering-react-app](React/server-side-rendering-react-app.md)
- [setState-what-does-it-do](React/setState-what-does-it-do.md)
- [super(props)-why-its-required](<React/super(props)-why-its-required.md>)
- [this.props.children](React/this.props.children.md)
- [Virtual-DOM-and-Reconciliation-Algorithm](React/Virtual-DOM-and-Reconciliation-Algorithm.md)
- [What are the approaches to include polyfills in your create-react-app](React/include-polyfills.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common Redux Interview Topics & Questions

(Below Links are all within this Repository)

- [What is Redux Actions](Redux/Actions.md)
- [actions-why-enclosed-in-curly-braces](Redux/actions-why-enclosed-in-curly-braces.md)
- [What are actions.payload](Redux/actions.payload.md)
- [What is applyMiddleware](Redux/applyMiddleware.md)
- [What is bindActionCreators](Redux/bindActionCreators.md)
- [What is combine-Recucer](Redux/combine-Recucer.md)
- [What is compose-function](Redux/compose-function.md)
- [What is Connect function](Redux/Connect.md)
- [What is container-component](Redux/container-component.md)
- [What is createStore](Redux/createStore.md)
- [Example of Currying](Redux/currying.md)
- [What is dispatch](Redux/dispatch.md)
- [flux-vs-redux](Redux/flux-vs-redux.md)
- [What is mapDispatchToProps](Redux/mapDispatchToProps.md)
- [mapStateToProps-basic-understanding-1](Redux/mapStateToProps-basic-understanding-1.md)
- [mapStateToProps-basic-understanding-2](Redux/mapStateToProps-basic-understanding-2.md)
- [mapStateToProps-how-exactly-it-gets-the-state-from-reducers](Redux/mapStateToProps-how-exactly-it-gets-the-state-from-reducers.md)
- [What is Provider](Redux/Provider.md)
- [What is Reducers](Redux/Reducers.md)
- [What is Redux Thunk](Redux/redux-thunk-basics.md)
- [what-is-thunk-in-programming](Redux/redux-thunk-what-is-thunk-in-programming.md)
- [What is Store](Redux/Store.md)
- [Why-Redux-needs-reducers-to-be-pure functions](React/immutable-state-store-in-React-Redux/Why-Redux-needs-reducers-to-be-pure-functions-VERY-GOOD-EXPLANATIONS.md)
- [immutable-state-store-in-React-Redux-2](React/immutable-state-store-in-React-Redux/immutable-state-store-in-React-Redux-2.md)
- [immutable-state-store-in-React-Redux-Pass-by-Reference-shallow-comapre](React/immutable-state-store-in-React-Redux/immutable-state-store-in-React-Redux-Pass-by-Reference-shallow-comapre.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common Angular Interview Topics & Questions

(Below Links are all within this Repository)

- [AsyncPipe-fundamentals](Angular-Topics-Interview/AsyncPipe/AsyncPipe-fundamentals.md)
- [AsyncPipe-basic-Oberservable-use-case](Angular-Topics-Interview/AsyncPipe/AsyncPipe-basic-Oberservable-use-case.md)
- [converting-a-subscribe-to-asyncPipe-1](Angular-Topics-Interview/AsyncPipe/converting-a-subscribe-to-asyncPipe-1.md)
- [converting-a-subscribe-to-asyncPipe-Simplest-use-case](Angular-Topics-Interview/AsyncPipe/converting-a-subscribe-to-asyncPipe-Simplest-use-case.md)
- [Converting-a-subscribe-to-asyncPipe-3](Converting-a-subscribe-to-asyncPipe-3)
- [Component-Communications-via-Input](Angular-Topics-Interview/Component-Data-Communications/Component-Communications-via-Input.md)
- [Component-Communications-via-Output-EventEmitter](Angular-Topics-Interview/Component-Data-Communications/Component-Communications-via-Output-EventEmitter.md)
- [ContentChildren-basics](Angular-Topics-Interview/Decorators/ContentChildren-basics.md)
- [decorators-basics-in-angular](Angular-Topics-Interview/Decorators/decorators-basics-in-angular.md)
- [decorators-basics-in-typescript](Angular-Topics-Interview/Decorators/decorators-basics-in-typescript.md)
- [Property-decorators-basics-in-angular-1](Angular-Topics-Interview/Decorators/Property-decorators-basics-in-angular-1.md)
- [Property-Decorators-Typescript-1](Angular-Topics-Interview/Decorators/Property-Decorators-Typescript-1.md)
- [Property-Decorators-Typescript-2](Angular-Topics-Interview/Decorators/Property-Decorators-Typescript-2.md)
- [QueryList-basics](Angular-Topics-Interview/Decorators/QueryList-basics.md)
- [TemplateRef-basics-1](Angular-Topics-Interview/Decorators/TemplateRef-basics-1.md)
- [TemplateRef-basics-2](Angular-Topics-Interview/Decorators/TemplateRef-basics-2.md)
- [ViewChild-basics](Angular-Topics-Interview/Decorators/ViewChild-basics.md)
- [AfterViewInit-hook](Angular-Topics-Interview/Life-Cycle-Hooks/AfterViewInit-hook.md)
- [ngOnChanges-Fundamentals](Angular-Topics-Interview/Life-Cycle-Hooks/ngOnChanges-Fundamentals.md)
- [ngOnChanges-SimpleChanges_interface](Angular-Topics-Interview/Life-Cycle-Hooks/ngOnChanges-SimpleChanges_interface.md)
- [ngOnInit-vs-Constructor](Angular-Topics-Interview/Life-Cycle-Hooks/ngOnInit-vs-Constructor.md)
- [ngOnInit-vs-ngAfterViewInit](Angular-Topics-Interview/Life-Cycle-Hooks/ngOnInit-vs-ngAfterViewInit.md)
- [ngOnChange-BestPractice](Angular-Topics-Interview/ng-Best_Practice/ngOnChange-BestPractice.md)
- [cold-vs-hot-observable](Angular-Topics-Interview/Observables/cold-vs-hot-observable.md)
- [examples-cancellable-with-takeUntil](Angular-Topics-Interview/Observables/examples-cancellable-with-takeUntil.ts)
- [examples-observable-is-Lazy](Angular-Topics-Interview/Observables/examples-observable-is-Lazy.ts)
- [Observable-basics](Angular-Topics-Interview/Observables/Observable-basics.md)
- [Observable-simple-implementation-1](Angular-Topics-Interview/Observables/Observable-simple-implementation-1.md)
- [Observable-vs-Promises](Angular-Topics-Interview/Observables/Observable-vs-Promises.md)
- [subscribe-method](Angular-Topics-Interview/Observables/subscribe-method.md)
- [Reading-Route-Parameters in Angular](Angular-Topics-Interview/Routing/Reading-Route-Parameters.md)
- [rx-js-best-practice - Dont-pass-streams-to-components-directly](Angular-Topics-Interview/rx-js/best-practices-common-pattern/Dont-pass-streams-to-components-directly.md)
- [subscribe_pattern-with-take(1)](<Angular-Topics-Interview/rx-js/best-practices-common-pattern/subscribe_pattern-with-take(1).md>)
- [Best Practice - when_using_async_pipe_no_need_to_unsubscribe](Angular-Topics-Interview/rx-js/best-practices-common-pattern/when_using_async_pipe_no_need_to_unsubscribe.md)
- [Is there a need to unsubscribe from the Observable the Angular HttpClient's methods return?](Angular-Topics-Interview/rx-js/angular-httpclient-unsubscribe.md)
- [combineLatest-basics](Angular-Topics-Interview/rx-js/combineLatest-basics.md)
- [debounceTime-usecase-input-validation](Angular-Topics-Interview/rx-js/debounceTime-usecase-input-validation.md)
- [pipe-basics-how-it-works-with-example](Angular-Topics-Interview/rx-js/pipe-basics-how-it-works-with-simple-good-example.md)
- [More on pipe-function-1](Angular-Topics-Interview/rx-js/pipe-function-1.md)
- [More on pipe-function-2](Angular-Topics-Interview/rx-js/pipe-function-2.md)
- [More on pipe-function-3](Angular-Topics-Interview/rx-js/pipe-function-3.md)
- [retryWhen - I want to retry an api call 10 times (waiting one second since it fails until next execution)](Angular-Topics-Interview/rx-js/retryWhen-1.md)
- [More on retryWhen-basics](Angular-Topics-Interview/rx-js/retryWhen-basics-2.md)
- [switchMap-get-route-params](Angular-Topics-Interview/rx-js/switchMap-get-route-params.md)
- [switchMap-good-example-for-user-input](Angular-Topics-Interview/rx-js/switchMap-good-example-for-user-input.md)
- [take(1)](<Angular-Topics-Interview/rx-js/take(1).md>)
- [class-in-typescript](Angular-Topics-Interview/TypeScript/Class-Definitions/class-in-typescript.md)
- [generic-typescript-class-definition](Angular-Topics-Interview/TypeScript/Class-Definitions/generic-typescript-class-definition.md)
- [get-method-in-typescript](Angular-Topics-Interview/TypeScript/Class-Definitions/get-method-in-typescript.md)
- [proxy-in-typescript](Angular-Topics-Interview/TypeScript/Class-Definitions/proxy-in-ts.md)
- [typescript - when-a-method-returns-boolean](Angular-Topics-Interview/Useful_Pattern_Observable/when-a-method-returns-boolean.md)
- [ViewEncapsulation-Basics](Angular-Topics-Interview/ViewEncapsulation/ViewEncapsulation-Basics.md)
- [ViewEncapsulation-None](Angular-Topics-Interview/ViewEncapsulation/ViewEncapsulation-None.md)
- [component-selectors-different-way](Angular-Topics-Interview/component-selectors-different-way.md)
- [ControlValueAccessor_basics](Angular-Topics-Interview/ControlValueAccessor_basics.md)
- [directive-basics](Angular-Topics-Interview/directive-basics.md)
- [host-selector](Angular-Topics-Interview/host-selector.md)
- [ng-content](Angular-Topics-Interview/ng-content.md)
- [ngModel-basics-1](Angular-Topics-Interview/ngModel-basics-1.md)
- [ngModel-basics-2](Angular-Topics-Interview/ngModel-basics-2.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common MongoDB Interview Topics & Questions

(Below Links are all within this Repository)

- [aggregation-in-mongodb](MongoDB/aggregation-in-mongodb.md)
- [delete-single-document-from-collection](MongoDB/delete-single-document-from-collection.md)
- [GridFS-storing-files-in-mongo](MongoDB/GridFS-storing-files-in-mongo.md)
- [indexing-in-mongo](MongoDB/indexing-in-mongo.md)
- [mongodb-quick-comands-cheat-sheet](MongoDB/mongodb-quick-comands-cheat-sheet.md)
- [mongoose-exec-method](MongoDB/mongoose-exec-method.md)
- [referencing-other-model-populate-method-mongoose](MongoDB/populate-method-mongoose-referencing-other-model.md)
- [referencing-another-schema-in-Mongoose-1](MongoDB/referencing-another-schema-in-Mongoose-1.md)
- [More on referencing-another-schema-in-Mongoose-1](MongoDB/referencing-another-schema-in-Mongoose-2.md)
- [sharding-in-mongodb](MongoDB/sharding-in-mongodb.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common HTML Interview Topics & Questions

(Below Links are all within this Repository)

- [Collection-of-HTML-Interview-Questions](HTML/Collection-of-HTML-Interview-Questions.md)
- [DOM-fundamentals](HTML/DOM-fundamentals.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common CSS Interview Topics & Questions

(Below Links are all within this Repository)

- [Collection-of-CSS-Questions](CSS/Collection-of-CSS-Questions.md)
- [BEM-Model](BEM-Model)
- [box-Model](box-Model)
- [flexbox](CSS/flexbox.md)
- [flexbox-example-centerting-elements](CSS/flexbox-example-centerting-elements.md)
- [Grid-Layout](CSS/Grid-Layout.md)
- [left-vs-margin-left](CSS/left-vs-margin-left.md)
- [not-pseudo-class-selector](CSS/not-pseudo-class-selector.md)
- [pseudo-class](CSS/pseudo-class.md)
- [relative-absolute-fixed-position](CSS/relative-absolute-fixed-position.md)
- [relative-positioning-basic-good-notes](CSS/relative-positioning-basic-good-notes.md)
- [rem-unit-basics-and-converting-px](CSS/rem-unit-basics-and-converting-px.md)
- [z-index](CSS/z-index.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most common Git and Github related Interview Topics & Questions

(Below Links are all within this Repository)

- [What is git stash](Git-and-Github/git-stash.md)
- [What is git rebase](Git-and-Github/git-rebase/git-rebase.md)
- [Resolving-merge-conflicts during git-rebase-](Git-and-Github/git-rebase/git-rebase-Resolving-merge-conflicts.md)
- [git-squash-many-commits-to-a-single-one-before-PR](Git-and-Github/PR-Flow/git-squash-many-commits-to-a-single-one-before-PR.md)
- [Pull-Requst-Steps-to-take-in-a-team-before-submitting-PR](Git-and-Github/PR-Flow/Pull-Requst-Steps-to-take-in-a-team-before-submitting-PR.md)
- [Update-cloned-repo-in-local-machine-with-latest-master-branch](Git-and-Github/PR-Flow/Update-cloned-repo-in-local-machine-with-latest-master-branch.md)
- [git-staging-area](Git-and-Github/git-staging-area.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Understanding the Theory and the fundamentals of some super-popular Algorithm questions

- :link: [Big O Cheatsheet](http://bigocheatsheet.com/)
  :link: [Quick Big O understanding for coding interviews](https://medium.com/@jayshah_84248/big-o-for-coding-interviews-e6ca8897f926)
- :link: [developers/sorting-algorithms](https://www.toptal.com/developers/sorting-algorithms)
- :link: [tackling-javascript-algorithms](https://medium.com/@yanganif/tackling-javascript-algorithms-66f1ac9770dc)
- :link: [sorting-algorithms-in-javascript](https://github.com/benoitvallon/computer-science-in-javascript/tree/master/sorting-algorithms-in-javascript)
- :link: [Learn-Data_Structure-Algorithm-by-Javascript](https://github.com/Algorithm-archive/Learn-Data_Structure-Algorithm-by-Javascript)
- :book: [Grokking Algorithms](https://www.goodreads.com/book/show/22847284-grokking-algorithms-an-illustrated-guide-for-programmers-and-other-curio)
- :link: [Algorithms Visualization](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html)
- :link: [coding-interviews-for-dummies](https://medium.freecodecamp.org/coding-interviews-for-dummies-5e048933b82b)
- :link: [educative.io/collection/page/](https://www.educative.io/collection/page/5642554087309312/5679846214598656/240002)
- :link: [Karp_algorithm](https://www.wikiwand.com/en/Rabin%E2%80%93Karp_algorithm)
- :link: [www.geeksforgeeks.org/top-algorithms-and-data-structures-for-competitive-programming/](https://www.geeksforgeeks.org/top-algorithms-and-data-structures-for-competitive-programming/)
- :link: [best javascript-algorithms github repo](https://github.com/trekhleb/javascript-algorithms)
- :link: [14-patterns-to-ace-any-coding-interview-question](https://hackernoon.com/14-patterns-to-ace-any-coding-interview-question-c5bb3357f6ed)
- :link: [Grokking the Coding Interview: Patterns for Coding Questions](https://www.educative.io/collection/5668639101419520/5671464854355968)
- :link: [https://github.com/amejiarosario/dsa.js-data-structures-algorithms-javascript](https://github.com/amejiarosario/dsa.js-data-structures-algorithms-javascript)
- :link: [coding-interview-university](https://github.com/jwasham/coding-interview-university)
- :link: [reactjs-interview-questions](https://github.com/sudheerj/reactjs-interview-questions)
- :link: [Front-end-Developer-Interview-Questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions)
- :link: [front-end-interview-handbook](https://github.com/yangshun/front-end-interview-handbook) - Almost complete answers to "Front-end Job Interview Questions" which you can use to interview potential candidates, test yourself or completely ignore

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Github Repositories with large collections of problems-and-solutions of them most popular Interview challenges

- :link: [Algorithms-Leetcode-Javascript](https://github.com/ignacio-chiazzo/Algorithms-Leetcode-Javascript)
- :link: [Algorithm-in-JavaScript](https://github.com/rohan-paul/Algorithm-in-JavaScript)
- :link: [Javascript-Challenges](https://github.com/rohan-paul/Javascript-Challenges)
- :link: [JS-Challenges](https://github.com/rohan-paul/The-Hacking-School-Full-Stack-Bootcamp-Projects/tree/master/JS-Challenges)
- :link: [code-problems-solutions](https://github.com/mkshen/code-problems-solutions)
- :link: [some common problems](https://gist.github.com/Smakar20?page=1)
- :link: [Cracking the Coding Interview - Javascript](https://github.com/careercup/CtCI-6th-Edition-JavaScript)
- :link: [interview-questions-in-javascript](https://github.com/kennymkchan/interview-questions-in-javascript)
- :link: [javascript-interview-questions](https://github.com/sudheerj/javascript-interview-questions)
- :link: [javascript-Exercises](https://github.com/kolodny/exercises)
- :link: [30-seconds-of-interview](https://github.com/30-seconds/30-seconds-of-interviews)
- :link: [js--interview-questions](https://github.com/vvscode/js--interview-questions)
- :link: [JavaScript-Code-Challenges](https://github.com/sadanandpai/javascript-code-challenges)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Overall multi-factor approach for winning this huge challenge and a great journey of getting the first Developer Job

- :link: [medium.com/javascript-scene/every-developer-needs-a-code-portfolio](https://medium.com/javascript-scene/every-developer-needs-a-code-portfolio-cc79c3d92110)
  :link: [Collection of Resources for Interview preparations and practices](https://medium.com/@jayshah_84248/how-to-do-well-in-a-coding-interview-2bcd67e93cb5)
  :link: [How I cleared the Amazon SDE 2 interview](https://medium.com/@rachit138/how-i-cleared-the-amazon-sde-2-interview-f82a33706ff4)
  :link: [How I got 7 Job Offers in 8 Weeks ](https://blog.usejournal.com/how-i-got-7-job-offers-in-8-weeks-part-1-please-interview-me-21e6f4ded106)
- :link: [/master-the-javascript-interview-soft-skills](https://medium.com/javascript-scene/master-the-javascript-interview-soft-skills-a8a5fb02c466)
- :link: [google-lost-a-chance-to-hire-me-finally-amazon-hired-me](https://medium.com/@jayshah_84248/google-lost-a-chance-to-hire-me-finally-amazon-hired-me-e35076c73fe2)
- :link: [the-best-way-to-learn-to-code-is-to-code-learn-app-architecture-by-building-apps](https://medium.com/javascript-scene/the-best-way-to-learn-to-code-is-to-code-learn-app-architecture-by-building-apps-7ec029db6e00)
- :link: [7-key-steps-to-getting-your-first-software-engineering-job](https://medium.freecodecamp.org/7-key-steps-to-getting-your-first-software-engineering-job-6ef80543cad9)
- :link: [5-key-learnings-from-the-post-bootcamp-job-search](https://medium.freecodecamp.org/5-key-learnings-from-the-post-bootcamp-job-search-9a07468d2331)
- :link: [how-to-get-your-first-developer-job-in-4-months](https://medium.freecodecamp.org/https-medium-com-samwcoding-how-to-get-your-first-developer-job-in-4-months-ec86da6e5d9a)
- :link: [how-to-land-your-first-dev-job-even-if-you-don-t-have-a-cs-degree](https://medium.com/swlh/how-to-land-your-first-dev-job-even-if-you-don-t-have-a-cs-degree-e83d08db4615)
- :link: [how-to-land-a-top-notch-tech-job-as-a-student](https://medium.freecodecamp.org/how-to-land-a-top-notch-tech-job-as-a-student-5c97fec82f3d)
- :link: [unlocking-the-javascript-code-interview-an-interviewer-perspective](https://medium.com/appsflyer/unlocking-the-javascript-code-interview-an-interviewer-perspective-f4fe06246b29)
- :link: [get-that-job-at-google.html](https://steve-yegge.blogspot.com/2008/03/get-that-job-at-google.html)
- :link: [i-failed-my-effing-coding-interview-ab720c339c8a](https://blog.usejournal.com/i-failed-my-effing-coding-interview)
- :link: [how-i-landed-a-full-stack-developer-job-without-a-tech-degree-or-work-experience](https://medium.freecodecamp.org/how-i-landed-a-full-stack-developer-job-without-a-tech-degree-or-work-experience-6add97be2051)
- :link: [here-are-4-best-ways-to-apply-for-software-engineer-jobs-and-exactly-how-to-use-them](https://medium.freecodecamp.org/here-are-4-best-ways-to-apply-for-software-engineer-jobs-and-exactly-how-to-use-them-a644a88b2241)
- :link: [how-to-get-a-tech-job-with-no-previous-work-experience](https://medium.freecodecamp.org/how-to-get-a-tech-job-with-no-previous-work-experience-6d3d7d25e1)
- :link: [the-hard-thing-about-learning-hard-things](https://medium.freecodecamp.org/the-hard-thing-about-learning-hard-things-168e655ac7f2)
- :link: [70-job-find-websites-for-developers-other-tech-professionals](https://medium.com/@traversymedia/70-job-find-websites-for-developers-other-tech-professionals-34cdb45518be)
- :link: [YouTube - 70+ Websites To Find Developer Jobs](https://www.youtube.com/watch?v=xKOPqWWmxEQ)
- :link: [YouTube - I'm 47 And Now I Want to be a Programmer](https://www.youtube.com/watch?v=EJDZ2L95Sjo)
- :link: [YouTube - How To Be A Well-Paid Programmer In 1 Year?](https://www.youtube.com/watch?v=V71Cv7mjgfI)
- :link: [the-secret-to-being-a-top-developer-is-building-things-heres-a-list-of-fun-apps-to-build](https://medium.freecodecamp.org/the-secret-to-being-a-top-developer-is-building-things-heres-a-list-of-fun-apps-to-build-aac61ac0736c)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

### Other important resources

- :link: [javascript cheatsheet](http://overapi.com/javascript)
- :link: [Super useful es6-cheatsheet](https://github.com/DrkSephy/es6-cheatsheet)
- :link: [freeCodeCamp Guide](https://guide.freecodecamp.org/)
- :link: [functional-programming-in-js-map-filter-reduce](https://hackernoon.com/functional-programming-in-js-map-filter-reduce-pt-5-308a205fdd5f)
- :link: [you-must-understand-these-14-javasript-functions](https://medium.com/javascript-in-plain-english/you-must-understand-these-14-javasript-functions-1f4fa1c620e2)
- :link: [developer.mozilla.org/JavaScript/A_re-introduction_to_JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)
- :link: [developer.mozilla.org/docs/JavaScript/Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
- :book: [You-Dont-Know-JS](https://github.com/getify/You-Dont-Know-JS)
- :link: [GeeksForGeeks](https://www.geeksforgeeks.org/)
- :link: [Dev.To](https://dev.to/)
- :link: [Stack Overflow](https://stackoverflow.com/)
- :link: [Dzone](https://dzone.com/)
- :link: [https://scotch.io/](https://scotch.io/)
- :link: [https://30secondsofcode.org/](https://30secondsofcode.org/)
- :link: [Front-end JavaScript Interviews in 2018–19](https://blog.webf.zone/front-end-javascript-interviews-in-2018-19-e17b0b10514)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Coding Challenge Practice Platforms

- :link: [interviewing.io](https://interviewing.io/)
- :link: [Leetcode](https://leetcode.com/)
- :link: [HackerRank](https://www.hackerrank.com/)
- :link: [CodeForces](http://codeforces.com/)
- :link: [CodeChef](https://www.codechef.com)
- :link: [Coderbyte](https://coderbyte.com/)
- :link: [CodinGame](https://www.codingame.com/)
- :link: [Cs Academy](https://csacademy.com/)
- :link: [Daily Coding Problem](https://www.dailycodingproblem.com/)
- :link: [Spoj](https://spoj.com/)
- :link: [HackerEarth](https://hackerearth.com/)
- :link: [TopCoder](https://www.topcoder.com/)
- :link: [Codewars](https://codewars.com/)
- :link: [Exercism](http://www.exercism.io/)
- :link: [CodeFights](https://codefights.com/)
- :link: [Project Euler](https://projecteuler.net/)
- :link: [Interviewcake](https://www.interviewcake.com/)
- :link: [InterviewBit](https://www.interviewbit.com/)
- :link: [uCoder](ucoder.com.br)
- :link: [LintCode](https://www.lintcode.com/)
- :link: [CodeCombat](https://codecombat.com/)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## More curated list of general resources for JavaScript Interviews

- :link: [Follow this list in Twitter - These are some great developers who regularly gives a lot of useful advice for a wannabe dev regularly](https://twitter.com/i/lists/1273224332521717761)

- :link: [https://www.thatjsdude.com/interview/js1.html](https://www.thatjsdude.com/interview/js1.html) - JS: Interview Algorithm Part-1

- :link: [https://www.thatjsdude.com/interview/js2.html](https://www.thatjsdude.com/interview/js2.html) - JS: Basics and Tricky Questions Part-2: intermediate

- :link: [https://www.thatjsdude.com/interview/dom.html](https://www.thatjsdude.com/interview/dom.html) - JS: Interview Questions Part-3

- :link: [https://medium.freecodecamp.org/3-questions-to-watch-out-for-in-a-javascript-interview-725012834ccb](https://medium.freecodecamp.org/3-questions-to-watch-out-for-in-a-javascript-interview-725012834ccb) - 3 JavaScript questions to watch out for during coding interviews

- :link: [https://github.com/ggomaeng/awesome-js](https://github.com/ggomaeng/awesome-js) - A curated list of javascript fundamentals and algorithms

- :link: [https://github.com/Chalarangelo/30-seconds-of-code](https://github.com/Chalarangelo/30-seconds-of-code) - Curated collection of useful Javascript snippets that you can understand in 30 seconds or less.

- :link: [https://medium.com/dev-bits/a-perfect-guide-for-cracking-a-javascript-interview-a-developers-perspective-23a5c0fa4d0d](https://medium.com/dev-bits/a-perfect-guide-for-cracking-a-javascript-interview-a-developers-perspective-23a5c0fa4d0d) - A perfect guide for cracking a JavaScript interview - A developer’s perspective

- :link: [master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9](https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9) - Master the JavaScript Interview: What’s the Difference Between Class & Prototypal Inheritance?

- :link: [https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36) - Master the JavaScript Interview: What is a Closure?

- :link: [https://medium.com/javascript-scene/master-the-javascript-interview-what-is-function-composition-20dfb109a1a0](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-function-composition-20dfb109a1a0) - Master the JavaScript Interview: What is Function Composition?

- :link: [https://medium.com/javascript-scene/common-misconceptions-about-inheritance-in-javascript-d5d9bab29b0a](https://medium.com/javascript-scene/common-misconceptions-about-inheritance-in-javascript-d5d9bab29b0a) - Common Misconceptions About Inheritance in JavaScript

- :link: [https://dev.to/arnavaggarwal/10-javascript-concepts-you-need-to-know-for-interviews?utm_source=hashnode.com](https://dev.to/arnavaggarwal/10-javascript-concepts-you-need-to-know-for-interviews?utm_source=hashnode.com) - 10 JavaScript concepts you need to know for interviews

- :link: [https://hackernoon.com/a-quick-introduction-to-functional-javascript-7e6fe520e7fa](https://hackernoon.com/a-quick-introduction-to-functional-javascript-7e6fe520e7fa) - A Quick Introduction to Functional Javascript

- :link: [https://github.com/ganqqwerty/123-Essential-JavaScript-Interview-Question](https://github.com/ganqqwerty/123-Essential-JavaScript-Interview-Questions) - 123-Essential-JavaScript-Interview-Question

- :link: [https://www.toptal.com/javascript/interview-questions](https://www.toptal.com/javascript/interview-questions) - 37 Essential JavaScript Interview Questions

- :link: [https://medium.com/coderbyte/a-tricky-javascript-interview-question-asked-by-google-and-amazon-48d212890703](https://medium.com/coderbyte/a-tricky-javascript-interview-question-asked-by-google-and-amazon-48d212890703) - A Tricky JavaScript Interview Question Asked by Google and Amazon

- :link: [Many tricky and common javascript-questions](https://github.com/lydiahallie/javascript-questions)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Most frequently asked concepts for Front End Engineering Interview

1. call, apply and bind method
2. Polyfill for bind method
3. Currying
4. Debouncing
5. async vs defer
6. Event Bubbling & Capturing
7. Prototype & Prototypal Inheritance
8. Throttling
9. Thinking Recursively
10. Local Storage and Session Storage
11. CORS
12. sum(a)(b)(c)...(n)
13. Web Storage APIs
14. Event Loop
15. Web Sockets
16. Closures
17. Callbacks & Promises
18. Revise everything again
19. Difference between deep clone and shallow clone and how to write your own deep clone fucntion/polyfill for deepclone
20. ES6 data structures such as Map and Set. In certain cases, Map is much better suited than an Object. Probably even Server Sent Events would be a good thing to know.
21. Observable and subscribers, subject, behaviour subject and repeatable subject

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## List of sites where you can hunt for a developer job

- :link: AngelList - https://angel.co
- :link: GitHub: http://jobs.github.com
- :link: Mashable: http://jobs.mashable.com/jobs
- :link: Indeed: http://indeed.com
- :link: StackOverflow: http://stackoverflow.com/jobs
- :link: LinkedIn: http://linkedIn.com
- :link: Glassdoor: http://glassdoor.com
- :link: Dice: http://dice.com
- :link: Monster: http://monster.com
- :link: Simply Hired: http://simplyhired.com
- :link: Toptal: https://toptal.com
- :link: Hired - https://hired.com
- :link: Muse: http://themuse.com/jobs
- :link: Tuts+: http://jobs.tutsplus.com
- :link: Krop: http://krop.com
- :link: PowerToFly: http://powertofly.com/jobs
- :link: Developers for Hire: http://developersforhire.com
- :link: Codepen job board: https://codepen.io/jobs
- :link: http://Joblist.app: http://joblist.app
- :link: Fullstack Job: http://fullstackjob.com
- :link: Authentic jobs: http://authenticjobs.com
- :link: Jobspresso: http://jobspresso.co
- :link: Jobs in Europe: http://landing.jobs
- :link: TripleByte: https://triplebyte.com

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Want a startup job?

- :link: AngelList: http://angel.co/jobs
- :link: Product Hunt: http://producthunt.com/jobs
- :link: Startup Hire: http://startuphire.com
- :link: Startupers: http://startupers.com
- :link: YCombinator: http://news.ycombinator.com/jobs

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Best places to job hunt for remote jobs:

- :link: FlexJobs: http://flexjobs.com
- :link: WeWorkRemotely: http://weworkremotely.com
- :link: RemoteOk: http://remoteok.io/remote-dev-jobs
- :link: Stackoverflow: http://stackoverflow.com/jobs/remote-developer-jobs
- :link: Working Nomads: http://workingnomads.co/remote-development-jobs
- :link: Remote . co - https://remote.co/remote-jobs/developer/
- :link: Remoters: http://remoters.net/jobs/software-development
- :link: JS Remotely: http://jsremotely.com
- :link: Front-end remote: http://frontendremotejobs.com
- :link: IWantRemote: http://iwantremote.com
- :link: DailyRemote - https://dailyremote.com
- :link: Remotive: https://remotive.io/remote-jobs/software-dev
- :link: Outsourcely: http://outsourcely.com/remote-web-development-jobs
- :link: Pangian: https://pangian.com/job-travel-remote/
- :link: RemoteLeads: http://remoteleads.io
- :link: Remote Talent: http://remotetalent.co/jobs
- :link: JustRemote: https://justremote.co/remote-developer-jobs
- :link: RemoteLeaf - https://remoteleaf.com
- :link: Sitepoint - https://sitepoint.com/jobs/

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Here are a few places to hunt for ios, react, vue and more

- :link: iOS: http://iosdevjobs.com
- :link: React: http://reactjobboard.com
- :link: Vue jobs: http://vuejobs.com
- :link: Ember: http://jobs.emberjs.com
- :link: Python Jobs - http://python.org/jobs

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Want a list of just JavaScript jobs?

- :link: JavaScript job XYZ: http://javascriptjob.xyz
- :link: Javascript remotely: http://jsremotely.com

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Are you looking for a junior dev job?

- :link: JrDevJobs: http://jrdevjobs.com
- :link: Stackoverflow Junior jobs: https://stackoverflow.com/jobs/junior-developer-jobs

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Women focused job boards!

- :link: Women Who Code: http://womenwhocode.com/jobs
- :link: Tech Ladies - https://hiretechladies.com

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Want a job as a freelance dev? Here's a list

- :link: Freelancer: http://freelancer.com/jobs
- :link: Upwork: http://upwork.com
- :link: FlexJobs: http://flexjobs.com/jobs
- :link: FreelancerMap: http://freelancermap.com
- :link: http://Gun.io: http://gun.io
- :link: Guru: http://guru.com/d/jobs

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Some useful websites for programmers

<li><a href="#when-you-get-stuck">When you get stuck</a></li>
<li><a href="#for-small-project-ideas">For small project ideas</a></li>
<li><a href="#general-coding-advice">General Coding advice</a></li>
<li><a href="#coding-style">Coding Style</a></li>
<li><a href="#general-good-articles">General Good Articles</a></li>

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## When you get stuck

- [Codementor](https://www.codementor.io) : A mentorship community to learn from fellow developers via live 1:1 help and more.
- [devRant](https://www.devrant.io) : Community where you can rant and release your stress
- [Learn Anything](https://learn-anything.xyz) : Community curated knowledge graph of best paths for learning anything
- [Quora](https://www.quora.com) : A place to share knowledge and better understand the world
- [Stack Overflow](https://stackoverflow.com) : subscribe to their weekly newsletter and any other topic which you find interesting

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Ideas For small project ideas

- [freeCodeCamp | React project ideas](https://medium.freecodecamp.org/every-time-you-build-a-to-do-list-app-a-puppy-dies-505b54637a5d?gi=c786640fbd11) : 27 fun app ideas you can build while learning React.
- [martyr2s-mega-project-ideas-list](http://www.dreamincode.net/forums/topic/78802-martyr2s-mega-project-ideas-list/) : contains about 125 project ideas from beginner to intermediate level.
- [karan/Projects](https://github.com/karan/Projects) : a large collection of small projects for beginners with
- [Wrong "big projects" for beginners](http://rodiongork.tumblr.com/post/108155476418/wrong-big-projects-for-beginners) : How to choose where to start
- [vicky002/1000-Projects](https://github.com/vicky002/1000_Projects) : Mega List of practical projects that one can solve in any programming language!
- [reddit.com/r/AppIdeas](https://www.reddit.com/r/AppIdeas/) : A place to discuss ideas for applications, for bored developers.
- [reddit.com/r/SomebodyMakeThis](https://www.reddit.com/r/SomebodyMakeThis/) : A home for ideas by people who lack time, money, or skills.

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## General Coding advice

- [10-ways-to-be-a-better-developer](https://stephenhaunts.files.wordpress.com/2014/04/10-ways-to-be-a-better-developer.png) : Ways to become a better dev!
- [Code Review Best Practices](https://www.kevinlondon.com/2015/05/05/code-review-best-practices.html) : Kevin London's blog
- [Design Patterns](https://sourcemaking.com/design_patterns) : Design Patterns explained in detail with examples.
- [Develop for Performance](http://developforperformance.com) : High-performance computing techniques for software architects and developers
- [How to become a programmer or the art of Googling well](https://okepi.wordpress.com/2014/08/21/how-to-become-a-programmer-or-the-art-of-googling-well/) : How to become a programmer or the art of Googling well
- [How to escape tutorial purgatory as a new developer — or at any time in your career](https://medium.freecodecamp.org/how-to-escape-tutorial-purgatory-as-a-new-developer-or-at-any-time-in-your-career-e3a4b2384a40) : How to escape tutorial purgatory
- [JS Project Guidelines](https://github.com/wearehive/project-guidelines) : A set of best practices for JavaScript projects.
- [Learn to Code With Me](https://learntocodewith.me) : A comprehensive site resource by Laurence Bradford for developers who aims to build a career in the tech world
- [Lessons From A Lifetime Of Being A Programmer](http://thecodist.com/article/lessons_from_a_lifetime_of_being_a_programmer) : The Codist Header Lessons From A Lifetime Of Being A Programmer
- [Programming Principles](https://webpro.github.io/programming-principles/) : Categorized overview of Programming Principles & Patterns
- [Software design pattern](https://en.wikipedia.org/wiki/Software_design_pattern) : The entire collection of Design Patterns.
- [Things I Wish Someone Had Told Me When I Was Learning How to Code — Free Code Camp](https://medium.freecodecamp.com/things-i-wish-someone-had-told-me-when-i-was-learning-how-to-code-565fc9dcb329?gi=fc6d0a309be) : What I’ve learned from teaching others
- [What every computer science major should know](http://matt.might.net/articles/what-cs-majors-should-know/) : The Principles of Good Programming
- [Working as a Software Developer](https://henrikwarne.com/2012/12/12/working-as-a-software-developer/) : Henrik Warne's blog
- [The Open Web Application Security Project (OWASP)](https://www.owasp.org) : OWASP is an open community dedicated to enabling organizations to conceive, develop, acquire, operate, and maintain applications that can be trusted.
- [14 Things I Wish I’d Known When Starting with MongoDB](https://www.infoq.com/articles/Starting-With-MongoDB/)
- [40 Keys Computer Science Concepts Explained In Layman’s Terms](http://carlcheo.com/compsci)
- [A Gentle Introduction To Graph Theory](https://dev.to/vaidehijoshi/a-gentle-introduction-to-graph-theory)
- [A programmer-friendly language that compiles to Lua.](http://moonscript.org)
- [A Software Developer’s Reading List](https://stevewedig.com/2014/02/03/software-developers-reading-list/) : Some good books and links in there.
- [Code a TCP/IP stack](http://www.saminiir.com/lets-code-tcp-ip-stack-5-tcp-retransmission/) : Let's code a TCP/IP stack, 5: TCP Retransmission
- [Codewords.recurse](https://codewords.recurse.com/issues/four/the-language-of-choice) : The language of choice
- [Data structure and Algorithms](https://techiedelight.quora.com/500-Data-Structures-and-Algorithms-practice-problems-and-their-solutions) : List of some algorithms and data structures with their solutions.
- [Dive into the byte code](https://www.wikiwand.com/en/Java_bytecode)
- [Expectations of a Junior Developer](http://blog.thefirehoseproject.com/posts/expectations-of-a-junior-developer/)
- [Getting Started with MongoDB – An Introduction](https://studio3t.com/knowledge-base/articles/mongodb-getting-started/)
- [Linux Inside](https://0xax.gitbooks.io/linux-insides/content/Booting/linux-bootstrap-1.html)
- [List of algorithms](https://www.wikiwand.com/en/List_of_algorithms)
- [Step by Step Guide to Database Normalization](https://www.databasestar.com/normalization-in-dbms/): A guide to database normalization.
- [The Key To Accelerating Your Coding Skills](http://blog.thefirehoseproject.com/posts/learn-to-code-and-be-self-reliant/)
- [Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [We are reinventing the retail industry through innovative technology](http://multithreaded.stitchfix.com)
- [What every programmer absolutely, positively needs to know about encodings and character sets to work with text](http://kunststube.net/encoding/)
- [What every programmer should know about memory - PDF](http://futuretech.blinkenlights.nl/misc/cpumemory.pdf)
- [Why fast pages are important](https://fly.io/articles/why-fast-pages-are-important/) : Why App Speed Matters, Revenue
- [qotoqot - improving-focus](https://qotoqot.com/blog/improving-focus/) : How I got to 200 productive hours a month
- [Pixel Beat - Unix](http://www.pixelbeat.org/docs/unix-parallel-tools.html) : Parallel processing with Unix tools
- [Learning Vim](https://hackernoon.com/learning-vim-what-i-wish-i-knew-b5dca186bef7) : What I Wish I Knew
- [Write a Kernel](http://arjunsreedharan.org/post/82710718100/kernel-101-lets-write-a-kernel) : Kernel 101 – Let’s write a Kernel
- [Learning JavaScript Design Patterns](https://addyosmani.com/resources/essentialjsdesignpatterns/book/) : the online version of the Learning JavaScript Design Patterns published by O'Reilly, released by the author Addy Osmani under CC BY-NC-ND 3.0
- [Working with Webhooks](https://requestbin.com/blog/working-with-webhooks/) : a comprehensive guide on webhooks

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Coding Style

- [Airbnb JS Style Guide](https://github.com/airbnb/javascript) : A mostly reasonable approach to JavaScript
- [Airbnb Ruby Style Guide](https://github.com/airbnb/ruby) : A ruby style guide by Airbnb
- [Ruby coding style guide](https://github.com/bbatsov/ruby-style-guide) : A community-driven Ruby coding style guide
- [Angular Style Guide](https://github.com/johnpapa/angular-styleguide/tree/master/a1) : Officially endorsed style guide by John Pappa
- [CS 106B Coding Style Guide](http://stanford.edu/class/archive/cs/cs106b/cs106b.1158/styleguide.shtml) : must see for those who create spaghetti
- [Debugging Faqs](http://www.umich.edu/~eecs381/generalFAQ/Debugging.html) : Check out how to debug your program
- [Directory of CS Courses (many with online lectures)](https://github.com/prakhar1989/awesome-courses) : Another online CS courses
- [Directory of Online CS Courses](https://github.com/ossu/computer-science) : Free online CS courses
- [Good C programming habits. • /r/C_Programming](https://www.reddit.com/r/C_Programming/comments/1vuubw/good_c_programming_habits/) : C programming habits to adopt
- [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
- [How to Report Bugs Effectively](https://www.chiark.greenend.org.uk/~sgtatham/bugs.html) : Want to report a bug but you don't how? Check out this post
- [What are some bad coding habits you would recommend a beginner avoid getting into?](https://www.reddit.com/r/learnprogramming/comments/1i4ds4/what_are_some_bad_coding_habits_you_would/) : Bad habits to avoid when you get start
- [PEP8 - Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/) : Style Guide for Python Code
- [Standard JS Style Guide](https://standardjs.com) : JavaScript style guide, with linter & automatic code fixer
- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html) : Google Python Style Guide
- [Aurelia Style Guide](https://github.com/behzad888/Aurelia-styleguide) : An Aurelia style guide by Behzad Abbasi(Behzad888)
- [Source Making ](https://sourcemaking.com/): Design Patterns & Refactoring
- [Refactoring Guru](https://refactoring.guru/): Refactoring And Design Patterns

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Collection of Leetcode Problem solution

- [github.com/AlanWei/LeetCode](https://github.com/AlanWei/LeetCode)
- [github.com/LiuL0703/algorithm/tree/master/LeetCode/JavaScript](https://github.com/LiuL0703/algorithm/tree/master/LeetCode/JavaScript)
- [github.com/ecmadao/algorithms/tree/master/leetcode](https://github.com/ecmadao/algorithms/tree/master/leetcode)
- [github.com/paopao2/leetcode-js](https://github.com/paopao2/leetcode-js)
- [github.com/cs1707/leetcode](https://github.com/cs1707/leetcode)
- [github.com/EasyHard/leetcodejs](https://github.com/EasyHard/leetcodejs)
- [github.com/fa-ge/leetcode](https://github.com/fa-ge/leetcode)
- [github.com/ktorng/AlgoInterviewPrep/tree/master/misc/LeetCode](https://github.com/ktorng/AlgoInterviewPrep/tree/master/misc/LeetCode)
- [github.com/bluesh/LeetCode](https://github.com/bluesh/LeetCode)
- [github.com/chihungyu1116/leetcode-javascript](https://github.com/chihungyu1116/leetcode-javascript)
- [github.com/didi0613/leetcode-javascript](https://github.com/didi0613/leetcode-javascript)
- [github.com/dnshi/Leetcode/tree/master/algorithms](https://github.com/dnshi/Leetcode/tree/master/algorithms)
- [github.com/xiaoyu2er/leetcode-js](https://github.com/xiaoyu2er/leetcode-js)
- [blog.sodhanalibrary.com/search/label/JavaScript](http://blog.sodhanalibrary.com/search/label/JavaScript)
- [github.com/imcoddy/leetcode](https://github.com/imcoddy/leetcode)
- [github.com/iwantooxxoox/leetcode](https://github.com/iwantooxxoox/leetcode)
- [github.com/karenpeng/leetCode](https://github.com/karenpeng/leetCode)
- [github.com/KMBaby-zyl/leetcode/tree/master/Algorithms](https://github.com/KMBaby-zyl/leetcode/tree/master/Algorithms)
- [github.com/MrErHu/Leetcode/tree/master/algorithms](https://github.com/MrErHu/Leetcode/tree/master/algorithms)
- [github.com/zzxboy1/leetcode/tree/master/algorithms](https://github.com/zzxboy1/leetcode/tree/master/algorithms)
- [github.com/loatheb/leetcode-javascript](https://github.com/loatheb/leetcode-javascript)
- [github.com/paopao2/leetcode-js](https://github.com/paopao2/leetcode-js)
- [github.com/theFool32/LeetCode](https://github.com/theFool32/LeetCode)
- [github.com/whwei/LeetCode](https://github.com/whwei/LeetCode)
- [github.com/jiangxiaoli/leetcode-javascript](https://github.com/jiangxiaoli/leetcode-javascript)
- [skyyen999.gitbooks.io/-leetcode-with-javascript/content/questions/299md.html](https://skyyen999.gitbooks.io/-leetcode-with-javascript/content/questions/299md.html)
- [github.com/HandsomeOne/LeetCode/tree/master/Algorithms](https://github.com/HandsomeOne/LeetCode/tree/master/Algorithms)
- [github.com/sean1093/leetcode/tree/master/algorithms](https://github.com/sean1093/leetcode/tree/master/algorithms)
- [github.com/zj972/leetcode/tree/master/code](https://github.com/zj972/leetcode/tree/master/code)
- [github.com/xiaoliwang/leetcode/tree/master/iojs](https://github.com/xiaoliwang/leetcode/tree/master/iojs)
- [github.com/dieface/leetcode/tree/master/javascript](https://github.com/dieface/leetcode/tree/master/javascript)
- [github.com/magicly/leetcode/tree/master/js](https://github.com/magicly/leetcode/tree/master/js)
- [github.com/LuciferChiu/leetcode/tree/master/solutions](https://github.com/LuciferChiu/leetcode/tree/master/solutions)
- [github.com/alenny/leetcode/tree/master/src](https://github.com/alenny/leetcode/tree/master/src)
- [github.com/kpman/leetcode/tree/master/src](https://github.com/kpman/leetcode/tree/master/src)
- [github.com/hijiangtao/LeetCode-with-JavaScript/tree/master/src](https://github.com/hijiangtao/LeetCode-with-JavaScript/tree/master/src)
- [www.cnblogs.com/Liok3187/default.html?page=1](https://www.cnblogs.com/Liok3187/default.html?page=1)
- [github.com/yuguo/LeetCode](https://github.com/yuguo/LeetCode)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## Collection of Cracking the Coding Interview Book Problem solution

- [github.com/sharlatta/cracking](https://github.com/sharlatta/cracking)
- [github.com/ammiranda/CrackingTheCodingInterview](https://github.com/ammiranda/CrackingTheCodingInterview)
- [github.com/bryclee/ctci](https://github.com/bryclee/ctci)
- [github.com/macalinao/node-ctci](https://github.com/macalinao/node-ctci)
- [github.com/seemaullal/CrackingTheCodingInterview-JS](https://github.com/seemaullal/CrackingTheCodingInterview-JS)
- [github.com/rcerf/MyCtci](https://github.com/rcerf/MyCtci)
- [github.com/SashaBayan/CCI](https://github.com/SashaBayan/CCI)
- [github.com/careercup/CtCI-6th-Edition-JavaScript-ES2015](https://github.com/careercup/CtCI-6th-Edition-JavaScript-ES2015)
- [github.com/ktorng/AlgoInterviewPrep/tree/master/CrackingTheCodingInterview](https://github.com/ktorng/AlgoInterviewPrep/tree/master/CrackingTheCodingInterview)
- [github.com/muddybarefeet/Cracking-the-Coding-Interview-Problems/tree/master/toyProblems](https://github.com/muddybarefeet/Cracking-the-Coding-Interview-Problems/tree/master/toyProblems)
- [github.com/randy909/coding-interview/tree/master/cracking](https://github.com/randy909/coding-interview/tree/master/cracking)
- [github.com/rohan-paul/Awesome-JavaScript-Interviews#collection-of-cracking-the-coding-interview-book-problem-solution](https://github.com/rohan-paul/Awesome-JavaScript-Interviews#collection-of-cracking-the-coding-interview-book-problem-solution)
- [github.com/careercup/ctci/tree/master/javascript/lib/data-structures](https://github.com/careercup/ctci/tree/master/javascript/lib/data-structures)
- [github.com/miguelmota/ctci-js](https://github.com/miguelmota/ctci-js)
- [github.com/ChirpingMermaid/CTCI](https://github.com/ChirpingMermaid/CTCI)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## UX-CSS-Design Sense Related

- [Accessibility Interview Questions](https://scottaohara.github.io/accessibility_interview_questions/)

## Most common System-Design Interview Topics & Questions

(Below Links are all within this Repository)

- [design-url-shortner](system-design/design-url-shortner.md)
- [e-Commerce-site](system-design/e-Commerce-site.md)
- [Whatsapp-Basic-Features-of-a-chat-app](system-design/Whatsapp-Basic-Features-of-a-chat-app.md)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## System-Design related topics-Some very useful articles

- [How to Rock a Systems Design Interview](http://www.palantir.com/2011/10/how-to-rock-a-systems-design-interview/)
- [System Interview](http://www.hiredintech.com/app#system-design)
- [Scalability for Dummies](http://www.lecloud.net/tagged/scalability)
- [Scalable Web Architecture and Distributed Systems](http://www.aosabook.org/en/distsys.html)
- [Numbers Everyone Should Know](http://everythingisdata.wordpress.com/2009/10/17/numbers-everyone-should-know/)
- [Fallacies of distributed systems](https://pages.cs.wisc.edu/~zuyu/files/fallacies.pdf)
- [Scalable System Design Patterns](http://horicky.blogspot.com/2010/10/scalable-system-design-patterns.html)
- [Introduction to Architecting Systems for Scale](http://lethain.com/introduction-to-architecting-systems-for-scale/)
- [Transactions Across Datacenters](http://snarfed.org/transactions_across_datacenters_io.html)
- [A Plain English Introduction to CAP Theorem](http://ksat.me/a-plain-english-introduction-to-cap-theorem/)
- [The CAP FAQ](https://github.com/henryr/cap-faq)
- [Paxos Made Simple](http://research.microsoft.com/en-us/um/people/lamport/pubs/paxos-simple.pdf)
- [Consistent Hashing](http://www.tom-e-white.com/2007/11/consistent-hashing.html)
- [NOSQL Patterns](http://horicky.blogspot.com/2009/11/nosql-patterns.html)
- [Scalability, Availability & Stability Patterns](http://www.slideshare.net/jboner/scalability-availability-stability-patterns)
- [Design a CDN network-Globally Distributed Content Delivery](http://repository.cmu.edu/cgi/viewcontent.cgi?article=2112&context=compsci)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a Google document system**

- [google-mobwrite](https://code.google.com/p/google-mobwrite/)
- [Differential Synchronization](https://neil.fraser.name/writing/sync/)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a random ID generation system**

- [Announcing Snowflake](https://blog.twitter.com/2010/announcing-snowflake)
- [snowflake](https://github.com/twitter/snowflake/)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a key-value database**

- [Introduction to Redis](http://www.slideshare.net/dvirsky/introduction-to-redis)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design the Facebook news feed function**

- [What are best practices for building something like a News Feed?](http://www.quora.com/What-are-best-practices-for-building-something-like-a-News-Feed)
- [What are the scaling issues to keep in mind while developing a social network feed?](http://www.quora.com/Activity-Streams/What-are-the-scaling-issues-to-keep-in-mind-while-developing-a-social-network-feed)
- [Activity Feeds Architecture](http://www.slideshare.net/danmckinley/etsy-activity-feeds-architecture)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design the Facebook timeline function**

- [Building Timeline](https://www.facebook.com/note.php?note_id=10150468255628920)
- [Facebook Timeline](http://highscalability.com/blog/2012/1/23/facebook-timeline-brought-to-you-by-the-power-of-denormaliza.html)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a function to return the top k requests during past time interval**

- [Efficient Computation of Frequent and Top-k Elements in Data Streams](http://www.cse.ust.hk/~raywong/comp5331/References/EfficientComputationOfFrequentAndTop-kElementsInDataStreams.pdf)
- [An Optimal Strategy for Monitoring Top-k Queries in Streaming Windows](http://davis.wpi.edu/xmdv/docs/EDBT11-diyang.pdf)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design an online multiplayer card game**

- [How to Create an Asynchronous Multiplayer Game](http://www.indieflashblog.com/how-to-create-an-asynchronous-multiplayer-game.html)
- [How to Create an Asynchronous Multiplayer Game Part 2: Saving the Game State to Online Database](http://www.indieflashblog.com/how-to-create-async-part2.html)
- [How to Create an Asynchronous Multiplayer Game Part 3: Loading Games from the Database](http://www.indieflashblog.com/how-to-create-async-part3.html)
- [How to Create an Asynchronous Multiplayer Game Part 4: Matchmaking](http://www.indieflashblog.com/how-to-create-async-part4-html.html#comment-4447)
- [Real Time Multiplayer in HTML5](http://buildnewgames.com/real-time-multiplayer/)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a graph search function**

- [Building out the infrastructure for Graph Search](https://www.facebook.com/notes/facebook-engineering/under-the-hood-building-out-the-infrastructure-for-graph-search/10151347573598920)
- [Indexing and ranking in Graph Search](https://www.facebook.com/notes/facebook-engineering/under-the-hood-indexing-and-ranking-in-graph-search/10151361720763920)
- [The natural language interface of Graph Search](https://www.facebook.com/notes/facebook-engineering/under-the-hood-the-natural-language-interface-of-graph-search/10151432733048920) and [Erlang at Facebook](http://www.erlang-factory.com/upload/presentations/31/EugeneLetuchy-ErlangatFacebook.pdf)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a picture sharing system**

- [Flickr Architecture](http://highscalability.com/flickr-architecture)
- [Instagram Architecture](http://highscalability.com/blog/2011/12/6/instagram-architecture-14-million-users-terabytes-of-photos.html)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a search engine**

- [How would you implement Google Search?](http://programmers.stackexchange.com/questions/38324/interview-question-how-would-you-implement-google-search)
- [Implementing Search Engines](http://www.ardendertat.com/2012/01/11/implementing-search-engines/)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a recommendation system**

- [Hulu’s Recommendation System](http://tech.hulu.com/blog/2011/09/19/recommendation-system.html)
- [Recommender Systems](http://ijcai13.org/files/tutorial_slides/td3.pdf)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a tinyurl system**

- [System Design for Big Data-tinyurl](http://n00tc0d3r.blogspot.com/)
- [URL Shortener API](https://developers.google.com/url-shortener/?csw=1)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a garbage collection system**

- [Baby's First Garbage Collector](http://journal.stuffwithstuff.com/2013/12/08/babys-first-garbage-collector/)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a scalable web crawling system**

- [How can I build a web crawler from scratch?](https://www.quora.com/How-can-I-build-a-web-crawler-from-scratch)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design the Facebook chat function**

- [Erlang at Facebook](http://www.erlang-factory.com/upload/presentations/31/EugeneLetuchy-ErlangatFacebook.pdf)
- [Facebook Chat](https://www.facebook.com/note.php?note_id=14218138919&id=9445547199&index=0)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a trending topic system**

- [Implementing Real-Time Trending Topics With a Distributed Rolling Count Algorithm in Storm](http://www.michael-noll.com/blog/2013/01/18/implementing-real-time-trending-topics-in-storm/)
- [Early detection of Twitter trends explained](http://snikolov.wordpress.com/2012/11/14/early-detection-of-twitter-trends/)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

**Design a cache system**

- [Introduction to Memcached](http://www.slideshare.net/oemebamo/introduction-to-memcached)

[[↑] Back to top](#table-of-contents-of-this-readme-file)

## System-Design-Company engineering blog

- [High Scalability](http://highscalability.com/)
- [The GitHub Blog](https://github.com/blog/category/engineering)
- [Engineering at Quora](http://engineering.quora.com/)
- [Yelp Engineering Blog](http://engineeringblog.yelp.com/)
- [Twitter Engineering](https://engineering.twitter.com/)
- [Facebook Engineering](https://www.facebook.com/Engineering)
- [Yammer Engineering](http://eng.yammer.com/blog/)
- [Etsy Code as Craft](http://codeascraft.com/)
- [Foursquare Engineering Blog](http://engineering.foursquare.com/)
- [Airbnb Engineering](http://nerds.airbnb.com/)
- [WebEngage Engineering Blog](http://engineering.webengage.com/)
- [LinkedIn Engineering](http://engineering.linkedin.com/blog)
- [The Netflix Tech Blog](http://techblog.netflix.com/)
- [BankSimple Simple Blog](https://www.simple.com/engineering/)
- [Square The Corner](http://corner.squareup.com/)
- [SoundCloud Backstage Blog](https://developers.soundcloud.com/blog/)
- [Flickr Code](http://code.flickr.net/)
- [Instagram Engineering](http://instagram-engineering.tumblr.com/)
- [Dropbox Tech Blog](https://tech.dropbox.com/)
- [Cloudera Developer Blog](http://blog.cloudera.com/)
- [Bandcamp Tech](http://bandcamptech.wordpress.com/)
- [Oyster Tech Blog](http://tech.oyster.com/)
- [THE REDDIT BLOG](http://www.redditblog.com/)
- [Groupon Engineering Blog](https://engineering.groupon.com/)
- [Songkick Technology Blog](http://devblog.songkick.com/)
- [Google Research Blog](http://googleresearch.blogspot.com/)
- [Pinterest Engineering Blog](http://engineering.pinterest.com/)
- [Twilio Engineering Blog](http://www.twilio.com/engineering)
- [Bitly Engineering Blog](http://word.bitly.com/)
- [Uber Engineering Blog ](https://eng.uber.com/)
- [Godaddy Engineering](http://engineering.godaddy.com/)
- [Splunk Blog](http://blogs.splunk.com/)
- [Coursera Engineering Blog](https://building.coursera.org/)
- [PayPal Engineering Blog](https://www.paypal-engineering.com/)
- [Nextdoor Engineering Blog](https://engblog.nextdoor.com/)
- [Booking.com Development Blog](https://blog.booking.com/)
- [Scalyr Engineering Blog ](https://blog.scalyr.com/)

[[↑] Back to top](#table-of-contents-of-this-readme-file)


# JavaScript Interview Questions & Answers

> Click :star:if you like the project. Pull Requests are highly appreciated. Follow me [@SudheerJonna](https://twitter.com/SudheerJonna) for technical updates.

Go to [Coding Exercise](#coding-exercise) for coding specific questions

## Downloading PDF/Epub formats

You can download the PDF and Epub version of this repository from the latest run on the [actions tab](https://github.com/sudheerj/JavaScript-Interview-Questions/actions).

---
---

### Table of Contents

| No. | Questions |
|---- | ---------
|1  | [What are the possible ways to create objects in JavaScript](#what-are-the-possible-ways-to-create-objects-in-javascript) |
|2  | [What is prototype chain](#what-is-a-prototype-chain)|
|3  | [What is the difference between Call, Apply and Bind](#what-is-the-difference-between-call-apply-and-bind)|
|4  | [What is JSON and its common operations](#what-is-json-and-its-common-operations)|
|5  | [What is the purpose of the array slice method](#what-is-the-purpose-of-the-array-slice-method)|
|6  | [What is the purpose of the array splice method](#what-is-the-purpose-of-the-array-splice-method)|
|7  | [What is the difference between slice and splice](#what-is-the-difference-between-slice-and-splice)|
|8  | [How do you compare Object and Map](#how-do-you-compare-object-and-map)|
|9  | [What is the difference between == and === operators](#what-is-the-difference-between-==-and-===-operators)|
|10 | [What are lambda or arrow functions](#what-are-lambda-or-arrow-functions)|
|11 | [What is a first class function](#what-is-a-first-class-function)|
|12 | [What is a first order function](#what-is-a-first-order-function)|
|13 | [What is a higher order function](#what-is-a-higher-order-function)|
|14 | [What is a unary function](#what-is-a-unary-function)|
|15 | [What is the currying function](#what-is-the-currying-function)|
|16 | [What is a pure function](#what-is-a-pure-function)|
|17 | [What is the purpose of the let keyword](#what-is-the-purpose-of-the-let-keyword)|
|18 | [What is the difference between let and var](#what-is-the-difference-between-let-and-var)|
|19 | [What is the reason to choose the name let as a keyword](#what-is-the-reason-to-choose-the-name-let-as-a-keyword)|
|20 | [How do you redeclare variables in switch block without an error](#how-do-you-redeclare-variables-in-switch-block-without-an-error)|
|21 | [What is the Temporal Dead Zone](#what-is-the-temporal-dead-zone)|
|22 | [What is IIFE(Immediately Invoked Function Expression)](#what-is-iifeimmediately-invoked-function-expression)|
|23 | [What is the benefit of using modules](#what-is-the-benefit-of-using-modules)|
|24 | [What is memoization](#what-is-memoization)|
|25 | [What is Hoisting](#what-is-hoisting)|
|26 | [What are classes in ES6](#what-are-classes-in-es6)|
|27 | [What are closures](#what-are-closures)|
|28 | [What are modules](#what-are-modules)|
|29 | [Why do you need modules](#why-do-you-need-modules)|
|30 | [What is scope in javascript](#what-is-scope-in-javascript)|
|31 | [What is a service worker](#what-is-a-service-worker)|
|32 | [How do you manipulate DOM using a service worker](#how-do-you-manipulate-dom-using-a-service-worker)|
|33 | [How do you reuse information across service worker restarts](#how-do-you-reuse-information-across-service-worker-restarts)|
|34 | [What is IndexedDB](#what-is-indexeddb)|
|35 | [What is web storage](#what-is-web-storage)|
|36 | [What is a post message](#what-is-a-post-message)|
|37 | [What is a cookie](#what-is-a-cookie)|
|38 | [Why do you need a Cookie](#why-do-you-need-a-cookie)|
|39 | [What are the options in a cookie](#what-are-the-options-in-a-cookie)|
|40 | [How do you delete a cookie](#how-do-you-delete-a-cookie)|
|41 | [What are the differences between cookie, local storage and session storage](#What-are-the-differences-between-cookie-local-storage-and-session-storage)|
|42 | [What is the main difference between localStorage and sessionStorage](#what-is-the-main-difference-between-localstorage-and-sessionstorage)|
|43 | [How do you access web storage](#how-do-you-access-web-storage)|
|44 | [What are the methods available on session storage](#what-are-the-methods-available-on-session-storage)|
|45 | [What is a storage event and its event handler](#what-is-a-storage-event-and-its-event-handler)|
|46 | [Why do you need web storage](#why-do-you-need-web-storage)|
|47 | [How do you check web storage browser support](#how-do-you-check-web-storage-browser-support)|
|48 | [How do you check web workers browser support](#how-do-you-check-web-workers-browser-support)|
|49 | [Give an example of web worker](#give-an-example-of-web-worker)|
|50 | [What are the restrictions of web workers on DOM](#what-are-the-restrictions-of-web-workers-on-dom)|
|51 | [What is a promise](#what-is-a-promise)|
|52 | [Why do you need a promise](#why-do-you-need-a-promise)|
|53 | [What are the three states of promise](#what-are-the-three-states-of-promise)|
|54 | [What is a callback function](#what-is-a-callback-function)|
|55 | [Why do we need callbacks](#why-do-we-need-callbacks)|
|56 | [What is a callback hell](#what-is-a-callback-hell)|
|57 | [What is server-sent events](#what-is-server-sent-events)|
|58 | [How do you receive server-sent event notifications](#how-do-you-receive-server-sent-event-notifications)|
|59 | [How do you check browser support for server-sent events](#how-do-you-check-browser-support-for-server-sent-events)|
|60 | [What are the events available for server sent events](#what-are-the-events-available-for-server-sent-events)|
|61 | [What are the main rules of promise](#what-are-the-main-rules-of-promise)|
|62 | [What is callback in callback](#what-is-callback-in-callback)|
|63 | [What is promise chaining](#what-is-promise-chaining)|
|64 | [What is promise.all](#what-is-promise.all)|
|65 | [What is the purpose of race method in promise](#what-is-the-purpose-of-race-method-in-promise)|
|66 | [What is a strict mode in javascript](#what-is-a-strict-mode-in-javascript)|
|67 | [Why do you need strict mode](#why-do-you-need-strict-mode)|
|68 | [How do you declare strict mode](#how-do-you-declare-strict-mode)|
|69 | [What is the purpose of double exclamation](#what-is-the-purpose-of-double-exclamation)|
|70 | [What is the purpose of delete operator](#what-is-the-purpose-of-delete-operator)|
|71 | [What is typeof operator](#what-is-typeof-operator)|
|72 | [What is undefined property](#what-is-undefined-property)|
|73 | [What is null value](#what-is-null-value)|
|74 | [What is the difference between null and undefined](#what-is-the-difference-between-null-and-undefined)|
|75 | [What is eval](#What-is-eval)|
|76 | [What is the difference between window and document](#what-is-the-difference-between-window-and-document)|
|77 | [How do you access history in javascript](#how-do-you-access-history-in-javascript)|
|78 | [How do you detect caps lock key turned on or not](#how-do-you-detect-caps-lock-key-turned-on-or-not)|
|79 | [What is isNaN](#what-is-isnan)|
|80 | [What are the differences between undeclared and undefined variables](#what-are-the-differences-between-undeclared-and-undefined-variables)|
|81 | [What are global variables](#what-are-global-variables)|
|82 | [What are the problems with global variables](#what-are-the-problems-with-global-variables)|
|83 | [What is NaN property](#what-is-nan-property)|
|84 | [What is the purpose of isFinite function](#what-is-the-purpose-of-isfinite-function)
|85 | [What is an event flow](#what-is-an-event-flow)|
|86 | [What is event bubbling](#what-is-event-bubbling)|
|87 | [What is event capturing](#what-is-event-capturing)|
|88 | [How do you submit a form using JavaScript](#how-do-you-submit-a-form-using-javascript)|
|89 | [How do you find operating system details](#how-do-you-find-operating-system-details)|
|90 | [What is the difference between document load and DOMContentLoaded events](#what-is-the-difference-between-document-load-and-domcontentloaded-events)|
|91 | [What is the difference between native, host and user objects](#what-is-the-difference-between-native,-host-and-user-objects)|
|92 | [What are the tools or techniques used for debugging JavaScript code](#what-are-the-tools-or-techniques-used-for-debugging-javascript-code)|
|93 | [What are the pros and cons of promises over callbacks](#what-are-the-pros-and-cons-of-promises-over-callbacks)|
|94 | [What is the difference between an attribute and a property](#what-is-the-difference-between-an-attribute-and-a-property)|
|95 | [What is same-origin policy](#what-is-same-origin-policy)|
|96 | [What is the purpose of void 0](#what-is-the-purpose-of-void-0)|
|97 | [Is JavaScript a compiled or interpreted language](#is-javascript-a-compiled-or-interpreted-language)|
|98 | [Is JavaScript a case-sensitive language](#is-javascript-a-case-sensitive-language)|
|99 | [Is there any relation between Java and JavaScript](#is-there-any-relation-between-java-and-javascript)|
|100| [What are events](#what-are-events)|
|101| [Who created javascript](#who-created-javascript)|
|102| [What is the use of preventDefault method](#what-is-the-use-of-preventdefault-method)|
|103| [What is the use of stopPropagation method](#what-is-the-use-of-stoppropagation-method)|
|104| [What are the steps involved in return false](#what-are-the-steps-involved-in-return-false)|
|105| [What is BOM](#what-is-bom)|
|106| [What is the use of setTimeout](#what-is-the-use-of-settimeout)|
|107| [What is the use of setInterval](#what-is-the-use-of-setinterval)|
|108| [Why is JavaScript treated as Single threaded](#why-is-javascript-treated-as-single-threaded)|
|109| [What is an event delegation](#what-is-an-event-delegation)|
|110| [What is ECMAScript](#what-is-ecmascript)|
|111| [What is JSON](#what-is-json)|
|112| [What are the syntax rules of JSON](#what-are-the-syntax-rules-of-json)|
|113| [What is the purpose JSON stringify](#what-is-the-purpose-json-stringify)|
|114| [How do you parse JSON string](#how-do-you-parse-json-string)|
|115| [Why do you need JSON](#why-do-you-need-json)|
|116| [What are PWAs](#what-are-pwas?)|
|117| [What is the purpose of clearTimeout method](#what-is-the-purpose-of-cleartimeout-method)|
|118| [What is the purpose of clearInterval method](#what-is-the-purpose-of-clearinterval-method)|
|119| [How do you redirect new page in javascript](#how-do-you-redirect-new-page-in-javascript)|
|120| [How do you check whether a string contains a substring](#how-do-you-check-whether-a-string-contains-a-substring)|
|121| [How do you validate an email in javascript](#how-do-you-validate-an-email-in-javascript)|
|122| [How do you get the current url with javascript](#how-do-you-get-the-current-url-with-javascript)|
|123| [What are the various url properties of location object](#what-are-the-various-url-properties-of-location-object)|
|124| [How do get query string values in javascript](#how-do-get-query-string-values-in-javascript)|
|125| [How do you check if a key exists in an object](#how-do-you-check-if-a-key-exists-in-an-object)|
|126| [How do you loop through or enumerate javascript object](#how-do-you-loop-through-or-enumerate-javascript-object)|
|127| [How do you test for an empty object](#how-do-you-test-for-an-empty-object)|
|128| [What is an arguments object](#what-is-an-arguments-object)|
|129| [How do you make first letter of the string in an uppercase](#how-do-you-make-first-letter-of-the-string-in-an-uppercase)|
|130| [What are the pros and cons of for loop](#what-are-the-pros-and-cons-of-for-loop)|
|131| [How do you display the current date in javascript](#how-do-you-display-the-current-date-in-javascript)|
|132| [How do you compare two date objects](#how-do-you-compare-two-date-objects)|
|133| [How do you check if a string starts with another string](#how-do-you-check-if-a-string-starts-with-another-string)|
|134| [How do you trim a string in javascript](#how-do-you-trim-a-string-in-javascript)|
|135| [How do you add a key value pair in javascript](#how-do-you-add-a-key-value-pair-in-javascript)|
|136| [Is the '!--' notation represents a special operator](#is-the-'!--'-notation-represents-a-special-operator)|
|137| [How do you assign default values to variables](#how-do-you-assign-default-values-to-variables)|
|138| [How do you define multiline strings](#how-do-you-define-multiline-strings)|
|139| [What is an app shell model](#what-is-an-app-shell-model)|
|140| [Can we define properties for functions](#can-we-define-properties-for-functions)|
|141| [What is the way to find the number of parameters expected by a function](#what-is-the-way-to-find-the-number-of-parameters-expected-by-a-function)|
|142| [What is a polyfill](#what-is-a-polyfill)|
|143| [What are break and continue statements](#what-are-break-and-continue-statements)|
|144| [What are js labels](#what-are-js-labels)|
|145| [What are the benefits of keeping declarations at the top](#what-are-the-benefits-of-keeping-declarations-at-the-top)|
|146| [What are the benefits of initializing variables](#what-are-the-benefits-of-initializing-variables)|
|147| [What are the recommendations to create new object](#what-are-the-recommendations-to-create-new-object)|
|148| [How do you define JSON arrays](#how-do-you-define-json-arrays)|
|149| [How do you generate random integers](#how-do-you-generate-random-integers)|
|150| [Can you write a random integers function to print integers with in a range](#can-you-write-a-random-integers-function-to-print-integers-with-in-a-range)|
|151| [What is tree shaking](#what-is-tree-shaking)|
|152| [What is the need of tree shaking](#what-is-the-need-of-tree-shaking)|
|153| [Is it recommended to use eval](#is-it-recommended-to-use-eval)|
|154| [What is a Regular Expression](#what-is-a-regular-expression)|
|155| [What are the string methods available in Regular expression](#what-are-the-string-methods-available-in-regular-expression)|
|156| [What are modifiers in regular expression](#what-are-modifiers-in-regular-expression)|
|157| [What are regular expression patterns](#what-are-regular-expression-patterns)|
|158| [What is a RegExp object](#what-is-a-regexp-object)|
|159| [How do you search a string for a pattern](#how-do-you-search-a-string-for-a-pattern)|
|160| [What is the purpose of exec method](#what-is-the-purpose-of-exec-method)|
|161| [How do you change style of a HTML element](#how-do-you-change-style-of-a-html-element)|
|162| [What would be the result of 1+2+'3'](#what-would-be-the-result-of-1+2+'3')|
|163| [What is a debugger statement](#what-is-a-debugger-statement)|
|164| [What is the purpose of breakpoints in debugging](#what-is-the-purpose-of-breakpoints-indebugging)|
|165| [Can I use reserved words as identifiers](#can-i-use-reserved-words-as-identifiers)|
|166| [How do you detect a mobile browser](#how-do-you-detect-a-mobile-browser)|
|167| [How do you detect a mobile browser without regexp](#how-do-you-detect-a-mobile-browser-without-regexp)|
|168| [How do you get the image width and height using JS](#how-do-you-get-the-image-width-and-height-using-js)|
|169| [How do you make synchronous HTTP request](#how-do-you-make-synchronous-http-request)|
|170| [How do you make asynchronous HTTP request](#how-do-you-make-asynchronous-http-request)|
|171| [How do you convert date to another timezone in javascript](#how-do-you-convert-date-to-another-timezone-in-javascript)|
|172| [What are the properties used to get size of window](#what-are-the-properties-used-to-get-size-of-window)|
|173| [What is a conditional operator in javascript](#what-is-a-conditional-operator-in-javascript)|
|174| [Can you apply chaining on conditional operator](#Can-you-apply-chaining-on-conditional-operator)|
|175| [What are the ways to execute javascript after page load](#what-are-the-ways-to-execute-javascript-after-page-load)|
|176| [What is the difference between proto and prototype](#what-is-the-difference-between-proto-and-prototype)|
|177| [Give an example where do you really need semicolon](#give-an-example-where-do-you-really-need-semicolon)|
|178| [What is a freeze method](#what-is-a-freeze-method)|
|179| [What is the purpose of freeze method](#what-is-the-purpose-of-freeze-method)|
|180| [Why do I need to use freeze method](#why-do-i-need-to-use-freeze-method)|
|181| [How do you detect a browser language preference](#how-do-you-detect-a-browser-language-preference)|
|182| [How to convert string to title case with javascript](#how-to-convert-string-to-title-case-with-javascript)|
|183| [How do you detect javascript disabled in the page](#how-do-you-detect-javascript-disabled-in-the-page)|
|184| [What are various operators supported by javascript](#what-are-various-operators-supported-by-javascript)|
|185| [What is a rest parameter](#what-is-a-rest-parameter)|
|186| [What happens if you do not use rest parameter as a last argument](#what-happens-if-you-do-not-use-rest-parameter-as-a-last-argument)|
|187| [What are the bitwise operators available in javascript](#what-are-the-bitwise-operators-available-in-javascript)|
|188| [What is a spread operator](#what-is-a-spread-operator)|
|189| [How do you determine whether object is frozen or not](#how-do-you-determine-whether-object-is-frozen-or-not)|
|190| [How do you determine two values same or not using object](#how-do-you-determine-two-values-same-or-not-using-object)|
|191| [What is the purpose of using object is method](#what-is-the-purpose-of-using-object-is-method)|
|192| [How do you copy properties from one object to other](#how-do-you-copy-properties-from-one-object-to-other)|
|193| [What are the applications of assign method](#what-are-the-applications-of-assign-method)|
|194| [What is a proxy object](#what-is-a-proxy-object)|
|195| [What is the purpose of seal method](#what-is-the-purpose-of-seal-method)|
|196| [What are the applications of seal method](#what-are-the-applications-of-seal-method)|
|197| [What are the differences between freeze and seal methods](#what-are-the-differences-between-freeze-and-seal-methods)|
|198| [How do you determine if an object is sealed or not](#how-do-you-determine-if-an-object-is-sealed-or-not)|
|199| [How do you get enumerable key and value pairs](#how-do-you-get-enumerable-key-and-value-pairs)|
|200| [What is the main difference between Object.values and Object.entries method](#what-is-the-main-difference-between-object.values-and-object.entries-method)|
|201| [How can you get the list of keys of any object](#how-can-you-get-the-list-of-keys-of-any-object)|
|202| [How do you create an object with prototype](#how-do-you-create-an-object-with-prototype)|
|203| [What is a WeakSet](#what-is-a-weakset)|
|204| [What are the differences between WeakSet and Set](#what-are-the-differences-between-weakset-and-set)|
|205| [List down the collection of methods available on WeakSet](#list-down-the-collection-of-methods-available-on-weakset)|
|206| [What is a WeakMap](#what-is-a-weakmap)|
|207| [What are the differences between WeakMap and Map](#what-are-the-differences-between-weakmap-and-map)|
|208| [List down the collection of methods available on WeakMap](#list-down-the-collection-of-methods-available-on-weakmap)|
|209| [What is the purpose of uneval](#what-is-the-purpose-of-uneval)|
|210| [How do you encode an URL](#how-do-you-encode-an-url)|
|211| [How do you decode an URL](#how-do-you-decode-an-url)|
|212| [How do you print the contents of web page](#how-do-you-print-the-contents-of-web-page)|
|213| [What is the difference between uneval and eval](#what-is-the-difference-between-uneval-and-eval)|
|214| [What is an anonymous function](#what-is-an-anonymous-function)|
|215| [What is the precedence order between local and global variables](#what-is-the-precedence-order-between-local-and-global-variables)|
|216| [What are javascript accessors](#what-are-javascript-accessors)|
|217| [How do you define property on Object constructor](#how-do-you-define-property-on-object-constructor)|
|218| [What is the difference between get and defineProperty](#what-is-the-difference-between-get-and-defineproperty)|
|219| [What are the advantages of Getters and Setters](#what-are-the-advantages-of-getters-and-setters)|
|220| [Can I add getters and setters using defineProperty method](#can-i-add-getters-and-setters-using-defineproperty-method)|
|221| [What is the purpose of switch-case](#what-is-the-purpose-of-switch-case)|
|222| [What are the conventions to be followed for the usage of swtich case](#what-are-the-conventions-to-be-followed-for-the-usage-of-swtich-case)|
|223| [What are primitive data types](#what-are-primitive-data-types)|
|224| [What are the different ways to access object properties](#what-are-the-different-ways-to-access-object-properties)|
|225| [What are the function parameter rules](#what-are-the-function-parameter-rules)|
|226| [What is an error object](#what-is-an-error-object)|
|227| [When you get a syntax error](#when-you-get-a-syntax-error)|
|228| [What are the different error names from error object](#what-are-the-different-error-names-from-error-object)|
|229| [What are the various statements in error handling](#what-are-the-various-statements-in-error-handling)|
|230| [What are the two types of loops in javascript](#what-are-the-two-types-of-loops-in-javascript)|
|231| [What is nodejs](#what-is-nodejs)|
|232| [What is an Intl object](#what-is-an-intl-object)|
|233| [How do you perform language specific date and time formatting](#how-do-you-perform-language-specific-date-and-time-formatting)|
|234| [What is an Iterator](#what-is-an-iterator)|
|235| [How does synchronous iteration works](#how-does-synchronous-iteration-works)|
|236| [What is an event loop](#what-is-an-event-loop)|
|237| [What is call stack](#what-is-call-stack)|
|238| [What is an event queue](#what-is-an-event-queue)|
|239| [What is a decorator](#what-is-a-decorator)|
|240| [What are the properties of Intl object](#what-are-the-properties-of-intl-object)|
|241| [What is an Unary operator](#what-is-an-unary-operator)|
|242| [How do you sort elements in an array](#how-do-you-sort-elements-in-an-array)|
|243| [What is the purpose of compareFunction while sorting arrays](#what-is-the-purpose-of-comparefunction-while-sorting-arrays)|
|244| [How do you reversing an array](#how-do-you-reversing-an-array)|
|245| [How do you find min and max value in an array](#how-do-you-find-min-and-max-value-in-an-array)|
|246| [How do you find min and max values without Math functions](#how-do-you-find-min-and-max-values-without--math-functions)|
|247| [What is an empty statement and purpose of it](#what-is-an-empty-statement-and-purpose-of-it)|
|248| [How do you get meta data of a module](#how-do-you-get-meta-data-of-a-module)|
|249| [What is a comma operator](#what-is-a-comma-operator)|
|250| [What is the advantage of a comma operator](#what-is-the-advantage-of-a-comma-operator)|
|251| [What is typescript](#what-is-typescript)|
|252| [What are the differences between javascript and typescript](#what-are-the-differences-between-javascript-and-typescript)|
|253| [What are the advantages of typescript over javascript](#what-are-the-advantages-of-typescript-over-javascript)|
|254| [What is an object initializer](#what-is-an-object-initializer)|
|255| [What is a constructor method](#what-is-a-constructor-method)|
|256| [What happens if you write constructor more than once in a class](#what-happens-if-you-write-constructor-more-than-once-in-a-class)|
|257| [How do you call the constructor of a parent class](#how-do-you-call-the-constructor-of-a-parent-class)|
|258| [How do you get the prototype of an object](#how-do-you-get-the-prototype-of-an-object)|
|259| [What happens If I pass string type for getPrototype method](#what-happens-if-i-pass-string-type-for-getprototype-method)|
|260| [How do you set prototype of one object to another](#how-do-you-set-prototype-of-one-object-to-another)|
|261| [How do you check whether an object can be extendable or not](#how-do-you-check-whether-an-object-can-be-extendable-or-not)|
|262| [How do you prevent an object to extend](#how-do-you-prevent-an-object-to-extend)|
|263| [What are the different ways to make an object non-extensible](#what-are-the-different-ways-to-make-an-object-non-extensible)|
|264| [How do you define multiple properties on an object](#how-do-you-define-multiple-properties-on-an-object)|
|265| [What is MEAN in javascript](#what-is-mean-in-javascript)|
|266| [What Is Obfuscation in javascript](#what-is-obfuscation-in-javascript)|
|267| [Why do you need Obfuscation](#why-do-you-need-obfuscation)|
|268| [What is Minification](#what-is-minification)|
|269| [What are the advantages of minification](#what-are-the-advantages-of-minification)|
|270| [What are the differences between Obfuscation and Encryption](#what-are-the-differences-between-obfuscation-and-encryption)|
|271| [What are the common tools used for minification](#what-are-the-common-tools-used-for-minification)|
|272| [How do you perform form validation using javascript](#how-do-you-perform-form-validation-using-javascript)|
|273| [How do you perform form validation without javascript](#how-do-you-perform-form-validation-without-javascript)|
|274| [What are the DOM methods available for constraint validation](#what-are-the-dom-methods-available-for-constraint-validation)|
|275| [What are the available constraint validation DOM properties](#what-are-the-available-constraint-validation-dom-properties)|
|276| [What are the list of validity properties](#what-are-the-list-of-validity-properties)|
|277| [Give an example usage of rangeOverflow property](#give-an-example-usage-of-rangeoverflow-property)|
|278| [Is enums feature available in javascript](#is-enums-feature-available-in-javascript)|
|279| [What is an enum](#What-is-an-enum)|
|280| [How do you list all properties of an object](#how-do-you-list-all-properties-of-an-object)|
|281| [How do you get property descriptors of an object](#how-do-you-get-property-descriptors-of-an-object)|
|282| [What are the attributes provided by a property descriptor](#what-are-the-attributes-provided-by-a-property-descriptor)|
|283| [How do you extend classes](#how-do-you-extend-classes)|
|284| [How do I modify the url without reloading the page](#how-do-i-modify-the-url-without-reloading-the-page)|
|285| [How do you check whether an array includes a particular value or not](#how-do-you-check-whether-an-array-includes-a-particular-value-or-not)|
|286| [How do you compare scalar arrays](#how-do-you-compare-scalar-arrays)|
|287| [How to get the value from get parameters](#how-to-get-the-value-from-get-parameters)|
|288| [How do you print numbers with commas as thousand separators](#how-do-you-print-numbers-with-commas-as-thousand-separators)|
|289| [What is the difference between java and javascript](#what-is-the-difference-between-java-and-javascript)|
|290| [Is javascript supports namespace](#is-javascript-supports-namespace)|
|291| [How do you declare namespace](#how-do-you-declare-namespace)|
|292| [How do you invoke javascript code in an iframe from parent page](#how-do-you-invoke-javascript-code-in-an-iframe-from-parent-page)|
|293| [How do get the timezone offset from date](#how-do-get-the-timezone-offset-from-date)|
|294| [How do you load CSS and JS files dynamically](#how-do-you-load-css-and-js-files-dynamically)|
|295| [What are the different methods to find HTML elements in DOM](#what-are-the-different-methods-to-find-html-elements-in-dom)|
|296| [What is jQuery](#what-is-jquery)|
|297| [What is V8 JavaScript engine](#what-is-v8-javascript-engine)|
|298| [Why do we call javascript as dynamic language](#why-do-we-call-javascript-as-dynamic-language)|
|299| [What is a void operator](#what-is-a-void-operator)|
|300| [How to set the cursor to wait](#how-to-set-the-cursor-to-wait)|
|301| [How do you create an infinite loop](#how-do-you-create-an-infinite-loop)|
|302| [Why do you need to avoid with statement](#why-do-you-need-to-avoid-with-statement)|
|303| [What is the output of below for loops](#what-is-the-output-of-below-for-loops)|
|304| [List down some of the features of ES6](#list-down-some-of-the-features-of-es6)|
|305| [What is ES6](#what-is-es6)|
|306| [Can I redeclare let and const variables](#can-I-redeclare-let-and-const-variables)|
|307| [Is const variable makes the value immutable](#is-const-variable-makes-the-value-immutable)|
|308| [What are default parameters](#what-are-default-parameters)|
|309| [What are template literals](#what-are-template-literals)|
|310| [How do you write multi-line strings in template literals](#how-do-you-write-multi-line-strings-in-template-literals)|
|311| [What are nesting templates](#what-are-nesting-templates)|
|312| [What are tagged templates](#what-are-tagged-templates)|
|313| [What are raw strings](#what-are-raw-strings)|
|314| [What is destructuring assignment](#what-is-destructuring-assignment)|
|315| [What are default values in destructuring assignment](#what-are-default-values-in-destructuring-assignment)|
|316| [How do you swap variables in destructuring assignment](#how-do-you-swap-variables-in-destructuring-assignment)|
|317| [What are enhanced object literals](#what-are-enhanced-object-literals)|
|318| [What are dynamic imports](#what-are-dynamic-imports)|
|319| [What are the use cases for dynamic imports](#what-are-the-use-cases-for-dynamic-imports)|
|320| [What are typed arrays](#what-are-typed-arrays)|
|321| [What are the advantages of module loaders](#what-are-the-advantages-of-module-loaders)|
|322| [What is collation](#what-is-collation)|
|323| [What is for...of statement](#what-is-for...of-statement)|
|324| [What is the output of below spread operator array](#what-is-the-output-of-below-spread-operator-array)|
|325| [Is PostMessage secure](#is-postmessage-secure)|
|326| [What are the problems with postmessage target origin as wildcard](#what-are-the-problems-with-postmessage-target-origin-as-wildcard)|
|327| [How do you avoid receiving postMessages from attackers](#how-do-you-avoid-receiving-postmessages-from-attackers)|
|328| [Can I avoid using postMessages completely](#can-i-avoid-using-postmessages-completely)|
|329| [Is postMessages synchronous](#is-postmessages-synchronous)|
|330| [What paradigm is Javascript](#what-paradigm-is-javascript)|
|331| [What is the difference between internal and external javascript](#what-is-the-difference-between-internal-and-external-javascript)|
|332| [Is JavaScript faster than server side script](#is-javascript-faster-than-server-side-script)|
|333| [How do you get the status of a checkbox](#how-do-you-get-the-status-of-a-checkbox)|
|334| [What is the purpose of double tilde operator](#what-is-the-purpose-of-double-tilde-operator)|
|335| [How do you convert character to ASCII code](#how-do-you-convert-character-to-ascii-code)|
|336| [What is ArrayBuffer](#what-is-arraybuffer)|
|337| [What is the output of below string expression](#what-is-the-output-of-below-string-expression)|
|338| [What is the purpose of Error object](#what-is-the-purpose-of-error-object)|
|339| [What is the purpose of EvalError object](#what-is-the-purpose-of-evalerror-object)|
|340| [What are the list of cases error thrown from non-strict mode to strict mode](#what-are-the-list-of-cases-error-thrown-from-non-strict-mode-to-strict-mode)|
|341| [Is all objects have prototypes](#is-all-objects-have-prototypes)|
|342| [What is the difference between a parameter and an argument](#what-is-the-difference-between-a-parameter-and-an-argument)|
|343| [What is the purpose of some method in arrays](#what-is-the-purpose-of-some-method-in-arrays)|
|344| [How do you combine two or more arrays](#how-do-you-combine-two-or-more-arrays)|
|345| [What is the difference between Shallow and Deep copy](#what-is-the-difference-between-shallow-and-deep-copy)|
|346| [How do you create specific number of copies of a string](#how-do-you-create-specific-number-of-copies-of-a-string)|
|347| [How do you return all matching strings against a regular expression](#how-do-you-return-all-matching-strings-against-a-regular-expression)|
|348| [How do you trim a string at the beginning or ending](#how-do-you-trim-a-string-at-the-beginning-or-ending)|
|349| [What is the output of below console statement with unary operator](#what-is-the-output-of-below-console-statement-with-unary-operator)|
|350| [Does javascript uses mixins](#does-javascript-uses-mixins)|
|351| [What is a thunk function](#what-is-a-thunk-function)|
|352| [What are asynchronous thunks](#what-are-asynchronous-thunks)|
|353| [What is the output of below function calls](#what-is-the-output-of-below-function-calls)|
|354| [How to remove all line breaks from a string](#how-to-remove-all-line-breaks-from-a-string)|
|355| [What is the difference between reflow and repaint](#what-is-the-difference-between-reflow-and-repaint)|
|356| [What happens with negating an array](#what-happens-with-negating-an-array)|
|357| [What happens if we add two arrays](#what-happens-if-we-add-two-arrays)|
|358| [What is the output of prepend additive operator on falsy values](#what-is-the-output-of-prepend-additive-operator-on-falsy-values)|
|359| [How do you create self string using special characters](#how-do-you-create-self-string-using-special-characters)|
|360| [How do you remove falsy values from an array](#how-do-you-remove-falsy-values-from-an-array)|
|361| [How do you get unique values of an array](#how-do-you-get-unique-values-of-an-array)|
|362| [What is destructuring aliases](#what-is-destructuring-aliases)|
|363| [How do you map the array values without using map method](#how-do-you-map-the-array-values-without-using-map-method)|
|364| [How do you empty an array](#how-do-you-empty-an-array)|
|365| [How do you rounding numbers to certain decimals](#how-do-you-rounding-numbers-to-certain-decimals)|
|366| [What is the easiest way to convert an array to an object](#what-is-the-easiest-way-to-convert-an-array-to-an-object)|
|367| [How do you create an array with some data](#how-do-you-create-an-array-with-some-data)|
|368| [What are the placeholders from console object](#what-are-the-placeholders-from-console-object)|
|369| [Is it possible to add CSS to console messages](#is-it-possible-to-add-css-to-console-messages)|
|370| [What is the purpose of dir method of console object](#what-is-the-purpose-of-dir-method-of-console-object)|
|371| [Is it possible to debug HTML elements in console](#is-it-possible-to-debug-html-elements-in-console)|
|372| [How do you display data in a tabular format using console object](#how-do-you-display-data-in-a-tabular-format-using-console-object)|
|373| [How do you verify that an argument is a Number or not](#how-do-you-verify-that-an-argument-is-a-number-or-not)|
|374| [How do you create copy to clipboard button](#how-do-you-create-copy-to-clipboard-button)|
|375| [What is the shortcut to get timestamp](#what-is-the-shortcut-to-get-timestamp)|
|376| [How do you flattening multi dimensional arrays](#how-do-you-flattening-multi-dimensional-arrays)|
|377| [What is the easiest multi condition checking](#what-is-the-easiest-multi-condition-checking)|
|378| [How do you capture browser back button](#how-do-you-capture-browser-back-button)|
|379| [How do you disable right click in the web page](#how-do-you-disable-right-click-in-the-web-page)|
|380| [What are wrapper objects](#what-are-wrapper-objects)|
|381| [What is AJAX](#what-is-ajax)|
|382| [What are the different ways to deal with Asynchronous Code](#what-are-the-different-ways-to-deal-with-asynchronous-code)|
|383| [How to cancel a fetch request](#how-to-cancel-a-fetch-request)|
|384| [What is web speech API](#what-is-web-speech-api)|
|385| [What is minimum timeout throttling](#what-is-minimum-timeout-throttling)|
|386| [How do you implement zero timeout in modern browsers](#how-do-you-implement-zero-timeout-in-modern-browsers)|
|387| [What are tasks in event loop](#what-are-tasks-in-event-loop)|
|388| [What are microtasks](#what-are-microtasks)|
|389| [What are different event loops](#what-are-different-event-loops)|
|390| [What is the purpose of queueMicrotask](#what-is-the-purpose-of-queuemicrotask)|
|391| [How do you use javascript libraries in typescript file](#how-do-you-use-javascript-libraries-in-typescript-file)|
|392| [What are the differences between promises and observables](#what-are-the-differences-between-promises-and-observables)|
|393| [What is heap](#what-is-heap)|
|394| [What is an event table](#what-is-an-event-table)|
|395| [What is a microTask queue](#what-is-a-microtask-queue)|
|396| [What is the difference between shim and polyfill](#what-is-the-difference-between-shim-and-polyfill)|
|397| [How do you detect primitive or non primitive value type](#how-do-you-detect-primitive-or-non-primitive-value-type)|
|398| [What is babel](#what-is-babel)|
|399| [Is Node.js completely single threaded](#is-node.js-completely-single-threaded)|
|400| [What are the common use cases of observables](#what-are-the-common-use-cases-of-observables)|
|401| [What is RxJS](#what-is-rxjs)|
|402| [What is the difference between Function constructor and function declaration](#what-is-the-difference-between-function-constructor-and-function-declaration)|
|403| [What is a Short circuit condition](#what-is-a-short-circuit-condition)|
|404| [What is the easiest way to resize an array](#what-is-the-easiest-way-to-resize-an-array)|
|405| [What is an observable](#what-is-an-observable)|
|406| [What is the difference between function and class declarations](#what-is-the-difference-between-function-and-class-declarations)|
|407| [What is an async function](#what-is-an-async-function)|
|408| [How do you prevent promises swallowing errors](#how-do-you-prevent-promises-swallowing-errors)|
|409| [What is deno](#what-is-deno)|
|410| [How do you make an object iterable in javascript](#how-do-you-make-an-object-iterable-in-javascript)|
|411| [What is a Proper Tail Call](#what-is-a-proper-tail-call)|
|412| [How do you check an object is a promise or not](#how-do-you-check-an-object-is-a-promise-or-not)|
|413| [How to detect if a function is called as constructor](#how-to-detect-if-a-function-is-called-as-constructor)|
|414| [What are the differences between arguments object and rest parameter](#what-are-the-differences-between-arguments-object-and-rest-parameter)|
|415| [What are the differences between spread operator and rest parameter](#what-are-the-differences-between-spread-operator-and-rest-parameter)|
|416| [What are the different kinds of generators](#what-are-the-different-kinds-of-generators)|
|417| [What are the built-in iterables](#what-are-the-built-in-iterables)|
|418| [What are the differences between for...of and for...in statements](#what-are-the-differences-between-for...of-and-for...in-statements)|
|419| [How do you define instance and non-instance properties](#how-do-you-define-instance-and-non-instance-properties)|
|420| [What is the difference between isNaN and Number.isNaN?](#what-is-the-difference-between-isnan-and-number.isnan)|
|421| [How to invoke an IIFE without any extra brackets?](#how-to-invoke-an-iife-without-any-extra-brackets)|
|422| [Is that possible to use expressions in switch cases?](#is-that-possible-to-use-expressions-in-switch-cases)|
|423| [What is the easiest way to ignore promise errors?](#what-is-the-easiest-way-to-ignore-promise-errors)|
|424| [How do style the console output using CSS?](#how-do-style-the-console-output-using-css)|

1. ### What are the possible ways to create objects in JavaScript

   There are many ways to create objects in javascript as below

   1. **Object constructor:**

      The simplest way to create an empty object is using the Object constructor. Currently this approach is not recommended.

      ```javascript
      var object = new Object();
      ```

   2. **Object's create method:**

      The create method of Object creates a new object by passing the prototype object as a parameter

      ```javascript
      var object = Object.create(null);
      ```

   3. **Object literal syntax:**

      The object literal syntax is equivalent to create method when it passes null as parameter

      ```javascript
      var object = {};
      ```

   4. **Function constructor:**

      Create any function and apply the new operator to create object instances,

      ```javascript
      function Person(name){
         var object = {};
         object.name=name;
         object.age=21;
         return object;
      }
      var object = new Person("Sudheer");
      ```

   5. **Function constructor with prototype:**

      This is similar to function constructor but it uses prototype for their properties and methods,

      ```javascript
      function Person(){}
      Person.prototype.name = "Sudheer";
      var object = new Person();
      ```

      This is equivalent to an instance created with an object create method with a function prototype and then call that function with an instance and parameters as arguments.

      ```javascript
      function func {};

      new func(x, y, z);
      ```

      **(OR)**

      ```javascript
      // Create a new instance using function prototype.
      var newInstance = Object.create(func.prototype)

      // Call the function
      var result = func.call(newInstance, x, y, z),

      // If the result is a non-null object then use it otherwise just use the new instance.
      console.log(result && typeof result === 'object' ? result : newInstance);
      ```

   6. **ES6 Class syntax:**

      ES6 introduces class feature to create the objects

      ```javascript
      class Person {
         constructor(name) {
            this.name = name;
         }
      }

      var object = new Person("Sudheer");
      ```

   7. **Singleton pattern:**

      A Singleton is an object which can only be instantiated one time. Repeated calls to its constructor return the same instance and this way one can ensure that they don't accidentally create multiple instances.

      ```javascript
      var object = new function(){
         this.name = "Sudheer";
      }
      ```

      **[⬆ Back to Top](#table-of-contents)**

2. ### What is a prototype chain

    **Prototype chaining** is used to build new types of objects based on existing ones. It is similar to inheritance in a class based language. 
    
    The prototype on object instance is available through **Object.getPrototypeOf(object)** or **__proto__** property whereas prototype on constructors function is available through **Object.prototype**.

    ![Screenshot](images/prototype_chain.png)

    **[⬆ Back to Top](#table-of-contents)**

3. ### What is the difference between Call, Apply and Bind

    The difference between Call, Apply and Bind can be explained with below examples,

    **Call:** The call() method invokes a function with a given `this` value and arguments provided one by one

    ```javascript
    var employee1 = {firstName: 'John', lastName: 'Rodson'};
    var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

    function invite(greeting1, greeting2) {
        console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
    }

    invite.call(employee1, 'Hello', 'How are you?'); // Hello John Rodson, How are you?
    invite.call(employee2, 'Hello', 'How are you?'); // Hello Jimmy Baily, How are you?
    ```

    **Apply:** Invokes the function with a given `this` value and allows you to pass in arguments as an array

    ```javascript
    var employee1 = {firstName: 'John', lastName: 'Rodson'};
    var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

    function invite(greeting1, greeting2) {
        console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
    }

    invite.apply(employee1, ['Hello', 'How are you?']); // Hello John Rodson, How are you?
    invite.apply(employee2, ['Hello', 'How are you?']); // Hello Jimmy Baily, How are you?
    ```

    **bind:** returns a new function, allowing you to pass any number of arguments

    ```javascript
    var employee1 = {firstName: 'John', lastName: 'Rodson'};
    var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

    function invite(greeting1, greeting2) {
        console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
    }

    var inviteEmployee1 = invite.bind(employee1);
    var inviteEmployee2 = invite.bind(employee2);
    inviteEmployee1('Hello', 'How are you?'); // Hello John Rodson, How are you?
    inviteEmployee2('Hello', 'How are you?'); // Hello Jimmy Baily, How are you?
    ```

    Call and apply are pretty interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for **comma** (separated list) and Apply is for **Array**. 
    
    Whereas Bind creates a new function that will have `this` set to the first parameter passed to bind().

    **[⬆ Back to Top](#table-of-contents)**

4. ### What is JSON and its common operations

    **JSON** is a text-based data format following JavaScript object syntax, which was popularized by `Douglas Crockford`. It is useful when you want to transmit data across a network and it is basically just a text file with an extension of .json, and a MIME type of application/json
    
    **Parsing:** Converting a string to a native object

    ```javascript
    JSON.parse(text)
    ```

    **Stringification:** converting a native object to a string so it can be transmitted across the network

    ```javascript
    JSON.stringify(object)
    ```

    **[⬆ Back to Top](#table-of-contents)**

5. ### What is the purpose of the array slice method

    The **slice()** method returns the selected elements in an array as a new array object. It selects the elements starting at the given start argument, and ends at the given optional end argument without including the last element. If you omit the second argument then it selects till the end.
    
    Some of the examples of this method are,

    ```javascript
    let arrayIntegers = [1, 2, 3, 4, 5];
    let arrayIntegers1 = arrayIntegers.slice(0,2); // returns [1,2]
    let arrayIntegers2 = arrayIntegers.slice(2,3); // returns [3]
    let arrayIntegers3 = arrayIntegers.slice(4); //returns [5]
    ```

    **Note:** Slice method won't mutate the original array but it returns the subset as a new array.

    **[⬆ Back to Top](#table-of-contents)**

6. ### What is the purpose of the array splice method

    The **splice()** method is used either adds/removes items to/from an array, and then returns the removed item. The first argument specifies the array position for insertion or deletion whereas the optional second argument indicates the number of elements to be deleted. Each additional argument is added to the array. 
    
    Some of the examples of this method are,

    ```javascript
    let arrayIntegersOriginal1 = [1, 2, 3, 4, 5];
    let arrayIntegersOriginal2 = [1, 2, 3, 4, 5];
    let arrayIntegersOriginal3 = [1, 2, 3, 4, 5];

    let arrayIntegers1 = arrayIntegersOriginal1.splice(0,2); // returns [1, 2]; original array: [3, 4, 5]
    let arrayIntegers2 = arrayIntegersOriginal2.splice(3); // returns [4, 5]; original array: [1, 2, 3]
    let arrayIntegers3 = arrayIntegersOriginal3.splice(3, 1, "a", "b", "c"); //returns [4]; original array: [1, 2, 3, "a", "b", "c", 5]
    ```

    **Note:** Splice method modifies the original array and returns the deleted array.

    **[⬆ Back to Top](#table-of-contents)**

7. ### What is the difference between slice and splice

    Some of the major difference in a tabular form

    | Slice | Splice |
    |---- | ---------
    | Doesn't modify the original array(immutable)  | Modifies the original array(mutable) |
    | Returns the subset of original array | Returns the deleted elements as array  |
    | Used to pick the elements from array | Used to insert or delete elements to/from array|

    **[⬆ Back to Top](#table-of-contents)**

8. ### How do you compare Object and Map

    **Objects** are similar to **Maps** in that both let you set keys to values, retrieve those values, delete keys, and detect whether something is stored at a key. Due to this reason, Objects have been used as Maps historically. But there are important differences that make using a Map preferable in certain cases.

    1. The keys of an Object are Strings and Symbols, whereas they can be any value for a Map, including functions, objects, and any primitive.
    2. The keys in Map are ordered while keys added to Object are not. Thus, when iterating over it, a Map object returns keys in order of insertion.
    3. You can get the size of a Map easily with the size property, while the number of properties in an Object must be determined manually.
    4. A Map is an iterable and can thus be directly iterated, whereas iterating over an Object requires obtaining its keys in some fashion and iterating over them.
    5. An Object has a prototype, so there are default keys in the map that could collide with your keys if you're not careful. As of ES5 this can be bypassed by using map = Object.create(null), but this is seldom done.
    6. A Map may perform better in scenarios involving frequent addition and removal of key pairs.

    **[⬆ Back to Top](#table-of-contents)**

9. ### What is the difference between == and === operators

    JavaScript provides both strict(===, !==) and type-converting(==, !=) equality comparison. The strict operators take type of variable in consideration, while non-strict operators make type correction/conversion based upon values of variables. The strict operators follow the below conditions for different types,
    1. Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions.
    2. Two numbers are strictly equal when they are numerically equal. i.e, Having the same number value.
       There are two special cases in this,
       1. NaN is not equal to anything, including NaN.
       2. Positive and negative zeros are equal to one another.
    3. Two Boolean operands are strictly equal if both are true or both are false.
    4. Two objects are strictly equal if they refer to the same Object.
    5. Null and Undefined types are not equal with ===, but equal with ==. i.e,
        null===undefined --> false but null==undefined --> true

    Some of the example which covers the above cases,

    ```javascript
    0 == false   // true
    0 === false  // false
    1 == "1"     // true
    1 === "1"    // false
    null == undefined // true
    null === undefined // false
    '0' == false // true
    '0' === false // false
    []==[] or []===[] //false, refer different objects in memory
    {}=={} or {}==={} //false, refer different objects in memory
    ```

    **[⬆ Back to Top](#table-of-contents)**

10. ### What are lambda or arrow functions

    An arrow function is a shorter syntax for a function expression and does not have its own **this, arguments, super, or new.target**. These functions are best suited for non-method functions, and they cannot be used as constructors.

    **[⬆ Back to Top](#table-of-contents)**

11. ### What is a first class function

    In Javascript, functions are first class objects. First-class functions means when functions in that language are treated like any other variable.

    For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable. For example, in the below example, handler functions assigned to a listener

    ```javascript
    const handler = () => console.log ('This is a click handler function');
    document.addEventListener ('click', handler);
    ```

    **[⬆ Back to Top](#table-of-contents)**

12. ### What is a first order function

    First-order function is a function that doesn’t accept another function as an argument and doesn’t return a function as its return value.

    ```javascript
    const firstOrder = () => console.log ('I am a first order function!');
    ```

    **[⬆ Back to Top](#table-of-contents)**

13. ### What is a higher order function

    Higher-order function is a function that accepts another function as an argument or returns a function as a return value or both.

    ```javascript
    const firstOrderFunc = () => console.log ('Hello, I am a First order function');
    const higherOrder = ReturnFirstOrderFunc => ReturnFirstOrderFunc();
    higherOrder(firstOrderFunc);
    ```

    **[⬆ Back to Top](#table-of-contents)**

14. ### What is a unary function

    Unary function (i.e. monadic) is a function that accepts exactly one argument. It stands for a single argument accepted by a function.
    
    Let us take an example of unary function,

    ```javascript
    const unaryFunction = a => console.log (a + 10); // Add 10 to the given argument and display the value
    ```

    **[⬆ Back to Top](#table-of-contents)**

15. ### What is the currying function

    Currying is the process of taking a function with multiple arguments and turning it into a sequence of functions each with only a single argument. Currying is named after a mathematician **Haskell Curry**. By applying currying, a n-ary function turns it into a unary function. 
    
    Let's take an example of n-ary function and how it turns into a currying function,

    ```javascript
    const multiArgFunction = (a, b, c) => a + b + c;
    console.log(multiArgFunction(1,2,3));// 6
    
    const curryUnaryFunction = a => b => c => a + b + c;
    curryUnaryFunction (1); // returns a function: b => c =>  1 + b + c
    curryUnaryFunction (1) (2); // returns a function: c => 3 + c
    curryUnaryFunction (1) (2) (3); // returns the number 6
    ```

    Curried functions are great to improve **code reusability** and **functional composition**.

    **[⬆ Back to Top](#table-of-contents)**

16. ### What is a pure function

    A **Pure function** is a function where the return value is only determined by its arguments without any side effects. i.e, If you call a function with the same arguments 'n' number of times and 'n' number of places in the application then it will always return the same value.
    
    Let's take an example to see the difference between pure and impure functions,

    ```javascript
    //Impure
    let numberArray = [];
    const impureAddNumber = number => numberArray.push(number);
    //Pure
    const pureAddNumber = number => argNumberArray =>
      argNumberArray.concat([number]);

    //Display the results
    console.log (impureAddNumber(6)); // returns 1
    console.log (numberArray); // returns [6]
    console.log (pureAddNumber(7) (numberArray)); // returns [6, 7]
    console.log (numberArray); // returns [6]
    ```

    As per above code snippets, **Push** function is impure itself by altering the array and returning an push number index which is independent of parameter value. Whereas **Concat** on the other hand takes the array and concatenates it with the other array producing a whole new array without side effects. Also, the return value is a concatenation of the previous array.
    
    Remember that Pure functions are important as they simplify unit testing without any side effects and no need for dependency injection. They also avoid tight coupling and make it harder to break your application by not having any side effects. These principles are coming together with **Immutability** concept of ES6 by giving preference to **const** over **let** usage.

    **[⬆ Back to Top](#table-of-contents)**

17. ### What is the purpose of the let keyword

    The `let` statement declares a **block scope local variable**. Hence the variables defined with let keyword are limited in scope to the block, statement, or expression on which it is used. Whereas variables declared with the `var` keyword used to define a variable globally, or locally to an entire function regardless of block scope.
    
    Let's take an example to demonstrate the usage,

    ```javascript
    let counter = 30;
    if (counter === 30) {
      let counter = 31;
      console.log(counter); // 31
    }
    console.log(counter); // 30 (because the variable in if block won't exist here)
    ```

    **[⬆ Back to Top](#table-of-contents)**

18. ### What is the difference between let and var

    You can list out the differences in a tabular format

    | var | let |
    |---- | ---------
    | It is been available from the beginning of JavaScript  | Introduced as part of ES6 |
    | It has function scope | It has block scope  |
    | Variables will be hoisted | Hoisted but not initialized |

    Let's take an example to see the difference,

    ```javascript
    function userDetails(username) {
       if(username) {
         console.log(salary); // undefined due to hoisting
         console.log(age); // ReferenceError: Cannot access 'age' before initialization
         let age = 30;
         var salary = 10000;
       }
       console.log(salary); //10000 (accessible to due function scope)
       console.log(age); //error: age is not defined(due to block scope)
    }
    userDetails('John');
    ```

    **[⬆ Back to Top](#table-of-contents)**

19. ### What is the reason to choose the name let as a keyword

    `let` is a mathematical statement that was adopted by early programming languages like **Scheme** and **Basic**. It has been borrowed from dozens of other languages that use `let` already as a traditional keyword as close to `var` as possible.

    **[⬆ Back to Top](#table-of-contents)**

20. ### How do you redeclare variables in switch block without an error

    If you try to redeclare variables in a `switch block` then it will cause errors because there is only one block. For example, the below code block throws a syntax error as below,

    ```javascript
    let counter = 1;
    switch(x) {
      case 0:
        let name;
        break;

      case 1:
        let name; // SyntaxError for redeclaration.
        break;
    }
    ```

    To avoid this error, you can create a nested block inside a case clause and create a new block scoped lexical environment.

    ```javascript
    let counter = 1;
        switch(x) {
          case 0: {
            let name;
            break;
          }
          case 1: {
            let name; // No SyntaxError for redeclaration.
            break;
          }
        }
    ```

    **[⬆ Back to Top](#table-of-contents)**

21. ### What is the Temporal Dead Zone

    The Temporal Dead Zone is a behavior in JavaScript that occurs when declaring a variable with the let and const keywords, but not with var. In ECMAScript 6, accessing a `let` or `const` variable before its declaration (within its scope) causes a ReferenceError. The time span when that happens, between the creation of a variable’s binding and its declaration, is called the temporal dead zone.
    
    Let's see this behavior with an example,

    ```javascript
    function somemethod() {
      console.log(counter1); // undefined
      console.log(counter2); // ReferenceError
      var counter1 = 1;
      let counter2 = 2;
    }
    ```

    **[⬆ Back to Top](#table-of-contents)**

22. ### What is IIFE(Immediately Invoked Function Expression)

    IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined. The signature of it would be as below,

    ```javascript
    (function ()
        {
          // logic here
        }
     )
    ();
    ```

    The primary reason to use an IIFE is to obtain data privacy because any variables declared within the IIFE cannot be accessed by the outside world. i.e, If you try to access variables with IIFE then it throws an error as below,

    ```javascript
    (function ()
            {
              var message = "IIFE";
              console.log(message);
            }
     )
    ();
    console.log(message); //Error: message is not defined
    ```

    **[⬆ Back to Top](#table-of-contents)**

23. ### What is the benefit of using modules

    There are a lot of benefits to using modules in favour of a sprawling. Some of the benefits are,
    1. Maintainability
    2. Reusability
    3. Namespacing

    **[⬆ Back to Top](#table-of-contents)**

24. ### What is memoization

    Memoization is a programming technique which attempts to increase a function’s performance by caching its previously computed results.  Each time a memoized function is called, its parameters are used to index the cache. If the data is present, then it can be returned, without executing the entire function. Otherwise the function is executed and then the result is added to the cache.
    Let's take an example of adding function with memoization,

    ```javascript
    const memoizAddition = () => {
      let cache = {};
     return (value) => {
      if (value in cache) {
       console.log('Fetching from cache');
       return cache[value]; // Here, cache.value cannot be used as property name starts with the number which is not a valid JavaScript  identifier. Hence, can only be accessed using the square bracket notation.
      }
      else {
       console.log('Calculating result');
       let result = value + 20;
       cache[value] = result;
       return result;
      }
     }
    }
    // returned function from memoizAddition
    const addition = memoizAddition();
    console.log(addition(20)); //output: 40 calculated
    console.log(addition(20)); //output: 40 cached
    ```

    **[⬆ Back to Top](#table-of-contents)**

25. ### What is Hoisting

    Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. Remember that JavaScript only hoists declarations, not initialisation.
    Let's take a simple example of variable hoisting,

    ```javascript
    console.log(message); //output : undefined
    var message = 'The variable Has been hoisted';
    ```

    The above code looks like as below to the interpreter,

    ```javascript
    var message;
    console.log(message);
    message = 'The variable Has been hoisted';
    ```

    **[⬆ Back to Top](#table-of-contents)**

26. ### What are classes in ES6

    In ES6, Javascript classes are primarily syntactic sugar over JavaScript’s existing prototype-based inheritance.
    For example, the prototype based inheritance written in function expression as below,

    ```javascript
    function Bike(model,color) {
        this.model = model;
        this.color = color;
    }

    Bike.prototype.getDetails = function() {
        return this.model + ' bike has' + this.color + ' color';
    };
    ```

    Whereas ES6 classes can be defined as an alternative

    ```javascript
    class Bike{
      constructor(color, model) {
        this.color= color;
        this.model= model;
      }

      getDetails() {
        return this.model + ' bike has' + this.color + ' color';
      }
    }
    ```

    **[⬆ Back to Top](#table-of-contents)**

27. ### What are closures

    A closure is the combination of a function and the lexical environment within which that function was declared. i.e, It is an inner function that has access to the outer or enclosing function’s variables. The closure has three scope chains
    
    1. Own scope where variables defined between its curly brackets
    2. Outer function’s variables
    3. Global variables
    
    Let's take an example of closure concept,

    ```javascript
    function Welcome(name){
      var greetingInfo = function(message){
       console.log(message+' '+name);
      }
    return greetingInfo;
    }
    var myFunction = Welcome('John');
    myFunction('Welcome '); //Output: Welcome John
    myFunction('Hello Mr.'); //output: Hello Mr.John
    ```

    As per the above code, the inner function(i.e, greetingInfo) has access to the variables in the outer function scope(i.e, Welcome) even after the outer function has returned.

    **[⬆ Back to Top](#table-of-contents)**

28. ### What are modules

    Modules refer to small units of independent, reusable code and also act as the foundation of many JavaScript design patterns.  Most of the JavaScript modules export an object literal, a function, or a constructor

    **[⬆ Back to Top](#table-of-contents)**

29. ### Why do you need modules

    Below are the list of benefits using modules in javascript ecosystem
    1. Maintainability
    2. Reusability
    3. Namespacing

    **[⬆ Back to Top](#table-of-contents)**

30. ### What is scope in javascript

    Scope is the accessibility of variables, functions, and objects in some particular part of your code during runtime. In other words, scope determines the visibility of variables and other resources in areas of your code.

    **[⬆ Back to Top](#table-of-contents)**

31. ### What is a service worker

    A Service worker is basically a script (JavaScript file) that runs in the background, separate from a web page and provides features that don't need a web page or user interaction. Some of the major features of service workers are Rich offline experiences(offline first web application development), periodic background syncs, push notifications, intercept and handle network requests and programmatically managing a cache of responses.

    **[⬆ Back to Top](#table-of-contents)**

32. ### How do you manipulate DOM using a service worker

    Service worker can't access the DOM directly. But it can communicate with the pages it controls by responding to messages sent via the `postMessage` interface, and those pages can manipulate the DOM.

    **[⬆ Back to Top](#table-of-contents)**

33. ### How do you reuse information across service worker restarts

    The problem with service worker is that it gets terminated when not in use, and restarted when it's next needed, so you cannot rely on global state within a service worker's `onfetch` and `onmessage` handlers. In this case, service workers will have access to IndexedDB API in order to persist and reuse across restarts.

    **[⬆ Back to Top](#table-of-contents)**

34. ### What is IndexedDB

    IndexedDB is a low-level API for client-side storage of larger amounts of structured data, including files/blobs. This API uses indexes to enable high-performance searches of this data.

    **[⬆ Back to Top](#table-of-contents)**

35. ### What is web storage

    Web storage is an API that provides a mechanism by which browsers can store key/value pairs locally within the user's browser, in a much more intuitive fashion than using cookies. The web storage provides two mechanisms for storing data on the client.
    1. **Local storage:** It stores data for current origin with no expiration date.
    2. **Session storage:** It stores data for one session and the data is lost when the browser tab is closed.

    **[⬆ Back to Top](#table-of-contents)**

36. ### What is a post message

    Post message is a method that enables cross-origin communication between Window objects.(i.e, between a page and a pop-up that it spawned, or between a page and an iframe embedded within it). Generally, scripts on different pages are allowed to access each other if and only if the pages follow same-origin policy(i.e, pages share the same protocol, port number, and host).

    **[⬆ Back to Top](#table-of-contents)**

37. ### What is a Cookie

    A cookie is a piece of data that is stored on your computer to be accessed by your browser. Cookies are saved as key/value pairs.
    For example, you can create a cookie named username as below,

    ```javascript
    document.cookie = "username=John";
    ```

    ![Screenshot](images/cookie.png)

    **[⬆ Back to Top](#table-of-contents)**

38. ### Why do you need a Cookie

    Cookies are used to remember information about the user profile(such as username). It basically involves two steps,
    1. When a user visits a web page, the user profile can be stored in a cookie.
    2. Next time the user visits the page, the cookie remembers the user profile.

    **[⬆ Back to Top](#table-of-contents)**

39. ### What are the options in a cookie

    There are few below options available for a cookie,
    1. By default, the cookie is deleted when the browser is closed but you can change this behavior by setting expiry date (in UTC time).

    ```javascript
    document.cookie = "username=John; expires=Sat, 8 Jun 2019 12:00:00 UTC";
    ```

    1. By default, the cookie belongs to a current page. But you can tell the browser what path the cookie belongs to using a path parameter.

    ```javascript
    document.cookie = "username=John; path=/services";
    ```

    **[⬆ Back to Top](#table-of-contents)**

40. ### How do you delete a cookie

    You can delete a cookie by setting the expiry date as a passed date. You don't need to specify a cookie value in this case.
    For example, you can delete a username cookie in the current page as below.

    ```javascript
    document.cookie = "username=; expires=Fri, 07 Jun 2019 00:00:00 UTC; path=/;";
    ```

    **Note:** You should define the cookie path option to ensure that you delete the right cookie. Some browsers doesn't allow to delete a cookie unless you specify a path parameter.

    **[⬆ Back to Top](#table-of-contents)**

41. ### What are the differences between cookie, local storage and session storage

    Below are some of the differences between cookie, local storage and session storage,

    | Feature | Cookie | Local storage | Session storage |
    |---- | --------- | ----- | ----- |
    | Accessed on client or server side | Both server-side & client-side | client-side only | client-side only |
    | Lifetime | As configured using Expires option  | until deleted | until tab is closed |
    | SSL support | Supported | Not supported | Not supported |
    | Maximum data size | 4KB | 5 MB | 5MB |

    **[⬆ Back to Top](#table-of-contents)**

42. ### What is the main difference between localStorage and sessionStorage

    LocalStorage is the same as SessionStorage but it persists the data even when the browser is closed and reopened(i.e it has no expiration time) whereas in sessionStorage data gets cleared when the page session ends.

    **[⬆ Back to Top](#table-of-contents)**

43. ### How do you access web storage

    The Window object implements the `WindowLocalStorage` and `WindowSessionStorage` objects which has `localStorage`(window.localStorage) and `sessionStorage`(window.sessionStorage) properties respectively. These properties create an instance of the Storage object, through which data items can be set, retrieved and removed for a specific domain and storage type (session or local).
    For example, you can read and write on local storage objects as below

    ```javascript
    localStorage.setItem('logo', document.getElementById('logo').value);
    localStorage.getItem('logo');
    ```

    **[⬆ Back to Top](#table-of-contents)**

44. ### What are the methods available on session storage

    The session storage provided methods for reading, writing and clearing the session data

    ```javascript
    // Save data to sessionStorage
    sessionStorage.setItem('key', 'value');

    // Get saved data from sessionStorage
    let data = sessionStorage.getItem('key');

    // Remove saved data from sessionStorage
    sessionStorage.removeItem('key');

    // Remove all saved data from sessionStorage
    sessionStorage.clear();
    ```

    **[⬆ Back to Top](#table-of-contents)**

45. ### What is a storage event and its event handler

    The StorageEvent is an event that fires when a storage area has been changed in the context of another document. Whereas onstorage property is an EventHandler for processing storage events.
    The syntax would be as below

    ```javascript
     window.onstorage = functionRef;
    ```

    Let's take the example usage of onstorage event handler which logs the storage key and it's values

    ```javascript
    window.onstorage = function(e) {
      console.log('The ' + e.key +
        ' key has been changed from ' + e.oldValue +
        ' to ' + e.newValue + '.');
    };
    ```

    **[⬆ Back to Top](#table-of-contents)**

46. ### Why do you need web storage

    Web storage is more secure, and large amounts of data can be stored locally, without affecting website performance. Also, the information is never transferred to the server. Hence this is a more recommended approach than Cookies.

    **[⬆ Back to Top](#table-of-contents)**

47. ### How do you check web storage browser support

    You need to check browser support for localStorage and sessionStorage before using web storage,

    ```javascript
    if (typeof(Storage) !== "undefined") {
      // Code for localStorage/sessionStorage.
    } else {
      // Sorry! No Web Storage support..
    }
    ```

    **[⬆ Back to Top](#table-of-contents)**

48. ### How do you check web workers browser support

    You need to check browser support for web workers before using it

    ```javascript
    if (typeof(Worker) !== "undefined") {
      // code for Web worker support.
    } else {
      // Sorry! No Web Worker support..
    }
    ```

    **[⬆ Back to Top](#table-of-contents)**

49. ### Give an example of a web worker

    You need to follow below steps to start using web workers for counting example
    1. Create a Web Worker File:  You need to write a script to increment the count value. Let's name it as counter.js

    ```javascript
    let i = 0;

    function timedCount() {
      i = i + 1;
      postMessage(i);
      setTimeout("timedCount()",500);
    }

    timedCount();
    ```

    Here postMessage() method is used to post a message back to the HTML page
    1. Create a Web Worker Object: You can create a web worker object by checking for browser support. Let's name this file as web_worker_example.js

    ```javascript
    if (typeof(w) == "undefined") {
      w = new Worker("counter.js");
    }
    ```

    and we can receive messages from web worker

    ```javascript
    w.onmessage = function(event){
      document.getElementById("message").innerHTML = event.data;
    };
    ```

    1. Terminate a Web Worker:
    Web workers will continue to listen for messages (even after the external script is finished) until it is terminated. You can use the terminate() method to terminate listening to the messages.

    ```javascript
    w.terminate();
    ```

    1. Reuse the Web Worker: If you set the worker variable to undefined you can reuse the code

    ```javascript
    w = undefined;
    ```

    **[⬆ Back to Top](#table-of-contents)**

50. ### What are the restrictions of web workers on DOM

    WebWorkers don't have access to below javascript objects since they are defined in an external files
    1. Window object
    2. Document object
    3. Parent object

    **[⬆ Back to Top](#table-of-contents)**

51. ### What is a promise

    A promise is an object that may produce a single value some time in the future with either a resolved value or a reason that it’s not resolved(for example, network error). It will be in one of the 3 possible states: fulfilled, rejected, or pending.

    The syntax of Promise creation looks like below,

    ```javascript
        const promise = new Promise(function(resolve, reject) {
          // promise description
        })
    ```

    The usage of a promise would be as below,

    ```javascript
    const promise = new Promise(resolve => {
      setTimeout(() => {
        resolve("I'm a Promise!");
      }, 5000);
    }, reject => {

    });

    promise.then(value => console.log(value));
    ```

    The action flow of a promise will be as below,

    ![Screenshot](images/promises.png)

    **[⬆ Back to Top](#table-of-contents)**

52. ### Why do you need a promise

    Promises are used to handle asynchronous operations. They provide an alternative approach for callbacks by reducing the callback hell and writing the cleaner code.

    **[⬆ Back to Top](#table-of-contents)**

53. ### What are the three states of promise

    Promises have three states:
    1. **Pending:** This is an initial state of the Promise before an operation begins
    2. **Fulfilled:** This state indicates that the specified operation was completed.
    3. **Rejected:** This state indicates that the operation did not complete. In this case an error value will be thrown.

    **[⬆ Back to Top](#table-of-contents)**

54. ### What is a callback function

    A callback function is a function passed into another function as an argument. This function is invoked inside the outer function to complete an action.
    Let's take a simple example of how to use callback function

    ```javascript
    function callbackFunction(name) {
      console.log('Hello ' + name);
    }

    function outerFunction(callback) {
      let name = prompt('Please enter your name.');
      callback(name);
    }

    outerFunction(callbackFunction);
    ```

    **[⬆ Back to Top](#table-of-contents)**

55. ### Why do we need callbacks

    The callbacks are needed because javascript is an event driven language. That means instead of waiting for a response javascript will keep executing while listening for other events.
    Let's take an example with the first function invoking an API call(simulated by setTimeout) and the next function which logs the message.

    ```javascript
    function firstFunction(){
      // Simulate a code delay
      setTimeout( function(){
        console.log('First function called');
      }, 1000 );
    }
    function secondFunction(){
      console.log('Second function called');
    }
    firstFunction();
    secondFunction();

    Output
    // Second function called
    // First function called
    ```

    As observed from the output, javascript didn't wait for the response of the first function and the remaining code block got executed. So callbacks are used in a way to make sure that certain code doesn’t execute until the other code finishes execution.

    **[⬆ Back to Top](#table-of-contents)**

56. ### What is a callback hell

    Callback Hell is an anti-pattern with multiple nested callbacks which makes code hard to read and debug when dealing with asynchronous logic. The callback hell looks like below,

    ```javascript
    async1(function(){
        async2(function(){
            async3(function(){
                async4(function(){
                    ....
                });
            });
        });
    });
    ```

    **[⬆ Back to Top](#table-of-contents)**

57. ### What are server-sent events

    Server-sent events (SSE) is a server push technology enabling a browser to receive automatic updates from a server via HTTP connection without resorting to polling. These are a one way communications channel - events flow from server to client only. This has been used in Facebook/Twitter updates, stock price updates, news feeds etc.

    **[⬆ Back to Top](#table-of-contents)**

58. ### How do you receive server-sent event notifications

    The EventSource object is used to receive server-sent event notifications. For example, you can receive messages from server as below,

    ```javascript
    if(typeof(EventSource) !== "undefined") {
      var source = new EventSource("sse_generator.js");
      source.onmessage = function(event) {
        document.getElementById("output").innerHTML += event.data + "<br>";
      };
    }
    ```

    **[⬆ Back to Top](#table-of-contents)**

59. ### How do you check browser support for server-sent events

    You can perform browser support for server-sent events before using it as below,

    ```javascript
    if(typeof(EventSource) !== "undefined") {
      // Server-sent events supported. Let's have some code here!
    } else {
      // No server-sent events supported
    }
    ```

    **[⬆ Back to Top](#table-of-contents)**

60. ### What are the events available for server sent events

    Below are the list of events available for server sent events
    | Event | Description |
    |---- | ---------
    | onopen  | It is used when a connection to the server is opened |
    | onmessage | This event is used when a message is received  |
    | onerror | It happens when an error occurs|

    **[⬆ Back to Top](#table-of-contents)**

61. ### What are the main rules of promise

    A promise must follow a specific set of rules,
    1. A promise is an object that supplies a standard-compliant `.then()` method
    2. A pending promise may transition into either fulfilled or rejected state
    3. A fulfilled or rejected promise is settled and it must not transition into any other state.
    4. Once a promise is settled, the value must not change.

    **[⬆ Back to Top](#table-of-contents)**

62. ### What is callback in callback

    You can nest one callback inside in another callback to execute the actions sequentially one by one. This is known as callbacks in callbacks.

    ```javascript
    loadScript('/script1.js', function(script) {
       console.log('first script is loaded');

      loadScript('/script2.js', function(script) {

        console.log('second script is loaded');

        loadScript('/script3.js', function(script) {

            console.log('third script is loaded');
          // after all scripts are loaded
        });

      })

    });
    ```

    **[⬆ Back to Top](#table-of-contents)**

63. ### What is promise chaining

    The process of executing a sequence of asynchronous tasks one after another using promises is known as Promise chaining. Let's take an example of promise chaining for calculating the final result,

    ```javascript
    new Promise(function(resolve, reject) {

      setTimeout(() => resolve(1), 1000);

    }).then(function(result) {

      console.log(result); // 1
      return result * 2;

    }).then(function(result) {

      console.log(result); // 2
      return result * 3;

    }).then(function(result) {

      console.log(result); // 6
      return result * 4;

    });
    ```

    In the above handlers, the result is passed to the chain of .then() handlers with the below work flow,
    1. The initial promise resolves in 1 second,
    2. After that `.then` handler is called by logging the result(1) and then return a promise with the value of result * 2.
    3. After that the value passed to the next `.then` handler by logging the result(2) and return a promise with result * 3.
    4. Finally the value passed to the last `.then` handler by logging the result(6) and return a promise with result * 4.

    **[⬆ Back to Top](#table-of-contents)**

64. ### What is promise.all

    Promise.all is a promise that takes an array of promises as an input (an iterable), and it gets resolved when all the promises get resolved or any one of them gets rejected. For example, the syntax of promise.all method is below,

    ```javascript
    Promise.all([Promise1, Promise2, Promise3]) .then(result) => {   console.log(result) }) .catch(error => console.log(`Error in promises ${error}`))
    ```

    **Note:** Remember that the order of the promises(output the result) is maintained as per input order.

    **[⬆ Back to Top](#table-of-contents)**

65. ### What is the purpose of the race method in promise

    Promise.race() method will return the promise instance which is firstly resolved or rejected. Let's take an example of race() method where promise2 is resolved first

    ```javascript
    var promise1 = new Promise(function(resolve, reject) {
        setTimeout(resolve, 500, 'one');
    });
    var promise2 = new Promise(function(resolve, reject) {
        setTimeout(resolve, 100, 'two');
    });

    Promise.race([promise1, promise2]).then(function(value) {
      console.log(value); // "two" // Both promises will resolve, but promise2 is faster
    });
    ```

    **[⬆ Back to Top](#table-of-contents)**

66. ### What is a strict mode in javascript

    Strict Mode is a new feature in ECMAScript 5 that allows you to place a program, or a function, in a “strict” operating context. This way it prevents certain actions from being taken and throws more exceptions. The literal expression `"use strict";` instructs the browser to use the javascript code in the Strict mode.

    **[⬆ Back to Top](#table-of-contents)**

67. ### Why do you need strict mode

    Strict mode is useful to write "secure" JavaScript by notifying "bad syntax" into real errors. For example, it eliminates accidentally creating a global variable by throwing an error and also throws an error for assignment to a non-writable property, a getter-only property, a non-existing property, a non-existing variable, or a non-existing object.

    **[⬆ Back to Top](#table-of-contents)**

68. ### How do you declare strict mode

    The strict mode is declared by adding "use strict"; to the beginning of a script or a function.
    If declared at the beginning of a script, it has global scope.

    ```javascript
    "use strict";
    x = 3.14; // This will cause an error because x is not declared
    ```

    and if you declare inside a function, it has local scope

    ```javascript
    x = 3.14;       // This will not cause an error.
    myFunction();

    function myFunction() {
      "use strict";
      y = 3.14;   // This will cause an error
    }
    ```

    **[⬆ Back to Top](#table-of-contents)**

69. ### What is the purpose of double exclamation

    The double exclamation or negation(!!) ensures the resulting type is a boolean. If it was falsey (e.g. 0, null, undefined, etc.), it will be false, otherwise, true.
    For example, you can test IE version using this expression as below,

    ```javascript
    let isIE8 = false;
    isIE8 = !! navigator.userAgent.match(/MSIE 8.0/);
    console.log(isIE8); // returns true or false
    ```

    If you don't use this expression then it returns the original value.

    ```javascript
    console.log(navigator.userAgent.match(/MSIE 8.0/));  // returns either an Array or null
    ```

    **Note:** The expression !! is not an operator, but it is just twice of ! operator.

    **[⬆ Back to Top](#table-of-contents)**

70. ### What is the purpose of the delete operator

    The delete keyword is used to delete the property as well as its value.

    ```javascript
    var user= {name: "John", age:20};
    delete user.age;

    console.log(user); // {name: "John"}
    ```

    **[⬆ Back to Top](#table-of-contents)**

71. ### What is the typeof operator

    You can use the JavaScript typeof operator to find the type of a JavaScript variable. It returns the type of a variable or an expression.

    ```javascript
    typeof "John Abraham"     // Returns "string"
    typeof (1 + 2)        // Returns "number"
    ```

    **[⬆ Back to Top](#table-of-contents)**

72. ### What is undefined property

    The undefined property indicates that a variable has not been assigned a value, or not declared at all. The type of undefined value is undefined too.

    ```javascript
    var user;    // Value is undefined, type is undefined
    console.log(typeof(user)) //undefined
    ```

    Any variable can be emptied by setting the value to undefined.

    ```javascript
    user = undefined
    ```

    **[⬆ Back to Top](#table-of-contents)**

73. ### What is null value

    The value null represents the intentional absence of any object value. It is one of JavaScript's primitive values. The type of null value is object.
    You can empty the variable by setting the value to null.

    ```javascript
    var user = null;
    console.log(typeof(user)) //object
    ```

    **[⬆ Back to Top](#table-of-contents)**

74. ### What is the difference between null and undefined

    Below are the main differences between null and undefined,

    | Null | Undefined |
    |---- | -----------|
    | It is an assignment value which indicates that variable points to no object.  | It is not an assignment value where a variable has been declared but has not yet been assigned a value. |
    | Type of null is object | Type of undefined is undefined  |
    | The null value is a primitive value that represents the null, empty, or non-existent reference. | The undefined value is a primitive value used when a variable has not been assigned a value.|
    | Indicates the absence of a value for a variable | Indicates absence of variable itself |
    | Converted to zero (0) while performing primitive operations | Converted to NaN while performing primitive operations |

    **[⬆ Back to Top](#table-of-contents)**

75. ### What is eval

    The eval() function evaluates JavaScript code represented as a string. The string can be a JavaScript expression, variable, statement, or sequence of statements.

    ```javascript
    console.log(eval('1 + 2')); //  3
    ```

    **[⬆ Back to Top](#table-of-contents)**

76. ### What is the difference between window and document

    Below are the main differences between window and document,

    | Window | Document |
    |---- | ---------
    | It is the root level element in any web page  | It is the direct child of the window object. This is also known as Document Object Model(DOM) |
    | By default window object is available implicitly in the page | You can access it via window.document or document.  |
    | It has methods like alert(), confirm() and properties like document, location | It provides methods like getElementById, getElementByTagName, createElement etc  |

    **[⬆ Back to Top](#table-of-contents)**

77. ### How do you access history in javascript

    The window.history object contains the browser's history. You can load previous and next URLs in the history using back() and next() methods.

    ```javascript
    function goBack() {
      window.history.back()
    }
    function goForward() {
      window.history.forward()
    }
    ```

    **Note:** You can also access history without window prefix.

    **[⬆ Back to Top](#table-of-contents)**

78. ### How do you detect caps lock key turned on or not

    The `mouseEvent getModifierState()` is used to return a boolean value that indicates whether the specified modifier key is activated or not. The modifiers such as CapsLock, ScrollLock and NumLock are activated when they are clicked, and deactivated when they are clicked again.
    
    Let's take an input element to detect the CapsLock on/off behavior with an example,
    
    ```html
        <input type="password" onmousedown="enterInput(event)">
          
        <p id="feedback"></p>
          
        <script>
        function enterInput(e) {
          var flag = e.getModifierState("CapsLock");
          if(flag) {
              document.getElementById("feedback").innerHTML = "CapsLock activated";
              
          } else {
              document.getElementById("feedback").innerHTML = "CapsLock not activated";
          }
        }
        </script>
    ```

    **[⬆ Back to Top](#table-of-contents)**

79. ### What is isNaN

    The isNaN() function is used to determine whether a value is an illegal number (Not-a-Number) or not. i.e, This function returns true if the value equates to NaN. Otherwise it returns false.

    ```javascript
    isNaN('Hello') //true
    isNaN('100') //false
    ```

    **[⬆ Back to Top](#table-of-contents)**

80. ### What are the differences between undeclared and undefined variables

    Below are the major differences between undeclared and undefined variables,

    | undeclared | undefined |
    |---- | ---------
    | These variables do not exist in a program and are not declared  | These variables declared in the program but have not assigned any value |
    | If you try to read the value of an undeclared variable, then a runtime error is encountered | If you try to read the value of an undefined variable, an undefined value is returned.  |

    **[⬆ Back to Top](#table-of-contents)**

81. ### What are global variables

    Global variables are those that are available throughout the length of the code without any scope. The var keyword is used to declare a local variable but if you omit it then it will become global variable

    ```javascript
    msg = "Hello" // var is missing, it becomes global variable
    ```

    **[⬆ Back to Top](#table-of-contents)**

82. ### What are the problems with global variables

    The problem with global variables is the conflict of variable names of local and global scope. It is also difficult to debug and test the code that relies on global variables.

    **[⬆ Back to Top](#table-of-contents)**

83. ### What is NaN property

    The NaN property is a global property that represents "Not-a-Number" value. i.e, It indicates that a value is not a legal number. It is very rare to use NaN in a program but it can be used as return value for few cases

    ```javascript
    Math.sqrt(-1)
    parseInt("Hello")
    ```

    **[⬆ Back to Top](#table-of-contents)**

84. ### What is the purpose of isFinite function

    The isFinite() function is used to determine whether a number is a finite, legal number. It returns false if the value is +infinity, -infinity, or NaN (Not-a-Number), otherwise it returns true.

    ```javascript
    isFinite(Infinity);  // false
    isFinite(NaN);       // false
    isFinite(-Infinity); // false

    isFinite(100);         // true
    ```

    **[⬆ Back to Top](#table-of-contents)**

85. ### What is an event flow

    Event flow is the order in which event is received on the web page. When you click an element that is nested in various other elements, before your click actually reaches its destination, or target element, it must trigger the click event for each of its parent elements first, starting at the top with the global window object.
    There are two ways of event flow
    1. Top to Bottom(Event Capturing)
    2. Bottom to Top (Event Bubbling)

    **[⬆ Back to Top](#table-of-contents)**

86. ### What is event bubbling

    Event bubbling is a type of event propagation where the event first triggers on the innermost target element, and then successively triggers on the ancestors (parents) of the target element in the same nesting hierarchy till it reaches the outermost DOM element.

    **[⬆ Back to Top](#table-of-contents)**

87. ### What is event capturing

    Event capturing is a type of event propagation where the event is first captured by the outermost element, and then successively triggers on the descendants (children) of the target element in the same nesting hierarchy till it reaches the innermost DOM element.

    **[⬆ Back to Top](#table-of-contents)**

88. ### How do you submit a form using JavaScript

    You can submit a form using JavaScript use document.form[0].submit(). All the form input's information is submitted using onsubmit event handler

    ```javascript
    function submit() {
        document.form[0].submit();
    }
    ```

    **[⬆ Back to Top](#table-of-contents)**

89. ### How do you find operating system details

    The window.navigator object contains information about the visitor's browser OS details. Some of the OS properties are available under platform property,

    ```javascript
    console.log(navigator.platform);
    ```

    **[⬆ Back to Top](#table-of-contents)**

90. ### What is the difference between document load and DOMContentLoaded events

    The `DOMContentLoaded` event is fired when the initial HTML document has been completely loaded and parsed, without waiting for assets(stylesheets, images, and subframes) to finish loading. Whereas The load event is fired when the whole page has loaded, including all dependent resources(stylesheets, images).

    **[⬆ Back to Top](#table-of-contents)**

91. ### What is the difference between native, host and user objects

    `Native objects` are objects that are part of the JavaScript language defined by the ECMAScript specification. For example, String, Math, RegExp, Object, Function etc core objects defined in the ECMAScript spec.
    `Host objects` are objects provided by the browser or runtime environment (Node). For example, window, XmlHttpRequest, DOM nodes etc are considered as host objects.
    `User objects` are objects defined in the javascript code. For example, User objects created for profile information.

    **[⬆ Back to Top](#table-of-contents)**

92. ### What are the tools or techniques used for debugging JavaScript code

    You can use below tools or techniques for debugging javascript
    1. Chrome Devtools
    2. debugger statement
    3. Good old console.log statement

    **[⬆ Back to Top](#table-of-contents)**

93. ### What are the pros and cons of promises over callbacks

    Below are the list of pros and cons of promises over callbacks,

    **Pros:**
    1. It avoids callback hell which is unreadable
    2. Easy to write sequential asynchronous code with .then()
    3. Easy to write parallel asynchronous code with Promise.all()
    4. Solves some of the common problems of callbacks(call the callback too late, too early, many times and swallow errors/exceptions)

    **Cons:**
    1. It makes little complex code
    2. You need to load a polyfill if ES6 is not supported

    **[⬆ Back to Top](#table-of-contents)**

94. ### What is the difference between an attribute and a property

    Attributes are defined on the HTML markup whereas properties are defined on the DOM. For example, the below HTML element has 2 attributes type and value,

    ```javascript
    <input type="text" value="Name:">
    ```

    You can retrieve the attribute value as below,

    ```javascript
    const input = document.querySelector('input');
    console.log(input.getAttribute('value')); // Good morning
    console.log(input.value); // Good morning
    ```

    And after you change the value of the text field to "Good evening", it becomes like

    ```javascript
    console.log(input.getAttribute('value')); // Good morning
    console.log(input.value); // Good evening
    ```

    **[⬆ Back to Top](#table-of-contents)**

95. ### What is same-origin policy

    The same-origin policy is a policy that prevents JavaScript from making requests across domain boundaries. An origin is defined as a combination of URI scheme, hostname, and port number. If you enable this policy then it prevents a malicious script on one page from obtaining access to sensitive data on another web page using Document Object Model(DOM).

    **[⬆ Back to Top](#table-of-contents)**

96. ### What is the purpose of void 0

    Void(0) is used to prevent the page from refreshing. This will be helpful to eliminate the unwanted side-effect, because it will return the undefined primitive value. It is commonly used for HTML documents that use href="JavaScript:Void(0);" within an ```<a>``` element. i.e, when you click a link, the browser loads a new page or refreshes the same page. But this behavior will be prevented using this expression.
    For example, the below link notify the message without reloading the page

    ```javascript
    <a href="JavaScript:void(0);" onclick="alert('Well done!')">Click Me!</a>
    ```

    **[⬆ Back to Top](#table-of-contents)**

97. ### Is JavaScript a compiled or interpreted language

    JavaScript is an interpreted language, not a compiled language. An interpreter in the browser reads over the JavaScript code, interprets each line, and runs it. Nowadays  modern browsers use a technology known as Just-In-Time (JIT) compilation, which compiles JavaScript to executable bytecode just as it is about to run.

    **[⬆ Back to Top](#table-of-contents)**

98. ### Is JavaScript a case-sensitive language

    Yes, JavaScript is a case sensitive language. The language keywords, variables, function & object names, and any other identifiers must always be typed with a consistent capitalization of letters.

    **[⬆ Back to Top](#table-of-contents)**

99. ### Is there any relation between Java and JavaScript

    No, they are entirely two different programming languages and have nothing to do with each other. But both of them are Object Oriented Programming languages and like many other languages, they follow similar syntax for basic features(if, else, for, switch, break, continue etc).

    **[⬆ Back to Top](#table-of-contents)**

100. ### What are events

     Events are "things" that happen to HTML elements. When JavaScript is used in HTML pages, JavaScript can `react` on these events. Some of the examples of HTML events are,

     1. Web page has finished loading
     2. Input field was changed
     3. Button was clicked

     Let's describe the behavior of click event for button element,

     ```javascript
     <!doctype html>
     <html>
      <head>
        <script>
          function greeting() {
            alert('Hello! Good morning');
          }
        </script>
      </head>
      <body>
        <button type="button" onclick="greeting()">Click me</button>
      </body>
     </html>
     ```

     **[⬆ Back to Top](#table-of-contents)**

101. ### Who created javascript

     JavaScript was created by Brendan Eich in 1995 during his time at Netscape Communications. Initially it was developed under the name `Mocha`, but later the language was officially called `LiveScript` when it first shipped in beta releases of Netscape.

     **[⬆ Back to Top](#table-of-contents)**

102. ### What is the use of preventDefault method

     The preventDefault() method cancels the event if it is cancelable, meaning that the default action or behaviour that belongs to the event will not occur. For example, prevent form submission when clicking on submit button and prevent opening the page URL when clicking on hyperlink are some common use cases.

     ```javascript
     document.getElementById("link").addEventListener("click", function(event){
      event.preventDefault();
     });
     ```

     **Note:** Remember that not all events are cancelable.

     **[⬆ Back to Top](#table-of-contents)**

103. ### What is the use of stopPropagation method

     The stopPropagation method is used to stop the event from bubbling up the event chain. For example, the below nested divs with stopPropagation method prevents default event propagation when clicking on nested div(Div1)

     ```javascript
     <p>Click DIV1 Element</p>
     <div onclick="secondFunc()">DIV 2
       <div onclick="firstFunc(event)">DIV 1</div>
     </div>

     <script>
     function firstFunc(event) {
       alert("DIV 1");
       event.stopPropagation();
     }

     function secondFunc() {
       alert("DIV 2");
     }
     </script>
     ```

     **[⬆ Back to Top](#table-of-contents)**

104. ### What are the steps involved in return false usage

     The return false statement in event handlers performs the below steps,

     1. First it stops the browser's default action or behaviour.
     2. It prevents the event from propagating the DOM
     3. Stops callback execution and returns immediately when called.

     **[⬆ Back to Top](#table-of-contents)**

105. ### What is BOM

     The Browser Object Model (BOM) allows JavaScript to "talk to" the browser. It consists of the objects navigator, history, screen, location and document which are children of the window. The Browser Object Model is not standardized and can change based on different browsers.

     ![Screenshot](images/bom.png)

     **[⬆ Back to Top](#table-of-contents)**

106. ### What is the use of setTimeout

     The setTimeout() method is used to call a function or evaluate an expression after a specified number of milliseconds. For example, let's log a message after 2 seconds using setTimeout method,

     ```javascript
     setTimeout(function(){ console.log("Good morning"); }, 2000);
     ```

     **[⬆ Back to Top](#table-of-contents)**

107. ### What is the use of setInterval

     The setInterval() method is used to call a function or evaluate an expression at specified intervals (in milliseconds). For example, let's log a message after 2 seconds using setInterval method,

     ```javascript
     setInterval(function(){ console.log("Good morning"); }, 2000);
     ```

     **[⬆ Back to Top](#table-of-contents)**

108. ### Why is JavaScript treated as Single threaded

     JavaScript is a single-threaded language. Because the language specification does not allow the programmer to write code so that the interpreter can run parts of it in parallel in multiple threads or processes. Whereas languages like java, go, C++ can make multi-threaded and multi-process programs.

     **[⬆ Back to Top](#table-of-contents)**

109. ### What is an event delegation

     Event delegation is a technique for listening to events where you delegate a parent element as the listener for all of the events that happen inside it.

     For example, if you wanted to detect field changes in inside a specific form, you can use event delegation technique,

     ```javascript
     var form = document.querySelector('#registration-form');

     // Listen for changes to fields inside the form
     form.addEventListener('input', function (event) {

     // Log the field that was changed
     console.log(event.target);

     }, false);
     ```

     **[⬆ Back to Top](#table-of-contents)**

110. ### What is ECMAScript

     ECMAScript is the scripting language that forms the basis of JavaScript. ECMAScript standardized by the ECMA International standards organization in the ECMA-262 and ECMA-402 specifications. The first edition of ECMAScript was released in 1997.

     **[⬆ Back to Top](#table-of-contents)**

111. ### What is JSON

     JSON (JavaScript Object Notation) is a lightweight format that is used for data interchanging. It is based on a subset of JavaScript language in the way objects are built in JavaScript.

     **[⬆ Back to Top](#table-of-contents)**

112. ### What are the syntax rules of JSON

     Below are the list of syntax rules of JSON
     1. The data is in name/value pairs
     2. The data is separated by commas
     3. Curly braces hold objects
     4. Square brackets hold arrays

     **[⬆ Back to Top](#table-of-contents)**

113. ### What is the purpose JSON stringify

     When sending data to a web server, the data has to be in a string format. You can achieve this by converting JSON object into a string using stringify() method.

     ```javascript
     var userJSON = {'name': 'John', age: 31}
     var userString = JSON.stringify(user);
     console.log(userString); //"{"name":"John","age":31}"
     ```

     **[⬆ Back to Top](#table-of-contents)**

114. ### How do you parse JSON string

     When receiving the data from a web server, the data is always in a string format. But you can convert this string value to a javascript object using parse() method.

     ```javascript
     var userString = '{"name":"John","age":31}';
     var userJSON = JSON.parse(userString);
     console.log(userJSON);// {name: "John", age: 31}
     ```

     **[⬆ Back to Top](#table-of-contents)**

115. ### Why do you need JSON

     When exchanging data between a browser and a server, the data can only be text. Since JSON is text only, it can easily be sent to and from a server, and used as a data format by any programming language.

     **[⬆ Back to Top](#table-of-contents)**

116. ### What are PWAs

     Progressive web applications (PWAs) are a type of mobile app delivered through the web, built using common web technologies including HTML, CSS and JavaScript. These PWAs are deployed to servers, accessible through URLs, and indexed by search engines.

     **[⬆ Back to Top](#table-of-contents)**

117. ### What is the purpose of clearTimeout method

     The clearTimeout() function is used in javascript to clear the timeout which has been set by setTimeout()function before that. i.e, The return value of setTimeout() function is stored in a variable and it’s passed into the clearTimeout() function to clear the timer.

     For example, the below setTimeout method is used to display the message after 3 seconds. This timeout can be cleared by the clearTimeout() method.

     ```javascript
     <script>
     var msg;
     function greeting() {
        alert('Good morning');
     }
     function start() {
       msg =setTimeout(greeting, 3000);

     }

     function stop() {
         clearTimeout(msg);
     }
     </script>
     ```

     **[⬆ Back to Top](#table-of-contents)**

118. ### What is the purpose of clearInterval method

     The clearInterval() function is used in javascript to clear the interval which has been set by setInterval() function. i.e, The return value returned by setInterval() function is stored in a variable and it’s passed into the clearInterval() function to clear the interval.

     For example, the below setInterval method is used to display the message for every 3 seconds. This interval can be cleared by the clearInterval() method.

     ```javascript
     <script>
     var msg;
     function greeting() {
        alert('Good morning');
     }
     function start() {
       msg = setInterval(greeting, 3000);

     }

     function stop() {
         clearInterval(msg);
     }
     </script>
     ```

     **[⬆ Back to Top](#table-of-contents)**

119. ### How do you redirect new page in javascript

     In vanilla javascript, you can redirect to a new page using the `location` property of window object. The syntax would be as follows,

     ```javascript
     function redirect() {
        window.location.href = 'newPage.html';
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

120. ### How do you check whether a string contains a substring

     There are 3 possible ways to check whether a string contains a substring or not,
     1. **Using includes:** ES6 provided `String.prototype.includes` method to test a string contains a substring

     ```javascript
     var mainString = "hello", subString = "hell";
     mainString.includes(subString)
     ```

     1. **Using indexOf:** In an ES5 or older environment, you can use `String.prototype.indexOf` which returns the index of a substring. If the index value is not equal to -1 then it means the substring exists in the main string.

     ```javascript
     var mainString = "hello", subString = "hell";
     mainString.indexOf(subString) !== -1
     ```

     1. **Using RegEx:** The advanced solution is using Regular expression's test method(`RegExp.test`), which allows for testing for against regular expressions

     ```javascript
     var mainString = "hello", regex = /hell/;
     regex.test(mainString)
     ```

     **[⬆ Back to Top](#table-of-contents)**

121. ### How do you validate an email in javascript

     You can validate an email in javascript using regular expressions. It is recommended to do validations on the server side instead of the client side. Because the javascript can be disabled on the client side.

     ```javascript
     function validateEmail(email) {
         var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
         return re.test(String(email).toLowerCase());
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

     The above regular expression accepts unicode characters.

122. ### How do you get the current url with javascript

     You can use `window.location.href` expression to get the current url path and you can use the same expression for updating the URL too. You can also use `document.URL` for read-only purposes but this solution has issues in FF.

     ```javascript
     console.log('location.href', window.location.href); // Returns full URL
     ```

     **[⬆ Back to Top](#table-of-contents)**

123. ### What are the various url properties of location object

     The below `Location` object properties can be used to access URL components of the page,
     1. href - The entire URL
     2. protocol - The protocol of the URL
     3. host - The hostname and port of the URL
     4. hostname - The hostname of the URL
     5. port - The port number in the URL
     6. pathname - The path name of the URL
     7. search - The query portion of the URL
     8. hash - The anchor portion of the URL

     **[⬆ Back to Top](#table-of-contents)**

124. ### How do get query string values in javascript

     You can use URLSearchParams to get query string values in javascript. Let's see an example to get the client code value from URL query string,

     ```javascript
     const urlParams = new URLSearchParams(window.location.search);
     const clientCode = urlParams.get('clientCode');
     ```

     **[⬆ Back to Top](#table-of-contents)**

125. ### How do you check if a key exists in an object

     You can check whether a key exists in an object or not using three approaches,

     1. **Using in operator:** You can use the in operator whether a key exists in an object or not

     ```javascript
     "key" in obj
     ```

     and If you want to check if a key doesn't exist, remember to use parenthesis,

     ```javascript
     !("key" in obj)
     ```

     1. **Using hasOwnProperty method:** You can use `hasOwnProperty` to particularly test for properties of the object instance (and not inherited properties)

     ```javascript
     obj.hasOwnProperty("key") // true
     ```

     1. **Using undefined comparison:** If you access a non-existing property from an object, the result is undefined. Let’s compare the properties against undefined to determine the existence of the property.

     ```javascript
     const user = {
       name: 'John'
     };

     console.log(user.name !== undefined);     // true
     console.log(user.nickName !== undefined); // false
     ```

     **[⬆ Back to Top](#table-of-contents)**

126. ### How do you loop through or enumerate javascript object

     You can use the `for-in` loop to loop through javascript object. You can also make sure that the key you get is an actual property of an object, and doesn't come from the prototype using `hasOwnProperty` method.

     ```javascript
     var object = {
         "k1": "value1",
         "k2": "value2",
         "k3": "value3"
     };

     for (var key in object) {
         if (object.hasOwnProperty(key)) {
             console.log(key + " -> " + object[key]); // k1 -> value1 ...
         }
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

127. ### How do you test for an empty object

     There are different solutions based on ECMAScript versions
     1. **Using Object entries(ECMA 7+):** You can use object entries length along with constructor type.

     ```javascript
     Object.entries(obj).length === 0 && obj.constructor === Object // Since date object length is 0, you need to check constructor check as well
     ```

     1. **Using Object keys(ECMA 5+):** You can use object keys length along with constructor type.

     ```javascript
     Object.keys(obj).length === 0 && obj.constructor === Object // Since date object length is 0, you need to check constructor check as well
     ```

     1. **Using for-in with hasOwnProperty(Pre-ECMA 5):** You can use a for-in loop along with hasOwnProperty.

     ```javascript
     function isEmpty(obj) {
       for(var prop in obj) {
         if(obj.hasOwnProperty(prop)) {
           return false;
         }
       }

       return JSON.stringify(obj) === JSON.stringify({});
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

128. ### What is an arguments object

     The arguments object is an Array-like object accessible inside functions that contains the values of the arguments passed to that function. For example, let's see how to use arguments object inside sum function,

     ```javascript
     function sum() {
         var total = 0;
         for (var i = 0, len = arguments.length; i < len; ++i) {
             total += arguments[i];
         }
         return total;
     }

     sum(1, 2, 3) // returns 6
     ```

     **Note:** You can't apply array methods on arguments object. But you can convert into a regular array as below.

     ```javascript
     var argsArray = Array.prototype.slice.call(arguments);
     ```

     **[⬆ Back to Top](#table-of-contents)**

129. ### How do you make first letter of the string in an uppercase

     You can create a function which uses a chain of string methods such as charAt, toUpperCase and slice methods to generate a string with the first letter in uppercase.

     ```javascript
     function capitalizeFirstLetter(string) {
         return string.charAt(0).toUpperCase() + string.slice(1);
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

130. ### What are the pros and cons of for loop

     The for-loop is a commonly used iteration syntax in javascript. It has both pros and cons
     ####Pros
     1. Works on every environment
     2. You can use break and continue flow control statements

     ####Cons
     1. Too verbose
     2. Imperative
     3. You might face one-by-off errors

     **[⬆ Back to Top](#table-of-contents)**

131. ### How do you display the current date in javascript

     You can use `new Date()` to generate a new Date object containing the current date and time. For example, let's display the current date in mm/dd/yyyy

     ```javascript
     var today = new Date();
     var dd = String(today.getDate()).padStart(2, '0');
     var mm = String(today.getMonth() + 1).padStart(2, '0'); //January is 0!
     var yyyy = today.getFullYear();

     today = mm + '/' + dd + '/' + yyyy;
     document.write(today);
     ```

     **[⬆ Back to Top](#table-of-contents)**

132. ### How do you compare two date objects

     You need to use date.getTime() method to compare date values instead of comparison operators (==, !=, ===, and !== operators)

     ```javascript
     var d1 = new Date();
     var d2 = new Date(d1);
     console.log(d1.getTime() === d2.getTime()); //True
     console.log(d1 === d2); // False
     ```

     **[⬆ Back to Top](#table-of-contents)**

133. ### How do you check if a string starts with another string

     You can use ECMAScript 6's `String.prototype.startsWith()` method to check if a string starts with another string or not. But it is not yet supported in all browsers. Let's see an example to see this usage,

     ```javascript
     "Good morning".startsWith("Good"); // true
     "Good morning".startsWith("morning"); // false
     ```

     **[⬆ Back to Top](#table-of-contents)**

134. ### How do you trim a string in javascript

     JavaScript provided a trim method on string types to trim any whitespaces present at the beginning or ending of the string.

     ```javascript
     "  Hello World   ".trim(); //Hello World
     ```

     If your browser(<IE9) doesn't support this method then you can use below polyfill.

     ```javascript
     if (!String.prototype.trim) {
         (function() {
             // Make sure we trim BOM and NBSP
             var rtrim = /^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g;
             String.prototype.trim = function() {
                 return this.replace(rtrim, '');
             };
         })();
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

135. ### How do you add a key value pair in javascript

     There are two possible solutions to add new properties to an object. Let's take a simple object to explain these solutions.

     ```javascript
     var object = {
         key1: value1,
         key2: value2
     };
     ```

     1. **Using dot notation:** This solution is useful when you know the name of the property

     ```javascript
     object.key3 = "value3";
     ```

     1. **Using square bracket notation:** This solution is useful when the name of the property is dynamically determined.

     ```javascript
     obj["key3"] = "value3";
     ```

     **[⬆ Back to Top](#table-of-contents)**

136. ### Is the !-- notation represents a special operator

     No,that's not a special operator. But it is a combination of 2 standard operators one after the other,
     1. A logical not (!)
     2. A prefix decrement (--)

     At first, the value decremented by one and then tested to see if it is equal to zero or not for determining the truthy/falsy value.

     **[⬆ Back to Top](#table-of-contents)**

137. ### How do you assign default values to variables

     You can use the logical or operator `||` in an assignment expression to provide a default value. The syntax looks like as below,

     ```javascript
     var a = b || c;
     ```

     As per the above expression, variable 'a 'will get the value of 'c' only if 'b' is falsy (if is null, false, undefined, 0, empty string, or NaN), otherwise 'a' will get the value of 'b'.

     **[⬆ Back to Top](#table-of-contents)**

138. ### How do you define multiline strings

     You can define multiline string literals using the '\' character followed by line terminator.

     ```javascript
     var str = "This is a \
     very lengthy \
     sentence!";
     ```

     But if you have a space after the '\' character, the code will look exactly the same, but it will raise a SyntaxError.

     **[⬆ Back to Top](#table-of-contents)**

139. ### What is an app shell model

     An application shell (or app shell) architecture is one way to build a Progressive Web App that reliably and instantly loads on your users' screens, similar to what you see in native applications. It is useful for getting some initial HTML to the screen fast without a network.

     **[⬆ Back to Top](#table-of-contents)**

140. ### Can we define properties for functions

     Yes, We can define properties for functions because functions are also objects.

     ```javascript
     fn = function(x) {
        //Function code goes here
     }

     fn.name = "John";

     fn.profile = function(y) {
       //Profile code goes here
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

141. ### What is the way to find the number of parameters expected by a function

     You can use `function.length` syntax to find the number of parameters expected by a function. Let's take an example of `sum` function to calculate the sum of numbers,

     ```javascript
     function sum(num1, num2, num3, num4){
         return num1 + num2 + num3 + num4;
     }
     sum.length // 4 is the number of parameters expected.
     ```

     **[⬆ Back to Top](#table-of-contents)**

142. ### What is a polyfill

     A polyfill is a piece of JS code used to provide modern functionality on older browsers that do not natively support it. For example, Silverlight plugin polyfill can be used to mimic the functionality of an HTML Canvas element on Microsoft Internet Explorer 7.

     **[⬆ Back to Top](#table-of-contents)**

143. ### What are break and continue statements

     The break statement is used to "jump out" of a loop. i.e, It breaks the loop and continues executing the code after the loop.

     ```javascript
     for (i = 0; i < 10; i++) {
       if (i === 5) { break; }
       text += "Number: " + i + "<br>";
     }
     ```

     The continue statement is used to "jump over" one iteration in the loop. i.e, It breaks one iteration (in the loop), if a specified condition occurs, and continues with the next iteration in the loop.

     ```javascript
     for (i = 0; i < 10; i++) {
         if (i === 5) { continue; }
         text += "Number: " + i + "<br>";
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

144. ### What are js labels

     The label statement allows us to name loops and blocks in JavaScript. We can then use these labels to refer back to the code later. For example, the below code with labels avoids printing the numbers when they are same,

     ```javascript
     var i, j;

     loop1:
     for (i = 0; i < 3; i++) {
        loop2:
        for (j = 0; j < 3; j++) {
           if (i === j) {
              continue loop1;
           }
           console.log('i = ' + i + ', j = ' + j);
        }
     }

     // Output is:
     //   "i = 1, j = 0"
     //   "i = 2, j = 0"
     //   "i = 2, j = 1"
     ```

     **[⬆ Back to Top](#table-of-contents)**

145. ### What are the benefits of keeping declarations at the top

     It is recommended to keep all declarations at the top of each script or function. The benefits of doing this are,
     1. Gives cleaner code
     2. It provides a single place to look for local variables
     3. Easy to avoid unwanted global variables
     4. It reduces the possibility of unwanted re-declarations

     **[⬆ Back to Top](#table-of-contents)**

146. ### What are the benefits of initializing variables

     It is recommended to initialize variables because of the below benefits,
     1. It gives cleaner code
     2. It provides a single place to initialize variables
     3. Avoid undefined values in the code

     **[⬆ Back to Top](#table-of-contents)**

147. ### What are the recommendations to create new object

     It is recommended to avoid creating new objects using `new Object()`. Instead you can initialize values based on it's type to create the objects.
     1. Assign {} instead of new Object()
     2. Assign "" instead of new String()
     3. Assign 0 instead of new Number()
     4. Assign false instead of new Boolean()
     5. Assign [] instead of new Array()
     6. Assign /()/ instead of new RegExp()
     7. Assign function (){} instead of new Function()

     You can define them as an example,

     ```javascript
     var v1 = {};
     var v2 = "";
     var v3 = 0;
     var v4 = false;
     var v5 = [];
     var v6 = /()/;
     var v7 = function(){};
     ```

     **[⬆ Back to Top](#table-of-contents)**

148. ### How do you define JSON arrays

     JSON arrays are written inside square brackets and arrays contain javascript objects. For example, the JSON array of users would be as below,

     ```javascript
     "users":[
       {"firstName":"John", "lastName":"Abrahm"},
       {"firstName":"Anna", "lastName":"Smith"},
       {"firstName":"Shane", "lastName":"Warn"}
     ]
     ```

     **[⬆ Back to Top](#table-of-contents)**

149. ### How do you generate random integers

     You can use Math.random() with Math.floor() to return random integers. For example, if you want generate random integers between 1 to 10, the multiplication factor should be 10,

     ```javascript
     Math.floor(Math.random() * 10) + 1;     // returns a random integer from 1 to 10
     Math.floor(Math.random() * 100) + 1;     // returns a random integer from 1 to 100
     ```

     **Note:** Math.random() returns a random number between 0 (inclusive),  and 1 (exclusive)

     **[⬆ Back to Top](#table-of-contents)**

150. ### Can you write a random integers function to print integers with in a range

     Yes, you can create a proper random function to return a random number between min and max (both included)

     ```javascript
     function randomInteger(min, max) {
       return Math.floor(Math.random() * (max - min + 1) ) + min;
     }
     randomInteger(1, 100); // returns a random integer from 1 to 100
     randomInteger(1, 1000); // returns a random integer from 1 to 1000
     ```

     **[⬆ Back to Top](#table-of-contents)**

151. ### What is tree shaking

     Tree shaking is a form of dead code elimination. It means that unused modules will not be included in the bundle during the build process and for that it relies on the static structure of ES2015 module syntax,( i.e. import and export). Initially this has been popularized by the ES2015 module bundler `rollup`.

     **[⬆ Back to Top](#table-of-contents)**

152. ### What is the need of tree shaking

     Tree Shaking can significantly reduce the code size in any application. i.e, The less code we send over the wire the more performant the application will be. For example, if we just want to create a “Hello World” Application using SPA frameworks then it will take around a few MBs, but by tree shaking it can bring down the size to just a few hundred KBs. Tree shaking is implemented in Rollup and Webpack bundlers.

     **[⬆ Back to Top](#table-of-contents)**

153. ### Is it recommended to use eval

     No, it allows arbitrary code to be run which causes a security problem. As we know that the eval() function is used to run text as code. In most of the cases, it should not be necessary to use it.

     **[⬆ Back to Top](#table-of-contents)**

154. ### What is a Regular Expression

     A regular expression is a sequence of characters that forms a search pattern. You can use this search pattern for searching data in a text. These can be used to perform all types of text search and text replace operations. Let's see the syntax format now,

     ```javascript
     /pattern/modifiers;
     ```

     For example, the regular expression or search pattern with case-insensitive username would be,

     ```javascript
     /John/i
     ```

     **[⬆ Back to Top](#table-of-contents)**

155. ### What are the string methods available in Regular expression

     Regular Expressions has two string methods: search() and replace().
     The search() method uses an expression to search for a match, and returns the position of the match.

     ```javascript
     var msg = "Hello John";
     var n = msg.search(/John/i); // 6
     ```

     The replace() method is used to return a modified string where the pattern is replaced.

     ```javascript
     var msg = "Hello John";
     var n = msg.replace(/John/i, "Buttler"); // Hello Buttler
     ```

     **[⬆ Back to Top](#table-of-contents)**

156. ### What are modifiers in regular expression

      Modifiers can be used to perform case-insensitive and global searches. Let's list down some of the modifiers,

      | Modifier | Description |
      |---- | ---------
      | i  | Perform case-insensitive matching |
      | g | Perform a global match rather than stops at first match  |
      | m | Perform multiline matching|

      Let's take an example of global modifier,

      ```javascript
      var text = "Learn JS one by one";
      var pattern = /one/g;
      var result = text.match(pattern); // one,one
      ```

      **[⬆ Back to Top](#table-of-contents)**

157. ### What are regular expression patterns

     Regular Expressions provide a group of patterns in order to match characters. Basically they are categorized into 3 types,
     1. **Brackets:** These are used to find a range of characters.
        For example, below are some use cases,
        1. [abc]: Used to find any of the characters between the brackets(a,b,c)
        2. [0-9]: Used to find any of the digits between the brackets
        3. (a|b): Used to find any of the alternatives separated with |
     2. **Metacharacters:** These are characters with a special meaning
        For example, below are some use cases,
        1. \\d: Used to find a digit
        2. \\s: Used to find a whitespace character
        3. \\b: Used to find a match at the beginning or ending of a word
     3. **Quantifiers:** These are useful to define quantities
        For example, below are some use cases,
        1. n+: Used to find matches for any string that contains at least one n
        2. n*: Used to find matches for any string that contains zero or more occurrences of n
        3. n?: Used to find matches for any string that contains zero or one occurrences of n

     **[⬆ Back to Top](#table-of-contents)**

158. ### What is a RegExp object

     RegExp object is a regular expression object with predefined properties and methods. Let's see the simple usage of RegExp object,

     ```javascript
     var regexp = new RegExp('\\w+');
     console.log(regexp);
     // expected output: /\w+/
     ```

     **[⬆ Back to Top](#table-of-contents)**

159. ### How do you search a string for a pattern

     You can use the test() method of regular expression in order to search a string for a pattern, and return true or false depending on the result.

     ```javascript
     var pattern = /you/;
     console.log(pattern.test("How are you?")); //true
     ```

     **[⬆ Back to Top](#table-of-contents)**

160. ### What is the purpose of exec method

     The purpose of exec method is similar to test method but it executes a search for a match in a specified string and returns a result array, or null instead of returning true/false.

     ```javascript
     var pattern = /you/;
     console.log(pattern.exec("How are you?")); //["you", index: 8, input: "How are you?", groups: undefined]
     ```

     **[⬆ Back to Top](#table-of-contents)**

161. ### How do you change the style of a HTML element

     You can change inline style or classname of a HTML element using javascript
     1. **Using style property:** You can modify inline style using style property

     ```javascript
     document.getElementById("title").style.fontSize = "30px";
     ```

     1. **Using ClassName property:** It is easy to modify element class using className property

     ```javascript
      document.getElementById("title").className = "custom-title";
      ```

     **[⬆ Back to Top](#table-of-contents)**

162. ### What would be the result of 1+2+'3'

     The output is going to be `33`. Since `1` and `2` are numeric values, the result of the first two digits is going to be a numeric value `3`. The next digit is a string type value because of that the addition of numeric value `3` and string type value `3` is just going to be a concatenation value `33`.

     **[⬆ Back to Top](#table-of-contents)**

163. ### What is a debugger statement

     The debugger statement invokes any available debugging functionality, such as setting a breakpoint. If no debugging functionality is available, this statement has no effect.
     For example, in the below function a debugger statement has been inserted. So
     execution is paused at the debugger statement just like a breakpoint in the script source.

     ```javascript
     function getProfile() {
     // code goes here
     debugger;
     // code goes here
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

164. ### What is the purpose of breakpoints in debugging

     You can set breakpoints in the javascript code once the debugger statement is executed and the debugger window pops up. At each breakpoint, javascript will stop executing, and let you examine the JavaScript values. After examining values, you can resume the execution of code using the play button.

     **[⬆ Back to Top](#table-of-contents)**

165. ### Can I use reserved words as identifiers

     No, you cannot use the reserved words as variables, labels, object or function names. Let's see one simple example,

     ```javascript
     var else = "hello"; // Uncaught SyntaxError: Unexpected token else
     ```

     **[⬆ Back to Top](#table-of-contents)**

166. ### How do you detect a mobile browser

     You can use regex which returns a true or false value depending on whether or not the user is browsing with a mobile.

     ```javascript
     window.mobilecheck = function() {
       var mobileCheck = false;
       (function(a){if(/(android|bb\d+|meego).+mobile|avantgo|bada\/|blackberry|blazer|compal|elaine|fennec|hiptop|iemobile|ip(hone|od)|iris|kindle|lge |maemo|midp|mmp|mobile.+firefox|netfront|opera m(ob|in)i|palm( os)?|phone|p(ixi|re)\/|plucker|pocket|psp|series(4|6)0|symbian|treo|up\.(browser|link)|vodafone|wap|windows ce|xda|xiino/i.test(a)||/1207|6310|6590|3gso|4thp|50[1-6]i|770s|802s|a wa|abac|ac(er|oo|s\-)|ai(ko|rn)|al(av|ca|co)|amoi|an(ex|ny|yw)|aptu|ar(ch|go)|as(te|us)|attw|au(di|\-m|r |s )|avan|be(ck|ll|nq)|bi(lb|rd)|bl(ac|az)|br(e|v)w|bumb|bw\-(n|u)|c55\/|capi|ccwa|cdm\-|cell|chtm|cldc|cmd\-|co(mp|nd)|craw|da(it|ll|ng)|dbte|dc\-s|devi|dica|dmob|do(c|p)o|ds(12|\-d)|el(49|ai)|em(l2|ul)|er(ic|k0)|esl8|ez([4-7]0|os|wa|ze)|fetc|fly(\-|_)|g1 u|g560|gene|gf\-5|g\-mo|go(\.w|od)|gr(ad|un)|haie|hcit|hd\-(m|p|t)|hei\-|hi(pt|ta)|hp( i|ip)|hs\-c|ht(c(\-| |_|a|g|p|s|t)|tp)|hu(aw|tc)|i\-(20|go|ma)|i230|iac( |\-|\/)|ibro|idea|ig01|ikom|im1k|inno|ipaq|iris|ja(t|v)a|jbro|jemu|jigs|kddi|keji|kgt( |\/)|klon|kpt |kwc\-|kyo(c|k)|le(no|xi)|lg( g|\/(k|l|u)|50|54|\-[a-w])|libw|lynx|m1\-w|m3ga|m50\/|ma(te|ui|xo)|mc(01|21|ca)|m\-cr|me(rc|ri)|mi(o8|oa|ts)|mmef|mo(01|02|bi|de|do|t(\-| |o|v)|zz)|mt(50|p1|v )|mwbp|mywa|n10[0-2]|n20[2-3]|n30(0|2)|n50(0|2|5)|n7(0(0|1)|10)|ne((c|m)\-|on|tf|wf|wg|wt)|nok(6|i)|nzph|o2im|op(ti|wv)|oran|owg1|p800|pan(a|d|t)|pdxg|pg(13|\-([1-8]|c))|phil|pire|pl(ay|uc)|pn\-2|po(ck|rt|se)|prox|psio|pt\-g|qa\-a|qc(07|12|21|32|60|\-[2-7]|i\-)|qtek|r380|r600|raks|rim9|ro(ve|zo)|s55\/|sa(ge|ma|mm|ms|ny|va)|sc(01|h\-|oo|p\-)|sdk\/|se(c(\-|0|1)|47|mc|nd|ri)|sgh\-|shar|sie(\-|m)|sk\-0|sl(45|id)|sm(al|ar|b3|it|t5)|so(ft|ny)|sp(01|h\-|v\-|v )|sy(01|mb)|t2(18|50)|t6(00|10|18)|ta(gt|lk)|tcl\-|tdg\-|tel(i|m)|tim\-|t\-mo|to(pl|sh)|ts(70|m\-|m3|m5)|tx\-9|up(\.b|g1|si)|utst|v400|v750|veri|vi(rg|te)|vk(40|5[0-3]|\-v)|vm40|voda|vulc|vx(52|53|60|61|70|80|81|83|85|98)|w3c(\-| )|webc|whit|wi(g |nc|nw)|wmlb|wonu|x700|yas\-|your|zeto|zte\-/i.test(a.substr(0,4))) mobileCheck = true;})(navigator.userAgent||navigator.vendor||window.opera);
       return mobileCheck;
     };
     ```

     **[⬆ Back to Top](#table-of-contents)**

167. ### How do you detect a mobile browser without regexp

     You can detect mobile browsers by simply running through a list of devices and checking if the useragent matches anything. This is an alternative solution for RegExp usage,

     ```javascript
     function detectmob() {
      if( navigator.userAgent.match(/Android/i)
      || navigator.userAgent.match(/webOS/i)
      || navigator.userAgent.match(/iPhone/i)
      || navigator.userAgent.match(/iPad/i)
      || navigator.userAgent.match(/iPod/i)
      || navigator.userAgent.match(/BlackBerry/i)
      || navigator.userAgent.match(/Windows Phone/i)
      ){
         return true;
       }
      else {
         return false;
       }
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

168. ### How do you get the image width and height using JS

     You can programmatically get the image and check the dimensions(width and height) using Javascript.

     ```javascript
     var img = new Image();
     img.onload = function() {
       console.log(this.width + 'x' + this.height);
     }
     img.src = 'http://www.google.com/intl/en_ALL/images/logo.gif';
     ```

     **[⬆ Back to Top](#table-of-contents)**

169. ### How do you make synchronous HTTP request

     Browsers provide an XMLHttpRequest object which can be used to make synchronous HTTP requests from JavaScript

     ```javascript
     function httpGet(theUrl)
     {
         var xmlHttpReq = new XMLHttpRequest();
         xmlHttpReq.open( "GET", theUrl, false ); // false for synchronous request
         xmlHttpReq.send( null );
         return xmlHttpReq.responseText;
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

170. ### How do you make asynchronous HTTP request

     Browsers provide an XMLHttpRequest object which can be used to make asynchronous HTTP requests from JavaScript by passing the 3rd parameter as true.

     ```javascript
     function httpGetAsync(theUrl, callback)
     {
         var xmlHttpReq = new XMLHttpRequest();
         xmlHttpReq.onreadystatechange = function() {
             if (xmlHttpReq.readyState == 4 && xmlHttpReq.status == 200)
                 callback(xmlHttpReq.responseText);
         }
         xmlHttp.open("GET", theUrl, true); // true for asynchronous
         xmlHttp.send(null);
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

171. ### How do you convert date to another timezone in javascript

     You can use the toLocaleString() method to convert dates in one timezone to another. For example, let's convert current date to British English timezone as below,

     ```javascript
     console.log(event.toLocaleString('en-GB', { timeZone: 'UTC' })); //29/06/2019, 09:56:00
     ```

     **[⬆ Back to Top](#table-of-contents)**

172. ### What are the properties used to get size of window

     You can use innerWidth, innerHeight, clientWidth, clientHeight properties of windows, document element and document body objects to find the size of a window. Let's use them combination of these properties to calculate the size of a window or document,

     ```javascript
     var width = window.innerWidth
     || document.documentElement.clientWidth
     || document.body.clientWidth;

     var height = window.innerHeight
     || document.documentElement.clientHeight
     || document.body.clientHeight;
     ```

     **[⬆ Back to Top](#table-of-contents)**

173. ### What is a conditional operator in javascript

     The conditional (ternary) operator is the only JavaScript operator that takes three operands which acts as a shortcut for if statements.

     ```javascript
     var isAuthenticated = false;
     console.log(isAuthenticated ? 'Hello, welcome' : 'Sorry, you are not authenticated'); //Sorry, you are not authenticated
     ```

     **[⬆ Back to Top](#table-of-contents)**

174. ### Can you apply chaining on conditional operator

     Yes, you can apply chaining on conditional operators similar to if … else if … else if … else chain. The syntax is going to be as below,

     ```javascript
     function traceValue(someParam) {
         return condition1 ? value1
              : condition2 ? value2
              : condition3 ? value3
              : value4;
     }

     // The above conditional operator is equivalent to:

     function traceValue(someParam) {
         if (condition1) { return value1; }
         else if (condition2) { return value2; }
         else if (condition3) { return value3; }
         else { return value4; }
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

175. ### What are the ways to execute javascript after page load

     You can execute javascript after page load in many different ways,
     1. **window.onload:**

     ```javascript
     window.onload = function ...
     ```

     1. **document.onload:**

     ```javascript
     document.onload = function ...
     ```

     1. **body onload:**

     ```javascript
     <body onload="script();">
     ```

     **[⬆ Back to Top](#table-of-contents)**

176. ### What is the difference between proto and prototype

     The `__proto__` object is the actual object that is used in the lookup chain to resolve methods, etc. Whereas `prototype` is the object that is used to build `__proto__` when you create an object with new

     ```javascript
     ( new Employee ).__proto__ === Employee.prototype;
     ( new Employee ).prototype === undefined;
     ```

     **[⬆ Back to Top](#table-of-contents)**

177. ### Give an example where do you really need semicolon

     It is recommended to use semicolons after every statement in JavaScript. For example, in the below case it throws an error ".. is not a function" at runtime due to missing semicolon.

     ```javascript
     // define a function
     var fn = function () {
         //...
     } // semicolon missing at this line

     // then execute some code inside a closure
     (function () {
         //...
     })();
     ```

     and it will be interpreted as

     ```javascript
     var fn = function () {
         //...
     }(function () {
         //...
     })();
     ```

     In this case, we are passing the second function as an argument to the first function and then trying to call the result of the first function call as a function. Hence, the second function will fail with a "... is not a function" error at runtime.

     **[⬆ Back to Top](#table-of-contents)**

178. ### What is a freeze method

     The **freeze()** method is used to freeze an object. Freezing an object does not allow adding new properties to an object,prevents from removing and prevents changing the enumerability, configurability, or writability of existing properties. i.e, It returns the passed object and does not create a frozen copy.

     ```javascript
     const obj = {
       prop: 100
     };

     Object.freeze(obj);
     obj.prop = 200; // Throws an error in strict mode

     console.log(obj.prop); //100
     ```

     **Note:** It causes a TypeError if the argument passed is not an object.

     **[⬆ Back to Top](#table-of-contents)**

179. ### What is the purpose of freeze method

     Below are the main benefits of using freeze method,

     1. It is used for freezing objects and arrays.
     2. It is used to make an object immutable.

     **[⬆ Back to Top](#table-of-contents)**

180. ### Why do I need to use freeze method

     In the Object-oriented paradigm, an existing API contains certain elements that are not intended to be extended, modified, or re-used outside of their current context. Hence it works as the `final` keyword which is used in various languages.

     **[⬆ Back to Top](#table-of-contents)**

181. ### How do you detect a browser language preference

     You can use navigator object to detect a browser language preference as below,

     ```javascript
     var language = navigator.languages && navigator.languages[0] || // Chrome / Firefox
                    navigator.language ||   // All browsers
                    navigator.userLanguage; // IE <= 10

     console.log(language);
     ```

     **[⬆ Back to Top](#table-of-contents)**

182. ### How to convert string to title case with javascript

     Title case means that the first letter of each word is capitalized. You can convert a string to title case using the below function,

     ```javascript
         function toTitleCase(str) {
             return str.replace(
                 /\w\S*/g,
                 function(txt) {
                     return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase();
                 }
             );
         }
         toTitleCase("good morning john"); // Good Morning John
     ```

     **[⬆ Back to Top](#table-of-contents)**

183. ### How do you detect javascript disabled in the page

     You can use the `<noscript>` tag to detect javascript disabled or not. The code block inside `<noscript>` gets executed when JavaScript is disabled, and is typically used to display alternative content when the page generated in JavaScript.

     ```javascript
     <script type="javascript">
         // JS related code goes here
     </script>
     <noscript>
         <a href="next_page.html?noJS=true">JavaScript is disabled in the page. Please click Next Page</a>
     </noscript>
     ```

     **[⬆ Back to Top](#table-of-contents)**

184. ### What are various operators supported by javascript

     An operator is capable of manipulating(mathematical and logical computations) a certain value or operand. There are various operators supported by JavaScript as below,
     1. **Arithmetic Operators:** Includes + (Addition),– (Subtraction), * (Multiplication), / (Division), % (Modulus), + + (Increment)  and – – (Decrement)
     2. **Comparison Operators:** Includes = =(Equal),!= (Not Equal), ===(Equal with type), > (Greater than),> = (Greater than or Equal to),< (Less than),<= (Less than or Equal to)
     3. **Logical Operators:** Includes &&(Logical AND),||(Logical OR),!(Logical NOT)
     4. **Assignment Operators:** Includes = (Assignment Operator), += (Add and Assignment Operator), – = (Subtract and Assignment Operator), *= (Multiply and Assignment), /= (Divide and Assignment), %= (Modules and Assignment)
     5. **Ternary Operators:** It includes conditional(: ?) Operator
     6. **typeof Operator:** It uses to find type of variable. The syntax looks like `typeof variable`

     **[⬆ Back to Top](#table-of-contents)**

185. ### What is a rest parameter

     Rest parameter is an improved way to handle function parameters which allows us to represent an indefinite number of arguments as an array. The syntax would be as below,

     ```javascript
     function f(a, b, ...theArgs) {
       // ...
     }
     ```

     For example, let's take a sum example to calculate on dynamic number of parameters,

     ```javascript
     function total(…args){
     let sum = 0;
     for(let i of args){
     sum+=i;
     }
     return sum;
     }
     console.log(fun(1,2)); //3
     console.log(fun(1,2,3)); //6
     console.log(fun(1,2,3,4)); //13
     console.log(fun(1,2,3,4,5)); //15
     ```

     **Note:** Rest parameter is added in ES2015 or ES6

     **[⬆ Back to Top](#table-of-contents)**

186. ### What happens if you do not use rest parameter as a last argument

     The rest parameter should be the last argument, as its job is to collect all the remaining arguments into an array. For example, if you define a function like below it doesn’t make any sense and will throw an error.

     ```javascript
     function someFunc(a,…b,c){
     //You code goes here
     return;
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

187. ### What are the bitwise operators available in javascript

     Below are the list of bitwise logical operators used in JavaScript
     1. Bitwise AND ( & )
     2. Bitwise OR ( | )
     3. Bitwise XOR ( ^ )
     4. Bitwise NOT ( ~ )
     5. Left Shift ( << )
     6. Sign Propagating Right Shift ( >> )
     7. Zero fill Right Shift ( >>> )

     **[⬆ Back to Top](#table-of-contents)**

188. ### What is a spread operator

     Spread operator allows iterables( arrays / objects / strings ) to be expanded into single arguments/elements. Let's take an example to see this behavior,

     ```javascript
     function calculateSum(x, y, z) {
       return x + y + z;
     }

     const numbers = [1, 2, 3];

     console.log(calculateSum(...numbers)); // 6
     ```

     **[⬆ Back to Top](#table-of-contents)**

189. ### How do you determine whether object is frozen or not

     Object.isFrozen() method is used to determine if an object is frozen or not.An object is frozen if all of the below conditions hold true,
     1. If it is not extensible.
     2. If all of its properties are non-configurable.
     3. If all its data properties are non-writable.
     The usage is going to be as follows,

     ```javascript
     const object = {
        property: 'Welcome JS world'
     };
     Object.freeze(object);
     console.log(Object.isFrozen(object));
     ```

     **[⬆ Back to Top](#table-of-contents)**

190. ### How do you determine two values same or not using object

     The Object.is() method determines whether two values are the same value. For example, the usage with different types of values would be,

     ```javascript
     Object.is('hello', 'hello');     // true
     Object.is(window, window);   // true
     Object.is([], []) // false
     ```

     Two values are the same if one of the following holds:
     1. both undefined
     2. both null
     3. both true or both false
     4. both strings of the same length with the same characters in the same order
     5. both the same object (means both object have same reference)
     6. both numbers and
        both +0
        both -0
        both NaN
        both non-zero and both not NaN and both have the same value.

     **[⬆ Back to Top](#table-of-contents)**

191. ### What is the purpose of using object is method

     Some of the applications of Object's `is` method are follows,
     1. It is used for comparison of two strings.
     2. It is used for comparison of two numbers.
     3. It is used for comparing the polarity of two numbers.
     4. It is used for comparison of two objects.

     **[⬆ Back to Top](#table-of-contents)**

192. ### How do you copy properties from one object to other

     You can use the Object.assign() method which is used to copy the values and properties from one or more source objects to a target object.  It returns the target object which has properties and values copied from the target object. The syntax would be as below,

     ```javascript
     Object.assign(target, ...sources)
     ```

     Let's take example with one source and one target object,

     ```javascript
     const target = { a: 1, b: 2 };
     const source = { b: 3, c: 4 };

     const returnedTarget = Object.assign(target, source);

     console.log(target); // { a: 1, b: 3, c: 4 }

     console.log(returnedTarget); // { a: 1, b: 3, c: 4 }
     ```

     As observed in the above code, there is a common property(`b`) from source to target so it's value has been overwritten.

     **[⬆ Back to Top](#table-of-contents)**

193. ### What are the applications of assign method

     Below are the some of main applications of Object.assign() method,

     1. It is used for cloning an object.
     2. It is used to merge objects with the same properties.

     **[⬆ Back to Top](#table-of-contents)**

194. ### What is a proxy object

     The Proxy object is used to define custom behavior for fundamental operations such as property lookup, assignment, enumeration, function invocation, etc. The syntax would be as follows,

     ```javascript
     var p = new Proxy(target, handler);
     ```

     Let's take an example of proxy object,

     ```javascript
     var handler = {
         get: function(obj, prop) {
             return prop in obj ?
                 obj[prop] :
                 100;
         }
     };

     var p = new Proxy({}, handler);
     p.a = 10;
     p.b = null;

     console.log(p.a, p.b); // 10, null
     console.log('c' in p, p.c); // false, 100
     ```

     In the above code, it uses `get` handler which define the behavior of the proxy when an operation is performed on it

     **[⬆ Back to Top](#table-of-contents)**

195. ### What is the purpose of seal method

     The **Object.seal()** method is used to seal an object, by preventing new properties from being added to it and marking all existing properties as non-configurable. But values of present properties can still be changed as long as they are writable. Let's see the below example to understand more about seal() method

     ```javascript
      const object = {
         property: 'Welcome JS world'
      };
      Object.seal(object);
      object.property = 'Welcome to object world';
      console.log(Object.isSealed(object)); // true
      delete object.property; // You cannot delete when sealed
      console.log(object.property); //Welcome to object world
     ```

     **[⬆ Back to Top](#table-of-contents)**

196. ### What are the applications of seal method

     Below are the main applications of Object.seal() method,
     1. It is used for sealing objects and arrays.
     2. It is used to make an object immutable.

     **[⬆ Back to Top](#table-of-contents)**

197. ### What are the differences between freeze and seal methods

     If an object is frozen using the Object.freeze() method then its properties become immutable and no changes can be made in them whereas if an object is sealed using the Object.seal() method then the changes can be made in the existing properties of the object.

     **[⬆ Back to Top](#table-of-contents)**

198. ### How do you determine if an object is sealed or not

     The Object.isSealed() method is used to determine if an object is sealed or not. An object is sealed if all of the below conditions hold true
     1. If it is not extensible.
     2. If all of its properties are non-configurable.
     3. If it is not removable (but not necessarily non-writable).
     Let's see it in the action

     ```javascript
     const object = {
     property: 'Hello, Good morning'
     };

     Object.seal(object); // Using seal() method to seal the object

     console.log(Object.isSealed(object));      // checking whether the object is sealed or not
     ```

     **[⬆ Back to Top](#table-of-contents)**

199. ### How do you get enumerable key and value pairs

     The Object.entries() method is used to return an array of a given object's own enumerable string-keyed property [key, value] pairs, in the same order as that provided by a for...in loop. Let's see the functionality of object.entries() method in an example,

     ```javascript
     const object = {
       a: 'Good morning',
       b: 100
     };

     for (let [key, value] of Object.entries(object)) {
       console.log(`${key}: ${value}`); // a: 'Good morning'
                                        // b: 100
     }
     ```

     **Note:** The order is not guaranteed as object defined.

     **[⬆ Back to Top](#table-of-contents)**

200. ### What is the main difference between Object.values and Object.entries method

     The Object.values() method's behavior is similar to Object.entries() method but it returns an array of values instead [key,value] pairs.

     ```javascript
      const object = {
        a: 'Good morning',
        b: 100
      };

      for (let value of Object.values(object)) {
        console.log(`${value}`); // 'Good morning'
                                     100
      }
     ```

     **[⬆ Back to Top](#table-of-contents)**

201. ### How can you get the list of keys of any object

     You can use the `Object.keys()` method which is used to return an array of a given object's own property names, in the same order as we get with a normal loop. For example, you can get the keys of a user object,

     ```javascript
     const user = {
       name: 'John',
       gender: 'male',
       age: 40
     };

     console.log(Object.keys(user)); //['name', 'gender', 'age']
     ```

     **[⬆ Back to Top](#table-of-contents)**

202. ### How do you create an object with prototype

     The Object.create() method is used to create a new object with the specified prototype object and properties. i.e, It uses an existing object as the prototype of the newly created object. It returns a new object with the specified prototype object and properties.

     ```javascript
      const user = {
        name: 'John',
        printInfo: function () {
          console.log(`My name is ${this.name}.`);
        }
      };

      const admin = Object.create(user);

      admin.name = "Nick"; // Remember that "name" is a property set on "admin" but not on "user" object

      admin.printInfo(); // My name is Nick
     ```

     **[⬆ Back to Top](#table-of-contents)**

203. ### What is a WeakSet

     WeakSet is used to store a collection of weakly(weak references) held objects. The syntax would be as follows,

     ```javascript
     new WeakSet([iterable]);
     ```

     Let's see the below example to explain it's behavior,

     ```javascript
     var ws = new WeakSet();
     var user = {};
     ws.add(user);
     ws.has(user);    // true
     ws.delete(user); // removes user from the set
     ws.has(user);    // false, user has been removed
     ```

     **[⬆ Back to Top](#table-of-contents)**

204. ### What are the differences between WeakSet and Set

     The main difference is that references to objects in Set are strong while references to objects in WeakSet are weak. i.e, An object in WeakSet can be garbage collected if there is no other reference to it.
     Other differences are,
     1. Sets can store any value Whereas WeakSets can store only collections of objects
     2. WeakSet does not have size property unlike Set
     3. WeakSet does not have methods such as clear, keys, values, entries, forEach.
     4. WeakSet is not iterable.

     **[⬆ Back to Top](#table-of-contents)**

205. ### List down the collection of methods available on WeakSet

     Below are the list of methods available on WeakSet,
     1. add(value): A new object is appended with the given value to the weakset
     2. delete(value): Deletes the value from the WeakSet collection.
     3. has(value): It returns true if the value is present in the WeakSet Collection, otherwise it returns false.
     4. length(): It returns the length of weakSetObject
     Let's see the functionality of all the above methods in an example,

     ```javascript
     var weakSetObject = new WeakSet();
     var firstObject = {};
     var secondObject = {};
     // add(value)
     weakSetObject.add(firstObject);
     weakSetObject.add(secondObject);
     console.log(weakSetObject.has(firstObject)); //true
     console.log(weakSetObject.length()); //2
     weakSetObject.delete(secondObject);
     ```

     **[⬆ Back to Top](#table-of-contents)**

206. ### What is a WeakMap

     The WeakMap object is a collection of key/value pairs in which the keys are weakly referenced. In this case, keys must be objects and the values can be arbitrary values. The syntax is looking like as below,

     ```javascript
     new WeakMap([iterable])
     ```

     Let's see the below example to explain it's behavior,

     ```javascript
      var ws = new WeakMap();
      var user = {};
      ws.set(user);
      ws.has(user);    // true
      ws.delete(user); // removes user from the map
      ws.has(user);    // false, user has been removed
     ```

     **[⬆ Back to Top](#table-of-contents)**

207. ### What are the differences between WeakMap and Map

     The main difference is that references to key objects in Map are strong while references to key objects in WeakMap are weak. i.e, A key object in WeakMap can be garbage collected if there is no other reference to it.
     Other differences are,
     1. Maps can store any key type Whereas WeakMaps can store only collections of key objects
     2. WeakMap does not have size property unlike Map
     3. WeakMap does not have methods such as clear, keys, values, entries, forEach.
     4. WeakMap is not iterable.

     **[⬆ Back to Top](#table-of-contents)**

208. ### List down the collection of methods available on WeakMap

     Below are the list of methods available on WeakMap,
     1. set(key, value): Sets the value for the key in the WeakMap object. Returns the WeakMap object.
     2. delete(key): Removes any value associated to the key.
     3. has(key): Returns a Boolean asserting whether a value has been associated to the key in the WeakMap object or not.
     4. get(key): Returns the value associated to the key, or undefined if there is none.
     Let's see the functionality of all the above methods in an example,

     ```javascript
     var weakMapObject = new WeakMap();
     var firstObject = {};
     var secondObject = {};
     // set(key, value)
     weakMapObject.set(firstObject, 'John');
     weakMapObject.set(secondObject, 100);
     console.log(weakMapObject.has(firstObject)); //true
     console.log(weakMapObject.get(firstObject)); // John
     weakMapObject.delete(secondObject);
     ```

     **[⬆ Back to Top](#table-of-contents)**

209. ### What is the purpose of uneval

     The uneval() is an inbuilt function which is used to create a string representation of the source code of an Object. It is a top-level function and is not associated with any object. Let's see the below example to know more about it's functionality,

     ```javascript
     var a = 1;
     uneval(a); // returns a String containing 1
     uneval(function user() {}); // returns "(function user(){})"
     ```

     **[⬆ Back to Top](#table-of-contents)**

210. ### How do you encode an URL

     The encodeURI() function is used to encode complete URI which has special characters except (, / ? : @ & = + $ #) characters.

     ```javascript
     var uri = 'https://mozilla.org/?x=шеллы';
     var encoded = encodeURI(uri);
     console.log(encoded); // https://mozilla.org/?x=%D1%88%D0%B5%D0%BB%D0%BB%D1%8B
     ```

     **[⬆ Back to Top](#table-of-contents)**

211. ### How do you decode an URL

     The decodeURI() function is used to decode a Uniform Resource Identifier (URI) previously created by encodeURI().

     ```javascript
      var uri = 'https://mozilla.org/?x=шеллы';
      var encoded = encodeURI(uri);
      console.log(encoded); // https://mozilla.org/?x=%D1%88%D0%B5%D0%BB%D0%BB%D1%8B
     try {
       console.log(decodeURI(encoded)); // "https://mozilla.org/?x=шеллы"
     } catch(e) { // catches a malformed URI
       console.error(e);
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

212. ### How do you print the contents of web page

     The window object provided a print() method which is used to print the contents of the current window. It opens a Print dialog box which lets you choose between various printing options. Let's see the usage of print method in an example,

     ```html
        <input type="button" value="Print" onclick="window.print()" />
     ```

     **Note:** In most browsers, it will block while the print dialog is open.

     **[⬆ Back to Top](#table-of-contents)**

213. ### What is the difference between uneval and eval

     The `uneval` function returns the source of a given object; whereas the `eval` function does the opposite, by evaluating that source code in a different memory area. Let's see an example to clarify the difference,

     ```javascript
     var msg = uneval(function greeting() { return 'Hello, Good morning'; });
     var greeting = eval(msg);
     greeting(); // returns "Hello, Good morning"
     ```

     **[⬆ Back to Top](#table-of-contents)**

214. ### What is an anonymous function

     An anonymous function is a function without a name! Anonymous functions are commonly assigned to a variable name or used as a callback function. The syntax would be as below,

     ```javascript
     function (optionalParameters) {
       //do something
     }

     const myFunction = function(){ //Anonymous function assigned to a variable
       //do something
     };

     [1, 2, 3].map(function(element){ //Anonymous function used as a callback function
       //do something
     });
     ```

     Let's see the above anonymous function in an example,

     ```javascript
     var x = function (a, b) {return a * b};
     var z = x(5, 10);
     console.log(z); // 50
     ```

     **[⬆ Back to Top](#table-of-contents)**

215. ### What is the precedence order between local and global variables

     A local variable takes precedence over a global variable with the same name. Let's see this behavior in an example.

     ```javascript
     var msg = "Good morning";
     function greeting() {
        msg = "Good Evening";
        console.log(msg);
     }
     greeting();
     ```

     **[⬆ Back to Top](#table-of-contents)**

216. ### What are javascript accessors

     ECMAScript 5 introduced javascript object accessors or computed properties through getters and setters. Getters uses the `get` keyword whereas Setters uses the `set` keyword.

     ```javascript
     var user = {
       firstName: "John",
       lastName : "Abraham",
       language : "en",
       get lang() {
         return this.language;
       }
       set lang(lang) {
       this.language = lang;
       }
     };
     console.log(user.lang); // getter access lang as en
     user.lang = 'fr';
     console.log(user.lang); // setter used to set lang as fr
     ```

     **[⬆ Back to Top](#table-of-contents)**

217. ### How do you define property on Object constructor

     The Object.defineProperty() static method is used to define a new property directly on an object, or modify an existing property on an object, and returns the object. Let's see an example to know how to define property,

     ```javascript
     const newObject = {};

     Object.defineProperty(newObject, 'newProperty', {
       value: 100,
       writable: false
     });

     console.log(newObject.newProperty); // 100

     newObject.newProperty = 200; // It throws an error in strict mode due to writable setting

     ```

     **[⬆ Back to Top](#table-of-contents)**

218. ### What is the difference between get and defineProperty

     Both have similar results until unless you use classes. If you use `get` the property will be defined on the prototype of the object whereas using `Object.defineProperty()` the property will be defined on the instance it is applied to.

     **[⬆ Back to Top](#table-of-contents)**

219. ### What are the advantages of Getters and Setters

     Below are the list of benefits of Getters and Setters,
     1. They provide simpler syntax
     2. They are used for defining computed properties, or accessors in JS.
     3. Useful to provide equivalence relation between properties and methods
     4. They can provide better data quality
     5. Useful for doing things behind the scenes with the encapsulated logic.

     **[⬆ Back to Top](#table-of-contents)**

220. ### Can I add getters and setters using defineProperty method

     Yes, You can use the `Object.defineProperty()` method to add Getters and Setters. For example, the below counter object uses increment, decrement, add and subtract properties,

     ```javascript
     var obj = {counter : 0};

     // Define getters
     Object.defineProperty(obj, "increment", {
       get : function () {this.counter++;}
     });
     Object.defineProperty(obj, "decrement", {
       get : function () {this.counter--;}
     });

     // Define setters
     Object.defineProperty(obj, "add", {
       set : function (value) {this.counter += value;}
     });
     Object.defineProperty(obj, "subtract", {
       set : function (value) {this.counter -= value;}
     });

     obj.add = 10;
     obj.subtract = 5;
     console.log(obj.increment); //6
     console.log(obj.decrement); //5
     ```

     **[⬆ Back to Top](#table-of-contents)**

221. ### What is the purpose of switch-case

     The switch case statement in JavaScript is used for decision making purposes. In a few cases, using the switch case statement is going to be more convenient than if-else statements. The syntax would be as below,

     ```javascript
     switch (expression)
     {
         case value1:
             statement1;
             break;
         case value2:
             statement2;
             break;
         .
         .
         case valueN:
             statementN;
             break;
         default:
             statementDefault;
     }
     ```

     The above multi-way branch statement provides an easy way to dispatch execution to different parts of code based on the value of the expression.

     **[⬆ Back to Top](#table-of-contents)**

222. ### What are the conventions to be followed for the usage of switch case

     Below are the list of conventions should be taken care,
     1. The expression can be of type either number or string.
     2. Duplicate values are not allowed for the expression.
     3. The default statement is optional. If the expression passed to switch does not match with any case value then the statement within default case will be executed.
     4. The break statement is used inside the switch to terminate a statement sequence.
     5. The break statement is optional. But if it is omitted, the execution will continue on into the next case.

     **[⬆ Back to Top](#table-of-contents)**

223. ### What are primitive data types

     A primitive data type is data that has a primitive value (which has no properties or methods). There are 7 types of primitive data types.
     
     1. string
     2. number
     3. boolean
     4. null
     5. undefined
     6. bigint
     7. symbol

     **[⬆ Back to Top](#table-of-contents)**

224. ### What are the different ways to access object properties

     There are 3 possible ways for accessing the property of an object.
     1. **Dot notation:** It uses dot for accessing the properties

     ```javascript
     objectName.property
     ```

     1. **Square brackets notation:** It uses square brackets for property access

     ```javascript
     objectName["property"]
     ```

     1. **Expression notation:** It uses expression in the square brackets

     ```javascript
     objectName[expression]
     ```

     **[⬆ Back to Top](#table-of-contents)**

225. ### What are the function parameter rules

     JavaScript functions follow below rules for parameters,
     1. The function definitions do not specify data types for parameters.
     2. Do not perform type checking on the passed arguments.
     3. Do not check the number of arguments received.
     i.e, The below function follows the above rules,

     ```javascript
     function functionName(parameter1, parameter2, parameter3) {
       console.log(parameter1); // 1
     }
     functionName(1);
     ```

     **[⬆ Back to Top](#table-of-contents)**

226. ### What is an error object

     An error object is a built in error object that provides error information when an error occurs. It has two properties: name and message. For example, the below function logs error details,

     ```javascript
     try {
       greeting("Welcome");
     }
     catch(err) {
       console.log(err.name + "<br>" + err.message);
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

227. ### When you get a syntax error

     A SyntaxError is thrown if you try to evaluate code with a syntax error. For example, the below missing quote for the function parameter throws a syntax error

     ```javascript
     try {
       eval("greeting('welcome)");   // Missing ' will produce an error
     }
     catch(err) {
       console.log(err.name);
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

228. ### What are the different error names from error object

     There are 6 different types of error names returned from error object,
     | Error Name | Description |
     |---- | ---------
     | EvalError  | An error has occurred in the eval() function |
     | RangeError | An error has occurred with a number "out of range"  |
     | ReferenceError | An error due to an illegal reference|
     | SyntaxError | An error due to a syntax error|
     | TypeError | An error due to a type error |
     | URIError | An error due to encodeURI() |

     **[⬆ Back to Top](#table-of-contents)**

229. ### What are the various statements in error handling

     Below are the list of statements used in an error handling,
     1. **try:** This statement is used to test a block of code for errors
     2. **catch:** This statement is used to handle the error
     3. **throw:** This statement is used to create custom errors.
     4. **finally:** This statement is used to execute code after try and catch regardless of the result.

     **[⬆ Back to Top](#table-of-contents)**

230. ### What are the two types of loops in javascript

     1. **Entry Controlled loops:** In this kind of loop type, the test condition is tested before entering the loop body. For example, For Loop and While Loop comes under this category.
     2. **Exit Controlled Loops:** In this kind of loop type, the test condition is tested or evaluated at the end of the loop body. i.e, the loop body will execute at least once irrespective of test condition true or false. For example, do-while loop comes under this category.

     **[⬆ Back to Top](#table-of-contents)**

231. ### What is nodejs

     Node.js is a server-side platform built on Chrome's JavaScript runtime for easily building fast and scalable network applications. It is an event-based, non-blocking, asynchronous I/O runtime that uses Google's V8 JavaScript engine and libuv library.

     **[⬆ Back to Top](#table-of-contents)**

232. ### What is an Intl object

     The Intl object is the namespace for the ECMAScript Internationalization API, which provides language sensitive string comparison, number formatting, and date and time formatting. It provides access to several constructors and language sensitive functions.

     **[⬆ Back to Top](#table-of-contents)**

233. ### How do you perform language specific date and time formatting

     You can use the `Intl.DateTimeFormat` object which is a constructor for objects that enable language-sensitive date and time formatting. Let's see this behavior with an example,

     ```javascript
     var date = new Date(Date.UTC(2019, 07, 07, 3, 0, 0));
     console.log(new Intl.DateTimeFormat('en-GB').format(date)); // 07/08/2019
     console.log(new Intl.DateTimeFormat('en-AU').format(date)); // 07/08/2019
     ```

     **[⬆ Back to Top](#table-of-contents)**

234. ### What is an Iterator

     An iterator is an object which defines a sequence and a return value upon its termination. It implements the Iterator protocol with a `next()` method which returns an object with two properties: `value` (the next value in the sequence) and `done` (which is true if the last value in the sequence has been consumed).

     **[⬆ Back to Top](#table-of-contents)**

235. ### How does synchronous iteration works

     Synchronous iteration was introduced in ES6 and it works with below set of components,

     **Iterable:** It is an object which can be iterated over via a method whose key is Symbol.iterator.
     **Iterator:** It is an object returned by invoking `[Symbol.iterator]()` on an iterable. This iterator object wraps each iterated element in an object and returns it via `next()` method one by one.
     **IteratorResult:** It is an object returned by `next()` method. The object contains two properties; the `value` property contains an iterated element and the `done` property  determines whether the element is the last element or not.

     Let's demonstrate synchronous iteration with an array as below,

     ```javascript
     const iterable = ['one', 'two', 'three'];
     const iterator = iterable[Symbol.iterator]();
     console.log(iterator.next());  // { value: 'one', done: false }
     console.log(iterator.next());  // { value: 'two', done: false }
     console.log(iterator.next());  // { value: 'three', done: false }
     console.log(iterator.next());  // { value: 'undefined, done: true }
     ```

     **[⬆ Back to Top](#table-of-contents)**

236. ### What is an event loop

     The Event Loop is a queue of callback functions. When an async function executes, the callback function is pushed into the queue. The JavaScript engine doesn't start processing the event loop until the async function has finished executing the code.
     **Note:** It allows Node.js to perform non-blocking I/O operations even though JavaScript is single-threaded.

     **[⬆ Back to Top](#table-of-contents)**

237. ### What is call stack

     Call Stack is a data structure for javascript interpreters to keep track of function calls in the program. It has two major actions,
     1. Whenever you call a function for its execution, you are pushing it to the stack.
     2. Whenever the execution is completed, the function is popped out of the stack.

     Let's take an example and it's state representation in a diagram format

     ```javascript
     function hungry() {
        eatFruits();
     }
     function eatFruits() {
        return "I'm eating fruits";
     }

     // Invoke the `hungry` function
     hungry();
     ```

     The above code  processed in a call stack as  below,
     1. Add the `hungry()` function to the call stack list and execute the code.
     2. Add the `eatFruits()` function to the call stack list and execute the code.
     3. Delete the `eatFruits()` function from our call stack list.
     4. Delete the `hungry()` function from the call stack list since there are no items anymore.

     ![Screenshot](images/call-stack.png)

     **[⬆ Back to Top](#table-of-contents)**

238. ### What is an event queue

     **[⬆ Back to Top](#table-of-contents)**

239. ### What is a decorator

     A decorator is an expression that evaluates to a function and that takes the target, name, and decorator descriptor as arguments. Also, it optionally returns a decorator descriptor to install on the target object. Let's define admin decorator for user class at design time,

     ```javascript
     function admin(isAdmin) {
        return function(target) {
            target.isAdmin = isAdmin;
        }
     }

     @admin(true)
     class User() {
     }
     console.log(User.isAdmin); //true

      @admin(false)
      class User() {
      }
      console.log(User.isAdmin); //false
     ```

     **[⬆ Back to Top](#table-of-contents)**

240. ### What are the properties of Intl object

     Below are the list of properties available on Intl object,
     1. **Collator:** These are the objects that enable language-sensitive string comparison.
     2. **DateTimeFormat:** These are the objects that enable language-sensitive date and time formatting.
     3. **ListFormat:** These are the objects that enable language-sensitive list formatting.
     4. **NumberFormat:** Objects that enable language-sensitive number formatting.
     5. **PluralRules:** Objects that enable plural-sensitive formatting and language-specific rules for plurals.
     6. **RelativeTimeFormat:** Objects that enable language-sensitive relative time formatting.

     **[⬆ Back to Top](#table-of-contents)**

241. ### What is an Unary operator

     The unary(+) operator is used to convert a variable to a number.If the variable cannot be converted, it will still become a number but with the value NaN. Let's see this behavior in an action.

     ```javascript
     var x = "100";
     var y = + x;
     console.log(typeof x, typeof y); // string, number

     var a = "Hello";
     var b = + a;
     console.log(typeof a, typeof b, b); // string, number, NaN
     ```

     **[⬆ Back to Top](#table-of-contents)**

242. ### How do you sort elements in an array

     The sort() method is used to sort the elements of an array in place and returns the sorted array. The example usage would be as below,

     ```javascript
     var months = ["Aug", "Sep", "Jan", "June"];
     months.sort();
     console.log(months); //  ["Aug", "Jan", "June", "Sep"]
     ```

     **[⬆ Back to Top](#table-of-contents)**

243. ### What is the purpose of compareFunction while sorting arrays

     The compareFunction is used to define the sort order. If omitted, the array elements are converted to strings, then sorted according to each character's Unicode code point value. Let's take an example to see the usage of compareFunction,

     ```javascript
     let numbers = [1, 2, 5, 3, 4];
     numbers.sort((a, b) => b - a);
     console.log(numbers); // [5, 4, 3, 2, 1]
     ```

     **[⬆ Back to Top](#table-of-contents)**

244. ### How do you reversing an array

     You can use the reverse() method to reverse the elements in an array. This method is useful to sort an array in descending order. Let's see the usage of reverse() method in an example,

     ```javascript
     let numbers = [1, 2, 5, 3, 4];
     numbers.sort((a, b) => b - a);
     numbers.reverse();
     console.log(numbers); // [1, 2, 3, 4 ,5]
     ```

     **[⬆ Back to Top](#table-of-contents)**

245. ### How do you find min and max value in an array

     You can use `Math.min` and `Math.max` methods on array variables to find the minimum and maximum elements within an array. Let's create two functions to find the min and max value with in an array,

     ```javascript
     var marks = [50, 20, 70, 60, 45, 30];
     function findMin(arr) {
       return Math.min.apply(null, arr);
     }
     function findMax(arr) {
       return Math.max.apply(null, arr);
     }

     console.log(findMin(marks));
     console.log(findMax(marks));
     ```

     **[⬆ Back to Top](#table-of-contents)**

246. ### How do you find min and max values without Math functions

     You can write functions which loop through an array comparing each value with the lowest value or highest value to find the min and max values. Let's create those functions to find min and max values,

     ```javascript
      var marks = [50, 20, 70, 60, 45, 30];
      function findMin(arr) {
        var length = arr.length
        var min = Infinity;
        while (length--) {
          if (arr[length] < min) {
            min = arr[len];
          }
        }
        return min;
      }

      function findMax(arr) {
        var length = arr.length
        var max = -Infinity;
        while (len--) {
          if (arr[length] > max) {
            max = arr[length];
          }
        }
        return max;
      }

      console.log(findMin(marks));
      console.log(findMax(marks));
     ```

     **[⬆ Back to Top](#table-of-contents)**

247. ### What is an empty statement and purpose of it

     The empty statement is a semicolon (;) indicating that no statement will be executed, even if JavaScript syntax requires one. Since there is no action with an empty statement you might think that it's usage is quite less, but the empty statement is occasionally useful when you want to create a loop that has an empty body. For example, you can initialize an array with zero values as below,

     ```javascript
     // Initialize an array a
     for(int i=0; i < a.length; a[i++] = 0) ;
     ```

     **[⬆ Back to Top](#table-of-contents)**

248. ### How do you get metadata of a module

     You can use the `import.meta` object which is a meta-property exposing context-specific meta data to a JavaScript module. It contains information about the current module, such as the module's URL. In browsers, you might get different meta data than NodeJS.

     ```javascript
     <script type="module" src="welcome-module.js"></script>
     console.log(import.meta); // { url: "file:///home/user/welcome-module.js" }
     ```

     **[⬆ Back to Top](#table-of-contents)**

249. ### What is a comma operator

     The comma operator is used to evaluate each of its operands from left to right and returns the value of the last operand. This is totally different from comma usage within arrays, objects, and function arguments and parameters. For example, the usage for numeric expressions would be as below,

     ```javascript
     var x = 1;
     x = (x++, x);

     console.log(x); // 2
     ```

     **[⬆ Back to Top](#table-of-contents)**

250. ### What is the advantage of a comma operator

     It is normally used to include multiple expressions in a location that requires a single expression. One of the common usages of this comma operator is to supply multiple parameters in a `for` loop. For example, the below for loop uses multiple expressions in a single location using comma operator,

     ```javascript
     for (var a = 0, b =10; a <= 10; a++, b--)
     ```

     You can also use the comma operator in a return statement where it processes before returning.

     ```javascript
     function myFunction() {
        var a = 1;
        return (a += 10, a); // 11
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

251. ### What is typescript

      TypeScript is a typed superset of JavaScript created by Microsoft that adds optional types, classes, async/await, and many other features, and compiles to plain JavaScript. Angular built entirely in TypeScript and used as a primary language. You can install it globally as

      ```bash
      npm install -g typescript
      ```

      Let's see a simple example of TypeScript usage,

      ```typescript
      function greeting(name: string): string {
         return "Hello, " + name;
      }

      let user = "Sudheer";

      console.log(greeting(user));
      ```

      The greeting method allows only string type as argument.

      **[⬆ Back to Top](#table-of-contents)**

252. ### What are the differences between javascript and typescript

     Below are the list of differences between javascript and typescript,

     | feature | typescript | javascript |
     |---- | --------- | ----
     | Language paradigm  | Object oriented programming language  | Scripting language |
     | Typing support | Supports static typing  | It has dynamic typing |
     | Modules | Supported | Not supported |
     | Interface | It has interfaces concept | Doesn't support interfaces |
     | Optional parameters | Functions support optional parameters | No support of optional parameters for functions |

     **[⬆ Back to Top](#table-of-contents)**

253. ### What are the advantages of typescript over javascript

     Below are some of the advantages of typescript over javascript,
     1. TypeScript is able to find compile time errors at the development time only and it makes sures less runtime errors. Whereas javascript is an interpreted language.
     2. TypeScript is strongly-typed or supports static typing which allows for checking type correctness at compile time. This is not available in javascript.
     3. TypeScript compiler can compile the .ts files into ES3,ES4 and ES5 unlike ES6 features of javascript which may not be supported in some browsers.

     **[⬆ Back to Top](#table-of-contents)**

254. ### What is an object initializer

     An object initializer is an expression that describes the initialization of an Object. The syntax for this expression is represented as a comma-delimited list of zero or more pairs of property names and associated values of an object, enclosed in curly braces ({}). This is also known as literal notation. It is one of the ways to create an object.

     ```javascript
     var initObject = {a: 'John', b: 50, c: {}};

     console.log(initObject.a); // John
     ```

     **[⬆ Back to Top](#table-of-contents)**

255. ### What is a constructor method

     The constructor method is a special method for creating and initializing an object created within a class. If you do not specify a constructor method, a default constructor is used. The example usage of constructor would be as below,

     ```javascript
     class Employee {
       constructor() {
         this.name = "John";
       }
     }

     var employeeObject = new Employee();

     console.log(employeeObject.name); // John
     ```

     **[⬆ Back to Top](#table-of-contents)**

256. ### What happens if you write constructor more than once in a class

     The "constructor" in a class is a special method and it should be defined only once in a class. i.e, If you write a constructor method more than once in a class it will throw a `SyntaxError` error.

     ```javascript
      class Employee {
        constructor() {
          this.name = "John";
        }
        constructor() {   //  Uncaught SyntaxError: A class may only have one constructor
          this.age = 30;
        }
      }

      var employeeObject = new Employee();

      console.log(employeeObject.name);
     ```

     **[⬆ Back to Top](#table-of-contents)**

257. ### How do you call the constructor of a parent class

     You can use the `super` keyword to call the constructor of a parent class. Remember that `super()` must be called before using 'this' reference. Otherwise it will cause a reference error. Let's the usage of it,

     ```javascript
     class Square extends Rectangle {
       constructor(length) {
         super(length, length);
         this.name = 'Square';
       }

       get area() {
         return this.width * this.height;
       }

       set area(value) {
         this.area = value;
       }
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

258. ### How do you get the prototype of an object

     You can use the `Object.getPrototypeOf(obj)` method to return the prototype of the specified object. i.e. The value of the internal `prototype` property. If there are no inherited properties then `null` value is returned.

     ```javascript
     const newPrototype = {};
     const newObject = Object.create(newPrototype);

     console.log(Object.getPrototypeOf(newObject) === newPrototype); // true
     ```

     **[⬆ Back to Top](#table-of-contents)**

259. ### What happens If I pass string type for getPrototype method

     In ES5, it will throw a TypeError exception if the obj parameter isn't an object. Whereas in ES2015, the parameter will be coerced to an `Object`.

     ```javascript
     // ES5
     Object.getPrototypeOf('James'); // TypeError: "James" is not an object
     // ES2015
     Object.getPrototypeOf('James'); // String.prototype
     ```

     **[⬆ Back to Top](#table-of-contents)**

260. ### How do you set prototype of one object to another

     You can use the `Object.setPrototypeOf()` method that sets the prototype (i.e., the internal `Prototype` property) of a specified object to another object or null. For example, if you want to set prototype of a square object to rectangle object would be as follows,

     ```javascript
     Object.setPrototypeOf(Square.prototype, Rectangle.prototype);
     Object.setPrototypeOf({}, null);
     ```

     **[⬆ Back to Top](#table-of-contents)**

261. ### How do you check whether an object can be extendable or not

     The `Object.isExtensible()` method is used to determine if an object is extendable or not. i.e, Whether it can have new properties added to it or not.

     ```javascript
     const newObject = {};
     console.log(Object.isExtensible(newObject)); //true
     ```

     **Note:** By default, all the objects are extendable. i.e, The new properties can be added or modified.

     **[⬆ Back to Top](#table-of-contents)**

262. ### How do you prevent an object to extend

     The `Object.preventExtensions()` method is used to prevent new properties from ever being added to an object. In other words, it prevents future extensions to the object. Let's see the usage of this property,

     ```javascript
     const newObject = {};
     Object.preventExtensions(newObject); // NOT extendable

     try {
       Object.defineProperty(newObject, 'newProperty', { // Adding new property
         value: 100
       });
     } catch (e) {
       console.log(e); // TypeError: Cannot define property newProperty, object is not extensible
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

263. ### What are the different ways to make an object non-extensible

     You can mark an object non-extensible in 3 ways,
     1. Object.preventExtensions
     2. Object.seal
     3. Object.freeze

     ```javascript
     var newObject = {};

     Object.preventExtensions(newObject); // Prevent objects are non-extensible
     Object.isExtensible(newObject); // false

     var sealedObject = Object.seal({}); // Sealed objects are non-extensible
     Object.isExtensible(sealedObject); // false

     var frozenObject = Object.freeze({}); // Frozen objects are non-extensible
     Object.isExtensible(frozenObject); // false
     ```

     **[⬆ Back to Top](#table-of-contents)**

264. ### How do you define multiple properties on an object

     The `Object.defineProperties()` method is used to define new or modify existing properties directly on an object and returning the object. Let's define multiple properties on an empty object,

     ```javascript
     const newObject = {};

     Object.defineProperties(newObject, {
       newProperty1: {
         value: 'John',
         writable: true
       },
       newProperty2: {}
     });
     ```

     **[⬆ Back to Top](#table-of-contents)**

265. ### What is MEAN in javascript

     The MEAN (MongoDB, Express, AngularJS, and Node.js) stack is the most popular open-source JavaScript software tech stack available for building dynamic web apps where you can write both the server-side and client-side halves of the web project entirely in JavaScript.

     **[⬆ Back to Top](#table-of-contents)**

266. ### What Is Obfuscation in javascript

     Obfuscation is the deliberate act of creating obfuscated javascript code(i.e, source or machine code) that is difficult for humans to understand. It is something similar to encryption, but a machine can understand the code and execute it.
     Let's see the below function before Obfuscation,

     ```javascript
     function greeting() {
        console.log('Hello, welcome to JS world');
     }
     ```

     And after the code Obfuscation, it would be appeared as below,

     ```javascript
     eval(function(p,a,c,k,e,d){e=function(c){return c};if(!''.replace(/^/,String)){while(c--){d[c]=k[c]||c}k=[function(e){return d[e]}];e=function(){return'\\w+'};c=1};while(c--){if(k[c]){p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c])}}return p}('2 1(){0.3(\'4, 7 6 5 8\')}',9,9,'console|greeting|function|log|Hello|JS|to|welcome|world'.split('|'),0,{}))
     ```

     **[⬆ Back to Top](#table-of-contents)**

267. ### Why do you need Obfuscation

     Below are the few reasons for Obfuscation,
     1. The Code size will be reduced. So data transfers between server and client will be fast.
     2. It hides the business logic from outside world and protects the code from others
     3. Reverse engineering is highly difficult
     4. The download time will be reduced

     **[⬆ Back to Top](#table-of-contents)**

268. ### What is Minification

     Minification is the process of removing all unnecessary characters(empty spaces are removed) and variables will be renamed without changing it's functionality. It is also a type of obfuscation .

     **[⬆ Back to Top](#table-of-contents)**

269. ### What are the advantages of minification

     Normally it is recommended to use minification for heavy traffic and intensive requirements of resources. It reduces file sizes with below benefits,
     1. Decreases loading times of a web page
     2. Saves bandwidth usages

     **[⬆ Back to Top](#table-of-contents)**

270. ### What are the differences between Obfuscation and Encryption

     Below are the main differences between Obfuscation and Encryption,

     | Feature | Obfuscation | Encryption |
     |---- | --------- | ----
     | Definition  | Changing the form of any data in any other form  | Changing the form of information to an unreadable format by using a key |
     | A key to decode | It can be decoded without any key  | It is required |
     | Target data format | It will be converted to a complex form  | Converted into an unreadable format  |

     **[⬆ Back to Top](#table-of-contents)**

271. ### What are the common tools used for minification

     There are many online/offline tools to minify the javascript files,
     1. Google's Closure Compiler
     2. UglifyJS2
     3. jsmin
     4. javascript-minifier.com/
     5. prettydiff.com

     **[⬆ Back to Top](#table-of-contents)**

272. ### How do you perform form validation using javascript

     JavaScript can be used to perform HTML form validation. For example, if the form field is empty, the function needs to notify, and return false, to prevent the form being submitted.
     Lets' perform user login in an html form,

     ```html
     <form name="myForm" onsubmit="return validateForm()" method="post">
     User name: <input type="text" name="uname">
     <input type="submit" value="Submit">
     </form>
     ```

     And the validation on user login is below,

     ```javascript
     function validateForm() {
       var x = document.forms["myForm"]["uname"].value;
       if (x == "") {
         alert("The username shouldn't be empty");
         return false;
       }
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

273. ### How do you perform form validation without javascript

     You can perform HTML form validation automatically without using javascript. The validation enabled by applying the `required` attribute to prevent form submission when the input is empty.

     ```html
     <form method="post">
       <input type="text" name="uname" required>
       <input type="submit" value="Submit">
     </form>
     ```

     **Note:** Automatic form validation does not work in Internet Explorer 9 or earlier.

     **[⬆ Back to Top](#table-of-contents)**

274. ### What are the DOM methods available for constraint validation

     The below DOM methods are available for constraint validation on an invalid input,
     1. checkValidity(): It returns true if an input element contains valid data.
     2. setCustomValidity(): It is used to set the validationMessage property of an input element.
     Let's take an user login form with DOM validations

     ```javascript
     function myFunction() {
       var userName = document.getElementById("uname");
       if (!userName.checkValidity()) {
         document.getElementById("message").innerHTML = userName.validationMessage;
       } else {
         document.getElementById("message").innerHTML = "Entered a valid username";
       }
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

275. ### What are the available constraint validation DOM properties

     Below are the list of some of the constraint validation DOM properties available,

     1. validity: It provides a list of boolean properties related to the validity of an input element.
     2. validationMessage: It displays the message when the validity is false.
     3. willValidate: It indicates if an input element will be validated or not.

     **[⬆ Back to Top](#table-of-contents)**

276. ### What are the list of validity properties

     The validity property of an input element provides a set of properties related to the validity of data.

     1. customError: It returns true, if a custom validity message is set.
     2. patternMismatch: It returns true, if an element's value does not match its pattern attribute.
     3. rangeOverflow: It returns true, if an element's value is greater than its max attribute.
     4. rangeUnderflow: It returns true, if an element's value is less than its min attribute.
     5. stepMismatch: It returns true, if an element's value is invalid according to step attribute.
     6. tooLong: It returns true, if an element's value exceeds its maxLength attribute.
     7. typeMismatch: It returns true, if an element's value is invalid according to type attribute.
     8. valueMissing: It returns true, if an element with a required attribute has no value.
     9. valid: It returns true, if an element's value is valid.

     **[⬆ Back to Top](#table-of-contents)**

277. ### Give an example usage of rangeOverflow property

     If an element's value is greater than its max attribute then rangeOverflow property returns true. For example, the below form submission throws an error if the value is more than 100,

     ```html
     <input id="age" type="number" max="100">
     <button onclick="myOverflowFunction()">OK</button>
     ```

     ```javascript
     function myOverflowFunction() {
       if (document.getElementById("age").validity.rangeOverflow) {
         alert("The mentioned age is not allowed");
       }
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

278. ### Is enums feature available in javascript

     No, javascript does not natively support enums. But there are different kinds of solutions to simulate them even though they may not provide exact equivalents. For example, you can use freeze or seal on object,

     ```javascript
     var DaysEnum = Object.freeze({"monday":1, "tuesday":2, "wednesday":3, ...})
     ```

     **[⬆ Back to Top](#table-of-contents)**

279. ### What is an enum

     An enum is a type restricting variables to one value from a predefined set of constants. JavaScript has no enums but typescript provides built-in enum support.

     ```javascript
     enum Color {
      RED, GREEN, BLUE
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

280. ### How do you list all properties of an object

     You can use the `Object.getOwnPropertyNames()` method which returns an array of all properties found directly in a given object. Let's the usage of it in an example,

     ```javascript
     const newObject = {
       a: 1,
       b: 2,
       c: 3
     };

     console.log(Object.getOwnPropertyNames(newObject));  ["a", "b", "c"]
     ```

     **[⬆ Back to Top](#table-of-contents)**

281. ### How do you get property descriptors of an object

     You can use the `Object.getOwnPropertyDescriptors()` method which returns all own property descriptors of a given object. The example usage of this method is below,

     ```javascript
      const newObject = {
        a: 1,
        b: 2,
        c: 3
      };
     const descriptorsObject = Object.getOwnPropertyDescriptors(newObject);
     console.log(descriptorsObject.a.writable); //true
     console.log(descriptorsObject.a.configurable); //true
     console.log(descriptorsObject.a.enumerable); //true
     console.log(descriptorsObject.a.value); // 1
     ```

     **[⬆ Back to Top](#table-of-contents)**

282. ### What are the attributes provided by a property descriptor

     A property descriptor is a record which has the following attributes
     1. value: The value associated with the property
     2. writable: Determines whether the value associated with the property can be changed or not
     3. configurable: Returns true if the type of this property descriptor can be changed and if the property can be deleted from the corresponding object.
     4. enumerable: Determines whether the property appears during enumeration of the properties on the corresponding object or not.
     5. set: A function which serves as a setter for the property
     6. get: A function which serves as a getter for the property

     **[⬆ Back to Top](#table-of-contents)**

283. ### How do you extend classes

     The `extends` keyword is used in class declarations/expressions to create a class which is a child of another class. It can be used to subclass custom classes as well as built-in objects. The syntax would be as below,

     ```javascript
     class ChildClass extends ParentClass { ... }
     ```

     Let's take an example of Square subclass from Polygon parent class,

     ```javascript
      class Square extends Rectangle {
        constructor(length) {
          super(length, length);
          this.name = 'Square';
        }

        get area() {
          return this.width * this.height;
        }

        set area(value) {
          this.area = value;
        }
      }
     ```

     **[⬆ Back to Top](#table-of-contents)**

284. ### How do I modify the url without reloading the page

     The `window.location.url` property will be helpful to modify the url but it reloads the page. HTML5 introduced the `history.pushState()` and `history.replaceState()` methods, which allow you to add and modify history entries, respectively. For example, you can use pushState as below,

     ```javascript
     window.history.pushState('page2', 'Title', '/page2.html');
     ```

     **[⬆ Back to Top](#table-of-contents)**

285. ### How do you check whether an array includes a particular value or not

     The `Array#includes()` method is used to determine whether an array includes a particular value among its entries by returning either true or false. Let's see an example to find an element(numeric and string) within an array.

     ```javascript
     var numericArray = [1, 2, 3, 4];
     console.log(numericArray.includes(3)); // true

     var stringArray = ['green', 'yellow', 'blue'];
     console.log(stringArray.includes('blue')); //true
     ```

     **[⬆ Back to Top](#table-of-contents)**

286. ### How do you compare scalar arrays

     You can use length and every method of arrays to compare two scalar(compared directly using ===) arrays. The combination of these expressions can give the expected result,

     ```javascript
     const arrayFirst = [1,2,3,4,5];
     const arraySecond = [1,2,3,4,5];
     console.log(arrayFirst.length === arraySecond.length && arrayFirst.every((value, index) => value === arraySecond[index])); // true
     ````

     If you would like to compare arrays irrespective of order then you should sort them before,

     ```javascript
     const arrayFirst = [2,3,1,4,5];
     const arraySecond = [1,2,3,4,5];
     console.log(arrayFirst.length === arraySecond.length && arrayFirst.sort().every((value, index) => value === arraySecond[index])); //true
     ````

     **[⬆ Back to Top](#table-of-contents)**

287. ### How to get the value from get parameters

     The `new URL()` object accepts the url string and `searchParams` property of this object can be used to access the get parameters. Remember that you may need to use polyfill or `window.location` to access the URL in older browsers(including IE).

     ```javascript
     let urlString = "http://www.some-domain.com/about.html?x=1&y=2&z=3"; //window.location.href
     let url = new URL(urlString);
     let parameterZ = url.searchParams.get("z");
     console.log(parameterZ); // 3
     ```

     **[⬆ Back to Top](#table-of-contents)**

288. ### How do you print numbers with commas as thousand separators

     You can use the `Number.prototype.toLocaleString()` method which returns a string with a language-sensitive representation such as thousand separator,currency etc of this number.

     ```javascript
     function convertToThousandFormat(x){
       return x.toLocaleString(); // 12,345.679
     }

     console.log(convertToThousandFormat(12345.6789));
     ```

     **[⬆ Back to Top](#table-of-contents)**

289. ### What is the difference between java and javascript

     Both are totally unrelated programming languages and no relation between them. Java is statically typed, compiled, runs on its own VM. Whereas Javascript is dynamically typed, interpreted, and runs in a browser and nodejs environments. Let's see the major differences in a tabular format,
     | Feature | Java | JavaScript |
     |---- | ---- | -----
     | Typed  | It's a strongly typed language | It's a dynamic typed language |
     | Paradigm | Object oriented programming  | Prototype based programming |
     | Scoping | Block scoped | Function-scoped |
     | Concurrency | Thread based | event based |
     | Memory | Uses more memory | Uses less memory. Hence it will be used for web pages |

     **[⬆ Back to Top](#table-of-contents)**

290. ### Is javascript supports namespace

     JavaScript doesn’t support namespace by default. So if you create any element(function, method, object, variable) then it becomes global and pollutes the global namespace. Let's take an example of defining two functions without any namespace,

     ```javascript
     function func1() {
         console.log("This is a first definition");

     }
     function func1() {
         console.log("This is a second definition");
     }
     func1(); // This is a second definition
     ```

     It always calls the second function definition. In this case, namespace will solve the name collision problem.

     **[⬆ Back to Top](#table-of-contents)**

291. ### How do you declare namespace

     Even though JavaScript lacks namespaces, we can use Objects , IIFE to create namespaces.
     1. **Using Object Literal Notation:** Let's wrap variables and functions inside an Object literal which acts as a namespace. After that you can access them using object notation

     ```javascript
     var namespaceOne = {
        function func1() {
            console.log("This is a first definition");
        }
     }
     var namespaceTwo = {
          function func1() {
              console.log("This is a second definition");
          }
      }
     namespaceOne.func1(); // This is a first definition
     namespaceTwo.func1(); // This is a second definition
     ```

     1. **Using IIFE (Immediately invoked function expression):** The outer pair of parentheses of IIFE creates a local scope for all the code inside of it and makes the anonymous function a function expression. Due to that, you can create the same function in two different function expressions to act as a namespace.

     ```javascript
     (function() {
      function fun1(){
        console.log("This is a first definition");
        } fun1();
     }());

     (function() {
         function fun1(){
            console.log("This is a second definition");
        } fun1();
      }());
     ```

     1. **Using a block and a let/const declaration:** In ECMAScript 6, you can simply use a block and a let declaration to restrict the scope of a variable to a block.

     ```javascript
      {
       let myFunction= function fun1(){
       console.log("This is a first definition");
       }
       myFunction();
      }
       //myFunction(): ReferenceError: myFunction is not defined.

      {
       let myFunction= function fun1(){
       console.log("This is a second definition");
       }
       myFunction();
      }
       //myFunction(): ReferenceError: myFunction is not defined.
     ```

     **[⬆ Back to Top](#table-of-contents)**

292. ### How do you invoke javascript code in an iframe from parent page

     Initially iFrame needs to be accessed using either `document.getElementBy` or `window.frames`. After that `contentWindow` property of iFrame gives the access for targetFunction

     ```javascript
     document.getElementById('targetFrame').contentWindow.targetFunction();
     window.frames[0].frameElement.contentWindow.targetFunction(); // Accessing iframe this way may not work in latest versions chrome and firefox

     ```

     **[⬆ Back to Top](#table-of-contents)**

293. ### How do get the timezone offset from date

     You can use the `getTimezoneOffset` method of the date object. This method returns the time zone difference, in minutes, from current locale (host system settings) to UTC

     ```javascript
     var offset = new Date().getTimezoneOffset();
     console.log(offset); // -480
     ```

     **[⬆ Back to Top](#table-of-contents)**

294. ### How do you load CSS and JS files dynamically

     You can create both link and script elements in the DOM and append them as child to head tag. Let's create a function to add script and style resources as below,

     ```javascript
     function loadAssets(filename, filetype) {
       if (filetype == "css") { // External CSS file
            var fileReference = document.createElement("link")
            fileReference.setAttribute("rel", "stylesheet");
            fileReference.setAttribute("type", "text/css");
            fileReference.setAttribute("href", filename);
       } else if (filetype == "js") { // External JavaScript file
            var fileReference = document.createElement('script');
            fileReference.setAttribute("type", "text/javascript");
            fileReference.setAttribute("src", filename);
       }
       if (typeof fileReference != "undefined")
            document.getElementsByTagName("head")[0].appendChild(fileReference)
      }
     ```

     **[⬆ Back to Top](#table-of-contents)**

295. ### What are the different methods to find HTML elements in DOM

     If you want to access any element in an HTML page, you need to start with accessing the document object. Later you can use any of the below methods to find the HTML element,
     1. document.getElementById(id): It finds an element by Id
     2. document.getElementsByTagName(name): It finds an element by tag name
     3. document.getElementsByClassName(name): It finds an element by class name

     **[⬆ Back to Top](#table-of-contents)**

296. ### What is jQuery

     jQuery is a popular cross-browser JavaScript library that provides Document Object Model (DOM) traversal, event handling, animations and AJAX interactions by minimizing the discrepancies across browsers. It is widely famous with its philosophy of “Write less, do more”. For example, you can display welcome message on the page load using jQuery as below,

     ```javascript
     $(document).ready(function(){ // It selects the document and apply the function on page load
         alert('Welcome to jQuery world');
     });
     ```

     **Note:** You can download it from jquery's official site or install it from CDNs, like google.

     **[⬆ Back to Top](#table-of-contents)**

297. ### What is V8 JavaScript engine

     V8 is an open source high-performance JavaScript engine used by the Google Chrome browser, written in C++. It is also being used in the node.js project. It implements ECMAScript and WebAssembly, and runs on Windows 7 or later, macOS 10.12+, and Linux systems that use x64, IA-32, ARM, or MIPS processors.
     **Note:** It can run standalone, or can be embedded into any C++ application.

     **[⬆ Back to Top](#table-of-contents)**

298. ### Why do we call javascript as dynamic language

     JavaScript is a loosely typed or a dynamic language because variables in JavaScript are not directly associated with any particular value type, and any variable can be assigned/reassigned with values of all types.

     ```javascript
     let age = 50;    // age is a number now
     age  = 'old'; // age is a string now
     age  = true;  // age is a boolean
     ```

     **[⬆ Back to Top](#table-of-contents)**

299. ### What is a void operator

     The `void` operator evaluates the given expression and then returns undefined(i.e, without returning value). The syntax would be as below,

     ```javascript
     void (expression)
     void expression
     ```

     Let's display a message without any redirection or reload

     ```javascript
     <a href="javascript:void(alert('Welcome to JS world'))">Click here to see a message</a>
     ```

     **Note:** This operator is often used to obtain the undefined primitive value, using "void(0)".

     **[⬆ Back to Top](#table-of-contents)**

300. ### How to set the cursor to wait

     The cursor can be set to wait in JavaScript by using the property "cursor". Let's perform this behavior on page load using the below function.

     ```javascript
     function myFunction() {
     window.document.body.style.cursor = "wait";
     }
     ```

     and this function invoked on page load

     ```html
     <body onload="myFunction()">
     ```

     **[⬆ Back to Top](#table-of-contents)**

301. ### How do you create an infinite loop

     You can create infinite loops using for and while loops without using any expressions. The for loop construct or syntax is better approach in terms of ESLint and code optimizer tools,

     ```javascript
     for (;;) {}
     while(true) {
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

302. ### Why do you need to avoid with statement

     JavaScript's with statement was intended to provide a shorthand for writing recurring accesses to objects. So it can help reduce file size by reducing the need to repeat a lengthy object reference without performance penalty. Let's take an example where it is used to avoid redundancy when accessing an object several times.

     ```javascript
     a.b.c.greeting   = 'welcome';
     a.b.c.age = 32;
     ```

     Using `with` it turns this into:

     ```javascript
     with(a.b.c) {
             greeting   = "welcome";
             age = 32;
     }
     ```

     But this `with` statement creates performance problems since one cannot predict whether an argument will refer to a real variable or to a property inside the with argument.

     **[⬆ Back to Top](#table-of-contents)**

303. ### What is the output of below for loops

     ```javascript
     for (var i = 0; i < 4; i++) { // global scope
       setTimeout(() => console.log(i));
     }

     for (let i = 0; i < 4; i++) { // block scope
       setTimeout(() => console.log(i));
     }
     ```

     The output of the above for loops is 4 4 4 4 and 0 1 2 3
     
     **Explanation:** Due to the event queue/loop of javascript, the `setTimeout` callback function is called after the loop has been executed. Since the variable i is declared with the `var` keyword it became a global variable and the value was equal to 4 using iteration when the time `setTimeout` function is invoked. Hence, the output of the first loop is `4 4 4 4`. 
     
     Whereas in the second loop, the variable i is declared as the `let` keyword it becomes a block scoped variable and it holds a new value(0, 1 ,2 3) for each iteration. Hence, the output of the first loop is `0 1 2 3`.

     **[⬆ Back to Top](#table-of-contents)**

304. ### List down some of the features of ES6

     Below are the list of some new features of ES6,
     1. Support for constants or immutable variables
     2. Block-scope support for variables, constants and functions
     3. Arrow functions
     4. Default parameters
     5. Rest and Spread Parameters
     6. Template Literals
     7. Multi-line Strings
     8. Destructuring Assignment
     9. Enhanced Object Literals
     10. Promises
     11. Classes
     12. Modules

     **[⬆ Back to Top](#table-of-contents)**

305. ### What is ES6

     ES6 is the sixth edition of the javascript language and it was released in June 2015. It was initially known as ECMAScript 6 (ES6) and later renamed to ECMAScript 2015. Almost all the modern browsers support ES6 but for the old browsers there are many transpilers, like Babel.js etc.

     **[⬆ Back to Top](#table-of-contents)**

306. ### Can I redeclare let and const variables

     No, you cannot redeclare let and const variables. If you do, it throws below error

     ```bash
     Uncaught SyntaxError: Identifier 'someVariable' has already been declared
     ```

     **Explanation:** The variable declaration with `var` keyword refers to a function scope and the variable is treated as if it were declared at the top of the enclosing scope due to hoisting feature. So all the multiple declarations contributing to the same hoisted variable without any error. Let's take an example of re-declaring variables in the same scope for both var and let/const variables.

     ```javascript
     var name = 'John';
     function myFunc() {
         var name = 'Nick';
         var name = 'Abraham'; // Re-assigned in the same function block
         alert(name); // Abraham
     }
     myFunc();
     alert(name); // John
     ```

     The block-scoped multi-declaration throws syntax error,

     ```javascript
     let name = 'John';
     function myFunc() {
         let name = 'Nick';
         let name = 'Abraham'; // Uncaught SyntaxError: Identifier 'name' has already been declared
         alert(name);
     }

     myFunc();
     alert(name);
     ```

     **[⬆ Back to Top](#table-of-contents)**

307. ### Is const variable makes the value immutable

     No, the const variable doesn't make the value immutable. But it disallows subsequent assignments(i.e, You can declare with assignment but can't assign another value later)

     ```javascript
     const userList = [];
     userList.push('John'); // Can mutate even though it can't re-assign
     console.log(userList); // ['John']
     ```

     **[⬆ Back to Top](#table-of-contents)**

308. ### What are default parameters

     In E5, we need to depend on logical OR operators to handle default values of function parameters. Whereas in ES6, Default function parameters feature allows parameters to be initialized with default values if no value or undefined is passed. Let's compare the behavior with an examples,

     ```javascript
     //ES5
     var calculateArea = function(height, width) {
        height =  height || 50;
        width = width || 60;

        return width * height;
     }
     console.log(calculateArea()); //300
     ```

     The default parameters makes the initialization more simpler,

     ```javascript
     //ES6
     var calculateArea = function(height = 50, width = 60) {
        return width * height;
     }

     console.log(calculateArea()); //300
     ```

     **[⬆ Back to Top](#table-of-contents)**

309. ### What are template literals

     Template literals or template strings are string literals allowing embedded expressions. These are enclosed by the back-tick (`) character instead of double or single quotes.
     In E6, this feature enables using dynamic expressions as below,

     ```javascript
     var greeting = `Welcome to JS World, Mr. ${firstName} ${lastName}.`
     ```

     In ES5, you need break string like below,

     ```javascript
     var greeting = 'Welcome to JS World, Mr. ' + firstName + ' ' + lastName.`
     ```

     **Note:** You can use multi-line strings and string interpolation features with template literals.

     **[⬆ Back to Top](#table-of-contents)**

310. ### How do you write multi-line strings in template literals

     In ES5, you would have to use newline escape characters('\\n') and concatenation symbols(+) in order to get multi-line strings.

     ```javascript
     console.log('This is string sentence 1\n' +
     'This is string sentence 2');
     ```

     Whereas in ES6, You don't need to mention any newline sequence character,

     ```javascript
     console.log(`This is string sentence
     'This is string sentence 2`);
     ```

     **[⬆ Back to Top](#table-of-contents)**

311. ### What are nesting templates

     The nesting template is a feature supported within template literals syntax to allow inner backticks inside a placeholder ${ } within the template. For example, the below nesting template is used to display the icons based on user permissions whereas outer template checks for platform type,

     ```javascript
     const iconStyles = `icon ${ isMobilePlatform() ? '' :
      `icon-${user.isAuthorized ? 'submit' : 'disabled'}` }`;
     ```

     You can write the above use case without nesting template features as well. However, the nesting template feature is more compact and readable.

     ```javascript
     //Without nesting templates
      const iconStyles = `icon ${ isMobilePlatform() ? '' :
       (user.isAuthorized ? 'icon-submit' : 'icon-disabled'}`;
     ```

     **[⬆ Back to Top](#table-of-contents)**

312. ### What are tagged templates

     Tagged templates are the advanced form of templates in which tags allow you to parse template literals with a function. The tag function accepts the first parameter as an array of strings and remaining parameters as expressions. This function can also return manipulated strings based on parameters. Let's see the usage of this tagged template behavior of an IT professional skill set in an organization,

     ```javascript
     var user1 = 'John';
     var skill1 = 'JavaScript';
     var experience1 = 15;

     var user2 = 'Kane';
     var skill2 = 'JavaScript';
     var experience2 = 5;

     function myInfoTag(strings, userExp, experienceExp, skillExp) {
       var str0 = strings[0]; // "Mr/Ms. "
       var str1 = strings[1]; // " is a/an "
       var str2 = strings[2]; // "in"

       var expertiseStr;
       if (experienceExp > 10){
         expertiseStr = 'expert developer';
       } else if(skillExp > 5 && skillExp <= 10) {
         expertiseStr = 'senior developer';
       } else {
         expertiseStr = 'junior developer';
       }

       return ${str0}${userExp}${str1}${expertiseStr}${str2}${skillExp};
     }

     var output1 = myInfoTag`Mr/Ms. ${ user1 } is a/an ${ experience1 } in ${skill1}`;
     var output2 = myInfoTag`Mr/Ms. ${ user2 } is a/an ${ experience2 } in ${skill2}`;

     console.log(output1);// Mr/Ms. John is a/an expert developer in JavaScript
     console.log(output2);// Mr/Ms. Kane is a/an junior developer in JavaScript
     ```

     **[⬆ Back to Top](#table-of-contents)**

313. ### What are raw strings

      ES6 provides a raw strings feature using the `String.raw()` method which is used to get the raw string form of template strings. This feature allows you to access the raw strings as they were entered, without processing escape sequences. For example, the usage would be as below,

      ```javascript
      var calculationString = String.raw `The sum of numbers is \n${1+2+3+4}!`;
      console.log(calculationString); // The sum of numbers is 10
      ```

      If you don't use raw strings, the newline character sequence will be processed by displaying the output in multiple lines

      ```javascript
      var calculationString = `The sum of numbers is \n${1+2+3+4}!`;
      console.log(calculationString);
      // The sum of numbers is
      // 10
      ```

      Also, the raw property is available on the first argument to the tag function

      ```javascript
      function tag(strings) {
         console.log(strings.raw[0]);
      }
      ```

      **[⬆ Back to Top](#table-of-contents)**

314. ### What is destructuring assignment

     The destructuring assignment is a JavaScript expression that makes it possible to unpack values from arrays or properties from objects into distinct variables.
     Let's get the month values from an array using destructuring assignment

     ```javascript
     var [one, two, three] = ['JAN', 'FEB', 'MARCH'];

     console.log(one); // "JAN"
     console.log(two); // "FEB"
     console.log(three); // "MARCH"
     ```

     and you can get user properties of an object using destructuring assignment,

     ```javascript
     var {name, age} = {name: 'John', age: 32};

     console.log(name); // John
     console.log(age); // 32
     ```

     **[⬆ Back to Top](#table-of-contents)**

315. ### What are default values in destructuring assignment

     A variable can be assigned a default value when the value unpacked from the array or object is undefined during destructuring assignment. It helps to avoid setting default values separately for each assignment. Let's take an example for both arrays and object use cases,

     **Arrays destructuring:**

     ```javascript
     var x, y, z;

     [x=2, y=4, z=6] = [10];
     console.log(x); // 10
     console.log(y); // 4
     console.log(z); // 6
     ```

     **Objects destructuring:**

     ```javascript
     var {x=2, y=4, z=6} = {x: 10};

     console.log(x); // 10
     console.log(y); // 4
     console.log(z); // 6
     ```

     **[⬆ Back to Top](#table-of-contents)**

316. ### How do you swap variables in destructuring assignment

     If you don't use destructuring assignment, swapping two values requires a temporary variable. Whereas using a destructuring feature, two variable values can be swapped in one destructuring expression. Let's swap two number variables in array destructuring assignment,

     ```javascript
     var x = 10, y = 20;

     [x, y] = [y, x];
     console.log(x); // 20
     console.log(y); // 10
     ```

     **[⬆ Back to Top](#table-of-contents)**

317. ### What are enhanced object literals

     Object literals make it easy to quickly create objects with properties inside the curly braces. For example, it provides shorter syntax for common object property definition as below.

     ```javascript
     //ES6
     var x = 10, y = 20
     obj = { x, y }
     console.log(obj); // {x: 10, y:20}
     //ES5
     var x = 10, y = 20
     obj = { x : x, y : y}
     console.log(obj); // {x: 10, y:20}
     ```

     **[⬆ Back to Top](#table-of-contents)**

318. ### What are dynamic imports

     The dynamic imports using `import()` function syntax allows us to load modules on demand by using promises or the async/await syntax. Currently this feature is in [stage4 proposal](https://github.com/tc39/proposal-dynamic-import). The main advantage of dynamic imports is reduction of our bundle's sizes, the size/payload response of our requests and overall improvements in the user experience.
     The syntax of dynamic imports would be as below,

     ```javascript
     import('./Module').then(Module => Module.method());
     ```

     **[⬆ Back to Top](#table-of-contents)**

319. ### What are the use cases for dynamic imports

     Below are some of the use cases of using dynamic imports over static imports,
     1. Import a module on-demand or conditionally. For example, if you want to load a polyfill on legacy browser

     ```javascript
     if (isLegacyBrowser()) {
         import(···)
         .then(···);
     }
     ```

     1. Compute the module specifier at runtime. For example, you can use it for internationalization.

     ```javascript
     import(`messages_${getLocale()}.js`).then(···);
     ```

     1. Import a module from within a regular script instead a module.

     **[⬆ Back to Top](#table-of-contents)**

320. ### What are typed arrays

     Typed arrays are array-like objects from ECMAScript 6 API for handling binary data. JavaScript provides 8 Typed array types,

     1. Int8Array: An array of 8-bit signed integers
     2. Int16Array: An array of 16-bit signed integers
     3. Int32Array: An array of 32-bit signed integers
     4. Uint8Array: An array of 8-bit unsigned integers
     5. Uint16Array: An array of 16-bit unsigned integers
     6. Uint32Array: An array of 32-bit unsigned integers
     7. Float32Array: An array of 32-bit floating point numbers
     8. Float64Array: An array of 64-bit floating point numbers

     For example, you can create an array of 8-bit signed integers as below

     ```javascript
     const a = new Int8Array();
     // You can pre-allocate n bytes
     const bytes = 1024
     const a = new Int8Array(bytes)
     ```

     **[⬆ Back to Top](#table-of-contents)**

321. ### What are the advantages of module loaders

     The module loaders provides the below features,
     1. Dynamic loading
     2. State isolation
     3. Global namespace isolation
     4. Compilation hooks
     5. Nested virtualization

     **[⬆ Back to Top](#table-of-contents)**

322. ### What is collation

     Collation is used for sorting a set of strings and searching within a set of strings. It is parameterized by locale and aware of Unicode. Let's take comparison and sorting features,
     1. **Comparison:**

     ```javascript
     var list = [ "ä", "a", "z" ]; // In German,  "ä" sorts with "a" Whereas in Swedish, "ä" sorts after "z"
     var l10nDE = new Intl.Collator("de");
     var l10nSV = new Intl.Collator("sv");
     console.log(l10nDE.compare("ä", "z") === -1); // true
     console.log(l10nSV.compare("ä", "z") === +1); // true
     ```

     1. **Sorting:**

     ```javascript
     var list = [ "ä", "a", "z" ]; // In German,  "ä" sorts with "a" Whereas in Swedish, "ä" sorts after "z"
     var l10nDE = new Intl.Collator("de");
     var l10nSV = new Intl.Collator("sv");
     console.log(list.sort(l10nDE.compare)) // [ "a", "ä", "z" ]
     console.log(list.sort(l10nSV.compare)) // [ "a", "z", "ä" ]
     ```

     **[⬆ Back to Top](#table-of-contents)**

323. ### What is for...of statement

     The for...of statement creates a loop iterating over iterable objects or elements such as built-in String, Array, Array-like objects (like arguments or NodeList), TypedArray, Map, Set, and user-defined iterables. The basic usage of for...of statement on arrays would be as below,

     ```javascript
     let arrayIterable = [10, 20, 30, 40, 50];

     for (let value of arrayIterable) {
       value ++;
       console.log(value); // 11 21 31 41 51
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

324. ### What is the output of below spread operator array

     ```javascript
     [...'John Resig']
     ```

     The output of the array is ['J', 'o', 'h', 'n', '', 'R', 'e', 's', 'i', 'g']
     **Explanation:** The string is an iterable type and the spread operator within an array maps every character of an iterable to one element. Hence, each character of a string becomes an element within an Array.

     **[⬆ Back to Top](#table-of-contents)**

325. ### Is PostMessage secure

     Yes, postMessages can be considered very secure as long as the programmer/developer is careful about checking the origin and source of an arriving message. But if you try to send/receive a message without verifying its source will create cross-site scripting attacks.

     **[⬆ Back to Top](#table-of-contents)**

326. ### What are the problems with postmessage target origin as wildcard

     The second argument of postMessage method specifies which origin is allowed to receive the message. If you use the wildcard “*” as an argument then any origin is allowed to receive the message. In this case, there is no way for the sender window to know if the target window is at the target origin when sending the message. If the target window has been navigated to another origin, the other origin would receive the data. Hence, this may lead to XSS vulnerabilities.

     ```javascript
     targetWindow.postMessage(message, '*');
     ```

     **[⬆ Back to Top](#table-of-contents)**

327. ### How do you avoid receiving postMessages from attackers

     Since the listener listens for any message, an attacker can trick the application by sending a message from the attacker’s origin,  which gives an impression that the receiver received the message from the actual sender’s window. You can avoid this issue by validating the origin of the message on the receiver's end using the “message.origin” attribute. For examples, let's check the sender's origin [http://www.some-sender.com](http://www.some-sender.com) on receiver side [www.some-receiver.com](www.some-receiver.com),

     ```javascript
     //Listener on http://www.some-receiver.com/
     window.addEventListener("message", function(message){
         if(/^http://www\.some-sender\.com$/.test(message.origin)){
              console.log('You received the data from valid sender', message.data);
        }
     });
     ```

     **[⬆ Back to Top](#table-of-contents)**

328. ### Can I avoid using postMessages completely

     You cannot avoid using postMessages completely(or 100%). Even though your application doesn’t use postMessage considering the risks, a lot of third party scripts use postMessage to communicate with the third party service. So your application might be using postMessage without your knowledge.

     **[⬆ Back to Top](#table-of-contents)**

329. ### Is postMessages synchronous

     The postMessages are synchronous in IE8 browser but they are asynchronous in IE9 and all other modern browsers (i.e, IE9+, Firefox, Chrome, Safari).Due to this asynchronous behaviour, we use a callback mechanism when the postMessage is returned.

     **[⬆ Back to Top](#table-of-contents)**

330. ### What paradigm is Javascript

     JavaScript is a multi-paradigm language, supporting imperative/procedural programming, Object-Oriented Programming and functional programming. JavaScript supports Object-Oriented Programming with prototypical inheritance.

     **[⬆ Back to Top](#table-of-contents)**

331. ### What is the difference between internal and external javascript

     **Internal JavaScript:** It is the source code within the script tag.
     **External JavaScript:** The source code is stored in an external file(stored with .js extension) and referred with in the tag.

     **[⬆ Back to Top](#table-of-contents)**

332. ### Is JavaScript faster than server side script

     Yes, JavaScript is faster than server side script. Because JavaScript is a client-side script it does not require any web server’s help for its computation or calculation. So JavaScript is always faster than any server-side script like ASP, PHP, etc.

     **[⬆ Back to Top](#table-of-contents)**

333. ### How do you get the status of a checkbox

     You can apply the `checked` property on the selected checkbox in the DOM. If the value is `True` means the checkbox is checked otherwise it is unchecked. For example, the below HTML checkbox element can be access using javascript as below,

     ```html
       <input type="checkbox" name="checkboxname" value="Agree"> Agree the conditions<br>
     ```

     ```javascript
     console.log(document.getElementById(‘checkboxname’).checked); // true or false
     ```

     **[⬆ Back to Top](#table-of-contents)**

334. ### What is the purpose of double tilde operator

     The double tilde operator(~~) is known as double NOT bitwise operator. This operator is going to be a quicker substitute for Math.floor().

     **[⬆ Back to Top](#table-of-contents)**

335. ### How do you convert character to ASCII code

     You can use the `String.prototype.charCodeAt()` method to convert string characters to ASCII numbers. For example, let's find ASCII code for the first letter of 'ABC' string,

     ```javascript
     "ABC".charCodeAt(0) // returns 65
     ```

     Whereas `String.fromCharCode()` method converts numbers to equal ASCII characters.

     ```javascript
     String.fromCharCode(65,66,67); // returns 'ABC'
     ```

     **[⬆ Back to Top](#table-of-contents)**

336. ### What is ArrayBuffer

     An ArrayBuffer object is used to represent a generic, fixed-length raw binary data buffer. You can create it as below,

     ```javascript
     let buffer = new ArrayBuffer(16); // create a buffer of length 16
     alert(buffer.byteLength); // 16
     ```

     To manipulate an ArrayBuffer, we need to use a “view” object.

     ```javascript
     //Create a DataView referring to the buffer
      let view = new DataView(buffer);
     ```

     **[⬆ Back to Top](#table-of-contents)**

337. ### What is the output of below string expression

     ```javascript
     console.log("Welcome to JS world"[0])
     ```

     The output of the above expression is "W".
     **Explanation:** The bracket notation with specific index on a string returns the character at a specific location. Hence, it returns the character "W" of the string. Since this is not supported in IE7 and below versions, you may need to use the .charAt() method to get the desired result.

     **[⬆ Back to Top](#table-of-contents)**

338. ### What is the purpose of Error object

     The Error constructor creates an error object and the instances of error objects are thrown when runtime errors occur. The Error object can also be used as a base object for user-defined exceptions. The syntax of error object would be as below,

     ```javascript
     new Error([message[, fileName[, lineNumber]]])
     ```

     You can throw user defined exceptions or errors using Error object in try...catch block as below,

     ```javascript
     try {
       if(withdraw > balance)
       throw new Error("Oops! You don't have enough balance");
     } catch (e) {
       console.log(e.name + ': ' + e.message);
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

339. ### What is the purpose of EvalError object

     The EvalError object indicates an error regarding the global `eval()` function. Even though this exception is not thrown by JavaScript anymore, the EvalError object remains for compatibility. The syntax of this expression would be as below,

     ```javascript
     new EvalError([message[, fileName[, lineNumber]]])
     ```

     You can throw EvalError with in try...catch block as below,

     ```javascript
     try {
       throw new EvalError('Eval function error', 'someFile.js', 100);
     } catch (e) {
       console.log(e.message, e.name, e.fileName);              // "Eval function error", "EvalError", "someFile.js"
     ```

     **[⬆ Back to Top](#table-of-contents)**

340. ### What are the list of cases error thrown from non-strict mode to strict mode

     When you apply 'use strict'; syntax, some of the below cases will throw a SyntaxError before executing the script
     1. When you use Octal syntax

     ```javascript
     var n = 022;
     ```

     1. Using `with` statement
     2. When you use delete operator on a variable name
     3. Using eval or arguments as variable or function argument name
     4. When you use newly reserved keywords
     5. When you declare a function in a block

     ```javascript
     if (someCondition) { function f() {} }
     ```

     Hence, the errors from above cases are helpful to avoid errors in development/production environments.

     **[⬆ Back to Top](#table-of-contents)**

341. ### Is all objects have prototypes

     No. All objects have prototypes except for the base object which is created by the user, or an object that is created using the new keyword.

     **[⬆ Back to Top](#table-of-contents)**

342. ### What is the difference between a parameter and an argument

     Parameter is the variable name of a function definition whereas an argument represents the value given to a function when it is invoked. Let's explain this with a simple function

     ```javascript
     function myFunction(parameter1, parameter2, parameter3) {
       console.log(arguments[0]) // "argument1"
       console.log(arguments[1]) // "argument2"
       console.log(arguments[2]) // "argument3"
     }
     myFunction("argument1", "argument2", "argument3")
     ```

     **[⬆ Back to Top](#table-of-contents)**

343. ### What is the purpose of some method in arrays

     The some() method is used to test whether at least one element in the array passes the test implemented by the provided function. The method returns a boolean value. Let's take an example to test for any odd elements,

     ```javascript
     var array = [1, 2, 3, 4, 5, 6 ,7, 8, 9, 10];

     var odd = element ==> element % 2 !== 0;

     console.log(array.some(odd)); // true (the odd element exists)
     ```

     **[⬆ Back to Top](#table-of-contents)**

344. ### How do you combine two or more arrays

     The concat() method is used to join two or more arrays by returning a new array containing all the elements. The syntax would be as below,

     ```javascript
     array1.concat(array2, array3, ..., arrayX)
     ```

     Let's take an example of array's concatenation with veggies and fruits arrays,

     ```javascript
       var veggies = ["Tomato", "Carrot", "Cabbage"];
       var fruits = ["Apple", "Orange", "Pears"];
       var veggiesAndFruits = veggies.concat(fruits);
       console.log(veggiesAndFruits); // Tomato, Carrot, Cabbage, Apple, Orange, Pears
     ```

     **[⬆ Back to Top](#table-of-contents)**

345. ### What is the difference between Shallow and Deep copy

      There are two ways to copy an object,

      **Shallow Copy:**
      Shallow copy is a bitwise copy of an object. A new object is created that has an exact copy of the values in the original object. If any of the fields of the object are references to other objects, just the reference addresses are copied i.e., only the memory address is copied.

      **Example**

      ```javascript
      var empDetails = {
        name: "John", age: 25, expertise: "Software Developer"
      }
      ```

      to create a duplicate

      ```javascript
      var empDetailsShallowCopy = empDetails    //Shallow copying!
      ```

      if we change some property value in the duplicate one like this:

      ```javascript
      empDetailsShallowCopy.name = "Johnson"
      ```

      The above statement will also change the name of `empDetails`, since we have a shallow copy. That means we're losing the original data as well.

      **Deep copy:**
      A deep copy copies all fields, and makes copies of dynamically allocated memory pointed to by the fields. A deep copy occurs when an object is copied along with the objects to which it refers.

      **Example**

      ```javascript
      var empDetails = {
        name: "John", age: 25, expertise: "Software Developer"
      }
      ```

      Create a deep copy by using the properties from the original object into new variable

      ```javascript
      var empDetailsDeepCopy = {
        name: empDetails.name,
        age: empDetails.age,
        expertise: empDetails.expertise
      }
      ```

      Now if you change `empDetailsDeepCopy.name`, it will only affect `empDetailsDeepCopy` & not `empDetails`

      **[⬆ Back to Top](#table-of-contents)**

346. ### How do you create specific number of copies of a string

     The `repeat()` method is used to construct and return a new string which contains the specified number of copies of the string on which it was called, concatenated together. Remember that this method has been added to the ECMAScript 2015 specification.
     Let's take an example of Hello string to repeat it 4 times,

     ```javascript
     'Hello'.repeat(4);  // 'HelloHelloHelloHello'
     ```

347. ### How do you return all matching strings against a regular expression

     The `matchAll()` method can be used to return an iterator of all results matching a string against a regular expression. For example, the below example returns an array of matching string results against a regular expression,

     ```javascript
     let regexp = /Hello(\d?))/g;
     let greeting = 'Hello1Hello2Hello3';

     let greetingList = [...greeting.matchAll(regexp)];

     console.log(greetingList[0]); //Hello1
     console.log(greetingList[1]); //Hello2
     console.log(greetingList[2]); //Hello3
     ```

     **[⬆ Back to Top](#table-of-contents)**

348. ### How do you trim a string at the beginning or ending

     The `trim` method of string prototype is used to trim on both sides of a string. But if you want to trim especially at the beginning or ending of the string then you can use `trimStart/trimLeft` and `trimEnd/trimRight` methods. Let's see an example of these methods on a greeting message,

     ```javascript
     var greeting = '   Hello, Goodmorning!   ';

     console.log(greeting); // "   Hello, Goodmorning!   "
     console.log(greeting.trimStart()); // "Hello, Goodmorning!   "
     console.log(greeting.trimLeft()); // "Hello, Goodmorning!   "

     console.log(greeting.trimEnd()); // "   Hello, Goodmorning!"
     console.log(greeting.trimRight()); // "   Hello, Goodmorning!"
     ```

     **[⬆ Back to Top](#table-of-contents)**

349. ### What is the output of below console statement with unary operator

     Let's take console statement with unary operator as given below,

     ```javascript
     console.log(+ 'Hello');
     ```

     The output of the above console log statement returns NaN. Because the element is prefixed by the unary operator and the JavaScript interpreter will try to convert that element into a number type. Since the conversion fails, the value of the statement results in NaN value.

     **[⬆ Back to Top](#table-of-contents)**

350. ### Does javascript uses mixins

     **[⬆ Back to Top](#table-of-contents)**

351. ### What is a thunk function

     A thunk is just a function which delays the evaluation of the value. It doesn’t take any arguments but gives the value whenever you invoke the thunk. i.e, It is used not to execute now but it will be sometime in the future. Let's take a synchronous example,

     ```javascript
     const add = (x,y) => x + y;

     const thunk = () => add(2,3);

     thunk() // 5
     ```

     **[⬆ Back to Top](#table-of-contents)**

352. ### What are asynchronous thunks

     The asynchronous thunks are useful to make network requests.  Let's see an example of network requests,

     ```javascript
     function fetchData(fn){
       fetch('https://jsonplaceholder.typicode.com/todos/1')
       .then(response => response.json())
       .then(json => fn(json))
     }

     const asyncThunk = function (){
        return fetchData(function getData(data){
           console.log(data)
       })
     }

     asyncThunk()
     ```

     The `getData` function won't be called immediately but it will be invoked only when the data is available from API endpoint. The setTimeout function is also used to make our code asynchronous. The best real time example is redux state management library which uses the asynchronous thunks to delay the actions to dispatch.

     **[⬆ Back to Top](#table-of-contents)**

353. ### What is the output of below function calls

     **Code snippet:**

     ```javascript
     const circle = {
       radius: 20,
       diameter() {
         return this.radius * 2;
       },
       perimeter: () => 2 * Math.PI * this.radius
     };
     ```

     console.log(circle.diameter());
     console.log(circle.perimeter());

     **Output:**

     The output is 40 and NaN. Remember that diameter is a regular function, whereas the value of perimeter is an arrow function. The `this` keyword of a regular function(i.e, diameter) refers to the surrounding scope which is a class(i.e, Shape object). Whereas this keyword of perimeter function refers to the surrounding scope which is a window object. Since there is no radius property on window objects it returns an undefined value and the multiple of number value returns NaN value.

     **[⬆ Back to Top](#table-of-contents)**

354. ### How to remove all line breaks from a string

     The easiest approach is using regular expressions to detect and replace newlines in the string. In this case, we use replace function along with string to replace with, which in our case is an empty string.

     ```javascript
     function remove_linebreaks( var message ) {
         return message.replace( /[\r\n]+/gm, "" );
     }
     ```

     In the above expression, g and m are for global and multiline flags.

     **[⬆ Back to Top](#table-of-contents)**

355. ### What is the difference between reflow and repaint

     A *repaint* occurs when changes are made which affect the visibility of an element, but not its layout. Examples of this include outline, visibility, or background color. A *reflow* involves changes that affect the layout of a portion of the page (or the whole page). Resizing the browser window, changing the font, content changing (such as user typing text), using JavaScript methods involving computed styles, adding or removing elements from the DOM, and changing an element's classes are a few of the things that can trigger reflow. Reflow of an element causes the subsequent reflow of all child and ancestor elements as well as any elements following it in the DOM.

      **[⬆ Back to Top](#table-of-contents)**

356. ### What happens with negating an array

     Negating an array with `!` character will coerce the array into a boolean. Since Arrays are considered to be truthy So negating it will return `false`.

     ```javascript
     console.log(![]); // false
     ```

     **[⬆ Back to Top](#table-of-contents)**

357. ### What happens if we add two arrays

     If you add two arrays together, it will convert them both to strings and concatenate them. For example, the result of adding arrays would be as below,

     ```javascript
     console.log(['a'] + ['b']);  // "ab"
     console.log([] + []); // ""
     console.log(![] + []); // "false", because ![] returns false.
     ```

     **[⬆ Back to Top](#table-of-contents)**

358. ### What is the output of prepend additive operator on falsy values

     If you prepend the additive(+) operator on falsy values(null, undefined, NaN, false, ""), the falsy value converts to a number value zero. Let's display them on browser console as below,

     ```javascript
     console.log(+null); // 0
     console.log(+undefined);// NaN
     console.log(+false); // 0
     console.log(+NaN); // NaN
     console.log(+""); // 0
     ```

     **[⬆ Back to Top](#table-of-contents)**

359. ### How do you create self string using special characters

     The self string can be formed with the combination of `[]()!+` characters. You need to remember the below conventions to achieve this pattern.
     1. Since Arrays are truthful values, negating the arrays will produce false: ![] === false
     2. As per JavaScript coercion rules, the addition of arrays together will toString them: [] + [] === ""
     3. Prepend an array with + operator will convert an array to false, the negation will make it true and finally converting the result will produce value '1': +(!(+[])) === 1

     By applying the above rules, we can derive below conditions

     ```javascript
     ![] + [] === "false"
     +!+[] === 1
     ```

     Now the character pattern would be created as below,

     ```javascript
           s               e               l               f
      ^^^^^^^^^^^^^   ^^^^^^^^^^^^^   ^^^^^^^^^^^^^   ^^^^^^^^^^^^^

      (![] + [])[3] + (![] + [])[4] + (![] + [])[2] + (![] + [])[0]
      ^^^^^^^^^^^^^   ^^^^^^^^^^^^^   ^^^^^^^^^^^^^   ^^^^^^^^^^^^^
     (![] + [])[+!+[]+!+[]+!+[]] +
     (![] + [])[+!+[]+!+[]+!+[]+!+[]] +
     (![] + [])[+!+[]+!+[]] +
     (![] + [])[+[]]
     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
     (![]+[])[+!+[]+!+[]+!+[]]+(![]+[])[+!+[]+!+[]+!+[]+!+[]]+(![]+[])[+!+[]+!+[]]+(![]+[])[+[]]
     ```

     **[⬆ Back to Top](#table-of-contents)**

360. ### How do you remove falsy values from an array

     You can apply the filter method on the array by passing Boolean as a parameter. This way it removes all falsy values(0, undefined, null, false and "") from the array.

     ```javascript
     const myArray = [false, null, 1,5, undefined]
     myArray.filter(Boolean); // [1, 5] // is same as myArray.filter(x => x);
     ```

     **[⬆ Back to Top](#table-of-contents)**

361. ### How do you get unique values of an array

     You can get unique values of an array with the combination of `Set` and rest expression/spread(...) syntax.

     ```javascript
     console.log([...new Set([1, 2, 4, 4, 3])]); // [1, 2, 4, 3]
     ```

     **[⬆ Back to Top](#table-of-contents)**

362. ### What is destructuring aliases

     Sometimes you would like to have a destructured variable with a different name than the property name. In that case, you'll use a `: newName` to specify a name for the variable. This process is called destructuring aliases.

     ```javascript
     const obj = { x: 1 };
     // Grabs obj.x as as { otherName }
     const { x: otherName } = obj;
     ```

     **[⬆ Back to Top](#table-of-contents)**

363. ### How do you map the array values without using map method

     You can map the array values without using the `map` method by just using the `from` method of Array. Let's map city names from Countries array,

     ```javascript
     const countries = [
         { name: 'India', capital: 'Delhi' },
         { name: 'US', capital: 'Washington' },
         { name: 'Russia', capital: 'Moscow' },
         { name: 'Singapore', capital: 'Singapore' },
         { name: 'China', capital: 'Beijing' },
         { name: 'France', capital: 'Paris' },
     ];

     const cityNames = Array.from(countries, ({ capital}) => capital);
     console.log(cityNames); // ['Delhi, 'Washington', 'Moscow', 'Singapore', 'Beijing', 'Paris']
     ```

     **[⬆ Back to Top](#table-of-contents)**

364. ### How do you empty an array

     You can empty an array quickly by setting the array length to zero.

     ```javascript
     let cities = ['Singapore', 'Delhi', 'London'];
     cities.length = 0; // cities becomes []
     ```

     **[⬆ Back to Top](#table-of-contents)**

365. ### How do you rounding numbers to certain decimals

     You can round numbers to a certain number of decimals using `toFixed` method from native javascript.

     ```javascript
     let pie = 3.141592653;
     pie = pie.toFixed(3); // 3.142
     ```

     **[⬆ Back to Top](#table-of-contents)**

366. ### What is the easiest way to convert an array to an object

     You can convert an array to an object with the same data using spread(...) operator.

     ```javascript
     var fruits = ["banana", "apple", "orange", "watermelon"];
     var fruitsObject = {...fruits};
     console.log(fruitsObject); // {0: "banana", 1: "apple", 2: "orange", 3: "watermelon"}
     ```

     **[⬆ Back to Top](#table-of-contents)**

367. ### How do you create an array with some data

     You can create an array with some data or an array with the same values using `fill` method.

     ```javascript
     var newArray = new Array(5).fill("0");
     console.log(newArray); // ["0", "0", "0", "0", "0"]
     ```

     **[⬆ Back to Top](#table-of-contents)**

368. ### What are the placeholders from console object

     Below are the list of placeholders available from console object,
     1. %o — It takes an object,
     2. %s — It takes a string,
     3. %d — It is used for a decimal or integer
     These placeholders can be represented in the console.log as below

     ```javascript
     const user = { "name":"John", "id": 1, "city": "Delhi"};
     console.log("Hello %s, your details %o are available in the object form", "John", user); // Hello John, your details {name: "John", id: 1, city: "Delhi"} are available in object
     ```

     **[⬆ Back to Top](#table-of-contents)**

369. ### Is it possible to add CSS to console messages

     Yes, you can apply CSS styles to console messages similar to html text on the web page.

     ```javascript
     console.log('%c The text has blue color, with large font and red background', 'color: blue; font-size: x-large; background: red');
     ```

     The text will be displayed as below,
     ![Screenshot](images/console-css.png)

     **Note:** All CSS styles can be applied to console messages.

     **[⬆ Back to Top](#table-of-contents)**

370. ### What is the purpose of dir method of console object

     The `console.dir()` is used to display an interactive list of the properties of the specified JavaScript object as JSON.

     ```javascript
     const user = { "name":"John", "id": 1, "city": "Delhi"};
     console.dir(user);
     ```

     The user object displayed in JSON representation
     ![Screenshot](images/console-dir.png)

     **[⬆ Back to Top](#table-of-contents)**

371. ### Is it possible to debug HTML elements in console

     Yes, it is possible to get and debug HTML elements in the console just like inspecting elements.

     ```javascript
     const element = document.getElementsByTagName("body")[0];
     console.log(element);
     ```

     It prints the HTML element in the console,
     
     ![Screenshot](images/console-html.png)

     **[⬆ Back to Top](#table-of-contents)**

372. ### How do you display data in a tabular format using console object

     The `console.table()` is used to display data in the console in a tabular format to visualize complex arrays or objects.

     ```js
     const users = [{ "name":"John", "id": 1, "city": "Delhi"}, { "name":"Max", "id": 2, "city": "London"}, { "name":"Rod", "id": 3, "city": "Paris"} ];
     console.table(users);
     ```

     The data visualized in a table format,
     
     ![Screenshot](images/console-table.png)
     **Not:** Remember that `console.table()` is not supported in IE.

     **[⬆ Back to Top](#table-of-contents)**

373. ### How do you verify that an argument is a Number or not

     The combination of IsNaN and isFinite methods are used to confirm whether an argument is a number or not.

     ```javascript
     function isNumber(n){
         return !isNaN(parseFloat(n)) && isFinite(n);
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

374. ### How do you create copy to clipboard button

     You need to select the content(using .select() method) of the input element and execute the copy command with execCommand (i.e, execCommand('copy')). You can also execute other system commands like cut and paste.

     ```javascript
     document.querySelector("#copy-button").onclick = function() {
       // Select the content
       document.querySelector("#copy-input").select();
       // Copy to the clipboard
       document.execCommand('copy');
     };
     ```

     **[⬆ Back to Top](#table-of-contents)**

375. ### What is the shortcut to get timestamp

     You can use `new Date().getTime()` to get the current timestamp. There is an alternative shortcut to get the value.

     ```javascript
     console.log(+new Date());
     console.log(Date.now());
     ```

     **[⬆ Back to Top](#table-of-contents)**

376. ### How do you flattening multi dimensional arrays

     Flattening bi-dimensional arrays is trivial with Spread operator.

     ```javascript
     const biDimensionalArr = [11, [22, 33], [44, 55], [66, 77], 88, 99];
     const flattenArr = [].concat(...biDimensionalArr); // [11, 22, 33, 44, 55, 66, 77, 88, 99]
     ```

     But you can make it work with multi-dimensional arrays by recursive calls,

     ```javascript
     function flattenMultiArray(arr) {
         const flattened = [].concat(...arr);
         return flattened.some(item => Array.isArray(item)) ? flattenMultiArray(flattened) : flattened;
      }
     const multiDimensionalArr = [11, [22, 33], [44, [55, 66, [77, [88]], 99]]];
     const flatArr = flattenMultiArray(multiDimensionalArr); // [11, 22, 33, 44, 55, 66, 77, 88, 99]
     ```

     **[⬆ Back to Top](#table-of-contents)**

377. ### What is the easiest multi condition checking

     You can use `indexOf` to compare input with multiple values instead of checking each value as one condition.

     ```javascript
     // Verbose approach
     if (input === 'first' || input === 1 || input === 'second' || input === 2) {
       someFunction();
     }
     // Shortcut
     if (['first', 1, 'second', 2].indexOf(input) !== -1) {
       someFunction();
     }
     ```

     **[⬆ Back to Top](#table-of-contents)**

378. ### How do you capture browser back button

     The `window.onbeforeunload` method is used to capture browser back button events. This is helpful to warn users about losing the current data.

     ```javascript
      window.onbeforeunload = function() {
         alert("You work will be lost");
      };
     ```

     **[⬆ Back to Top](#table-of-contents)**

379. ### How do you disable right click in the web page

     The right click on the page can be disabled by returning false from the `oncontextmenu` attribute on the body element.

     ```html
     <body oncontextmenu="return false;">
     ```

     **[⬆ Back to Top](#table-of-contents)**

380. ### What are wrapper objects

     Primitive Values like string,number and boolean don't have properties and methods but they are temporarily converted or coerced to an object(Wrapper object) when you try to perform actions on them. For example, if you apply toUpperCase() method on a primitive string value, it does not throw an error but returns uppercase of the string.

     ```javascript
     let name = "john";

     console.log(name.toUpperCase());  // Behind the scenes treated as console.log(new String(name).toUpperCase());
     ```

     i.e, Every primitive except null and undefined have Wrapper Objects and the list of wrapper objects are String,Number,Boolean,Symbol and BigInt.

     **[⬆ Back to Top](#table-of-contents)**

381. ### What is AJAX

     AJAX stands for Asynchronous JavaScript and XML and it is a group of related technologies(HTML, CSS, JavaScript, XMLHttpRequest API etc) used to display data asynchronously. i.e. We can send data to the server and get data from the server without reloading the web page.

     **[⬆ Back to Top](#table-of-contents)**

382. ### What are the different ways to deal with Asynchronous Code

     Below are the list of different ways to deal with Asynchronous code.
     1. Callbacks
     2. Promises
     3. Async/await
     4. Third-party libraries such as async.js,bluebird etc

     **[⬆ Back to Top](#table-of-contents)**

383. ### How to cancel a fetch request

     Until a few days back, One shortcoming of native promises is no direct way to cancel a fetch request. But the new `AbortController` from js specification allows you to use a signal to abort one or multiple fetch calls.
     The basic flow of cancelling a fetch request would be as below,
     1. Create an `AbortController` instance
     2. Get the signal property of an instance and pass the signal as a fetch option for signal
     3. Call the AbortController's abort property to cancel all fetches that use that signal
     For example, let's pass the same signal to multiple fetch calls will cancel all requests with that signal,

     ```javascript
     const controller = new AbortController();
     const { signal } = controller;

     fetch("http://localhost:8000", { signal }).then(response => {
         console.log(`Request 1 is complete!`);
     }).catch(e => {
         if(e.name === "AbortError") {
             // We know it's been canceled!
         }
     });

     fetch("http://localhost:8000", { signal }).then(response => {
         console.log(`Request 2 is complete!`);
     }).catch(e => {
          if(e.name === "AbortError") {
              // We know it's been canceled!
           }
     });

     // Wait 2 seconds to abort both requests
     setTimeout(() => controller.abort(), 2000);
     ```

     **[⬆ Back to Top](#table-of-contents)**

384. ### What is web speech API

     Web speech API is used to enable modern browsers recognize and synthesize speech(i.e, voice data into web apps). This API has been introduced by W3C Community in the year 2012. It has two main parts,
     1. **SpeechRecognition (Asynchronous Speech Recognition or Speech-to-Text):** It provides the ability to recognize voice context from an audio input and respond accordingly. This is accessed by the `SpeechRecognition` interface.
     The below example shows on how to use this API to get text from speech,

     ```javascript
     window.SpeechRecognition = window.webkitSpeechRecognition || window.SpeechRecognition;  // webkitSpeechRecognition for Chrome and SpeechRecognition for FF
     const recognition = new window.SpeechRecognition();
     recognition.onresult = (event) => { // SpeechRecognitionEvent type
       const speechToText = event.results[0][0].transcript;
       console.log(speechToText);
     }
     recognition.start();
     ```

     In this API, browser is going to ask you for permission to use your microphone
     1. **SpeechSynthesis (Text-to-Speech):** It provides the ability to recognize voice context from an audio input and respond. This is accessed by the `SpeechSynthesis` interface.
     For example, the below code is used to get voice/speech from text,

     ```javascript
     if('speechSynthesis' in window){
         var speech = new SpeechSynthesisUtterance('Hello World!');
         speech.lang = 'en-US';
         window.speechSynthesis.speak(speech);
     }
     ```

     The above examples can be tested on chrome(33+) browser's developer console.
     **Note:**  This API is still a working draft and only available in Chrome and Firefox browsers(ofcourse Chrome only implemented the specification)
     **[⬆ Back to Top](#table-of-contents)**

385. ### What is minimum timeout throttling

     Both browser and NodeJS javascript environments throttles with a minimum delay that is greater than 0ms. That means even though setting a delay of 0ms will not happen instantaneously.
     **Browsers:** They have a minimum delay of 4ms. This throttle occurs when successive calls are triggered due to callback nesting(certain depth) or after a certain number of successive intervals.
     Note: The older browsers have a minimum delay of 10ms.
     **Nodejs:** They have a minimum delay of 1ms. This throttle happens when the delay is larger than 2147483647 or less than 1.
     The best example to explain this timeout throttling behavior is the order of below code snippet.

     ```javascript
     function runMeFirst() {
         console.log('My script is initialized');
     }
     setTimeout(runMeFirst, 0);
     console.log('Script loaded');
     ```

     and the output would be in

     ```cmd
     Script loaded
     My script is initialized
     ```

     If you don't use `setTimeout`, the order of logs will be sequential.

     ```javascript
     function runMeFirst() {
        console.log('My script is initialized');
     }
     runMeFirst();
     console.log('Script loaded');
     ```

     and the output is,

     ```cmd
     My script is initialized
     Script loaded
     ```

     **[⬆ Back to Top](#table-of-contents)**

386. ### How do you implement zero timeout in modern browsers

     You can't use setTimeout(fn, 0) to execute the code immediately due to minimum delay of greater than 0ms. But you can use window.postMessage() to achieve this behavior.

     **[⬆ Back to Top](#table-of-contents)**

387. ### What are tasks in event loop

     A task is any javascript code/program which is scheduled to be run by the standard mechanisms such as initially starting to run a program, run an event callback, or an interval or timeout being fired. All these tasks are scheduled on a task queue.
     Below are the list of use cases to add tasks to the task queue,
     1. When a new javascript program is executed directly from console or running by the ```<script>``` element, the task will be added to the task queue.
     2. When an event fires, the event callback added to task queue
     3. When a setTimeout or setInterval is reached, the corresponding callback added to task queue

     **[⬆ Back to Top](#table-of-contents)**

388. ### What is microtask

     Microtask is the javascript code which needs to be executed immediately after the currently executing task/microtask is completed. They are kind of blocking in nature. i.e, The main thread will be blocked until the microtask queue is empty.
     The main sources of microtasks are Promise.resolve, Promise.reject, MutationObservers, IntersectionObservers etc

     **Note:** All of these microtasks are processed in the same turn of the event loop.
     **[⬆ Back to Top](#table-of-contents)**

389. ### What are different event loops

     **[⬆ Back to Top](#table-of-contents)**

390. ### What is the purpose of queueMicrotask

     **[⬆ Back to Top](#table-of-contents)**

391. ### How do you use javascript libraries in typescript file

     It is known that not all JavaScript libraries or frameworks have TypeScript declaration files. But if you still want to use libraries or frameworks in our TypeScript files without getting compilation errors, the only solution is `declare` keyword along with a variable declaration. For example, let's imagine you have a library called `customLibrary` that doesn’t have a TypeScript declaration and have a namespace called `customLibrary` in the global namespace. You can use this library in typescript code as below,

     ```javascript
     declare var customLibrary;
     ```

     In the runtime, typescript will provide the type to the `customLibrary` variable as `any` type. The another alternative without using declare keyword is below

     ```javascript
     var customLibrary: any;
     ```

     **[⬆ Back to Top](#table-of-contents)**

392. ### What are the differences between promises and observables

     Some of the major difference in a tabular form

     | Promises | Observables |
     |---- | ---------
     | Emits only a single value at a time  | Emits multiple values over a period of time(stream of values ranging from 0 to multiple) |
     | Eager in nature; they are going to be called immediately  | Lazy in nature; they require subscription to be invoked |
     | Promise is always asynchronous even though it resolved immediately | Observable can be either synchronous or asynchronous|
     | Doesn't provide any operators | Provides operators such as map, forEach, filter, reduce, retry, and retryWhen etc |
     | Cannot be canceled | Canceled by using unsubscribe() method |

     **[⬆ Back to Top](#table-of-contents)**

393. ### What is heap

     Heap(Or memory heap) is the memory location where objects are stored when we define variables. i.e, This is the place where all the memory allocations and de-allocation take place. Both heap and call-stack are two containers of JS runtime.
     Whenever runtime comes across variables and function declarations in the code it stores them in the Heap.

     ![Screenshot](images/heap.png)

     **[⬆ Back to Top](#table-of-contents)**

394. ### What is an event table

     Event Table is a data structure that stores and keeps track of all the events which will be executed asynchronously like after some time interval or after the resolution of some API requests. i.e Whenever you call a setTimeout function or invoke async operation, it is added to the Event Table.
     It doesn't not execute functions on it’s own. The main purpose of the event table is to keep track of events and send them to the Event Queue as shown in the below diagram.

     ![Screenshot](images/event-table.png)

     **[⬆ Back to Top](#table-of-contents)**

395. ### What is a microTask queue

     Microtask Queue is the new queue where all the tasks initiated by promise objects get processed before the callback queue.
     The microtasks queue are processed before the next rendering and painting jobs. But if these microtasks are running for a long time then it leads to visual degradation.

     **[⬆ Back to Top](#table-of-contents)**

396. ### What is the difference between shim and polyfill

     A shim is a library that brings a new API to an older environment, using only the means of that environment.  It isn't necessarily restricted to a web application. For example, es5-shim.js is used to emulate ES5 features on older browsers (mainly pre IE9).
     Whereas polyfill is a piece of code (or plugin) that provides the technology that you, the developer, expect the browser to provide natively.
     In a simple sentence, A polyfill is a shim for a browser API.

     **[⬆ Back to Top](#table-of-contents)**

397. ### How do you detect primitive or non primitive value type

     In JavaScript, primitive types include boolean, string, number, BigInt, null, Symbol and undefined. Whereas non-primitive types include the Objects. But you can easily identify them with the below function,

     ```javascript
     var myPrimitive = 30;
     var myNonPrimitive = {};
     function isPrimitive(val) {
         return Object(val) !== val;
     }

     isPrimitive(myPrimitive);
     isPrimitive(myNonPrimitive);
     ```

     If the value is a primitive data type, the Object constructor creates a new wrapper object for the value. But If the value is a non-primitive data type (an object), the Object constructor will give the same object.

     **[⬆ Back to Top](#table-of-contents)**

398. ### What is babel

     Babel is a JavaScript transpiler to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript in current and older browsers or environments. Some of the main features are listed below,
     1. Transform syntax
     2. Polyfill features that are missing in your target environment (using @babel/polyfill)
     3. Source code transformations (or codemods)

     **[⬆ Back to Top](#table-of-contents)**

399. ### Is Node.js completely single threaded

     Node is a single thread, but some of the functions included in the Node.js standard library(e.g, fs module functions) are not single threaded. i.e, Their logic runs outside of the Node.js single thread to improve the speed and performance of a program.

     **[⬆ Back to Top](#table-of-contents)**

400. ### What are the common use cases of observables

     Some of the most common use cases of observables are web sockets with push notifications, user input changes, repeating intervals, etc

     **[⬆ Back to Top](#table-of-contents)**

401. ### What is RxJS

     RxJS (Reactive Extensions for JavaScript) is a library for implementing reactive programming using observables that makes it easier to compose asynchronous or callback-based code. It also provides utility functions for creating and working with observables.

     **[⬆ Back to Top](#table-of-contents)**

402. ### What is the difference between Function constructor and function declaration

     The functions which are created with `Function constructor` do not create closures to their creation contexts but they are always created in the global scope. i.e, the function can access its own local variables and global scope variables only. Whereas function declarations can access outer function variables(closures) too.

     Let's see this difference with an example,

     **Function Constructor:**

     ```javascript
     var a = 100;
     function createFunction() {
         var a = 200;
         return new Function('return a;');
     }
     console.log(createFunction()()); // 100
     ```

     **Function declaration:**

     ```javascript
     var a = 100;
     function createFunction() {
         var a = 200;
         return function func() {
             return a;
         }
     }
     console.log(createFunction()()); // 200
     ```

     **[⬆ Back to Top](#table-of-contents)**

403. ### What is a Short circuit condition

     Short circuit conditions are meant for condensed way of writing simple if statements. Let's demonstrate the scenario using an example. If you would like to login to a portal with an authentication condition, the expression would be as below,

     ```javascript
     if (authenticate) {
        loginToPorta();
     }
     ```

     Since the javascript logical operators evaluated from left to right, the above expression can be simplified using && logical operator

     ```javascript
     authenticate && loginToPorta();
     ```

     **[⬆ Back to Top](#table-of-contents)**

404. ### What is the easiest way to resize an array

     The length property of an array is useful to resize or empty an array quickly. Let's apply length property on number array to resize the number of elements from 5 to 2,

     ```javascript
     var array = [1, 2, 3, 4, 5];
     console.log(array.length); // 5

     array.length = 2;
     console.log(array.length); // 2
     console.log(array); // [1,2]
     ```

     and the array can be emptied too

     ```javascript
     var array = [1, 2, 3, 4, 5];
     array.length = 0;
     console.log(array.length); // 0
     console.log(array); // []
     ```

     **[⬆ Back to Top](#table-of-contents)**

405. ### What is an observable

     An Observable is basically a function that can return a stream of values either synchronously or asynchronously to an observer over time. The consumer can get the value by calling `subscribe()` method.
     Let's look at a simple example of an Observable

     ```javascript
     import { Observable } from 'rxjs';

     const observable = new Observable(observer => {
       setTimeout(() => {
         observer.next('Message from a Observable!');
       }, 3000);
     });

     observable.subscribe(value => console.log(value));
     ```

     ![Screenshot](images/observables.png)

     **Note:** Observables are not part of the JavaScript language yet but they are being proposed to be added to the language

     **[⬆ Back to Top](#table-of-contents)**

406. ### What is the difference between function and class declarations

     The main difference between function declarations and class declarations is `hoisting`. The function declarations are hoisted but not class declarations.

     **Classes:**

     ```javascript
     const user = new User(); // ReferenceError

     class User {}
     ```

     **Constructor Function:**

     ```javascript
      const user = new User(); // No error

      function User() {
      }
     ```

     **[⬆ Back to Top](#table-of-contents)**

407. ### What is an async function

     An async function is a function declared with the `async` keyword which enables asynchronous, promise-based behavior to be written in a cleaner style by avoiding promise chains. These functions can contain zero or more `await` expressions.

     Let's take a below async function example,

     ```javascript
     async function logger() {

       let data = await fetch('http://someapi.com/users'); // pause until fetch returns
       console.log(data)
     }
     logger();
     ```

     It is basically syntax sugar over ES2015 promises and generators.

     **[⬆ Back to Top](#table-of-contents)**

408. ### How do you prevent promises swallowing errors

     While using asynchronous code, JavaScript’s ES6 promises can make your life a lot easier without having callback pyramids and error handling on every second line. But Promises have some pitfalls and the biggest one is swallowing errors by default.

     Let's say you expect to print an error to the console for all the below cases,

      ```javascript
      Promise.resolve('promised value').then(function() {
            throw new Error('error');
      });

      Promise.reject('error value').catch(function() {
            throw new Error('error');
      });

      new Promise(function(resolve, reject) {
            throw new Error('error');
      });
      ```

      But there are many modern JavaScript environments that won't print any errors. You can fix this problem in different ways,

     1. **Add catch block at the end of each chain:** You can add catch block to the end of each of your promise chains

         ```javascript
         Promise.resolve('promised value').then(function() {
             throw new Error('error');
         }).catch(function(error) {
           console.error(error.stack);
         });
          ```

        But it is quite difficult to type for each promise chain and verbose too.

     2. **Add done method:** You can replace first solution's then and catch blocks with done method

         ```javascript
         Promise.resolve('promised value').done(function() {
             throw new Error('error');
         });
         ```

        Let's say you want to fetch data using HTTP and later perform processing on the resulting data asynchronously. You can write `done` block as below,

         ```javascript
         getDataFromHttp()
           .then(function(result) {
             return processDataAsync(result);
           })
           .done(function(processed) {
             displayData(processed);
           });
         ```

         In future, if the processing library API changed to synchronous then you can remove `done` block as below,

         ```javascript
          getDataFromHttp()
            .then(function(result) {
              return displayData(processDataAsync(result));
            })
         ```

         and then you forgot to add `done` block to `then` block leads to silent errors.

     3. **Extend ES6 Promises by Bluebird:**
         Bluebird extends the ES6 Promises API to avoid the issue in the second solution. This library has a “default” onRejection handler which will print all errors from rejected Promises to stderr. After installation, you can process unhandled rejections

         ```javascript
         Promise.onPossiblyUnhandledRejection(function(error){
             throw error;
         });
         ```

         and discard a rejection, just handle it with an empty catch

         ```javascript
         Promise.reject('error value').catch(function() {});
         ```

     **[⬆ Back to Top](#table-of-contents)**

409. ### What is deno

     Deno is a simple, modern and secure runtime for JavaScript and TypeScript that uses V8 JavaScript engine and the Rust programming language.

     **[⬆ Back to Top](#table-of-contents)**

410. ### How do you make an object iterable in javascript

     By default, plain objects are not iterable. But you can make the object iterable by defining a `Symbol.iterator` property on it.

     Let's demonstrate this with an example,

     ```javascript
     const collection = {
       one: 1,
       two: 2,
       three: 3,
       [Symbol.iterator]() {
         const values = Object.keys(this);
         let i = 0;
         return {
           next: () => {
             return {
               value: this[values[i++]],
               done: i > values.length
             }
           }
         };
       }
     };

     const iterator = collection[Symbol.iterator]();

     console.log(iterator.next());    // → {value: 1, done: false}
     console.log(iterator.next());    // → {value: 2, done: false}
     console.log(iterator.next());    // → {value: 3, done: false}
     console.log(iterator.next());    // → {value: undefined, done: true}
     ```

     The above process can be simplified using a generator function,

     ```javascript
      const collection = {
        one: 1,
        two: 2,
        three: 3,
        [Symbol.iterator]: function * () {
          for (let key in this) {
            yield this[key];
          }
        }
      };
      const iterator = collection[Symbol.iterator]();
      console.log(iterator.next());    // {value: 1, done: false}
      console.log(iterator.next());    // {value: 2, done: false}
      console.log(iterator.next());    // {value: 3, done: false}
      console.log(iterator.next());    // {value: undefined, done: true}
     ```

     **[⬆ Back to Top](#table-of-contents)**

411. ### What is a Proper Tail Call

     First, we should know about tail call before talking about "Proper Tail Call". A tail call is a subroutine or function call performed as the final action of a calling function. Whereas **Proper tail call(PTC)** is a technique where the program or code will not create additional stack frames for a recursion when the function call is a tail call.

     For example, the below classic or head recursion of factorial function relies on stack for each step. Each step need to be processed upto `n * factorial(n - 1)`

     ```javascript
     function factorial(n) {
       if (n === 0) {
         return 1
       }
       return n * factorial(n - 1)
     }
     console.log(factorial(5)); //120
     ```

     But if you use Tail recursion functions, they keep passing all the necessary data it needs down the recursion without relying on the stack.

     ```javascript
     function factorial(n, acc = 1) {
       if (n === 0) {
         return acc
       }
       return factorial(n - 1, n * acc)
     }
     console.log(factorial(5)); //120
     ```

     The above pattern returns the same output as the first one. But the accumulator keeps track of total as an argument without using stack memory on recursive calls.

     **[⬆ Back to Top](#table-of-contents)**

412. ### How do you check an object is a promise or not

      If you don't know if a value is a promise or not, wrapping the value as `Promise.resolve(value)` which returns a promise

      ```javascript
         function isPromise(object){
            if(Promise && Promise.resolve){
            return Promise.resolve(object) == object;
            }else{
            throw "Promise not supported in your environment"
            }
         }

         var i = 1;
         var promise = new Promise(function(resolve,reject){
            resolve()
         });

         console.log(isPromise(i)); // false
         console.log(isPromise(p)); // true
      ```

      Another way is to check for `.then()` handler type

      ```javascript
      function isPromise(value) {
         return Boolean(value && typeof value.then === 'function');
      }
      var i = 1;
      var promise = new Promise(function(resolve,reject){
         resolve()
      });

      console.log(isPromise(i)) // false
      console.log(isPromise(promise)); // true
      ```

      **[⬆ Back to Top](#table-of-contents)**

413. ### How to detect if a function is called as constructor

      You can use `new.target` pseudo-property to detect whether a function was called as a constructor(using the new operator) or as a regular function call.

      1. If a constructor or function invoked using the new operator, new.target returns a reference to the constructor or function.
      2. For function calls, new.target is undefined.

      ```javascript
      function Myfunc() {
         if (new.target) {
            console.log('called with new');
         } else {
            console.log('not called with new');
         }
      }

      new Myfunc(); // called with new
      Myfunc(); // not called with new
      Myfunc.call({}); not called with new
      ```

     **[⬆ Back to Top](#table-of-contents)**

414. ### What are the differences between arguments object and rest parameter

     There are three main differences between arguments object and rest parameters

     1. The arguments object is an array-like but not an array. Whereas the rest parameters are array instances.
     2. The arguments object does not support methods such as sort, map, forEach, or pop. Whereas these methods can be used in rest parameters.
     3. The rest parameters are only the ones that haven’t been given a separate name, while  the arguments object contains all arguments passed to the function

     **[⬆ Back to Top](#table-of-contents)**

415. ### What are the differences between spread operator and rest parameter

     Rest parameter collects all remaining elements into an array. Whereas Spread operator allows iterables( arrays / objects / strings ) to be expanded into single arguments/elements. i.e, Rest parameter is opposite to the spread operator.

     **[⬆ Back to Top](#table-of-contents)**

416. ### What are the different kinds of generators

     There are five kinds of generators,

     1. **Generator function declaration:**

         ```javascript
          function* myGenFunc() {
               yield 1;
               yield 2;
               yield 3;
          }
          const genObj = myGenFunc();
         ```

     2. **Generator function expressions:**

        ```javascript
        const myGenFunc = function* () {
               yield 1;
               yield 2;
               yield 3;
        };
        const genObj = myGenFunc();
        ```

     3. **Generator method definitions in object literals:**

        ```javascript
         const myObj = {
             * myGeneratorMethod() {
                yield 1;
                yield 2;
                yield 3;
             }
         };
         const genObj = myObj.myGeneratorMethod();
        ```

     4. **Generator method definitions in class:**

        ```javascript
          class MyClass {
             * myGeneratorMethod() {
                yield 1;
                yield 2;
                yield 3;
             }
          }
          const myObject = new MyClass();
          const genObj = myObject.myGeneratorMethod();
        ```

     5. **Generator as a computed property:**

        ```javascript
        const SomeObj = {
          *[Symbol.iterator] () {
            yield 1;
            yield 2;
            yield 3;
          }
        }

        console.log(Array.from(SomeObj)); // [ 1, 2, 3 ]
        ```

     **[⬆ Back to Top](#table-of-contents)**

417. ### What are the built-in iterables

     Below are the list of built-in iterables in javascript,

     1. Arrays and TypedArrays
     2. Strings: Iterate over each character or Unicode code-points
     3. Maps: iterate over its key-value pairs
     4. Sets: iterates over their elements
     5. arguments: An array-like special variable in functions
     6. DOM collection such as NodeList

     **[⬆ Back to Top](#table-of-contents)**

418. ### What are the differences between for...of and for...in statements

     Both for...in and for...of statements iterate over js data structures. The only difference is over what they iterate:

     1. for..in iterates over all enumerable property keys of an object
     2. for..of iterates over the values of an iterable object.

     Let's explain this difference with an example,

     ```javascript
     let arr = ['a', 'b', 'c'];

     arr.newProp = 'newVlue';

     // key are the property keys
     for (let key in arr) {
       console.log(key);
     }

     // value are the property values
     for (let value of arr) {
       console.log(value);
     }
     ```

     Since for..in loop iterates over the keys of the object, the first loop logs 0, 1, 2 and newProp while iterating over the array object. The for..of loop iterates over the values of a arr data structure and logs  a, b, c in the console.

     **[⬆ Back to Top](#table-of-contents)**

419. ### How do you define instance and non-instance properties

     The Instance properties must be defined inside of class methods. For example, name and age properties defined insider constructor as below,

     ```javascript
     class Person {
       constructor(name, age) {
         this.name = name;
         this.age = age;
       }
     }
     ```

     But Static(class) and prototype data properties must be defined outside of the ClassBody declaration. Let's assign the age value for Person class as below,

     ```javascript
     Person.staticAge = 30;
     Person.prototype.prototypeAge = 40;
     ```

     **[⬆ Back to Top](#table-of-contents)**

420. ### What is the difference between isNaN and Number.isNaN?

     1. **isNaN**: The global function `isNaN` converts the argument to a Number and returns true if the resulting value is NaN.
     2. **Number.isNaN**: This method does not convert the argument. But it returns true when the type is a Number and value is NaN.

     Let's see the difference with an example,

     ```javascript
     isNaN(‘hello’);   // true
     Number.isNaN('hello'); // false
     ```
     
     **[⬆ Back to Top](#table-of-contents)**
     
421. ### How to invoke an IIFE without any extra brackets?
     Immediately Invoked Function Expressions(IIFE) requires a pair of parenthesis to wrap the function which contains set of statements.
     ```js
     (function(dt) { 
        console.log(dt.toLocaleTimeString()); 
      })(new Date()); 
     ```
     Since both IIFE and void operator discard the result of an expression, you can avoid the extra brackets using `void operator` for IIFE  as below,
     ```js
      void function(dt) { 
        console.log(dt.toLocaleTimeString()); 
      }(new Date()); 
     ```

    **[⬆ Back to Top](#table-of-contents)**

422. ### Is that possible to use expressions in switch cases?
     You might have seen expressions used in switch condition but it is also possible to use for switch cases by assigning true value for the switch condition. Let's see the weather condition based on temparature as an example,
     ```js
     const weather = function getWeather(temp) {
        switch(true) {
            case temp < 0: return 'freezing';
            case temp < 10: return 'cold';
            case temp < 24: return 'cool';
            default: return 'unknown';
        }
        }(10);
     ```
     
    **[⬆ Back to Top](#table-of-contents)**
         
423. ### What is the easiest way to ignore promise errors?    
     The easiest and safest way to ignore promise errors is void that error. This approach is ESLint friendly too.
     
     ```js
     await promise.catch(e => void e);
     ```
     **[⬆ Back to Top](#table-of-contents)**
     
424. ### How do style the console output using CSS?

     You can add CSS styling to the console output using the CSS format content specifier %c. The console string message can be appended after the specifier and CSS style in another argument. Let's print the red the color text using console.log and CSS specifier as below,
     ```js
     console.log("%cThis is a red text", "color:red");
     ```
    
     It is also possible to add more styles for the content. For example, the font-size can be modified for the above text
     ```js
     console.log("%cThis is a red text with bigger font", "color:red; font-size:20px");
     ```
     **[⬆ Back to Top](#table-of-contents)**
         
### Coding Exercise

#### 1. What is the output of below code

```javascript
var car = new Vehicle("Honda", "white", "2010", "UK");
console.log(car);

function Vehicle(model, color, year, country) {
    this.model = model;
    this.color = color;
    this.year = year;
    this.country = country;
}
```

- 1: Undefined
- 2: ReferenceError
- 3: null
- 4: {model: "Honda", color: "white", year: "2010", country: "UK"}

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

   The function declarations are hoisted similar to any variables. So the placement for `Vehicle` function declaration doesn't make any difference.

</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 2. What is the output of below code

```javascript
function foo() {
    let x = y = 0;
    x++;
    y++;
    return x;
}

console.log(foo(), typeof x, typeof y);
```

- 1: 1, undefined and undefined
- 2: ReferenceError: X is not defined
- 3: 1, undefined and number
- 4: 1, number and number

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 3

Of course the return value of `foo()` is 1 due to the increment operator. But the statement `let x = y = 0` declares a local variable x. Whereas y declared as a global variable accidentally. This statement is equivalent to,

```javascript
 let x;
 window.y = 0;
 x = window.y;
```

Since the block scoped variable x is undefined outside of the function, the type will be undefined too. Whereas the global variable `y` is available outside the function, the value is 0 and type is number.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 3. What is the output of below code

```javascript
function main(){
   console.log('A');
   setTimeout(
      function print(){ console.log('B'); }
   ,0);
   console.log('C');
}
main();
```

- 1: A, B and C
- 2: B, A and C
- 3: A and C
- 4: A, C and B

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

The statements order is based on the event loop mechanism. The order of statements follows the below order,

1. At first, the main function is pushed to the stack.
2. Then the browser pushes the fist statement of the main function( i.e, A's console.log) to the stack, executing and popping out immediately.
3. But `setTimeout` statement moved to Browser API to apply the delay for callback.
4. In the meantime, C's console.log added to stack, executed and popped out.
5. The callback of `setTimeout` moved from Browser API to message queue.
6. The `main` function popped out from stack because there are no statements to execute
7. The callback moved from message queue to the stack since the stack is empty.
8. The console.log for B is added to the stack and display on the console.

</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 4. What is the output of below equality check

```javascript
console.log(0.1 + 0.2 === 0.3);
```

- 1: false
- 2: true

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

This is due to the float point math problem. Since the floating point numbers are encoded in binary format, the addition operations on them lead to rounding errors. Hence, the comparison of floating points doesn't give expected results.
You can find more details about the explanation here [0.30000000000000004.com/](https://0.30000000000000004.com/)

</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 5. What is the output of below code

```javascript
var y = 1;
  if (function f(){}) {
    y += typeof f;
  }
  console.log(y);
```

- 1: 1function
- 2: 1object
- 3: ReferenceError
- 4: 1undefined

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

The main points in the above code snippets are,

1. You can see function expression instead function declaration inside if statement. So it always returns true.
2. Since it is not declared(or assigned) anywhere, f is undefined and typeof f is undefined too.

In other words, it is same as

```javascript
var y = 1;
  if ('foo') {
    y += typeof f;
  }
  console.log(y);
```

**Note:** It returns 1object for MS Edge browser
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 6. What is the output of below code

```javascript
function foo() {
  return
  {
    message: "Hello World"
  };
}
console.log(foo());
```

- 1: Hello World
- 2: Object {message: "Hello World"}
- 3: Undefined
- 4: SyntaxError

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 3

This is a semicolon issue. Normally semicolons are optional in JavaScript. So if there are any statements(in this case, return) missing semicolon, it is automatically inserted immediately. Hence, the function returned as undefined.

Whereas if the opening curly brace is along with the return keyword then the function is going to be returned as expected.

```javascript
function foo() {
  return {
    message: "Hello World"
  };
}
console.log(foo()); // {message: "Hello World"}
```

</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 7. What is the output of below code

```javascript
var myChars = ['a', 'b', 'c', 'd']
delete myChars[0];
console.log(myChars);
console.log(myChars[0]);
console.log(myChars.length);
```

- 1: [empty, 'b', 'c', 'd'], empty, 3
- 2: [null, 'b', 'c', 'd'], empty, 3
- 3: [empty, 'b', 'c', 'd'], undefined, 4
- 4: [null, 'b', 'c', 'd'], undefined, 4

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 3

The `delete` operator will delete the object property but it will not reindex the array or change its length. So the number or elements or length of the array won't be changed.
If you try to print myChars then you can observe that it doesn't set an undefined value, rather the property is removed from the array. The newer versions of Chrome use `empty` instead of `undefined` to make the difference a bit clearer.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 8. What is the output of below code in latest Chrome

```javascript
var array1 = new Array(3);
console.log(array1);

var array2 = [];
array2[2] = 100;
console.log(array2);

var array3 = [,,,];
console.log(array3);
```

- 1: [undefined × 3], [undefined × 2, 100], [undefined × 3]
- 2: [empty × 3], [empty × 2, 100], [empty × 3]
- 3: [null × 3], [null × 2, 100], [null × 3]
- 4: [], [100], []

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

The latest chrome versions display `sparse array`(they are filled with holes) using this empty x n notation. Whereas the older versions have undefined x n notation.
**Note:** The latest version of FF displays `n empty slots` notation.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 9. What is the output of below code

```javascript
const obj = {
  prop1: function() { return 0 },
  prop2() { return 1 },
  ['prop' + 3]() { return 2 }
}

console.log(obj.prop1());
console.log(obj.prop2());
console.log(obj.prop3());
```

- 1: 0, 1, 2
- 2: 0, { return 1 }, 2
- 3: 0, { return 1 }, { return 2 }
- 4: 0, 1, undefined

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

ES6 provides method definitions and property shorthands for objects. So both prop2 and prop3 are treated as regular function values.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 10. What is the output of below code

```javascript
console.log(1 < 2 < 3);
console.log(3 > 2 > 1);
```

- 1: true, true
- 2: true, false
- 3: SyntaxError, SyntaxError,
- 4: false, false

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

The important point is that if the statement contains the same operators(e.g, < or >) then it can be evaluated from left to right.
The first statement follows the below order,

1. console.log(1 < 2 < 3);
2. console.log(true < 3);
3. console.log(1 < 3); // True converted as `1` during comparison
4. True

Whereas the second statement follows the below order,

1. console.log(3 > 2 > 1);
2. console.log(true > 1);
3. console.log(1 > 1); // False converted as `0` during comparison
4. False

</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 11. What is the output of below code in non-strict mode

```javascript
function printNumbers(first, second, first) {
  console.log(first, second, first);
}
printNumbers(1, 2, 3);
```

- 1: 1, 2, 3
- 2: 3, 2, 3
- 3: SyntaxError: Duplicate parameter name not allowed in this context
- 4: 1, 2, 1

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

In non-strict mode, the regular JavaScript functions allow duplicate named parameters. The above code snippet has duplicate parameters on 1st and 3rd parameters.
The value of the first parameter is mapped to the third argument which is passed to the function. Hence, the 3rd argument overrides the first parameter.

**Note:** In strict mode, duplicate parameters will throw a Syntax Error.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 12. What is the output of below code

```javascript
const printNumbersArrow = (first, second, first) => {
  console.log(first, second, first);
}
printNumbersArrow(1, 2, 3);
```

- 1: 1, 2, 3
- 2: 3, 2, 3
- 3: SyntaxError: Duplicate parameter name not allowed in this context
- 4: 1, 2, 1

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 3

Unlike regular functions, the arrow functions doesn't not allow duplicate parameters in either strict or non-strict mode. So you can see `SyntaxError` in the console.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 13. What is the output of below code

```javascript
const arrowFunc = () => arguments.length;
console.log(arrowFunc(1, 2, 3));
```

- 1: ReferenceError: arguments is not defined
- 2: 3
- 3: undefined
- 4: null

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

Arrow functions do not have an `arguments, super, this, or new.target` bindings. So any reference to `arguments` variable tries to resolve to a binding in a lexically enclosing environment. In this case, the arguments variable is not defined outside of the arrow function. Hence, you will receive a reference error.

Where as the normal function provides the number of arguments passed to the function

```javascript
const func = function () {
                    return arguments.length;
                    }
console.log(func(1, 2, 3));
```

But If you still want to use an arrow function then rest operator on arguments provides the expected arguments

```javascript
const arrowFunc = (...args) => args.length;
console.log(arrowFunc(1, 2, 3));
```

</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 14. What is the output of below code

```javascript
console.log( String.prototype.trimLeft.name === 'trimLeft' );
console.log( String.prototype.trimLeft.name === 'trimStart' );
```

- 1: True, False
- 2: False, True

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

In order to be consistent with functions like `String.prototype.padStart`, the standard method name for trimming the whitespaces is considered as `trimStart`. Due to web web compatibility reasons, the old method name 'trimLeft' still acts as an alias for 'trimStart'. Hence, the prototype for 'trimLeft' is always 'trimStart'
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 15. What is the output of below code

```javascript
console.log(Math.max());
```

- 1: undefined
- 2: Infinity
- 3: 0
- 4: -Infinity

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

-Infinity is the initial comparant because almost every other value is bigger. So when no arguments are provided, -Infinity is going to be returned.
**Note:** Zero number of arguments is a valid case.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 16. What is the output of below code

```javascript
console.log(10 == [10]);
console.log(10 == [[[[[[[10]]]]]]]);
```

- 1: True, True
- 2: True, False
- 3: False, False
- 4: False, True

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1
As per the comparison algorithm in the ECMAScript specification(ECMA-262), the above expression converted into JS as below
```javascript
10 === Number([10].valueOf().toString()) // 10
```
So it doesn't matter about number brackets([]) around the number, it is always converted to a number in the expression.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 17. What is the output of below code

```javascript
console.log(10 + '10');
console.log(10 - '10');
```

- 1: 20, 0
- 2: 1010, 0
- 3: 1010, 10-10
- 4: NaN, NaN

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

The concatenation operator(+) is applicable for both number and string types. So if any operand is string type then both operands concatenated as strings. Whereas subtract(-) operator tries to convert the operands as number type.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 18. What is the output of below code

```javascript
console.log([0] == false);
if([0]) {
console.log("I'm True");
} else {
console.log("I'm False");
}

```

- 1: True, I'm True
- 2: True, I'm False
- 3: False, I'm True
- 4: False, I'm False

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

In comparison operators, the expression `[0]` converted to Number([0].valueOf().toString()) which is resolved to false. Whereas `[0]` just becomes a truthy value without any conversion because there is no comparison operator.
</p>
</details>

#### 19. What is the output of below code

```javascript
console.log([1, 2] + [3, 4]);
```

- 1: [1,2,3,4]
- 2: [1,2][3,4]
- 3: SyntaxError
- 4: 1,23,4

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

The + operator is not meant or defined for arrays. So it converts arrays into strings and concatenates them.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 20. What is the output of below code

```javascript
const numbers = new Set([1, 1, 2, 3, 4]);
console.log(numbers);

const browser = new Set('Firefox');
console.log(browser);
```

- 1: {1, 2, 3, 4}, {"F", "i", "r", "e", "f", "o", "x"}
- 2: {1, 2, 3, 4}, {"F", "i", "r", "e", "o", "x"}
- 3: [1, 2, 3, 4], ["F", "i", "r", "e", "o", "x"]
- 4: {1, 1, 2, 3, 4}, {"F", "i", "r", "e", "f", "o", "x"}

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

Since `Set` object is a collection of unique values, it won't allow duplicate values in the collection. At the same time, it is case sensitive data structure.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 21. What is the output of below code

```javascript
console.log(NaN === NaN);
```

- 1: True
- 2: False

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

JavaScript follows IEEE 754 spec standards. As per this spec, NaNs are never equal for floating-point numbers.
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 22. What is the output of below code

```javascript
let numbers = [1, 2, 3, 4, NaN];
console.log(numbers.indexOf(NaN));
```

- 1: 4
- 2: NaN
- 3: SyntaxError
- 4: -1

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

The `indexOf` uses strict equality operator(===) internally and `NaN === NaN` evaluates to false. Since indexOf won't be able to find NaN inside an array, it returns -1 always.
But you can use `Array.prototype.findIndex` method to find out the index of NaN in an array or You can use `Array.prototype.includes` to check if NaN is present in an array or not.

```javascript
let numbers = [1, 2, 3, 4, NaN];
console.log(numbers.findIndex(Number.isNaN)); // 4

console.log(numbers.includes(Number.isNaN)); // true
```

</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 23. What is the output of below code

```javascript
let [a, ...b,] = [1, 2, 3, 4, 5];
console.log(a, b);
```

- 1: 1, [2, 3, 4, 5]
- 2: 1, {2, 3, 4, 5}
- 3: SyntaxError
- 4: 1, [2, 3, 4]

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 3

When using rest parameters, trailing commas are not allowed and will throw a SyntaxError.
If you remove the trailing comma then it displays 1st answer

```javascript
let [a, ...b] = [1, 2, 3, 4, 5];
console.log(a, b); // 1, [2, 3, 4, 5]
```

</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 25. What is the output of below code

```javascript
async function func() {
   return 10;
}
console.log(func());
```

- 1: Promise {\<fulfilled\>: 10}
- 2: 10
- 3: SyntaxError
- 4: Promise {\<rejected\>: 10}

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

Async functions always return a promise. But even if the return value of an async function is not explicitly a promise, it will be implicitly wrapped in a promise. The above async function is equivalent to below expression,

```javascript
function func() {
   return Promise.resolve(10)
}
```
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 26. What is the output of below code

```javascript
async function func() {
   await 10;
}
console.log(func());
```

- 1: Promise {\<fulfilled\>: 10}
- 2: 10
- 3: SyntaxError
- 4: Promise {\<resolved\>: undefined}

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

The await expression returns value 10 with promise resolution and the code after each await expression can be treated as existing in a `.then` callback. In this case, there is no return expression at the end of the function. Hence, the default return value of `undefined` is returned as the resolution of the promise.  The above async function is equivalent to below expression,

```javascript
function func() {
   return Promise.resolve(10).then(() => undefined)
}
```
</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 27. What is the output of below code

```javascript
function delay() {
  return new Promise(resolve => setTimeout(resolve, 2000));
}

async function delayedLog(item) {
  await delay();
  console.log(item);
}

async function processArray(array) {
  array.forEach(item => {
    await delayedLog(item);
  })
}

processArray([1, 2, 3, 4]);
```

- 1: SyntaxError
- 2: 1, 2, 3, 4
- 3: 4, 4, 4, 4
- 4: 4, 3, 2, 1

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

Even though “processArray” is an async function, the anonymous function that we use for `forEach` is synchronous. If you use await inside a synchronous function then it throws a syntax error.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 28. What is the output of below code

```javascript
function delay() {
  return new Promise(resolve => setTimeout(resolve, 2000));
}

async function delayedLog(item) {
  await delay();
  console.log(item);
}

async function process(array) {
  array.forEach(async (item) => {
    await delayedLog(item);
  });
  console.log('Process completed!');
}
process([1, 2, 3, 5]);
```

- 1: 1 2 3 5 and Process completed!
- 2: 5 5 5 5 and Process completed!
- 3: Process completed! and 5 5 5 5
- 4: Process completed! and 1 2 3 5

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

The forEach method will not wait until all items are finished but it just runs the tasks and goes next. Hence, the last statement is displayed first followed by a sequence of promise resolutions.

But you control the array sequence using for..of loop,

```javascript
async function processArray(array) {
  for (const item of array) {
    await delayedLog(item);
  }
  console.log('Process completed!');
}
```

</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 29. What is the output of below code

```javascript
var set = new Set();
set.add("+0").add("-0").add(NaN).add(undefined).add(NaN);;
console.log(set);
```

- 1: Set(4) {"+0", "-0", NaN, undefined}
- 2: Set(3) {"+0", NaN, undefined}
- 3: Set(5) {"+0", "-0", NaN, undefined, NaN}
- 4: Set(4) {"+0", NaN, undefined, NaN}

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

Set has few exceptions from equality check,

1. All NaN values are equal
2. Both +0 and -0 considered as different values

</p>
</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 30. What is the output of below code

```javascript
const sym1 = Symbol('one');
const sym2 = Symbol('one');

const sym3 = Symbol.for('two');
const sym4 = Symbol.for('two');

cnsooe.log(sym1 === sym2, sym3 === sym4);
```

- 1: true, true
- 2: true, false
- 3: false, true
- 4: false, false

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 3

Symbol follows below conventions,

1. Every symbol value returned from Symbol() is unique irrespective of the optional string.
2. `Symbol.for()` function creates a symbol in a global symbol registry list. But it doesn't  necessarily create a new symbol on every call, it checks first if a symbol with the given key is already present in the registry and returns the symbol if it is found. Otherwise a new symbol created in the registry.

**Note:** The symbol description is just useful for debugging purposes.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 31. What is the output of below code

```javascript
const sym1 = new Symbol('one');
console.log(sym1);
```

- 1: SyntaxError
- 2: one
- 3: Symbol('one')
- 4: Symbol

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

`Symbol` is a just a standard function and not an object constructor(unlike other primitives new Boolean, new String and new Number). So if you try to call it with the new operator will result in a TypeError
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 32. What is the output of below code

```javascript
let myNumber = 100;
let myString = '100';

if (!typeof myNumber === "string") {
   console.log("It is not a string!");
} else {
    console.log("It is a string!");
}

if (!typeof myString === "number"){
   console.log("It is not a number!")
} else {
   console.log("It is a number!");
}
```

- 1: SyntaxError
- 2: It is not a string!, It is not a number!
- 3: It is not a string!, It is a number!
- 4: It is a string!, It is a number!

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

The return value of `typeof myNumber (OR) typeof myString` is always the truthy value (either "number" or "string"). Since ! operator converts the value to a boolean value, the value of both `!typeof myNumber or !typeof myString` is always false. Hence the if condition fails and control goes to else block.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 33. What is the output of below code

```javascript
console.log(JSON.stringify({ myArray: ['one', undefined, function(){}, Symbol('')] }));
console.log(JSON.stringify({ [Symbol.for('one')]: 'one' }, [Symbol.for('one')]));
```

- 1: {"myArray":['one', undefined, {}, Symbol]}, {}
- 2: {"myArray":['one', null,null,null]}, {}
- 3: {"myArray":['one', null,null,null]}, "{ [Symbol.for('one')]: 'one' }, [Symbol.for('one')]"
- 4: {"myArray":['one', undefined, function(){}, Symbol('')]}, {}

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

The symbols has below constraints,

1. The undefined, Functions, and Symbols are not valid JSON values. So those values are either omitted (in an object) or changed to null (in an array). Hence, it returns null values for the value array.
2. All Symbol-keyed properties will be completely ignored. Hence it returns an empty object({}).

</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 34. What is the output of below code

```javascript
class A {
  constructor() {
    console.log(new.target.name)
  }
}

class B extends A { constructor() { super() } }

new A();
new B();
```

- 1: A, A
- 2: A, B

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

Using constructors, `new.target` refers to the constructor (points to the class definition of class which is initialized) that was directly invoked by new. This also applies to the case if the constructor is in a parent class and was delegated from a child constructor.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 35. What is the output of below code

```javascript
const [x, ...y,] = [1, 2, 3, 4];
console.log(x, y);
```

- 1: 1, [2, 3, 4]
- 2: 1, [2, 3]
- 3: 1, [2]
- 4: SyntaxError

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

It throws a syntax error because the rest element should not have a trailing comma. You should always consider using a rest operator as the last element.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 36. What is the output of below code

```javascript
const {a: x = 10, b: y = 20} = {a: 30};

console.log(x);
console.log(y);
```

- 1: 30, 20
- 2: 10, 20
- 3: 10, undefined
- 4: 30, undefined

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

The object property follows below rules,

1. The object properties can be retrieved and assigned to a variable with a different name
2. The property assigned a default value when the retrieved value is `undefined`

</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 37. What is the output of below code

```javascript
function area({length = 10, width = 20}) {
  console.log(length*width);
}

area();
```

- 1: 200
- 2: Error
- 3: undefined
- 4: 0

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

If you leave out the right-hand side assignment for the destructuring object, the function will look for at least one argument to be supplied when invoked. Otherwise you will receive an error `Error: Cannot read property 'length' of undefined` as mentioned above.

You can avoid the error with either of the below changes,

1. **Pass at least an empty object:**

```javascript
function area({length = 10, width = 20}) {
  console.log(length*width);
}

area({});
```

2. **Assign default empty object:**

```javascript
function area({length = 10, width = 20} = {}) {
  console.log(length*width);
}

area();
```

</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 38. What is the output of below code

```javascript
const props = [
  { id: 1, name: 'John'},
  { id: 2, name: 'Jack'},
  { id: 3, name: 'Tom'}
];

const [,, { name }] = props;
console.log(name);
```

- 1: Tom
- 2: Error
- 3: undefined
- 4: John

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

It is possible to combine Array and Object destructuring. In this case, the third element in the array props accessed first followed by name property in the object.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 39. What is the output of below code

```javascript
function checkType(num = 1) {
  console.log(typeof num);
}

checkType();
checkType(undefined);
checkType('');
checkType(null);
```

- 1: number, undefined, string, object
- 2: undefined, undefined, string, object
- 3: number, number, string, object
- 4: number, number, number, number

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 3

If the function argument is set implicitly(not passing argument) or explicitly to undefined, the value of the argument is the default parameter. Whereas for other falsy values('' or null), the value of the argument is passed as a parameter.

Hence, the result of function calls categorized as below,

1. The first two function calls logs number type since the type of default value is number
2. The type of '' and null values are string and object type respectively.

</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 40. What is the output of below code

```javascript
function add(item, items = []) {
  items.push(item);
  return items;
}

console.log(add('Orange'));
console.log(add('Apple'));
```

- 1: ['Orange'], ['Orange', 'Apple']
- 2: ['Orange'], ['Apple']

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

Since the default argument is evaluated at call time, a new object is created each time the function is called. So in this case, the new array is created and an element pushed to the default empty array.

</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 41. What is the output of below code

```javascript
function greet(greeting, name, message = greeting + ' ' + name) {
  console.log([greeting, name, message]);
}

greet('Hello', 'John');
greet('Hello', 'John', 'Good morning!');
```

- 1: SyntaxError
- 2: ['Hello', 'John', 'Hello John'], ['Hello', 'John', 'Good morning!']


<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

Since parameters defined earlier are available to later default parameters, this code snippet doesn't throw any error.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 42. What is the output of below code

```javascript
function outer(f = inner()) {
  function inner() { return 'Inner' }
}
outer();
```

- 1: ReferenceError
- 2: Inner

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

The functions and variables declared in the function body cannot be referred from default value parameter initializers. If you still try to access, it throws a run-time ReferenceError(i.e, `inner` is not defined).
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 43. What is the output of below code

```javascript
function myFun(x, y, ...manyMoreArgs) {
  console.log(manyMoreArgs)
}

myFun(1, 2, 3, 4, 5);
myFun(1, 2);
```

- 1: [3, 4, 5], undefined
- 2: SyntaxError
- 3: [3, 4, 5], []
- 4: [3, 4, 5], [undefined]

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 3

The rest parameter is used to hold the remaining parameters of a function and it becomes an empty array if the argument is not provided.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 44. What is the output of below code

```javascript
const obj = {'key': 'value'};
const array = [...obj];
console.log(array);
```

- 1: ['key', 'value']
- 2: TypeError
- 3: []
- 4: ['key']

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

Spread syntax can be applied only to iterable objects. By default, Objects are not iterable, but they become iterable when used in an Array, or with iterating functions such as `map(), reduce(), and assign()`. If you still try to do it, it still throws `TypeError: obj is not iterable`.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 45. What is the output of below code

```javascript
function* myGenFunc() {
    yield 1;
    yield 2;
    yield 3;
}
var myGenObj = new myGenFunc;
console.log(myGenObj.next().value);
```

- 1: 1
- 2: undefined
- 3: SyntaxError
- 4: TypeError

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

Generators are not constructible type. But if you still proceed to do, there will be an error saying "TypeError: myGenFunc is not a constructor"

</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 46. What is the output of below code

```javascript

function* yieldAndReturn() {
  yield 1;
  return 2;
  yield 3;
}

var myGenObj = yieldAndReturn()
console.log(myGenObj.next());
console.log(myGenObj.next());
console.log(myGenObj.next());
```

- 1: { value: 1, done: false }, { value: 2, done: true }, { value: undefined, done: true }
- 2: { value: 1, done: false }, { value: 2, done: false }, { value: undefined, done: true }
- 3: { value: 1, done: false }, { value: 2, done: true }, { value: 3, done: true }
- 4: { value: 1, done: false }, { value: 2, done: false }, { value: 3, done: true }

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1

A return statement in a generator function will make the generator finish. If a value is returned, it will be set as the value property of the object and done property to true. When a generator is finished, subsequent next() calls return an object of this form: `{value: undefined, done: true}`.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 47. What is the output of below code

```javascript
const myGenerator = (function *(){
  yield 1;
  yield 2;
  yield 3;
})();
for (const value of myGenerator) {
  console.log(value);
  break;
}

for (const value of myGenerator) {
  console.log(value);
}
```

- 1: 1,2,3 and 1,2,3
- 2: 1,2,3 and 4,5,6
- 3: 1 and 1
- 4: 1

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

The generator should not be re-used once the iterator is closed. i.e, Upon exiting a loop(on completion or using break & return), the generator is closed and trying to iterate over it again does not yield any more results. Hence, the second loop doesn't print any value.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 48. What is the output of below code

```javascript
const num = 0o38;
console.log(num);
```

- 1: SyntaxError
- 2: 38

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1
If you use an invalid number(outside of 0-7 range) in the octal literal, JavaScript will throw a SyntaxError. In ES5, it treats the octal literal as a decimal number.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 49. What is the output of below code

```javascript
const squareObj = new Square(10);
console.log(squareObj.area);

class Square {
  constructor(length) {
    this.length = length;
  }

  get area() {
    return this.length * this.length;
  }

  set area(value) {
    this.area = value;
  }
}
```

- 1: 100
- 2: ReferenceError

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

Unlike function declarations, class declarations are not hoisted. i.e, First You need to declare your class and then access it, otherwise it will throw a ReferenceError "Uncaught ReferenceError: Square is not defined".

**Note:** Class expressions also applies to the same hoisting restrictions of class declarations.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 50. What is the output of below code

```javascript
function Person() { }

Person.prototype.walk = function() {
  return this;
}

Person.run = function() {
  return this;
}

let user = new Person();
let walk = user.walk;
console.log(walk());

let run = Person.run;
console.log(run());
```

- 1: undefined, undefined
- 2: Person, Person
- 3: SyntaxError
- 4: Window, Window

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4

When a regular or prototype method is called without a value for **this**, the methods return an initial this value if the value is not undefined. Otherwise global window object will be returned. In our case, the initial `this` value is undefined so both methods return window objects.

</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 51. What is the output of below code

```javascript
class Vehicle {
  constructor(name) {
    this.name = name;
  }

  start() {
    console.log(`${this.name} vehicle started`);
  }
}

class Car extends Vehicle {
  start() {
    console.log(`${this.name} car started`);
    super.start();
  }
}

const car = new Car('BMW');
console.log(car.start());
```

- 1: SyntaxError
- 2: BMW vehicle started, BMW car started
- 3: BMW car started, BMW vehicle started
- 4: BMW car started, BMW car started

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 3

The super keyword is used to call methods of a superclass. Unlike other languages the super invocation doesn't need to be a first statement. i.e, The statements will be executed in the same order of code.

</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 52. What is the output of below code

```javascript
const USER = {'age': 30};
USER.age = 25;
console.log(USER.age);
```

- 1: 30
- 2: 25
- 3: Uncaught TypeError
- 4: SyntaxError

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2

Even though we used constant variables, the content of it is an object and the object's contents (e.g properties) can be altered. Hence, the change is going to be valid in this case.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 53. What is the output of below code

```javascript
console.log('🙂' === '🙂');
```

- 1: false
- 2: true

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 2
Emojis are unicodes and the unicode for smile symbol is "U+1F642". The unicode comparision of same emojies is equivalent to string comparison. Hence, the output is always true.

</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 54. What is the output of below code?

```javascript
console.log(typeof typeof typeof true);
```

- 1: string
- 2: boolean
- 3: NaN
- 4: number

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1
The typeof operator on any primitive returns a string value. So even if you apply the chain of typeof operators on the return value, it is always string.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 55. What is the output of below code?

```javascript
let zero = new Number(0);

if (zero) {
  console.log("If");
} else {
  console.log("Else");
}
```

- 1: If
- 2: Else
- 3: NaN
- 4: SyntaxError

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1
1. The type of operator on new Number always returns object. i.e, typeof new Number(0) --> object. 
2. Objects are always truthy in if block

Hence the above code block always goes to if section.

</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 55. What is the output of below code in non strict mode?

```javascript
let msg = "Good morning!!";

msg.name = "John"; 

console.log(msg.name);
```

- 1: ""
- 2: Error
- 3: John
- 4: Undefined

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 4
It returns undefined for non-strict mode and returns Error for strict mode. In non-strict mode, the wrapper object is going to be created and get the mentioned property. But the object get disappeared after accessing the property in next line.
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

#### 56. What is the output of below code?

```javascript
let count = 10;

(function innerFunc() {
    if (count === 10) {
        let count = 11;
        console.log(count);
    }
    console.log(count);
})();
```

- 1: 11, 10
- 2: 11, 11
- 3: 10, 11
- 4: 10, 10

<details><summary><b>Answer</b></summary>
<p>

##### Answer: 1
11 and 10 is logged to the console. 

The innerFunc is a closure which captures the count variable from the outerscope. i.e, 10. But the conditional has another local variable `count` which overwrites the ourter `count` variable. So the first console.log displays value 11.
Whereas the second console.log logs 10 by capturing the count variable from outerscope.
 
</p>

</details>

---

**[⬆ Back to Top](#table-of-contents)**

---

## Disclaimer

The questions provided in this repository are the summary of frequently asked questions across numerous companies. We cannot guarantee that these questions will actually be asked during your interview process, nor should you focus on memorizing all of them. The primary purpose is for you to get a sense of what some companies might ask — do not get discouraged if you don't know the answer to all of them ⁠— that is ok!

Good luck with your interview 😊

---
# Node.js Interview Questions

*Click <img src="assets/star.png" width="18" height="18" align="absmiddle" title="Star" /> if you like the project. Pull Request are highly appreciated.*

## Table of Contents

* *[NodeJS APIs](nodejs-api.md)*

| Sl.No|  Questions       |
|------|------------------|
| 01. |[What does the runtime environment mean in Node.js?](#q-what-does-the-runtime-environment-mean-in-nodejs)|
| 02. |[What is Node.js?](#q-what-is-nodejs)|
| 03. |[What is Node.js Process Model?](#q-what-is-nodejs-process-model)|
| 04. |[What are the data types in Node.js?](#q-what-are-the-data-types-in-nodejs)|
| 05. |[How to create a simple server in Node.js that returns Hello World?](#q-how-to-create-a-simple-server-in-nodejs-that-returns-hello-world)|
| 06. |[How do Node.js works?](#q-how-do-nodejs-works)|
| 07. |[What is an error-first callback?](#q-what-is-an-error-first-callback)|
| 08. |[What is callback hell in Node.js?](#q-what-is-callback-hell-in-nodejs)|
| 09. |[What are Promises in Node.js?](#q-what-are-promises-in-nodejs)|
| 10. |[What tools can be used to assure consistent style?](#q-what-tools-can-be-used-to-assure-consistent-style)|
| 11. |[When should you npm and when yarn?](#q-when-should-you-npm-and-when-yarn)|
| 12. |[What is a stub?](#q-what-is-a-stub)|
| 13. |[What is a test pyramid? How can you implement it when talking about HTTP APIs?](#q-what-is-a-test-pyramid-how-can-you-implement-it-when-talking-about-http-apis)|
| 14. |[How can you secure your HTTP cookies against XSS attacks?](#q-how-can-you-secure-your-http-cookies-against-xss-attacks)|
| 15. |[How can you make sure your dependencies are safe?](#q-how-can-you-make-sure-your-dependencies-are-safe)|
| 16. |[What is Event loop in Node.js? And How does it work?](#q-what-is-event-loop-in-nodejs-and-how-does-it-work)|
| 17. |[What is REPL? What purpose it is used for?](#q-what-is-repl-what-purpose-it-is-used-for)|
| 18. |[What is the difference between Asynchronous and Non-blocking?](#q-what-is-the-difference-between-asynchronous-and-non-blocking)|
| 19. |[How to debug an application in Node.js?](#q-how-to-debug-an-application-in-nodejs)|
| 20. |[What are some of the most popular modules of Node.js?](#q-what-are-some-of-the-most-popular-modules-of-nodejs)|
| 21. |[What is EventEmitter in Node.js?](#q-what-is-eventemitter-in-nodejs)|
| 22. |[How many types of streams are present in node.js?](#q-how-many-types-of-streams-are-present-in-nodejs)|
| 23. |[What is crypto in Node.js? How do you cipher the secure information in Node.js?](#q-what-is-crypto-in-nodejs-how-do-you-cipher-the-secure-information-in-nodejs)|
| 24. |[What is the use of DNS module in Node.js?](#q-what-is-the-use-of-dns-module-in-nodejs)|
| 25. |[What are the security mechanisms available in Node.js?](#q-what-are-the-security-mechanisms-available-in-nodejs)|
| 26. |[Name the types of API functions in Node.js.](#q-name-the-types-of-api-functions-in-nodejs)
| 27. |[How does Node.js handle child threads?](#q-how-does-nodejs-handle-child-threads)|
| 28. |[What is the preferred method of resolving unhandled exceptions in Node.js?](#q-what-is-the-preferred-method-of-resolving-unhandled-exceptions-in-nodejs)|
| 29. |[How does Node.js support multi-processor platforms, and does it fully utilize all processor resources?](#q-how-does-nodejs-support-multi-processor-platforms-and-does-it-fully-utilize-all-processor-resources)|
| 30. |[What is typically the first argument passed to a Node.js callback handler?](#q-what-is-typically-the-first-argument-passed-to-a-nodejs-callback-handler)|
| 31. |[How Node.js read the content of a file?](#q-how-nodejs-read-the-content-of-a-file)|
| 32. |[What is JIT and how is it related to Node.js?](#q-what-is-jit-and-how-is-it-related-to-nodejs)|
| 33. |[What is difference between put and patch?](#q-what-is-difference-between-put-and-patch)|
| 34. |[List types of Http requests supported by Node.js.](#q-list-types-of-http-requests-supported-by-nodejs)
| 35. |[Why to use Express.js?](#q-why-to-use-expressjs)|
| 36. |[Write the steps for setting up an Express JS application.](#q-write-the-steps-for-setting-up-an-express-js-application)
| 37. |[Since node is a single threaded process, how to make use of all CPUs?](#q-since-node-is-a-single-threaded-process-how-to-make-use-of-all-cpus)|
| 38. |[What does emitter do and what is dispatcher?](#q-what-does-emitter-do-and-what-is-dispatcher)|
| 39. |[How to kill child processes that spawn their own child processes in Node.js?](#q-how-to-kill-child-processes-that-spawn-their-own-child-processes-in-nodejs)|
| 40. |[What do you understand by Reactor Pattern in Node.js?](#q-what-do-you-understand-by-reactor-pattern-in-nodejs)|
| 41. |[What are the key features of Node.js?](#q-what-are-the-key-features-of-nodejs)|
| 42. |[What are globals in Node.js?](#q-what-are-globals-in-nodejs)|
| 43. |[What is chaining process in Node.js?](#q-what-is-chaining-process-in-nodejs)|
| 44. |[What is a control flow function? what are the steps does it execute?](#q-what-is-a-control-flow-function-what-are-the-steps-does-it-execute)|
| 45. |[What is npm in Node.js?](#q-what-is-npm-in-nodejs)|
| 46. |[When to use Node.js and when not to use it?](#q-when-to-use-nodejs-and-when-not-to-use-it)|
| 47. |[Explain how does Node.js work?](#q-explain-how-does-nodejs-work)|
| 48. |[Is Node.js entirely based on a single-thread?](#q-is-nodejs-entirely-based-on-a-single-thread)|
| 49. |[How to make post request in Node.js?](#q-how-to-make-post-request-in-nodejs)|
| 50. |[Can you create http server in Node.js, explain the code used for it?](#q-can-you-create-http-server-in-nodejs-explain-the-code-used-for-it)|
| 51. |[How to load html in Node.js?](#q-how-to-load-html-in-nodejs)|
| 52. |[How can you listen on port 80 with Node?](#q-how-can-you-listen-on-port-80-with-node)|
| 53. |[What is the difference between operational and programmer errors?](#q-what-is-the-difference-between-operational-and-programmer-errors)|
| 54. |[Why npm shrinkwrap is useful?](#q-why-npm-shrinkwrap-is-useful)|
| 55. |[What is your favourite HTTP framework and why?](#q-what-is-your-favourite-http-framework-and-why)|
| 56. |[What are the Challenges with Node.js?](#q-what-are-the-challenges-with-nodejs)|
| 57. |[What is the difference between Node.js vs Ajax?](#q-what-is-the-difference-between-nodejs-vs-ajax)|
| 58. |[How Node.js overcomes the problem of blocking of I/O operations?](#q-how-nodejs-overcomes-the-problem-of-blocking-of-i-o-operations)|
| 59. |[Mention the steps by which you can async in Node.js?](#q-mention-the-steps-by-which-you-can-async-in-nodejs)|
| 60. |[What are the timing features of Node.js?](#q-what-are-the-timing-features-of-nodejs)|
| 61. |[What is LTS releases of Node.js why should you care?](#q-what-is-lts-releases-of-nodejs-why-should-you-care)|
| 62. |[Why should you separate Express 'app' and 'server'?](#q-why-should-you-separate-express-app-and-server)|
| 63. |[What is the difference between process.nextTick() and setImmediate()?](#q-what-is-the-difference-between-processnexttick-and-setimmediate)|
| 64. |[What is difference between JavaScript and Node.js?](#q-what-is-difference-between-javascript-and-nodejs)|
| 65. |[What are the difference between Events and Callbacks?](#q-what-are-the-difference-between-events-and-callbacks)|
| 66. |[Explain RESTful Web Services in Node.js?](#q-explain-restful-web-services-in-nodejs)|
| 67. |[How to handle file upload in Node js?](#q-how-to-handle-file-upload-in-node-js)|
| 68. |[Explain the terms body-parser, cookie-parser, debug, jade, morgan, nodemon, pm2, serve-favicon, cors in Express JS?](#q-explain-the-terms-body-parser-cookie-parser-debug-jade-morgan-nodemon-pm2-serve-favicon-cors-in-express-js)|
| 69. |[How does routing work in Node.js](#q-how-does-routing-work-in-node-js)|
| 70. |[How Node prevents blocking code?](#q-how-node-prevents-blocking-code)|
| 71. |[What is difference between promise and async await in node js?](#q-what-is-difference-between-promise-and-async-await-in-node-js)|
| 72. |[How to use JSON Web Token (JWT) for authentication in node js?](#q-how-to-use-json-web-token-jwt-for-authentication-in-node-js)|
| 73. |[How to build a microservices architecture with node js?](#q-how-to-build-a-microservices-architecture-with-node-js)|
| 74. |[How to use Q promise in node js?](#q-how-to-use-q-promise-in-node-js)|
| 75. |[How to use locale (i18n) in node js?](#q-how-to-use-locale-i18n-in-node-js)|
| 76. |[How to Implement Memcached in Nodejs?](#q-how-to-implement-memcached-in-nodejs)|
| 77. |[Explain Error Handling in Nodejs?](#q-explain-error-handling-in-nodejs)|
| 78. |[How to generate and verify checksum of the given string in Nodejs](#q-how-to-generate-and-verify-checksum-of-the-given-string-in-nodejs)|

<br/>

## Q. ***What does the runtime environment mean in Node.js?***

The Node.js runtime is the software stack responsible for installing your web service\'s code and its dependencies and running your service.

The Node.js runtime for App Engine in the standard environment is declared in the `app.yaml` file:

```js
runtime: nodejs10
```

The runtime environment is literally just the environment your application is running in. This can be used to describe both the hardware and the software that is running your application. How much RAM, what version of node, what operating system, how much CPU cores, can all be referenced when talking about a runtime environment.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is Node.js?***

Node.js is an open-source server side runtime environment built on Chrome\'s V8 JavaScript engine. It provides an event driven, non-blocking (asynchronous) I/O and cross-platform runtime environment for building highly scalable server-side applications using JavaScript.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is Node.js Process Model?***

Node.js runs in a single process and the application code runs in a single thread and thereby needs less resources than other platforms. All the user requests to your web application will be handled by a single thread and all the I/O work or long running job is performed asynchronously for a particular request. So, this single thread doesn't have to wait for the request to complete and is free to handle the next request. When asynchronous I/O work completes then it processes the request further and sends the response.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are the data types in Node.js?***

*Primitive Types*

* String
* Number
* Boolean
* Undefined
* Null
* RegExp

* `Buffer`: Node.js includes an additional data type called Buffer (not available in browser\'s JavaScript). Buffer is mainly used to store binary data, while reading from a file or receiving packets over the network.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to create a simple server in Node.js that returns Hello World?***

**Step 01**: Create a project directory

```bash
mkdir myapp
cd myapp
```

**Step 02**: Initialize project and link it to npm

```bash
npm init
```

This creates a `package.json` file in your myapp folder. The file contains references for all npm packages you have downloaded to your project. The command will prompt you to enter a number of things.
You can enter your way through all of them EXCEPT this one:

```bash
entry point: (index.js)
```

Rename this to:

```bash
app.js
```

**Step 03**: Install Express in the myapp directory

```bash
npm install express --save
```

**Step 04**: app.js

```js
var express = require('express');
var app = express();
app.get('/', function (req, res) {
  res.send('Hello World!');
});

app.listen(3000, function () {
  console.log('Example app listening on port 3000!');
});
```

**Step 05**: Run the app

```bah
node app.js
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How do Node.js works?***

<p align="center">
  <img src="assets/event-loop.png" alt="Node Architecture" width="800px" />
</p>

Node is completely event-driven. Basically the server consists of one thread processing one event after another.

A new request coming in is one kind of event. The server starts processing it and when there is a blocking IO operation, it does not wait until it completes and instead registers a callback function. The server then immediately starts to process another event (maybe another request). When the IO operation is finished, that is another kind of event, and the server will process it (i.e. continue working on the request) by executing the callback as soon as it has time.

So the server never needs to create additional threads or switch between threads, which means it has very little overhead. If you want to make full use of multiple hardware cores, you just start multiple instances of node.js

Node JS Platform does not follow Request/Response Multi-Threaded Stateless Model. It follows Single Threaded with Event Loop Model. Node JS Processing model mainly based on Javascript Event based model with Javascript callback mechanism.  
  
**Single Threaded Event Loop Model Processing Steps:**

* Clients Send request to Web Server.
* Node JS Web Server internally maintains a Limited Thread pool to provide services to the Client Requests.
* Node JS Web Server receives those requests and places them into a Queue. It is known as “Event Queue”.
* Node JS Web Server internally has a Component, known as “Event Loop”. Why it got this name is that it uses indefinite loop to receive requests and process them. 
* Event Loop uses Single Thread only. It is main heart of Node JS Platform Processing Model.
* Even Loop checks any Client Request is placed in Event Queue. If no, then wait for incoming requests for indefinitely.
* If yes, then pick up one Client Request from Event Queue
    * Starts process that Client Request
    * If that Client Request Does Not requires any Blocking IO Operations, then process everything, prepare response and send it back to client.
    * If that Client Request requires some Blocking IO Operations like interacting with Database, File System, External Services then it will follow different approach
        * Checks Threads availability from Internal Thread Pool
        * Picks up one Thread and assign this Client Request to that thread.
        * That Thread is responsible for taking that request, process it, perform Blocking IO operations, prepare response and send it back to the Event Loop
        * Event Loop in turn, sends that Response to the respective Client.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is an error-first callback?***

The pattern used across all the asynchronous methods in Node.js is called *Error-first Callback*. Here is an example:

```javascript
fs.readFile( "file.json", function ( err, data ) {
  if ( err ) {
    console.error( err );
  }
  console.log( data );
});
```

Any asynchronous method expects one of the arguments to be a callback. The full callback argument list depends on the caller method, but the first argument is always an error object or null. When we go for the asynchronous method, an exception thrown during function execution cannot be detected in a try/catch statement. The event happens after the JavaScript engine leaves the try block. 

In the preceding example, if any exception is thrown during the reading of the file, it lands on the callback function as the first and mandatory parameter.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is callback hell in Node.js?***

`Callback hell` is a phenomenon that afflicts a JavaScript developer when he tries to execute multiple asynchronous operations one after the other.

An asynchronous function is one where some external activity must complete before a result can be processed; it is “asynchronous” in the sense that there is an unpredictable amount of time before a result becomes available. Such functions require a callback function to handle errors and process the result.

```javascript
getData(function(a){
    getMoreData(a, function(b){
        getMoreData(b, function(c){ 
            getMoreData(c, function(d){ 
	            getMoreData(d, function(e){ 
		            ...
		        });
	        });
        });
    });
});
```

**Techniques for avoiding callback hell**

1. Using Async.js
1. Using Promises
1. Using Async-Await

* **Managing callbacks using Async.js**  

`Async` is a really powerful npm module for managing asynchronous nature of JavaScript. Along with Node.js, it also works for JavaScript written for browsers.

Async provides lots of powerful utilities to work with asynchronous processes under different scenarios.

```bash
npm install --save async
```

* **ASYNC WATERFALL**  

```javascript
var async = require('async');
async.waterfall([
    function(callback) {
        //doSomething
        callback(null, paramx); //paramx will be availaible as the first parameter to the next function
        /**
            The 1st parameter passed in callback.
            @null or @undefined or @false control moves to the next function
            in the array
            if @true or @string the control is immedeatly moved
            to the final callback fucntion
            rest of the functions in the array
            would not be executed
        */
    },
    function(arg1, callback) {
        //doSomething else
      // arg1 now equals paramx
        callback(null, result);
    },
    function(arg1, callback) {
        //do More
        // arg1 now equals 'result'
        callback(null, 'done');
    },
    function(arg1, callback) {
        //even more
        // arg1 now equals 'done'
        callback(null, 'done');
    }
], function (err, result) {
    //final callback function
    //finally do something when all function are done.
    // result now equals 'done'
});
```

* **ASYNC SERIES**  

```javascript
var async = require('async');
async.series([
    function(callback){
        // do some stuff ...
        callback(null, 'one');
        /**
            The 1st parameter passed in callback.
            @null or @undefined or @false control moves to the next function
            in the array
            if @true or @string the control is immedeatly moved
            to the final callback fucntion with the value of err same as
            passed over here and
            rest of the functions in the array
            would not be executed
        */
    },
    function(callback){
        // do some more stuff ...
        callback(null, 'two');
    }
],
// optional callback
function(err, results){
    // results is now equal to ['one', 'two']
});
```

* **Managing callbacks hell using promises**  

Promises are alternative to callbacks while dealing with asynchronous code. Promises return the value of the result or an error exception. The core of the promises is the `.then()` function, which waits for the promise object to be returned. The `.then()` function takes two optional functions as arguments and depending on the state of the promise only one will ever be called. The first function is called when the promise if fulfilled (A successful result). The second function is called when the promise is rejected.

```javascript
var outputPromise = getInputPromise().then(function (input) {
    //handle success
}, function (error) {
    //handle error
});
```

* **Using Async Await**  

Async await makes asynchronous code look like it\’s synchronous. This has only been possible because of the reintroduction of promises into node.js. Async-Await only works with functions that return a promise.

```javascript
const getrandomnumber = function(){
    return new Promise((resolve, reject)=>{
        setTimeout(() => {
            resolve(Math.floor(Math.random() * 20));
        }, 1000);
    });
}

const addRandomNumber = async function(){
    const sum = await getrandomnumber() + await getrandomnumber();
    console.log(sum);
}

addRandomNumber();
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are Promises in Node.js?***

It allows to associate handlers to an asynchronous action\'s eventual success value or failure reason. This lets asynchronous methods return values like synchronous methods: instead of the final value, the asynchronous method returns a promise for the value at some point in the future.

Promises in node.js promised to do some work and then had separate callbacks that would be executed for success and failure as well as handling timeouts. Another way to think of promises in node.js was that they were emitters that could emit only two events: success and error.The cool thing about promises is you can combine them into dependency chains (do Promise C only when Promise A and Promise B complete).

The core idea behind promises is that a promise represents the result of an asynchronous operation. A promise is in one of three different states:

* pending - The initial state of a promise.
* fulfilled - The state of a promise representing a successful operation.
* rejected - The state of a promise representing a failed operation.
Once a promise is fulfilled or rejected, it is immutable (i.e. it can never change again).  

**Creating a Promise**

```javascript
var myPromise = new Promise(function(resolve, reject){
   ....
})
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What tools can be used to assure consistent style?***

* ESLint
* Standard

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***When should you npm and when yarn?***

* **npm**  

It is the default method for managing packages in the Node.js runtime environment. It relies upon a command line client and a database made up of public and premium packages known as the the npm registry. Users can access the registry via the client and browse the many packages available through the npm website. Both npm and its registry are managed by npm, Inc.

```bash
node -v
npm -v
```

* **Yarn**  

Yarn was developed by Facebook in attempt to resolve some of npm’s shortcomings. Yarn isn’t technically a replacement for npm since it relies on modules from the npm registry. Think of Yarn as a new installer that still relies upon the same npm structure. The registry itself hasn’t changed, but the installation method is different. Since Yarn gives you access to the same packages as npm, moving from npm to Yarn doesn’t require you to make any changes to your workflow.

```bash
npm install yarn --global
```

**Comparing Yarn vs npm**

* Fast: Yarn caches every package it downloads so it never needs to again. It also parallelizes operations to maximize resource utilization so install times are faster than ever.
* Reliable: Using a detailed, but concise, lockfile format, and a deterministic algorithm for installs, Yarn is able to guarantee that an install that worked on one system will work exactly the same way on any other system.
* Secure: Yarn uses checksums to verify the integrity of every installed package before its code is executed.
* Offline Mode: If you've installed a package before, you can install it again without any internet connection.
* Deterministic: The same dependencies will be installed the same exact way across every machine regardless of install order.
* Network Performance: Yarn efficiently queues up requests and avoids request waterfalls in order to maximize network utilization.
* Multiple Registries: Install any package from either npm or Bower and keep your package workflow the same.
* Network Resilience: A single request failing won't cause an install to fail. Requests are retried upon failure.
* Flat Mode: Resolve mismatching versions of dependencies to a single version to avoid creating duplicates.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a stub?***

Stubbing and verification for node.js tests. Enables you to validate and override behaviour of nested pieces of code such as methods, require() and npm modules or even instances of classes. This library is inspired on node-gently, MockJS and mock-require.  

**Features of Stub:**  

* Produces simple, lightweight Objects capable of extending down their tree
* Compatible with Nodejs
* Easily extendable directly or through an ExtensionManager
* Comes with predefined, usable extensions

Stubs are functions/programs that simulate the behaviours of components/modules. Stubs provide canned answers to function calls made during test cases. Also, you can assert on with what these stubs were called.

A use-case can be a file read, when you do not want to read an actual file:

```javascript
var fs = require('fs');

var readFileStub = sinon.stub(fs, 'readFile', function (path, cb) {  
  return cb(null, 'filecontent');
});

expect(readFileStub).to.be.called;  
readFileStub.restore();
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a test pyramid? How can you implement it when talking about HTTP APIs?***

The "Test Pyramid" is a metaphor that tells us to group software tests into buckets of different granularity. It also gives an idea of how many tests we should have in each of these groups. It shows which kinds of tests you should be looking for in the different levels of the pyramid and gives practical examples on how these can be implemented.

<p align="center">
  <img src="assets/testPyramid.png" alt="Test Pyramid" />
</p>

Mike Cohn\'s original test pyramid consists of three layers that your test suite should consist of (bottom to top):

1. Unit Tests
1. Service Tests
1. User Interface Tests

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How can you secure your HTTP cookies against XSS attacks?***

**1.** When the web server sets cookies, it can provide some additional attributes to make sure the cookies won\'t be accessible by using malicious JavaScript. One such attribute is HttpOnly.

```javascript
Set-Cookie: [name]=[value]; HttpOnly
```

HttpOnly makes sure the cookies will be submitted only to the domain they originated from.

**2.** The "Secure" attribute can make sure the cookies are sent over secured channel only.

```javascript
Set-Cookie: [name]=[value]; Secure
```

**3.** The web server can use X-XSS-Protection response header to make sure pages do not load when they detect reflected cross-site scripting (XSS) attacks.

```javascript
X-XSS-Protection: 1; mode=block
```

**4.** The web server can use HTTP Content-Security-Policy response header to control what resources a user agent is allowed to load for a certain page. It can help to prevent various types of attacks like Cross Site Scripting (XSS) and data injection attacks.

```javascript
Content-Security-Policy: default-src 'self' *.http://sometrustedwebsite.com
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How can you make sure your dependencies are safe?***

The only option is to automate the update / security audit of your dependencies. For that there are free and paid options:

1. npm outdated
2. Trace by RisingStack
3. NSP
4. GreenKeeper
5. Snyk
6. npm audit
7. npm audit fix

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is Event loop in Node.js? And How does it work?***

The event loop is what allows Node.js to perform non-blocking I/O operations — despite the fact that JavaScript is single-threaded — by offloading operations to the system kernel whenever possible.

Node.js is a single-threaded application, but it can support concurrency via the concept of `event` and `callbacks`. Every API of Node.js is asynchronous and being single-threaded, they use `async function calls` to maintain concurrency. Node uses observer pattern. Node thread keeps an event loop and whenever a task gets completed, it fires the corresponding event which signals the event-listener function to execute.

**Event-Driven Programming**

In an event-driven application, there is generally a main loop that listens for events, and then triggers a callback function when one of those events is detected.

Although events look quite similar to callbacks, the difference lies in the fact that callback functions are called when an asynchronous function returns its result, whereas event handling works on the observer pattern. The functions that listen to events act as Observers. Whenever an event gets fired, its listener function starts executing. Node.js has multiple in-built events available through events module and EventEmitter class which are used to bind events and event-listeners as follows

```javascript
// Import events module
var events = require('events');

// Create an eventEmitter object
var eventEmitter = new events.EventEmitter();
```

*Example*:

```javascript
// Import events module
var events = require('events');

// Create an eventEmitter object
var eventEmitter = new events.EventEmitter();

// Create an event handler as follows
var connectHandler = function connected() {
   console.log('connection succesful.');
  
   // Fire the data_received event 
   eventEmitter.emit('data_received');
}

// Bind the connection event with the handler
eventEmitter.on('connection', connectHandler);
 
// Bind the data_received event with the anonymous function
eventEmitter.on('data_received', function() {
   console.log('data received succesfully.');
});

// Fire the connection event 
eventEmitter.emit('connection');

console.log("Program Ended.");
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is REPL? What purpose it is used for?***

REPL (READ, EVAL, PRINT, LOOP) is a computer environment similar to Shell (Unix/Linux) and command prompt. Node comes with the REPL environment when it is installed. System interacts with the user through outputs of commands/expressions used. It is useful in writing and debugging the codes. The work of REPL can be understood from its full form:

* **Read**: It reads the inputs from users and parses it into JavaScript data structure. It is then stored to memory.
* **Eval**: The parsed JavaScript data structure is evaluated for the results.
* **Print**: The result is printed after the evaluation.
* **Loop**: Loops the input command. To come out of NODE REPL, press ctrl+c twice

Simple Expression

```js
$ node
> 10 + 20
30
> 10 + ( 20 * 30 ) - 40
570
>
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the difference between Asynchronous and Non-blocking?***

**1. Asynchronous**

The architecture of asynchronous explains that the message sent will not give the reply on immediate basis just like we send the mail but do not get the reply on an immediate basis. It does not have any dependency or order. Hence improving the system efficiency and performance. The server stores the information and when the action is done it will be notified.

**2. Non-Blocking**

Nonblocking immediately responses with whatever data available. Moreover, it does not block any execution and keeps on running as per the requests. If an answer could not be retrieved than in those cases API returns immediately with an error. Nonblocking is mostly used with I/O(input/output). Node.js is itself based on nonblocking I/O model. There are few ways of communication that a nonblocking I/O has completed. The callback function is to be called when the operation is completed. Nonblocking call uses the help of javascript which provides a callback function.

* **Asynchronous VS Non-Blocking**  

1) Asynchronous does not respond immediately, While Nonblocking responds immediately if the data is available and if not that simply returns an error.
2) Asynchronous improves the efficiency by doing the task fast as the response might come later, meanwhile, can do complete other tasks. Nonblocking does not block any execution and if the data is available it retrieves the information quickly.
3) Asynchronous is the opposite of synchronous while nonblocking I/O is the opposite of blocking. They both are fairly similar but they are also different as asynchronous is used with a broader range of operations while nonblocking is mostly used with I/O.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to debug an application in Node.js?***

* **node-inspector**

```bash
npm install -g node-inspector
```

Run

```bash
node-debug app.js
```

* **Debugging**
    * Debugger
    * Node Inspector
    * Visual Studio Code
    * Cloud9
    * Brackets

* **Profiling**

```bash
1. node --prof ./app.js
2. node --prof-process ./the-generated-log-file
```

* **Heapdumps**
    * node-heapdump with Chrome Developer Tools

* **Tracing**
    * Interactive Stack Traces with TraceGL

* **Logging**  
Libraries that output debugging information
    * Caterpillar
    * Tracer
    * scribbles

Libraries that enhance stack trace information  
* Longjohn

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are some of the most popular modules of Node.js?***

* **Async**: Async is a utility module which provides straight-forward, powerful functions for working with asynchronous JavaScript.
* **Browserify**: Browserify will recursively analyze all the require() calls in your app in order to build a bundle you can serve up to the browser in a single <script> tag.
* **Bower**: Bower is a package manager for the web. It works by fetching and installing packages from all over, taking care of hunting, finding, downloading, and saving the stuff you’re looking for.
* **Backbone**: Backbone.js gives structure to web applications by providing models with key-value binding and custom events, collections with a rich API of enumerable functions, views with declarative event handling, and connects it all to your existing API over a RESTful JSON interface.
* **Csv**: csv module has four sub modules which provides CSV generation, parsing, transformation and serialization for Node.js.
* **Debug**: Debug is a tiny node.js debugging utility modelled after node core\'s debugging technique.
* **Express**: Express is a fast, un-opinionated, minimalist web framework. It provides small, robust tooling for HTTP servers, making it a great solution for single page applications, web sites, hybrids, or public HTTP APIs.
* **Forever**: A simple CLI tool for ensuring that a given node script runs continuously (i.e. forever).
* **Grunt**: is a JavaScript Task Runner that facilitates creating new projects and makes performing repetitive but necessary tasks such as linting, unit testing, concatenating and minifying files (among other things) trivial.
* **Gulp**: is a streaming build system that helps you automate painful or time-consuming tasks in your development workflow.
* **Hapi**: is a streaming build system that helps you automate painful or time-consuming tasks in your development workflow.
* **Http-server**: is a simple, zero-configuration command-line http server. It is powerful enough for production usage, but it\'s simple and hackable enough to be used for testing, local development, and learning.
* **Inquirer**: A collection of common interactive command line user interfaces.
* **Jquery**: jQuery is a fast, small, and feature-rich JavaScript library.
* **Jshint**: Static analysis tool to detect errors and potential problems in JavaScript code and to enforce your team\'s coding conventions.
* **Koa**: Koa is web app framework. It is an expressive HTTP middleware for node.js to make web applications and APIs more enjoyable to write.
* **Lodash**: The lodash library exported as a node module. Lodash is a modern JavaScript utility library delivering modularity, performance, & extras.
* **Less**: The less library exported as a node module.
* **Moment**: A lightweight JavaScript date library for parsing, validating, manipulating, and formatting dates.
* **Mongoose**: It is a MongoDB object modeling tool designed to work in an asynchronous environment.
* **MongoDB**: The official MongoDB driver for Node.js. It provides a high-level API on top of mongodb-core that is meant for end users.
* **Npm**: is package manager for javascript.
* **Nodemon**: It is a simple monitor script for use during development of a node.js app, It will watch the files in the directory in which nodemon was started, and if any files change, nodemon will automatically restart your node application.
* **Nodemailer**: This module enables e-mail sending from a Node.js applications.
* **Optimist**: is a node.js library for option parsing with an argv hash.
* **Phantomjs**: An NPM installer for PhantomJS, headless webkit with JS API. It has fast and native support for various web standards: DOM handling, CSS selector, JSON, Canvas, and SVG.
* **Passport**: A simple, unobtrusive authentication middleware for Node.js. Passport uses the strategies to authenticate requests. Strategies can range from verifying username and password credentials or authentication using OAuth or OpenID.
* **Q**: Q is a library for promises. A promise is an object that represents the return value or the thrown exception that the function may eventually provide.
* **Request**: Request is Simplified HTTP request client make it possible to make http calls. It supports HTTPS and follows redirects by default.
* **Socket.io**: Its a node.js realtime framework server.
* **Sails**: Sails : API-driven framework for building realtime apps, using MVC conventions (based on Express and Socket.io)
* **Through**: It enables simplified stream construction. It is easy way to create a stream that is both readable and writable.
* **Underscore**: Underscore.js is a utility-belt library for JavaScript that provides support for the usual functional suspects (each, map, reduce, filter...) without extending any core JavaScript objects.
* **Validator**: A nodejs module for a library of string validators and sanitizers.
* **Winston**: A multi-transport async logging library for Node.js
* **Ws**: A simple to use, blazing fast and thoroughly tested websocket client, server and console for node.js
* **Xml2js**: A Simple XML to JavaScript object converter.
* **Yo**: A CLI tool for running Yeoman generators
* **Zmq**: Bindings for node.js and io.js to ZeroMQ .It is a high-performance asynchronous messaging library, aimed at use in distributed or concurrent applications.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is EventEmitter in Node.js?***

All objects that emit events are members of EventEmitter class. These objects expose an `eventEmitter.on()` function that allows one or more functions to be attached to named events emitted by the object.

When the EventEmitter object emits an event, all of the functions attached to that specific event are called synchronously. All values returned by the called listeners are ignored and will be discarded.

*Example*:

```javascript
var events = require('events');
var eventEmitter = new events.EventEmitter();

// listener #1
var listner1 = function listner1() {
   console.log('listner1 executed.');
}

// listener #2
var listner2 = function listner2() {
   console.log('listner2 executed.');
}

// Bind the connection event with the listner1 function
eventEmitter.addListener('connection', listner1);

// Bind the connection event with the listner2 function
eventEmitter.on('connection', listner2);

var eventListeners = require('events').EventEmitter.listenerCount
   (eventEmitter,'connection');
console.log(eventListeners + " Listner(s) listening to connection event");

// Fire the connection event 
eventEmitter.emit('connection');

// Remove the binding of listner1 function
eventEmitter.removeListener('connection', listner1);
console.log("Listner1 will not listen now.");

// Fire the connection event 
eventEmitter.emit('connection');

eventListeners = require('events').EventEmitter.listenerCount(eventEmitter,'connection');
console.log(eventListeners + " Listner(s) listening to connection event");

console.log("Program Ended.");
```

Now run the main.js 

```bash
$ node main.js
```

Output

```bash
2 Listner(s) listening to connection event
listner1 executed.
listner2 executed.
Listner1 will not listen now.
listner2 executed.
1 Listner(s) listening to connection event
Program Ended.
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How many types of streams are present in node.js?***

Streams are objects that let you read data from a source or write data to a destination in continuous fashion.
There are four types of streams

* **Readable** − Stream which is used for read operation.
* **Writable** − Stream which is used for write operation.
* **Duplex** − Stream which can be used for both read and write operation.
* **Transform** − A type of duplex stream where the output is computed based on input.  

Each type of Stream is an EventEmitter instance and throws several events at different instance of times.  

*Example*:

* **data** − This event is fired when there is data is available to read.
* **end** − This event is fired when there is no more data to read.
* **error** − This event is fired when there is any error receiving or writing data.
* **finish** − This event is fired when all the data has been flushed to underlying system. 

**Reading from a Stream**

```javascript
var fs = require("fs");
var data = '';

// Create a readable stream
var readerStream = fs.createReadStream('input.txt');

// Set the encoding to be utf8. 
readerStream.setEncoding('UTF8');

// Handle stream events --> data, end, and error
readerStream.on('data', function(chunk) {
   data += chunk;
});

readerStream.on('end',function() {
   console.log(data);
});

readerStream.on('error', function(err) {
   console.log(err.stack);
});

console.log("Program Ended");
```

**Writing to a Stream**

```javascript
var fs = require("fs");
var data = 'Simply Easy Learning';

// Create a writable stream
var writerStream = fs.createWriteStream('output.txt');

// Write the data to stream with encoding to be utf8
writerStream.write(data,'UTF8');

// Mark the end of file
writerStream.end();

// Handle stream events --> finish, and error
writerStream.on('finish', function() {
   console.log("Write completed.");
});

writerStream.on('error', function(err) {
   console.log(err.stack);
});

console.log("Program Ended");
```

**Piping the Streams**

Piping is a mechanism where we provide the output of one stream as the input to another stream. It is normally used to get data from one stream and to pass the output of that stream to another stream. There is no limit on piping operations.

```javascript
var fs = require("fs");

// Create a readable stream
var readerStream = fs.createReadStream('input.txt');

// Create a writable stream
var writerStream = fs.createWriteStream('output.txt');

// Pipe the read and write operations
// read input.txt and write data to output.txt
readerStream.pipe(writerStream);

console.log("Program Ended");
```

**Chaining the Streams**

Chaining is a mechanism to connect the output of one stream to another stream and create a chain of multiple stream operations. It is normally used with piping operations.  

```javascript
var fs = require("fs");
var zlib = require('zlib');

// Compress the file input.txt to input.txt.gz
fs.createReadStream('input.txt')
   .pipe(zlib.createGzip())
   .pipe(fs.createWriteStream('input.txt.gz'));
  
console.log("File Compressed.");
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is crypto in Node.js? How do you cipher the secure information in Node.js?***

The Node.js Crypto module supports cryptography. It provides cryptographic functionality that includes a set of wrappers for open SSL\'s hash HMAC, cipher, decipher, sign and verify functions.

* **Hash**: A hash is a fixed-length string of bits i.e. procedurally and deterministically generated from some arbitrary block of source data.
* **HMAC**: HMAC stands for Hash-based Message Authentication Code. It is a process for applying a hash algorithm to both data and a secret key that results in a single final hash.

* Encryption Example using Hash and HMAC

```javascript
const crypto = require('crypto');  
const secret = 'abcdefg';  
const hash = crypto.createHmac('sha256', secret)  
                   .update('Welcome to JavaTpoint')  
                   .digest('hex');  
console.log(hash);  
```

* Encryption example using Cipher

```javascript
const crypto = require('crypto');  
const cipher = crypto.createCipher('aes192', 'a password');  
var encrypted = cipher.update('Hello JavaTpoint', 'utf8', 'hex');  
encrypted += cipher.final('hex');  
console.log(encrypted);
```

* Decryption example using Decipher

```javascript
const crypto = require('crypto');  
const decipher = crypto.createDecipher('aes192', 'a password');  
var encrypted = '4ce3b761d58398aed30d5af898a0656a3174d9c7d7502e781e83cf6b9fb836d5';  
var decrypted = decipher.update(encrypted, 'hex', 'utf8');  
decrypted += decipher.final('utf8');  
console.log(decrypted);  
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the use of DNS module in Node.js?***

DNS is a node module used to do name resolution facility which is provided by the operating system as well as used to do an actual DNS lookup. No need for memorising IP addresses – DNS servers provide a nifty solution of converting domain or subdomain names to IP addresses. This module provides an asynchronous network wrapper and can be imported using the following syntax.

```javascript
const dns = require('dns');
```

*Example*: `dns.lookup()` function  

```javascript
const dns = require('dns');  
dns.lookup('www.google.com', (err, addresses, family) => {  
  console.log('addresses:', addresses);  
  console.log('family:',family);  
});  
```

*Example*: `resolve4()` and `reverse()` functions

```javascript
const dns = require('dns');  
dns.resolve4('www.google.com', (err, addresses) => {  
  if (err) throw err;  
  console.log(`addresses: ${JSON.stringify(addresses)}`);  
  addresses.forEach((a) => {  
    dns.reverse(a, (err, hostnames) => {  
      if (err) {  
        throw err;  
      }  
      console.log(`reverse for ${a}: ${JSON.stringify(hostnames)}`);  
    });  
  });  
});
```

*Example*: print the localhost name using `lookupService()` function

```javascript
const dns = require('dns');  
dns.lookupService('127.0.0.1', 22, (err, hostname, service) => {  
  console.log(hostname, service);  
    // Prints: localhost  
});
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are the security mechanisms available in Node.js?***

**Using the Helmet module**

Helmet helps to secure your Express applications by setting various HTTP headers, like:

* X-Frame-Options to mitigates clickjacking attacks,
* Strict-Transport-Security to keep your users on HTTPS,
* X-XSS-Protection to prevent reflected XSS attacks,
* X-DNS-Prefetch-Control to disable browsers DNS prefetching.

```javascript
const express = require('express')
const helmet = require('helmet')
const app = express()

app.use(helmet())
```

**Validating user input**

Validating user input is one of the most important things to do when it comes to the security of your application. Failing to do it correctly can open up your application and users to a wide range of attacks, including command injection, SQL injection or stored cross-site scripting.

To validate user input, one of the best libraries you can pick is joi. Joi is an object schema description language and validator for JavaScript objects.

```javascript
const Joi = require('joi');

const schema = Joi.object().keys({
    username: Joi.string().alphanum().min(3).max(30).required(),
    password: Joi.string().regex(/^[a-zA-Z0-9]{3,30}$/),
    access_token: [Joi.string(), Joi.number()],
    birthyear: Joi.number().integer().min(1900).max(2013),
    email: Joi.string().email()
}).with('username', 'birthyear').without('password', 'access_token')

// Return result
const result = Joi.validate({
    username: 'abc',
    birthyear: 1994
}, schema)
// result.error === null -> valid
```

**Securing your Regular Expressions**

Regular Expressions are a great way to manipulate texts and get the parts that you need from them. However, there is an attack vector called Regular Expression Denial of Service attack, which exposes the fact that most Regular Expression implementations may reach extreme situations for specially crafted input, that cause them to work extremely slowly.

The Regular Expressions that can do such a thing are commonly referred as Evil Regexes. These expressions contain:
*grouping with repetition,
*inside the repeated group:
    *repetition, or
    *alternation with overlapping  

Examples of Evil Regular Expressions patterns:

```bash
(a+)+
([a-zA-Z]+)*
(a|aa)+
```

**Security.txt**

Security.txt defines a standard to help organizations define the process for security researchers to securely disclose security vulnerabilities.

```javascript
const express = require('express')
const securityTxt = require('express-security.txt')

const app = express()

app.get('/security.txt', securityTxt({
  // your security address
  contact: 'email@example.com',
  // your pgp key
  encryption: 'encryption',
  // if you have a hall of fame for securty resourcers, include the link here
  acknowledgements: 'http://acknowledgements.example.com'
}))
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Name the types of API functions in Node.js?***

There are two types of API functions in Node.js:

* Asynchronous, Non-blocking functions
* Synchronous, Blocking functions

**1. Blocking functions**

In a blocking operation, all other code is blocked from executing until an I/O event that is being waited on occurs. Blocking functions execute synchronously.

*Example*:

```javascript
const fs = require('fs');
const data = fs.readFileSync('/file.md'); // blocks here until file is read
console.log(data);
// moreWork(); will run after console.log
```

The second line of code blocks the execution of additional JavaScript until the entire file is read. moreWork () will only be called after Console.log

**2. Non-blocking functions**

In a non-blocking operation, multiple I/O calls can be performed without the execution of the program being halted. Non-blocking functions execute asynchronously.

*Example*:

```javascript
const fs = require('fs');
fs.readFile('/file.md', (err, data) => {
  if (err) throw err;
  console.log(data);
});
// moreWork(); will run before console.log
```

Since `fs.readFile()` is non-blocking, moreWork() does not have to wait for the file read to complete before being called. This allows for higher throughput.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How does Node.js handle child threads?***

Node.js is a single threaded language which in background uses multiple threads to execute asynchronous code.
Node.js is non-blocking which means that all functions ( callbacks ) are delegated to the event loop and they are ( or can be ) executed by different threads. That is handled by Node.js run-time.

* Nodejs Primary application runs in an event loop, which is in a single thread.
* Background I/O is running in a thread pool that is only accessible to C/C++ or other compiled/native modules and mostly transparent to the JS.
* Node v11/12 now has experimental worker_threads, which is another option.
* Node.js does support forking multiple processes ( which are executed on different cores ).
* It is important to know that state is not shared between master and forked process.
* We can pass messages to forked process ( which is different script ) and to master process from forked process with function send.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the preferred method of resolving unhandled exceptions in Node.js?***

Unhandled exceptions in Node.js can be caught at the Process level by attaching a handler for uncaughtException event.

```javascript
process.on('uncaughtException', function(err) {
    console.log('Caught exception: ' + err);
});
```

Process is a global object that provides information about the current Node.js process. Process is a listener function that is always listening to events.

Few events are :

1. Exit
1. disconnect
1. unhandledException
1. rejectionHandled

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How does Node.js support multi-processor platforms, and does it fully utilize all processor resources?***

Since Node.js is by default a single thread application, it will run on a single processor core and will not take full advantage of multiple core resources. However, Node.js provides support for deployment on multiple-core systems, to take greater advantage of the hardware. The Cluster module is one of the core Node.js modules and it allows running multiple Node.js worker processes that will share the same port.

The cluster module helps to spawn new processes on the operating system. Each process works independently, so you cannot use shared state between child processes. Each process communicates with the main process by IPC and pass server handles back and forth.

Cluster supports two types of load distribution:

* The main process listens on a port, accepts new connection and assigns it to a child process in a round robin fashion.
* The main process assigns the port to a child process and child process itself listen the port.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is typically the first argument passed to a Node.js callback handler?***

The first argument to any callback handler is an optional error object

```javascript
function callback(err, results) {
    // usually we'll check for the error before handling results
    if(err) {
        // handle error somehow and return
    }
    // no error, perform standard callback handling
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How Node.js read the content of a file?***

The "normal" way in Node.js is probably to read in the content of a file in a non-blocking, asynchronous way. That is, to tell Node to read in the file, and then to get a callback when the file-reading has been finished. That would allow us to hand several requests in parallel.

Common use for the File System module:

* Read files
* Create files
* Update files
* Delete files
* Rename files  

**Read Files**  
index.html

```html
<html>
<body>
  <h1>My Header</h1>
  <p>My paragraph.</p>
</body>
</html>
```

```javascript
// read_file.js

var http = require('http');
var fs = require('fs');
http.createServer(function (req, res) {
  fs.readFile('index.html', function(err, data) {
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.write(data);
    res.end();
  });
}).listen(8080);
```

Initiate read_file.js:

```bash
node read_file.js
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is JIT and how is it related to Node.js?***
 
Node.js has depended on the V8 JavaScript engine to provide code execution in the language. The V8 is a JavaScript engine built at the google development center, in Germany. It is open source and written in C++. It is used for both client side (Google Chrome) and server side (node.js) JavaScript applications. A central piece of the V8 engine that allows it to execute JavaScript at high speed is the JIT (Just In Time) compiler. This is a dynamic compiler that can optimize code during runtime. When V8 was first built the JIT Compiler was dubbed FullCodegen. Then, the V8 team implemented Crankshaft, which included many performance optimizations that FullCodegen did not implement.

The `V8` was first designed to increase the performance of the JavaScript execution inside web browsers. In order to obtain speed, V8 translates JavaScript code into more efficient machine code instead of using an interpreter. It compiles JavaScript code into machine code at execution by implementing a JIT (Just-In-Time) compiler like a lot of modern JavaScript engines such as SpiderMonkey or Rhino (Mozilla) are doing. The main difference with V8 is that it doesn’t produce bytecode or any intermediate code.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is difference between put and patch?***

PUT and PATCH are HTTP verbs and they both relate to updating a resource. The main difference between PUT and PATCH requests are in the way the server processes the enclosed entity to modify the resource identified by the Request-URI.

In a PUT request, the enclosed entity is considered to be a modified version of the resource stored on the origin server, and the client is requesting that the stored version be replaced.

With PATCH, however, the enclosed entity contains a set of instructions describing how a resource currently residing on the origin server should be modified to produce a new version.

Also, another difference is that when you want to update a resource with PUT request, you have to send the full payload as the request whereas with PATCH, you only send the parameters which you want to update.

The most commonly used HTTP verbs POST, GET, PUT, DELETE are similar to CRUD (Create, Read, Update and Delete) operations in database. We specify these HTTP verbs in the capital case. So, the below is the comparison between them.

* `POST` - create
* `GET`  - read  
* `PUT`  - update
* `DELETE` - delete

**PATCH**: Submits a partial modification to a resource. If you only need to update one field for the resource, you may want to use the PATCH method.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***List types of Http requests supported by Node.js?***

The HTTP core module is a key module to Node.js networking.

```javascript
const http = require('http')
```

**http.METHODS**

```javascript
require('http').METHODS
[ 'ACL',
  'BIND',
  'CHECKOUT',
  'CONNECT',
  'COPY',
  'DELETE',
  'GET',
  'HEAD',
  'LINK',
  'LOCK',
  'M-SEARCH',
  'MERGE',
  'MKACTIVITY',
  'MKCALENDAR',
  'MKCOL',
  'MOVE',
  'NOTIFY',
  'OPTIONS',
  'PATCH',
  'POST',
  'PROPFIND',
  'PROPPATCH',
  'PURGE',
  'PUT',
  'REBIND',
  'REPORT',
  'SEARCH',
  'SUBSCRIBE',
  'TRACE',
  'UNBIND',
  'UNLINK',
  'UNLOCK',
  'UNSUBSCRIBE' ]
  ```

**http.STATUS_CODES**

  ```javascript
  require('http').STATUS_CODES
{ '100': 'Continue',
  '101': 'Switching Protocols',
  '102': 'Processing',
  '200': 'OK',
  '201': 'Created',
  '202': 'Accepted',
  '203': 'Non-Authoritative Information',
  '204': 'No Content',
  '205': 'Reset Content',
  '206': 'Partial Content',
  '207': 'Multi-Status',
  '208': 'Already Reported',
  '226': 'IM Used',
  '300': 'Multiple Choices',
  '301': 'Moved Permanently',
  '302': 'Found',
  '303': 'See Other',
  '304': 'Not Modified',
  '305': 'Use Proxy',
  '307': 'Temporary Redirect',
  '308': 'Permanent Redirect',
  '400': 'Bad Request',
  '401': 'Unauthorized',
  '402': 'Payment Required',
  '403': 'Forbidden',
  '404': 'Not Found',
  '405': 'Method Not Allowed',
  '406': 'Not Acceptable',
  '407': 'Proxy Authentication Required',
  '408': 'Request Timeout',
  '409': 'Conflict',
  '410': 'Gone',
  '411': 'Length Required',
  '412': 'Precondition Failed',
  '413': 'Payload Too Large',
  '414': 'URI Too Long',
  '415': 'Unsupported Media Type',
  '416': 'Range Not Satisfiable',
  '417': 'Expectation Failed',
  '418': 'I\'m a teapot',
  '421': 'Misdirected Request',
  '422': 'Unprocessable Entity',
  '423': 'Locked',
  '424': 'Failed Dependency',
  '425': 'Unordered Collection',
  '426': 'Upgrade Required',
  '428': 'Precondition Required',
  '429': 'Too Many Requests',
  '431': 'Request Header Fields Too Large',
  '451': 'Unavailable For Legal Reasons',
  '500': 'Internal Server Error',
  '501': 'Not Implemented',
  '502': 'Bad Gateway',
  '503': 'Service Unavailable',
  '504': 'Gateway Timeout',
  '505': 'HTTP Version Not Supported',
  '506': 'Variant Also Negotiates',
  '507': 'Insufficient Storage',
  '508': 'Loop Detected',
  '509': 'Bandwidth Limit Exceeded',
  '510': 'Not Extended',
  '511': 'Network Authentication Required' }
  ```

**Making HTTP Requests**

```javascript
const request = require('request');

request('https://nodejs.org/', function(err, res, body) {
    console.log(body);
});
```

The first argument to request can either be a URL string, or an object of options. Here are some of the more common options you\'ll encounter in your applications:

* **url**: The destination URL of the HTTP request
* **method**: The HTTP method to be used (GET, POST, DELETE, etc)
* **headers**: An object of HTTP headers (key-value) to be set in the request
* **form**: An object containing key-value form data

```javascript
const request = require('request');

const options = {
    url: 'https://nodejs.org/file.json',
    method: 'GET',
    headers: {
        'Accept': 'application/json',
        'Accept-Charset': 'utf-8',
        'User-Agent': 'my-reddit-client'
    }
};

request(options, function(err, res, body) {
    let json = JSON.parse(body);
    console.log(json);
});
```

Using the options object, this request uses the GET method to retrieve JSON data directly from Reddit, which is returned as a string in the body field. From here, you can use `JSON.parse` and use the data as a normal JavaScript object.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Why to use Express.js?***

ExpressJS is a prebuilt NodeJS framework that can help you in creating server-side web applications faster and smarter. Simplicity, minimalism, flexibility, scalability are some of its characteristics and since it is made in NodeJS itself, it inherited its performance as well.

Express 3.x is a light-weight web application framework to help organize your web application into an MVC architecture on the server side. You can then use a database like `MongoDB` with `Mongoose` (for modeling) to provide a backend for your Node.js application. Express.js basically helps you manage everything, from routes, to handling requests and views.

It has become the standard server framework for node.js. Express is the backend part of something known as the MEAN stack. The MEAN is a free and open-source JavaScript software stack for building dynamic web sites and web applications which has the following components;

1. **MongoDB** - The standard NoSQL database
2. **Express.js** - The default web applications framework
3. **Angular.js** - The JavaScript MVC framework used for web applications
4. **Node.js** - Framework used for scalable server-side and networking applications.

The Express.js framework makes it very easy to develop an application which can be used to handle multiple types of requests like the GET, PUT, and POST and DELETE requests.

**using Express**

```javascript
var express=require('express');
var app=express();
app.get('/',function(req,res) {
  res.send('Hello World!');
});
var server=app.listen(3000,function() {});
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Write the steps for setting up an Express JS application?***

**1. Install Express Generator**

```bash
C:\node>npm install -g express-generator
```

**2. Create an Express Project**

```bash
C:\node>express --view="ejs" nodetest1
```

**3. Edit Dependencies**

MAKE SURE TO CD INTO YOUR nodetest FOLDER. OK, now we have some basic structure in there, but we're not quite done. You'll note that the express-generator routine created a file called package.json in your nodetest1 directory. Open this up in a text editor and it'll look like this:
```javascript
// C:\node\nodetest1\package.json
{
  "name": "nodetest1",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "start": "node ./bin/www"
  },
  "dependencies": {
    "cookie-parser": "~1.4.3",
    "debug": "~2.6.9",
    "ejs": "~2.5.7",
    "express": "~4.16.0",
    "http-errors": "~1.6.2",
    "morgan": "~1.9.0"
  }
}
```

This is a basic JSON file describing our app and its dependencies. We need to add a few things to it. Specifically, calls for MongoDB and Monk. 

```bash
C:\node\nodetest1>npm install --save monk@^6.0.6 mongodb@^3.1.13
```

**4. Install Dependencies**

```bash
C:\node\nodetest1>npm install
C:\node\nodetest1>npm start
```

Node Console

```bash
> nodetest1@0.0.0 start C:\node\nodetest1
> node ./bin/www
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Since node is a single threaded process, how to make use of all CPUs?***

Node.js is a single threaded language which in background uses multiple threads to execute asynchronous code.
Node.js is non-blocking which means that all functions ( callbacks ) are delegated to the event loop and they are ( or can be ) executed by different threads. That is handled by Node.js run-time.

* Node.js does support forking multiple processes ( which are executed on different cores ).
* It is important to know that state is not shared between master and forked process.
* We can pass messages to forked process ( which is different script ) and to master process from forked process with function send.

A single instance of Node.js runs in a single thread. To take advantage of multi-core systems, the user will sometimes want to launch a cluster of Node.js processes to handle the load. The cluster module allows easy creation of child processes that all share server ports.

```javascript
const cluster = require('cluster');
const http = require('http');
const numCPUs = require('os').cpus().length;

if (cluster.isMaster) {
  console.log(`Master ${process.pid} is running`);

  // Fork workers.
  for (let i = 0; i < numCPUs; i++) {
    cluster.fork();
  }

  cluster.on('exit', (worker, code, signal) => {
    console.log(`worker ${worker.process.pid} died`);
  });
} else {
  // Workers can share any TCP connection
  // In this case it is an HTTP server
  http.createServer((req, res) => {
    res.writeHead(200);
    res.end('hello world\n');
  }).listen(8000);

  console.log(`Worker ${process.pid} started`);
}
```

Running Node.js will now share port 8000 between the workers:

```bash
$ node server.js
Master 3596 is running
Worker 4324 started
Worker 4520 started
Worker 6056 started
Worker 5644 started
```

The worker processes are spawned using the `child_process.fork()` method, so that they can communicate with the parent via IPC and pass server handles back and forth.

The cluster module supports two methods of distributing incoming connections.

The first one (and the default one on all platforms except Windows), is the round-robin approach, where the master process listens on a port, accepts new connections and distributes them across the workers in a round-robin fashion, with some built-in smarts to avoid overloading a worker process.

The second approach is where the master process creates the listen socket and sends it to interested workers. The workers then accept incoming connections directly.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What does emitter do and what is dispatcher?***

Node.js core API is based on asynchronous event-driven architecture in which certain kind of objects called emitters periodically emit events that cause listener objects to be called.

All objects that emit events are members of EventEmitter class. These objects expose an eventEmitter.on() function that allows one or more functions to be attached to named events emitted by the object.

When the EventEmitter object emits an event, all of the functions attached to that specific event are called synchronously. All values returned by the called listeners are ignored and will be discarded.

```javascript
const EventEmitter = require('events');
class MyEmitter extends EventEmitter {}
const myEmitter = new MyEmitter();
myEmitter.on('event', function(a, b) {
  console.log(a, b, this);
  // Prints:
  //   Technoetics Club MyEmitter {
  //     domain: null,
  //     _events: { event: [Function] },
  //     _eventsCount: 1,
  //     _maxListeners: undefined }
});
myEmitter.emit('event','Technoetics', 'Club');
```

Here we create a myEmitter object and emit event at the end which triggers the callback function and we are able to get the desired output.

By default, all listeners attached to a particular event object are called by the EventListener object synchronously in the order in which they are registered or attached to the event object.

**Dispatcher**

The Dispatcher has functionality not provided nor expected in EventEmitter, the most notable being waitFor, which allows a store to ensure that another store has been updated in response to an action before it proceeds.

Pattern-wise, the Dispatcher is also a singleton, whereas EventEmitter is an API that you might object-assign onto multiple stores.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to kill child processes that spawn their own child processes in Node.js?***

If a child process in Node.js spawn their own child processes, kill() method will not kill the child process’s own child processes. For example, if I start a process that starts it’s own child processes via child_process module, killing that child process will not make my program to quit.

```javascript
var spawn = require('child_process').spawn;
var child = spawn('my-command');

child.kill();
```

The program above will not quit if `my-command` spins up some more processes.

**PID range hack**

We can start child processes with {detached: true} option so those processes will not be attached to main process but they will go to a new group of processes. Then using process.kill(-pid) method on main process we can kill all processes that are in the same group of a child process with the same pid group. In my case, I only have one processes in this group.

```javascript
var spawn = require('child_process').spawn;
var child = spawn('my-command', {detached: true});

process.kill(-child.pid);
```

Please note - before pid. This converts a pid to a group of pids for process kill() method.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What do you understand by Reactor Pattern in Node.js?***

Reactor Pattern is an idea of non-blocking I/O operations in Node.js. This pattern provides a handler(in case of Node.js, a callback function) that is associated with each I/O operation. When an I/O request is generated, it is submitted to a demultiplexer.

This demultiplexer is a notification interface that is used to handle concurrency in non-blocking I/O mode and collects every request in form of an event and queues each event in a queue. Thus, the demultiplexer provides the Event Queue, which we often hear. When a request is collected by the demultiplexer, it returns the control back to the system and does not blocks the I/O. At the same time, there is an Event Loop which iterates over the items in the Event Queue. Every event has a callback function associated with it, and that callback function is invoked when the Event Loop iterates.

The callback function further mostly have other callbacks associated within representing some asynchronous operations. These operations are inserted in the Event Queue by the demultiplexer and are ready to be processed once the Event Loop iterates over them. That is why calls to other operations must be asynchronous.

When all the items in the Event Queue are processed and there are no pending operations left, Node.js terminates the application automatically.

<p align="center">
  <img src="assets/reactor-pattern.jpg" alt="Test Pyramid" width="800px" />
</p>

1. The application generates a new I/O operation by submitting a request to the Event Demultiplexer. The application also specifies a handler, which will be invoked when the operation completes. Submitting a new request to the Event Demultiplexer is a non-blocking call and it immediately returns the control back to the application.
2. When a set of I/O operations completes, the Event Demultiplexer pushes the new events into the Event Queue.
3. At this point, the Event Loop iterates over the items of the Event Queue.
4. For each event, the associated handler is invoked.
5. The handler, which is part of the application code, will give back the control to the Event Loop when its execution completes (5a). However, new asynchronous operations might be requested during the execution of the handler (5b), causing new operations to be inserted in the Event Demultiplexer (1), before the control is given back to the Event Loop.
6. When all the items in the Event Queue are processed, the loop will block again on the Event Demultiplexer which will then trigger another cycle.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are the key features of Node.js?***

* **Asynchronous event driven IO helps concurrent request handling** – All APIs of Node.js are asynchronous. This feature means that if a Node receives a request for some Input/Output operation, it will execute that operation in the background and continue with the processing of other requests. Thus it will not wait for the response from the previous requests.
* **Fast in Code execution** – Node.js uses the V8 JavaScript Runtime engine, the one which is used by Google Chrome. Node has a wrapper over the JavaScript engine which makes the runtime engine much faster and hence processing of requests within Node.js also become faster.
* **Single Threaded but Highly Scalable** – Node.js uses a single thread model for event looping. The response from these events may or may not reach the server immediately. However, this does not block other operations. Thus making Node.js highly scalable. Traditional servers create limited threads to handle requests while Node.js creates a single thread that provides service to much larger numbers of such requests.
* **Node.js library uses JavaScript** – This is another important aspect of Node.js from the developer’s point of view. The majority of developers are already well-versed in JavaScript. Hence, development in Node.js becomes easier for a developer who knows JavaScript.
* **There is an Active and vibrant community for the Node.js framework** – The active community always keeps the framework updated with the latest trends in the web development.
* **No Buffering** – Node.js applications never buffer any data. They simply output the data in chunks.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are globals in Node.js?***

There are three keywords in Node.js which constitute as Globals. These are Global, Process, and Buffer.

**1. Global**

The Global keyword represents the global namespace object. It acts as a container for all other `global` objects. If we type `console.log(global)`, it will print out all of them.

An important point to note about the global objects is that not all of them are in the global scope, some of them fall in the module scope. So, it is wise to declare them without using the var keyword or add them to Global object.

Variables declared using the var keyword become local to the module whereas those declared without it get subscribed to the global object.

**2. Process**

It is also one of the global objects but includes additional functionality to turn a synchronous function into an async callback. There is no boundation to access it from anywhere in the code. It is the instance of the EventEmitter class. And each node application object is an instance of the Process object.

It primarily gives back the information about the application or the environment.

* `<process.execPath>` – to get the execution path of the Node app.
* `<process.Version>` – to get the Node version currently running.
* `<process.platform>` – to get the server platform.

Some of the other useful Process methods are as follows.

* `<process.memoryUsage>` – To know the memory used by Node application.
* `<process.NextTick>` – To attach a callback function that will get called during the next loop. It can cause a delay in executing a function.

**3. Buffer**

The Buffer is a class in Node.js to handle binary data. It is similar to a list of integers but stores as a raw memory outside the V8 heap.

We can convert JavaScript string objects into Buffers. But it requires mentioning the encoding type explicitly.

* `<ascii>` – Specifies 7-bit ASCII data.
* `<utf8>` – Represents multibyte encoded Unicode char set.
* `<utf16le>` – Indicates 2 or 4 bytes, little endian encoded Unicode chars.
* `<base64>` – Used for Base64 string encoding.
* `<hex>` – Encodes each byte as two hexadecimal chars.

Here is the syntax to use the Buffer class.

```javascript
var buffer = new Buffer(string, [encoding]);
```

The above command will allocate a new buffer holding the string with `utf8` as the default encoding. However, if you like to write a `string` to an existing buffer object, then use the following line of code.

```javascript
buffer.write(string)
```

This class also offers other methods like `readInt8` and `writeUInt8` that allows read/write from various types of data to the buffer.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is chaining process in Node.js?***

It is an approach to connect the output of one stream to the input of another stream, thus creating a chain of multiple stream operations.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a control flow function? what are the steps does it execute?***

It is a generic piece of code which runs in between several asynchronous function calls is known as control flow function.

It executes the following steps.

* Control the order of execution.
* Collect data.
* Limit concurrency.
* Call the next step in the program.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is npm in Node.js?***

NPM stands for Node Package Manager. It provides following two main functionalities.

* It works as an Online repository for node.js packages/modules which are present at <nodejs.org>.
* It works as Command line utility to install packages, do version management and dependency management of Node.js packages.
NPM comes bundled along with Node.js installable. We can verify its version using the following command-

```bash
npm --version
```

NPM helps to install any Node.js module using the following command.

```bash
npm install <Module Name>
```

For example, following is the command to install a famous Node.js web framework module called express-

```bash
npm install express
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***When to use Node.js and when not to use it?***

**When to use Node.js** 

It is ideal to use Node.js for developing streaming or event-based real-time applications that require less CPU usage such as.

* Chat applications.
* Game servers -- Node.js is good for fast and high-performance servers, that face the need to handle thousands of user requests simultaneously.

* Good For A Collaborative Environment -- It is suitable for environments where multiple people work together. For example, they post their documents, modify them by doing check-out and check-in of these documents. Node.js supports such situations by creating an event loop for every change made to the document. The “Event loop” feature of Node.js enables it to handle multiple events simultaneously without getting blocked.

* Advertisement Servers -- Here again, we have servers that handle thousands of request for downloading advertisements from a central host. And Node.js is an ideal solution to handle such tasks.

* Streaming Servers -- Another ideal scenario to use Node.js is for multimedia streaming servers where clients fire request’s towards the server to download different multimedia contents from it.

To summarize, it’s good to use Node.js, when you need high levels of concurrency but less amount of dedicated CPU time.

Last but not the least, since Node.js uses JavaScript internally, so it fits best for building client-side applications that also use JavaScript.

**When to not use Node.js**

However, we can use Node.js for a variety of applications. But it is a single threaded framework, so we should not use it for cases where the application requires long processing time. If the server is doing some calculation, it won’t be able to process any other requests. Hence, Node.js is best when processing needs less dedicated CPU time.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Explain how does Node.js work?***

A Node.js application creates a single thread on its invocation. Whenever Node.js receives a request, it first completes its processing before moving on to the next request.

Node.js works asynchronously by using the event loop and callback functions, to handle multiple requests coming in parallel. An Event Loop is a functionality which handles and processes all your external events and just converts them to a callback function. It invokes all the event handlers at a proper time. Thus, lots of work is done on the back-end, while processing a single request, so that the new incoming request doesn’t have to wait if the processing is not complete.

While processing a request, Node.js attaches a callback function to it and moves it to the back-end. Now, whenever its response is ready, an event is called which triggers the associated callback function to send this response.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Is Node.js entirely based on a single-thread?***

Yes, it is true that Node.js processes all requests on a single thread. But it is just a part of the theory behind Node.js design. In fact, more than the single thread mechanism, it makes use of events and callbacks to handle a large no. of requests asynchronously.

Moreover, Node.js has an optimized design which utilizes both JavaScript and C++ to guarantee maximum performance. JavaScript executes at the server-side by Google Chrome v8 engine. And the C++ lib UV library takes care of the non-sequential I/O via background workers.

To explain it practically, let’s assume there are 100s of requests lined up in Node.js queue. As per design, the main thread of Node.js event loop will receive all of them and forwards to background workers for execution. Once the workers finish processing requests, the registered callbacks get notified on event loop thread to pass the result back to the user.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to make post request in Node.js?***

Following code snippet can be used to make a Post Request in Node.js.

```javascript
var request = require('request');
    request.post('http://www.example.com/action', { form: { key: 'value' } },
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        }
    });
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Can you create http server in Node.js, explain the code used for it?***

Yes, we can create HTTP Server in Node.js. We can use the `<http-server>` command to do so.

Following is the sample code.

```javascript
var http = require('http');
var requestListener = function (request, response) {
    response.writeHead(200, {'Content-Type': 'text/plain'});
    response.end('Welcome Viewers\n');
}
var server = http.createServer(requestListener);
server.listen(4200); // The port where you want to start with.
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to load html in Node.js?***

To load HTML in Node.js we have to change the “Content-type” in the HTML code from text/plain to text/html.

```javascript
fs.readFile(filename, "binary", function(err, file) {
    if(err) { 
        response.writeHead(500, {"Content-Type": "text/plain"});
        response.write(err + "\n");
        response.end();
        return;
    }

response.writeHead(200);
response.write(file, "binary");
response.end();
});
```

Now we will modify this code to load an HTML page instead of plain text.

```javascript
fs.readFile(filename, "binary", function(err, file) {
    if(err) { 
        response.writeHead(500, {"Content-Type": "text/html"});
        response.write(err + "\n");
        response.end();
        return;
    }

response.writeHead(200, {"Content-Type": "text/html"});
response.write(file);
response.end();
});
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How can you listen on port 80 with Node?***

Instead of running on port 80 we can redirect port 80 to your application\'s port (>1024) using

```bash
iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3000
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the difference between operational and programmer errors?***

Operation errors are not bugs, but problems with the system, like request timeout or hardware failure. On the other hand programmer errors are actual bugs.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Why npm shrinkwrap is useful?***

NPM shrinkwrap lets you lock down the ver­sions of installed pack­ages and their descen­dant pack­ages. It helps you use same package versions on all environments (development, staging, production) and also improve download and installation speed. Having same versions of packages on all environments can help you test systems and deploy with confidence. If all tests pass on one machine, you can be sure that it will pass on all other because you know that you use same code!

```bash
npm shrinkwrap
```

It should create new npm-shrinkwrap.json file with information about all packages you use.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is your favourite HTTP framework and why?***

**Express.js**

Express provides a thin layer on top of Node.js with web application features such as basic routing, middleware, template engine and static files serving, so the drastic I/O performance of Node.js doesn’t get compromised.

Express is a minimal, un-opinionated framework. it doesn’t apply any of the prevalent design patterns such as MVC, MVP, MVVM or whatever is trending out of the box. For fans of simplicity, this is a big plus among all other frameworks because you can build your application with your own preference and no unnecessary learning curve. This is especially advantageous when creating a new personal project with no historical burden, but as the project or developing team grows, lack of standardization may lead to extra work for project/code management, and worst case scenario it may lead to the inability to maintain.  

**Generator**

Even though the framework is un-opinionated, it does have the generator that generates specific project folder structure. After installing express-generator npm package and creating application skeleton with generator command, an application folder with clear hierarchy will be created to help you organize images, front-end static JavaScript, stylesheet files and HTML template files.

```bash
npm install express-generator -g
express helloapp
```

**Middleware**  

Middleware are basically just functions that have full access to both request and response objects.

```javascript
var app = express();

app.use(cookieParser());
app.use(bodyParser());
app.use(logger());
app.use(authentication());

app.get('/', function (req, res) {
  // ...
});

app.listen(3000);
```

An Express application is essentially Node.js with a host of middleware functions, whether you want to customize your own middleware or take advantage of the built-in middlewares of the framework, Express made the process natural and intuitive.

**Template Engine**

Template engines allow developer to embed backend variables into HTML files, and when requested the template file will be rendered to plain HTML format with the variables interpolated with their actual values. By default, the express-generator uses Pug (originally known as Jade) template engine, but other options like Mustache and EJS also work with Express seamlessly.

**Database Integration**  

As a minimal framework, Express does not consider database integration as a required aspect within its package, thus it leans toward no specific database usage whatsoever. While adopting a particular data storage technology, be it MySQL, MongoDB, PostgreSQL, Redis, ElasticSearch or something else, it’s just a matter of installing the particular npm package as database driver. These third party database drivers do not conform to unified syntax when doing CRUD instructions, which makes switching databases a big hassle and error prone.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are the Challenges with Node.js?***

**Challenges with Node.js Application Maintenance**

Improper maintenance of an application can result in issues related to stability or flexibility, often leading to the app\'s failure. If the code is not well-written or if developers use outdated tools, the performance can suffer, and users might experience more bugs and app crashes. On top of that, poor-quality code can hamper the app’s scaling capacity and the further development of the application. In the worst case scenario, it might become impossible to introduce new features without rewriting the codebase from scratch.

1. Extensive stack
2. Technical Debt
3. Scalability challanges
4. Poor documentation

**How to Deal With Maintenance Problems**

1. Conduct code review
2. Use microservices
3. Improve code quality
4. Test before new feature implementation
5. Improve documentation
6. Update the stack
7. Dig into the roots

## Q. ***What is the difference between Node.js vs Ajax?***

**1. AJAX**

AJAX stands for Asynchronous Javascript and XML, it’s used to allow web pages (client-side) to update asynchronously by communicating with a web server and by exchanging data. This essentially means that applications can talk to a server in the background of the application. It uses some core components to function:

1. The browser `XMLHttpRequest` object to request data from a server
1. HTML/CSS to display or collect data
1. DOM for dynamic display
1. JSON/XML for interchanging the data
1. Javascript to unify everything

**2. Node.js**

Node.js allows the developers to develop a web application in a single language called JavaScript for both client side and server side.

Unlike the other programming languages, Node.js has its cycle of the event in the form of language which is very beneficial for high-performance and scalable application development.

It is required for those web applications where traffic rate is very high. Node.js is an event based I/O language and its response time is very high rather than the other traditional languages. It is being used by the famous websites like Linked in, Twitter and Gmail.

The runtime environment of Node.js interprets JavaScript, which is very easy and simple to understand and code. Due to this reason, even the developers find it easy going which keeps them happy and relaxed. It is pertinent for real-time collaborative apps.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How Node.js overcomes the problem of blocking of I/O operations?***

Node.js solves this problem by putting the event based model at its core, using an event loop instead of threads. 

Node.js uses an event loop for this. An event loop is “an entity that handles and processes external events and converts them into callback invocations”. Whenever data is needed nodejs registers a callback and sends the operation to this event loop. Whenever the data is available the callback is called.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Mention the steps by which you can async in Node.js?***

ES 2017 introduced Asynchronous functions. Async functions are essentially a cleaner way to work with asynchronous code in JavaScript. 

**Async/Await**

* The newest way to write asynchronous code in JavaScript.
* It is non blocking (just like promises and callbacks).
* Async/Await was created to simplify the process of working with and writing chained promises.
* Async functions return a Promise. If the function throws an error, the Promise will be rejected. If the function returns a value, the Promise will be resolved.  

Syntax

```javascript
// Normal Function
function add(x,y){
  return x + y;
}
// Async Function
async function add(x,y){
  return x + y;
}
```

**Await**

Async functions can make use of the await expression. This will pause the async function and wait for the Promise to resolve prior to moving on.  

*Example*:

```javascript
function doubleAfter2Seconds(x) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(x * 2);
    }, 2000);
  });
}

async function addAsync(x) {
  const a = await doubleAfter2Seconds(10);
  const b = await doubleAfter2Seconds(20);
  const c = await doubleAfter2Seconds(30);
  return x + a + b + c;
}


addAsync(10).then((sum) => {
  console.log(sum);
});
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are the timing features of Node.js?***

The Performance Timing API provides an implementation of the W3C Performance Timeline specification. The purpose of the API is to support collection of high resolution performance metrics. This is the same Performance API as implemented in modern Web browsers.

```javascript
const { PerformanceObserver, performance } = require('perf_hooks');

const obs = new PerformanceObserver((items) => {
  console.log(items.getEntries()[0].duration);
  performance.clearMarks();
});
obs.observe({ entryTypes: ['measure'] });

performance.mark('A');
doSomeLongRunningProcess(() => {
  performance.mark('B');
  performance.measure('A to B', 'A', 'B');
});
``` 

**`request` module**  
The popular request module has a built-in method to measure HTTP timings. You can enable it with the time property.

```javascript
const request = require('request')

request({
  uri: 'https://nodejs.org',
  method: 'GET',
  time: true
}, (err, resp) => {
  console.log(err || resp.timings)
})
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is LTS releases of Node.js why should you care?***

An LTS(Long Term Support) version of Node.js receives all the critical bug fixes, security updates and performance

LTS versions of Node.js are supported for at least 18 months and are indicated by even version numbers (e.g. 4, 6, 8). They’re best for production since the LTS release line is focussed on stability and security, whereas the Current release line has a shorter lifespan and more frequent updates to the code. Changes to LTS versions are limited to bug fixes for stability, security updates, possible npm updates, documentation updates and certain performance improvements that can be demonstrated to not break existing applications.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Why should you separate Express 'app' and 'server'?***

Keeping the API declaration separated from the network related configuration (port, protocol, etc) allows testing the API in-process, without performing network calls, with all the benefits that it brings to the table: fast testing execution and getting coverage metrics of the code. It also allows deploying the same API under flexible and different network conditions. Bonus: better separation of concerns and cleaner code.

API declaration, should reside in app.js:

```javascript
var app = express();
app.use(bodyParser.json());
app.use("/api/events", events.API);
app.use("/api/forms", forms);
```

Server network declaration, should reside in /bin/www:

```javascript
var app = require('../app');
var http = require('http');

/**
 * Get port from environment and store in Express.
 */

var port = normalizePort(process.env.PORT || '3000');
app.set('port', port);

/**
 * Create HTTP server.
 */

var server = http.createServer(app);
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the difference between process.nextTick() and setImmediate()?***

The difference between `process.nextTick()` and `setImmediate()` is that `process.nextTick()` defers the execution of an action till the next pass around the event loop or it simply calls the callback function once the ongoing execution of the event loop is finished whereas `setImmediate()` executes a callback on the next cycle of the event loop and it gives back to the event loop for executing any I/O operations.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is difference between JavaScript and Node.js?***

|    	|JavaScript	|Node JS    |
|-------|-----------|-----------|
|Type	|JavaScript is a programming language. It running in any web browser with a proper browser engine.|	It is an interpreter and environment for JavaScript with some specific useful libraries which JavaScript programming can use separately.|
|Utility	|Mainly using for any client-side activity for a web application, like possible attribute validation or refreshing the page in a specific interval or provide some dynamic changes in web pages without refreshing the page.|	It mainly used for accessing or performing any non-blocking operation of any operating system, like creating or executing a shell script or accessing any hardware specific information or running any backend job.|
|Running Engine| JavaScript running any engine like Spider monkey (FireFox), JavaScript Core (Safari), V8 (Google Chrome).|	Node JS only run in a V8 engine which mainly used by google chrome. And javascript program which will be written under this Node JS will be always run in V8 Engine.|

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are the difference between Events and Callbacks?***

Node.js is a single-threaded application, but it support concurrency via the concept of **event** and **callbacks**. Every API of Node.js is asynchronous and being single-threaded, they use async function calls to maintain concurrency. Node thread keeps an event loop and whenever a task gets completed, it fires the corresponding event which signals the event-listener function to execute.

callback functions are called when an asynchronous function returns its result, whereas event handling works on the **observer pattern**. The functions that listen to events act as Observers. Whenever an event gets fired, its listener function starts executing. Node.js has multiple in-built events available through events module and EventEmitter class which are used to bind events and event-listeners

**1. Callback**: A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

*Example*: synchronous callback

```js
function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

processUserInput(greeting);
```

**2. Events**: Every action on a computer is an event. Node.js allows us to create and handle custom events easily by using events module. Event module includes `EventEmitter` class which can be used to raise and handle custom events.

*Example*:

```js
var event = require('events');  
var eventEmitter = new event.EventEmitter();  
  
//  Add listener function for Sum event  
eventEmitter.on('Sum', function(num1, num2) {  
    console.log('Total: ' + (Number(num1) + Number(num2)));  
});  

//  Call Event.  
eventEmitter.emit('Sum', '10', '20');
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Explain RESTful Web Services in Node.js?***

REST stands for REpresentational State Transfer. REST is web standards based architecture and uses HTTP Protocol.
It is an architectural style as well as an approach for communications purposes that is often used in various web services development. A REST Server simply provides access to resources and REST client accesses and modifies the resources using HTTP protocol.

**HTTP methods**

* `GET` − Provides read-only access to a resource.
* `PUT` − Creates a new resource.
* `DELETE` − Removes a resource.
* `POST` − Updates an existing resource or creates a new resource.
* `PATCH`− Update/modify a resource

**Principles of REST**

* Uniform Interface
* Stateless
* Cacheable
* Client-Server
* Layered System
* Code on Demand (optional)

*Example*:

**users.json**

```json
{
   "user1" : {
      "id": 1,
      "name" : "Ehsan Philip",
      "age" : 24
   },

   "user2" : {
      "id": 2,
      "name" : "Karim Jimenez",
      "age" : 22
   },

   "user3" : {
      "id": 3,
      "name" : "Giacomo Weir",
      "age" : 18
   }
}
```

**List Users** ( `GET` method)

Let\'s implement our first RESTful API listUsers using the following code in a server.js file −

```js
var express = require('express');
var app = express();
var fs = require("fs");

app.get('/listUsers', function (req, res) {
   fs.readFile( __dirname + "/" + "users.json", 'utf8', function (err, data) {
      console.log( data );
      res.end( data );
   });
})

var server = app.listen(3000, function () {
   var host = server.address().address
   var port = server.address().port
   console.log("App listening at http://%s:%s", host, port)
});
```

**Add User** ( `POST` method )

Following API will show you how to add new user in the list. 

```js
var express = require('express');
var app = express();
var fs = require("fs");

var user = {
   "user4" : {
      "id": 4,
      "name" : "Spencer Amos",
      "age" : 28
   }
}

app.post('/addUser', function (req, res) {
   // First read existing users.
   fs.readFile( __dirname + "/" + "users.json", 'utf8', function (err, data) {
      data = JSON.parse( data );
      data["user4"] = user["user4"];
      console.log( data );
      res.end( JSON.stringify(data));
   });
})

var server = app.listen(3000, function () {
   var host = server.address().address
   var port = server.address().port
   console.log("App listening at http://%s:%s", host, port)
})
```

**Delete User**

```js
var express = require('express');
var app = express();
var fs = require("fs");

var id = 2;

app.delete('/deleteUser', function (req, res) {
   // First read existing users.
   fs.readFile( __dirname + "/" + "users.json", 'utf8', function (err, data) {
      data = JSON.parse( data );
      delete data["user" + 2];
      console.log( data );
      res.end( JSON.stringify(data));
   });
})

var server = app.listen(3000, function () {
   var host = server.address().address
   var port = server.address().port
   console.log("App listening at http://%s:%s", host, port)
})
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to handle file upload in Node.js?***

* **express**: Popular web framework built on top of Node.js, used for creating REST-API.
* **body-parser**: Parse incoming request bodies in a middleware
* **multer**: Middleware for handling multipart/form-data — file uploads

**1. Installing the dependencies**

```bash
npm install express body-parser multer --save
```

**2. Package.json**

```json
{
  "name": "file_upload",
  "version": "0.0.1",
  "dependencies": {
    "express": "4.13.3",
    "multer": "1.1.0"
  },
  "devDependencies": {
    "should": "~7.1.0",
    "mocha": "~2.3.3",
    "supertest": "~1.1.0"
  }
}
```

**3. Server.js**

```js
var express = require("express");
var bodyParser = require('body-parser');
var multer  = require('multer');
var app = express();

// for text/number data transfer between clientg and server
app.use(bodyParser());

var storage =   multer.diskStorage({
  destination: function (req, file, callback) {
    callback(null, './uploads');
  },
  filename: function (req, file, callback) {
    callback(null, file.fieldname + '-' + Date.now());
  }
});

var upload = multer({ storage : storage}).single('userPhoto');

app.get('/', function(req, res) {
      res.sendFile(__dirname + "/index.html");
});

// POST: upload for single file upload
app.post('/api/photo', function(req, res) {
    upload(req,res,function(err) {
        if(err) {
            return res.end("Error uploading file.");
        }
        res.end("File is uploaded");
    });
});

app.listen(3000, function(){
    console.log("Listening on port 3000");
});
```

**4. index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Multer-File-Upload</title>
</head>
<body>
    <h1>MULTER File Upload | Single File Upload</h1> 

    <form id = "uploadForm"
         enctype = "multipart/form-data"
         action = "/api/photo"
         method = "post"
    >
      <input type="file" name="userPhoto" />
      <input type="submit" value="Upload Image" name="submit">
    </form>
</body>
</html>
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Explain the terms body-parser, cookie-parser, morgan, nodemon, pm2, serve-favicon, cors, dotenv, fs-extra, moment in Express JS?***

**a) body-parser**

`body-parser` extract the entire body portion of an incoming request stream and exposes it on `req.body`. This body-parser module parses the JSON, buffer, string and URL encoded data submitted using HTTP POST request.

*Example*:

```bash
npm install express ejs body-parser
```

```js
// server.js

var express = require('express')
var bodyParser = require('body-parser')

var app = express()

// create application/json parser
var jsonParser = bodyParser.json()

// create application/x-www-form-urlencoded parser
var urlencodedParser = bodyParser.urlencoded({ extended: false })

// POST /login gets urlencoded bodies
app.post('/login', urlencodedParser, function (req, res) {
  res.send('welcome, ' + req.body.username)
})

// POST /api/users gets JSON bodies
app.post('/api/users', jsonParser, function (req, res) {
  // create user in req.body
})
```

**b) cookie-parser**

A cookie is a piece of data that is sent to the client-side with a request and is stored on the client-side itself by the Web Browser the user is currently using.

The `cookie-parser` middleware\'s cookieParser function takes a `secret` string or array of strings as the first argument and an `options` object as the second argument.

**Installation**

```bash
npm install cookie-parser
```

*Example*:

```js
var express = require('express')
var cookieParser = require('cookie-parser')

var app = express()
app.use(cookieParser())

app.get('/', function (req, res) {
  // Cookies that have not been signed
  console.log('Cookies: ', req.cookies)

  // Cookies that have been signed
  console.log('Signed Cookies: ', req.signedCookies)
})

app.listen(3000)
```

**c) morgan**

HTTP request logger middleware for node.js.

**Installation**

```bash
npm install morgan
```

*Example*: write logs to a file

```js
var express = require('express')
var fs = require('fs')
var morgan = require('morgan')
var path = require('path')

var app = express()

// create a write stream (in append mode)
var accessLogStream = fs.createWriteStream(path.join(__dirname, 'access.log'), { flags: 'a' })

// setup the logger
app.use(morgan('combined', { stream: accessLogStream }))

app.get('/', function (req, res) {
  res.send('hello, world!')
})
```

**d) nodemon**

Nodemon is a utility that will monitor for any changes in source and automatically restart your server.

**Installation**

```bash
npm install -g nodemon
```

*Example*:

```js
{
  // ...
  "scripts": {
    "start": "nodemon server.js"
  },
  // ...
}
```

**e) pm2**

**P**(rocess) **M**(anager) **2** (pm2) is a production process manager for Node.js applications with a built-in load balancer. It allows to keep applications alive forever, to reload them without downtime and to facilitate common system admin tasks.

**Installation**

```bash
npm install pm2 -g
```

**Start an application**

```bash
pm2 start app.js
```

**[[Read More](https://pm2.keymetrics.io/docs/usage/quick-start/)]**

**f) serve-favicon**

Node.js middleware for serving a favicon. The `serve-favicon` module lets us exclude requests for the favicon in our logger middleware. It also caches the icon in memory to improve performance by reducing disk access. In addition, it provides an `ETag` based on the contents of the icon, rather than file system properties.

**Installation**

```bash
npm install serve-favicon
```

*Example*:

```js
var express = require('express')
var favicon = require('serve-favicon')
var path = require('path')

var app = express()
app.use(favicon(path.join(__dirname, 'public', 'favicon.ico')))

// Add your routes here, etc.

app.listen(3000)
```

**g) cors**

**C**ross-**O**rigin **R**esource **S**haring (CORS) headers allow apps running in the browser to make requests to servers on different domains (also known as origins). CORS headers are set on the server side - the HTTP server is responsible for indicating that a given HTTP request can be cross-origin. CORS defines a way in which a browser and server can interact and determine whether or not it is safe to allow a cross-origin request.

**Installation**

```bash
npm install cors
```

**Example: Enable All CORS Requests**

```js
var express = require('express')
var cors = require('cors')
var app = express()

app.use(cors())

app.get('/products/:id', function (req, res, next) {
  res.json({msg: 'This is CORS-enabled for all origins!'})
})

app.listen(8080, function () {
  console.log('CORS-enabled web server listening on port 80')
})
```

**Example: Enable CORS for a Single Route**

```js
var express = require('express')
var cors = require('cors')
var app = express()

app.get('/products/:id', cors(), function (req, res, next) {
  res.json({msg: 'This is CORS-enabled for a Single Route'})
})

app.listen(8080, function () {
  console.log('CORS-enabled web server listening on port 80')
})
```

**h) dotenv**

When a NodeJs application runs, it injects a global variable called `process.env` which contains information about the state of environment in which the application is running. The `dotenv` loads environment variables stored in the `.env` file into `process.env`.

**Installation**

```bash
npm install dotenv
```

**Usage**

```js
// .env

DB_HOST=localhost
DB_USER=admin
DB_PASS=root
```

```js
// config.js

const db = require('db')

db.connect({
  host: process.env.DB_HOST,
  username: process.env.DB_USER,
  password: process.env.DB_PASS
})
```

**i) fs-extra**

`fs-extra` contains methods that aren\'t included in the vanilla Node.js fs package. Such as recursive `mkdir`, `copy`, and `remove`. It also uses graceful-fs to prevent `EMFILE` errors.

**Installation**

```bash
npm install fs-extra
```

**Usage**

```js
const fs = require('fs-extra')


// Async with callbacks:
fs.copy('/tmp/myfile', '/tmp/mynewfile', err => {
  if (err) return console.error(err)
  console.log('success!')
})
```

**j) moment**

A JavaScript date library for parsing, validating, manipulating, and formatting dates.

**Installation**

```bash
npm install moment --save
```

**Usage**

* Format Dates

```js
const moment = require('moment');

moment().format('MMMM Do YYYY, h:mm:ss a'); // October 24th 2020, 3:15:22 pm
moment().format('dddd');                    // Saturday
moment().format("MMM Do YY");               // Oct 24th 20
```

* Relative Time

```js
const moment = require('moment');

moment("20111031", "YYYYMMDD").fromNow(); // 9 years ago
moment("20120620", "YYYYMMDD").fromNow(); // 8 years ago
moment().startOf('day').fromNow();        // 15 hours ago
```

* Calendar Time

```js
const moment = require('moment');

moment().subtract(10, 'days').calendar(); // 10/14/2020
moment().subtract(6, 'days').calendar();  // Last Sunday at 3:18 PM
moment().subtract(3, 'days').calendar();  // Last Wednesday at 3:18 PM
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How does routing work in Node.js?***

Routing defines the way in which the client requests are handled by the application endpoints. We define routing using methods of the Express app object that correspond to HTTP methods; for example, `app.get()` to handle `GET` requests and `app.post` to handle `POST` requests, `app.all()` to handle all HTTP methods and `app.use()` to specify middleware as the callback function.

These routing methods "listens" for requests that match the specified route(s) and method(s), and when it detects a match, it calls the specified callback function.

*Syntax*:

```js
app.METHOD(PATH, HANDLER)
```

Where:

* app is an instance of express.
* METHOD is an `HTTP request method`.
* PATH is a path on the server.
* HANDLER is the function executed when the route is matched.

**a) Route methods**

```js
// GET method route
app.get('/', function (req, res) {
  res.send('GET request')
})

// POST method route
app.post('/login', function (req, res) {
  res.send('POST request')
})

// ALL method route
app.all('/secret', function (req, res, next) {
  console.log('Accessing the secret section ...')
  next() // pass control to the next handler
})
```

**b) Route paths**

Route paths, in combination with a request method, define the endpoints at which requests can be made. Route paths can be strings, string patterns, or regular expressions.

The characters `?`, `+`, `*`, and `()` are subsets of their regular expression counterparts. The hyphen `(-)` and the dot `(.)` are interpreted literally by string-based paths.

*Example*:

```js
// This route path will match requests to /about.
app.get('/about', function (req, res) {
  res.send('about')
})


// This route path will match acd and abcd.
app.get('/ab?cd', function (req, res) {
  res.send('ab?cd')
})


// This route path will match butterfly and dragonfly
app.get(/.*fly$/, function (req, res) {
  res.send('/.*fly$/')
})
```

**c) Route parameters**

Route parameters are named URL segments that are used to capture the values specified at their position in the URL. The captured values are populated in the `req.params` object, with the name of the route parameter specified in the path as their respective keys.

*Example*:

```js
app.get('/users/:userId', function (req, res) {
  res.send(req.params)
})
```

**Response methods**

| Method            | Description                   |
|-------------------|-------------------------------|
|`res.download()`   |Prompt a file to be downloaded.|
|`res.end()`        |End the response process.|
|`res.json()`       |Send a JSON response.|
|`res.jsonp()`      |Send a JSON response with JSONP support.|
|`res.redirect()`   |Redirect a request.|
|`res.render()`     |Render a view template.|
|`res.send()`       |Send a response of various types.|
|`res.sendFile()`   |Send a file as an octet stream.|
|`res.sendStatus()` |Set the response status code and send its string representation as the response body.|

**d) Router method**

```js
var express = require('express')
var router = express.Router()

// middleware that is specific to this router
router.use(function timeLog (req, res, next) {
  console.log('Time: ', Date.now())
  next()
})

// define the home page route
router.get('/', function (req, res) {
  res.send('Birds home page')
})

// define the about route
router.get('/about', function (req, res) {
  res.send('About birds')
})

module.exports = router
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How node.js prevents blocking code?***

**Blocking vs Non-blocking**

**Blocking** is when the execution of additional JavaScript in the Node.js process must wait until a non-JavaScript operation completes. This happens because the event loop is unable to continue running JavaScript while a **blocking** operation is occurring.

Synchronous methods in the Node.js standard library that use **libuv** are the most commonly used blocking operations. Native modules may also have blocking methods. Blocking methods execute `synchronously` and non-blocking methods execute `asynchronously`.

*Example:*

```js
// Blocking
const fs = require('fs');
const data = fs.readFileSync('/file.md'); // blocks here until file is read
console.log(data);
moreWork(); // will run after console.log

// Non-blocking
const fs = require('fs');
fs.readFile('/file.md', (err, data) => {
  if (err) throw err;
  console.log(data);
});
moreWork(); // will run before console.log
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is difference between promises and async-await in Node.js?***

**1. Promises**

A promise is used to handle the asynchronous result of an operation. JavaScript is designed to not wait for an asynchronous block of code to completely execute before other synchronous parts of the code can run. With Promises, we can defer the execution of a code block until an async request is completed. This way, other operations can keep running without interruption.

**States of Promises:**

* `Pending`: Initial State, before the Promise succeeds or fails.
* `Resolved`: Completed Promise
* `Rejected`: Failed Promise, throw an error

*Example:*

```js
function logFetch(url) {
  return fetch(url)
    .then(response => {
      console.log(response);
    })
    .catch(err => {
      console.error('fetch failed', err);
    });
}
```

**2. Async-Await**

`Await` is basically syntactic sugar for **Promises**. It makes asynchronous code look more like synchronous/procedural code, which is easier for humans to understand.

Putting the keyword `async` before a function tells the function to return a Promise. If the code returns something that is not a `Promise`, then JavaScript automatically wraps it into a resolved promise with that value. The `await` keyword simply makes JavaScript wait until that `Promise` settles and then returns its result.

*Example:*

```js
async function logFetch(url) {
  try {
    const response = await fetch(url);
    console.log(response);
  }
  catch (err) {
    console.log('fetch failed', err);
  }
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

#### 72Q. ***How to use JSON Web Token (JWT) for authentication in Node.js?***

JSON Web Token (JWT) is an open standard that defines a compact and self-contained way of securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed.

There are some advantages of using JWT for authorization:

* Purely stateless. No additional server or infra required to store session information.
* It can be easily shared among services.

JSON Web Tokens consist of three parts separated by dots (.), which are:

```js
jwt.sign(payload, secretOrPrivateKey, [options, callback])
```

* **Header** - Consists of two parts: the type of token (i.e., JWT) and the signing algorithm (i.e., HS512)
* **Payload** - Contains the claims that provide information about a user who has been authenticated along with other information such as token expiration time.
* **Signature** - Final part of a token that wraps in the encoded header and payload, along with the algorithm and a secret

**Installation**

```bash
npm install jsonwebtoken bcryptjs --save
```

**Example**: AuthController.js

```js
var express = require('express');
var router = express.Router();
var bodyParser = require('body-parser');
var User = require('../user/User');

var jwt = require('jsonwebtoken');
var bcrypt = require('bcryptjs');
var config = require('../config');


router.use(bodyParser.urlencoded({ extended: false }));
router.use(bodyParser.json());

router.post('/register', function(req, res) {
  
  var hashedPassword = bcrypt.hashSync(req.body.password, 8);
  
  User.create({
    name : req.body.name,
    email : req.body.email,
    password : hashedPassword
  },
  function (err, user) {
    if (err) return res.status(500).send("There was a problem registering the user.")
    // create a token
    var token = jwt.sign({ id: user._id }, config.secret, {
      expiresIn: 86400 // expires in 24 hours
    });
    res.status(200).send({ auth: true, token: token });
  });
});
```

**config.js**

```js
// config.js
module.exports = {
  'secret': 'supersecret'
};
```

The `jwt.sign()` method takes a payload and the secret key defined in `config.js` as parameters. It creates a unique string of characters representing the payload. In our case, the payload is an object containing only the id of the user.

* **[[Reference](https://www.npmjs.com/package/jsonwebtoken)]**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to build a microservices architecture with Node.js?***

**Microservices**

Microservices are a style of **service-oriented architecture** (SOA) where the app is structured on an assembly of interconnected services. With microservices, the application architecture is built with lightweight protocols. The services are finely seeded in the architecture. Microservices disintegrate the app into smaller services and enable improved modularity.

<p align="center">
  <img src="assets/monolithic-and-microservices-architecture.jpg" alt="Microservices" width="400px" />
</p>

There are few things worth emphasizing about the superiority of microservices, and distributed systems generally, over monolithic architecture:

* Modularity — responsibility for specific operations is assigned to separate pieces of the application
* Uniformity — microservices interfaces (API endpoints) consist of a base URI identifying a data object and standard HTTP methods (GET, POST, PUT, PATCH and DELETE) used to manipulate the object
* Robustness — component failures cause only the absence or reduction of a specific unit of functionality
* Maintainability — system components can be modified and deployed independently
* Scalability — instances of a service can be added or removed to respond to changes in demand.
* Availability — new features can be added to the system while maintaining 100% availability.
* Testability — new solutions can be tested directly in the production environment by implementing them for  restricted segments of users to see how they behave in real life.

**Creating Microservices with Node.js**

**Step 01: Creating a Server to Accept Requests**

This file is creating our server and assigns routes to process all requests.

```js
//  server.js

const express = require('express')
const app = express();
const port = process.env.PORT || 3000;

const routes = require('./api/routes');
routes(app);
app.listen(port, function() {
   console.log('Server started on port: ' + port);
});
```

**Step 02: Defining the routes**

The next step is to define the routes for the microservices and then assign each to a target in the controller. We have two endpoints. One endpoint called "about" that returns information about the application. And a "distance" endpoint that includes two path parameters, both Zip Codes of the Lego store. This endpoint returns the distance, in miles, between these two Zip Codes.

```js
const controller = require('./controller');

module.exports = function(app) {
   app.route('/about')
       .get(controller.about);
   app.route('/distance/:zipcode1/:zipcode2')
       .get(controller.getDistance);
};
```

**Step 03: Adding Controller Logic**

Within the controller file, we are going to create a controller object with two properties. Those properties are the functions to handle the requests we defined in the routes module.

```js
var properties = require('../package.json')
var distance = require('../service/distance');

var controllers = {
   about: function(req, res) {
       var aboutInfo = {
           name: properties.name,
           version: properties.version
       }
       res.json(aboutInfo);
   },
   getDistance: function(req, res) {
           distance.find(req, res, function(err, dist) {
               if (err)
                   res.send(err);
               res.json(dist);
           });
       },
};

module.exports = controllers;
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to use Q promise in Node.js?***

A promise is an object that represents the return value or the thrown exception that the function may eventually provide. A promise can also be used as a proxy for a remote object to overcome latency.

Promise is relatively an easy implementation for asynchronous operation. The promise object returned from the function represents an operation which is not completed yet, but it guarantees to the caller of the operation that the operation will be completed in future.

Promise has the following states:

* **Pending** - asynchronous operation is not yet completed.
* **Fulfilled** - asynchronous operation is completed successfully.
* **Rejected** - asynchronous operation is terminated with an error.
* **Settled** - asynchronous operation is either fulfilled or rejected.
* **Callback** - function is executed if the promise is executed with value.
* **Errback** - function is executed if the promise is rejected.

**Moving to Promises from Callback**

On the first pass, promises can mitigate the **Pyramid of Doom**: the situation where code marches to the right faster than it marches forward.

```js
step1(function (value1) {
    step2(value1, function(value2) {
        step3(value2, function(value3) {
            step4(value3, function(value4) {
                // Do something with value4
            });
        });
    });
});
```

With a promise library, it can flatten the pyramid.

```js
Q.fcall(promisedStep1)
.then(promisedStep2)
.then(promisedStep3)
.then(promisedStep4)
.then(function (value4) {
    // Do something with value4
})
.catch(function (error) {
    // Handle any error from all above steps
})
.done();
```

* **[[Reference](https://www.npmjs.com/package/q)]**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to implement Memcached in Node.js?***

**Memcached** is a general-purpose distributed memory caching system. It is often used to speed up dynamic database-driven websites by caching data and objects in RAM to reduce the number of times an external data source (such as a database or API) must be read. Memcached is free and open-source software, licensed under the Revised BSD licence. Memcached runs on Unix-like operating systems (at least LINUX and OS X) and on Microsoft windows.

We can store data to memcached server in key pair format. So whenever any request come from the app can be matched with memcached server without any query from mysql/Nosql server. This increases the performance of the application.

**Installation**

```bash
npm install memcached
```

**Setting up the client**

The constructor of the memcached client take 2 different arguments server locations and options. Syntax:

```bash
var Memcached = require('memcached');
var memcached = new Memcached(Server locations, options);
```

**Example usage**:

```js
var Memcached = require('memcached');
// all global configurations should be applied to the .config object of the Client.
Memcached.config.poolSize = 25;

var memcached = new Memcached('localhost:11211', {retries:10,retry:10000,remove:true,failOverServers:['192.168.0.103:11211']});
```

<br/>

**[[Reference](https://www.npmjs.com/package/memcached)]**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to generate and verify checksum of the given string in Nodejs***

The **checksum** (aka **hash sum**) calculation is a one-way process of mapping an extensive data set of variable length (e.g., message, file), to a smaller data set of a fixed length (hash). The length depends on a hashing algorithm.

For the checksum generation, we can use node `crypto()` module. The module uses `createHash(algorithm)` to create a checksum (hash) generator. The algorithm is dependent on the available algorithms supported by the version of OpenSSL on the platform.

**Example:**

```js
const crypto = require('crypto');

// To get a list of all available hash algorithms
crypto.getHashes() // [ 'md5', 'sha1', 'sha3-256', ... ]

  
// Create hash of SHA1 type
const key = "MY_SECRET_KEY";


// 'digest' is the output of hash function containing  
// only hexadecimal digits
hashPwd = crypto.createHash('sha1').update(key).digest('hex');
  
console.log(hashPwd); //ef5225a03e4f9cc953ab3c4dd41f5c4db7dc2e5b
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

#### Q. ***Explain Error Handling in Nodejs?***
#### Q. ***How to use locale (i18n) in Node.js?***
#### Q. ***What are the types of memory leaks in node.js***
#### Q. ***How to implement a Sleep function?***
#### Q. ***How does the cluster load balance work in node.js?***
#### Q. ***What is daemon process? how to implement it in node.js?*** 
#### Q. ***How to synchronize data between multiple clients on node.js server?***

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

