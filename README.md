# **trainee-academy-assignments**

This repository showcases a few of my solutions to the assignments I have done in Trainee Academy. I have chosen three assignments that I thought were educational and interesting. They represent a variety of programming concepts we have learned and that I feel I am now using confidently.
Only the essential parts of the code are included in this document. The full executable versions can be found from this repository.

## **Assignment #1: Cleanup**:

### The assignment

```javascript
const objectArray = [ 
    { x: 14, y: 21, type: "tree", toDelete: false },
    { x: 1, y: 30, type: "house", toDelete: false },
    { x: 22, y: 10, type: "tree", toDelete: true },
    { x: 5, y: 34, type: "rock", toDelete: true },
    null,
    { x: 19, y: 40, type: "tree", toDelete: false },
    { x: 35, y: 35, type: "house", toDelete: false },
    { x: 19, y: 40, type: "tree", toDelete: true },
    { x: 24, y: 31, type: "rock", toDelete: false } 
];
```

There are some entries in the above array that are marked to be deleted.
1. Erase the entries by finding them and setting them to null. Do not replace the original array, but modify it instead.
2. Erase the entries by generating a new array with Array.map where the objects to be deleted have been replaced with null and the rest stay as-is.
3. Imagine that instead of 9 entries, the above array would have 100,000 entries. What would be the implications for performance and memory use between doing it like in 1) or like in 2)? To answer this question, write a comment to your source where you present your thoughts on the subject.


### Initial thoughts

There are two assignments. In both I want the result to be an array with equal amount of elements as in the original array, but with some of the elements being null. In the first one I need to modify the original array, and in the second one I will create a new array.

In the first assignment I need to iterate through every element of the array, modifying it as we move from one to the next. In the second one the array method `map` takes care of the actual iteration and I need just to implement the logic for creating new elements.

I decided to first do 1) and 2), and after having solutions think about 3) when I have something concrete down.

### Solution

#### 1)
```javascript
for (let i = 0; i < objectArray.length; i++) {
    if (objectArray[i] !== null && objectArray[i].toDelete) {
        objectArray[i] = null;
    }
}
```

In this solution to the first part I first check that the objectArray element is not null, since I can't check the value of the toDelete parameter if that would be the case. If the element is not null and it does have the toDelete parameter set to true, the element in question will be set to null.

#### 2)
```javascript
const cleaned = objectArrayCopy.map(element => {
    if (element === null || !element.toDelete) {
        return element;
    }

    return null;
});
```

In this solution to the second part I use the map method as required. The callback function that takes the element as parameter first checks if the element is null. If so, the element itself is returned. If the element is not null, it continues to check if it has a truthy toDelete property. If that is not the case, again the element itself is returned.

In all other cases null is returned. This means that null is returned if the element was *not* null *and* it had a truthy toDelete property.

#### 3)
Since the approach used in 2) creates a copy of the array, it takes more memory and typically also executes slower. Assuming no special optimizations, the performance of processing big arrays could be significantly worse with 2), especially if it's done often.

## **Assignment#2:Social media buttons**

### The assignment
Re-create the following page with HTML, Bootstrap and CSS.
Each icon and the text under it should be inside one element that’s a link to the respective page.

### Solution

```html
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Social</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <link href="style.css" rel="stylesheet"></script>
  </head>
  <body class="text-center">
    <div class="background">
        <h1>My Social Media Accounts</h1>
      <div class="main-container text-center">
        <div class="container mt-5 mb-5 pt-3">
          <div class="row">
            <div class="col text-center">
              <a href="https://github.com"><img class="socialimg" src="./images/github.png" alt="GitHub" /><p>GitHub</p></a>
            </div>
            <div class="col text-center">
              <a href="https://www.moddb.com"><img class="socialimg" src="./images/moddb.png" alt="ModDB" /><p>ModDB</p></a>
            </div>
            <div class="col text-center">
              <a href="https://www.youtube.com"><img class="socialimg" src="./images/youtube.png" alt="YouTube" /><p>YouTube</p></a>
            </div>
            <div class="col text-center">
                <a href="https://fi.linkedin.com"><img class="socialimg" src="./images/linkedin.png" alt="LinkedIn" /><p>LinkedIn</p></a>
            </div>
            <div class="col text-center">
                <a href="https://twitter.com"><img class="socialimg" src="./images/twitter.png" alt="Twitter" /><p>Twitter</p></a>
            </div>
            <div class="col text-center">
                <a href="https://instagram.com"><img class="socialimg" src="./images/instagram.png" alt="Instagram" /><p>Instagram</p></a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </body>
</html>
```
```css
.socialimg {
    width: 6em;
    height: 6em;
}

h1 {
    color: #ff00ff;
    text-shadow: 0.05em 0.1em #FFFFFF;
}

a {
    color: white;
    text-decoration: none;
}    

body {
    background-color: #222222;
    color: #dddddd;
    height: 100vh;
}

.background {
    margin: auto;
    padding: 0;
    position: absolute;
    width: 100%;
    min-height: 100%;
}

.main-container {
    font-size: 1.25em;
    font-weight: bold;
    vertical-align: middle;
    max-width: 70em;
    margin: auto;
    outline: 0.5em dashed #bb00bb;
    background-color: rgba(255, 0, 128, 0.5);
    border-radius: 2em;
}
```

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





