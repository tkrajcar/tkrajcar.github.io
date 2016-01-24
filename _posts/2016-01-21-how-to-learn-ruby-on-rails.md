---
layout: post
title:  "How to Learn Ruby on Rails"
date:   2016-01-21 13:37:00
excerpt: If you're new to Ruby or programming altogether, read this post for my best advice on how to learn to make web apps with Ruby on Rails.
---

I've been seeing variations on this question more and more lately:

> I really want to make a web app and I hear Rails is a great tool. How should I go about learning it?

My simple answer is: **don't**. Not yet.

I first got seriously into Rails in mid-2011 (Rails 3.0 era) and I'm still a huge fan of both Rails and Ruby. I now [work full-time leading a Ruby team creating software used by thousands of other Ruby developers](https://github.com/newrelic/rpm), and couldn't be happier with my job. That said, I'm becoming more convinced that **learning Rails is a terrible way to learn Ruby, and an even more terrible way to learn programming**.

Many of the people asking "how do I learn Rails?" got the idea to learn Rails in the first place because they were told (either directly or via an article, Hacker News comment, etc) that it is  a great framework by one of its many fans. **Unfortunately, people who are experts at things are often terrible at considering beginner's perspectives when giving advice**.

Teaching anything is hard. It's a difficult thing to put aside all of the learned knowledge, situational experience, and general intuition/instincts that you've picked up over however many thousands of hours doing something, and think about how it feels to be new. The best people to explain how to do something are people who just reached a basic understanding themselves, because they just went through the process, and are in the best possible mindset to communicate their observations to somebody else.

### Error: Complexity level too deep

When learning anything new (in this case: "how to make a web app," or perhaps "how to code" or "how to code in Ruby"), you want to accomplish something substantial and exciting enough to fuel your motivation to keep going, but you don’t want to take on too much complexity simultaneously. Trying to learn many things at once just raises the difficulty to a point where you're very likely to get frustrated and quit, never to return.

If you dive straight into Rails, you're learning both a new programming language and a complex framework at the same time. The same conveniences and general "magic" that make Rails incredibly powerful for its experienced users are incredibly opaque and confusing for new developers. Just to reiterate, I'm a huge fan of Rails. I just don't think it's a good teaching framework for budding developers. Its best-practices-informed project file structure creates dozens of files (55 as of this writing), so even finding the right place to drop your code in is a battle. The same pattern follows the farther you go. You have to not only understand what classes are, but also the MVC paradigm. You can't just write and read stuff from a database, you have to use the console to first create a migration (which itself means first learning what migrations are, then learning the special language used in them). Don't get me wrong -- **I love the magic**. But for newcomers to Ruby there's just too much to learn at once, especially if you're *also* learning HTML, CSS, and <s>JavaScript</s> CoffeeScript at the same time.

### What you should do instead

So, here's my advice for a would-be Rails developer: if you are new to programming altogether, start with my colleague Chris Pine's brilliant little book, [Learn to Program](http://amzn.to/23fTg1C). You will learn the core concepts of computer programming and the Ruby language and have a good time doing so.

Once you are familiar with basic programming concepts (variables, etc), **pick a very simple database-less project, and build it in [Sinatra](http://www.sinatrarb.com/)**. Sinatra is a wonderfully elegant little framework. It's one gem with few dependencies. All your code goes in one file, unless you choose to divide it. It's very non-magical and "explicit." It's easy to wrap your head around what the framework is doing for you automatically and what your code is making happen. The [Sinatra tutorial on the homepage](http://www.sinatrarb.com/) gets you to 'hello world' wonderfully fast, and the thorough [README](http://www.sinatrarb.com/intro.html) clearly explains many of its deeper features.


When you're ready to add a database, **add [Sequel](https://github.com/jeremyevans/sequel), not ActiveRecord**. ActiveRecord is a powerful database framework, and I love working with it, but Sequel has that same "explicit" characteristic that is so essential for new programmers. There's no magic-location configuration files or migrations. There's little magic at all, actually. And if you're familiar with SQL, which many would-be web developers are, it's super easy to just run raw SQL with no object mapping.

Your first project will not be your last, and your choices (good or bad) in your first project will not ruin everything forever. By building a "toy" project first, before your dream app, you create the immensely-powerful rush of success ("I made it do a thing!") that will fuel further learning cycles. 

Once you've built a thing or two in Sinatra, you'll either be ready to step up in complexity to Rails and more ready to understand (and appreciate!) all the cool things it does for you, or you'll be hooked on Sinatra's elegance and just want to stick with that. Either one works for me!

Agree? Disagree? Come <a href="https://twitter.com/timkrajcar">find me on Twitter</a> and let me know!

<small> Thanks to <a href="https://twitter.com/kwugirl">KWu</a> and <a href="https://twitter.com/otherchrispine">Chris Pine</a> for their contributions to this post!</small>
