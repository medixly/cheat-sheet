# Ultimate Cheat Sheet

## Table of Contents
- [Setup](#Setup)
- [Git](#Git)

## Setup

Install Node.js [here](https://nodejs.org/en/).

How to install Expo: open terminal or command prompt

```
//for windows
npm i -g expo-cli

//for mac
sudo npm i -g expo-cli
```

Install Expo Go on your mobile device:
- [App Store](https://apps.apple.com/us/app/expo-go/id982107779)
- [Google Play](https://play.google.com/store/apps/details?id=host.exp.exponent&hl=en_US&gl=US)

Install (if you already heaven't) the code editor of your choice, I recommend [VS code](https://code.visualstudio.com/)

How to start new Expo Project:
- Open terminal/cmd prompt and go to directory of your choice
```
expo init [insert project name here]
```

How to start your project:
- in your project directory
```
expo start 

//or

npm start
```
- Then in metro bundler, scan the qr code with your phone


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
