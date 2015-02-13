---
layout: post
title: Go Challenge 1
published: false
---

#### The world's first monthly Go Challenge for developers (newbies included) is now live!

<img align="right" src="http://rubylearning.com/images/m_aimonetti.jpg" height="200" width="200" alt="Matt Aimonetti" title="Matt Aimonetti" />
The first Go Challenge's author is [Matt Aimonetti](http://matt.aimonetti.net/) who is the CTO and co-founder of [Splice](https://splice.com/), a technology platform for music creators which streamlines the fragmented process of creating and sharing music, freeing musicians to spend their time and energy on the creative process. Long before Splice, Matt was a former sound engineer who tried his hand as an artist before transitioning to full time programming working for companies such as Sony PlayStation and LivingSocial. Matt has been active in the Open Source community for many years developing or contributing to many projects (Merb, Rails, MacRuby and many more), he also wrote a [free book about Go](http://www.golangbootcamp.com/) and is a published tech author for O'Reilly. Matt is based in Santa Monica, California.

Matt has this to say about the challenge:

> Very often developers just need an excuse to learn a new language or develop their own skills. The Go challenge is a great opportunity to work on a low-pressure, isolated, fun challenge and hopefully learn a lot. Getting out of the day to day programmer routine is an awesome way to challenge your brain and become a better developer.

--- 

#### The Go Challenge 1

This morning I took my daughter Giana to my secret lab to show her the various inventions I built over the years. That's when I realized that the awesome drum machine prototype I designed in the 90s had disappeared!!! The only related things I could find were printouts of the patterns I had created on the device as well as backups saved on floppy disks. Here are the printed patterns:

```
pattern_1.splice
Saved with HW Version: 0.808-alpha
Tempo: 120
(0) kick     |x---|x---|x---|x---|
(1) snare    |----|x---|----|x---|
(2) clap     |----|x-x-|----|----|
(3) hh-open  |--x-|--x-|x-x-|--x-|
(4) hh-close |x---|x---|----|x--x|
(5) cowbell  |----|----|--x-|----|
```

```
pattern_2.splice
Saved with HW Version: 0.808-alpha
Tempo: 98.4
(0) kick    |x---|----|x---|----|
(1) snare   |----|x---|----|x---|
(3) hh-open |--x-|--x-|x-x-|--x-|
(5) cowbell |----|----|x---|----|
```

```
pattern_3.splice
Saved with HW Version: 0.808-alpha
Tempo: 118
(40) kick    |x---|----|x---|----|
(1) clap     |----|x---|----|x---|
(3) hh-open  |--x-|--x-|x-x-|--x-|
(5) low-tom  |----|---x|----|----|
(12) mid-tom |----|----|x---|----|
(9) hi-tom   |----|----|-x--|----|
```

```
pattern_4.splice
Saved with HW Version: 0.909
Tempo: 240
(0) SubKick	      |----|----|----|----|
(1) Kick	      |x---|----|x---|----|
(99) Maracas	  |x-x-|x-x-|x-x-|x-x-|
(255) Low Conga	  |----|x---|----|x---|
```

```
pattern_5.splice
Saved with HW Version: 0.708-alpha
Tempo: 999
(1) Kick	|x---|----|x---|----|
(2) HiHat	|x-x-|x-x-|x-x-|x-x-|
```

I need your help to reverse engineer the binary format used by my drum machine and write a decoder so I will be able to implement a new drum machine, using Go this time!

You will find [attached 5 files](http://rubylearning.com/data/patterns.zip) with a pattern per file.

#### Some information about my legacy drum machine

My drum machine loads an audio sample per track allowing the programmer to schedule the playback of the sound. The scheduling of the playback is done using the concept of steps. A step is one of the parts of the measure that is being programmed (the programmed measure is known as a pattern). The measure (also called a bar) is divided in steps.

![measure.png](http://rubylearning.com/data/measure.png)

My drum machine only supports 16 step measure patterns played in 4/4 time. The measure is comprised of 4 quarter notes, each quarter notes comprised of 4 sixteenth notes and each sixteenth note corresponds to a step.
If all these music terms are confusing, don't worry, just know that the drum machine uses grid of 16 parts to let you trigger a sound. We have one sound per track and each track can be programmed independently. Each part is called a step. The speed of the playback is based on the tempo AKA bpm.

Taking an example from the printouts above:
```
(40) kick |x---|----|x---|----|
```

means that we have a track called "kick" (id 40) with the sound output being triggered on the first and ninth steps.

#### Goal

The goal of this challenge is to write a binary decoder that given a binary backup, outputs the same printouts as shown above.

#### Requirements

* Only use standard libraries

#### Hints

* Look around to see how data is usually serialized/encoded.
* Become familiar with encoding/binary package.
* ```hex.Dump()``` is very useful when debugging binary data.
* Think about the various permutations of data, imagine what other patterns could look like.

#### I don't know where to start :(

The first step is to reverse engineer the binary file format. Look at the hex value to see if you can detect patterns. Binary data usually contains some sort of headers, then the encoded data. You should expect to find the data described in the printouts:

* version
* tempo
* track with each track containing
  * id
  * name
  * 16 steps

Then you need to write a decoder that takes one of the provided binary files and
extracts/prints the data.

#### Go further (optional, not evaluated for the challenge)

Add more cowbell, reading the binary format is one thing, being able to generate/modify the data is even more fun. Take a pattern of your choosing and add more cowbell!

---

#### How to Enter the Go Challenge ?

* Read the **Challenge Rules** located next on this page. By participating in this challenge, you agree to be bound by these Challenge Rules.
* Create a [secret gist](https://gist.github.com/) of your code (using language Go) and **share the link with satish [at] joshsoftware.com before the 16th of the month**. No new solutions will be accepted after that. Also send **your photo, country of residence, twitter id and any explanation if needed**.
* On the 16th of the month at [6 am IST](http://www.worldtimeserver.com/convert_time_in_IN.aspx?y=2015&mo=3&d=16&h=6&mn=0), all the solutions will be thrown open for [everyone to see, comment upon and cast votes](https://groups.google.com/d/forum/go-challenge). 

#### Challenge Rules

* The Challenge is open to individuals.
* You maintain ownership of all code you submit and can release it under an open source license or keep it private after the challenge.
* Each entrant shall indemnify, defend, and hold JoshSoftware Pvt. Ltd. (who has sponsored the domain and is the organizer of these challenges) harmless from any third party claims arising from or related to that entrant’s participation in the Challenge. In no event shall JoshSoftware Pvt. Ltd. be liable to an entrant for acts or omissions arising out of or related to the Challenge or that entrant's participation in the Challenge.
* Odds of winning depend on the number and quality of entries received. 
* All taxes, including income taxes, are the sole responsibility of winners. 
* No prize substitution is permitted. 

#### Questions?

If you have any doubts / questions about this challenge, please post them in our **[forum](https://groups.google.com/forum/#!forum/go-challenge)** and the author will reply asap.

#### Evaluators

[Nathan Youngman](http://www.gophercon.in/blog/2014/11/06/nathan/) has agreed to set guidelines for evaluation. [Jacques Fuentes](https://twitter.com/jpfuentes2), [Jiahua Chen](http://about.me/unknwon), [Jyotiska NK](https://twitter.com/jyotiska_nk), [Niket Patel](https://twitter.com/nexneo), [Nishant Modak](https://www.linkedin.com/in/modak), [Piyush Verma](https://twitter.com/meson10) and [Pravin Mishra](https://twitter.com/pravinmishra88) have all agreed to go thro' all the submitted solutions of a challenge. They will comment and rank these solutions. More evaluators are welcome.

#### Best Solution

The author of the Go Challenge for the particular month will decide the best solution, with help from the evaluators. This author shall have the sole authority and discretion to select the award recipient(s). 

#### Notification

The winning entries will be announced here on this blog. The winners will be sent their prizes by email/postal mail.

#### Prizes

One prize will be awarded for the best solution selected by the author and a panel and the other will be for the best popular voted solution by the community.

Here are some great prizes provided by our sponsors for the event.

_Winner (selected by the author)_:

* [Anand D N](https://twitter.com/Wanderer140) - [Essential-Go screencast](https://www.kajabinext.com/marketplace/courses/1-essential-go)
* [Apcera](https://www.apcera.com/) - [Go Gopher Messenger Bag](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [Cube Root Software](http://cuberoot.in/) - An eBook [Go-The Standard Library](https://leanpub.com/go-thestdlib)
* [Helpshift](http://www.helpshift.com/) - An eBook [A Go Developer's Notebook](https://leanpub.com/GoNotebook)
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [John Sonmez](https://twitter.com/jsonmez) - An eBook [Soft Skills: The software developer's life manual](http://www.amazon.com/gp/product/1617292397/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=1617292397&linkCode=as2&tag=satishtalimsw-20&linkId=WGSAUMHIF2SVWJ7D)
* [Manning Publications Co.](http://manning.com/) - Two eBooks [Go Web Programming](http://www.manning.com/chang/) and [Go in Action](http://www.manning.com/ketelsen/)
* [NodePrime](http://www.nodeprime.com/) - An eBook [The Go Programming Language Phrasebook (Developer's Library)](http://goo.gl/mTwIOS)
* [O'Reilly](http://www.oreilly.com/) - An eBook [Go:Up and Running](http://shop.oreilly.com/product/0636920030638.do)
* [Packt Publishing](https://www.packtpub.com/) - A print book [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [RainingClouds](http://rainingclouds.com/#!/) - An eBook [Level Up Your Web Apps With Go](http://shop.oreilly.com/product/9780992461294.do)
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

_Winner (selected by the Go community)_:

* [Anand D N](https://twitter.com/Wanderer140) - [Essential-Go screencast](https://www.kajabinext.com/marketplace/courses/1-essential-go)
* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [Docker](https://www.docker.com/) - A ticket to [DockerCon 2015](http://www.dockercon.com/) in SFO, USA OR to DockerCon Europe (to be announced but probably in Dec. 2015).
* [Helpshift](http://www.helpshift.com/) - An eBook [A Go Developer's Notebook](https://leanpub.com/GoNotebook)
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [John Sonmez](https://twitter.com/jsonmez) - An eBook [Soft Skills: The software developer's life manual](http://www.amazon.com/gp/product/1617292397/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=1617292397&linkCode=as2&tag=satishtalimsw-20&linkId=WGSAUMHIF2SVWJ7D)
* [Manning Publications Co.](http://manning.com/) - Two eBooks [Go Web Programming](http://www.manning.com/chang/) and [Go in Action](http://www.manning.com/ketelsen/)
* [NodePrime](http://www.nodeprime.com/) - An eBook [The Go Programming Language Phrasebook (Developer's Library)](http://goo.gl/mTwIOS)
* [Packt Publishing](https://www.packtpub.com/) - An eBook [Building Your First Application with Go-Video](https://www.packtpub.com/application-development/building-your-first-application-go-video)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [RainingClouds](http://rainingclouds.com/#!/) - An eBook [Level Up Your Web Apps With Go](http://shop.oreilly.com/product/9780992461294.do)
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

Anyone can a get 42% off on the price of the following eBooks from [Manning Publications Co.](http://manning.com/):

* [Go Web Programming](http://www.manning.com/chang/) - Use discount code: **cftw15go**
* [Go in Action](http://www.manning.com/ketelsen/) - Use discount code: **cftw15go**

Also, anyone can a get 20% off on the price of the following print and / or eBooks from [Packt Publishing](https://www.packtpub.com/):

* [Building Your First Application with Go-Video](https://www.packtpub.com/application-development/building-your-first-application-go-video) - Use discount code: **20%byfag20**
* [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go) - Use discount code: **20%mcig20**
* [Go Programming Blueprints](https://www.packtpub.com/application-development/go-programming-blueprints) - Use discount code: **20%gpbs20**

#### Winner Interviews

After a winner wins the monthly challenge, he/she would be interviewed by [Sourcegraph](https://sourcegraph.com/) and the interview will be published on their [blog](https://sourcegraph.com/blog).

#### Sponsors

This challenge's sponsors are: [Anand D N](https://twitter.com/Wanderer140), [Apcera](https://www.apcera.com/), [CoreOS](https://coreos.com/), [Cube Root Software](http://cuberoot.in/), [DigitalOcean](https://www.digitalocean.com/), [Docker](https://www.docker.com/), [GopherCasts](https://gophercasts.io/), [Helpshift](http://www.helpshift.com/), [InfluxDB](http://influxdb.com/), [John Sonmez](https://twitter.com/jsonmez), [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/), [Manning Publications Co.](http://manning.com/), [NodePrime](http://www.nodeprime.com/), [O'Reilly](http://www.oreilly.com/), [Packt Publishing](https://www.packtpub.com/), [Qwinix Technologies](http://www.qwinixtech.com/), [RainingClouds](http://rainingclouds.com/#!/) and [Sourcegraph](https://sourcegraph.com/).

#### Credit

* The Gopher character is based on the Go mascot designed by Renée French and copyrighted under the Creative Commons Attribution 3.0 license.
* The Go Challenge is being organized by [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/) with help from the Go community.
