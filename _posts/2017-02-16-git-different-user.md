---
layout: post
title:  "Using different Git users for different repositories"
date:   2017-02-12
categories: git
---
I need to use two different Git users: one is for my private tasks and another is for my customer projects. I set up my own user as a global and have to switch the user when I'm working on customer projects. Unfortunately, often I forgot to do it and make commits under a wrong user that causes the issues and additional work. I looked for a solution and I've found a good article([link](https://orrsella.com/2013/08/10/git-using-different-user-emails-for-different-repositories/){:target="_blank"}).

From Git 2.8 you can use per-repo user by running the following commands:

```
rem Require setting user.name and email per-repo:
git config --global user.useConfigOnly true

rem Remove email address from global config:
git config --global --unset-all user.email
```

To set up a user use the following:

```
git config --global user.name "John Doe"
git config --global user.email john.doe@address.com
```

I created bat file for each user and put these files to PATH enviroment variable. When I clone a new repo I have to setup a user by calling one of the bat files. If I forget and commit something Git prevents me committing. Then I call necessary bat file and commit again. It works! :)