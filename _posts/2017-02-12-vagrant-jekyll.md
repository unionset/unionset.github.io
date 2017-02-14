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

NOTES:

- GitHub Pages only supports [kramdown](https://kramdown.gettalong.org/) as a Markdown processor([here](https://help.github.com/articles/updating-your-markdown-processor-to-kramdown/)).
- Now GitHub Pages uses not last kramdown version([here](https://pages.github.com/versions/)).
- If do not switch from jekyll to github-pages(like it's shown below) the content differs because of different kramdown version.

Steps
---

1. Install [Vagrant](https://www.vagrantup.com/downloads.html){:target="_blank"}.

1. Create Jekyll VM folder and download [vagrant-jekyll](https://github.com/jden123/vagrant-jekyll/){:target="_blank"}.

1. Start VM and connect.  
	```
	vagrant up
	```  
	```
	vagrant ssh
	```

1. Go to /projects folder.  
	```cd /projects/```  
	  
	vagrant-jekyll maps local machine folder(default: D:\Projects\GitHubPages) to VM folder(default: /projects). 
	It allows you to write a post on local machine using your favourite tools and build the content on VM. 

	*NOTE: the mapping can be changed using config.vm.synced_folder in vagrant file.*

1. Create a new site.   
	```
	jekyll new my-blog
	```
    
    Or go to created site folder.
1. Tweak Gemfile. 
    * Comment   
	``` 
	gem "jekyll", "3.3.1" 
	```
   
	* Uncomment   
	``` 
	#gem "github-pages", group: :jekyll_plugins 
	```

1. Remove ```Gemfile.lock```.

1. Call  
	```
	bundle install   
	```

1. Start the local server.  

	```
	bundle exec jekyll serve -H 0.0.0.0
	```

1. On local machine open a browser and go to ```localhost:4000```.  
Now you can see your blog.

1. To finish just press ctrl+c and then type exit.