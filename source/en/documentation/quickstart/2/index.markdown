---
layout: page
title: "Ruby in twenty minutes (2/4)"
date: 2011-08-05 23:33
comments: false
sharing: false
footer: false
---
What if we want to say “Hello” a lot without getting our fingers all tired? We need to define a method!

``` ruby
    irb (main):010:0> def h
    irb (main):011:1>   puts "Hello World!"
    irb (main):012:1> end
    => nil
```

The code `def h` starts the definition of the method. It tells Ruby that
we’re defining a method, that its name is `h`. The next line is the body of
the method, the same line we saw earlier: `puts "Hello World"`. Finally, the last line `end` tells Ruby we’re done defining the method. Ruby’s response `=> nil` tells us that it knows we’re done defining the method.

## The Brief, Repetitive Lives of a Method

Now let’s try running that method a few times:

``` ruby
    irb (main):013:0> h
    Hello World!
    => nil
    irb (main):014:0> h()
    Hello World!
    => nil
```

Well, that was easy. Calling a method in Ruby is as easy as just mentioning its name to Ruby. If the method doesn’t take parameters
that’s all you need. You can add empty parentheses if you’d like, but they’re not needed.

What if we want to say hello to one person, and not the whole world? Just redefine `h` to take a name as a parameter.

``` ruby
    irb (main):015:0> def h (name)
    irb (main):016:1>   puts "Hello #{name}!"
    irb (main):017:1> end
    => nil
    irb (main):018:0> h ("Matz")
    Hello Matz!
    => nil
```

So it works… but let’s take a second to see what’s going on here.

## Holding Spots in a String

What’s the `#{name}` bit? That’s Ruby’s way of inserting something into a string. The bit between the braces is turned into a string (if it isn’t one already) and then substituted into the outer string at that point. You can also use this to make sure that someone’s name is properly capitalized:

``` ruby
    irb (main):019:0> def h(name = "World")
    irb (main):020:1>    puts "Hello #{name.capitalize}!"
    irb (main):021:1> end
    => nil
    irb (main):022:0> h "chris"
    Hello Chris!
    => nil
    irb (main):023:0> h
    Hello World!
    => nil
```

A couple of other tricks to spot here. One is that we’re calling the method without parentheses again. If it’s obvious what you’re doing, the parentheses are optional. The other trick is the default parameter `World`. What this is saying is “If the name isn’t supplied, use the default name of `"World"`”.

## Evolving Into a Greeter

What if we want a real greeter around, one that remembers your name and welcomes you and treats you always with respect. You might want to use
an object for that. Let’s create a “Greeter” class.

``` ruby
    irb (main):024:0> class Greeter
    irb (main):025:1>   def initialize (name = "World")
    irb (main):026:2>     @name = name
    irb (main):027:2>   end
    irb (main):028:1>   def say_hi
    irb (main):029:2>     puts "Hi #{@name}!"
    irb (main):030:2>   end
    irb (main):031:1>   def say_bye
    irb (main):032:2>     puts "Bye #{@name}, come back soon."
    irb (main):033:2>   end
    irb (main):034:1> end
    => nil
```

The  new keyword here is `class`. This defines a new class called `Greeter` and a bunch of methods for that class. Also notice ``name`. This is an instance variable, and is available to all the methods of the class. As you can see it’s used by `say_hi` and `say_bye`.

So how do we get this Greeter class set in motion? [create an object][ruby20min3].


## [1][ruby20min1] | 2 | [3][ruby20min3] | [4][ruby20min4]

[ruby20min1]: ../
[ruby20min3]: ../3
[ruby20min4]: ../4