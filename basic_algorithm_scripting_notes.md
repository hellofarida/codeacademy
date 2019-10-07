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

**.splice(index, number of elements, extra elements)**
* Changes an array, by adding or removing elements from it
* The first parameter will select which index to start with
* The second parameter will select how many elements after the index to include

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













