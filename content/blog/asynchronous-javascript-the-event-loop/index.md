---
title: "Asynchronous JavaScript: The Event Loop"
date: "2020-05-17"
category: "JavaScript"
---

![](./asynchronous_javascript.png)

If you're talking about Asynchronous JavaScript, it's really important to understand the **event loop** and how things work under the hood.

Let's take an example to understand a simple asynchronous operation in JavaScript.

```js
setTimeout(() => {
    console.log("Hello")
}, 1000)

console.log("Me first")

//me first
//Hello
```

> `setTimeout` is a browser API that executes a piece of code after a specified time interval like 1000ms, 2000ms, etc. You can read about it in detail [here](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Timeouts_and_intervals#setTimeout).

<br>

The order of execution will be **me first** and then **Hello**- because of the non-blocking nature of JavaScript.

We all know that JavaScript works on as single thread, also known as the _main thread_. In case of async scenarios like waiting for some seconds to complete a task, the main thread needs to be blocked-- but that's not really how JavaScript works. Let's dig into it!

<br>


* When `setTimeout` is called, a **timer** fires up in the browser. In our case, the timer expires in 1000ms. This timer has a reference to our callback function. In order for the cb function to be executed, it needs to be pushed to the call stack. **CallStack is a data structure that keeps track of functions and the order in which they are executed**.

<br>

* When our timer finishes in the background, the callback function is ready to get executed, **but before that**, it doesn't really get pushed to the call stack directly. Instead, It gets _queued_ to the callback queue. Now, the control shifts to the event loop.

<br>

* Event loop is a **process** that checks whether the call stack is empty or not. If it's empty, the event loop takes out our function from the callback queue- or **deques** it- and pushes it to the call stack. Now, the function gets executed and prints out **"Hello"**. The event loop just sits between the call stack and the task/cb queue.

<br>


Coming back to our example again, JavaScript encounters the first line; Oh! It's a `setTimeout`, we'll have to wait for it to finish in the background. Meanwhile, jump to the next line which reads `console.log("Me first")`. So it just logs that out. After, it logs "Hello".

Similarly, if we take this example, the result will still be the same!!


```js
function sayHello() {
  console.log("Hello")
}

function meFirst() {
  console.log("me first")
}

setTimeout(sayHello, 1000)
meFirst()


//me first
//hello
```

* `setTimeout` is invoked; it goes to the Web API land where the timer runs.
*  Meanwhile, `meFirst` function is pushed to the stack, prints "**me first**", and gets popped off.
*  Timer completes, the cb `sayHello` gets _queued_ to the callback queue/task queue.
*  Now, the call stack looks empty because `meFirst` has already been popped off.
*  So, event loop pushes the cb `sayHello` to the stack.
*  "**hello**" gets printed.

<br>


If you want to visualize, you can check out for yourself how the event loop is working- [here](http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D).

<br>

![](https://media.giphy.com/media/Rl4wAR60aSSDhnpTnd/giphy.gif)


<br><br>

**Thank You for reading this article. Follow me on [Twitter](https://twitter.com/_himalayan_) for more updates.**







