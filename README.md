# **Exercise portfolio**
This repository showcases a few of my solutions to the assignments I have done in Trainee Academy. I have chosen two assignments that I thought were educational and interesting. They represent a variety of programming concepts we have learned and that I feel I am now using confidently.
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

## **Assignment#2:Crades**

We have the following list of students:
```javascript
const students = [ { name: "Sami", score: 24.75 },
                   { name: "Heidi", score: 20.25 },
                   { name: "Jyrki", score: 27.5 },
                   { name: "Helinä", score: 26.0 },
                   { name: "Maria", score: 17.0 },
                   { name: "Yrjö", score: 14.5  } ];

```
Create a function getGrades that takes a list of students as a parameter and returns the students' grades in a new array.
Scores are converted to grades in the following way:

< 14.0 results in grade 0
[14.0, 17.0] results in grade 1
]17.0, 20.0] results in grade 2
]20.0, 23.0] results in grade 3
]23.0, 26.0] results in grade 4


26.0 results in grade 5



Note the inclusive/exclusive bounds! For example, the range [14.0, 17.0] includes both 14.0 and 17.0, while the range ]17.0, 20.0] excludes 17.0 (but includes everything that is just above 17.0, even 17.000001).

Instead of returning only an array of grade numbers, return an array of new objects, where each object contains the student's name and their grade.

### Solution

**1)**

The code defines an array called students with objects containing the name and score for each student.

```javascript
const students = [ { name: "Sami", score: 24.75 },
                   { name: "Heidi", score: 20.25 },
                   { name: "Jyrki", score: 27.5 },
                   { name: "Helinä", score: 26.0 },
                   { name: "Maria", score: 17.0 },
                   { name: "Yrjö", score: 14.5  } ];
```

**2)**

The getGrades function takes an array of student objects as its argument and returns a new array that maps each student to an object containing their name and grade.
The function uses the Array.prototype.map() method to iterate over each student object in the input array.
For each student object, the function calculates the student's grade based on their score using a series of conditional statements.
The function creates a new object with the student's name and calculated grade, and returns this object to the new array that is being built by the map() method.
Once the map() method has processed all of the student objects in the input array, it returns a new array of objects that contain each student's name and grade.

```javascript
function getGrades(studentArray) {
    return studentArray.map(student => {
        let grade;
        if (student.score < 14.0) {
            grade = 0;
        } else if (student.score <= 17.0) {
            grade = 1;
        } else if (student.score <= 20.0) {
            grade = 2;
        } else if (student.score <= 23.0) {
            grade = 3;
        } else if (student.score < 26.0) {
            grade = 4;
        } else {
            grade = 5;
        }
        return {name: student.name, grade:grade};
    });
}
```

**3)**

The code calls the getGrades function with the students array as its argument, and stores the resulting array of objects in a variable called grades.
Finally, the code prints the grades array to the console using the console.log() method.

```javascript
const grades = getGrades(students);
console.log(grades);
```

So, when you run this code, you will see an array of objects in the console that contains the name and grade for each student, based on the grade calculation rules in the getGrades function.





