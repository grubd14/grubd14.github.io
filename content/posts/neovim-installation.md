---
title: "Installing neovim in Ubuntu based distros"
date: 2021-9-26
# weight: 1
# aliases: ["/first"]
categories: ["neovim"]
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
howCodeCopyButtons: true
disableSpecial1stPost: false
disableScrollToTop: false
ShowShareButtons: true
cover:
  image: "/cover-images/cover-neovim.png#center" 
  alt: "<alt text>" # alt text
  caption: "neovim" # display caption under cover
  relative: false 
  hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/grubd14/grubd14.github.io/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
![neovim](/images/neovim.png#center)

# Neovim 
Neovim is a great piece of software if you are looking for an alternative to vim. Neovim is a fork of Vim with more features as well as bugs. But neovim community is very active so must of the bugs are fixed quickly. Neovim is in eary stages. Stable version 0.5.1 was relased recently which brings great features like native LSP and support for lua scripting language. Neovim has transitioned away from vimscript which is quite slow compared to lua. The community has already made great plugins based on lua for neovim.

# Ways of Installation 
## adding the PPA
There are several ways of installing [neovim](https://github.com/neovim/neovim) in Ubuntu and Ubuntu based distros  but the most easiest way is to add 
PPA from the neovim team. To add the PPA copy the following code and paste into the terminal
```
sudo add-apt-repository ppa:neovim-ppa/stable

sudo apt update
 ```
 
 To install neovim Enter the following code:
 ``` 
 sudo apt install neovim
 ```
 To check the neovim verson 
 ```
 nvim -v 
 ```
 
 ## using the appimage version
 Neovim team also provides appimage version of daily and stable builds which can be used in every linux distros. To use the appimage version from the terminal you can add the appimage binary in local bin directory.

1. First download the appimage version from the release page of [neovim](https://github.com/neovim/neovim/releases/).
2. Make the appimage executable from the terminal by going to the directory in which it is downloaded
```
chmod +x neovim.appimage
```
3. Move the appimage to the local bin.
*Note:You can also move appimage binary to root bin directory by executing with it sudo privelages*
```
mv neovim.appimage /home/computer/.local/bin
```
4. After moving neovim to local bin directory you can rename the neovim appimage to just *nvim* for convenience to launch through terminal.
5. Now just type nvim and press enter into terminal.
