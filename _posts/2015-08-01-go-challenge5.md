---
layout: post
title: Go Challenge
tags: [go challenge, golang]
---

![update.jpg](/images/update.jpg)

**25th Aug. at 6.00 am IST**: The August 2015 Go Challenge is now closed.

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

[Go 1.5rc1](https://golang.org/dl/#go1.5rc1) is out! The gc compiler is now written in Go, and the [go/types package](https://tip.golang.org/pkg/go/types/) is now part of the standard library.

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

---

#### Challenge Rules and how to enter the Go Challenge?

By participating in this challenge, you agree to be bound by the Challenge Rules below:

* The Challenge is open to individuals.
* Evaluators cannot enter the challenge except under the "Just for Fun" category.
* Each entrant shall indemnify, defend, and hold JoshSoftware Pvt. Ltd. (who has sponsored the domain and is the organizer of these challenges) harmless from any third party claims arising from or related to that entrant's participation in the Challenge. In no event shall JoshSoftware Pvt. Ltd. be liable to an entrant for acts or omissions arising out of or related to the Challenge or that entrant's participation in the Challenge.
* Odds of winning depend on the number and quality of entries received. 
* All taxes, including income taxes, are the sole responsibility of the winners. 
* No prize substitution is permitted.
* Create a zip of your Go source code and test cases and send the zip file to **golangchallenge [at] gmail.com before 25th of August 2015 (6 am IST). Use [this link](http://www.worldtimeserver.com/convert_time_in_IN.aspx?y=2015&mo=8&d=25&h=6&mn=0) to find the equivalent time in your city/country**. No new solutions will be accepted after that. In the email mention **your full name, country of residence, twitter or GitHub id (if any) and participating under which category - Just participating | Participating and exploring further | Just for Fun | Anonymous entry**. We are accepting anonymous submissions and will evaluate them too but then these participants are not eligible for the prizes. 
* We will give your zip file to the evaluation team. 
* We shall be publishing on this blog, a list of participant names. If you don't want your name to appear kindly mention the same in your email. 
* You are allowed to re-submit your code if you feel it is necessary.
* **Note**: Avoid sharing your code with anyone else; if your solution becomes available to the general public it might impact evaluation of your submission.
* After the challenge is over, all submissions will be made available [online on GitHub](https://github.com/golangchallenge/GCSolutions) under the [BSD 3-Clause License](http://opensource.org/licenses/BSD-3-Clause) or the [GNU General Public License, version 3 - GPL-3.0](http://opensource.org/licenses/GPL-3.0) unless a participant has indicated that his/her solution should not be made public before the challenge ends.

#### How will the challenge be evaluated?

Entries will be anonymized and evaluated by the challenge author and a team of evaluators.

* Functioning code and a test suite that passes.
* Code hygiene. Use [gofmt](https://golang.org/cmd/gofmt/), [vet](https://godoc.org/golang.org/x/tools/cmd/vet) and [lint](https://github.com/golang/lint). Review [CodeReviewComments](https://code.google.com/p/go-wiki/wiki/CodeReviewComments).
* Readability. How easy is it for another programmer to grasp what your entry is doing?
* Code structure. Do types and files have good names?
* Reliability. Are errors properly handled?
* Appropriate consideration given to memory and performance (nothing is unnecessarily expensive).

#### Questions?

If you have any questions about this challenge, please join the [golang-challenge channel on slack](http://t.co/n6EesY9Mmv) and ask your questions with the tag @josharian so that the challenge author is aware of your question(s) and can reply to the same (the author is totally unavailable from midday Fri 31st July until Monday morning 3rd Aug, Pacific time. Other than that, he will be available). This is a room for people who are going to participate in the Go Challenge. You can also send us an email at golangchallenge [at] gmail.com

#### Evaluators

[Nathan Youngman](https://twitter.com/nathany) had set the guidelines for evaluation for the first Go Challenge. Subsequently [Dominik Honnef](https://twitter.com/dominikhonnef) modified the guidelines based on his experience as an evaluator for the first challenge. [Austin Riendeau](https://github.com/apriendeau), [Cory LaNou](https://twitter.com/corylanou), [Edd Robinson](https://github.com/e-dard), [Gautam Dey](https://github.com/gdey), [Jyotiska NK](https://twitter.com/jyotiska_nk), [Kevin Gillette](https://twitter.com/kevingillette) and [Pravin Mishra](https://twitter.com/pravinmishra88) have agreed to go through all the submitted solutions of a challenge. They will comment and rank these solutions.

#### Best Solution

The author of the Go Challenge will decide the best five solutions. The author shall have the sole authority and discretion to select the award recipients. 

#### Notification

The winning entries will be announced here on this blog. The winners will be sent their prizes by email/postal mail.

#### Prizes

The author of the challenge will select 5 winners but prizes will be awarded to the top 2 winners.

Here are some great prizes provided by our sponsors for the event.

_Winner 1_:

* [Apcera](https://www.apcera.com/) - [Go Gopher Messenger Bag](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [Cube Root Software](http://cuberoot.in/) - An eBook [Go-The Standard Library](https://leanpub.com/go-thestdlib)
* [Docker](https://www.docker.com/) - To be announced
* [GitHub](https://github.com/) - Free 1 year of a [Personal Micro Plan](https://github.com/pricing).
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [Manning Publications Co.](http://manning.com/) - Two eBooks [Go Web Programming](http://www.manning.com/chang/) and [Go in Action](http://www.manning.com/ketelsen/)
* [Packt Publishing](https://www.packtpub.com/) - A print book [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [SoStronk](https://www.sostronk.com/) - [Counter-Strike: Global Offensive](http://store.steampowered.com/app/730/) game. You will need to have a free [Steam account](https://store.steampowered.com/join/?) to receive this gift.
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

_Winner 2_:

* [Anand D N](https://twitter.com/Wanderer140) - An eBook: [Mastering Go Web Services](http://shop.oreilly.com/product/9781783981304.do)
* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [Manning Publications Co.](http://manning.com/) - One eBook [Go Web Programming](http://www.manning.com/chang/)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [SoStronk](https://www.sostronk.com/) - [Counter-Strike: Global Offensive](http://store.steampowered.com/app/730/) game. You will need to have a free [Steam account](https://store.steampowered.com/join/?) to receive this gift.
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

#### Winner Interviews

After a winner wins the monthly challenge, he/she would be interviewed by [Sourcegraph](https://sourcegraph.com/) and the interview will be published on their [blog](https://sourcegraph.com/blog).

#### Challenge Solutions

All the solutions submitted by the participants will be available **[here](https://github.com/golangchallenge/GCSolutions)** after the challenge ends.

#### Sponsors

This challenge's sponsors are: [Anand D N](https://twitter.com/Wanderer140), [Cube Root Software](http://cuberoot.in/), [Docker](https://www.docker.com/), [GitHub](https://github.com/), [InfluxDB](http://influxdb.com/), [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/), [Manning Publications Co.](http://manning.com/), [Packt Publishing](https://www.packtpub.com/), [Qwinix Technologies](http://www.qwinixtech.com/), [SoStronk](https://www.sostronk.com/) and [Sourcegraph](https://sourcegraph.com/).

#### Credit

* The Gopher character is based on the Go mascot designed by Renée French and copyrighted under the Creative Commons Attribution 3.0 license.
* [GitHub](https://github.com/) for the yearly sponsorship of a [GitHub Bronze Organisation plan](https://github.com/pricing) for the Go Challenge.
* The Go Challenge is being organized by [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/) with help from the Go community.


