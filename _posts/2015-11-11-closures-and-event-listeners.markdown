---
layout: post
title:  "Closures and Event Listeners"
categories: javascript
---

#Closures and Event Listeners

{% highlight javascript %}
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
{% endhighlight %}

>The bolded part is the outer function. We immediately invoke it by wrapping it in parentheses and calling it right away, passing in num. This method of wrapping an anonymous function in parentheses and calling it right away is called an IIFE (Immediately-Invoked Function Expression, pronounced like "iffy"). This is where the "magical" part happens.

>We're passing the value of num into our outer function. Inside that outer function, the value is known as numCopy -- aptly named, since it's a copy of num in that instant. Now it doesn't matter that num changes later down the line. We stored the value of num in numCopy inside our outer function.

>Lastly, the outer function returns the inner function to the event listener. Because of the way JavaScript scope works, that inner function has access to numCopy. In the near future, num will increment, but that doesn't matter. The inner function has access to numCopy, which will never change.

>Now, when someone clicks, it'll execute the returned inner function, alerting numCopy.

---

## [Don't make functions within a loop](https://jslinterrors.com/dont-make-functions-within-a-loop)

{% highlight javascript %}
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
{% endhighlight %}

>This will work as we expect it to but the problem now is that the JavaScript interpreter will create an instance of the capturing function per loop iteration. It has to do this because it doesn't know if the function object will be modified elsewhere. Since functions are standard JavaScript objects, they can have properties like any other object, which could be changed in the loop. Thus by creating the function in the loop context, you cause the interpreter to create multiple function instances, which can cause unexpected behavior and performance problems. To fix the issue, we need to move the function out of the loop: