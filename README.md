![alt text](https://timdoes.com/img/tutorials/react/testing-with-react-babel-mocha-expect/heading.png "React Testing with React, Babel, Mocha, and Expect")

# React Testing with React, Babel, Mocha, and Expect

## Lesson 1

### 1. Create a new node project

To create our testing node project, let's open our command line. Since I am on a mac, I will be using *Terminal*. First we need to enter our Projects directory (where we keep all our web projects). Then we need to create our project folder and enter it (let's keep it small for easy viewing). Finally, we will initialize our node project. To do all this, let's enter the following commands. Remember to change **Projects** to whatever directory you use.

`cd ~/Projects`  
`mkdir react-testing && cd react-testing`  
`npm init`

Keep pressing `enter` to select all the defaults as this will create our bare **package.json** file.

### 2. Viewing our **package.json** file

Let's open our project in our favorite IDE. For example, I use [https://atom.io/](atom.io) so I will open the project with the following command:

`atom .`

Now if we look at our **package.json** file we will see:

```js
/*  /package.json  */
{
  "name": "react-testing",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

### 3. Install dependencies

Time to install the dependencies we need to run our tests. To do so we will head back to *Terminal* and type:

`react react-dom --save`  
`babel-core babel-preset-es2015 babel-preset-react babel-preset-stage-2 expect mocha react-addons-test-utils --save-dev`

Our **package.json** file should now look like:

```js
{
  "name": "react-testing",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "react": "^0.14.6",
    "react-dom": "^0.14.6"
  },
  "devDependencies": {
    "babel-core": "^6.4.0",
    "babel-preset-es2015": "^6.3.13",
    "babel-preset-react": "^6.3.13",
    "babel-preset-stage-2": "^6.3.13",
    "expect": "^1.13.4",
    "mocha": "^2.3.4",
    "react-addons-test-utils": "^0.14.6"
  }
}
```

### 4. Create Babel presets

> For more information on setting up Babel 6 plugins and presets, visit [babeljs.io](http://babeljs.io/blog/2015/10/31/setting-up-babel-6/)

Since we will be using ES2015, aka ES6, we will need to make sure we compile our code down to ES5.

To keep this short and sweet we will just be using the few presets presets we installed earlier.

Tell Babel to use them by creating a **.babelrc** file in the root directory.

```js
/*  /.babelrc  */
{
  "presets": [
    "es2015",
    "react",
    "stage-2"
  ]
}
```

## 5. Create `npm run test` command

Now we need to tell node where our test files are located and how to run them. This is done with one simple line of code. In our **package.json** file, let's change the `test` command in the scripts section to the following:

```js
/*  /package.json  */
{
  ...
  "scripts": {
    "test": "mocha './src/**/*.test.js' --compilers js:babel-core/register"
  },
  ...
}
```

This tells node to use mocha for testing and to look for any file in our **/src/** directory, under any folder **/src/\*\*/**, and with the file extension **/src/\*\*/\*.test.js**.

We can run the test command, `npm run test` at any time from the root directory of our project in our command line.

But first we need to create our first test file.

## 6. Creating our first test file

To make sure we have everything setup correctly, let's make our first test file, ...drumroll... **first.test.js**.

```js
import expect from 'expect';

describe('first test', () => {

  it('should be true', () => {
    expect(true).toEqual(true);
  });

});
```

## 7. Running our first test!

So now we are ready to run our first test in *Terminal*.

`npm run test`

If all goes well we should see:

![alt text](https://timdoes.com/img/tutorials/react/testing-with-react-babel-mocha-expect/screenshot_1_7.png "Results for first.test.js")

Success! Now it's time to pick up our game and start building some real tests in Lesson 2 (Coming soon). Stay tuned as next we will learn how to build failing tests and then build the components to make them pass.
