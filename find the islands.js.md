# find the islands

```javascript
//find the island
// Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.
//https://leetcode.com/problems/number-of-islands/
grid1 = [[1, 1, 1, 1, 0], [1, 1, 0, 1, 0], [1, 1, 0, 0, 0], [0, 0, 0, 0, 0]]
grid2 = [[1, 1, 0, 0, 0], [1, 1, 0, 0, 0], [0, 0, 1, 0, 0], [0, 0, 0, 1, 1]]
grid3 = [[1, 0, 1, 0, 1], [0, 1, 0, 1, 0], [1, 0, 1, 0, 1], [0, 1, 0, 1, 0]]
grid4 = [[1, 1, 1, 1, 1], [0, 0, 0, 1, 0], [0, 1, 0, 1, 1], [0, 1, 1, 1, 0]]

const searchLand = (index, index2, grid, knownLand) => {
  if (knownLand.indexOf(`${index},${index2}`) === -1) {
    knownLand.push(`${index},${index2}`)
    if (!(grid[index] && grid[index][index2])) {
      return
    }

    searchLand(index, index2 + 1, grid, knownLand)
    searchLand(index + 1, index2, grid, knownLand)
    searchLand(index - 1, index2, grid, knownLand)
    searchLand(index, index2 - 1, grid, knownLand)

    return true
  }
}

const countIsland = (grid) => {
  let knownLand = []
  return grid.reduce((island, array, index) => {
    array.forEach((element, index2) => {
      element === 1 && searchLand(index, index2, grid, knownLand) && island++
    })
    return island
  }, 0)
}

console.log(countIsland(grid1))
console.log(countIsland(grid2))
console.log(countIsland(grid3))
console.log(countIsland(grid4))

// the logic behind it is
// 1. create an empty "knownLand" array
// 2. use 2 for loop to loop into the element, 
// 2.a(case1) if this element is in the known land list or it is sea, ignore this element
// 2.b(case2) if not in the knownLand list, then increase island number by 1
// 2.b.i push the x,y index of this land into known land as string (do not push it as array or else you will having hard time compare it)
// 2.b.ii if the right element is 1, recur into step 2.b.i
// 2.b.iii if the bottom element is 1, recur into step 2.b.i
// 2.b.iii if the left element is and is not in the knownLand list, recur into step 2.b.i(edited)
// the code is very short, but it become long to deal with error because if you try to get element of 2D arraywith higher index, it will error, however this is not the case if the array is 1D, weird, such inconsistency!(edited)
// since it is a recursion, you can try it with any size of 2D array, not limited to 4x5
```
not really the question I designed but some one shows me and this is how I solve it
not optimized though
