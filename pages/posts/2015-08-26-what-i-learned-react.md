---
date: 2015/08/26
description:
tag: web development
author: Me
title: What I Learned Yesterday - React vs. jQuery
---

_Every day at AcademicWorks, the Engineering Team has a Dev Sync where we share something we learned from the day before. Here is what I learned yesterday..._

## Did you say React?!

You'll hear comparisons between Knockout vs. Backbone or Angular vs. Ember. There's a javascript framework war going on out there. Now, the newest title contender in the hearts and minds of yavascripters is REACT.

![javascript battle royale]({{ site.baseurl }}public/images/js-war.gif)

It's fun to watch, but I've been hesitant to jump into this battle and pick a side. Frankly, this is because I'm still learning so much about basic javascript patterns. And I'm able to use jQuery to manipulate the DOM and modify my UI. And when I really need it, I've enjoyed learning and using helper libraries like [Underscore](http://underscorejs.org/) or [Leaflet](http://leafletjs.com/) to achieve the baseline goals for a given project.

But what if the battle isn't between _New Thing_ vs. _Other New Thing_? What if the battle is over the fundamental way we interact with the DOM?

I just completed Shu Uesugi's (aka [@chibicode](https://twitter.com/chibicode)) [React.js Introduction For People Who Know Just Enough jQuery To Get By](http://reactfordesigners.com/labs/reactjs-introduction-for-people-who-know-just-enough-jquery-to-get-by/) and this paradigm shift became more clear for me.

## What I Learned

The tutorial compares the tried and true jQuery model of interacting with the DOM through selectors and event handlers (like `$(".item").on("click", doSomething())`) to the new paradigm of how React can make the same changes to the UI by rendering a fresh HTML component anytime state is changed.

This is the important takeaway:

> In jQuery, you write event handlers which modify the DOM.
> In React.js, you write event handlers which modify the state. And you write render() to reflect the current state.

![]({{ site.baseurl }}public/images/jquery-style-vs-react-style.png)

## More resources

- [Facebook: Official React Tutorial](https://facebook.github.io/react/docs/tutorial.html)
- [Egghead: Build Your First React.js App](https://egghead.io/series/build-your-first-react-js-application)
