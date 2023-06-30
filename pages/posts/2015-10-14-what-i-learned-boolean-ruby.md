---
date: 2015/10/14
description:
tag: web development
author: Me
title: What I Learned Yesterday - Booleans have no natural ordering in Ruby
---

_Every day at AcademicWorks, the Engineering Team has a Dev Sync where we share something we learned from the day before. Here is what I learned yesterday..._

## So I wanted to sort stuff in Ruby

Say I have a list of books that a user likes and I want these books listed out in a table. But we also happen to know which of these books is the user's absolute favorite book. That book should be displayed at the top of the list! And fortunately, we have a helper method already defined, `#favorite?`, which returns `true` if the book in question is the user's favorite.

Easy, let's sort our list of books using `book.favorite?`:

```ruby
books.sort_by { |book| book.favorite? }
```

But this returns an error: `ArgumentError: comparison of TrueClass with false failed`

## What I Learned

> In Ruby, Boolean values have no natural ordering.

So, it turns out that I was wrong to assume that Ruby knows how to sort booleans. In the language C, false has a smaller value that true. But, the designer(s) of the Ruby language probably thought any ordering for booleans would be confusing for developers so it is intentionally left out of the comparison operators<sup><a href="http://stackoverflow.com/questions/14816131/why-doesnt-sort-or-the-spaceship-flying-saucer-operator-work-on-boolean">1</a></sup>.

But fortunately, there is a simple trick too allow us to sort by boolean values:

```ruby
books.sort_by { |book| book.favorite? ? 0 : 1 }
```

All we do here is covert the true and false values to equivalent Number values which we can sort.

## More resources

- [Stackoverflow: sort_by with Boolean in Rails](http://stackoverflow.com/questions/8737111/sort-by-with-boolean-in-rails)
- <a name="link1">][Stackoverflow: Why doesn't sort or the spaceship (flying saucer) operator (<=>) work on booleans in Ruby?](http://stackoverflow.com/questions/14816131/why-doesnt-sort-or-the-spaceship-flying-saucer-operator-work-on-boolean)</a>
- [Mark Needham: Sorting by boolean fields](http://www.markhneedham.com/blog/2011/01/08/ruby-sorting-by-boolean-fields/)
