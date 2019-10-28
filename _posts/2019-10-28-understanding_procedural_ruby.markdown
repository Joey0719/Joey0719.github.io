---
layout: post
title:      "Understanding Procedural Ruby"
date:       2019-10-28 21:56:39 +0000
permalink:  understanding_procedural_ruby
---


Ruby provides the programmer with a set of very powerful features borrowed from the domain of functional 

programming, namely closures, high-order functions and first-class functions. These features are implemented

in Ruby by means of code blocks, Proc objects and methods (that are also objects) - concepts that are closely

related and yet differ in subtle ways. In fact I found myself quite confused about this topic, having a difficulty to

understand the difference between blocks, procs and methods and unsure about the best practices of using them.

I was unsure of how the Ruby concepts map to similar idioms from other programming languages. Sifting though

hundreds of newsgroup posts, I saw that I'm not the only one with this problem, and in fact quite a lot of "Ruby Nubies"

struggle with the same ideas.

In this blog I lay out my understanding of this facet of Ruby, which comes as a result of extensive research of Ruby books,

documentation and comp.lang.ruby, in sincere hope that other people will find it useful as well. Ruby doesn't really have 

functions. Rather, it has two slightly different concepts - methods and Procs (which are, as we have seen, simply what 

other languages call functions objects, or functors). Both are blocks of code - methods are bound to Objects, and 

Procs are bound to the local variables in scope. Their uses are quite different.


