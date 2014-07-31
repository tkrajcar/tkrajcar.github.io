---
layout: post
title: "iTerm Tab & Window Titles with zsh"
excerpt: A quick and easy solution for your .zshrc to get useful tab & window titles.
---

If you use the excellent [iTerm](http://iterm.sourceforge.net/) Terminal replacement on Mac, you probably heavily use tabs and windows for managing multiple sessions. For whatever reason, by default zsh doesn't report the current working directory as the tab title when you're working locally. I'd noticed this before, but when [@anniegreens](http://anniegreens.com/), one of my teammates, mentioned it, I figured it was time to dig in and learn some zsh scripting.

I found plenty of other solutions to this problem, but many of them used a ton of code and I wanted a simple solution that I understood, rather than dropping a bunch of stuff into my .zshrc that I didn't really understand. Note this is written for zsh 4.3.11, which is what comes with OS X Lion.

Another distinction of my solution is that, rather than treating the tab title and the window title the same, like most other solutions, it puts the full relative path in the window title, and then the right-most 24 characters (exactly enough to fit without being ...-ed by iTerm) in the tab title. 

Here's the relevant section of my .zshrc, which you can view in [my dotfiles repo on GitHub](https://github.com/tkrajcar/dotfiles):

{% highlight bash %}
# set tab title to cwd
precmd () {
  tab_label=${PWD/${HOME}/\~} # use 'relative' path
  echo -ne "\e]2;${tab_label}\a" # set window title to full string
  echo -ne "\e]1;${tab_label: -24}\a" # set tab title to rightmost 24 characters
}
{% endhighlight %}
