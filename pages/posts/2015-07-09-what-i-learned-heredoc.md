---
date: 2015/07/09
description:
tag: web development
author: Me
title: What I Learned Yesterday - Heredoc
---

_Every day at AcademicWorks, the Engineering Team has a Dev Sync where we share something we learned from the day before. Here is what I learned yesterday..._

## What I learned

A **heredoc** (or [Here document](https://en.wikipedia.org/wiki/Here_document)) is a way to declare a file or a long string inline. One of the advantages to saving a string in a heredoc is that you preserve line breaks, indentation and other white spaces. It also ignores quotations, so if you had a string with quotes in it, they don't have to be escaped.

This is confusing to read:

```ruby
"<pre>\n  <code>puts \"foobar\"</code>\n<pre>"
```

But this is equivalent and it reads much better.

```ruby
<<-EOS
<pre>
  <code>puts "foobar"</code>
</pre>
EOS
```

_EOS here stands for "end of string". It's a common convention to use "EOS" with heredocs, but it doesn't really matter. Any string after `<<-` is how you are telling the heredoc what to look for and when to terminate itself. Once it encounters "EOS" the second time, the heredoc knows it's reached the... end of the string._

In our code base, I encountered this use of a heredoc in our code. We are using a method like `html_code` as a helper method. It's a much prettier way to inject a string of `HTML` while preserving the code indentation we are familiar.

```ruby
def html_code
  html_code = <<-HTML
    <div class="textile-meta">
      <div class="example">
        <span>Example Formatting: <strong>*bold*</strong>, <em>_italics_</em></span>
      </div>
    </div>
  HTML

  html_code.html_safe
end
```

## More resources

- [Wikipedia](https://en.wikipedia.org/wiki/Here_document)
- [Strip Leading Whitespace from Heredocs in Ruby](http://anti-pattern.com/strip-leading-whitespace-from-heredocs-in-ruby)
- [Using heredoc for prettier Ruby code](http://makandracards.com/makandra/1675-using-heredoc-for-prettier-ruby-code)
- [Heredoc and Indent](http://rubyquicktips.com/post/4438542511/heredoc-and-indent)
- [Ruby's here document mini tutorial](http://log.gmarik.info/2007/12/rubys-here-document-heredoc-mini.html)
