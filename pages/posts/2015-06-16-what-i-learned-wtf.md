---
date: 2015/06/16
description:
tag: web development
author: Me
title: What I Learned Yesterday - Pry wtf
---

_Every day at AcademicWorks, the Engineering Team has a Dev Sync where we share something we learned from the day before. Here is what I learned yesterday..._

## What I learned

This week, we've kicked off a new development cycle but we are also still QAing our newest release version. So in addition to jumping into some brand new features, I've been bug hunting and bashing.

:bug: :bug: :bug: :bug: :bug: :bug: :bug: :bug: :bug: :bug:

The essential tools for debugging in Javascript & Ruby are the `debugger` keyword for Chrome Dev Tools, and `<% binding.pry %>` for the Rails console. I've been learning a lot with these two tools but I wanted to focus on learning more about Pry. So I watched this conference talk from RailsConf2014.

<iframe width="560" height="315" src="https://www.youtube.com/embed/4hfMUP5iTq8" frameborder="0" allowfullscreen></iframe>

In addition to this great video (which really focuses on Pry as a feature building, general purpose tool, not just as a debugger), I stumbled across the `wtf?` command. Emblematic of a developer's sense of humor, the `wtf?` command will show you the stack trace of your last Exception Error. And the more `?` or `!` you throw at the end of the command, the more lines in your stack trace are shown.

```ruby
[1] pry(main)> called_this_method_without_defining_it_first
# NameError: undefined local variable or method `called_this_method_without_defining_it_first' for main:Object
# from (pry):1:in `<main>'
[2] pry(main)> wtf?
# Exception: NameError: undefined local variable or method `called_this_without_defining_it_first' for main:Object
# --
# 0: (pry):1:in `<main>'
# 1: /Users/jjackson/.rvm/gems/ruby-1.9.3-p125/gems/pry-0.9.9.3/lib/pry/# pry_instance.rb:249:in `eval'
# 2: /Users/jjackson/.rvm/gems/ruby-1.9.3-p125/gems/pry-0.9.9.3/lib/pry/pry_instance.rb:249:in `re'
# 3: /Users/jjackson/.rvm/gems/ruby-1.9.3-p125/gems/pry-0.9.9.3/lib/pry/pry_instance.rb:227:in `rep'
# etc..
```

## More resources

- [Pry 102: Advanced Features](http://jonathan-jackson.net/2012/05/03/pry-session-102)
