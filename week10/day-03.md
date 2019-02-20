# Day 03

What we covered today:

* [Fibonacci Solutions](https://github.com/wofockham/wdi-30/tree/master/13-advanced/recursion)
* [Meteor.js](https://github.com/wofockham/wdi-30/tree/master/13-advanced/simple-todos)

Warmup

* [Collatz](https://github.com/Yiannimoustakas/wdi30-homework/tree/master/warmups/week10/day03_collatz)

## Meteor

Meteor, or MeteorJS, is a free and open-source isomorphic JavaScript web framework written using Node.js. Meteor allows for rapid prototyping and produces cross-platform code. 

* [Meteor.js](https://www.meteor.com/)
* [Class Demo](https://github.com/wofockham/wdi-30/tree/master/13-advanced/simple-todos)

#### Installation

Step 1: Install Meteor

```bash
curl https://install.meteor.com/ | sh
```

Step 2: Create Meteor Project

```bash
meteor create simple-todos
```

Step 3: cd into new folder

```text
cd simple-todos
```

Step 4: Install react dependencies

```bash
meteor npm install --save react react-dom
```

Step 5: Remove and add local Meteor dependencies

```bash
meteor remove blaze-html-templates
meteor add static-html
meteor add react-meteor-data
```

Step 6: Start Meteor Server

```bash
meteor
```







