# filter duplicate object

```javascript
var arr = [
	{ a: 1, b: 2, c: 3 },
	{ ccc: 4 },
	{ a: 10, b: 20, c: 30 },
	{ bbb: 2 },
	{ a: 1, b: 2, c: 3 },
	{ bbb: 2 },
	{ ccc: 3 },
]
var string = JSON.stringify(arr)

var trimmed = string.substring(2, string.length - 2)

var split = trimmed.split('},{')

var unique = new Set(split)

var uniqueArray = Array.from(unique)

var uniqueIndex = uniqueArray.map(e => {
	return split.indexOf(e)
})
var answer = uniqueIndex.map(e => {
	return arr[e]
})

console.log(answer)
```
