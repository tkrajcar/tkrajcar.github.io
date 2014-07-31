---
layout: post
title: "TIMBABWE Anew: Refresh and stack change"
categories: Ruby
excerpt: I initially launched this blog in May 2011, built on WordPress, with a fair amount of customization to a stock theme. At the time, I was looking for a simple, easy setup with a platform I was familiar with, and it more or less did the job. However, in the last few months, I've been wanting to make a change, even though I don't have that many posts or that much traffic.
---

I initially [launched this blog](/2011/05/welcome-to-timbabwe/) in May 2011, built on WordPress, with a fair amount of customization to a stock theme. At the time, I was looking for a simple, easy setup with a platform I was familiar with, and it more or less did the job.

However, in the last few months, I've been wanting to make a change, even though I don't have that many posts or that much traffic. Key reasons:

1. The never-ending WordPress comment spam had to go.
2. The never-ending parade of WordPress security and plugin updates had to go, too. I've got nothing against CMSes that need frequent updates, but the workload was way out of scale for my tiny little one-author blog.
3. I've been getting much deeper into the Ruby community, and wanted to have a Ruby-based blog.
4. While I was mostly satisfied with the look and feel of the old blog, there were quite a few bugs with the design, which was supposed to be [responsive](http://www.alistapart.com/articles/responsive-web-design/), and the amount of code detritus from the old theme meant that fixing them was unlikely, especially since it suffered from typical CMS "div soup".
5. For my simple little needs, depending on a whole PHP and MySQL stack is pretty silly. Working with static files makes a lot more sense and is a lot more portable. Also, with no database, now everything's in Git and [shared on Github](https://github.com/tkrajcar/timbabwe), meaning I have no need to do any other level of backups.

So, here's the new build, which you're reading this on. So far I've only put about 4-5 hours into it. Solves all of the above problems, and then some.

## Front-End

* For fonts and colors, I kept everything pretty much the same as I had designed in May; [Francois One](http://www.google.com/webfonts/specimen/Francois+One) for titles and [Droid Sans](http://www.google.com/webfonts/specimen/Droid+Sans) for body copy.
* For a HTML boilerplate, I used [Skeleton](http://getskeleton.com/), which provides a mobile-friendly, truly responsive grid system along with media queries. It seems to be working wonderfully; I had my pages looking just how I wanted (with no clutter or fluff) in just an hour or two - plus, no more weird resizing bugs like I had before. Score!

## Back-End

* <del>After doing a survey of what's out there, I settled on [Jekyll](https://github.com/mojombo/jekyll), a simple Ruby engine that reads in layout files in HTML and posts in Markdown, and outputs fully static files. This gives me all the power I need while remaining truly portable and maintenance-free.</del> <strong>EDIT:</strong> Since then I've changed over to using [Octopress](http://octopress.org/), a superset of Jekyll that adds quite a bit more functionality.
* I've chosen at the moment to deploy to [Heroku](http://www.heroku.com/) which gives me a cost- and hassle-free hosting solution, but again, since the site you're seeing is actually 100% static files, it's easy to put it somewhere else if needed.
* <del>Jekyll includes Pygments by default for code-highlighting, but it seemed a bit odd to me to use a Python library for code highlighting on a Ruby blog, plus it would remove my ability to use Heroku, so I integrated [CodeRay](http://coderay.rubychan.de/), a pure-Ruby syntax highlighter, into Jekyll instead with a custom plugin.</del> <strong>EDIT:</strong> OctoPress includes Pygments again after all.
* Comments are now being handled by [DISQUS](http://www.disqus.com/). No more spam!
* I continue to rely on [Clicky](http://getclicky.com/219995) for analytics; realtime, fast, very effective.

So far, I'm very pleased! Want to see the gory details? The [source is on Github](https://github.com/tkrajcar/timbabwe), so feel free to poke around!
