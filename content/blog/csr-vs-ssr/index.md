---
title: 'Client Side Rendering and Server Side Rendering'
date: '2019-06-11'
category: "JavaScript"
---

![](./ssr-csr.jpg)

When a client interacts with a website, a response is sent in the form of HTML, CSS and JavaScript. That's what the content you see on a web page. Now, two popular techniques that we see in action are- Server Side Rendering and Client-Side Rendering. Let's see what they are!

# SSR:

* When the client requests a webpage, a fully-packed HTML document is sent back.
* It has already been populated with all the CSS and JavaScript required.
* Again, the client requests another page, and the same process repeats. Server does it work and sends back the document. 
* Server-side-rendering hits with SEO beacuse of the inability of Google bots to understand JS.

# CSR:
* This is what most of the SPAs have been using such as Gatsby, React, etc.
* Here, client sends a request to the server; the server sends an empty or minimal html document back. Browser then fetches the JavaScript and populate it on the client side to make the page interactive.
* If you see a minimal HTML on the page source, that's definitely CSR.
* SSR is a bit faster as the HTML gets rendered as compared to the miminal HTML in CSR.

---
<br>
See what the response from the server looks like in case of `create-react-app`. Look how it's so minimal.

```js

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    <meta
      name="description"
      content="Web site created using create-react-app"
    />
    <link rel="apple-touch-icon" href="/logo192.png" />
    <link rel="manifest" href="/manifest.json" />
    <title>React App</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  <script src="/static/js/bundle.js"></script><script src="/static/js/0.chunk.js"></script><script src="/static/js/main.chunk.js"></script></body>
</html>
```


<br><br>

Thank You for reading this article. Follow me on [Twitter](https://twitter.com/_himalayan_) for more updates.





