---
layout: post
title:  "reValuate"
date:   2021-04-18
excerpt: "Get rewarded for throwing out trash the right way"
feature: https://yamozha.xyz/assets/img/posts/revaluate_banner.png
project: true
tag:
- reValuate
- nature
- recycling
- project
- blog

comments: true
---

## Backstory
The story behind reValuate is quite short, as it is a school project. Weirdly enough it's not for a subject from the IT kinds, but rather Economics. In class, we had this goal in mind - make the students(and teachers) in our school start throwing their trash out in the right recycling bin. I got assigned to make a website about the whole ordeal. Initially the idea about the website was it to be just a short introduction to the project but it accidentally became **the** project.

## Non-technical explanation of the website

The process of the website is:  

`The user uploads an image/video --> It gets validated by an administrator --> They get reCoins(insite credits) --> They spend them in the school, where the cashier takes their points, in order to give them a reward equal to them.`  

Simple enough!  

The website is pretty simple for the user too - you log in/register and you have two options: 1. Upload an image or video 2. Check your balance.  

As for the administrator and cashier, a little bit more complicated. I suggest clicking on [this link](https://www.youtube.com/channel/UCIWblGtjXAxwbTMUbhZ_PDQ), if you speak Bulgarian and you're interested in an in-depth tutorial.  

Long story short, the administrator has an extra menu, in which he clicks a button according to whether or not the piece of media is valid, and the cashier enters in the user's identification number and the number of reCoins needed to make the purchase.

## Technical explanation of the website
On the technical side of things, the website is quite simple as well(but it took way too much time!), it's just a django backend website, which just handles the media and the users(as well as other minor details like the reCoins). I made a RESTful API as well, in hopes of making a mobile application with the same backend as the website, but that is still very heavily W.I.P. 

## Closing
Well, this article turned out way shorter than I expected, but I'm still content with it. As for the project, judging from the fact that we still haven't officially released it, I can't give you any statistics or anything like that, but I am pretty hyped about doing it in the future, so expect another article about this(in 2022, if our work continues being this humorously slow)