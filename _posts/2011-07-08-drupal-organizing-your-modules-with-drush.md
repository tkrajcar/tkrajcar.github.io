---
layout: post
title: Drupal - Organizing Your Modules With Drush
categories: Drupal
excerpt: I've been using Drush for some time now for Drupal development. Especially for downloading, enabling, and updating modules, it is considerably quicker than doing things by hand. Another practice I’ve also taken to is putting all downloaded modules in a contrib/ folder instead of simply in sites/all/modules/. This makes my custom modules stand out much more than they would otherwise, which is a good thing for multi-developer sites or for just generally taking a look at what custom code a site is using.
---
I've been using <a title="Drush" href="http://www.drush.ws" target="_blank">Drush</a> for some time now for Drupal development. Especially for downloading, enabling, and updating modules, it is considerably quicker than doing things by hand.

Another practice I've also taken to is putting all downloaded modules in a <code>contrib/</code> folder instead of simply in <code>sites/all/modules/</code>. This makes my custom modules stand out much more than they would otherwise, which is a good thing for multi-developer sites or for just generally taking a look at what custom code a site is using.

Drush, however, by default, puts everything you download via <code>drush dl mymodule</code> into <code>sites/all/modules/</code>. There's a <code>--destination</code> parameter, but I would quickly tire of having to remember that every time. But, there's a quick an easy solution using a <code>drushrc</code> file.

If you don't already have a drushrc setup, you'll need to make one in your <code>.drush</code> folder in your home directory. You can make any number of drushrc files in <code>~/.drush/</code>, as long as they all end in <code>drushrc.php</code>.

Here's the one I created and named <code>aliases.drushrc.php</code> (just in case I want to add more aliases later):

{% highlight php linenos %}
<?php
$command_specific['dl'] = array('destination' => 'sites/all/modules/contrib');
?>
{% endhighlight %}

For my next trick, I'm going to try <a href="http://technicalpickles.com/posts/never-leave-your-dotfiles-behind-again-with-homesick/">Homesick</a>, a Ruby gem for helping your dot files follow you around, so I can get this file created everywhere I need it.

