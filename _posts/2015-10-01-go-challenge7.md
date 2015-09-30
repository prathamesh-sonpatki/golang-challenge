---
layout: post
title: Go Challenge - 7
tags: [go challenge, golang]
---

#### The October 2015 Go Challenge for developers (newbies included)

#### Francesc Campoy Flores: Author of the 7th Go Challenge

<img align="right" src="/images/francesc-campoy-flores.png" height="200" width="200" alt="Francesc Campoy Flores" title="Francesc Campoy Flores" style="border:5px solid black" />
The 7th Go Challenge author is Francesc Campoy Flores who joined the Go team in 2012 as Developer Advocate after several years as a Python and C++ developer. His mission is to make Go useful and fun.

Francesc has this to say about the challenge:

> "Preparing this challenge got me so excited about the support for OpenGL and simple audio primitives that I had to concentrate on writing the description rather than hacking on my own virtual piano.

> Event based applications are easily modeled using goroutines and channels, and I expect this project will be a chance for everyone to experiment with them."

--- 

#### The Go Challenge 7

##### A piano on your phone

##### Preamble

The latest version of Go 1.5 released last month includes, among many other cool things, experimental support for mobile platforms such as Android and iOS.

I have personally played around with the the golang.org/x/mobile packages and thought this challenge would be a great opportunity to see what great projects people could come up.


**Goals of the challenge**

The goal is simple: build a virtual piano for mobile devices.

The piano should display a set of keys (some white, some black) as in real traditional pianos (see image below). When the user presses a key a sound should be played. How and what exactly the key sounds is left to your choice and artistic freedom.

![piano-octave](/images/piano-octave.png)

**Requirements of the challenge**

The resulting application should:

* run on Android (at least),
* uses the [golang.org/x/mobile/gl](https://godoc.org/golang.org/x/mobile/gl) to display a set of keys,
* use the [golang.org/x/mobile/exp/audio](https://godoc.org/golang.org/x/mobile/exp/audio) package to generate sounds
* have some way for the user to act on what sound is generated

**Bonus features**:

* use complex interactions other than simple taps
* allow the user to save/export the music generated
* create a web page where users can show their skills
* provide a way for different musicians to colaborate/compete

**Hints**

There's multiple ways to generate audio. You can use audio files quite easily, but it would be much more creative to provide a way to generate sounds "from scratch" with [https://godoc.org/golang.org/x/mobile/exp/audio/al](https://godoc.org/golang.org/x/mobile/exp/audio/al).

---

#### Challenge Rules and how to enter the Go Challenge?

By participating in this challenge, you agree to be bound by the Challenge Rules below:

* The Challenge is open to individuals.
* Evaluators cannot enter the challenge except under the "Just for Fun" category.
* Each entrant shall indemnify, defend, and hold JoshSoftware Pvt. Ltd. (who has sponsored the domain and is the organizer of these challenges) harmless from any third party claims arising from or related to that entrant's participation in the Challenge. In no event shall JoshSoftware Pvt. Ltd. be liable to an entrant for acts or omissions arising out of or related to the Challenge or that entrant's participation in the Challenge.
* Odds of winning depend on the number and quality of entries received. 
* All taxes, including income taxes, are the sole responsibility of the winners. 
* No prize substitution is permitted.
* Create a zip of your Go source code and test cases and send the zip file to **golangchallenge [at] gmail.com before 27th of October 2015 (6 am IST). Use [this link](http://www.worldtimeserver.com/convert_time_in_IN.aspx?y=2015&mo=10&d=27&h=6&mn=0) to find the equivalent time in your city/country**. No new solutions will be accepted after that. In the email mention **your full name, country of residence, twitter or GitHub id (if any) and participating under which category - Just participating | Participating and exploring further | Just for Fun | Anonymous entry**. We are accepting anonymous submissions and will evaluate them too but then these participants are not eligible for the prizes. 
* We shall be publishing on this blog, a list of participant names. If you don't want your name to appear kindly mention the same in your email. 
* You are allowed to re-submit your code if you feel it is necessary.
* After the challenge is over, all submissions will be made available [online on GitHub](https://github.com/golangchallenge/GCSolutions) under the [BSD 3-Clause License](http://opensource.org/licenses/BSD-3-Clause) or the [GNU General Public License, version 3 - GPL-3.0](http://opensource.org/licenses/GPL-3.0) unless a participant has indicated that his/her solution should not be made public before the challenge ends.

#### How will the challenge be evaluated?

Entries will be evaluated by the challenge author and a team of evaluators.

#### Questions?

If you have any questions about this challenge, please join the [golang-challenge channel on slack](http://t.co/n6EesY9Mmv) and ask your questions. This is a room for people who are going to participate in the Go Challenge. You can also send us an email at golangchallenge [at] gmail.com

#### Evaluators

[Nathan Youngman](https://twitter.com/nathany) had set the guidelines for evaluation for the first Go Challenge. Subsequently [Dominik Honnef](https://twitter.com/dominikhonnef) modified the guidelines based on his experience as an evaluator for the first challenge. [Austin Riendeau](https://github.com/apriendeau), [Cory LaNou](https://twitter.com/corylanou), [Edd Robinson](https://github.com/e-dard), [Gautam Dey](https://github.com/gdey), [Jyotiska NK](https://twitter.com/jyotiska_nk), [Kevin Gillette](https://twitter.com/kevingillette) and [Pravin Mishra](https://twitter.com/pravinmishra88) have agreed to go through all the submitted solutions of a challenge. They will comment and rank these solutions.

#### Best Solution

The author of the Go Challenge will decide the best five solutions. The author shall have the sole authority and discretion to select the award recipients. 

#### Notification

The winning entries will be announced here on this blog. The winners will be sent their prizes by email/postal mail.

#### Prizes

The author of the challenge will select 2 winners and prizes will be awarded to them.

Here are some great prizes provided by our sponsors for the event.

_Winner 1_:

* [Apcera](https://www.apcera.com/) - [Go Gopher Messenger Bag](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [Cube Root Software](http://cuberoot.in/) - An eBook [Go-The Standard Library](https://leanpub.com/go-thestdlib)
* [Docker](https://www.docker.com/) - 1 ticket to DockerCon Europe in November.
* [GitHub](https://github.com/) - Free 1 year of a [Personal Micro Plan](https://github.com/pricing).
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [Manning Publications Co.](http://manning.com/) - Two eBooks [Go Web Programming](http://www.manning.com/chang/) and [Go in Action](http://www.manning.com/ketelsen/)
* [Packt Publishing](https://www.packtpub.com/) - A print book [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

_Winner 2_:

* [Anand D N](https://twitter.com/Wanderer140) - An eBook: [Mastering Go Web Services](http://shop.oreilly.com/product/9781783981304.do)
* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [Manning Publications Co.](http://manning.com/) - One eBook [Go Web Programming](http://www.manning.com/chang/)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

#### Winner Interviews

After a winner wins the monthly challenge, he/she would be interviewed by [Sourcegraph](https://sourcegraph.com/) and the interview will be published on their [blog](https://sourcegraph.com/blog).

#### Challenge Solutions

All the solutions submitted by the participants will be available **[here](https://github.com/golangchallenge/GCSolutions)** after the challenge ends.

#### Sponsors

This challenge's sponsors are: [Anand D N](https://twitter.com/Wanderer140), [Cube Root Software](http://cuberoot.in/), [Docker](https://www.docker.com/), [GitHub](https://github.com/), [InfluxDB](http://influxdb.com/), [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/), [Manning Publications Co.](http://manning.com/), [Packt Publishing](https://www.packtpub.com/), [Qwinix Technologies](http://www.qwinixtech.com/) and [Sourcegraph](https://sourcegraph.com/).

#### Credit

* The Gopher character is based on the Go mascot designed by Renée French and copyrighted under the Creative Commons Attribution 3.0 license.
* [GitHub](https://github.com/) for the yearly sponsorship of a [GitHub Bronze Organisation plan](https://github.com/pricing) for the Go Challenge.
* The Go Challenge is being organized by [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/) with help from the Go community.
