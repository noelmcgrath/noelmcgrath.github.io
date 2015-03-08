---
layout: post
title:  "Setting up my blog"
date:   2015-03-07 15:31:10

---
I used a vagrant box, so I can install whatever software is required. Create a Vagrantfile and add the following

```bash
Vagrant.configure("2") do |config|
	config.vm.box = "noel2"
	config.vm.box_url = "https://github.com/jose-lpa/packer-ubuntu_14.04/releases/download/v2.0/ubuntu-14.04.box"

	config.vm.synced_folder "./", "/vagrant", create: true

	config.vm.network "forwarded_port", guest: 4000, host: 4000 
end

```

vagrant up to bring box up

## SSH onto vagrant box
vagrant ssh

Needed to update ruby version on box

```bash
# See http://jekyllrb.com/docs/troubleshooting/#installation-problems
sudo apt-get install ruby1.9.1-dev

```

Then follow steps outlined [here][jekyllwithpages]


This failed as no javascript on machine and I had to install node.js first

```bash
sudo apt-get install node.js

```


## using jekyll
To get started, do the following

```bash
$ jekyll new myblog
$ cd myblog
$ jekyll serve
# => Now browse to http://localhost:4000

```

## Create a post
- Create a file in the _posts directory, and off you go

## Links
- [GitHub Pages](https://pages.github.com/)
- [jekyll](http://jekyllrb.com)
- [Markdown-Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
- [markdown](http://daringfireball.net/projects/markdown)
- [How I built my blog in one day](http://erjjones.github.io/blog/How-I-built-my-blog-in-one-day/)
- [build blog jekyll github pages](http://www.smashingmagazine.com/2014/08/01/build-blog-jekyll-github-pages/)


[jekyllwithpages]:      https://help.github.com/articles/using-jekyll-with-pages/