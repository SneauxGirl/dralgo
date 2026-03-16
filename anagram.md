```
  __ _ _ __   __ _  __ _ _ __ __ _ _ __ ___  
 / _` | '_ \ / _` |/ _` | '__/ _` | '_ ` _ \ 
| (_| | | | | (_| | (_| | | | (_| | | | | | |
 \__,_|_| |_|\__,_|\__, |_|  \__,_|_| |_| |_|
                    __/ |                    
                   |___/                     
```
------------------------------------------------------

# ANAGRAM

------------------------------------------------------

A word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

// ===== Example Problem =====
```
Given two strings, write a function to determine if one string is an anagram of the other.
Parameters: Assume the input strings only contain alphanumeric characters and are case insensitive.
```
// ===== Clarifying Questions =====

 - Should the function ignore spaces and punctuation?
 - Is it case sentitive?

// ===== TestCase =====
```
console.log(isAnagram('silent', 'listen'))
```

------------------------------------------------------
## Method 1
// ===== FREQUENCY COUNTER =====

- Fastest at scale

```
function isAnagram(string1, string2) {
  if (string1.lenth !== string2.lenth) return false;
  
  const charCount = {};
  
  for (let char of string1.toLowerCase()) {
    charCount[char] = (charCount[char] || 0) + 1;
  }
  
  for (let char of string2.toLowerCase()) {
    if (!charCount[char]) return false;
    charCount[char]--;
  }
    return true;
} 
```
------------------------------------------------------
## Method 2
// ===== SORTING =====

- Normalize will sort and count all characters (inc digits and spaces), convert to lowercase, and compare
```
function isAnagram(string1, string2) {
  const normalize = string => string.toLowerCase().split('').sort().join('');
  return normalize(string1) === normalize(string2);
}
```
------------------------------------------------------
## Method 3
// ===== CLEAN AND SORT =====

- Strips out anything that is not a letter (upper/lower), converts to lower case, and compares
```
function isAnagram(string1, string2) {
  const cleanString = string => string.replace(/[^\w]/g, '').toLowerCase();
  return cleanString(string1).split('').sort().join('') ===
    cleanString(string2).split('').sort().join('');
}
```