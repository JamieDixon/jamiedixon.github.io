---
layout: post
title:  "Functional Programming for the dysfunctional mind - Part II - Composition"
date:   2015-01-27 12:00:00
---

In [Part I of Functional Programming for the dysfunctional mind](/2015/01/22/functional-programming-part1.html)  I introduced the series and talked a little about some of the new learnings I've discovered as I delve into the world of Functional Programming.

In this part I'm going to talk a little about composition.

If you've read part one you'll know that my love for words is not only an auditory sensibility but also a tactile adventure. Sometimes a word just gets into your bones and leads you through an old decaying door afore a secret garden.

The word "composition" has this kind of fluid effect on me. It's a word that flows off the tongue and creates imagery of music and soundwaves.

Functional Programming brings with it it's own concept of composition and just as the word slips effortlessly along its vector, so too does the concept in programming.

Composition in Functional Programming is all about the flow of functions and their execution. It's about piecing together the notes of a program to build mad rocking riffs.

We can use function composition for many purposes, some explicit and some more implicit.

Let's start with a real-world JavaScript example based on some SVG work I did recently. Here's some functions:

```
function getSvgShapes(fragment) { // Get some shapes out of an SVG fragment
   return fragment.selectAll('circle, rect, path');
}

function getSvgShapeColours(shapes) { // Grab the fill colour of each shape
   return shapes.map(function (shape) {
      return shape.css('fill');
   });
}

function distinct(items) { // Filter a collection for distinct values
   var seen = [];
   return items.filter(function (item) {
     var isSeen = seen.indexOf(item) > -1;
     seen.push(item);
     return !isSeen;
   });
}

```

We'll use these three functions as our basic building blocks for this example.

The traditional way to use these three functions in combination would be to store the result of each function in a variable and then pass it along to the next function in line.

```
var shapes = getSvgShapes(fragment);
var colours = getSvgShapeColours(shapes);
var distinctColours = distinct(colours);
```

A more composed way of expressing this is in the form f(g(z(x)))

```
var distinctColours = distinct(getSvgShapeColours(getSvgShapes(fragment)))
```

In both cases we can see that the output of one function becomes the input to another function. In the latter example we've created a highly composed version of the former which makes your code easier to reason about.
It's easier to reason about because the relationship between the outputs and inputs is not only explicit, but it is, by it's nature confined to a single location in your code file.

This is all good and well but what's the big deal? We're just passing results to functions and we've been doing that since forever.

Composition in Functional Programming isn't just about passing outputs as inputs, it's also about crafting named compositions that become the building blocks of more specialised functions.

A named composition is what we get when we take a bunch of functions and we compose them within another, reusable function.

```
function distinctShapeColours(fragment) {
   return distinct(getSvgShapeColours(getSvgShapes(fragment)));
}
```

Now we have a named composition `distinctShapeColours` that we can apply to any SVG fragment to obtain a distinct collection of shape colours. The real power of this is in our ability to not only compose our three basic functions, but to also compose our new named composition with other functions in future.

It would be a pain if we had to manually write our own named composition functions every time we wanted to compose and luckily, libraries such as LoDash and Underscore come with their own implementations of compose.

```
var distinctShapeColours = _.compose(distinct, getSvgShapeColours, getSvgShapes);
var colours = distinctShapeColours(fragment);
```

You'll notice here that the flow of the function parameters is right-to-left. In english that means you can read the parameters left-to-right as "Apply `distinct` to the output of `getSvgShapeColours` once you've applied `getSvgShapeColours` to the output of `getSvgShapes`" and so on.

I find it's easier to read the parameters right-to-left. "`getSvgShapes` then pass the result to `getSvgShapeColours` then pass its result to `distinct`".

In LoDash the function is actually named `flowRight` rather than `compose`.

A hidden benefit of writing code that's composable is that you start to consider unary arity (single parameter functions) as a really good thing.

Since we can only compose functions that take single parameters (the return value from the previous function), we start to factor our code into discrete pieces that can be composed together to craft complex programs.

We often achieve SRP (Single Responsibility Principle) through the trail left behind by our thought process while aiming for highly composable functions. Win!

I'm only just scratching the surface of composition here and as my understanding of Functional Programming increases I'm sure I'll have a lot more to say about the topic.

The immediately obvious benefits so far seem great. It becomes easier to reason about our programs, they're easier to read and entire programs start to become compositions of highly reusable streams.

Not only that, but our entire focus changes. We start to think about how data flows through our systems and gradiates between forms. Rather than seeing our programs as sets of instructions we can start to see them as musical scores and data as our musician.

Next time I'll talk about crafting unary functions from polyadic functions, currying and partial application.