# Sort According to Properties

```javascript
const item = ['ball', 'box', 'ball', 'ball', 'box', 'x']
const price = [2, 2, 2, 2, 2, 5]
const weight = [1, 2, 3, 1, 2, 2]

const itemIndex = {}
const itemPrice = {}
const itemWeight = {}

item.forEach((element, index) => {
    const priceProp = 'price ' + price[index]
    const weightProp = 'weight ' + weight[index]
    if (!itemIndex[element]) {
        itemIndex[element] = {
            [priceProp]: { [weightProp]: [] },
        }
    } else if (!itemIndex[element][priceProp]) {
        itemIndex[element][priceProp] = {
            [weightProp]: [],
        }
    } else if (!itemIndex[element][priceProp][weightProp]) {
        itemIndex[element][priceProp][weightProp] = []
    }

    itemIndex[element][priceProp][weightProp].push(index)
    itemPrice[element] = (itemPrice[element] || 0) + price[index]
    itemWeight[element] = (itemWeight[element] || 0) + weight[index]
})

console.log('index', itemIndex)
console.log('price', itemPrice)
console.log('weight', itemWeight)
```

Question not yet complete, probably will delete this as this is just some long winding question that doesn't really challenge your knowledge or algorithm.
