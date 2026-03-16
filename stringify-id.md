
------------------------------------------------------

# STRINGIFY ID

------------------------------------------------------

// ===== Example Problem =====
```
Write a function that creates a stringified representation of an object.
```
// ===== Clarifying Questions =====

- Which properties would you like included in the stringified ID?
- Is there a particular order you would like the keys sorted?
- Are there any properties you would like to keep hidden from the stringified ID?

// ===== TestCase =====

- See each

------------------------------------------------------
## Method 1
// ===== BUILT IN METHODS =====
```
function stringifyId(object) {
  return JSON.stringify(object);
}
const user = { id: 123, name: "Fred Weasley", role: "BFF" };
console.log(stringifyId(user));
```
------------------------------------------------------
## Method 2
// ===== CUSTOM STRINGIFY ID =====
```
function stringifyId(object, keys) {
  return keys.map(key => `${key}:${object[key]}`).join('|');
}
const user = { id: 123, name: "Fred Weasley", role: "BFF" };
console.log(stringifyId(user, ['id', 'name'])); 
```
------------------------------------------------------
## Method 3
// ===== CUSTOM STRINGIFY ID WITH NESTED OBJECTS =====
```
function stringifyId(object, keys) {
  return keys.map(key => {
  const value = key.split('.').reduce((account, part) => account && account[part], object);
  return `${key}:${value}`;
  }).join('|');
}
const user = { 
  id: 123, 
  name: "Baymax", 
  role: {
    type: "BigHero", 
    level: 6,
  } 
};

console.log(stringifyId(user, ['name', 'role.type', 'role.level']));
```
------------------------------------------------------
## Method 4
// ===== JSON.STRINGIFY - SORTED FOR CONSISTENCY =====
```
function stringifyId(object, keys) {
  const sortedKeys = Object.keys(object).sort();
  const sortedObj = {};
  sortedKeys.forEach(key => sortedObj[key] = object[key]);
  return JSON.stringify(sortedObj);
}
  
const user = { 
  id: 123, 
  name: "Baymax", 
  role: {
    type: "BigHero", 
    level: 6,
  } 
};

console.log(stringifyId(user, ['name', 'role.type', 'role.level']));
```
```
         @\_______/@
        @|XXXXXXXX |
       @ |X||    X |
      @  |X||    X |
     @   |XXXXXXXX |
    @    |X||    X |             V
   @     |X||   .X |
  @      |X||.  .X |                      V
 @      |%XXXXXXXX%||
@       |X||  . . X||
        |X||   .. X||                               @     @
        |X||  .   X||.                              ||====%
        |X|| .    X|| .                             ||    %
        |X||.     X||   .                           ||====%
       |XXXXXXXXXXXX||     .                        ||    %
       |XXXXXXXXXXXX||         .                 .  ||====% .
       |XX|        X||                .        .    ||    %  .
       |XX|        X||                   .          ||====%   .
       |XX|        X||              .          .    ||    %     .
       |XX|======= X||============================+ || .. %  ........
===== /            X||                              ||    %
                   X||           /)                 ||    %
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
cr: alyosha_u_washington_edu| Nina Butorac
```