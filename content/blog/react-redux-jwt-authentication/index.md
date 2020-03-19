<!-- ---
title: 'React-Redux JWT Authentication'
date: '2020-03-12'
category: 'React'
---

![](https://pushed.to/cokeSchlumpf/rethink-it/posts/images/2018-01-26_reactredux.png)

In this article, we'll look at how JWT authentication works in a full stack application. We'll be using React on the frontend with a little help from Redux in managing the state, and node.js, express and mongodb on the backend.

We're going to build a simple auth application which involves registration and login. React- Bootstrap is what we're going to use for styling the app.

Before we get started, I assume you are familiar with React and Redux. You can read more about those two from the official docs, as well as from my articles.

So, let's get started.
<hr>
<br><br>

We're going to set up the boilerplate for our application. In order to do that, open your terminal and type:

```js
express --view=ejs react-redux-auth
```

The above command will create an express application for us with **ejs** as the default templating engine. The folder structure would look like this:

```js
react-redux-auth
  > bin
  > public 
  > routes
  > views
  > app.js
  > package.json
```

That's the backend boilerplate. Now, we're going to configure webpack as the module bundler for our app, in simple words, it just grabs our entire code, do some transformations, and generate a bundle. You can read more about webpack [here](http://www.codehunt.tech/setting-up-a-react-project-using-webpack-and-babel/).











    















 -->
