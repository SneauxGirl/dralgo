 ```
                         __                                 
                   _.--""  |                                
    .----.     _.-'   |/\| |.--.                            
    |jrei|__.-'   _________|  |_)  _______________          
    |  .-""-.""""" ___,    `----'"))   __   .-""-.""""--._  
    '-' ,--. `    |tic|   .---.       |:.| ' ,--. `      _`.
     ( (    ) ) __|tac|__ \\|// _..--  \/ ( (    ) )--._".-.
      . `--' ;\__________________..--------. `--' ;--------'
       `-..-'                               `-..-'          
```
------------------------------------------------------

# PALINDROME

------------------------------------------------------

A palindrome is a word, phrase or sequence that reads the same backward as forward.

// ===== Example Problem =====
```
Write a function that checks if a string is a palindrome.
```
// ===== Clarifying Questions =====

- Should spaces be considered part of the palindrome?
- Should digits be considered part of the palindrome?
- Should case be considered part of the palindrome?

// ===== TestCase =====
```
console.log(isPalindrome("1. Once upon a no puecno"));
console.log(isPalindrome("racecar"));
```

------------------------------------------------------
## Method 1
// ===== REVERSE STRING =====
```
function isPalindrome(string) {
let reversed = string.split('').reverse().join('');
return string === reversed;
}
```
------------------------------------------------------
## Method 2
// ===== FOR LOOP =====
```
function isPalindrome(string) {
  let length = string.length;
  for (let i = 0; i < length / 2; i ++) {
    if (string[i] !== string[length - 1 - i]) {
      return false;
    }
  }
       return true;
}
```
------------------------------------------------------
## Method 3
// ===== RECURSION =====

- Good for repeating patterns in general
```
function isPalindrome(string) {
  if (string.length <= 1) {
    return true;
  }
  if (string[0] !== string[string.length - 1]) {
    return false;
  }
  return isPalindrome(string.slice(1, -1))
}
```