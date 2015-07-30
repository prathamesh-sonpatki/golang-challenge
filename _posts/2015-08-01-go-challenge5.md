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

**Goals of the challenge**

At a high level, the goal of this challenge is to write a tool that will find unnecessarily exported identifiers in a package and help unexport them.

This is inspired by the fact that the cmd/compile/internal/gc exports much more than it needs to. (This is ok insofar as it is an [internal package](https://golang.org/s/go14internal), but it'd be better for the API to be more precise.)


**Requirements of the challenge**

Solutions should:

* Be general purpose. That is, the tool should accept a package as an argument.
* Cover all exported identifiers, including functions, constants, variables, types, field names in structs, etc. If godoc shows it, it qualifies.
* Allow the user to decide which identifiers should be unexported. There may be good reasons to keep an identified exported even if it is not used by any packages. One simple way to do this is to have unexport generate a series of [gorename](http://godoc.org/golang.org/x/tools/cmd/gorename) commands. The user could then decide which renamings to apply. It is up to you to design the interface as you please.
* Use only packages found in the standard library and the [golang.org/x/tools repo](http://godoc.org/golang.org/x/tools). Note that there are two copies of the go/types package, [one in the standard library](htts://golang.org/pkg/go/types/) and one in [golang.org/x/tools](http://godoc.org/golang.org/x/tools/go/types). It is ok to use either one. All else being equal, the standard library version is preferable, but the useful [go/loader package](http://godoc.org/golang.org/x/tools/go/loader) in golang.org/x/tools is not (yet?) part of the standard library.
* Use Go 1.5.


Bonus features:

* Provide flag (-safe?) that restricts the use of unexport to internal packages. Only with an internal package can you know definitively that no one is using an exported identifier.
* Provide a mode that shows the number of uses of each exported identifier, and perhaps by which packages they are used.
* Warn if unexporting an identifier will cause a naming collision.
* Whatever else you can think of that would be useful in such a tool. However, please keep the tool focused. If you think building such tools is fun and want ideas for other tools that would be helpful, just ask. :)
* Concise, tone-neutral notes about places where you got stuck or confused and about places where the documentation or examples could be improved. This will help all future gophers. Super bonus points for writing blog posts or making other introductory materials to help others.


**Hints**

unexport might sound complicated to build. It's actually not, thanks to the amazing packages you can build on. The hard part is getting up to speed on the tools at your disposal; the learning curve can be steep. Be patient, build incrementally, and make toys as you go.

In addition to the packages mentioned so far, you might also find the standard library's [go/* packages](http://golang.org/pkg/go/) useful, particularly go/ast.

Examples of programs that use go/ast, go/types, and related packages include:

* [Tools in golang.org/x/tools/cmd](http://godoc.org/golang.org/x/tools/cmd) such as eg, fiximports, goimports, gorename, gotype, and stringer.
* [Tools in the standard library](http://golang.org/cmd/) such as cover, doc, go, gofmt, and vet.
* Other tools, such as [lint](https://github.com/golang/lint), [impl](https://github.com/josharian/impl), and [grind](http://godoc.org/rsc.io/grind).

I recommend using little test packages during development rather than tackling cmd/compile/internal/gc, because package gc is large and complex.


**Special note for the evaluators**

Good entries will be small and obviously correct.

My personal goal in setting this challenge is to inspire more gophers to know about these tools and to solve programming/refactoring problems they face by writing tools. The Go team has laid the groundwork for an ecosystem of awesome tools and seeded it with powerful programs. I hope that this will encourage its growth.



