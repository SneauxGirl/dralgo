```
array.slicearray.slicearray.slicearray.slicearray.slice
  rray.slicearray.slicearray.slicearray.slicearray.sli
    ray.slicearray.slicearray.slicearray.slicearray
      ay.slicearray.slicearray.slicearray.slicear
        y.slicearray.slicearray.slicearray.sli
          .slicearray.slicearray.slicearray
```
------------------------------------------------------

# ARRAY CHUNK

------------------------------------------------------

// ===== Example Problem =====
```
Given an array and a chunk size, split the array into sub-arrays where each sub-array has the length of the chunk size.
```
// ===== Clarifying Questions =====

- What should happen if the array can't be divided equally? Should the remaining elements be included in the final array?
- Can the chunk size be larger than the array length?

// ===== TestCase =====
```
console.log(chunk([1, 2, 3, 4, 5, 6], 3))
console.log(chunk([1, 2, 3, 4, 5], 2))
```

------------------------------------------------------
## Method 1
// ===== LOOPING WITH SLICING =====
```
function chunk(array, size) {
  const chunkedArray = [];
  let index = 0;
  
  while (index < array.length) {
    chunkedArray.push(array.slice(index, index + size));
    index += size;
  }
  
  return chunkedArray;
}
```
------------------------------------------------------
## Method 2
// ===== LOOPING WITH PUSH AND SUBARRAY CONSTRUCTION =====
```
  function chunk(array, size) {
  const chunkedArray = [];
  let chunk = [];
  
  for (let i = 0; i < array.length; i++) {
    chunk.push(array[i]);
    
    if (chunk.length === size) {
      chunkedArray.push(chunk);
      chunk = [];
    }
  }
     if (chunk.length) {
       chunkedArray.push(chunk);
     }
  
  return chunkedArray
}
```
------------------------------------------------------
## Method 3
// ===== ARRAY.PROTOTYPE.SPLICE =====

- WARNING: This method does not retain the original array length
```
function chunk(array, size) {
  const chunkedArray = [];
  
  while (array.length > 0) {
    chunkedArray.push(array.splice(0, size));
  }
  
  return chunkedArray
}
```