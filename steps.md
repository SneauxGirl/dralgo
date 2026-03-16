
------------------------------------------------------

# STEPS

------------------------------------------------------

// ===== Example Problem =====
```
You are given a positive integer 'n', representing the number of levels in a staircase.
Each level should consist of '#' symbols, starting with 1 at the top level and increasing by 1 on each subsequent level.
The remaining characters on each level are spaces.

Parameters: positive integers, include trailing spaces.
```
// ===== Clarifying Questions =====

- Should each level include trailing spaces?
- What happens if 'n' is zero or negative?
```
'#    '
'##   '
'###  '
'#### '
'#####'
steps(5);
```

------------------------------------------------------
## Method 1
// ===== NESTED LOOPS =====
```
function steps(n) {
  for (let row = 1; row <= n; row++) {
    let step = '';
    for (let column = 1; column <= n; column++) {
      if (column <= row) {
          step += '#';
      } else {
           step += ' ';
      }
    }
    console.log(step);
  }
}

steps(5);
```
------------------------------------------------------
## Method 2
// ===== STRINGS AND PADDING =====
```
function steps(n) {
  for (let i = 1; i <= n; i++) {
    let step = '#'.repeat(i).padEnd(n, ' ');
    console.log(step);
  }
}

steps(5);
```
```
                .'`-._
              .'      `-.'`-._
            ._        .'      `-.'`-._
            |_`-._  .'        .'      `-.'`-._
          .'  `-._`|`-._    .'        .'      `-.'`-._
        .'        .|    `-.|`-._    .'        .'      `-.'`-._
      .'        .' |            `-.|`-._    .'        .'      `-.
      |_`-._   /   |                    `-.|`-._   ..'          /
    .'  `-._`-'    |                            `.' `-._      .'|
  .'        `-|    |                            /       `-.  /  |
.'          .'|    |                        .'`-._        /|'   |
|`-._      / .'`-._|                       /      `-._  .'      |
|    `-._.' /       `-._.                .'          .|/        |
|        |.'         .' |_            .'`-._        /           |
|         `-._      / .'  `-.__      /      `-._  .'            |
|             `-._.' /         .'| .'          .|/              |
|                 |.'         / .'`-._        /                 |
|                  `-._     .' /      `-._  .'                  |
|                      `-._/ .'          .|/                    |
|                          |/           /                       |
|                           `-._      .'                        |
|                               `-._ /                          |
|                                   |                           |
|                                   |                           |
|                                   |                           |
|                                   |                         .'
|                                   |                        /
|                                   |                      .'
|                                   |                    .'
`-.                                 |                   /
   `-.                              |                 .'
      `-.                           |               .'
         `-.                        |              /
            `-.                     |            .'
               `-.                  |          .'
                  `-.               |         /
                     `-.            |       .'
                        `-.         |     .'
 VK                        `-.      |    /
                              `-.   |  .'
                                 `-.|.'
```