---
layout: post
title:  "Introducing MatchMaker"
date:   2018-07-24
permalink: /writing/introducing-match-maker
crosspost_to_medium: true
---

# MatchMaker

Over the last six months I’ve noticed a pattern arise in how I build UI components: the need to enable or disable JavaScript and their accompanying UI components based on viewport size, usually aligned with predefined breakpoints.  The problem lead to a fun little solution:

[MatchMaker - A really small library to make working with matchMedia a little easier](https://www.npmjs.com/package/mq-match-maker).

At first, I went the lazy route: changing the display property in CSS based on a media query. But overtime I realized a lot of unnecessary JavaScript was running behind the scenes.

Then I moved onto another approach: use the matchMedia API to initialize a new `MediaQueryList` object to check if the browser matches the requested media query. This approach felt way better. The JavaScript was deferred or executed by code rather than just hiding the elements using with CSS. The logic was in one place and was easier to see what was happening and why.

This approach has noticeable downsides. In each JS module I’d have to do the following:

1. Create a new instance of matchMedia with the media query string passed as an argument. 
2. Possibly check and run some JS based on the matchMedia.matches value on load. 
3. Create the event listener
4. Run the function(s) again (or more functions) when the event listener fires

### MatchMaker’s Purpose

MatchMaker’s purpose is to allow anyone to use the matchMedia API without having to declare a bunch of nonsense, pass in callbacks to match certain queries, fire at relevant moments based on the matchMedia response, and optionally execute (or not) based on the initially executed return value from matchMedia.

The API looks like this:

    matchMaker.register(<MEDIA QUERY STRING>, <NAMED CALLBACK>, <DEFER RUNNING ON LOAD>);

    matchMaker.deregister(<MEDIA QUERY STRING>, <NAMED CALLBACK>);

In actual implementation it may look something like this if you wanted to prevent the function from running immediately: 

    matchMaker.register('(min-width: 600px)', this.updateAspectRatio, false);

Or if you wanted the callback to fire immediately and each time it matches the `mediaQuery`
    matchMaker.register('(min-width: 600px)', this.updateAspectRatio)

An example of degregistering a named callback

    matchMaker.deregister('(min-width: 600px)', this.updateAspectRatio)

### Why is this useful?

At first I didn’t know if this would be useful to others. It may not be the next Lodash but a few scenarios come to mind that may be helpful for engineers:

1. [You want to initialize a UI component JS above a viewport width](https://codepen.io/pbj/pen/ejvaaZ)
2. [Enable or disable click events based on viewport width](https://codepen.io/pbj/pen/zLwqPG)
3. [Reset state based on viewport width](https://codepen.io/pbj/pen/ZjKZWa)

Download the library here: [https://www.npmjs.com/package/mq-match-maker](https://www.npmjs.com/package/mq-match-maker)
