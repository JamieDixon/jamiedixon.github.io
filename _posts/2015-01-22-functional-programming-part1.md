---
layout: post
title:  "Functional Programming for the dysfunctional mind - Part I"
date:   2015-01-22 12:00:00
---

The science and art of choosing names for things is a well known conundrum. Some even say it's one of the few hard things in computer science. But then most of us who program wouldn't call ourselves scientists anyhow.

Words that have dual meanings are reserved a special place in my heart. I imagine people choosing ambiguous words with smirks on their faces in much the same was as a small boy grins as he eats his newly acquired bag of Haribo behind an old oak tree, far from the thieving fingers of his friends.

The Functional in Functional Programming is one of those delicious words. A word that in one breath conveys the orientation (another cutely ambiguous word) of the language whilst also implying that there are other, non functional, or dysfunctional languages. It gives me a warm feeling when I read those words. Like being privy to an inside joke amid a sea of straight facedness.

But this series isn't about words. It's about Functional Programming. There will be a lot of mention of words throughout, especially given the flocks of new words landing in the ponds of this newly discovered world I find myself intrigued by.

I should say it up front. All of this is new to me. I know very little about Functional Programming at this point and my aim is to document my journey in the hope that someone might find these musings of some use, or interested, or hell, just some reading to pass the time whilst avoiding Functional Programming.

Mathematics is also something that eludes me. When the gods were handing out the Mathematical genes, or when my teachers were trying to drill us with times tables, I was already a bit busy imagining what It'd be like to ride a dragon through the school halls, burning up the hymn books.

This series of posts come from someone who left secondary school with worse grades than you can imagine. Programming became a love of mine when I was 16 and we've been on one heck of a journey so far. But scientist or mathematician I am not. I'm a guy who really loves to program and who also can't multiply in his head, lest those dragons maketh their return.

My journey into Functional Programming started with some exploration into F#, a language that I plan to spend a lot more time with. Since then the majority of my exploration has been around functional concepts in JavaScript.

I've been inundated with a host of new words and new ways of talking. Where I use to iterate collections I now apply map over values. Where there used to be no names for parameter numbers and no word even describe the concept, now there's Arity with it's Unary, Poliadic and Variadic variations.

A world of Functors, Monads, Compositions and fmaps is springing up around me and so far, I like it!

There will come a time probably in the next few weeks where I'll even be able to talk about Functional Programming is some way that isn't completely abstract and only meaningful to myself. That's part of how I learn. I get the concept, I can make sense and apply it, but I can't yet describe why it's useful. Sometimes it's better to be able to do a thing than to be able to talk about it, at least at first.

That's the other purpose of this series. To be able to put into words some of the things I'm learning so I can become clearer, more organised and from that, more powerfully engaged with this learning process.

A major part of learning something new is practice and I've been spending a lot of time trying out some of the new concepts I've been learning. Currying, Partial Application, crafting pure functions and composing functions from basic building blocks into complex programs. I like to do a few code kata each day too which keeps me just on the edge of the frustration/reward boundary.

Today I came across this kata at codewards.com. The idea is to write a function that will add numbers together when called in succession such that:

```
add(1) -> 1;
add(1)(5) -> 6
add(5)(10)(20) -> 35
```

and so on.

If you've had some experience writing these kind of chained function calls before this is probably an easy one. It took me about 45 minutes to get there with it and the journey was pleasantly exhilarating.
You can give it a go too at http://www.codewars.com/kata/a-chain-adding-function/javascript

For the next piece in this series I'll focus on something more specific with much more code and examples. If there's something you want to know about Functional Programming then asking me questions is a great way to help me improve. I might even add and article about it so hit me up on twitter https://twitter.com/jamiedixon or drop me a note to jamie [at] offthescript.com

Until next time.