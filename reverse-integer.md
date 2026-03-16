```
       1          2 2               3 3 3 3              2 2                   1
      11        2     2          3          3          2     2                11
    1  1      2         2        3     3    3        2         2            1  1
    1  1      2     2   2          3 3      3        2     2   2            1  1
  1    1        2 2     2                  3           2 2     2          1    1
1      1              2                3 3                   2          1      1
       1            2                      3               2                   1
       1          2                          3           2                     1
       1        2                3           3         2                       1
       1      2 2 2       2        3       3         2 2 2       2             1 
       1      2     2 2 2            3 3 3          2     2 2 2                1
```

------------------------------------------------------

# REVERSE INTEGER

------------------------------------------------------

// ===== Example Problem =====
```
Write a function that reverses an integer.
```
// ===== Clarifying Questions =====

- How would you like negatives handled? Reverse the integer or reverse only the digits?
- Should decimals be included or should the integer be rounded before reverse?
- How would you like overflow handled for over 32b?

// ===== Notes =====

- 32b signed integers range: -2,147,483,648 to 2,147,483,647
- 0x7FFFFFFF (seven 'f's)

// ===== TestCase =====
```
console.log(reverseInteger(1023456789));
console.log(reverseInteger(1234567.89));
console.log(reverseInteger(-123456789));
console.log(reverseInteger(1000));
```

------------------------------------------------------
## Method 1
// ===== STRING MANIPULATION =====
```
function reverseInteger(number) {
  const isNegative = number < 0;
  let reversed = parseInt(Math.abs(number).toString().split('').reverse().join(''));
  if (reversed)
  return isNegative ? -reversed : reversed;
}
```
------------------------------------------------------
## Method 2
// ===== STRING MANIPULATION =====
```
function reverseInteger(number) {
  let reversed = 0;
  const isNegative = number < 0;
  number = Math.abs(number);
  
  while (number > 0) {
    reversed = reversed * 10 + number % 10;
    number = Math.floor(number / 10);
  }
  if (reversed > 0x7FFFFFFF) {
    return 0;
  }
  return isNegative ? -reversed : reversed;
}
```