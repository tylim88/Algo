# Async Function Behavior.md
```javascript
var a = async () => {
	console.log(1)
	const b = await 2
	console.log(b)
	return console.log(3)
}
console.log(0)
a()
console.log(4)
```

guess the output
