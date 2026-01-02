---
title: Explaining The Weird On My Twitter Timeline
layout: post
---

If any of you have in the recent past seen my Twitter timeline [@arelangi][profile] and are wondering what all the tweets are about, this post is for you.

<!--excerpt-->

Alright, I've built this simple program in Go, which basically hijacks a signal that the Amazon Dash button sends by sniffing for packets on the network. What does this have to do with my timeline you ask? Well, as well meaning as I am it's been really hard for me to consistently work out and reading Dan Ariely's books I figured that it'd be nice to have an incentive to working out. In this case the incentive being not shaming myself on my Twitter timeline.

For everyday I workout I am supposed to press the Amazon Dash button which signifies the program that I've worked out. If I fail to do so, the program tweets out the embarassing message you might've noticed on my timeline. I've put up a couple of checks in place to make sure that I can't bypass this mechanism. The code is all open source and is available [here][godash] and [here][godashdaemon] for anyone who wishes to check it out.

The talk I gave about this is [here][talk]


[profile]: https://twitter.com/arelangi "arelangi"
[talk]: http://adityarelangi.com/talks/2016/april/#1 "talk"
[godash]: https://github.com/logzer0/godash "go dash"
[godashdaemon]: https://github.com/logzer0/godashdaemon "go dash daemon"