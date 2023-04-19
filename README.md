# **trainee-academy-assignments**
This repository showcases a few of my solutions to the assignments I have done in Trainee Academy. I have chosen three assignments that I thought were educational and interesting. They represent a variety of programming concepts we have learned and that I feel I am now using confidently.
Only the essential parts of the code are included in this document. The full executable versions can be found from this repository.

## **Assignment#1:Repetitive code**
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
Create another function that figures out which triangle had the biggest area and prints it. For example, if the area of the third triangle was biggest, it'd print "Third triangle has biggest area!". Call your function at the end of the code

### Solution
**1)**

The calculateTriangleArea function is defined with a single parameter triangle. This function calculates the area of a triangle using the formula: area = (width * length) / 2.0.
```javascript
function calculateTriangleArea(triangle){
   return triangle.width * triangle.length / 2.0;
}
```
**2)**

Create three triangle objects, each with a width and length property.

```javascript
const firstTriangle = { width: 7.0, length: 3.5 };
const secondTriangle = { width: 4.3, length: 6.4 };
const thirdTriangle = { width: 5.5, length: 5.0 };
```
**3)**

Calculate the area of each triangle using the calculateTriangleArea function, and log the result to the console using console.log.

```javascript
console.log("Area of first triangle: " + calculateTriangleArea(firstTriangle));
console.log("Area of second triangle: " + calculateTriangleArea(secondTriangle));
console.log("Area of third triangle: " + calculateTriangleArea(thirdTriangle));
```

**4)**

Define a function printLargestTriangle that takes three triangle objects as input.
Inside printLargestTriangle, call calculateTriangleArea for each of the three triangles, and store the result in areaOne, areaTwo, and areaThird.

```javascript
function printLargestTriangle(triangleOne, triangleTwo, triangleThird){
    const areaOne = calculateTriangleArea(triangleOne);
    const areaTwo = calculateTriangleArea(triangleTwo);
    const areaThird = calculateTriangleArea(triangleThird);
```

**5)**

Compare the areas of the three triangles using if...else if...else statements to determine which triangle has the largest area.
Log the result to the console using console.log.

```javascript
    if (areaOne >= areaTwo && areaOne >= areaThird){
        console.log("First triangle has biggest area!")
    }else if(areaTwo >= areaOne && areaTwo >= areaThird){
        console.log("Second triangle has biggest area!")
    }else{
        console.log("Third triangle has biggest area!")
    }
}
```
**6)**

Call the printLargestTriangle function with the three triangle objects as input, to find and print the triangle with the largest area.

```javascript
printLargestTriangle(firstTriangle, secondTriangle, thirdTriangle)
```

## **Assignment#2:Repetitive code**





