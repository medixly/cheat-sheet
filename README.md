# Ultimate Cheat Sheet

if you have any questions dm me

## Table of Contents
- [Setup](#Setup)
- [Git](#Git)
- [Repo Structure](#Repo-Structure)
- [Basic JS](#Basic-js)
- [React Native](#react-native)
- [StyleSheet](#StyleSheet)
- [Navigation](#navigation)
- [Context](#context)

## Setup

### Installing Node.js

- Install Node.js [here](https://nodejs.org/en/).

### Installing Expo

- open terminal/cmd prompt
```
//for windows
npm i -g expo-cli

//for mac
sudo npm i -g expo-cli
```

### Install Expo Go on your mobile device:
- [App Store](https://apps.apple.com/us/app/expo-go/id982107779)
- [Google Play](https://play.google.com/store/apps/details?id=host.exp.exponent&hl=en_US&gl=US)

### Install (if you already heaven't) the code editor of your choice
- I recommend [VS code](https://code.visualstudio.com/)

### How to start new Expo Project:
- Open terminal/cmd prompt and go to directory of your choice
```
expo init [insert project name here]
```

### How to run your project:
- navigate to your project directory in terminal/cmd prompt
```
expo start 
//or
npm start
```
- Then in metro bundler, scan the qr code with your phone

### installing dependencies
```
npm i [dependency name]
```
- can use yarn or expo install instead as well
- after cloning the repo, make sure to run ```npm i``` in order to make sure all dependencies are installed

## Git

### Initialize project as repo (pre-initialized for Expo projects)

```
git init
```

### Clone an existing repository

```
git clone [repo link]
```

### Branches
- important for merging code
  - merge code when two people worked on the repo at the same time, causing conflicting issues
- you can merge branches with a pr (pull request)
- simply create a new branch so the different code can be on separate branches, then merge w/pr

```
//create branch
git branch [branch name]

// go to branch
git checkout [branch name]
```

### How to push changes to a repo

This requires 3 steps 
- staging changes
- commit changes
- push changes

#### Staging changes

```
git add [filename]
//or to stage all changes
git add .
```

#### Commit changes (w/ message)

```
//a message would be like "worked on home screen" or "improved ui"
git commit -m "[insert message]"
```

#### Push changes
```
git push
```

### Pull changes from a repo

```
git pull
```

## Repo-Structure

Note: This is how I personally set up repo's and what I recommend just to stay organized.

### Base folder
![unknown](https://user-images.githubusercontent.com/63271391/149857387-ca935bf0-c5f0-4ca5-be31-b746f3dfcde9.png)

### src folder
![1](https://user-images.githubusercontent.com/63271391/149857400-c7148dc3-7bb2-4370-8ba6-34d81619466e.png)


## Basic-js

i hope this is somewhat accurate

how to print to console:

```
console.log("hello world");
```

Defining variables: 
- use let or const, dont use var
  - let allows the variable to be updated, const makes the variable constant

in react, you have to use useState otherwise variables wont update
you dont have to useState when variable is definied within the scope of a function however
you have to use useEffect if you want the function to be called either on the start of the loading of the page

Usage: 

```
import { useState, useEffect } from "react";

export default function File() {
  //define variables using useState, sets var to 1
  const [var, setVar] = useState(1);
  
  //useEffect to call the function on start of loading page, the [] can have for instance a variable inside, and if that variable changes then the useEffect function is called again but since its empty useEffect runs immediately on start of page
  useEffect(() => {
    console.log(var); // should print 1
    //setVar function increments var by 1
    setVar(var+1);
    console.log(var) //should print 2, however setState does not update asynchronously so it might not finish updating by the time you call console.log()
  }, []);
}
```


## react-native

Resources:
- [Mosh Video](https://youtu.be/0-S5a0eXPoc?t=2790)
- [React-native docs](https://reactnative.dev/docs/getting-started)
- [Expo docs](https://docs.expo.dev/)
- [UI Components](https://docs.expo.dev/guides/userinterface/)


## StyleSheet
- the CSS of react native
- all StyleSheet properties can be found [here](https://github.com/vhpoet/react-native-styling-cheat-sheet)

### Importing 

```
import { StyleSheet } from "react-native";
```

## Navigation
- [Docs](https://reactnavigation.org/)
- [Tab navigator](https://reactnavigation.org/docs/tab-based-navigation/)
- [Stack Navigator](https://reactnavigation.org/docs/stack-navigator/)

Note: For stack navigator, you have to install a ton of dependencies which is really annoying. run these in your cmd prompt in your project directory:
```
expo install react-native-gesture-handler react-native-reanimated react-native-screens react-native-safe-area-context @react-native-community/masked-view
```

## Context

A simple way to establish global variables that can be accessed by every file in your project.

In src/utils/context.js:

```
import { createContext } from "react";

const Context = createContext();

export default Context;
```

In App.js, make sure to wrap your entire code in the Context.Provider and import the proper components. Try to follow this code:

```
import Context from "./src/utils/context.js";

export default function App() {
  let var = 0;
  let variable = 0;
  
  return (
    <Context.Provider value={{
      //all the variables you want to be global
      var, variable
    }}>
      // THE REST OF YOUR APP
    </Context.provider>
  );
}
```

Then in a file where you want access to these files, import useContext and follow this code:

```
import { useContext } from "react";
import Context from "../utils/context.js";

export default function File() {
  let { var, variable } = useContext(Context);
}
```
