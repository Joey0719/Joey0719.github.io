---
layout: post
title:      "My style of working with Procedural Ruby."
date:       2019-12-17 17:27:24 -0500
permalink:  my_style_of_working_with_procedural_ruby
---



You'll often have a piece of code that needs to be executed many times in a program. Instead of writing that piece of code over and over, there's a feature in most programming languages called a procedure, which allows you to extract the common code to one place. In Ruby, we call it a method. Before we can use a method, we must first define it with the reserved word def. After the def we give our method a name. At the end of our method definition, we use the reserved word end to denote its completion. This is an example of a method definition named say:


There's a comment in the method body to show you where the logic for the method definition will go. So why do we want a method named say? To say something, of course! Suppose we had the following code in a file named say.rb. Create this file and type these examples along.

say.rb
puts "hello"
puts "hi"
puts "how are you"
puts "I'm fine"
Notice how we've duplicated the puts many times. We'd like to have one place where we can puts and send that one place the information we want to puts. Let's create a method definition to do that.

say.rb
def say(words)
  puts words
end

say("hello")
say("hi")
say("how are you")
say("I'm fine")
On first glance this may seem silly, since we didn't save any lines of code, and in fact added more code. But what we've done is extracted the logic of printing out text, so that our program can have more flexibility.

We call (or invoke) the method by typing its name and passing in arguments. You'll notice that there's a (words) after say in the method definition. This is what's called a parameter. Parameters are used when you have data outside of a method definition's scope, but you need access to it within the method definition. If the method definition does not need access to any outside data, you do not need to define any parameters.

You will also see the term method invocation to refer to calling a method.

You can name parameters whatever you'd like, but like we said earlier, it is always the goal of a good programmer to give things meaningful and explicit names. We name the parameter words because the say method expects some words to be passed in so it knows what to say! Arguments are pieces of information that are sent to a method invocation to be modified or used to return a specific result. We "pass" arguments to a method when we call it. Here, we are using an argument to pass the word, or string of words, that we want to use in the say method definition. When we pass those words into the method definition, they're assigned to the local variable words and we can use them however we please from within the method definition. Note that the words local variable is scoped at the method definition level; that is, you cannot reference this local variable outside of the say method definition.

When we call say("hello"), we pass in the string "hello" as the argument in place for the words parameter. Then the code within the method definition is executed with the words local variable evaluated to "hello".

One of the benefits that methods give us is the ability to make changes in one place that affect many places in our program. Suppose we wanted to add a . at the end of every string we send to the say method. We only have to make that change in one place.

say.rb
def say(words)
  puts words + '.'    ## <= We only make the change here!
end

say("hello")
say("hi")
say("how are you")
say("I'm fine")
Run this code using the ruby say.rb command from your terminal to see the result. We've now added a . on each line and we only had to add it once in our program. Now you're starting to see the power of methods.

Default Parameters
When you're defining methods you may want to structure your method definition so that it always works, whether given parameters or not. Let's restructure our say method definition again so that we can assign a default parameter in case the caller doesn't send any arguments.

say.rb
def say(words='hello')
  puts words + '.'
end

say()
say("hi")
say("how are you")
say("I'm fine")
You'll notice that say() prints hello. to the console. We have provided a default parameter that is used whenever our method is called without any arguments. Nice!

Optional Parentheses
Many Rubyists will leave off parentheses when calling methods as a style choice. For example, say() could be rewritten as just say. With arguments, instead of say("hi"), it could just be say "hi". This leads to more fluid reading of code, but sometimes it can be confusing. Keep that in mind when you're reading Ruby; it can get tricky deciphering between local variables and method names!


