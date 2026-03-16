```
 ________________________________________________________
/  ____________________________________________________  \
| |<_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> | |
| |<_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> | |
| |_|___|___|___|___|___|___|___|___|___|___|___|___|__| |
|  ____________________________________________________  |
| | |   |   |   |   |   |   |   |   |   |   |   |   |  | |
| |<_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> | |
| |<_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> | |
| |<_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> | |
| |<_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> <_> | |
| |<_>_<_>_<_>_<_>_<_>_<_>_<_>_<_>_<_>_<_>_<_>_<_>_<_>_| |
\___________________________________________________LGB__/
```
------------------------------------------------------

# MAX CHARACTER

------------------------------------------------------

// ===== Example Problem =====
```
Write a function that returns the most frequent character in a string.
```
// ===== TestCase =====
```
console.log(maxCharacter("If I was a rich man v2.000000001"));
```

- REGEX: 
```
string = string.toLowerCase().replace(/[^a-z0-9]/g, '');
```

------------------------------------------------------
## Method 1
// ===== TWO FOR LOOPS =====
```
function maxCharacter(string) {
  const charMap = {};
  let maxChar = '';
  let maxCount = 0;

  for (let char of string) {
    charMap[char] = (charMap[char] || 0) + 1;

  for (let char in charMap) {
    if (charMap[char] > maxCount) {
      maxCount = charMap[char];
      maxChar = char;
    }
  }
   return maxChar;
}
```
------------------------------------------------------
## Method 2
// ===== COMBINED FOR LOOPS =====

- More efficient
```
function maxCharacter(string) {
  const charMap = {};
  let maxChar = '';
  let maxCount = 0;

  for (let char of string) {
    charMap[char] = (charMap[char] || 0) + 1;
    if (charMap[char] > maxCount) {
      maxCount = charMap[char];
      maxChar = char;
    }
  }
   return maxChar;
}
```