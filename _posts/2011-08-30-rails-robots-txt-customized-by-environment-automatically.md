---
layout: post
title: Rails - robots.txt Customized By Environment Automatically
categories: Ruby
excerpt: By default the Rails environment includes public/robots.txt that puts no restrictions on search engines accessing your site. This is generally OK for production, but definitely not desired for development & staging. By generating the file using Rails, you can easily have a different file for each environment without having to move files back and forth.
---

By default the Rails environment includes <code>public/robots.txt</code> that puts no restrictions on search engines accessing your site. This is generally OK for production, but definitely not desired for development & staging. By generating the file using Rails, you can easily have a different file for each environment without having to move files back and forth.

My solution was inspired by <a href="http://stackoverflow.com/questions/2748882/multiple-robots-txt-for-subdomains-in-rails/2923402#2923402" target="_blank">this StackOverflow answer</a>, but it is out of date for Rails 3, so I updated it, and simplified it a little bit too.

Here's how I solved this:

* Copy <code>public/robots.txt</code> to <code>config/robots.development.txt</code>, <code>config/robots.production.txt</code>, and any other environments you might have created, and edit the files to have the correct values for your environments. For example, for most sites, everything but production should have the <code>User-Agent: *</code> and <code>Disallow: /</code> lines uncommented.
* Delete the default <code>public/robots.txt</code> (otherwise it will always be served by your webserver and Rails won't even know of the request).
* In one of your controllers, add a method to handle incoming requests for <code>robots.txt</code> - here's mine:

{% highlight ruby linenos %}
def robots
  robots = File.read(Rails.root + "config/robots.#{Rails.env}.txt")
  render :text => robots, :layout => false, :content_type => "text/plain"
end
{% endhighlight %}

* In <code>config/routes.rb</code>, add: <code>get '/robots.txt' => 'pages#robots'</code>
* To check that everything is working, visit <code>http://mysite/robots.txt</code> and make sure there's no errors. I also used <a href="http://www.frobee.com/robots-txt-check">this robots.txt verifier</a> makes sure my files were formatted properly and served with the text/plain content type.
