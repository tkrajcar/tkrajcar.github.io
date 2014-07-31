---
layout: post
title: Rails - Customized link_to Helpers
categories: Ruby
excerpt: Rails by default has a number of helper methods that return simple HTML. One that’s extremely powerful is link_to which, generally speaking, generates links to other pages. On one particular project, I knew I would be writing a lot of links that referenced another site. While I certainly could’ve written raw HTML since they weren’t using named routes or any other Rails niftiness and were essentially static links with a few dynamic URL variables, one of the principles of Rails is Don’t Repeat Yourself, so I wrote a custom link_to helper for the occasion.
---

In my spare time I've been learning Ruby on Rails. I've not been so excited about a web technology in a very long time. I'm really enjoying working on my projects with it and it's the most productive I've ever been as a web developer. At some point I want to write a more detailed analysis on my thoughts, but in the meantime, here's something I did that was kind of interesting that might be of use to somebody out there.

Rails by default has a number of helper methods that return simple HTML. One that's extremely powerful is <a href="http://api.rubyonrails.org/classes/ActionView/Helpers/UrlHelper.html#method-i-link_to"><code>link_to</code></a> which, generally speaking, generates links to other pages.

On one particular project, I knew I would be writing a lot of links that referenced another site. While I certainly could've written raw HTML since they weren't using named routes or any other Rails niftiness and were essentially static links with a few dynamic URL variables, one of the principles of Rails is Don't Repeat Yourself, so I wrote a custom <code>link_to</code> helper for the occasion.

In general, I knew all of my calls would be to the same domain, with varying pages and URL variables, ie:

    http://www.constantsite.com/variable.cfm?urlvar1=dynamic&urlvar2=dynamic


Happily, Ruby hashes can easily be serialized as URL variables, and thanks to the ability of Ruby to merge hashes, I can even set a default <code>target</code> attribute that can be overridden later.

Here's what I ended up with in my <code>pages_helper.rb</code>:

{% highlight ruby %}
def link_to_mysite(text, page, urlvars={}, options={})
  link_to text, "http://constantsite.com/#{page}.cfm?#{urlvars.to_query}", {:target => "_blank"}.merge(options)
end
{% endhighlight %}

And some sample usage:

{% highlight ruby %}
link_to_mysite "No URL vars", "novar"
# renders: <a href="http://constantsite.com/novar.cfm?" target="_blank">No URL vars</a>

link_to_mysite "Yeah!", "init", {:id => myvar}, {:class => "example"}
# renders: <a href="http://constantsite.com/init.cfm?id=<myvar contents>" class="example" target="_blank">Yeah!</a>

link_to_mysite "No new window", "samewindow", {:id => myvar}, {:target=> "_self"}
# renders: <a href="http://constantsite.com/samewindow.cfm?id=<myvar contents>" target="_self">No new window</a>
{% endhighlight %}

Two little subtleties of the Ruby language at work here:
1. By using <code>={}</code> on my last two arguments, they become optional, with the default being empty hashes.</li>
2. When merging two hashes, the keys from the argument to <code>merge()</code> override the keys from the object you call <code>merge()</code> on. That, combined with Ruby's lovely habit of treating everything as an object, lets me declare my default <code>:target</code> (and any other future options) first, knowing it will be overridden automatically if the method is invoked with a specified <code>:target</code>.

Ruby is <strong>awesome</strong> - and Rails makes it even better.
