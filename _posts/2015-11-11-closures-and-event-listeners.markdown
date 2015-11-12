---
layout: post
title:  "Closures and Event Listeners"
categories: javascript
---

#Closures and Event Listeners

```javascript
// clear the screen for testing
document.body.innerHTML = '';

var nums = [1,2,3];

// Let's loop over the numbers in our array
for (var i = 0; i < nums.length; i++) {

    // This is the number we're on...
    var num = nums[i];

    // We're creating a DOM element for the number
    var elem = document.createElement('div');
    elem.textContent = num;

    // ... and when we click, alert the value of `num`
    elem.addEventListener('click', (function(numCopy) {
        return function() {
            alert(numCopy);
        };
    })(num));

    document.body.appendChild(elem);
};
```
---
## [Don't make functions within a loop](https://jslinterrors.com/dont-make-functions-within-a-loop)
>This will work as we expect it to but the problem now is that the JavaScript interpreter will create an instance of the capturing function per loop iteration. It has to do this because it doesn't know if the function object will be modified elsewhere. Since functions are standard JavaScript objects, they can have properties like any other object, which could be changed in the loop. Thus by creating the function in the loop context, you cause the interpreter to create multiple function instances, which can cause unexpected behavior and performance problems. To fix the issue, we need to move the function out of the loop:

```javascript
var elems = document.getElementsByClassName("myClass"), i;

function makeClickHandler(i) {
    "use strict";
    return function () {
        this.innerHTML = i;
    };
}

for (i = 0; i < elems.length; i++) {
    elems[i].addEventListener("click", makeClickHandler(i));
}
```
