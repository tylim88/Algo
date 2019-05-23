```javascript
//to get started, simply change originalArray variable to any dimension (mixed or not mixed) you desire

var originalArray = [[1, 1], [1, 1],  2, [3, 3], [5,6,[7,8,[9,10],11]], [3, 3], 4, 4, [5,6,[7,8,[9,10],11]]];
var element = [];
var arrayLength = 0;
var startConcate = false;
var concatingString = "";
var subElement;
var twoDimensionArray = [];
var temp = [];
var temIndex = [];
var subElement2;
var uniqueArray = [];

function convertArrayToElement(array, firstIteration){

	arrayLength = array.length;

	if (arrayLength === undefined) {//check if this an array

		element.push(array.toString());
	}
	else if (arrayLength > 0){

		if (!firstIteration){

			element.push("[");
		}

		array.forEach(function(each){//cannot use conventional for loop or else variable i will be reset to 0 each iteration
						
						if (firstIteration){

							element.push(0);
						}

						convertArrayToElement(each, false);// recursive function

						if (firstIteration){

							element.push(1);
						}
					  }
				     ); 

		if (!firstIteration){

			element.push("]");
		}
	}
}

function convertToTwoDimension(array){

	startConcate = false;
	concatingString = "";
	twoDimensionArray = [];

	for (var i = 0; i < array.length; i++) {

		subElement = array[i];

		if (typeof subElement !== "string") {

			startConcate = !startConcate;

			if (!startConcate) {

				twoDimensionArray.push(concatingString);
				concatingString = "";
			}
		}
		else if (typeof subElement === "string") {//for finite case dont use defualt case "else" for non boolean comparison

			if (startConcate) {

				concatingString += subElement + ",";
			}
		}

		// console.log("startConcate", startConcate); 	
		// console.log("concatingString", concatingString);
	}

}


function getElementIndex(){

	temp = [];
	tempIndex = [];

	for (var i = 0; i < twoDimensionArray.length; i++) {
		
		subElement2 = twoDimensionArray[i];
		
		if(temp.indexOf(subElement2) === -1){

			temp.push(subElement2);
			tempIndex.push(i);
		}
	}
}

function removeDuplicate(array){

	uniqueArray = [];

	for (var i = 0; i < tempIndex.length; i++) {
		
		uniqueArray.push(originalArray[tempIndex[i]]);

	}
	console.log(originalArray);
	console.log(uniqueArray);
}

convertArrayToElement(originalArray, true);
convertToTwoDimension(element);
getElementIndex();
removeDuplicate(originalArray);

// console.log(element);
// console.log(twoDimensionArray);
```

This code is old, will update syntax when I feel want to.
