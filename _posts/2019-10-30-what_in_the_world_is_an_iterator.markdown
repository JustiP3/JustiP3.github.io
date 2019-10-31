---
layout: post
title:      "What in the world is an iterator? "
date:       2019-10-30 21:57:39 -0400
permalink:  what_in_the_world_is_an_iterator
---


To my audience, if you are trying to gain a better understanding of what is an iterator, I think you would be better off watching any of the myriad of youtube videos that come complete with infographics, visual aids, and whatnot, that is how I learned. I am just another student who recently came to an understanding of how they worked and what is the point. If you are grading me on a blog post assignment, I hope this is satisfactory. 

SO, Why iterators? What is the point? Can't a loop do this?

Yes, a loop can do this with the same outcome. Then why? Iterators are a shortcut for the common and simpler loops that you might want to use.
Iterators operate on a collection like an array or a hash, one element at a time. A loop does the same thing, but requires additional steps like creating an index and finding the length of the array or hash to prevent an infinite loop. If you are someone familiar with loops, the additional steps may seem at first a lot easier than learning how to use an iterator. 
That was definitely the case for me.

What is the deal with that weird, new, and confusing syntax?

array.each do |temp_variable|
<operation>
end 

For me, understanding the syntax was my #1 issue with iterators. Each is one of the most common. What is happening in the above block is this:
1. temp_variable represent the value of the current element of the array
2. for each element of this array we are going to do <operation>, whatever that may be. One possibility is puts "Hey my value is #<temp_variable>!" Which would print that string with the value interpolated in place of <temp_variable>.
3. return the original array. This is specific to the "each" iterator and is very important to remember. 

Once you understand the syntax, you should realize how that is so much easier to use than the basic loop. 

So then if iterators are so cool, then why have loops at all?

Sometimes you need to do a complex operation beyond just going through each element of an array or hash one at a time and storing a value in a new array, or modifying each element in a similar way. Maybe you want to prompt users for an input and you don't want to continue until they enter a valid input. Some things just can't be handled with an iterator that was designed to work on a collection one at a time from start to finish. 

Iterators are critical to understand if you want to write clean, concise, readable, and expandable code. Additionally, once you understand the basic “each” and “collect”, you can expand your arsenal with more powerful iterators. I have recently discovered "delete_if" and you can find many more in the ruby documentation. 

delete_if works as you might think, it operates on an array deleting each element of the array that makes the block passed true,  and returns the modified array. 
For example:
array = [1,3,5,7,9,12,15,20]
array.delete_if { |array_element| array_elelment < 10}
#=> [12,15,20]

Let's walk through this:
We start with our original array and we are going to delete if the current "array_element" if the value is less than 10.
First, we look at the first element, which as a value of 1. 1 is less than 10 and evaluates as true. This element is immediately deleted from the array.
Second, we look at element 2 which has a value of 3. 3 is also less than 10 so this is also deleted.
We follow a similar pattern deleting each element of this array until we get to 12.
when |array_element| is equal to 12 the conditional statement passed in the block "array_element < 10" evaluates false because 12 is greater than 10. This element is not deleted! The same occurs for 15 and 20. 
Since these were the only elements not deleted, 12, 15, and 20 are returned in an array. 

Again, if you were reading this to gain a better understanding of iterators, I hope this helped but keep looking. There are great learning resources out there. 





