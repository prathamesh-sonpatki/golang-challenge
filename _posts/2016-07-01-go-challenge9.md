---
layout: post
title: Go Challenge - 9
tags: [go challenge, golang]
published: false
---

#### The July 2016 Go Challenge for developers (newbies included)

#### Aaron Cruz: Author of the 9th Go Challenge

<img align="right" src="/images/aaron-cruz.jpg" height="200" width="200" alt="Aaron Cruz" title="Aaron Cruz" style="border:5px solid black" />
The 9th Go Challenge author, Aaron Cruz, lives in the suburbs of Vienna, Austria but is a native of the suburbs of Seattle. In his former life he was a shepherd, a cheesemaker and a sous chef. Now he is freelancing, building native iOS and Android apps and their respective API's. In his spare time, he organizes a range of user groups in Vienna. If you get him started talking about food, he may never stop. He spoke at GopherConIndia 2015 and 2016.

Aaron has this to say about the challenge:

> ""

--- 

#### The Go Challenge 9

##### Nothin' But a Go Thang

##### Preamble

I grew up with Hip Hop. It connected me with a culture that seemed very alien, having grown up in the suburb of a suburb in Northwestern USA. Hip Hop changed dramatically over the years but one thing that stayed constant was story telling.

Here are some samples of some of my favorites over the decades starting from my youth to the present.

80s Eric B. & Rakim - I Ain't No Joke
<iframe width="420" height="315" src="https://www.youtube.com/embed/2TN-kDEKxF0" frameborder="0" allowfullscreen></iframe>

**The Goal of the challenge**

The goal of this challenge is to implement a Sudoku solver.

**Requirements of the challenge**

Your program should read a puzzle of this form from standard input:

```
1 _ 3 _ _ 6 _ 8 _
_ 5 _ _ 8 _ 1 2 _
7 _ 9 1 _ 3 _ 5 6
_ 3 _ _ 6 7 _ 9 _
5 _ 7 8 _ _ _ 3 _
8 _ 1 _ 3 _ 5 _ 7
_ 4 _ _ 7 8 _ 1 _
6 _ 8 _ _ 2 _ 4 _
_ 1 2 _ 4 5 _ 7 8
```

And it should write the solution to standard output:

```
1 2 3 4 5 6 7 8 9
4 5 6 7 8 9 1 2 3
7 8 9 1 2 3 4 5 6
2 3 4 5 6 7 8 9 1
5 6 7 8 9 1 2 3 4
8 9 1 2 3 4 5 6 7
3 4 5 6 7 8 9 1 2
6 7 8 9 1 2 3 4 5
9 1 2 3 4 5 6 7 8
```

It should reject malformed or invalid inputs and recognize and report puzzles that cannot be solved.

(Incidentally, the puzzle above makes a nice test case, because the solution is easy to validate by sight.)

**Bonus features**:

* Print a rating of the puzzle's difficulty (easy, medium, hard). This rating should roughly coincide with the ratings of shown by sites like [Web Sudoku](http://www.websudoku.com/).
* Implement a puzzle generator that produces a puzzle of the given difficulty rating.
* Maximize the efficiency of your program. ([Write a benchmark](http://dave.cheney.net/2013/06/30/how-to-write-benchmarks-in-go).)
* Write test cases, and use the [cover tool](https://blog.golang.org/cover) to make sure your tests are thorough.
(I found a bug in both my implementation and a test case when I checked the coverage.)
* Use a non-obvious technique, like Knuth's "Dancing Links" or something of your own invention.

**Hints**

* For an elegant and efficient representation of the puzzle, try using an array (not a slice).
* Recursion can dramatically simplify your implementation.

---

#### Challenge Rules and how to enter the Go Challenge?

By participating in this challenge, you agree to be bound by the Challenge Rules below:

* The Challenge is open to individuals.
* Evaluators cannot enter the challenge except under the "Just for Fun" category.
* Each entrant shall indemnify, defend, and hold JoshSoftware Pvt. Ltd. (who has sponsored the domain and is the organizer of these challenges) harmless from any third party claims arising from or related to that entrant's participation in the Challenge. In no event shall JoshSoftware Pvt. Ltd. be liable to an entrant for acts or omissions arising out of or related to the Challenge or that entrant's participation in the Challenge.
* Odds of winning depend on the number and quality of entries received. 
* All taxes, including income taxes, are the sole responsibility of the winners. 
* No prize substitution is permitted.
* Create a zip of your Go source code and test cases and send the zip file to **golangchallenge [at] gmail.com before 24th of November 2015 (6 am IST)**. Use [this link](http://www.worldtimeserver.com/convert_time_in_IN.aspx?y=2015&mo=11&d=24&h=6&mn=0) to find the equivalent time in your city/country. No new solutions will be accepted after that. In the email mention **your full name, country of residence, twitter or GitHub id (if any) and participating under which category - Just participating or Participating and exploring further or Just for Fun or Anonymous entry**. We are accepting anonymous submissions and will evaluate them too but then these participants are not eligible for the prizes. 
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
* [Cube Root Software](http://cuberoot.in/) - An eBook [Functional Programming for the Object-Oriented Programmer](https://leanpub.com/fp-oo)
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [Manning Publications Co.](http://manning.com/) - Two eBooks [Go Web Programming](http://www.manning.com/chang/) and [Go in Action](http://www.manning.com/ketelsen/)
* [Packt Publishing](https://www.packtpub.com/) - A print book [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)

_Winner 2_:

* [Anand D N](https://twitter.com/Wanderer140) - An eBook: [Mastering Go Web Services](http://shop.oreilly.com/product/9781783981304.do)
* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [Manning Publications Co.](http://manning.com/) - One eBook [Go Web Programming](http://www.manning.com/chang/)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)

#### Challenge Solutions

All the solutions submitted by the participants will be available **[here](https://github.com/golangchallenge/GCSolutions)** after the challenge ends.

#### Sponsors

This challenge's sponsors are: [Anand D N](https://twitter.com/Wanderer140), [Apcera](https://www.apcera.com/), [Cube Root Software](http://cuberoot.in/), [InfluxDB](http://influxdb.com/), [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/), [Manning Publications Co.](http://manning.com/), [Packt Publishing](https://www.packtpub.com/) and [Qwinix Technologies](http://www.qwinixtech.com/).

#### Credit

* The Gopher character is based on the Go mascot designed by Renée French and copyrighted under the Creative Commons Attribution 3.0 license.
* [GitHub](https://github.com/) for the yearly sponsorship of a [GitHub Bronze Organisation plan](https://github.com/pricing) for the Go Challenge.
* The Go Challenge is being organized by [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/) with help from the Go community.
