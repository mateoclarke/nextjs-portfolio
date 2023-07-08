---
date: 2015/06/25
description:
tag: web development
author: Me
title: Browser Rendering
---

_Every day at AcademicWorks, the Engineering Team has a Dev Sync where we share something we learned from the day before. Here is what I learned yesterday..._

## What I learned

Today I found a nice [Youtube](https://www.youtube.com/watch?v=n1cKlKM3jYI) walk-through on **Browser Rendering**. It revolves around this diagram:

![](/public/images/browser-rendering.png)

The simplified explanation of the browser rending process goes like this:

You start with your **HTML & CSS files**. Your browser then parses these files into the **DOM** (Document Object Model) & the **CSSOM** (Cascading Stylesheets Object Model). These are internal tree representation models for the browser. It's like the browser's map. These models are made up of nodes with parent/ sibling/ancestor type relationships. Each node represents an HTML element or CSS rule.

The **Render Tree** is a combination of the DOM & CSSOM tree models but it only contains the elements and rules that will need to be painted or displayed on the page. So HTML elements like `<head>`, `<link>`, and `<meta>` are left out.

Then each node in the Render Tree will go through the **Layout** process. The browser will decide where each node on the page will be painted. This is the browser's geometric calculation process. Continuing with the mapping analogy, this is like when the surveying team goes out into the field.

Finally, based on the calculations in the Layout process, every node from the Render Tree is **Painted** onto the screen.

Chrome Canary has features in the Timeline panel that allow you to see each paint event the browser fires to load all you're elements from the render tree.

![](/public/images/chrome-canary.png)

It's important to understand how an app's pages are being loaded by the browser because this is the key to understanding a site's front-end performance...

## More resources

[Youtube: An Introduction to Browser Rendering](https://www.youtube.com/watch?v=n1cKlKM3jYI)
[Profiling Long Paint Times with DevTools' Continuous Painting Mode](https://developers.google.com/web/updates/2013/02/Profiling-Long-Paint-Times-with-DevTools-Continuous-Painting-Mode?hl=en)
[Youtube: Paul Irish, "Delivering the goods" - Fluent 2014 Keynote](https://www.youtube.com/watch?v=R8W_6xWphtw)
