---
layout: post
title: Go Challenge
tags: [go challenge, golang]
published: false
---

#### The August 2015 Go Challenge for developers (newbies included)

#### Josh Bleecher Snyder: Author of the 5th Go Challenge

<img align="right" src="/images/josh.jpg" height="150" width="150" alt="Josh Bleecher Snyder" title="Josh Bleecher Snyder" style="border:5px solid black" />
The 5th Go Challenge author is Josh Bleecher Snyder an active contributor to the Go project. He's an engineer at [Braintree](https://www.braintreepayments.com/) and previously co-founded [card.io](https://www.card.io/).

Josh has this to say about the challenge:

> "I love writing tools to work with Go. It gives you a much deeper appreciation for the language and places incredible (and delightfully dangerous) power at your fingertips."

--- 

#### The Go Challenge 5

##### unexport

##### Preamble

[Go 1.5 Beta 3](https://groups.google.com/forum/m/#!topic/golang-nuts/hm9tWv534bI) is out! The gc compiler is now written in Go, and the [go/types package](htts://golang.org/pkg/go/types/) is now part of the standard library.

Time for some fun. :)

The compiler was converted from C to Go mechanically. This helped avoid bugs, but it means that the code is still very C-ish. The Go team has been slowly and carefully doing cleanup to make the compiler more idiomatic. It is preferable to use type-safe tools (such as [eg](http://godoc.org/golang.org/x/tools/cmd/eg) and [gorename](http://godoc.org/golang.org/x/tools/cmd/gorename)) to do large-scale cleanup, because they make fewer mistakes than humans.

But sometimes, [the tool you need doesn't exist](https://go-review.googlesource.com/#/c/7593/). Fortunately, the standard library gives us [amazing tools to build tools](https://talks.golang.org/2014/hammers.slide#1). So you build one.

Let's build one.


