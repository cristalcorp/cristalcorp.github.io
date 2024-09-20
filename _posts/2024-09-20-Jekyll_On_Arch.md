---
layout: post
title: Jekyll on Arch
feature-img: "assets/img/posts/jekyll/jekyll_logo.png"
categories: blog
tags: [Blog, Ruby, Arch]
---

How to make a local environment on Arch for Jekyll blog dev

# Jekyll On Arch

In order to have the ability to work locally on this blog, a few things are necessary. As I forget them all every time I need to reconfigure my computer, I ll go through them here.

## Side A : Arch
First of all, install Ruby. Usually ERB is included but not this time ( or not here at least ) so the package ruby-erb is also needed. Base-devel is needed for compilations.

```bash
sudo pacman -S ruby base-devel ruby-erb
  
# is this overkill ?
sudo pacman -S libffi zlib openssl readline libyaml gdbm
```

## Side B : Jekyll
Now that Ruby is correctly set up on our system, just a bit of config and we can launch the server.
From within the jekyll folder

```bash
# Install the needed gems
gem install bundler

# Add bundle tools to the PATH. In .zshrc add
export PATH=$PATH:~/.local/share/gem/ruby/3.2.0/bin

# To avoid permissions issue we need to set a directory for bundle to install the needed gems
mkdir ~/Documents/ruby/
bundle config path ~/Documents/ruby

# Then install 
bundle install
bundle update

# And finally launch the local server
bundle exec jekyll serve
```


