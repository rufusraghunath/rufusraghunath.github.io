Code Sharing: Classes vs. Prototypes
===========

I originally wrote this article for students at <a href="http://www.codefirstgirls.org.uk/">Code First: Girls</a> London. You may find it useful if you are interested in prototypal inheritance and JavaScript in general, and have some experience with classical inheritance. The article assumes some Ruby knowledge, but experience in any classical language (Java, C#, etc.) should translate well.

Introduction
---------
On your coding adventures so far, you've probably already realized that in order to maintain and organize your programs, you need to introduce some sort of predictable and intuitive structure. A common problem is sharing data or functionality between separate parts of the program that need to do similar kinds of things.

One way of achieving this is with the concept of _inheritance_. You can think of it in the same way as biological inheritance – you inherit some attributes from your parents, but might still have attributes of your own that your parents don't have. The most common form of sharing is called _classical inheritance_ (classical as in "involving classes"). Lots of people feel that this works well in object-oriented languages (Rich Hickey would disagree!), and you're probably already a little familiar with it from Ruby or another classical OO language.

But beware! Javascript has neither classes nor classical inheritance, _but it's often written as though it did_! In fact, the language makes several provisions to help programmers "pretend" that they're writing classes, which can be pretty confusing. For example, ECMAScript 6 (the 2015 version of JS) implements a `class` keyword. <a href="https://www.destroyallsoftware.com/talks/wat">Wat?!</a>

This has historically been because JS was often written by people who spend most of their time programming in other, likely classical, tech stacks (less so nowawdays because you can now write fullstack JS). So it was sensible for the language to provide familiar-feeling solutions to those developers. However, JS has its own way of sharing data and functionality: prototypal inheritance.

In this article we are going to learn about this very simple and powerful concept. Hopefully it will clear up any misconceptions you might have about JS and help you avoid future confusion.

Classes in Ruby
---------
Let's use classes in Ruby as a refresher on how classical inheritance can work. Say we're bored on weekends and want a loving puppy to keep us company. We could write:

{% highlight ruby %}
class Dog
    def initialize name
        @name = name
        puts "Why hello there. I am your new dog, and my name is #{@name}!"
    end

    def bark
        puts "WOOF!"
    end
end
{% endhighlight %}

This creates a "blueprint" for a _type of thing_ that we've called `Dog`. When you ask for a new `Dog`, Ruby looks at the blueprint and gives you back an object that has all the methods and properties that we've specified in the class. This is called _instantiation_ – making a specific thing (object) based on an abstract thing (class). Of course, in Ruby, classes are objects in their own right (instances of the class `Class`), but let's not go there...

The `initialize` method runs once when the object is brought into life, so it's often used to pass properties needed to make a class instance fully functional (for example, in this case the `name` argument gets saved in the instance variable `@name` and could be accessed later if needed).

With me so far? Cool, so let's go get our puppy...

{% highlight ruby %}
spot = Dog.new("Spot")
# Why hello there. I am your new dog, and my name is Spot!

spot.bark
# WOOF!
{% endhighlight %}

Nice. So now we have a barking dog. But what if we want to go for walkies? Guess we should add some form of walking functionality...

{% highlight ruby %}
class Dog
    def initialize name
        @name = name
        puts "Why hello there. I am your new dog, and my name is #{@name}!"
    end

    def bark
        puts "WOOF!"
    end

    def walk
        puts "Aw yiss, going for walkies!"
    end
end

spot = Dog.new("Spot")
# Why hello there. I am your new dog, and my name is Spot!

spot.walk
# Aw yiss, going for walkies!

{% endhighlight %}

That's nice and all, but doesn't it feel weird somehow to have `walk` associated with `Dog`? Surely walking is not a dog-specific thing. A more accurate domain model would be to think of a dog as an example of one type of thing that is able to walk – for simplicity's sake, let's call it `Animal`. Sounds like another class to me...

{% highlight ruby %}
class Animal
    def walk
        puts "Aw yiss, going for walkies!"
    end
end
{% endhighlight %}

So now we have dogs and animals. To give `Dog` access to `walk`, we need to somehow connect the two classes. That's where _inheritance_ comes in.

{% highlight ruby %}
class Animal
    def walk
        puts "Aw yiss, going for walkies!"
    end
end

class Dog < Animal
    def initialize name
        @name = name
        puts "Why hello there. I am your new dog, and my name is #{@name}!"
    end

    def bark
        puts "WOOF!"
    end
end

spot = Dog.new("Spot")
# Why hello there. I am your new dog, and my name is Spot!

spot.bark
# WOOF!

spot.walk
# Aw yiss, going for walkies!
{% endhighlight %}

Dogs are a logical subset of animals, yes? All dogs are animals, but not all animals are dogs. So, by representing that in our code like above we can include all `Animal` code in the `Dog` class. You can use `spot.methods` to get an array of all the available methods on our puppy, and you'll see that it includes both `bark` and `walk`!

{% highlight ruby %}
spot.methods.include? :bark
# true

spot.methods.include? :walk
# true
{% endhighlight %}

The beauty of this design is that we can now create as many other kinds of animals as we like, and they'll all be able to walk! And there you have it, the basics of classical inheritance.

"Classes" in JS > ES6
---------
As mentioned before, there is now a `class` keyword in JS. So you can now write things like this:

{% highlight javascript %}
class Dog {
    bark() {
        console.log("WOOF!");
    }
}

const spot = new Dog();
spot.bark();
// WOOF!
{% endhighlight %}

Hooray. We now have a JS blueprint for a barking dog. For a more realistic example, let's look at Facebook's React, which can be written with this kind of setup:

{% highlight javascript %}
import React from 'react';

class ExampleComponent extends React.Component {
    constructor(props) {
        super(props);
        this.setState({
            message: "Hello, world!"
        });
    }

    render() {
        return (
           // render some JSX
        );
    }
}
{% endhighlight %}

The idea here is that when `new ExampleComponent()` gets called, `constructor` runs first (like `initialize` in Ruby). The call to `super` means that the `constructor` on the superordinated class (the class that `ExampleComponent` inherits from – in this example `React.Component`) will also be called. The same concept exists in Ruby, Java, and other classical languages.

All seems pretty familiar, doesn't it? Still, it's important to remember that this is _not_ the same as `class` in Ruby. In fact, it's just a thin layer of syntactic sugar around the way people used to write fake classes in JS back in the day, before ES6 was a thing. That means that when you write a class in ES6, what you actually get is...

"Classes" in JS =< ES6
---------
You might already be aware that Javascript has first-class functions – you can pass functions around like variables and then use them whenever you like. You can also define _constructor functions_ that can be used with the `new` keyword (but you have to use the `function` keyword rather than using the new ES6 arrow functions).

{% highlight javascript %}
const Dog = function() {};
new Dog();
// Dog {}
{% endhighlight %}

FYI, constructor function names are capitalised by convention.

Interestingly, JavaScript functions are just key-value collections. What I mean by that is that, in essence, they're just like hashes in Ruby, dictionaries in Python, or maps in many other languages. You can assign properties to them and access their properties later. 

There are, however, a few things that distinguish functions from normal JS objects. For one thing, they are _callable_. That means that when you define a function, you can equip it with a block of code that it will remember and be able to execute when you ask it to.

Another of the special properties they have is called `prototype`. At the moment, we haven't set a prototype on `Dog`:

{% highlight javascript %}
Dog.prototype;
// undefined
{% endhighlight %}

Let's play around with it now to see what it does:

{% highlight javascript %}
const bark = function() {
    console.log('WOOF!');
};

Dog.prototype.bark = bark;

Dog.prototype;
// { bark: () }

const spot = new Dog();
spot.bark();
// WOOF!
{% endhighlight %}

We define a `bark` function, then add it to the `Dog` prototype. And like magic, our new dog `spot` is able to bark.

The `class` keyword in ES6 works exactly like this, it just saves you the trouble of dealing with `prototype`. But it writes the exact same code for you at the end of the day, so that the ES6 `Dog` from the previous section and the one we've just written are completely identical.

Prototypal inheritance: The prototype chain
---------
OK, so we've seen how classes work in Ruby, and we've seen a very similar-looking thing in JavaScript. So why do I keep saying there are no classes in JS? Time for a peek under the hood to see how inheritance in JS actually works!

Every object in JS has a property called `__proto__`. You can think of this as a kind of "phone book", or a lexion – whenever you ask an object for a property that hasn't been defined on it, it can pass the request on to the object defined as its `__proto__`. This is known as _delegation_.

In this way, all JavaScript objects are linked together in a cooperative lookup arrangement known as the _prototype chain_. (If you're into computer science, this is conceptually pretty similar to a [linked list](https://www.youtube.com/watch?v=_jQhALI4ujg)). If you follow this chain for long enough, you will always end up reaching `Object`, the final link.

{% highlight javascript %}
new Object().__proto__;
// Object {}

new Array().__proto__;
// []

new Array().__proto__.__proto__;
// Object {}

new Dog().__proto__;
// function() {}

new Dog().__proto__.__proto__;
// Object {}
{% endhighlight %}

It is indeed objects all the way down (forgive the joke).

To summarise, the major difference between prototypal and classical inheritance is that the functionality of superordinated classes always becomes part of inheriting classes, while prototypes are simply independent objects that get delegated to by other objects.

There are many neat tools in JS, such as `Object.create()`, that let you exploit this prototypal functionality in order to knit together your objects in useful and elegant ways that allow you to "share" (read: delegate) functionality without locking your domain model into rigid class hierarchies.

Prototypal inheritance: Constructor functions
---------
But Rufus, I hear you cry, earlier you were talking about `prototype`, and now we're suddenly talking about this bizarre thing with four underscores called `__proto__`. What gives?

No worries – this final mystery, too, shall be divulged.

It turns out that a function in JS essentially gets two prototypes – `__proto__` because it's just another kind of object, and `prototype` _just in case you want to use it as a constructor function_. Every time you "instantiate" your constructor funciton, JS actually gives you back a brand new object with its `__proto__` set your constructor's `prototype`.

{% highlight javascript %}
function CodeFirstGirls() {};

CodeFirstGirls.prototype.isFun = true;
CodeFirstGirls.prototype.javaScriptRating = "over 9000";

CodeFirstGirls.prototype;
// {
//    isFun: true,
//    javaScriptRating: "over 9000"
// }

new CodeFirstGirls().__proto__;
// {
//    isFun: true,
//    javaScriptRating: "over 9000"
// }
{% endhighlight %}

As a final aside, an interesting thing in ES6 is the introduction of arrow functions. This is a more elegant and concise way of writing functions: `() => {}` as opposed to `function() {}`. However, you can't use ES6 arrow functions as constructors because they don't have their own `this` context. But that's a whole other conversation for another day, so relax if that sounds like meaningless gibberish to you. You can read more about arrow funtions [here](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/Arrow_functions).

Try it yourself
---------
If you're feeling comfortable with what we've covered here so far, you can try to re-implement JavaScript's `new`. The function should be called `renew` and implement prototypal inheritance.

Hint: you might want to look into `Object.create`.

Further reading
---------
If this was interesting to you, I recommend that you pick up <a href="http://shop.oreilly.com/product/9780596517748.do">_JavaScript: The Good Parts_</a>, by Douglas Crockford. It is _the_ classic text on writing good JS, and what's more, it's short, readable, and funny (as well as highly opinionated). It includes an excellent introduction to prototypal inheritance.