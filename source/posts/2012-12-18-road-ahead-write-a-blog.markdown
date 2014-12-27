---
layout: post
title: "Basics of OctoBlog"
date: 2012-12-18 14:47
comments: true
categories: Octopress
---

Okay... So its time to create a new blog using Octopress. After a lot of hardwork on deploying Octopress you could not stop yourself to write. So time to learn Octopress features. 
<!--more-->

first of all, create a new post using
```bash new post
akash@desktop:$ rake new_post["post_name"]
```
This will create a directory ``source/_post/`` and a markdown file naming as
``YY-MM-DD-blog_name.markdown`` in "_post" directory. Reason for this convention is "permalink". It helps to create <a href="http://en.wikipedia.org/wiki/Permalink">permalink.</a> This syntax is human-readable and gives you idea of when was the particular post written & name of the post.

Open newly created markdown file using any editor like VI,emacs,gedit as your wish. You will find properties of post as
		---
		layout: post
		title: "Basics of OctoBlog"
		date: 2012-12-18 14:47
		comments: true
		categories: Octopress
		---
This is YAML front matter. As per jekyll, any file with YAML front matter will be processed as jekyll special file. Above texts are of this post. ``layout, title, date, comments, categories`` these are special variables.</br>

``layout: post`` specifies to use layout file ``post.html`` which reside in directory ``source/_layout``</br>
"categories" variable defined the category of your post. You can have multiple categories in your blog like Networking,Programming,Social. If your post belong to "Social" category then simply set categories to Social. Posts belongs to same category will be grouped.</br>

From the next line to - - - you can start writing your blog.

Commonly used markups while decorating blog<br>
1. Excerpts: On your home page you wants to show only some content of post and then link to full post. You might have seen "Read more", "Continue", etc. links on blogs. These are Excerpts. It is simple in Octopress. Just add ``<!--more-->`` ( "more" enclosed in html comment).</br>
2. ``<a href="some link"> Text to display </a>`` HTML Anchor tag. No need to explain</br>
3. to write in a box as above ( i dont know what is the term for it ), enclose text within 2 backticks as</br>
\`\` your text \`\`</br>
4. to include source code in your post
   	```[lang name] [title of source code]
	...your code
	...
	...	
	```(again ends with 3 backticks)



