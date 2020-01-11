---
title: 'Getting Started with React Router '
date: '2020-01-11'
category: "React"
---

![](https://repository-images.githubusercontent.com/19872456/05dca500-f010-11e9-9588-a96554294e4e)

React Router is a declarative library built on top of React to create dynamic routing in React applications. When we say [dynamic routing](https://reacttraining.com/react-router/web/guides/philosophy), we mean routing that takes place when you app is rendering. Everything is considered a Component in React Router. The [official docs](https://reacttraining.com/react-router/web/guides/quick-start) are well-wriiten and more than enough to get started with. 

So, let's get started with React Router.

<br>

## Basic Routing

First and foremost, we need to import ```BrowserRouter```, ```Link``` and ```Route``` from **react-router-dom**.


* **BrowserRouter**- You'd simply say it is a component that is needed to enable routing in our application. We wrap the nested routes within the <Router> component. Basically, it keeps the UI in sync with the url we are navigating to. It uses the history API and has its own advantage. Let's look at an example.

```js
<Route path="/about" component={About} />
```

Here, **About** component will have access to the ```history``` object. It comes in handy whenver we have to redirect to another page, with the use of history's ```push``` method.


* **Link**- Link component basically generates an anchor tag. 

```js
 <Link to="/about">About</Link>
 ```

 Whenver we click on a link, the route will change. Here, when we click on the **About** link, it will simply take us to the **/about** route, and we can see the content in the **About page.**

 * **Route**- In order to see what component should be rendered when the path matches, we will use the **Route** component. 

 ```js
<Route path="/about" component={About} />
```
Here, when the path matches to **/about**, we want the **About** component to get rendered.

Check this CodeSandbox out below:

<iframe
     src="https://codesandbox.io/embed/agitated-newton-7z08i?fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="react-router-1"
     allow="geolocation; microphone; camera; midi; vr; accelerometer; gyroscope; payment; ambient-light-sensor; encrypted-media; usb"
     sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"
></iframe>


## URL Parameters

Here's another simple example to understand the url parameters.

```js
import React, { Component } from "react";
import "./styles.css";
import { BrowserRouter as Router, Link, Route } from "react-router-dom";

const Home = () => {
  return <h2>Home</h2>;
};

const About = () => {
  return <h2>About</h2>;
};

const Topic = props => {
  return <h2>{props.match.params.topicId}</h2>;
};

const Topics = props => {
  return (
    <div>
      <h2>Topics</h2>
      <ul>
        <li>
          <Link to={`${props.match.url}/rendering`}>Rendering with React</Link>
        </li>

        <li>
          <Link to={`${props.match.url}/components`}>Components</Link>
        </li>

        <li>
          <Link to={`${props.match.url}/props-v-state`}>Props v State</Link>
        </li>
      </ul>

        // :topicId is like a placeholder here.
        // We can access this topicID in our Topics component
        // with the help of match object's url property.
      <Route path="/topics/:topicId" component={Topic} />

      <Route
        exact
        path={props.match.url}
        render={() => <h3>Please select a topic</h3>}
      />
    </div>
  );
};

class App extends Component {
  render() {
    return (
      <Router>
        <div>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
            <li>
              <Link to="/topics">Topics</Link>
            </li>
          </ul>

          <hr />

          <Route exact path="/" component={Home} />
          <Route path="/about" component={About} />
          <Route path="/topics" component={Topics} />
        </div>
      </Router>
    );
  }
}

export default App;
```

<iframe
     src="https://codesandbox.io/embed/flamboyant-poitras-x5frf?fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="react-router-5"
     allow="geolocation; microphone; camera; midi; vr; accelerometer; gyroscope; payment; ambient-light-sensor; encrypted-media; usb"
     sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"
></iframe>


## Switch and handling "404" routes

Before moving any further, it's important to know the behaviour of Switch component. Switch renders the very first route that matches.

```js
<Switch>
    <Route exact path="/" component={Home} />
    <Route path="/will-match" component={WillMatch} />
    <Route component={404Page} />
</Switch>
```
Here, when we go to _/_ route, ```Home``` will get rendered and when we go to _/will-match_,  ```WillMatch``` will get rendered. If we go to any other route, say, _/movies_, the ```404Page``` component will get rendered saying that the page you requested was not found. 

Try this [CodeSandbox](https://codesandbox.io/embed/autumn-grass-moj8v?fontsize=14&hidenavigation=1&theme=dark).


<br><br>

Thank You for reading this article. Follow me on [Twitter](https://twitter.com/_himalayan_) for more updates.


















