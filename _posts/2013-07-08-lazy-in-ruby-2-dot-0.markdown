---
layout: post
title: "Lazy in Ruby 2.0"
date: 2013-07-08 14:09
comments: true
categories: 
---

Ruby 2.0 is pretty cool. Over the past week or so I've been working with [Stefan Lance](http://stefanlance.com) at the [Flatiron School](http://flatironschool.com/) on updating the [Ruby Koans](http://rubykoans.com/) to Ruby 2.0. It's been a lot of fun, and I've been learning quite a bit along the way. 

One new feature that I've been working on for the Ruby Koans is the [lazy enumerator](http://ruby-doc.org/core-2.0/Enumerator/Lazy.html). The basic idea is that you can extract values over an infinite series of values. 

Let's see some examples. 

Infinite Range
---
	range = 1..Float::INFINITY
	
Here we have our infinite range. If you wanted to try collecting on it in Ruby 1.9.3, you'd get an infinite loop: 

	range.collect{ |x| x }.first(5) # => infinite loop
	
However, by using lazy, we can get our desired output:

	range.lazy.collect{ |x| x }.first(5) # => [1,2,3,4,5]

Lazy Select
---

With lazy select, you can iterate over an infinite loop and take out only the values that you need. 

	class Num
		def even
			i = 0
				loop do
  					yield i
	 		   		i += 2 
			end
		end
	end
	
	num = Num.new 



	
	num.enum_for(:evens).lazy.select{|i| i < 5 }.take(3).each{|i| enums << i} # => 0, 2


