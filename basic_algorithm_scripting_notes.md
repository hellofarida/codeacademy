# Codeacademy: Basic Algorithm Scripting

### Factorialize a Number

**Factorial**: The product of an integer and all the integers below it.

*ie. Factorial 4 ( 4! ) is 4 * 3 * 2 * 1 = 24.*
*ie. 0! is 1. But why?*

---

#### Why 0! = 1
A factorial is the number of combinations possible with the numbers less or equal to that number. It helps to know that a factorial helps determine orders of permutation, but what the hell is that?

---

**Permutation**: A specific, unique order of elements in a set.

*ie. There are six permuations of a set [1, 2, 3], which contains 3 elements and we can write them in  different ways:*

> * 1, 2, 3
> * 1, 3, 2
> * 2, 3, 1
> * 2, 1, 3
> * 3, 2, 1
> * 3, 1, 2

Another way you can express this is 3! = 6.

This brings us back to why 0! = 1. There is only one combination possible with numbers less or equal to this. 1! also equals 1.

**Write a function to process factorials:**

    function factorialize(num) {
      if (num === 0) { return 1 }
      return num * factorialize(num-1)
    }

**Why does this work?**
A friendly term called **Recursion**: A technique where a function is called within itself until it arrives at a result.

---

## Return length of longest word in a sentence

**My solution**:

    function findLongestWordLength(str) {
      const str_array = str.split(' ').sort(
        function(a, b) {
        return b.length - a.length
      });
      return str_array[0].length
    }

**Their solution:**

    function findLongestWordLength(str) {
    var words = str.split(' ');
    var maxLength = 0;

    for (var i = 0; i < words.length; i++) {
      if (words[i].length > maxLength) {
        maxLength = words[i].length;
      }
    }

      return maxLength;
    }

---

## Return Largest Numbers in Arrays

**My solution:**

    function largestOfFour(arr) {
    let largestNumbers = []

    let i = 0;
      for (i = 0; i < arr.length; i++) {
      largestNumbers.push(Math.max(...arr[i]));
    }

    return largestNumbers;
    }

**Their Solution:**

    function largestOfFour(arr) {
      return arr.map(Function.apply.bind(Math.max, null));
    }


---

## Confirm the Ending

### Slice vs splice vs split

**.slice(from, until)**
* Copies part of an array and returns a new array
* Does not create a new array
* You choose which part of the array to slice *starting from index 0*
* Can be used for arrays and strings

        const phrase = "May the sauce be with you"

        // "sauce be with you"
        console.log(phrase.slice(8))

* You choose which position to slice until

        // "sauce"
        console.log(phrase.slice(8,13))

**.splice(index, deleteCount, extra elements)**
* Changes an array, by adding or removing elements from it
* The first parameter will select which index to start with
* The second parameter will select how many elements after the index to delete

        let array = ["May", "the", "sauce", "be", "with", "you"]

        // "sauce be with you"
        console.log(array.splice(2))

        // "sauce"
        console.log(array.splice(2,1))

**.split(separator, limit)**
* Only for strings
* Splits a string into an array of sub strings
* If you have an array you can use the .toString() method to turn your array into a string first
* You can limit where the string stops with the second parameter

        const string = "May the sauce be with you"

        console.log(string.split(""))
        // M,a,y, ,t,h,e, ,s,a,u,c,e, ,b,e, ,w,i,t,h, ,y,o,u

**My Solution**

    function confirmEnding(str, target) {
      return str.slice(str.length - target.length) === target;
    }

*I cheated a bit becuase I forgot the difference between the above methods*

---

## Repeat a String Repeat a String

**My Solution**

    function repeatStringNumTimes(str, num) {
      let newString = "";

      while (num > 0) {
        newString += str
        num--
      }

      return newString
    }

---

## Truncate a String

**My solution**

    function truncateString(str, num) {
      let newString = str.slice(0, num)
      if(num !== 3) {
        return str.length <= num ? str : newString + '...'
        } else {
          return str
        }
    }

**Their solution**

    function truncateString(str, num) {
      if (str.length <= num) {
        return str;
      } else {
        return str.slice(0, num > 3 ? num - 3 : num) + '...';
      }
    }

---

## Finders Keepers

* Return the first number in a given array that is true in the equation given in the second param

**My solution**

        function findElement(arr, func) {
          let num = 0;

          for(let i = 0;i < arr.length;i++) {
            let num = arr[i]
             if(func(num)) {
               return num
             }
          }

          return undefined
        }

---

## Boo Hoo

* Check to see if something is a Boolean Primitive or not
* This one was tricky as 'false' is a boolean but returns as false, so you must check the typeof the param

**My solution (same as their solution)**

    function booWho(bool) {
      return typeof bool === 'boolean'
    }

---

## Title Case a Sentence

* Take a string & downcase
* Extract the first letter of each word and uppercase it

**My solution**

    function titleCase(str) {
      let titleCaseArr = str.toLowerCase().split(" ")

      return titleCaseArr.map(
        function(phrase) {
          return phrase.replace(phrase[0], phrase[0].toUpperCase())
        }).join(' ')
    }


**Their solution**

      function titleCase(str) {
        return str.toLowerCase().replace(/(^|\s)\S/g, (L) => L.toUpperCase());
      }

## Slice and Splice

**My Solution (based of their solution -- understanding of splice needed to be amedned)**

    function frankenSplice(arr1, arr2, n) {
      let baseArray = arr2.slice()

      for(let i=0;i<arr1.length;i++) {
        baseArray.splice(n, 0, arr1[i])
        n++
      }

      return baseArray

    }

---

## Falsy Bouncer

* Filter out all falsy values in an array.
* Falsy values in JavaScript are *false*, *null*, *0*, *""*, *undefined*, and *NaN*.

**My Soltion**

    function bouncer(arr) {

      function isTruthy(value) {
        return Boolean(value)
      }

      let onlyTruthys = arr.filter(isTruthy);
      return onlyTruthys;
    }

**Their solution**

    function bouncer(arr) {
      return arr.filter(Boolean);
    }

* In using a true return in my own function I forgot the Boolean function was it's own method of returning true so you could do it in one line -- brain fart

---

## Where do I Belong

**My Solution**

    function getIndexToIns(arr, num) {
      arr.push(num);
      return arr.sort(function(a, b){return a-b}).indexOf(num)
    }

**Their solution**

    function getIndexToIns(arr, num) {
      return arr.concat(num).sort((a,b) => a-b).indexOf(num);
    }


### .concat()
* Concat merges two or arrays and returns it as a whole new array
* Allows the solution to be solved in one nifty line, as you need to return the amended array when using .push() (even though it doesn't read too well for human eyes)

---
