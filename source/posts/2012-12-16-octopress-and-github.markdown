---
layout: post
title: "Octopress and GitHub"
date: 2012-12-16 19:09
comments: true
categories: Octopress
---
Finally i managed to deploy Octopress on <a href="http://pages.github.com">GitHub (pages)</a> with custom theme. I added facebook profile link that wasn't provided by Octopress. Octopress is really easy,simple and beautiful.But I faced some problems while setting up Octopress.</br>So i thought of writing the first blog on "Deploying Octopress on GitHub".
<!--more-->

I assumed you have installed RVM and Ruby on your machine.
</br>My environment: ``RVM 1.17.3, Ruby 1.9.3p327, Ubuntu 11.10``

<h4>Installing Octopress</h4>

```bash prepare workspace
akash@desktop:$ mkdir github_pages #create your project directory
akash@desktop:$ cd github_pages
akash@desktop:$ git clone https://github.com/imathis/octopress.git octopress #clone octopress repo into octopress directory
akash@desktop:$ bundle install # more about bundler http://gembundler.com/
```

Now install Octopress
```bash install Octopress
akash@desktop:$ rake install 
```
This command install Octopress default theme. You can install third party themes for octopress. <a href="https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes">List of third party themes</a>

<h4>Deploying to GitHub</h4>
You must have a github repository with strict naming convention as ``username.github.com``.
After creating repository on GitHub, its time to configure rake for deploying blog. 
```bash rake setup
akash@desktop:$ rake setup_github_pages
```
This will ask you for github repository details. You have to follow the convention as

``git@github.com:username/username.github.com``
Note: do not add ".git" at the end.

```bash Check for remote repository
git remote -v 

#This was my output.
origin	git@github.com:akash0x53/akash0x53.github.com (fetch)
origin	git@github.com:akash0x53/akash0x53.github.com (push)

#If your output is
octopress   git://github.com/imathis/octopress.git (fetch)
octopress   git://github.com/imathis/octopress.git (push)

#then you need to add your repo using
akash@desktop:$ git add remote add origin git@github.com:username/username.github.com.git
```
To delete Octopress branch using
```bash Deleting remote branch
akash@desktop:$ git remote rm Octopress
```
To publish pages on GitHub rename your branch to ``source`` branch
```bash rename branch
akash@desktop:$ git branch 
		* master
akash@desktop:$ git branch -m master source
akash@desktop:$ git branch
		* source
```

Now setup is complete. You can preview your blog using

		akash@desktop:$ rake preview
This command creates temporary server, listening on port 4000, goto browser and type <a href="localhost:4000">localhost:4000</a>.
If you are satisfied with your work then do not wait to publish.

```bash First push to GitHub
akash@desktop:$ rake generate
akash@desktop:$ git add .
akash@desktop:$ git commit -m "some message"
akash@desktop:$ git push origin source
akash@desktop:$ rake deploy
```
Wait for email from GitHub; as its your first push.

Congratulations you have successfully deployed your blog on GitHub.












