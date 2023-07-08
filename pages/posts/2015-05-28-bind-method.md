---
date: 2015/05/28
description:
tag: web development
author: Me
title: '_.bind method'
---

_Every day at AcademicWorks, the Engineering Team has a Dev Sync where we share something we learned from the day before. Often times we'll hear about some new movie, a cool Kickstarter project, or an interesting ruby gem._

## What I learned

As I mentioned earlier [this week](insert_link), the keyword `this` in Javascript is confusing.

If we aren't careful, the context for any function we run can be different from what we expect. The keyword `this` can refer to the object that is calling the function. But sometimes we want `this` to be explicitly bound or set always to same object.

Here at AW, we use [underscore](http://underscorejs.org/#bind)'s `_.bind` method. One specific example is how we use bind within a jQuery event listener to explicitly bind our function to the instance of a module that was instantiated with a constructor function.

```javascript
this.$el.on(
  'click',
  '.js-target-container',
  _.bind(this.toggleActionButton, this)
)
```

## More resources

- [Underscore bind docs](http://underscorejs.org/#bind)
- [Youtube: Javascript Context Tutorial - What makes Javascript Weird...and Awesome Pt5](https://www.youtube.com/watch?v=fjJoX9F_F5g)
- [JavaScript’s Apply, Call, and Bind Methods are Essential for JavaScript Professionals](http://javascriptissexy.com/javascript-apply-call-and-bind-methods-are-essential-for-javascript-professionals/)
