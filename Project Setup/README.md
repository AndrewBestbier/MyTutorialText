##Introduction and Outcomes:
Welcome to the first proper stage of the tutorial. By this point, you should have all the prerequisites installed. I recommend that you write all code from scratch, but if you would like to compare your final result at the end of this section, you can view the code on Github. (TODO Link).

At the end of this section, we will have the following: 
 
* A NPM project set up.
* All the nessary packages install for React, ES6, webpack, webpack hot-loading and testing
* An example React component

##Project Setup

The first step is to create the project and navigate into it. 

~~~
mkdir redux-pouch-tutorial && cd $_
~~~

We will now create an NPM project. You will be prompted with numerous questions, but just click 'enter' for now. To create the project, run the following:

~~~
npm init
~~~


Then run the following command to define our project's structure:

```
mkdir src dist test
```
The **src** file is for our project's raw code. The code here, as will be explained later in this tutorial, is compiled into a single file in **/dist/bundle.js**

The **dist** file is for our minified/concatnated code drawn from our **/src** and **/node_modules** files.


Now create a **index.html** and **bundle.js** file in the **/dist** directory and populate the **index.html** file with the following:

~~~
<!DOCTYPE html>
<html>
<body>
  <div id="app"></div> <!-- Our React application will be put here -->
  <script src="bundle.js"></script>
</body>
</html>
~~~

Now before we die of boredom, let's lay the foundation for React/Redux development.

##Package installations

###React

Now let us add **React** to the project. We will also be using **react-hot-loader** to enable us to use hot-loading which will vastly improve our development speed.

~~~
npm install --save react react-dom
npm install --save-dev react-hot-loader
~~~

###Webpack
For this project, we will use **webpack** which is a module bundler. We will also be using **webpack-dev-server** which is a small Node.js Express server. Install these both locally and globally so that we can access these commands from the terminal.

~~~
npm install -g webpack webpack-dev-server 
npm install --save-dev webpack webpack-dev-server
~~~

We will also be install **babel-loader** and **babel-core**. Both **babel-loader** and **babel-core** will enabled use to use React's JSX and ES6 syntax. 

~~~
npm install --save-dev babel-core babel-loader
~~~



Finally, create a file called **webpack.config.js** in the root folder and populate it with the following code:

~~~
var webpack = require('webpack');

module.exports = {
  entry: [
    'webpack-dev-server/client?http://localhost:8080', //Creating a small node/express server
    'webpack/hot/only-dev-server', //So that we can use hot-loading
    './src/index.js' //Our starting point for our development.
  ],
  module: {
    loaders: [{
      test: /\.jsx?$/,
      exclude: /node_modules/,
      loader: 'react-hot!babel'
    }],
  },
  resolve: {
    extensions: ['', '.js', '.jsx'] //We can use .js and React's .jsx files using Babel
  },
  output: {
    path: __dirname + '/dist',
    publicPath: '/',
    filename: 'bundle.js' //All our code is compiled into a single file called bundle.js
  },
  devServer: {
    contentBase: './dist',
    hot: true
  },
  plugins: [
    new webpack.HotModuleReplacementPlugin() //Hot loading
  ]
};
~~~


##Our first component

In your ./src directory, create a file called **Component.jsx** and populate it with the following code:

~~~
import React from 'react';

export default React.createClass({

  render: function() {
    return (
      <div>Hello World!</div>
    )
  }
});
~~~

This is a super simple component that will just render the text: 'Hello World!'. Now in our index.js file - the starting point of our application - we can import our new component. This is done as follows:

~~~
import React from 'react';
import ReactDOM from 'react-dom';
import Component from './Component'; //Our component is imported here

ReactDOM.render(
  <Component/>, //Our component is rendered here
  document.getElementById('app') //Our component is 'pushed' into the div in ./dist/index.html
);
~~~

If you now start up our app with the following command, and navigate to http://localhost:8080/, you should see the text: 'Hello World!'.

~~~
webpack-dev-server
~~~
The great thing about hot-loading, is that you can now change the text in our Component, and it will instantly render the new text in our browser.


##Testing















