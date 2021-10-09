---
title: "Installing Global Packages in NPM without using SUDO privelages"
date: 2021-10-09
# weight: 2
# aliases: ["/first"]
categories: ["npm"]
author: "Sushil"
showToc: true
TocOpen: false 
draft: false
hidemeta: false
comments: false
description: "neovim for ubuntu"
canonicalURL: "https://canonical.url/to/page"
disableHLJS: false
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowCodeCopyButtons: true
disableSpecial1stPost: false
disableScrollToTop: false

cover:
  image: "/cover-images/cover-npm.png"
  alt: "<alt text>" # alt text
  caption: "npm" # display caption under cover
  relative: false 
  hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/grubd14/grubd14.github.io/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
![npm](/images/node.png#center)
# NPM
NPM is the default package manager for Node.js, a JavaScript runtime environment. Node.js comes packaged with npm which is mostly used for downloading packages from the [npmjs](https://www.npmjs.com/) repository consisting of opensource packages. There are many more alternatives to npm which provide different client side experience. Yarn is one of the popular alternative to npm which is developed by facebook.

## problem
NPM always had its fare share of problems whether it was related to package, package dependencies and many more problems. The problem here we are talking is about the npm requiring SUDO privelages to download package in linux. By default npm downloads global packages in root directory which requires entering sudo command every time when download global packages.

## fixing the problem
The given fix is for linux.

1. First create a directory for installing global packages in home directory of your machine. You can give any name to the directory.
```
mkdir ~/.npm-global-packages
```
2. Now configure npm to download global package to the directory you created. In terminal enter the following command:
```
npm config set prefix '~/.npm-global-packages'
```
3. Open or create a ``` ~/.profile ``` file in the home directory and add the following code to make the bin path visible to the system. So that installed packages can be easily run from terminal.
```
export PATH=~/.npm-global-packages/bin:$PATH
```
4. On the command line, update your system variables:
```
source ~/.profile
```
5. Now to test the configuration try installing packages with -g command
```
npm install -g eslint
```

