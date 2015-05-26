---
layout: post
title: Go Challenge 4
tags: [go challenge, golang]

---
![update.jpg](/images/update.jpg)

**The challenge author has added this:**.

**Additional Hint**: The challenge as presented might have bottlenecks. Your job is to do the best you can with the input you are given. You might find it interesting to measure where bottlenecks are and experiment with how to remove them by modifying the driver program (but your final submitted solution should still follow the instructions given earlier, using the unmodified driver).

--- 

#### The June 2015 Go Challenge for developers (newbies included)

#### Jeff R. Allen: Author of the 4th Go Challenge

<img align="right" src="/images/jra.jpg" height="200" width="200" alt="Jeff R. Allen" title="Jeff R. Allen" style="border:5px solid black" />
The 4th Go Challenge author is [Jeff R. Allen](http://blog.nella.org/). Jeff R. Allen is just another Go hacker in Lausanne, Switzerland. He's been using Go since 2010, and remembers using `gofix` every week to fix his programs. He's interested in performance tuning the standard library (but only once it is correct, and only if the result is [clearer than it was before](https://github.com/golang/go/commit/6d248cec56dd56f3ddb92bd587b5c4ac2f9919b1)).

When he is not busy hacking Go, he likes to cut his grass with a scythe and give the clippings to the alpacas who live next door.

Jeff has this to say about the challenge:

> "This challenge is a version of a [packing problem](http://en.wikipedia.org/wiki/Packing_problems)."

> With problems of this type, there are often a range of solutions available from "trivial but not very good", through to "perfect, but too expensive". It is my hope that this range of possible solutions gives the range of programmers that the Golang Challenge attracts a range of different experiences solving it.

> The previous challenges have attracted a huge amount of interest. For this we are thankful. But it also means evaluating all of them is hard for our volunteer evaluators. This challenge has been structured to allow us to evaluate the solutions for performance automatically. An unfortunate side effect of making a challenge easier to grade is that we need to take away some of the wide open possibility by constraining the format of the solutions. We hope you can understand the tradeoff and have fun anyway.

--- 

#### The Go Challenge 4

##### Parker & Packer Unpacking & Repacking, Limited

##### Preamble

A few years ago, Bob Parker and his partner Bob Packer found an unexploited niche in the global logistics industry. They realized that poorly packed boxes were wasting space, and worse, tying up pallets that could be resold for a profit. They founded a company and business is booming!

Now they've got a problem. They've got more boxes to repack than they can mange with their staff. They've invested in robots to help them increase their capacity, and you're in charge of programming them.

##### Goals of the challenge

Your task is to implement an algorithm that, given a trucks full of a pallets with boxes on them that may or may not be correctly packed, packs boxes onto the pallets correctly. A correctly packed pallet is one where none of the boxes on it overlap, and none of the boxes hang over the edge of the pallet. Pallets are packed in only two dimensions, with a single layer of boxes which have an arbitrary height. All of the trucks are going the same place anyway, so it doesn't matter which truck a box goes in, as long as it is packed correctly on a pallet.

Empty pallets left over after repacking are pure profit. More empties = more better! And if a truck leaves the warehouse with more pallets on it than it came with, it comes out of your profit. So pack carefully!

##### Requirements of the challenge

Download a [zip file](http://golang-challenge.com/data/ch4/gc4.zip) where you'll find a driver program made up of a parser that reads trucks full of pallets from an input file, passes them through the repacker, and evaluates the results.

Your job is to replace the current `repack.go` file with your own. You may not modify the other provided Go files. You may add additional files.

Your `repack.go` file will be evaluated on an input file with enough trucks in it to keep your algorithm busy for more than 2 seconds. The better the performance of your algorithm is, the more trucks you'll manage to process in the given time, and thus the more pallets you'll be able to empty, and the more profit you'll make for your client.

* Use only the standard library.
* Submit a replacement `repack.go`, and any other files needed to make it compile with the provided files (for example, maybe `repack_test.go`).
* All of your code should be in `package main`. Showing that you know how to structure code into packages is not part of this challenge.

**Note**: Only 30% of your overall score is based on the runtime behavior (the reliability and performance) of your entry. Faster is better, but only if it remains readable and idiomatic Go code. Remember that your colleagues at Parker & Packer have to maintain your code next month when you are working on Golang Challenge #5!

##### Hints

You can use the file `testdata/100trucks.txt` to develop your algorithm.

You can also use the `-generate` and `-seed` flags to generate your own test files if you'd like. The input file used for evaluating all entries will be generated using `-generate` with a huge number of trucks, and a different seed from the default.

Your solution will be evaluated on a multi-core system (for example, MacOS X 10.9.5 on a 2.4 GHz Intel Core i7). Note that `GOMAXPROCS` is already set to 4 in `main.go`. If you choose to use multiple goroutines in your repacker, you might be able to process more boxes in the given time, thereby freeing up more pallets and more profit.

---

#### Challenge Rules and how to enter the Go Challenge?

By participating in this challenge, you agree to be bound by the Challenge Rules below:

* The Challenge is open to individuals.
* Evaluators cannot enter the challenge except under the "Just for Fun" category.
* Each entrant shall indemnify, defend, and hold JoshSoftware Pvt. Ltd. (who has sponsored the domain and is the organizer of these challenges) harmless from any third party claims arising from or related to that entrant's participation in the Challenge. In no event shall JoshSoftware Pvt. Ltd. be liable to an entrant for acts or omissions arising out of or related to the Challenge or that entrant's participation in the Challenge.
* Odds of winning depend on the number and quality of entries received. 
* All taxes, including income taxes, are the sole responsibility of the winners. 
* No prize substitution is permitted.
* Create a zip of your Go source code and test cases and send the zip file to **golangchallenge [at] gmail.com before 23rd of June 2015 (6 am IST). Use [this link](http://www.worldtimeserver.com/convert_time_in_IN.aspx?y=2015&mo=6&d=23&h=6&mn=0) to find the equivalent time in your city/country**. No new solutions will be accepted after that. In the email mention **your full name, country of residence, twitter or GitHub id (if any) and participating under which category - Just participating | Participating and exploring further | Just for Fun | Anonymous entry**. We are accepting anonymous submissions and will evaluate them too but then these participants are not eligible for the prizes. 
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

If you have any questions about this challenge, please join the [golang-challenge channel on slack](http://t.co/n6EesY9Mmv) and ask your questions with the tag @jeff_allen so that the challenge author is aware of your question(s) and can reply to the same. This is a room for people who are going to participate in the Go Challenge. You can also send us an email at golangchallenge [at] gmail.com

#### Evaluators

[Nathan Youngman](https://twitter.com/nathany) had set the guidelines for evaluation for the first Go Challenge. Subsequently [Dominik Honnef](https://twitter.com/dominikhonnef) modified the guidelines based on his experience as an evaluator for the first challenge. [Austin Riendeau](https://github.com/apriendeau), [Cory LaNou](https://twitter.com/corylanou), [Edd Robinson](https://github.com/e-dard), [Gautam Dey](https://github.com/gdey), [Jyotiska NK](https://twitter.com/jyotiska_nk), [Kevin Gillette](https://twitter.com/kevingillette) and [Pravin Mishra](https://twitter.com/pravinmishra88) have agreed to go through all the submitted solutions of a challenge. They will comment and rank these solutions.

#### Best Solution

The author of the Go Challenge will decide the best five solutions. The author shall have the sole authority and discretion to select the award recipients. 

#### Notification

The winning entries will be announced here on this blog. The winners will be sent their prizes by email/postal mail.

#### Prizes

The author of the challenge will select 5 winners.

Here are some great prizes provided by our sponsors for the event.

_Winner 1_:

* [Apcera](https://www.apcera.com/) - [Go Gopher Messenger Bag](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [CoreOS](https://coreos.com/) - Company T-Shirt and stickers and a free ticket to the [CoreOS Fest](https://coreos.com/fest/) in SFO.
* [Crowd Interactive](http://www.crowdint.com/) - A US$ 25 Amazon digital gift card.
* [Cube Root Software](http://cuberoot.in/) - An eBook [Go-The Standard Library](https://leanpub.com/go-thestdlib)
* [DigitalOcean](https://www.digitalocean.com/) - US$ 50 Amex Gift Card
* [GitHub](https://github.com/) - Free 1 year of a [Personal Micro Plan](https://github.com/pricing) and a [T-Shirt](http://github.myshopify.com/) of your choice.
* [Helpshift](http://www.helpshift.com/) - An eBook [A Go Developer's Notebook](https://leanpub.com/GoNotebook)
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [John Sonmez](https://twitter.com/jsonmez) - An eBook [Soft Skills: The software developer's life manual](http://www.amazon.com/gp/product/1617292397/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=1617292397&linkCode=as2&tag=satishtalimsw-20&linkId=WGSAUMHIF2SVWJ7D)
* [Koding](https://koding.com/Pricing) - A free Hobbyist plan for 3 months
* [Manning Publications Co.](http://manning.com/) - Two eBooks [Go Web Programming](http://www.manning.com/chang/) and [Go in Action](http://www.manning.com/ketelsen/)
* [NodePrime](http://www.nodeprime.com/) - An eBook [The Go Programming Language Phrasebook (Developer's Library)](http://goo.gl/mTwIOS)
* [O'Reilly](http://www.oreilly.com/) - An eBook [Mastering Go Web Services](http://shop.oreilly.com/product/9781783981304.do)
* [Packt Publishing](https://www.packtpub.com/) - A print book [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [RainingClouds](http://rainingclouds.com/#!/) - An eBook [Level Up Your Web Apps With Go](http://shop.oreilly.com/product/9780992461294.do)
* [SoStronk](https://www.sostronk.com/) - [Counter-Strike: Global Offensive](http://store.steampowered.com/app/730/) game. You will need to have a free [Steam account](https://store.steampowered.com/join/?) to receive this gift.
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

_Winner 2_:

* [Anand D N](https://twitter.com/Wanderer140) - An eBook: [Mastering Go Web Services](http://shop.oreilly.com/product/9781783981304.do)
* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [CoreOS](https://coreos.com/) - Company T-Shirt and stickers and a free ticket to the [CoreOS Fest](https://coreos.com/fest/) in SFO.
* [Crowd Interactive](http://www.crowdint.com/) - A US$ 25 Amazon digital gift card.
* [DigitalOcean](https://www.digitalocean.com/) - US$ 50 Amex Gift Card
* [Docker](https://www.docker.com/) - A ticket to [DockerCon 2015](http://www.dockercon.com/) in SFO, USA OR to DockerCon Europe (to be announced but probably in Dec. 2015).
* [GitHub](https://github.com/) - Free 1 year of a [Personal Micro Plan](https://github.com/pricing) and a [T-Shirt](http://github.myshopify.com/) of your choice.
* [Helpshift](http://www.helpshift.com/) - An eBook [A Go Developer's Notebook](https://leanpub.com/GoNotebook)
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [John Sonmez](https://twitter.com/jsonmez) - An eBook [Soft Skills: The software developer's life manual](http://www.amazon.com/gp/product/1617292397/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=1617292397&linkCode=as2&tag=satishtalimsw-20&linkId=WGSAUMHIF2SVWJ7D)
* [Koding](https://koding.com/Pricing) - A free Hobbyist plan for 3 months
* [Manning Publications Co.](http://manning.com/) - One eBook [Go Web Programming](http://www.manning.com/chang/)
* [NodePrime](http://www.nodeprime.com/) - An eBook [The Go Programming Language Phrasebook (Developer's Library)](http://goo.gl/mTwIOS)
* [Packt Publishing](https://www.packtpub.com/) - An eBook [Building Your First Application with Go-Video](https://www.packtpub.com/application-development/building-your-first-application-go-video)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [RainingClouds](http://rainingclouds.com/#!/) - An eBook [Level Up Your Web Apps With Go](http://shop.oreilly.com/product/9780992461294.do)
* [SoStronk](https://www.sostronk.com/) - [Counter-Strike: Global Offensive](http://store.steampowered.com/app/730/) game. You will need to have a free [Steam account](https://store.steampowered.com/join/?) to receive this gift.
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

_Winner 3_:

* [Anand D N](https://twitter.com/Wanderer140) - An eBook: [Mastering Go Web Services](http://shop.oreilly.com/product/9781783981304.do)
* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [DigitalOcean](https://www.digitalocean.com/) - US$ 50 Amex Gift Card
* [GitHub](https://github.com/) - Free 1 year of a [Personal Micro Plan](https://github.com/pricing) and a [T-Shirt](http://github.myshopify.com/) of your choice.
* [Manning Publications Co.](http://manning.com/) - One eBook [Go in Action](http://www.manning.com/ketelsen/)
* [NodePrime](http://www.nodeprime.com/) - An eBook [The Go Programming Language Phrasebook (Developer's Library)](http://goo.gl/mTwIOS)
* [Packt Publishing](https://www.packtpub.com/) - An eBook [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [RainingClouds](http://rainingclouds.com/#!/) - An eBook [Level Up Your Web Apps With Go](http://shop.oreilly.com/product/9780992461294.do)
* [SoStronk](https://www.sostronk.com/) - [Counter-Strike: Global Offensive](http://store.steampowered.com/app/730/) game. You will need to have a free [Steam account](https://store.steampowered.com/join/?) to receive this gift.

_Winner 4_:

* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [DigitalOcean](https://www.digitalocean.com/) - US$ 50 Amex Gift Card
* [GitHub](https://github.com/) - Free 1 year of a [Personal Micro Plan](https://github.com/pricing) and a [T-Shirt](http://github.myshopify.com/) of your choice.
* [Manning Publications Co.](http://manning.com/) - One eBook [Go in Practice](http://www.manning.com/butcher/)
* [NodePrime](http://www.nodeprime.com/) - An eBook [The Go Programming Language Phrasebook (Developer's Library)](http://goo.gl/mTwIOS)
* [Packt Publishing](https://www.packtpub.com/) - An eBook [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [RainingClouds](http://rainingclouds.com/#!/) - An eBook [Level Up Your Web Apps With Go](http://shop.oreilly.com/product/9780992461294.do)
* [SoStronk](https://www.sostronk.com/) - [Counter-Strike: Global Offensive](http://store.steampowered.com/app/730/) game. You will need to have a free [Steam account](https://store.steampowered.com/join/?) to receive this gift.

_Winner 5_:

* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [DigitalOcean](https://www.digitalocean.com/) - US$ 50 Amex Gift Card
* [GitHub](https://github.com/) - Free 1 year of a [Personal Micro Plan](https://github.com/pricing) and a [T-Shirt](http://github.myshopify.com/) of your choice.
* [Manning Publications Co.](http://manning.com/) - One eBook [Go in Practice](http://www.manning.com/butcher/)
* [NodePrime](http://www.nodeprime.com/) - An eBook [The Go Programming Language Phrasebook (Developer's Library)](http://goo.gl/mTwIOS)
* [Packt Publishing](https://www.packtpub.com/) - An eBook [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [RainingClouds](http://rainingclouds.com/#!/) - An eBook [Level Up Your Web Apps With Go](http://shop.oreilly.com/product/9780992461294.do)
* [SoStronk](https://www.sostronk.com/) - [Counter-Strike: Global Offensive](http://store.steampowered.com/app/730/) game. You will need to have a free [Steam account](https://store.steampowered.com/join/?) to receive this gift.

Anyone can a get 42% off on the price of the following eBooks from [Manning Publications Co.](http://manning.com/):

* [Go Web Programming](http://www.manning.com/chang/) - Use discount code: **cftw15go**
* [Go in Action](http://www.manning.com/ketelsen/) - Use discount code: **cftw15go**
* [Go in Practice](http://www.manning.com/butcher/) - Use discount code: **cftw15go**

#### Winner Interviews

After a winner wins the monthly challenge, he/she would be interviewed by [Sourcegraph](https://sourcegraph.com/) and the interview will be published on their [blog](https://sourcegraph.com/blog).

#### Challenge Solutions

All the solutions submitted by the participants will be available **[here](https://github.com/golangchallenge/GCSolutions)** after the challenge ends.

#### The Winners

![winner.png](/images/winner.png)

#### Sponsors

This challenge's sponsors are: [Anand D N](https://twitter.com/Wanderer140), [Apcera](https://www.apcera.com/), [CoreOS](https://coreos.com/), [Crowd Interactive](http://www.crowdint.com/), [Cube Root Software](http://cuberoot.in/), [DigitalOcean](https://www.digitalocean.com/), [Docker](https://www.docker.com/), [GitHub](https://github.com/), [GopherCasts](https://gophercasts.io/), [Helpshift](http://www.helpshift.com/), [InfluxDB](http://influxdb.com/), [John Sonmez](https://twitter.com/jsonmez), [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/), [Manning Publications Co.](http://manning.com/), [NodePrime](http://www.nodeprime.com/), [O'Reilly](http://www.oreilly.com/), [Packt Publishing](https://www.packtpub.com/), [Qwinix Technologies](http://www.qwinixtech.com/), [RainingClouds](http://rainingclouds.com/#!/), [SoStronk](https://www.sostronk.com/) and [Sourcegraph](https://sourcegraph.com/).

#### Credit

* The Gopher character is based on the Go mascot designed by Renée French and copyrighted under the Creative Commons Attribution 3.0 license.
* [GitHub](https://github.com/) for the yearly sponsorship of a [GitHub Bronze Organisation plan](https://github.com/pricing) for the Go Challenge.
* The Go Challenge is being organized by [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/) with help from the Go community.
