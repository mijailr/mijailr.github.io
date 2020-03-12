---
layout: post
title: Dynamic git config - Use diferent profiles per folder
date: 2020-03-11 23:06 -0500
---

Some times we need to use different git profiles to have meaningful commits signatures when we need to use work profiles or personal profiles.

You can do this if you use `git >= 2.13` with the rule `includeIf` you can choose when to use a particular profile when
you are on a specific folder or subfolders.

To do that you need to modify the file `~/.gitconfig` with this content:

{% highlight ini %}
[user]
    name = Your Name
    email = your.personal.email@example.org
[includeIf "gitdir:~/Projects/Work/"]
    path = ~/.gitconfig-work
{% endhighlight %}

And you should have a file like `~/.gitconfig-work` (for this example) with this content:

{% highlight ini %}
[user]
    name = Your Name
    email = your.work.email@example-company.com
{% endhighlight %}

You can add as many `includeIf` as you need.

So now if you cd to any git project inside `~/Projects/Work` your git config should be like this:

{% highlight sh %}
~ $ git config user.email
your.personal.email@example.org
~ $ cd ~/Projects/Work/some-project
~/Projects/Work/some-project $ git config user.email
your.work.email@example-company.com
~/Projects/Work/some-project $ cd ~/Projects/personal-website
/Projects/personal-website $ git config user.email
your.personal.email@example.org
{% endhighlight %}
