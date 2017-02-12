---
layout: post
title:  "Running GitHub pages blog on Windows"
date:   2017-02-12
categories: githubpages jekyll vagrant
---
[GitHub Pages](https://pages.github.com/){:target="_blank"} is a static site hosting service that supports Jekyll, a popular static site generator. it's a perfect way to get your own blog for free.  

Jekyll allows you to create new posts using [markdown syntax](https://guides.github.com/features/mastering-markdown/){:target="_blank"}. The HTML is generated automatically. 
It's based on Ruby and you have to install it to start working. 
If you do not want you can use [vagrant-jekyll](https://github.com/jden123/vagrant-jekyll/){:target="_blank"} that includes all you need to build a blog using Jekyll.

Steps
---
1. Install [Vagrant](https://www.vagrantup.com/downloads.html){:target="_blank"}.
2. Create Jekyll VM folder and download [vagrant-jekyll](https://github.com/jden123/vagrant-jekyll/){:target="_blank"}.
3. Start VM and connect.
	```
	vagrant up
	vagrant ssh
	```
4. Go to /projects folder.
	```
	cd /projects/
	```
    
    vagrant-jekyll maps local machine folder(default: D:\Projects\GitHubPages) to VM folder(default: /projects). 
    It allows you to write a post on local machine using your favourite tools and build the content on VM. 
    
    *NOTE: the mapping can be changed using config.vm.synced_folder in vagrant file.*
5. Create a new site. 
	```
	jekyll new my-blog
	```
    Or go to created site folder.
6. Start the local server.
	```
	 jekyll serve -H 0.0.0.0
	```
7. On local machine open a browser and go to 
	```
	localhost:4000
	```
    Now you can see your blog.
8. To finish just press ctrl+c and then type exit.