---
layout: post
title:      "Looping in Ruby"
date:       2018-09-30 21:39:02 +0000
permalink:  looping_in_ruby
---


Explain a difficult part about Looping as if you were teaching it to a Learn student who had just started it.

Explain your particular style of working with Looping.

Loops are a construct that allows you to automatically repeat statements in less than a second. Once a condition is met, the loop stops. If no condition is given, Ruby will infinitely loop that statement. The following code creates an infinite loop in Ruby, because no condition is provided. 

```
loop do 
   puts "Hello World"
end
```

We can break the above code using the keyword break, which acts as a control for the loop. For example,

```
f = 4
loop do
    f += 16
    puts f
		break
end
```

The above loop took the variable f with the value of 4 and added 4 to each new loop until f equalled 16. The word break tells Ruby to stop looping after the first cycle.

One of my favorite loops, is the times loop. As explicit as it sounds, the times loop, runs your code as many times as you tell it to. For example,

```
3.times{ |x| puts x}
```

In the above code, Ruby returns the value of the variable x for three successive loops starting at 0. The curly braces notation { } tells Ruby to "do" whatever statement is within the braces and "end" after the braces close and once the conditon is met. `puts x` is a block which tells Ruby to return x until the condition `3.times` is met. The pipes `| |` around x indicate that x is an interator. Iteration in Ruby, means to repeat something. Therefore, iteration is a method that loops over data and operate on each element in that collection. 
to In this case, Ruby returns the following to the above code:

```
>> 3.times { |x| puts x }
0
1
2
=> 3
```

Some other 'loops' that execute code a certain number of times include: for loop, while loop, until loop
