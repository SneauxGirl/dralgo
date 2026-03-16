```
,PYRAMIDPYRAMIDPYRAMIDPYRAM#IDPYRAMIDPYRAMIDPYRAMID,
#PYRAMID#PYRAMID#PYRAMID##PYRAMID##PYRAMID#PYRAMID#I
PYRAMID#PYRAMID#"  "#####"  "PYRAMID#8PYRAMID#PYRAM8
8::::::::::::::'    `###'    `:::::::::::::::::::::8
Ib:::::::::::"        #        `::::::' `:::::::::dI
`8888888888P            Y88888888888P     Y88888888'
 Ib:::::::'              `:::::::::'       `:::::dI
  Yb::::"                  ":::::"           "::dP
   Y88P                      Y8P               `P
    Y'                        "
                                `:::::::::::;8"
       "888888888888888888888888888888888888"
```
------------------------------------------------------

# PYRAMID

------------------------------------------------------

// ===== Example Problem =====
```
You are given a positive integer 'n', representing the number of levels in the pyramid.
Each level should have '#' symbols, with the number of '#' increasing as you go down the levels.
The symbols are centered with spaces on BOTH sides.

Parameters: positive integers, centered # with spaces on each side.
```
// ===== Clarifying Questions =====

- Should the pyramid be symetrical with the # centered and spaces on both sides?
- This a standard pyramid or inverted?
- What happens if 'n' is zero or negative?

```
Example: steps(5)

'    #    '
'   ###   '
'  #####  '
' ####### '
'#########'
```

------------------------------------------------------
## Method 1
// ===== NESTED LOOPS =====
```
function pyramid(n) {
  const midpoint = Math.floor((2 * n - 1) / 2);
  
  for (let row = 0 ; row <n; row++) {
    let level = '';
    
    for (let column = 0; column < 2 * n -1; column++) {
      if (midpoint - row <= column && midpoint + row >= column) {
        level += '#';
      } else {
        level += ' ';
      }
    }
    console.log(level)
  }
}

pyramid(5);
```
------------------------------------------------------
## Method 2
// ===== STRING METHODS AND PADDING =====
```
function pyramid(n) {
  for (let row = 1; row <= n; row++) {
    const numHashes = 2 * row - 1;
    const numSpaces = n - row;
    
    const level = ' '.repeat(numSpaces) + '#'.repeat(numHashes) + ' '.repeat(numSpaces);
    console.log(level);
  }
}
pyramid(5);
```