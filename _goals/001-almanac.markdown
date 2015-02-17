---
layout: post
title:  "001 - Almanac & Foundation"
date:   2015-01-31
site_url:   "http://www.almanacnyc.com"
img: '/uploads/foundation.jpg'
categories: goals
project_type: goals
summary: "In January I used Zurb's Foundation for the first time in a client project."
display: active
cta: Visit Project
---
While buildling Almanac, I decided to try out Zurb's Foundation framework. I figured since it was a Framework I'd have very little ramp-up and would be able to figure out any nuances from their documentation and stackoverflow.

I was interested to play with Foundation since I've only messed with Bootstrap out of client necessity so I figured this would be a great chance to learn a new framework to better way my options.

Since I use Grunt in my workflow I knew I could just integrate Foundation into my process pretty easily. But then realized since this site was built on Wordpress, it might get a little tricky. Luckily the world of open-sourced projects came to save the day and I was able to use FoundationPress which did exactly what I needed. 

Aside from FoundationPress' few opinions the framework integrated into the project seamlessly. I noticed however that Foundation has a few caveats of its own. Things like floating the last item in a row to the right and what not had to be overridden but nothing within Foundation ever really held up my process. 

FoundationPress, however, did have a few hiccups along the way. The size of the project itself was enormous. For the first time in my development career I hit IE's 4095 selector limits. Upon further inspection *all* of Foundation was being included in this project and I'd need to cut stuff down to only the necessities in order to work in IE9. 

Other than the one small hiccup of IE's selector rule everything went pretty smoothly. I happen to like the difference in naming (or opinion) that Foundation carries when it comes to rows[^1]. Not sure I have a clear winner in the framework game but this gave me a good opportunity to try something new while still being productive. 

<a class="btn btn-project" href="{{page.site_url}}" target="_blank">{{page.cta}}</a>

[^1]: As opposed to Bootstrap's style having a parent container on rows.