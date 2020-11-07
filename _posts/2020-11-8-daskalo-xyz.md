---
layout: post
title:  "daskalo.xyz"
date:   2016-04-06
excerpt: "My idea for easier online classes"
project: true
tag:
- jekyll 
- moon
- blog
- about
- theme
comments: true
---

## My idea
One day while I was getting up to log in to the daily online classes we had last schoolyear during the pandemic, I spent around 15 minutes searching mindlessly for the Zoom links we needed to go to.  
I was wondering whether I could provide a solution to that. And then I thought about a website, that had all the links inside of it.  
And my first prototype was this:  
![the old rendition](/assets/img/posts/daskalo_old.png)

After this prototype I went into thinking - *damn, this is way too hard to use - I need to make it automatic!*  
So I decided to make a php script that decides(based on the grade you select) which class you have right now, and it automatically sent you to that zoom call!  

aaaaand it looked like *this*:
![the newer rendition](/assets/img/posts/daskalo_auto_old.png)

And obviously(after a lot of comments about how it looked), one night, I decided to make the website look better.  
So this is the final product:
![the newest rendition](/assets/img/posts/daskalo_new.png)

you can check out the code [over here]("https://github.com/yamozha/daskalo-xyz")  
but I believe only the [PHP script]("https://github.com/yamozha/daskalo-xyz/blob/main/programs/10a/program.php") is worth looking at.
