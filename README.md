# **trainee-academy-assignments**


## **Assignment#3:Repetitive code**
The following code has 3 triangles with different lengths for their cathetuses. The trianges' areas are calculated and printed.
However, if you look at the code, you'll notice that it has some repetition. In particular, the way the area is calculated for a triangle is repeated 3 times.
The code would be cleaner if that calculation was split into its own function that took a triangle as a parameter and returned the area of the given triangle. That function could  then be called 3 times (once for each triangle) instead of having the calculation just copy-pasted in the code.
Split the area calculation into its own function as described above and replace the repetitive calculations with calls to your function.
Create another function that figures out which triangle had the biggest area and prints it. For example, if the area of the third triangle was biggest, it'd print "Third triangle has biggest area!". Call your function at the end of the code.


```javascript
const firstTriangle = { width: 7.0, length: 3.5 };
const secondTriangle = { width: 4.3, length: 6.4 };
const thirdTriangle = { width: 5.5, length: 5.0 };

let firstTriangleArea = firstTriangle.width * firstTriangle.length;
firstTriangleArea = firstTriangleArea / 2.0;

let secondTriangleArea = secondTriangle.width * secondTriangle.length;
secondTriangleArea = secondTriangleArea / 2.0;

let thirdTriangleArea = thirdTriangle.width * thirdTriangle.length;
thirdTriangleArea = thirdTriangleArea / 2.0;

console.log("Area of first triangle: " + firstTriangleArea);
console.log("Area of second triangle: " + secondTriangleArea);
console.log("Area of third triangle: " + thirdTriangleArea);
```
### Solution
```javascript
function calculateTriangleArea(triangle){
   return triangle.width * triangle.length / 2.0;
}

const firstTriangle = { width: 7.0, length: 3.5 };
const secondTriangle = { width: 4.3, length: 6.4 };
const thirdTriangle = { width: 5.5, length: 5.0 };


console.log("Area of first triangle: " + calculateTriangleArea(firstTriangle));
console.log("Area of second triangle: " + calculateTriangleArea(secondTriangle));
console.log("Area of third triangle: " + calculateTriangleArea(thirdTriangle));

function printLargestTriangle(triangleOne, triangleTwo, triangleThird){
    const areaOne = calculateTriangleArea(triangleOne);
    const areaTwo = calculateTriangleArea(triangleTwo);
    const areaThird = calculateTriangleArea(triangleThird);

    if (areaOne >= areaTwo && areaOne >= areaThird){
        console.log("First triangle has biggest area!")
    }else if(areaTwo >= areaOne && areaTwo >= areaThird){
        console.log("Second triangle has biggest area!")
    }else{
        console.log("Third triangle has biggest area!")
    }
}

printLargestTriangle(firstTriangle, secondTriangle, thirdTriangle)
```





