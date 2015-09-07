---
layout: post
title: Go Challenge - 6
tags: [go challenge, golang]
---

#### The September 2015 Go Challenge for developers (newbies included)

#### Steve Francia: Author of the 6th Go Challenge

<img align="right" src="/images/steve-francia.jpg" height="200" width="200" alt="Steve Francia" title="Steve Francia" style="border:5px solid black" />
The 6th Go Challenge author is Steve Francia who is responsible for two of the largest projects in Go (and open source); He's the Chief Operator of the [Docker](https://www.docker.com/) project and the creator of [Hugo](http://gohugo.io/), the most contributed-to community project in Go. He loves open source and is thrilled to be able to work on it full time, and then some. He has also created some of the most widely-used Go libraries, including [cobra](https://github.com/spf13/cobra), [viper](https://github.com/spf13/viper) and [nitro](https://github.com/spf13/nitro). In writing, Steve tweets as [@spf13](https://twitter.com/spf13), blogs at [spf13.com](http://spf13.com/) and has written a few books for O'Reilly. In person, he enjoys giving talks and workshops and spending time with the Go community around the world. When not coding, he is usually having fun outdoors with his wife and four children.

Steve has this to say about the challenge:

> "I thought it would be fun to play with Mazes. I don't really have any prior experiences with programming mazes and I learned a lot through this exercise. I hope you will enjoy it as well."

--- 

#### The Go Challenge 6

##### Daedalus & Icarus

##### Preamble

In Greek mythology, Daedalus was a skillful craftsman and artist. He is the father of Icarus, and the creator of the Labyrinth. This Go challenge will be unlike any previous one. You will be creating two bots which will compete head to head with all of the other participants.

**Bot 1. Daedalus**

![labyrinth](https://cloud.githubusercontent.com/assets/173412/9587928/39240f64-4ff3-11e5-81a4-1c3c3b53883e.jpg)

Daedalus's job is to create a challenging Labyrinth for his opponent (shadow Icarus) to solve. The Labyrinth must be 15 cells by 10 cells. Icarus will be place in a random location which will be accessible to the goal which is a set of wings. The Labyrinth must be fully enclosed and there must be a possible solution. Icarus must be located in a random location accessible to the treasure. The treasure (wings) must also be in a random location that is accessible to Icarus.

**Bot 2. Icarus**

![icarus-and-daedalus](https://cloud.githubusercontent.com/assets/173412/9587929/3927a93a-4ff3-11e5-93ef-63d572d719f7.jpg)

Icarus wakes up to find himself inside of a dark Labyrinth. Due to the darkness of the Labyrinth he can only see his immediate room and if there is a wall or not to the top, right, bottom and left. He takes one step and then can discover if his new cell has walls on each of the four sides.

**Goals of the challenge**

Your goal is to write a maze generator and a maze solver to go head to head against other bots.

The goal is to have your Icarus solve your opponents Labyrinth the fastest (lowest number of steps). Victory will require a cleverly crafted maze as well as a intelligent solver.

We will run a big tournament to determine who has created the best pair of Bots. Each round will consist of two entrants going head to head.

We will run 500 simulations between opponents and take the average number of steps taken to solve the labyrinth. The competitor with the lower average steps will win and go onto the next round.  

**Ground Rules**:

* Every maze generated must be solvable.
* Both Icarus and the treasure must be randomly placed.
* Mazes must be fully enclosed. The only way out is the treasure.
* Dynamic (shifting) mazes are not allowed. Once icarus wakes up the walls and treasure must be fixed.
* A wall needs to be set on both sides of neighboring cells. No one way walls.
* Mazes may have more than one correct solution.
* No cheating. Don't miscount steps or anything like that.

This is meant to be fun. The hope for this challenge is to get you thinking about how to write code in Go. We will be exposing you to some of the basic libraries you would use to write both command line applications and web services.

**Requirements of the challenge**

<img width="482" alt="maze" src="https://cloud.githubusercontent.com/assets/173412/9589016/95282588-4ff9-11e5-8b86-18c0e1d1f227.png">

You will be given incomplete source code for application which you must complete. The structure and scaffolding of the application is there for you already done, but the critical logic is missing.

You will communicate with your opponent bot over a REST API. A complete skeleton for the app structure will be provided to you to ensure every bot has the same flags & endpoints.

This challenge makes use of 3 libraries outside the standard library:

* [gin](https://github.com/gin-gonic/gin) : One of the many web frameworks available for Go. I particularly like the speed and interface Gin provides.
* [cobra](https://github.com/spf13/cobra) : A Commander for modern Go CLI interactions. Used by Google’s Kubernetes, RedHat’s Project Atomic, Docker, OpenShift, CoreOS’s Rocket, Parse, GiantSwarm & GopherJS
* [viper](https://github.com/spf13/viper) : A complete configuration solution for Go applications. It is designed to work within an application, and can handle all types of configuration needs and formats.

There are 4 different operations already defined for the program.

* a bare `labyrinth` will run a server and connect your client to it to solve it
* `labyrinth daedalus` will run a server
* `labyrinth icarus` will run a client
* `labyrinth author` will output your given name
* `labyrinth help` will output help for these commands and the flags they take.

You will need to make changes to at least 3 files to complete your task.

You will need to:

* Put your name in the `var AuthorName = "spf13"` line in commands/labyrinth.go file
* Write the `createMaze()` function in the commands/daedalus.go file
* Write the `solveMaze()` function in the commands/icarus.go file

You may (and likely will want to) make other changes to these files but keep the integrity of the API intact.

**Bonus features**:

The default behavior of the `labyrinth` program is to run a server and connect to it with a client thus creating and solving a maze. This is really helpful for testing.

There is an additional library provided that will do nice things like providing a few interfaces and a `printMaze(Maze)` function that will print the maze to the terminal in ascii.

**Hints**

[This site](http://www.astrolog.org/labyrnth/algrithm.htm) is a pretty good resource explaining different types of Mazes.

[Mazes for Programmers](http://www.amazon.com/Mazes-Programmers-Twisty-Little-Passages-ebook/dp/B013HA1UY4/ref=mt_kindle?_encoding=UTF8&me=) is also a helpful book.

**Special note for the evaluators**

Running `labyrinth daedalus` from competitor A and `labyrinth icarus --times 500` from competitor B is all that is needed for running a simulation.

---

#### Challenge Rules and how to enter the Go Challenge?

By participating in this challenge, you agree to be bound by the Challenge Rules below:

* The Challenge is open to individuals.
* Evaluators cannot enter the challenge except under the "Just for Fun" category.
* Each entrant shall indemnify, defend, and hold JoshSoftware Pvt. Ltd. (who has sponsored the domain and is the organizer of these challenges) harmless from any third party claims arising from or related to that entrant's participation in the Challenge. In no event shall JoshSoftware Pvt. Ltd. be liable to an entrant for acts or omissions arising out of or related to the Challenge or that entrant's participation in the Challenge.
* Odds of winning depend on the number and quality of entries received. 
* All taxes, including income taxes, are the sole responsibility of the winners. 
* No prize substitution is permitted.
* Git clone this [repo](https://github.com/golangchallenge/gc6). The cloned repo should be private, only accessible to you till the end of the challenge. You could use any of these [Free GitHub Alternatives for Private Repositories](http://toppersworld.com/top-10-free-github-alternatives-for-private-repositories/). You can keep pushing your code to this cloned private repo of yours.
* At the end of the challenge make your repo public and send us the URL to **golangchallenge [at] gmail.com on 15th of Sept 2015 (6 am IST). Use [this link](http://www.worldtimeserver.com/convert_time_in_IN.aspx?y=2015&mo=9&d=15&h=6&mn=0) to find the equivalent time in your city/country**. No new solutions will be accepted after that. In the email mention **your full name, country of residence, twitter or GitHub id (if any) and participating under which category - Just participating | Participating and exploring further | Just for Fun | Anonymous entry**. We are accepting anonymous submissions and will evaluate them too but then these participants are not eligible for the prizes. 
* We shall be publishing on this blog, a list of participant names. If you don't want your name to appear kindly mention the same in your email. 
* You are allowed to re-submit your code if you feel it is necessary.
* **Note**: Avoid making your private repo public till the end of the challenge; if your solution becomes available to the general public it might impact evaluation of your submission.
* After the challenge is over, all submissions will be made available [online on GitHub](https://github.com/golangchallenge/GCSolutions) under the [BSD 3-Clause License](http://opensource.org/licenses/BSD-3-Clause) or the [GNU General Public License, version 3 - GPL-3.0](http://opensource.org/licenses/GPL-3.0) unless a participant has indicated that his/her solution should not be made public before the challenge ends.

#### How will the challenge be evaluated?

Entries will be evaluated by the challenge author and a team of evaluators.

#### Questions?

If you have any questions about this challenge, please join the [golang-challenge channel on slack](http://t.co/n6EesY9Mmv) and ask your questions with the tag @spf13 so that the challenge author is aware of your question(s) and can reply to the same. This is a room for people who are going to participate in the Go Challenge. You can also send us an email at golangchallenge [at] gmail.com

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
* [Docker](https://www.docker.com/) - 1 ticket to DockerCon Europe in November.
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
