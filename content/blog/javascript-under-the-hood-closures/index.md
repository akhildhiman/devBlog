---
title: 'JavaScript Under The Hood: Closures'
date: '2020-02-19'
category: "JavaScript"
---

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRK9UTas_jNfrVLzDyWYtgJuetp8nqYmKe_hXzEhcZj_Ao8NJHP)

Before jumping straight into closures, one should have a clear understanding of how scoping works in JavaScript. There are two types of scopes- **local** and **global**.

* Variables declared outside of code block have global scope.
* Variables declared inside of a block have local scope.

<br>

```js
var bandName = "Ministry"
```
In the example above, we have declared a global variable ```bandName``` and assigned it a value.

<br><br>

```js
var bandName = "Ministry" // global variable

function main() {
    var bandName = "Mayhem" // locally-scoped variable becuase var is functionally scoped
    console.log(bandName)
}

console.log(bandName)
main()
console.log(bandName)


// Output
Ministry
Mayhem
Ministry
```

> The above example would have the same output if we used let in place of var.

<br>

> Variables declared with ```var``` have no block-scope unlike ```let``` and ```const```. They're only functionally-scoped. 

<br><br>

There's one thing about ```var``` that it can be reassigned as compared to ```let``` and ```const```.





```js
var condition = true

var bandName = "Ministry" //declaring globally

    if (condition) {
        var bandName = "Mayhem" //reassigning
        console.log(bandName)
    }

console.log(bandName)

// Output
Mayhem
Mayhem
```

Here, we're decaring ```bandName``` as a global variable. Inside the block of a **if** statement, we're reassigning another value to the same variable. The output in same both the time because, block scoping doesn't work with the ```var``` keyword. It does not understand that it's a part of the block of the if statement. On the other hand, let understands that it's a part of the if statement's code block. 

Now, if we try and use ```let``` instead of ```var```, we should see something different.


```js
var condition = true

let bandName = "Ministry" //declaring globally

    if (condition) {
        let bandName = "Mayhem" //declaring locally
        console.log(bandName)
    }

console.log(bandName)

// Output
Mayhem
Ministry
```


If you want to know about hoisting, you can read my previous article [here](http://www.codehunt.tech/es6-and-variable-hosting/).
<hr>
<br><br>


# Closure














