---
layout: post
title:  "Reductive"
date:   2020-09-19 12:12:01 -0400
categories: Javascript
---
The reduce method is a powerful tool built into vanilla Javascript that can do a lot of heavy lifting for a software developer. Knowing how to use it can distinguish an experienced programmer from her less experienced peers. However, reduce is not as straightforward to use  as the other enumerators built into vanilla JS. Few problems actually call for it, and using reduce unnecessarily can prove to be far more trouble than it's worth. If we're going to understand how to use reduce, we first need to understand what it is and when it is best employed. 

Broadly speaking, a reducer is a logic tool that distills a refined data point from a larger data set. If the data set is a stew, the reducer is the stovetop which will "boil it down" to a more refined product. Different languages approach this concept in slightly different ways. In Javascript, a reducer looks like this:

```

const array = [1, 4, 8, 5]
const reducer = (accumulator, currentValue) => accumulator + currentValue

console.log(array.reduce(reducer))

output: 18

```

What's happening here is very interesting. I am calling the reduce method on my array, and then I am passing my custom reducer function to the reduce method. What's interesting about this is that my custom reducer can be basically anything. In this case, I'm just summming each entry with the accumulator's current value. In short, I'm summing the array. The nature of the reduce method saves the result of this expression in the accumulator variable for the next pass of the array, so all I have to do is decide what will be done upon each visit to an entry in the array. You might have already guessed, but this means that I can use reduce whenever I want. I could always use reduce! Who needs map anyway? But this is, of course, a trap.

snippet


const array = [2, 8, 11, 19]
const reducer = (accumulator, currentValue) =>  currentValue % 2 == 0 ? accumulator + currentValue : accumulator

console.log(array.reduce(reducer))

output: 8

The reduce method is generally intended for a specific purpose: merging data. In the example above, I'm just filtering for even values. And it doesn't even work that well! Do you need the value of a single entry from the data set? Use the find method. Do you need a subset of the original dataset? Use the filter method. There a ton of built in tools that can be fit to the problem at hand. Do you need to return a single value that must be influenced by every entry in an array? Then the reduce method might be a good pick. But there is an additional consideration to make before committing to this path: do your coworkers know how to use reduce? Are you the only one within arm's reach that knows how to debug it? I personally have known devs with many years more experience than myself that get by every day with just the map enumerator. Without casting aspersions, it's important to note that while using cool tools is fun, it's not always very practical. So when exactly should you use reduce? Well, there's no one answer. But from what I understand, the best time to use reduce is when you want to both return a smaller portion of data while also performing some operation when stopping at each entry. It's at this point that using reduce becomes more efficient and it's time to start breaking out your accumulators.
