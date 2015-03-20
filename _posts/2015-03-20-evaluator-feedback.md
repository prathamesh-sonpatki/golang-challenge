---
layout: post
title: Feedback on the Go Challenge solutions
tags: [go challenge, golang]
---

#### About Evaluator Dominik Honnef

<img align="right" src="/images/dominik-honnef.png" alt="Dominik Honnef" title="Dominik Honnef" style="border:5px solid black" />
I've been programming for half my life, ever since my childhood. Having started in VB6 and PHP, I quickly worked my way towards Ruby and then finally Go. Along the way, I've always tried to contribute to open source in one way or another, but Go finally spawned the kind of down to earth, no nonsense community I feel comfortable in.

#### Dominik's feedback to the Go Challenge 1 participants

Reviewing almost 90 different solutions to the same problem revealed a lot of very common mistakes.

I think the most important mistake was that people didn't keep it simple.

Don't split your solution into 10 files. Not counting tests, this challenge took about 200 lines to solve. Then why would we need for example a file `track.go`, that only contains the definition of the `Track` struct? Java programmers are used to the rule of "one class per file", and so are Ruby programmers. But in Go, we prefer grouping code by their purpose. A pattern and a track belong to the same semantic unit, and can go in the same file. Decoding those Splice files is a semantic unit, thus decoding can go into a file, too. It doesn't need to be split into files for decoding the header, the track, and a utility for finding a null byte. If I want to read how the decoding works, I want to read it top to bottom; I don't want to jump between files constantly, especially if I first have to find out which file is the next file to read.

On that note, however: Do use multiple files when it makes sense. The template for the challenge came with two files: `decoder.go` and `drum.go` – and almost nobody even touched `drum.go`. Now, if all you wanted to do was decode Splice files, fine, you could've deleted `drum.go` – but we also wanted to print those patterns, and the challenge hinted at the fact that people would also want to encode those files, or play them. At that point it is natural to have code that is common between the different units in a separate file. As such, the `Pattern` and `Track` types, as well as their `String` methods, should've gone into the `drum.go` file, so that `decoder.go` could focus on the actual decoding.

Don't add extra types if you don't need them – a `type Step bool` has no benefit over a plain `bool` if your type doesn't at least have a method on it. It just adds complexity for no gain.

Streaming is a beautiful concept. Go embraces the `io.Reader` and `io.Writer` interfaces, and a lot of code is built on those. That includes `encoding/binary`, which everybody used. The `encoding/binary` package makes it incredibly easy to read bytes from an `io.Reader` and turn them into meaningful data, such as floats, or structs. It is quite unfortunate, then, that a lot of people first read the whole file into memory. Most people did this so they could operate on a `[]byte`, but they didn't save anything in terms of complexity. Some people, after reading the file into memory, realised that `encoding/binary` works best with an `io.Reader`, so what did they do? They wrapped their `[]byte` in a `bytes.Reader`… Instead of just using the file they opened as what it is: an `io.Reader`. I strongly suggest that people read ["Crossing Streams: a Love Letter to
io.Reader" by Jason Moiron](http://jmoiron.net/blog/crossing-streams-a-love-letter-to-ioreader/) to understand the beauty of `io.Reader`.

Get to know your standard library. Splice files encode their length in the header, and may contain trailing data. That's why you must abort reading after N bytes. Most people solved that by manually counting bytes. When they read a float32, they added 4 to an int. When they read 16 steps, they added 16 to an int, and so on. But there's a way simpler solution to this: using `io.LimitedReader` – a reader that has a maximum length and wraps an existing reader. Together with the earlier advice of using the `io.Reader` directly, this would've eliminated a lot of code.

Errors are values. Those of you who did use the `io.Reader`, instead of reading everything into a `[]byte`, had a lot of error checking. Everytime they read something, they had to check for an error. That's a lot of noise. It can be avoided though, for example by using a sticky error – wrap the reader in a custom reader that remembers the last error it encountered. You can then just parse the entire file, pretending errors don't happen, and at the end you check a single struct field, which contains the first error that occured, if any. Here I strongly suggest you read ["Errors are values" by Rob Pike](http://blog.golang.org/errors-are-values).

Don't leak implementation details. A track has a name, and 16 beats that might be on or off. What type do we use for storing binary states? Booleans. How were beats stored in the file? One byte per beat. What type do we use for storing binary states? Still booleans. Just because the file contains 16 bytes, doesn't mean that our `Track` type should contain a `[16]byte` – It should be a `[16]bool`. Or maybe even a `[]bool`. The user of a `Track` doesn't care about the raw bytes in a file. He might not even have read the track from a file. He cares about beats and their on/off state. (And yes, you could've used a uint16 to encode 16 beats more efficiently, but now your API is going to be more complex, too. Did you really need the extra space
efficiency?)

Don't write code to pass tests, write code to solve the problem. Pattern 5 had extra data at the end of the file that you weren't supposed to parse (it looked kind of like a second Splice file). Of course, the correct solution was to use the encoded file length. However, a lot of people didn't find the length, and that's fine, there's still ways to work around it. What is not fine, however, is to read a track and check if its ID is "SPLI" and abort the loop. Of course it passed the tests, but was it correct? Of course not. There could've been any other kind of data in that file, too. It could've even looked like a valid track. Or maybe our Splice file wasn't supposed to end there and it was corrupted instead. Solve the problem, not the tests. Tests are rarely complete. Any test can be passed by hard-coding the expected inputs and outputs.

I'll end this with a short list of other issues I encountered that don't deserve their own lengthy prose:

- The "SPLICE" bytes aren't useless – check for them to see if your file really is a Splice file.
- My name is Dominik. It's not DominikWhoHasAFatherAndAMother. Variables shouldn't be named like that, either. Go read
  [Notes on Programming in C](http://doc.cat-v.org/bell_labs/pikestyle).
- No byte was useless, every byte had a meaning. Only the version was padded.
- `fmt.Sprintf` worked well, you didn't need text/template.
- Simple code is good. Don't add extra features that have nothing to do with the problem.
- Readability is key. `gofmt` is a thing. So are `golint` and `go vet`.
- There's a thing called "short reads". `Read` is allowed to return less bytes than fit in the buffer, without it being an error. You probably wanted `io.ReadFull`.

#### Discussion 

Please join the [golang-challenge channel](http://t.co/n6EesY9Mmv) on slack if you want to discuss this blog post. This is a room for people who are going to participate / have participated in the Go Challenge.

