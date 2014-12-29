---
layout: post
title:  "Forwarding Class Methods in Ruby"
date:   2014-12-29 13:37:00
excerpt: Forwarding or delegating methods in Ruby is a common occurrence, but forwarding class methods can be just as useful. The SingleForwardable module can help save the day!
---

Recently I had a project where I wanted to make a simple "centralized logger" that could be called from anywhere in a small application. I decided to set up a simple class that I could call from anywhere in the app, re-using the <a href="http://www.ruby-doc.org/stdlib-2.2.0/libdoc/logger/rdoc/Logger.html)">Ruby Logger class</a>'s various write methods (<code>#debug</code>, <code>#warn</code>, and so on).

I experimented with a lot of different solutions for forwarding or delegating a Ruby class method. My first stop was at the <a href="http://www.ruby-doc.org/stdlib-2.2.0/libdoc/forwardable/rdoc/Forwardable.html">Forwardable module</a>, but I couldn't figure out a way to get it to delegate a class method. I eventually rigged up a somewhat hacky solution with <a href="http://www.ruby-doc.org/core-2.2.0/Module.html#method-i-define_method">define_method</a>, but I wasn't very happy with it.

Finally, a co-worker pointed me to <a href="http://www.ruby-doc.org/stdlib-2.2.0/libdoc/forwardable/rdoc/SingleForwardable.html">SingleForwardable</a>, which can be used to set up delegations for individual objects, classes, or modules. Perfect!

{% highlight ruby linenos %}
require 'logger'
require 'forwardable'

class SpecialLogger
  extend SingleForwardable

  @logger = Logger.new(STDOUT)
  @logger.level = Logger::INFO

  def_delegators :@logger, :debug, :info, :warn, :error, :fatal
end

SpecialLogger.warn("Oh no!")
# W, [2014-12-29T15:07:39.704559 #41608]  WARN -- : Oh no!
{% endhighlight %}

Works perfectly, and in just a few quick, extremely readable, lines of code.
