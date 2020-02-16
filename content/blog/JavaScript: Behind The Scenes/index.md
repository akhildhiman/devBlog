---
title: 'The Execution Context'
date: '2020-02-16'
category: "JavaScript"
---

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRK9UTas_jNfrVLzDyWYtgJuetp8nqYmKe_hXzEhcZj_Ao8NJHP)


Before you dive deep into JavaScript, it's important to understand what's going on behind the scenes. 

We all know that JavaScript is a single threaded programming language. It means that the thread of execution executes one line of code at a time.

**Execution Context** is the environment created when our code runs. When we start the program, we are in the Global Execution Context and whenever a function is called or invoked, we enter the Local Execution Context. There are two parts in an Execution Context that we must know:

* **Thread of Execution**- goes through line by line and executes the code.
* **Memory**- the variables and functions declared will be stored in the computer's memory by JavaScript for later use.

<br>

Let's look at this example to understand what actually happens when JavaScript sees our code.


```js
const num = 3
function multiplyBy2(inputNumber) {
    const result = inputNumber * 2
    return result
}

const output = multiplyBy2(num)
const newOutPut = multiplyBy2(10)
```

Alright, by default, we are in the **Global Execution Context** and it has a memory called **Global Memory.**

<br>

**Global Memory**
* We declare a ```const``` **num** and assign it a value of 3. 
* We define a function by the identifier or label ```multiplyBy2``` and store the entire function definition in it.
* The thread of execution goes down. Now, we declare a const ```output```. At the time, we don't know its final value, but what we know is that the ```output``` const will store the result of ```multiplyBy2``` function.

<br>

So, we've now encountered a function invocation, and whenver a function is invoked, we create a **Local Execution Context.** Let's jump into it. 

### Local Execution Context of **multiplyBy2(num)**
* We store the parameter ```inputNumber``` in the local memory and assign it a value of 3. ```inputNumber``` is a placeholder for the argument ```num```(  in fact, it's called a parameter) which is equal to 3, because it has already been declared in the global memory.
* Next up, we decare the const ```result``` and store the result of ```inputNumber * 2```,  which is 6. 
* We return the value of the ```result``` const. JavaScript looks for the value of ```result```, finds it in the local memory, returns it, and thus we now have the value for the const ```output``` equals to 6 in the global memory.

 ```js
const output = 6
  ```

* The function ends and the Local Execution Context is destroyed. The thread of execution is back to Global code from the function code. It's also popped out from the **Call Stack.**

<br>

> Call Stack is a data structure that keeps track of our code. It tells us which function's execution context is running, so the thread of execution points to that function in the call stack. Whenever a function is invoked, we create a local execution context and push it to the callstack, and when it's finished, we pop it off. Global code is by default in the call stack as soon as we start running our code. There can only be one function running at a time. Callstack helps keep track of that.
<br>

<br>

![](https://miro.medium.com/max/638/1*CCHexfHNCNo-f8aw3rbRew.jpeg)
Now, we're back in global. In the last line, we declare another const with the label of ```newOutPut```. Once again, we don't know its final value yet. By default, it is **unitialised**.

### Local Execution Context of **multiplyBy2(10)**

* We push this function to the top of the callstack.
* We'll do the same steps again and again. 
* We assign ```inputNumber``` with a value of 10 in the local memory, get the result and assign it to  ```newOutPut``` in the global memory.
```js
const newOutPut = 20
```
* Finally, we pop the function off the callstack.
<br><br>

So, that was the whole thing behind Execution Context and how JavaScript runs our code. 

<br>

Thank You for reading this article. Follow me on [Twitter](https://twitter.com/_himalayan_) for more updates.











