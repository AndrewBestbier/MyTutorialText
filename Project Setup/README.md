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


Now run the following command to create a **index.html** and **bundle.js** file in the **/dist** directory:



Finally, populate the **index.html** file and **bundle.js** file with the following code respectively:

~~~
<!DOCTYPE html>
<html>
<body>
  <div id="app"></div> <!-- Our React application will be put here -->
  <script src="bundle.js"></script>
</body>
</html>
~~~

and 

~~~
console.log("Redux, React and PouchDb tutorial!");
~~~

If you run the following in your terminal, you should be greeted with a blank page in your browser, with "Redux, React and PouchDb tutorial!" logged in your browser's console.

~~~
open index.html
~~~

Now before we die of boredom, let's get into the more interesting world of React, Redux and PouchDb!