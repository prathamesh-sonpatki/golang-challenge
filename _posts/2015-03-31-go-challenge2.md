---
layout: post
title: Go Challenge 2
tags: [go challenge, golang]
---

![update.jpg](/images/update.jpg)

* This challenge ends in 2 days from now.

#### The April 2015 Go Challenge for developers (newbies included)

#### Guillaume J. Charmes: Author of the second Go Challenge

<img align="right" src="/images/guillaume-j-charmes.jpg" height="200" width="200" alt="Guillaume J. Charmes" title="Guillaume J. Charmes" style="border:5px solid black" />
The second Go Challenge author is [Guillaume J. Charmes](https://twitter.com/charme_g). French first, software developer second. He loves to travel and used to live in France, China, Russia, Réunion, San Francisco, Chicago and Miami. He also likes to travel between technologies and languages: He jumped from C and ASM to PHP to fall into Python to then migrate to Go with some sides of Ruby. He is coming from a low-level ASM/C background which he uses to teach as well as for web security. 

He started using Go in 2009 and fell in love with its syntax and concurrency model. He joined dotCloud, Inc. where he was the only Go developer for a while. This is when they started Docker..., in Go. Arrived to Docker 1.0, he moved on to Citrix, Inc. under the sun of Florida where he helps the moving process from Ruby to Go.

Guillaume has this to say about the challenge:

> "Data security is a very important matter and this challenge is a good way to dive in with the `NaCl` package and leverage the power of Go interfaces to implement a clean solution over the network."

--- 

#### The Go Challenge 2

##### Can you help me secure my company’s data transmission?

Last week, our competitor released a feature that we were working on in secret. We suspect that they are spying on our network. Can you help us prevent our competitor from spying on our network?

#### To get started

Check out the two files **main.go** and **main_test.go** [here](https://gist.github.com/creack/333f89f6aec5b789c1a0). These files are the starting point for this challenge.

![update.jpg](/images/update.jpg)

**3rd April 2015**: Guillaume has made 2 changes to the test files:

* The first change is minor and concerns Window user with dual stack. He has changed the `net.Listen("tcp", ":0")` to `net.Listen("tcp", "127.0.0.1:0")`. This shouldn't change anything for most people.
* The second is more problematic and would impact people using `io.Copy`. In TestReadWritePing, he has moved the `w.Close()` in the writing goroutine just like in the other tests.

#### Goal of the challenge

In order to prevent our competitor from spying on our network, we are going to write a small system that leverages [NaCl](http://nacl.cr.yp.to/) to establish secure communication. **NaCl** is a crypto system that uses a public key for encryption and a private key for decryption.

Your goal is to implement the functions in **main.go** and make it pass the provided tests in **main_test.go**.

#### Steps involved

The first step is going to be able to generate the public and private keys. Next, we want to create an `io.Writer` and `io.Reader` that will allow us to automatically encrypt/decrypt our data.

##### Part 1

Implement the following helpers that will return our NACL Reader / Writer.

```
func NewSecureReader(r io.Reader, priv, pub *[32]byte) io.Reader
func NewSecureWriter(w io.Writer, priv, pub *[32]byte) io.Writer
```

##### Part 2

Now that we can encrypt/decrypt message locally, it would be interesting to do so over the network!

We are going to write a server that will exchange keys with the client in order to establish a secure communication.

In order to be able to encrypt/decrypt, we need to perform a key exchange upon connection.

For the sake of the exercise, performing the key exchange in plain text is acceptable. (In a production system, it would not be acceptable due to MITM risk!)

Unfortunately, everybody has already left for the day, so let's write a secure echo server so we can test!

In order to test our echo server, we can do:

```
$> ./challenge2 -l 8080&
$> ./challenge2 8080 “hello world”
hello world
```

#### Requirements of the challenge

* Use the latest version of Go i.e. version 1.4.2
* Use only standard library and package(s) under `golang.org/x/crypto/nacl`.

#### Hints

* We consider that our messages will always be smaller than 32KB
* Most of the elements involved for encryption/decryption have fixed length
* `encoding/binary` can be useful for the variable parts
 
#### Further exploration

If you have liked this challenge, you can keep programming **outside** the main challenge. You can:

* create an actual user interface. It would be nice if both side had a prompt and could send more than one message at a time.
* Handle multiple client and group chat
* Add compression

Please keep in mind that cryptography is a complex subject matter, with many very subtle risks and mistakes to make. While it makes for a fun exercise, inventing your own crypto systems for production use is usually not a good idea and should be left to a handful of very talented people.

---

#### Challenge Rules and how to enter the Go Challenge?

By participating in this challenge, you agree to be bound by the Challenge Rules below:

* The Challenge is open to individuals.
* Evaluators cannot enter the challenge except under the "Just for Fun" category.
* Each entrant shall indemnify, defend, and hold JoshSoftware Pvt. Ltd. (who has sponsored the domain and is the organizer of these challenges) harmless from any third party claims arising from or related to that entrant's participation in the Challenge. In no event shall JoshSoftware Pvt. Ltd. be liable to an entrant for acts or omissions arising out of or related to the Challenge or that entrant's participation in the Challenge.
* Odds of winning depend on the number and quality of entries received. 
* All taxes, including income taxes, are the sole responsibility of the winners. 
* No prize substitution is permitted. 
* Create a zip of your Go source code and send the zip file to **golangchallenge [at] gmail.com before 18th of April 2015 (6 am IST). Use [this link](http://www.worldtimeserver.com/convert_time_in_IN.aspx?y=2015&mo=4&d=18&h=6&mn=0) to find the equivalent time in your city/country**. No new solutions will be accepted after that. In the email mention **your full name, country of residence, twitter or GitHub id (if any) and participating under which category - Just participating | Participating and exploring further | Just for Fun | Anonymous entry**. We are accepting anonymous submissions and will evaluate them too but then these participants are not eligible for the prizes. 
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

If you have any questions about this challenge, please join the [golang-challenge channel on slack](http://t.co/n6EesY9Mmv) and ask your questions. This is a room for people who are going to participate in the Go Challenge. You can also send us an email at golangchallenge [at] gmail.com

#### Evaluators

[Nathan Youngman](https://twitter.com/nathany) had set the guidelines for evaluation for the first Go Challenge. Subsequently [Dominik Honnef](https://twitter.com/dominikhonnef) modified the guidelines based on his experience as an evaluator for the first challenge. [Akshay Deo](https://twitter.com/akshay_deo), [Austin Riendeau](https://github.com/apriendeau), [Cory LaNou](https://twitter.com/corylanou), [Damian Gryski](https://twitter.com/dgryski), [Dominik Honnef](http://dominik.honnef.co/), [Gautam Dey](https://github.com/gdey), [Jeff R. Allen](http://blog.nella.org/category/golang/), [Jiahua Chen](https://twitter.com/joe2010xtmf), [Jyotiska NK](https://twitter.com/jyotiska_nk), [Kevin Gillette](https://twitter.com/kevingillette), [Niket Patel](https://twitter.com/nexneo), [Pat Fogarty](https://github.com/patfogarty) and [Pravin Mishra](https://twitter.com/pravinmishra88) have agreed to go through all the submitted solutions of a challenge. They will comment and rank these solutions.

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

Also, anyone can a get 25% off on the price (valid till 31st March 2015) of the following print and / or eBooks from [Packt Publishing](https://www.packtpub.com/):

* [Building Your First Application with Go-Video](https://www.packtpub.com/application-development/building-your-first-application-go-video) - Use discount code: **byfag25**
* [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go) - Use discount code: **giccm25**
* [Go Programming Blueprints](https://www.packtpub.com/application-development/go-programming-blueprints) - Use discount code: **bgpg25**

#### Winner Interviews

After a winner wins the monthly challenge, he/she would be interviewed by [Sourcegraph](https://sourcegraph.com/) and the interview will be published on their [blog](https://sourcegraph.com/blog).

#### The Participants

There are three categories of participants. Most are just participating in the challenge; some have added more steps and some are participating "Just for Fun".

**Participating**

**Australia**

<ul>
<li><a href="https://github.com/beefsack" target="_blank">Michael Alexander</a></li>
<li><a href="https://github.com/peterstace" target="_blank">Peter Stace</a></li>
</ul>

**Brazil**

<ul>
<li><a href="https://github.com/kasa" target="_blank">Eduardo Kasa</a></li>
<li><a href="https://github.com/mathcunha" target="_blank">Matheus Cunha</a></li>
<li><a href="https://github.com/cupello" target="_blank">Rafael Cupello</a></li>
</ul>

**Canada**

<ul>
<li><a href="https://github.com/arianitu" target="_blank">Arianit Uka</a></li>
<li><a href="https://github.com/idawes" target="_blank">Ian Dawes</a></li>
<li><a href="https://github.com/kenpratt" target="_blank">Ken Pratt</a></li>
<li><a href="https://github.com/musiaht" target="_blank">Sum Thai</a></li>
</ul>

**China**

<ul>
<li><a href="https://twitter.com/iwangbin" target="_blank">Wang Bin</a></li>
</ul>

**Costa Rica**

<ul>
<li><a href="https://github.com/mem" target="_blank">Marcelo Magallon</a></li>
</ul>

**Denmark**

<ul>
<li><a href="https://github.com/stengaard" target="_blank">Brian Stengaard</a></li>
<li><a href="https://github.com/pstibrany" target="_blank">Peter Štibraný</a></li>
<li><a href="https://github.com/homburg" target="_blank">Thomas B Homburg</a></li>
</ul>

**France**

<ul>
<li><a href="https://github.com/briv" target="_blank">Blaise Rivet</a></li>
<li><a href="https://github.com/rakoo/" target="_blank">Matthieu Rakotojaona</a></li>
<li><a href="https://github.com/blizarre" target="_blank">Simon Marache-Francisco</a></li>
<li><a href="https://twitter.com/schorlet" target="_blank">Stéphane Chorlet</a></li>
</ul>

**Germany**

<ul>
<li><a href="https://twitter.com/alpe1" target="_blank">Alexander Peters</a></li>
<li><a href="https://github.com/andrewslotin" target="_blank">Andrey Slotin</a></li>
<li><a href="https://github.com/giuliop" target="_blank">Giulio Pizzini</a></li>
<li><a href="https://github.com/cryptix" target="_blank">Henry Bubert</a></li>
<li><a href="https://twitter.com/tobischo" target="_blank">Tobias Schoknecht</a></li>
</ul>

**Greece**

<ul>
<li><a href="https://github.com/0xDiBa" target="_blank">Dimitris Bachtis</a></li>
</ul>

**India**

<ul>
<li><a href="https://github.com/jijeshmohan" target="_blank">Jijesh Mohan</a></li>
<li><a href="https://github.com/mantishK" target="_blank">Kumar Mantesh</a></li>
<li><a href="https://github.com/copyninja" target="_blank">Vasudev Kamath</a></li>
</ul>

**Indonesia**

<ul>
<li><a href="https://github.com/gedex" target="_blank">Akeda Bagus</a></li>
<li><a href="https://twitter.com/peeyek" target="_blank">Bayu Aldi Yansyah</a></li>
<li><a href="https://github.com/yisiper" target="_blank">Christoper</a></li>
<li><a href="https://github.com/septiaji" target="_blank">Septiaji Purwono R.</a></li>
<li>William Shallum</li>
</ul>

**Ireland**

<ul>
<li><a href="https://twitter.com/_dan_w" target="_blank">Daniel Wakefield</a></li>
</ul>

**Italy**

<ul>
<li><a href="https://github.com/eraclitux" target="_blank">Andrea Masi</a></li>
<li><a href="https://github.com/FiloSottile" target="_blank">Filippo Valsorda</a></li>
</ul>

**Netherlands**

<ul>
<li><a href="https://github.com/rpkamp" target="_blank">Rémon van de Kamp</a></li>
</ul>

**Nigeria**

<ul>
<li><a href="https://twitter.com/abiosoft" target="_blank">Abiola Ibrahim</a></li>
</ul>

**Norway**

<ul>
<li><a href="https://github.com/flexd" target="_blank">Kristoffer Berdal</a></li>
</ul>

**Romania**

<ul>
<li><a href="https://github.com/lcosmin" target="_blank">Cosmin Luță</a></li>
</ul>

**Russia**

<ul>
<li><a href="https://github.com/paystee" target="_blank">Anton Tereshchenkov</a></li>
</ul>

**Slovenia**

<ul>
	<li><a href="https://github.com/zobo" target="_blank">Damjan Cvetko</a></li>
</ul>

**Switzerland**

<ul>
<li><a href="https://www.linkedin.com/in/eagm74" target="_blank">Alejandro Garcia</a></li>
</ul>

**UK**

<ul>
<li><a href="https://github.com/saracen" target="_blank">Arran Walker</a></li>
<li><a href="https://github.com/e-dard" target="_blank">Edward Robinson</a></li>
<li><a href="https://github.com/ichinaski/" target="_blank">Iñigo Lopez</a></li>
<li><a href="https://twitter.com/MikeMunday" target="_blank">Michael Munday</a></li>
<li>Primrose Mbanefo</li>
</ul>

**Ukraine**

<ul>
<li><a href="https://github.com/edpelesh" target="_blank">Eduard Pelesh</a></li>
</ul>

**USA**

<ul>
<li><a href="https://github.com/mettledrum" target="_blank">Andrew Hoyle</a></li>
<li><a href="https://github.com/atongen" target="_blank">Andrew Tongen</a></li>
<li><a href="https://github.com/cretz/" target="_blank">Chad Retz</a></li>
<li><a href="https://github.com/cicavey" target="_blank">Christopher Cavey</a></li>
<li><a href="https://github.com/djoyahoy" target="_blank">Daniel Joyce</a></li>
<li><a href="http://www.codeforthought.net" target="_blank">Doug Cichon</a></li>
<li><a href="https://github.com/jamra" target="_blank">Jacob Amrany</a></li>
<li><a href="https://github.com/JJasonClark" target="_blank">Jason Clark</a></li>
<li><a href="https://twitter.com/TinSoldier6" target="_blank">Jason A. Gade</a></li>
<li><a href="https://github.com/jdeppe-pivotal" target="_blank">Jens Deppe</a></li>
<li><a href="https://github.com/jimdoescode" target="_blank">Jim Saunders</a></li>
<li><a href="https://github.com/jordan-wright" target="_blank">Jordan Wright</a></li>
<li><a href="https://github.com/jboverfelt" target="_blank">Justin Overfelt</a></li>
<li><a href="https://github.com/kevinjos" target="_blank">Kevin Schiesser</a></li>
<li><a href="https://github.com/ameske" target="_blank">Kyle Ames</a></li>
<li><a href="https://github.com/lukechampine" target="_blank">Luke Champine</a></li>
<li><a href="https://github.com/MarkMoudy" target="_blank">Mark Moudy</a></li>
<li><a href="https://github.com/nvanbenschoten" target="_blank">Nathan VanBenschoten</a></li>
<li><a href="https://twitter.com/nickmarrone" target="_blank">Nicholas Marrone</a></li>
<li><a href="https://github.com/rcarver" target="_blank">Ryan Carver</a></li>
<li><a href="https://twitter.com/Littledot1230" target="_blank">Sheng-Dean Chang</a></li>
<li><a href="https://github.com/trevorarjeski" target="_blank">Trevor Arjeski</a></li>
<li><a href="https://github.com/zmb3" target="_blank">Zac Bergquist</a></li>
<li><a href="https://github.com/zclark" target="_blank">Zach Clark</a></li>
<li><a href="https://github.com/lziest" target="_blank">Zi Lin</a></li>
</ul>

**Vietnam**

<ul>
<li><a href="https://github.com/elgris" target="_blank">Ivan Kirichenko</a></li>
<li><a href="https://github.com/nqv" target="_blank">Quoc Viet Nguyen</a></li>
</ul>
  
**Added more steps**

**Germany**

<ul>
<li><a href="https://github.com/husio" target="_blank">Piotr Husiatyński</a></li>
</ul>

**Mexico**

<ul>
<li><a href="https://github.com/jpadif" target="_blank">Josué Alejandro Padilla Fabián</a></li>
</ul>

**USA**

<ul>
<li><a href="https://github.com/zagzagal" target="_blank">Paul Schuster</a></li>
</ul>

**Just for Fun**

**India**

<ul>
  <li><a href="http://kidoman.io/" target="_blank">Karan Misra</a></li>
</ul>

**Liberia**

<ul>
  <li>Anonymous</li>
</ul>

**USA**

<ul>
  <li><a href="https://github.com/johnathanhowell" target="_blank">Johnathan Howell</a></li>
</ul>

#### Challenge Solutions

All the solutions submitted by the participants will be available **[here](https://github.com/GoChallenge/GCSolutions)** after the challenge ends.

#### The Winners

![winner.png](/images/winner.png)

#### Sponsors

This challenge's sponsors are: [Anand D N](https://twitter.com/Wanderer140), [Apcera](https://www.apcera.com/), [CoreOS](https://coreos.com/), [Crowd Interactive](http://www.crowdint.com/), [Cube Root Software](http://cuberoot.in/), [DigitalOcean](https://www.digitalocean.com/), [Docker](https://www.docker.com/), [GitHub](https://github.com/), [GopherCasts](https://gophercasts.io/), [Helpshift](http://www.helpshift.com/), [InfluxDB](http://influxdb.com/), [John Sonmez](https://twitter.com/jsonmez), [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/), [Manning Publications Co.](http://manning.com/), [NodePrime](http://www.nodeprime.com/), [O'Reilly](http://www.oreilly.com/), [Packt Publishing](https://www.packtpub.com/), [Qwinix Technologies](http://www.qwinixtech.com/), [RainingClouds](http://rainingclouds.com/#!/), [SoStronk](https://www.sostronk.com/) and [Sourcegraph](https://sourcegraph.com/).

#### Credit

* The Gopher character is based on the Go mascot designed by Renée French and copyrighted under the Creative Commons Attribution 3.0 license.
* [GitHub](https://github.com/) for the yearly sponsorship of a [GitHub Bronze Organisation plan](https://github.com/pricing) for the Go Challenge.
* The Go Challenge is being organized by [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/) with help from the Go community.
