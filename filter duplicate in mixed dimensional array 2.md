# filter duplicate in mixed dimensional array 2
```
function arrayUnique(items) {
    var hash = {}
    var out = []

    items.forEach(e => {
        if (!hash[e]) {
            hash[e] = true;
            out.push(e);
        }
    });

    return out;
}

// example question
s = [
    [1, 1],
    [1, 1],
    2,
    [3, 3],
    [5, 6, [7, 8, [9, 10], 11]],
    [3, 3],
    4,
    4,
    [5, 6, [7, 8, [9, 10], 11]],
]

// example answer
a = [[1, 1], 2, [3, 3], [5, 6, [7, 8, [9, 10], 11]], 4]

// answer returned by function
a2 = arrayUnique(s)

console.log(a2) // [[1, 1], 2, [3, 3], [5, 6, [7, 8, [9, 10], 11]], 4]

// The above example show how arrayUnique function remove duplicate elements from array s
// On the first sight, the function is able to return the same output as example answer, however:
// 1. Please find edge case(s) that cause the function to return wrong answer.
// 2. Explain why the edge case(s) break the function and also the limitation of the function.
// 3. Write a solution that also work with the edge case(s).
// no tricks no traps, the is pure logic questions, you dont need to sanitize the input
// This question test your understanding on JS array datatype, the elegant solution in other languages like Python will not work in JS.
```
