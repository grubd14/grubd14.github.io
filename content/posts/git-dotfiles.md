---
title: "Managing a barebone git directory of dotfiles"
date: 2023-5-5
# weight: 2
# aliases: ["/first"]
categories: ["git"]
author: "Sushil"
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "managing dotfiles in linux"
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


editPost:
    URL: "https://github.com/grubd14/grubd14.github.io/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
![dotfiles](/images/dot.png#center)
# dotfiles
There are thousands other ways to manage your dotfiles efficiently. While there are countless opensource programs and scripts to maintain your dotfiles, I find them very difficult to use. My method of managing dotfiles may not scale very well but it is easier to manage.

# steps
If you have been using your linux machine for a quite a time than you may know there are various dotfiles created by several programs in your home directory which are necessory to run programs. This dot files are mostly configuration files for your programs.

1. First of all create a an exact replica of your home directory in a folder of your choice. I created a folder in `Documents` and named it dotfiles.
```
mkdir ~/Documents/dotfiles
```
2. Now copy all the important necessary dotfiles to the the folder you created. Don't miss any dotfiles because we are going to delete them later. Also avoid copying folders with programs binary. You can do so but it is not advised.

3. Now delete the actual original files and folders that you copied from your home directory.

4. Now, this is an important step, since we are going to symlink are files from the dotfiles folder to the home directory where previously the dotfiles resided.

5. Symlink also called symbolic link is easy to do in linux.Now here is how to do it.
```
ln -s /home/<root-name>/Documents/dotfiles/<file-you-want-symlink> ~/<place where the actual file resides>
```
The given command may not explain very well. So I am providing an example.
```
ln -s /home/<root>/Documents/dotfiles/.zshrc ~/.zshrc
```
- for folders
```
ln -s /home/<root>?Documents/dotfiles/kitty ~/.config/kitty
```
You can also create a text files with similar commands for other files and folder.

# backup
People like me distro-hop frequently. So, it is better to initiate a git repository and backup to services of your choice like github, gitlab etc.





