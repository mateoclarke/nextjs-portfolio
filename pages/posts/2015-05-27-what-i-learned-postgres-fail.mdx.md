---
date: 2015/05/27
description:
tag: web development
author: Me
title: What I Learned Yesterday - Postgres Fails
---

_Every day at AcademicWorks, the Engineering Team has a Dev Sync where we share something we learned from the day before. Often times we'll hear about some new movie, a cool Kickstarter project, or an interesting ruby gem. Our VP of Engineering has issued a challenge to our team. Whoever can teach something they learned from the day before that is technical in nature and directly related to our work for 20 consecutive days will win a prize. Here is what I learned yesterday..._

# PostgreSQL Fails, now what?

I was having issues starting up my environment. Our Rails scholarship app depends on a separate indexer app that runs a bunch of tasks with [foreman](http://theforeman.org/).

After digging in a bit and with much guidance from my primary mentor on the team, all signs pointed to my Postgres server having died.

## What I learned

- `$ ps aux | grep postgres` checks to see what programs are running postgres. If you don't get anything back, that points to your postgres server being MIA.
- The Unix `tail` command gets you the last 10 lines of a file. If you run this command on your server log, it can give you better details about what process failed and why.
  - EX: `$ tail -n 50 /usr/local/var/postgres/server.log`
- Postmaster (`postmaster.pid`) is postegres' process- id file. If you already have a `postmaster.pid` file in your postgres folder, you might have issues.
  - To delete the redundant file: `rm -rf /usr/local/var/postgres/postmaster.pid`
- Now my `foreman start` works and I can start coding on the Rails app. Enough with the [yak shaving](http://en.wiktionary.org/wiki/yak_shaving).

![Yak loop](http://media.giphy.com/media/11KL2DW3ddivK/giphy.gif)

## _Update (07-14-2015)_

I found [this discussion thread](https://www.ruby-forum.com/topic/1735505#1035801) that helped me find and kill a zombie server.

Once you're seeing an error like `A server is already running` or `Address already in use`, you probably have a **zombie server** you were unaware of.

First:
`lsof -i :3000` (given that the zombie server is running on port 3000)

This tells you the PID (process id) of the server you need to kill. And it prints out something like:

    COMMAND   PID    USER   FD   TYPE SIZE/OFF NODE NAME
    ruby    15744   mateo   21u  IPv4      0t0  TCP *:hbci (LISTEN)

and then copy that `<PID>` number (in my case 15744) and check if it is actually running something:
`ps ax | grep <PID>`

Finally, to kill a zombie:
`kill -QUIT <PID>`
