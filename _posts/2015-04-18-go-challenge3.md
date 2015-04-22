---
layout: post
title: Go Challenge 3
tags: [go challenge, golang]
---

#### The May 2015 Go Challenge for developers (newbies included)

#### Sau Sheong Chang: Author of the third Go Challenge

<img align="right" src="/images/sausheong.jpg" height="200" width="200" alt="Sau Sheong Chang" title="Sau Sheong Chang" style="border:5px solid black" />
The third Go Challenge author is [Sau Sheong Chang](https://twitter.com/sausheong). He has been doing software development for 20 years, mostly in web application development. He is active in the Ruby and Go developer communities and has contributed to open source projects and spoke at meetups and conferences. Sau Sheong has also published 3 programming-related books, mostly on Ruby and is working on a 4th book titled [Go Web Programming](http://manning.com/chang). He is currently a Director of Global Consumer Engineering in PayPal, based out of sunny Singapore and has in his career worked for HP, Yahoo, and also ran a technology startup during the dot-com days.

Sau has this to say about the challenge:

> "This is a challenge for beginners to start learning about writing web applications in Go. Generating photo-mosaics is the fun bit. After the challenge, the challenge participant should be able to write a web application, write test cases, call REST-based API and at the very least, manipulate images all using the standard Go library."

> "And of course, have lots of fun in the process."

--- 

#### The Go Challenge 3

##### Go Picture This!

##### Preamble

A photographic mosaic, or a photo-mosaic is a picture (usually a photograph) that has been divided into (usually equal sized) rectangular sections, each of which is replaced with another picture (called a tile picture). If we view it from far away or if you squint at it, then the original picture can be seen. If we look closer though, we will see that the picture is in fact made up of many hundreds or thousands of smaller tile pictures.

##### Goals of the challenge

Your mission, should you accept it, is to write a photo-mosaic generating web application that:

* Allows the user to upload a target picture, which is the picture that will be made into a photo-mosaic
* Allows the user to connect to one or more photo-sharing sites like Instagram or Flickr or Facebook Photos (or any photo-sharing site of your choice) to get tile pictures. Your user doesn't necessarily need to log in, you can use the image search APIs to get the tile pictures
* Allows the user to use a search filter (for e.g. use only pictures with cats in it) to filter out a set of tile pictures
* Generates a photo-mosaic of the target picture using the tile pictures

##### Bonus goals (optional, not part of the challenge)

Add features to your web application to:

* Allow the user to log in (can be your own database or log in through a third party like GitHub or Twitter or Facebook, through OAuth2). (Note: if you are authenticating the user through OAuth2, you should use the OAuth2 login flow instead of an external library).
* Allow the user to save the photo-mosaic, either on the site or upload it back to the photo-sharing site

##### Requirements of the challenge

* Use the latest version of Go i.e. version 1.4.2
* The critical part is not the UI but learning to write web applications, so I won't be too bothered if the participant uses [Bootstrap](http://en.wikipedia.org/wiki/Bootstrap_%28front-end_framework%29) or [Polymer](https://www.polymer-project.org/0.5/) or any other CSS frameworks. I'm even ok if you use AngularJS or any other front-end frameworks, though that would be missing a chunk of learning. I'm more concerned about the user experience -- the web application should have good performance, easy to follow steps and a well understood interface
* Deploy to a publicly available site; the final software must not only be working, but be usable. You can use Google Cloud Platform or Heroku or any cloud provider, as long as it is working and is deployed publicly, it will be accepted
* Individual tile pictures must be clearly visible when magnified, though it is expected to be smaller
* Use only the standard library, except for database drivers (if used). Do not use any web frameworks such as Beego or the Gorilla Toolkit. Also, Google App Engine's own libraries would be considered external.
* You need to write test cases for the main flow. Do submit your test cases. 
* Do [organize your code](https://youtu.be/XCsL89YtqCs).

##### Hints

You can find out more about photo-mosaics from this Wikipedia entry - [http://en.wikipedia.org/wiki/Photographic_mosaic](http://en.wikipedia.org/wiki/Photographic_mosaic)

You can also look at some photo-mosaic sites that are already available:

* [http://www.picturemosaics.com](http://www.picturemosaics.com)
* [http://www.easymoza.com](http://www.easymoza.com)
* [http://mosaically.com](http://mosaically.com)

Remember not to use the 'ghosting' technique when creating photo-mosaics, that's a big no-no. 'Ghosting' is when you place a faint picture of the target under your mosaic to create an illusion of a mosaic. It's kind of like cheating!

As a starter to deploying your web application to a public provider, you can read this eBook:

[How to Deploy a Go Web App to the Google App Engine 101](https://leanpub.com/howtodeployagowebapptothegoogleappengine101)

Or you can view this YouTube video to learn more - [https://www.youtube.com/watch?v=XCsL89YtqCs](https://www.youtube.com/watch?v=XCsL89YtqCs)

If you find this challenge daunting or find yourself stuck, do go to the [Gophers Slack](http://t.co/n6EesY9Mmv) channel #golang-challenge and chat with me (@sausheong) - I will help you along the way.

---

#### Challenge Rules and how to enter the Go Challenge?

By participating in this challenge, you agree to be bound by the Challenge Rules below:

* The Challenge is open to individuals.
* Evaluators cannot enter the challenge except under the "Just for Fun" category.
* Each entrant shall indemnify, defend, and hold JoshSoftware Pvt. Ltd. (who has sponsored the domain and is the organizer of these challenges) harmless from any third party claims arising from or related to that entrant's participation in the Challenge. In no event shall JoshSoftware Pvt. Ltd. be liable to an entrant for acts or omissions arising out of or related to the Challenge or that entrant's participation in the Challenge.
* Odds of winning depend on the number and quality of entries received. 
* All taxes, including income taxes, are the sole responsibility of the winners. 
* No prize substitution is permitted.
* Create a zip of your Go source code and test cases and send the zip file to **golangchallenge [at] gmail.com before 18th of May 2015 (6 am IST). Use [this link](http://www.worldtimeserver.com/convert_time_in_IN.aspx?y=2015&mo=5&d=18&h=6&mn=0) to find the equivalent time in your city/country**. No new solutions will be accepted after that. In the email mention **your full name, country of residence, twitter or GitHub id (if any) and participating under which category - Just participating | Participating and exploring further | Just for Fun | Anonymous entry**. We are accepting anonymous submissions and will evaluate them too but then these participants are not eligible for the prizes. 
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

If you have any questions about this challenge, please join the [golang-challenge channel on slack](http://t.co/n6EesY9Mmv) and ask your questions with the tag @sausheong so that the challenge author is aware of your question(s) and can reply to the same. This is a room for people who are going to participate in the Go Challenge. You can also send us an email at golangchallenge [at] gmail.com

#### Evaluators

[Nathan Youngman](https://twitter.com/nathany) had set the guidelines for evaluation for the first Go Challenge. Subsequently [Dominik Honnef](https://twitter.com/dominikhonnef) modified the guidelines based on his experience as an evaluator for the first challenge. [Akshay Deo](https://twitter.com/akshay_deo), [Austin Riendeau](https://github.com/apriendeau), [Cory LaNou](https://twitter.com/corylanou), [Gautam Dey](https://github.com/gdey), [Jyotiska NK](https://twitter.com/jyotiska_nk), [Kevin Gillette](https://twitter.com/kevingillette) and [Pravin Mishra](https://twitter.com/pravinmishra88) have agreed to go through all the submitted solutions of a challenge. They will comment and rank these solutions.

#### Best Solution

The author of the Go Challenge will decide the best five solutions. The author shall have the sole authority and discretion to select the award recipients. 

#### Notification

The winning entries will be announced here on this blog. The winners will be sent their prizes by email/postal mail.

#### Prizes

The author of the challenge will select 5 winners.

Here are some great prizes provided by our sponsors for the event.

_Winner 1_:

* [Anand D N](https://twitter.com/Wanderer140) - [Essential-Go screencast](https://www.kajabinext.com/marketplace/courses/1-essential-go)
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
* [O'Reilly](http://www.oreilly.com/) - An eBook [Introduction to Go Programming](http://shop.oreilly.com/product/0636920035305.do)
* [Packt Publishing](https://www.packtpub.com/) - A print book [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [RainingClouds](http://rainingclouds.com/#!/) - An eBook [Level Up Your Web Apps With Go](http://shop.oreilly.com/product/9780992461294.do)
* [SoStronk](https://www.sostronk.com/) - [Counter-Strike: Global Offensive](http://store.steampowered.com/app/730/) game. You will need to have a free [Steam account](https://store.steampowered.com/join/?) to receive this gift.
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

_Winner 2_:

* [Anand D N](https://twitter.com/Wanderer140) - [Essential-Go screencast](https://www.kajabinext.com/marketplace/courses/1-essential-go)
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
