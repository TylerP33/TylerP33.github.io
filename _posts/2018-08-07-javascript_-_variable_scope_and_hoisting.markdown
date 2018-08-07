---
layout: post
title:      "JavaScript - Variable Scope and Hoisting"
date:       2018-08-07 10:37:17 -0400
permalink:  javascript_-_variable_scope_and_hoisting
---

We encounter a ton of information throughout this program.  So much so, that even when you think you have covered all your tracks with good notes, concepts still manage to fall through the cracks.  A perfect example of this is trying to keep straight all the rules and scenarios for scope and hoisting within JavaScript.  Seeing that those two concepts play an integral part in JavaScript, I thought a blog review post would be a great idea!

The definition of "hoisting" is JavaScript's default behavior of moving all declarations to the top of the current scope.  In JavaScript, we hav two possibilties of scope; we have the top of the current script or the top of the current function.  We call this local and global scope.  Here is a simple example of a hoisting within a script.


```
<!DOCTYPE html>
<html>
<body>

<p id="demo"></p>

<script>
x = 5; // Assign 5 to x

elem = document.getElementById("demo"); // Find an element 
elem.innerHTML = x;                     // Display x in the element

var x; // Declare x


</script>

</body>
</html>
```


As you can see, we have assigned x = 5 before we have even assigned a variable X.  The output will still be 5.  Essentially, a variable can be used before it has been declared.  That is because the `var x;` gets hoisted to the top of the script.  To show the inverse, take a look at this example:

```
<!DOCTYPE html>
<html>
<body>

<p id="demo"></p>

<script>
var x; // Declare x
x = 5; // Assign 5 to x

elem = document.getElementById("demo"); // Find an element 
elem.innerHTML = x;                     // Display x in the element
</script>

</body>
</html> 
```

The `var x;` starts at the top, and x=5 is interpretated after.  The tricky question is, is `var x;` interpreted before x = 5 in the first script?  Yes!  That is because `var` declarations will be hoisted.  `let` and `const` declarations are "hoisted" as well, in that the scope indentifier will always reference that particular variable (not the assignment).  With that being said, there is a dramatic differnce between `var` declarations and the other two variable choices, `let` and `const`.    

This difference is in their initialisation. `var` and `function` are initialised with undefined, which does not cause an error, and it allows the variable expression to match the variable declaration at run-time.  `let` and `const` are will throw an ReferenceError when you try to access it.  These specific variable types only get initialised when a `let`/`const`/`class` statement is evaluated.  Everything before (above) is called the "temporal dead zone".  

Here is a perfect example of the two:

```
x = y = "global";
(function() {
    x; // undefined
    y; // Reference error: y is not defined

    var x = "local";
    let y = "local";
}());
```

Notice the reference error "y" is getting compared to the undefined "x" is getting?  That is because both variables are hoisted, but only one is being allowed to be retroactively assigned (`var`).  Pretty nifty, huh?

Just for good measure, here is another example displaying `let` and `const` hoisting issues:

```
(function() {              //IIFE
    console.log(hero);     //ReferenceError hero is not defined
    console.log(antiHero); // ReferenceError antiHero is not defined
    let hero       = "Atom";
    const antiHero = "CaptainCold";
})();
```


We have talked about global scope (in a script) and we have shown some examples of local scope (in a function).  We have not talked about block scope yet though!  Variables that are declared with `let` and `const` have the block scope, as well as any continued sub-blocks as their scope.  Here is a good example for this:

```
(function() {              //IIFE
    let hero = "Batman";
    if(true) {
        let hero = "The Flash";
        console.log(hero); //The Flash
    }
    console.log(hero);     //Batman
})();
```

Just so show another example of the difference between global/local scope, and how they pertain to `var` and `let`:

```
var hero     = "Batman";
let antiHero = "Captain Cold";
if (true) {
    var hero     = "The Flash";     //scope is global
    let antiHero = "Reverse Flash"; //scope is (local) block-level
    console.log(hero);              //The Flash
    console.log(antiHero);          //Reverse Flash
}
console.log(hero);                  //The Flash
console.log(antiHero);              //Captain Cold
```

You have two `let` variables that are declared as `antiHero`.  One is declared inside a block, while the other remains at the top of the script.  When we run console.log outside of the block, the `let` variable's assignment at the top of the script is returned.  Now, when we run console.log on the block-level `let`, as we can see, it only has access to the block level assignment.  With `var`, there is something strickingly different about the assignment value.  it stays consistent with the block result!

Inside the block, we can see that `var` gets change to "The Flash".  This assignment extends into the global scope, and maintains that same assignment value, even though, at the top of our script, ```var hero     = "Batman"```.  Var scope is global, therefore, it will maintain that block level scope all the way into the global scope of the script.

Like I said at the beginning, remembering all the nuances of scope and hoisting isn't too tough once you re-read the information.  But, the key is to stay on top of these important concepts and make them second nature in your programming.


